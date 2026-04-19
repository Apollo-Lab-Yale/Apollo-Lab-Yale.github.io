---
layout: default
title: News
permalink: /news/
---

<!-- Extraction of unique variables for dropdowns -->
{% assign all_news = site.data.news %}
{% assign all_years = "" | split: "," %}
{% assign all_types = "" | split: "," %}

{% for post in all_news %}
  {% assign y = post.date | date: "%Y" %}
  {% assign all_years = all_years | push: y %}
  
  {% assign t = post.type | default: "Announcement" | capitalize %}
  {% assign all_types = all_types | push: t %}
{% endfor %}

{% assign all_years = all_years | uniq | sort | reverse %}
{% assign all_types = all_types | uniq | sort %}

<!-- Filter Control Panel -->
<div class="card mb-5 mt-4 shadow-sm" style="border-radius: 12px; border-top: 4px solid #3b82f6 !important;">
  <div class="card-body p-4 bg-light" style="border-radius: 12px;">
    <div class="row">
      <!-- Year -->
      <div class="col-md-3 mb-3 mb-md-0">
        <label for="filter-year" class="form-label" style="font-weight: 600; font-size: 0.9em;">Year</label>
        <select id="filter-year" class="form-control filter-input border-0 shadow-sm" style="border-radius: 8px;">
          <option value="all">All Years</option>
          {% for year in all_years %}
            <option value="{{ year }}">{{ year }}</option>
          {% endfor %}
        </select>
      </div>
      <!-- News Type -->
      <div class="col-md-3 mb-3 mb-md-0">
        <label for="filter-type" class="form-label" style="font-weight: 600; font-size: 0.9em;">Category</label>
        <select id="filter-type" class="form-control filter-input border-0 shadow-sm" style="border-radius: 8px;">
          <option value="all">All Categories</option>
          {% for category in all_types %}
            <option value="{{ category | downcase }}">{{ category }}</option>
          {% endfor %}
        </select>
      </div>

      <!-- Word Search -->
      <div class="col-md-3">
        <label for="filter-search" class="form-label" style="font-weight: 600; font-size: 0.9em;">Text Search</label>
        <div class="input-group shadow-sm" style="border-radius: 8px;">
          <input type="text" autocomplete="off" id="filter-search" class="form-control filter-input border-0" placeholder="Type here..." style="border-radius: 8px 0 0 8px;">
          <button class="btn btn-white bg-white border-0" type="button" onclick="document.getElementById('filter-search').value=''; document.getElementById('filter-search').dispatchEvent(new Event('input'));" style="border-radius: 0 8px 8px 0;" title="Clear Search">
            <i class="fas fa-times text-muted"></i>
          </button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Timeline Stream -->
<div class="news-timeline pb-5" id="news-container">
  {% for post in site.data.news %}
    {% assign entry_type = post.type | default: "announcement" | downcase %}
    {% assign display_type = post.type | default: "Announcement" | capitalize %}
    {% assign icon = "fas fa-newspaper" %}
    
    {% assign lower_title = post.title | downcase %}
    {% if entry_type == "paper" or entry_type == "publication" or lower_title contains 'paper' or lower_title contains 'journal' or lower_title contains 'conference' %}
      {% assign icon = "fas fa-file-alt" %}
      {% assign display_type = "Publication" %}
    {% elsif entry_type == "award" or entry_type == "prize" or lower_title contains 'award' or lower_title contains 'won' or lower_title contains 'fellowship' %}
      {% assign icon = "fas fa-trophy" %}
      {% assign display_type = "Award" %}
    {% elsif entry_type == "grant" or entry_type == "funding" %}
      {% assign icon = "fas fa-money-bill-wave" %}
    {% elsif entry_type == "conference" %}
      {% assign icon = "fas fa-users" %}
    {% elsif entry_type == "talk" or entry_type == "presentation" or lower_title contains 'talk' or lower_title contains 'keynote' or lower_title contains 'presentation' %}
      {% assign icon = "fas fa-microphone" %}
      {% assign display_type = "Presentation" %}
    {% elsif entry_type == "media" or entry_type == "press" %}
      {% assign icon = "fas fa-bullhorn" %}
    {% endif %}

    <!-- Extract Word Count for Smart Collapse Logic -->
    {% assign word_count = post.content | strip_html | number_of_words %}

    <div class="card mb-4 news-card shadow-sm" 
         data-year="{{ post.date | date: "%Y" }}" 
         data-type="{{ entry_type | downcase }}" 
         data-tags="{{ post.tags | join: ',' | downcase | escape }}"
         data-text="{{ post.title | append: ' ' | append: post.content | strip_html | downcase | escape }}"
         style="border-left: 5px solid #3b82f6 !important; border-radius: 12px !important; transition: transform 0.2s;">
      
      <div class="card-body p-4">
        <div class="d-flex align-items-center mb-3">
          <div class="icon-circle text-white d-flex justify-content-center align-items-center" style="background-color: #3b82f6; width: 50px; height: 50px; border-radius: 50%; min-width: 50px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
            <i class="{{ icon }} fa-lg"></i>
          </div>
          <div class="ms-3 mb-0 pb-0" style="margin-left: 1rem !important;">
            <h4 class="card-title mb-1 pb-0" style="margin-bottom: 0 !important; font-weight: 700;">
              {{ post.title }}
            </h4>
            <div class="d-flex align-items-center mt-1">
              <span class="badge bg-secondary text-white" style="font-size:0.85em; margin-right: 1.25rem !important;">{{ display_type }}</span>
              <h6 class="card-subtitle text-muted mb-0" style="font-size: 0.9rem; font-weight: 500;">
                {{ post.date | date: '%B %-d, %Y' }}
              </h6>
            </div>
          </div>
        </div>
        
        <div class="card-text mt-3" style="font-size: 1.05rem; line-height: 1.6; color: #1a1a1a !important;">
          
          <!-- Content hidden by default behind the toggle button -->
          <div id="full-{{ forloop.index }}" class="d-none mt-2">
            {{ post.content | markdownify | replace: '<img', '<img class="img-fluid rounded shadow-sm my-3" style="max-height:400px; display:block;"' }}
          </div>
          
          <button class="btn btn-sm btn-outline-primary rounded-pill mt-2 px-3 fw-bold" id="toggle-{{ forloop.index }}" onclick="toggleNews({{ forloop.index }})">
            Read Full Story <i class="fas fa-chevron-down ms-1"></i>
          </button>

        </div>
        
        {% if post.tags.size > 0 %}
          <div class="mt-4 pt-3 border-top">
            {% for tag in post.tags %}
              <span class="badge bg-light text-dark border me-1 px-2 py-1">{{ tag }}</span>
            {% endfor %}
          </div>
        {% endif %}
      </div>
    </div>
  {% endfor %}
</div>

<script>
// Toggle Function logic for Smart Expanders
function toggleNews(id) {
  const full = document.getElementById('full-' + id);
  const btn = document.getElementById('toggle-' + id);
  
  if (full.classList.contains('d-none')) {
    // Reveal Full
    full.classList.remove('d-none');
    btn.innerHTML = 'Close Story <i class="fas fa-chevron-up ms-1"></i>';
    btn.classList.replace('btn-outline-primary', 'btn-light');
  } else {
    // Hide Full
    full.classList.add('d-none');
    btn.innerHTML = 'Read Full Story <i class="fas fa-chevron-down ms-1"></i>';
    btn.classList.replace('btn-light', 'btn-outline-primary');
  }
}

// Live Javascript Dashboard Filter Logic
document.addEventListener('DOMContentLoaded', function() {
  const filterInputs = document.querySelectorAll('.filter-input');
  const newsCards = document.querySelectorAll('.news-card');

  // Core Filtering Pipeline
  function filterNews() {
    const yrVal = document.getElementById('filter-year').value;
    const tyVal = document.getElementById('filter-type').value;
    const searchVal = document.getElementById('filter-search').value.toLowerCase().trim();

    newsCards.forEach(card => {
      const cYear = card.getAttribute('data-year');
      const cType = card.getAttribute('data-type');
      const cText = card.getAttribute('data-text');

      const matchYear = (yrVal === 'all' || cYear === yrVal);
      const matchType = (tyVal === 'all' || cType.includes(tyVal));
      
      let matchSearch = true;
      if (searchVal !== '') {
        matchSearch = cText.includes(searchVal);
      }

      if (matchYear && matchType && matchSearch) {
        card.style.display = '';
      } else {
        card.style.display = 'none';
      }
    });
  }

  // Bind execution events to all dropdowns and search bars
  filterInputs.forEach(input => {
    if (input.tagName.toLowerCase() === 'select') {
      input.addEventListener('change', filterNews);
    } else {
      input.addEventListener('input', filterNews);
    }
  });
});
</script>
