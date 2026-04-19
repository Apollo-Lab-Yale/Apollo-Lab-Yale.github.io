---
title: Publications
permalink: /publications/
---

<!-- Override Unstable Sorts: Year Descending, Title Ascending -->
{% assign all_pubs = "" | split: "," %}
{% assign year_groups = site.data.publications | group_by: "year" | sort: "name" | reverse %}
{% for group in year_groups %}
  {% assign sorted_items = group.items | sort_natural: "title" %}
  {% for item in sorted_items %}
    {% assign all_pubs = all_pubs | push: item %}
  {% endfor %}
{% endfor %}

<!-- Extraction of unique variables for dropdowns -->
{% assign all_years = site.data.publications | map: "year" | uniq | sort | reverse %}
{% assign all_types = all_pubs | map: "type" | uniq | sort %}
{% assign all_venues = all_pubs | map: "venue" | compact | uniq | sort %}
{% assign all_threads = site.data.research | map: "title" | sort %}

<!-- Filter Control Panel -->
<div class="card mb-5 mt-4 shadow-sm" style="border-radius: 12px; background-color: #f8f9fa; border-top: 4px solid #3b82f6 !important;">
  <div class="card-body p-4">
    
    <!-- Top Row: Structured Dropdowns -->
    <div class="row">
      <div class="col-md-2 mb-3">
        <label for="filter-year" style="font-weight: 500; font-size: 0.9em; color: #555;">Year</label>
        <select id="filter-year" class="form-control filter-input">
          <option value="all">All</option>
          {% for year in all_years %}
          <option value="{{ year }}">{{ year }}</option>
          {% endfor %}
        </select>
      </div>
      
      <div class="col-md-2 mb-3">
        <label for="filter-type" style="font-weight: 500; font-size: 0.9em; color: #555;">Type</label>
        <select id="filter-type" class="form-control filter-input">
          <option value="all">All</option>
          {% for type in all_types %}
          <option value="{{ type | downcase }}">{{ type }}</option>
          {% endfor %}
        </select>
      </div>
      
      <div class="col-md-2 mb-3">
        <label for="filter-venue" style="font-weight: 500; font-size: 0.9em; color: #555;">Venue</label>
        <select id="filter-venue" class="form-control filter-input">
          <option value="all">All</option>
          {% for venue in all_venues %}
          <option value="{{ venue | downcase }}">{{ venue }}</option>
          {% endfor %}
        </select>
      </div>
      
      <div class="col-md-3 mb-3">
        <label for="filter-thread" style="font-weight: 500; font-size: 0.9em; color: #555;">Research Thread</label>
        <select id="filter-thread" class="form-control filter-input">
          <option value="all">All Threads</option>
          {% for thread in all_threads %}
          <option value="{{ thread | downcase | strip }}">{{ thread }}</option>
          {% endfor %}
        </select>
      </div>
      

    </div>
    
    <!-- Bottom Row: Dynamic Author Auto-Complete -->
    <div class="row">
      <div class="col-md-12">
        <label for="filter-author" style="font-weight: 500; font-size: 0.9em; color: #555;">Search Authors</label>
        <div class="input-group">
          <input type="text" autocomplete="off" id="filter-author" class="form-control filter-input border-right-0" list="author-list" placeholder="Start typing an author's name...">
          <div class="input-group-append">
            <button class="btn btn-outline-secondary bg-white border-left-0" type="button" onclick="document.getElementById('filter-author').value=''; document.getElementById('filter-author').dispatchEvent(new Event('input'));" title="Clear Search" style="border-color: #ced4da;">
              <i class="fas fa-times text-muted"></i>
            </button>
          </div>
        </div>
        <datalist id="author-list">
          <!-- Options injected dynamically via JS -->
        </datalist>
      </div>
    </div>
    
  </div>
</div>

<div class="pub-list" id="publications-container">
{% for publication in all_pubs %}
  {% assign slug = publication.title | slugify %}
  
  <!-- Publish attributes to correctly bind with Javascript filter logic -->
  <div class="card mb-5 shadow-sm pub-card" 
       id="{{ slug }}" 
       data-year="{{ publication.year }}" 
       data-type="{{ publication.type | downcase }}" 
       data-venue="{{ publication.venue | default: '' | downcase }}"
       data-threads="{% if publication.threads %}{{ publication.threads | join: '|' | downcase | escape }}{% endif %}"
       data-authors="{{ publication.authors | escape }}"
       data-keywords="{{ publication.keywords | escape }}"
       style="scroll-margin-top: 100px; border-radius: 12px; overflow: hidden; border-left: 5px solid #3b82f6 !important;">
       
    <div class="card-body p-4">
      <div class="row align-items-center">
        <!-- Details Column -->
        <div class="{% if publication.video %}col-md-7{% else %}col-12{% endif %} mb-4 mb-md-0">
          <h4 class="card-title font-weight-bold" style="line-height: 1.4;">
            {{ publication.title }}
            <a href="#{{ slug }}" class="text-muted ml-2" title="Direct link to this paper" style="font-size: 0.7em; text-decoration: none;">
              <i class="fas fa-link"></i>
            </a>
          </h4>
          
          <h6 class="card-subtitle mt-3 mb-3 text-muted" style="line-height: 1.5; font-size: 1.1rem;">
            {{ publication.authors }}
          </h6>
          
          <div class="mb-4">
            <span class="badge badge-primary bg-primary text-white p-2 mr-2" style="font-size: 0.9em; font-weight: 500;">
              {% if publication.type %}{{ publication.type }}{% if publication.venue %}: {% endif %}{% endif %}{{ publication.venue }}
            </span> 
            <span class="badge badge-secondary bg-secondary text-white p-2" style="font-size: 0.9em; font-weight: 500;">
              {{ publication.year }}
            </span>
            
            {% if publication.keywords %}
              {% assign keywords = publication.keywords | split: "," %}
              {% for kw in keywords %}
                <span class="badge badge-light bg-light text-secondary border p-2 ml-1" style="font-size: 0.85em;">{{ kw | strip }}</span>
              {% endfor %}
            {% endif %}
          </div>
          
          <div class="mt-4 pt-3 border-top">
            {% if publication.link %}
              <a href="{{ publication.link }}" target="_blank" class="btn btn-danger btn-sm text-white mr-2 mt-2" style="border-radius: 5px;">
                <i class="fas fa-file-pdf mr-1"></i> PDF
              </a>
            {% endif %}
            
            {% if publication.website %}
              <a href="{{ publication.website }}" target="_blank" class="btn btn-info btn-sm text-white mr-2 mt-2" style="border-radius: 5px; background-color: #17a2b8;">
                <i class="fas fa-globe mr-1"></i> Website
              </a>
            {% endif %}
            
            {% if publication.code %}
              <a href="{{ publication.code }}" target="_blank" class="btn btn-dark btn-sm text-white mr-2 mt-2" style="border-radius: 5px;">
                <i class="fab fa-github mr-1"></i> Code
              </a>
            {% endif %}
            
            {% if publication.crates %}
              <a href="{{ publication.crates }}" target="_blank" class="btn btn-warning btn-sm text-dark mr-2 mt-2" style="border-radius: 5px; background-color: #f9c74f; border-color: #f9c74f;">
                <i class="fas fa-box-open mr-1"></i> crates.io
              </a>
            {% endif %}
            
            <!-- Support for any other arbitrary links! -->
            {% if publication.extra_links %}
              {% for extra in publication.extra_links %}
                <a href="{{ extra.url }}" target="_blank" class="btn btn-outline-primary btn-sm mr-2 mt-2" style="border-radius: 5px;">
                  <i class="{{ extra.icon | default: 'fas fa-external-link-alt' }} mr-1"></i> {{ extra.name }}
                </a>
              {% endfor %}
            {% endif %}
            
            <button class="btn btn-outline-secondary btn-sm mt-2" style="border-radius: 5px;" onclick="navigator.clipboard.writeText(window.location.protocol + '//' + window.location.host + window.location.pathname + '#{{ slug }}'); alert('Link copied to clipboard!');">
              <i class="fas fa-copy mr-1"></i> Copy Link
            </button>
          </div>
        </div>
        
        <!-- Video Column -->
        {% if publication.video %}
        <div class="col-md-5">
          <div class="embed-responsive embed-responsive-16by9 shadow-sm" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; border-radius: 10px;">
            <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" src="{{ publication.video }}" allowfullscreen></iframe>
          </div>
        </div>
        {% endif %}
        
      </div>
    </div>
  </div>
{% endfor %}
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const filterInputs = document.querySelectorAll('.filter-input');
  const pubCards = document.querySelectorAll('.pub-card');
  const authorDatalist = document.getElementById('author-list');

  // Dynamically populate Authors Datalist
  const allAuthors = new Set();

  pubCards.forEach(card => {
    const authorsStr = card.getAttribute('data-authors');
    if (authorsStr) {
      authorsStr.split(',').forEach(a => {
        const cleanlyTrimmed = a.trim();
        if(cleanlyTrimmed) allAuthors.add(cleanlyTrimmed);
      });
    }
  });

  // Inject Authors dynamically into the datalist for predictive text dropdowns
  [...allAuthors].sort().forEach(author => {
    const option = document.createElement('option');
    option.value = author;
    authorDatalist.appendChild(option);
  });

  function filterPublications() {
    const yearVal = document.getElementById('filter-year').value;
    const typeVal = document.getElementById('filter-type').value;
    const venueVal = document.getElementById('filter-venue').value;
    const threadVal = document.getElementById('filter-thread').value;
    const authorVal = document.getElementById('filter-author').value.toLowerCase().trim();

    pubCards.forEach(card => {
      const cYear = card.getAttribute('data-year');
      const cType = card.getAttribute('data-type');
      const cVenue = card.getAttribute('data-venue');
      const cThreads = card.getAttribute('data-threads');
      const cAuthors = card.getAttribute('data-authors').toLowerCase();
      const cKeywords = card.getAttribute('data-keywords').toLowerCase();

      const matchYear = (yearVal === 'all' || cYear === yearVal);
      const matchType = (typeVal === 'all' || cType === typeVal);
      const matchVenue = (venueVal === 'all' || cVenue === venueVal);
      
      let matchThread = true;
      if (threadVal !== 'all') {
        if (!cThreads) {
          matchThread = false;
        } else {
          matchThread = cThreads.split('|').map(s => s.trim()).includes(threadVal);
        }
      }
      
      let matchAuthor = true;
      if (authorVal !== '') {
        // String substring contains 
        matchAuthor = cAuthors.includes(authorVal);
      }

      if (matchYear && matchType && matchVenue && matchThread && matchAuthor) {
        card.style.display = '';
      } else {
        card.style.display = 'none';
      }
    });
  }

  // Attach execution listeners
  filterInputs.forEach(input => {
    input.addEventListener('change', filterPublications);
    if (input.type === 'text') {
      input.addEventListener('input', filterPublications);
    }
  });
});
</script>
