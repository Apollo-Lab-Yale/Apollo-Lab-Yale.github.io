---
layout: home
title: APOLLO Lab
description: Applied Planning, Learning, and Optimization Lab @ Yale University
background: /assets/theme/images/homepage-background.png
permalink: /
---


<div class="card elite-mesh-container shadow-sm border-0 mt-5 mb-5" style="border-radius: 24px; overflow: hidden;">
  <div class="card-body p-4 p-md-5" style="position: relative; z-index: 5;">
    <div class="row align-items-center">
      <div class="col-md-1 d-none d-md-flex justify-content-center">
        <!-- Modern Glass Accent Bar -->
        <div style="width: 6px; height: 140px; background: rgba(255, 255, 255, 0.4); backdrop-filter: blur(4px); border-radius: 10px; box-shadow: 0 0 15px rgba(255,255,255,0.2);"></div>
      </div>
      <div class="col-md-11">
        <h2 class="font-weight-bold mb-4" style="color: #ffffff; letter-spacing: -0.02em; text-shadow: 0 2px 10px rgba(0,0,0,0.2);">
          Welcome to the Applied Planning, Learning, and Optimization (<span style="color: #ffffff; font-weight: 900;">APOLLO</span>) Lab at Yale
        </h2>
        
        <!-- Glassmorphic Text Container for readability -->
        <div style="background: rgba(255, 255, 255, 0.05); backdrop-filter: blur(8px); padding: 1.5rem; border-radius: 16px; border: 1px solid rgba(255, 255, 255, 0.1);">
          <p style="font-size: 1.15rem; line-height: 1.7; color: rgba(255, 255, 255, 0.9);">
            Our lab is driven by the goal of enabling <strong>robots and learning systems to act and improve in real-time</strong>, directly within the dynamic, uncertain environments of the real world. We develop algorithms for fast optimization, planning, and control that allow systems to continuously update their behavior as they operate — tightly integrating perception, action, and learning so that robots can react quickly, gather the right information, and adapt their strategies on the fly.
          </p>
          <p style="font-size: 1.15rem; line-height: 1.7; color: rgba(255, 255, 255, 0.9); margin-bottom: 0;">
            Our work spans learning, geometry, and applied math, and is motivated by domains where real-time adaptability has meaningful societal impact: <strong>home and assistive robotics</strong>, where systems must operate safely alongside people; <strong>healthcare and robotic surgery</strong>, where precision and real-time feedback are essential; and <strong>disaster response</strong>, where robots must act under uncertainty with limited prior information.
          </p>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Dynamic Research Media Gallery -->
<h3 class="mt-5 mb-4 font-weight-bold" style="letter-spacing: -0.02em; padding-bottom: 0.5rem; border-bottom: 2px solid #e2e8f0; color: #1e293b;">
  <i class="fas fa-flask text-primary me-2" style="font-size: 0.85em;"></i> Research Topics
</h3>

<div id="home-research-gallery" class="carousel slide shadow border-0 mb-5 pb-0" data-bs-ride="carousel" data-bs-pause="false" style="border-radius: 16px; overflow: hidden; background-color: #ffffff;">
  <!-- Indicators -->
  <div class="carousel-indicators mb-2">
    {% assign idx = 0 %}
    {% for thread in site.data.research %}
      {% if thread.media %}
        {% for m in thread.media %}
          <button type="button" data-bs-target="#home-research-gallery" data-bs-slide-to="{{ idx }}" class="{% if idx == 0 %}active{% endif %}" aria-current="true"></button>
          {% assign idx = idx | plus: 1 %}
        {% endfor %}
      {% endif %}
    {% endfor %}
  </div>

  <!-- Gallery Items -->
  <div class="carousel-inner">
    {% assign active_set = false %}
    {% for thread in site.data.research %}
      {% if thread.media %}
        {% for m in thread.media %}
          <div class="carousel-item {% if active_set == false %}active{% assign active_set = true %}{% endif %}" style="height: 550px;">
            {% if m.type == 'video' %}
            <video autoplay loop muted playsinline webkit-playsinline preload="auto" class="d-block mx-auto" style="object-fit: contain; width: 100%; height: 100%;">
              <source src="{{ m.src | relative_url }}" type="video/mp4">
            </video>
            {% else %}
            <img src="{{ m.src | relative_url }}" class="d-block mx-auto" style="object-fit: contain; width: 100%; height: 100%;" alt="{{ thread.title }}">
            {% endif %}
            
            <!-- Thread Title Caption -->
            <div class="carousel-caption d-none d-md-block" style="background: linear-gradient(to top, rgba(255,255,255,0.95) 0%, rgba(255,255,255,0.7) 40%, transparent 100%); bottom: 0; left: 0; right: 0; padding-bottom: 2.5rem; padding-top: 3rem;">
              <h5 class="mb-0 font-weight-bold" style="letter-spacing: 0.02em; color: #3b82f6 !important; text-shadow: 0 1px 2px rgba(255,255,255,0.8);">{{ thread.title }}</h5>
            </div>
          </div>
        {% endfor %}
      {% endif %}
    {% endfor %}
  </div>
  
  <button class="carousel-control-prev" type="button" data-bs-target="#home-research-gallery" data-bs-slide="prev" style="background: none; width: 8%; border: none;">
    <span class="carousel-control-prev-icon" aria-hidden="true" style="filter: drop-shadow(0 2px 4px rgba(0,0,0,0.8)); opacity: 1 !important;"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#home-research-gallery" data-bs-slide="next" style="background: none; width: 8%; border: none;">
    <span class="carousel-control-next-icon" aria-hidden="true" style="filter: drop-shadow(0 2px 4px rgba(0,0,0,0.8)); opacity: 1 !important;"></span>
    <span class="visually-hidden">Next</span>
  </button>
</div>

<!-- Lab Space Section -->
<h3 class="mt-5 mb-4 font-weight-bold" style="letter-spacing: -0.02em; padding-bottom: 0.5rem; border-bottom: 2px solid #e2e8f0; color: #1e293b;">
  <i class="fas fa-building text-primary me-2" style="font-size: 0.85em;"></i> Lab Space
</h3>

<div class="shadow border-0 mb-5" style="border-radius: 16px; overflow: hidden; background-color: #ffffff; position: relative; z-index: 5; aspect-ratio: 16/9;">
  <video autoplay loop muted playsinline webkit-playsinline preload="metadata" onended="this.play()" class="d-block mx-auto" style="width: 100%; height: 100%; object-fit: cover; background-color: #000;">
    <source src="https://apollo-lab-yale.github.io/assets/theme/videos/IMG_4092.mp4" type="video/mp4">
    <source src="{{ '/assets/theme/videos/IMG_4092.mp4' | relative_url }}" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

# <iframe src="https://apollo-lab-yale.github.io/apollo-resources/" width="100%" height="500"></iframe>

<script>
/**
 * Apollo Ironclad Video Watchdog - Home Edition
 * Ensures background videos start playing and KEEP playing.
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
    
    // 1. Carousel Lifecycle Sync
    $('.carousel').on('slid.bs.carousel', function() {
      $(this).find('.carousel-item.active video').each(function() { forcePlay(this); });
    });

    // 2. Interaction Unlocker
    const unlocker = function() {
      $videos.each(function() { forcePlay(this); });
      $('body').off('click touchstart scroll', unlocker);
    };
    $('body').on('click touchstart scroll', unlocker);

    // 3. Persistence Heartbeat (Checks every 2s for browser-side pauses)
    setInterval(function() {
      $videos.each(function() {
        if (this.paused && !this.seeking) {
          forcePlay(this);
        }
      });
    }, 2000);

    // Initial Trigger
    setTimeout(function() { $videos.each(function() { forcePlay(this); }); }, 300);
  }

  $(document).ready(initializeIroncladWatchdog);

})(window.jQuery);
</script>