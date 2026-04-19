---
title: Research
permalink: /research/
---

<p class="lead mb-5 text-center px-4" style="font-size: 1.25rem; line-height: 1.7; color: #475569;">
  We are pursuing several research directions simultaneously in the lab. The following vignettes provide a snapshot of some of the key challenges we are addressing and the innovative solutions we are developing.
</p>

{% for thread in site.data.research %}
{% assign thread_idx = forloop.index %}
<div id="{{ thread.title | slugify }}" class="card border-0 mb-5" style="scroll-margin-top: 100px; border-radius: 16px; overflow: hidden; background: linear-gradient(135deg, #ffffff 0%, #f8fafc 100%); border-left: 5px solid #3b82f6 !important; box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);">
  <div class="card-body p-4 p-lg-5">
    
    <!-- Thread Title -->
    <h2 class="font-weight-bold mb-4" style="color: #1e293b; letter-spacing: -0.02em; border-bottom: 4px solid #3b82f6; padding-bottom: 0.75rem; display: inline-flex; align-items: center; gap: 15px;">
      <i class="{{ thread.icon }}" style="color: #3b82f6; font-size: 0.9em;"></i>
      {{ thread.title }}
      <a href="#{{ thread.title | slugify }}" class="ms-2" style="font-size: 0.6em; vertical-align: middle; color: #94a3b8; transition: color 0.2s ease; text-decoration: none;" 
            onmouseover="this.style.color='#3b82f6'" 
            onmouseout="this.style.color='#94a3b8'" 
            title="Link to this thread">
        <i class="fas fa-link"></i>
      </a>
    </h2>
    
    <div class="row mt-3">
      {% if thread.media and thread.media.size > 0 %}
        <!-- Dedicated Media Header Segment -->
        <div class="col-12 mb-5">
          
          {% if thread.media.size == 1 %}
            <!-- Single Media Formatter -->
            {% assign m = thread.media[0] %}
            {% if m.type == 'video' %}
              <div class="shadow-sm text-center" style="border-radius: 12px; overflow: hidden; background-color: #ffffff;">
                <video autoplay loop muted playsinline webkit-playsinline preload="auto" onended="this.play()" style="display: block; object-fit: contain; width: 100%; max-height: 550px;">
                  <source src="{{ m.src | relative_url }}" type="video/mp4">
                </video>
              </div>
            {% else %}
              <div class="shadow-sm text-center" style="border-radius: 12px; overflow: hidden; background-color: #ffffff;">
                <img src="{{ m.src | relative_url }}" class="img-fluid" style="width: 100%; height: 100%; max-height: 550px; object-fit: contain;" alt="{{ thread.title }}">
              </div>
            {% endif %}
            
          {% else %}
            <!-- Multi-Media Gallery Carousel -->
            <div id="carousel-thread-{{ thread_idx }}" class="carousel slide shadow-sm" data-bs-ride="carousel" data-bs-pause="false" style="border-radius: 12px; overflow: hidden; background-color: #ffffff;">
              
              <!-- Indicators -->
              <div class="carousel-indicators mb-2">
                {% for m in thread.media %}
                  <button type="button" data-bs-target="#carousel-thread-{{ thread_idx }}" data-bs-slide-to="{{ forloop.index0 }}" class="{% if forloop.first %}active{% endif %}" aria-current="true"></button>
                {% endfor %}
              </div>

              <!-- Gallery Items -->
              <div class="carousel-inner">
                {% for m in thread.media %}
                  <div class="carousel-item {% if forloop.first %}active{% endif %}" style="height: 550px;">
                    {% if m.type == 'video' %}
                      <video autoplay loop muted playsinline webkit-playsinline preload="auto" onended="this.play()" class="d-block mx-auto" style="object-fit: contain; width: 100%; height: 100%;">
                        <source src="{{ m.src | relative_url }}" type="video/mp4">
                      </video>
                    {% else %}
                      <img src="{{ m.src | relative_url }}" class="d-block mx-auto" style="object-fit: contain; width: 100%; height: 100%;" alt="Thread Gallery Image">
                    {% endif %}
                  </div>
                {% endfor %}
              </div>
              
              <!-- Interaction Controls -->
              <button class="carousel-control-prev" type="button" data-bs-target="#carousel-thread-{{ thread_idx }}" data-bs-slide="prev" style="background: none; width: 8%; border: none;">
                <span class="carousel-control-prev-icon" aria-hidden="true" style="filter: drop-shadow(0 2px 4px rgba(0,0,0,0.8)); opacity: 1 !important;"></span>
                <span class="visually-hidden">Previous</span>
              </button>
              <button class="carousel-control-next" type="button" data-bs-target="#carousel-thread-{{ thread_idx }}" data-bs-slide="next" style="background: none; width: 8%; border: none;">
                <span class="carousel-control-next-icon" aria-hidden="true" style="filter: drop-shadow(0 2px 4px rgba(0,0,0,0.8)); opacity: 1 !important;"></span>
                <span class="visually-hidden">Next</span>
              </button>
            </div>
          {% endif %}
        </div>
      {% endif %}
        
      <!-- Full Width Text Field and Selected Publications -->
      <div class="col-12">
        <div style="font-size: 1.15rem; line-height: 1.7; color: #334155;">
          {{ thread.content | markdownify | replace: '<img', '<img class="img-fluid rounded shadow-sm my-3" style="max-height:400px; display:block;"' }}
        </div>
        
        <!-- Case-Insensitive Explicit Selected Publications -->
        {% assign related_pubs = "" | split: "," %}
        {% if thread.selected_publications %}
          {% for selected_title in thread.selected_publications %}
            {% assign selected_title_down = selected_title | downcase %}
            {% for pub in site.data.publications %}
              {% assign pub_title_down = pub.title | downcase %}
              {% if pub_title_down == selected_title_down %}
                {% assign related_pubs = related_pubs | push: pub %}
                {% break %}
              {% endif %}
            {% endfor %}
          {% endfor %}
        {% endif %}
        
        {% if related_pubs.size > 0 %}
        <div class="mt-4 pt-4 border-top">
          <h4 class="font-weight-bold mb-3" style="color: #1e293b; font-size: 1.15rem;">
            <i class="fas fa-book-open text-primary me-2"></i> Selected publications
          </h4>
          <ul class="list-unstyled mb-0 ps-1">
            {% for pub in related_pubs %}
            {% assign pub_slug = pub.title | slugify %}
            <li class="mb-2">
              <a href="{{ '/publications/#' | append: pub_slug | relative_url }}" class="text-decoration-none" style="color: #3b82f6; font-weight: 500; transition: color 0.2s;" onmouseover="this.style.color='#2563eb';" onmouseout="this.style.color='#3b82f6';">
                <i class="fas fa-file-alt me-2 text-muted" style="font-size: 0.9em;"></i> {{ pub.title }}
              </a>
            </li>
            {% endfor %}
          </ul>
        </div>
        {% endif %}
        
      </div>
      
    </div>
  </div>
</div>
{% endfor %}

<script>
/**
 * Apollo Ironclad Video Watchdog
 */
(function($) {
  "use strict";

  function forcePlay(video) {
    if (video && video.paused) {
      video.play().catch(function() {});
    }
  }

  function initializeIroncladWatchdog() {
    const $videos = $('video[loop]');
    
    // Carousel Lifecycle Sync
    $('.carousel').on('slid.bs.carousel', function() {
      $(this).find('.carousel-item.active video').each(function() {
        forcePlay(this);
      });
    });

    // Interaction Unlocker
    const unlocker = function() {
      $videos.each(function() { forcePlay(this); });
      $('body').off('click touchstart scroll', unlocker);
    };
    $('body').on('click touchstart scroll', unlocker);

    // Persistence Heartbeat
    setInterval(function() {
      $videos.each(function() {
        if (this.paused && !this.seeking) {
          forcePlay(this);
        }
      });
    }, 2000);
    
    $videos.each(function() { forcePlay(this); });
  }

  $(document).ready(initializeIroncladWatchdog);

})(window.jQuery);
</script>