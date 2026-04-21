---
layout: home
title: APOLLO Lab
description: Applied Planning, Learning, and Optimization Lab @ Yale University
background: /assets/theme/images/homepage-background.png
permalink: /
---


<!-- Editorial Hero Welcome — elegant, no card -->
<div class="apollo-hero mt-4 mb-5">

  <!-- Hero image -->
  <div class="apollo-hero-image-wrap">
    <img src="{{ '/assets/theme/images/homepage-background.png' | relative_url }}" alt="APOLLO Lab" class="apollo-hero-img">
  </div>

  <!-- Top label -->
  <div class="apollo-hero-label">
    <span class="apollo-hero-line"></span>
    Yale University · Computer Science
    <span class="apollo-hero-line"></span>
  </div>

  <!-- Main statement -->
  <h2 class="apollo-hero-headline">
    Applied Planning, Learning, and Optimization (APOLLO) Lab
  </h2>

  <!-- Clean prose -->
  <div class="apollo-hero-prose">
    <p>
      We develop algorithms for <strong>fast planning, learning, and optimization</strong> that allow robots and autonomous agents to continuously adapt as they operate, tightly integrating perception, action, and learning so systems can react quickly, gather the right information, and improve in real-time.
    </p>
    <p>
      Our work is applied in <strong>home and assistive robotics</strong>, <strong>healthcare and robotic surgery</strong>, and <strong>disaster response</strong>.
    </p>
  </div>

</div>

<style>
/* ─── Apollo Editorial Hero ─────────────────────────────── */
.apollo-hero {
  padding: 0.75rem 0 3rem;
  text-align: center;
  position: relative;
}

/* Hero image */
.apollo-hero-image-wrap {
  margin-bottom: 2rem;
}

.apollo-hero-img {
  width: 100%;
  max-height: 300px;
  object-fit: cover;
  border-radius: 20px;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.10);
  display: block;
}

.apollo-hero-label {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 14px;
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: #64748b;
  margin-bottom: 1.75rem;
}

.apollo-hero-line {
  display: inline-block;
  height: 1px;
  width: 36px;
  background: linear-gradient(90deg, transparent, #94a3b8, transparent);
}

.apollo-hero-headline {
  font-size: clamp(1.4rem, 3.2vw, 2.2rem) !important;
  font-weight: 800 !important;
  letter-spacing: -0.03em !important;
  line-height: 1.2 !important;
  margin-bottom: 1.75rem !important;
  /* Gradient text */
  background: linear-gradient(120deg, #2563eb 0%, #6366f1 40%, #a855f7 70%, #3b82f6 100%);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  /* Entry + shimmer animation */
  animation: heroHeadlineIn 0.7s cubic-bezier(0.22, 1, 0.36, 1) both,
             heroShimmer 4s linear 0.7s infinite;
}

@keyframes heroHeadlineIn {
  from {
    opacity: 0;
    transform: translateY(18px);
    letter-spacing: 0.02em;
  }
  to {
    opacity: 1;
    transform: translateY(0);
    letter-spacing: -0.03em;
  }
}

@keyframes heroShimmer {
  0%   { background-position: 200% center; }
  100% { background-position:   0% center; }
}



/* Prose */
.apollo-hero-prose {
  max-width: 720px;
  margin: 0 auto;
  text-align: left;
  padding: 0 1rem;
  border-left: 3px solid #e2e8f0;
  padding-left: 1.5rem;
}

.apollo-hero-prose p {
  font-size: 1.05rem;
  line-height: 1.75;
  color: #475569;
  margin-bottom: 0.9rem;
}

.apollo-hero-prose p:last-child { margin-bottom: 0; }

.apollo-hero-prose strong {
  color: #1e293b;
  font-weight: 700;
}

@media (max-width: 576px) {
  .apollo-hero { padding: 1.5rem 0 2rem; }
  .apollo-hero-prose { border-left: none; padding-left: 0; text-align: center; }
}
/* ─────────────────────────────────────────────────────── */
</style>

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