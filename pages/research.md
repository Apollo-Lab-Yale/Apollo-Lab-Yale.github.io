---
title: Research
permalink: /research/
---

<section class="research-mission" aria-labelledby="research-mission-title">
  <p class="agenda-eyebrow">Our research mission</p>
  <h2 id="research-mission-title">Robots that adapt while they work.</h2>
  <p>We develop the computational foundations for robots that can update their understanding, actions, and skills as the world changes.</p>
  <p>A robot working in an unfamiliar environment needs to gather useful information, revise its actions, and learn from what happens. Our research asks how to make those updates practical within the time and computation available during operation.</p>
  <p>We exploit geometry, reuse information across related computations, and learn efficiently from experience. These ideas connect our work in perception, planning, learning, and optimization.</p>
</section>

<nav class="agenda-jump-links" aria-label="Research questions">
  {% for group in site.data.research_agenda %}{% if group.kind == 'core' %}
    <a href="#{{ group.id }}">{{ group.label }} <span aria-hidden="true">&darr;</span></a>
  {% endif %}{% endfor %}
</nav>

<div class="research-scenario">
  <h3>One situation, three connected challenges</h3>
  <p>Imagine a robot reaching for an unfamiliar object as its surroundings change. It must build a useful model of the object, choose where to look, revise its motion, and use the outcome to improve its next attempt.</p>
  <p>Our projects address different parts of this process. Our longer-term goal is to bring these capabilities together so that better perception informs action, and experience improves both.</p>
</div>

{% for group in site.data.research_agenda %}
<section id="{{ group.id }}" class="research-agenda-section{% if group.kind != 'core' %} research-agenda-supporting{% endif %}" aria-labelledby="{{ group.id }}-title">
  <p class="agenda-eyebrow">{{ group.eyebrow }}</p>
  <h2 id="{{ group.id }}-title">{{ group.title }}</h2>
  <p class="agenda-question">{{ group.question }}</p>
  <div class="agenda-description">{{ group.description | markdownify }}</div>
  {% for project in group.projects %}
    {% include research_project.html %}
  {% endfor %}
</section>
{% endfor %}

<div class="research-next-step">
  <p>Explore the papers behind this agenda, or find out how to contribute.</p>
  <a class="btn btn-primary" href="{{ '/publications/' | relative_url }}">Browse publications</a>
  <a class="btn btn-outline-primary" href="{{ '/joining/' | relative_url }}">Join the lab</a>
</div>

<script>
// Preserve links from team profiles and bookmarks into the detailed project sections.
(function () {
  function revealLinkedProject() {
    let id;
    try { id = decodeURIComponent(window.location.hash.slice(1)); } catch (_) { return; }
    const target = document.getElementById(id);
    if (target && target.tagName === 'DETAILS') {
      target.open = true;
      requestAnimationFrame(function () { target.scrollIntoView({ block: 'start' }); });
    }
  }
  document.addEventListener('DOMContentLoaded', revealLinkedProject);
  window.addEventListener('hashchange', revealLinkedProject);
})();
</script>

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
