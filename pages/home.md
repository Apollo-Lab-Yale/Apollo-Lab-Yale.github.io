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
<h3 class="mt-5 mb-0 font-weight-bold" style="letter-spacing: -0.02em; color: #1e293b;">
  <i class="fas fa-flask text-primary me-2" style="font-size: 0.85em;"></i> Research Topics
</h3>

<!-- Dynamic Topic Header (Modern & Clean) -->
<div class="active-topic-meta mt-2 mb-4">
  <div class="d-flex align-items-center gap-3">
    <span class="badge bg-primary bg-opacity-10 text-primary px-2 py-1" style="font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.05em; font-weight: 800; border-radius: 4px;">Active Topic</span>
    <h4 id="apollo-active-topic-title" class="mb-0" style="font-size: 1.1rem; color: #475569; font-weight: 600; transition: opacity 0.3s ease;">Initializing...</h4>
  </div>
</div>

<style>
/* ─── Apollo Research Gallery Enhancements ──────────────── */
#home-research-gallery {
  border-radius: 20px;
  overflow: hidden;
  background-color: #f8fafc; 
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.05), 0 10px 10px -5px rgba(0, 0, 0, 0.02) !important;
  border: 1px solid rgba(0,0,0,0.03);
}

/* Enhanced Controls */
.apollo-gallery-control {
  width: 8% !important;
  opacity: 0.9;
  transition: all 0.3s ease;
}

.apollo-gallery-control:hover {
  opacity: 1;
  width: 9% !important;
}

.apollo-gallery-control-icon {
  background-color: rgba(15, 23, 42, 0.6) !important;
  background-size: 45% 45% !important;
  border-radius: 50% !important;
  width: 44px !important;
  height: 44px !important;
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  transition: all 0.2s cubic-bezier(0.34, 1.56, 0.64, 1);
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}

.apollo-gallery-control:hover .apollo-gallery-control-icon {
  transform: scale(1.1);
  background-color: rgba(15, 23, 42, 0.85) !important;
  box-shadow: 0 8px 16px rgba(0,0,0,0.3);
}

/* Responsive Scaling for Arrows */
@media (max-width: 992px) {
  .apollo-gallery-control { width: 12% !important; }
}

@media (max-width: 768px) {
  .apollo-gallery-control { width: 15% !important; }
  .apollo-gallery-control-icon { 
    width: 36px !important; 
    height: 36px !important; 
  }
}

/* Indicators Refinement */
.apollo-gallery-indicators {
  bottom: 1.25rem !important;
  margin-bottom: 0 !important;
}

.apollo-gallery-indicators button {
  width: 7px !important;
  height: 7px !important;
  border-radius: 50% !important;
  margin: 0 4px !important;
  background-color: #94a3b8 !important;
  border: none !important;
  opacity: 0.3 !important;
  transition: all 0.3s ease;
}

.apollo-gallery-indicators button.active {
  width: 20px !important;
  border-radius: 4px !important;
  background-color: #3b82f6 !important;
  opacity: 1 !important;
}
/* ────────────────────────────────────────────────────────── */
</style>

<div id="home-research-gallery" class="carousel slide" data-bs-ride="carousel" data-bs-pause="false">
  <!-- Indicators -->
  <div class="carousel-indicators apollo-gallery-indicators">
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
          <div class="carousel-item {% if active_set == false %}active{% assign active_set = true %}{% endif %}" style="height: 550px;" data-topic-title="{{ thread.title }}">
            {% if m.type == 'video' %}
            <video autoplay loop muted playsinline webkit-playsinline preload="auto" class="d-block mx-auto" style="object-fit: contain; width: 100%; height: 100%;">
              <source src="{{ m.src | relative_url }}" type="video/mp4">
            </video>
            {% else %}
            <img src="{{ m.src | relative_url }}" class="d-block mx-auto" style="object-fit: contain; width: 100%; height: 100%;" alt="{{ thread.title }}">
            {% endif %}
          </div>
        {% endfor %}
      {% endif %}
    {% endfor %}
  </div>
  
  <button class="carousel-control-prev apollo-gallery-control" type="button" data-bs-target="#home-research-gallery" data-bs-slide="prev">
    <span class="carousel-control-prev-icon apollo-gallery-control-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button class="carousel-control-next apollo-gallery-control" type="button" data-bs-target="#home-research-gallery" data-bs-slide="next">
    <span class="carousel-control-next-icon apollo-gallery-control-icon" aria-hidden="true"></span>
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

<!-- <iframe src="https://apollo-lab-yale.github.io/apollo-resources/" width="100%" height="500"></iframe> -->

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

  function updateActiveTitle($carousel) {
    const $activeItem = $carousel.find('.carousel-item.active');
    const title = $activeItem.data('topic-title');
    const $titleEl = $('#apollo-active-topic-title');
    
    // Smooth transition
    $titleEl.css('opacity', '0');
    setTimeout(() => {
      $titleEl.text(title);
      $titleEl.css('opacity', '1');
    }, 150);
  }

  function initializeIroncladWatchdog() {
    const $carousel = $('#home-research-gallery');
    const $videos = $('video[loop]');
    
    // 1. Carousel Lifecycle Sync (Video + Title)
    $carousel.on('slid.bs.carousel', function() {
      $(this).find('.carousel-item.active video').each(function() { forcePlay(this); });
      updateActiveTitle($(this));
    });

    // 2. Initial Title Set
    updateActiveTitle($carousel);

    // 3. Interaction Unlocker
    const unlocker = function() {
      $videos.each(function() { forcePlay(this); });
      $('body').off('click touchstart scroll', unlocker);
    };
    $('body').on('click touchstart scroll', unlocker);

    // 4. Persistence Heartbeat (Checks every 2s for browser-side pauses)
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