---
layout: archive
title: "Art"
permalink: /art/
author_profile: true
---

{% include base_path %}

<style>
  .art-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
  }
  
  .art-item {
    text-align: center;
  }
  
  /* Make horizontal images span 2 columns */
  .art-item.horizontal {
    grid-column: span 2;
  }
  
  .art-item img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
    max-height: 600px;
    object-fit: contain;
  }
  
  .art-item img:hover {
    transform: scale(1.05);
  }
  
  .art-item h3 {
    margin-top: 1rem;
    font-size: 1.2rem;
    text-transform: capitalize;
  }
  
  @media (max-width: 768px) {
    .art-item.horizontal {
      grid-column: span 1;
    }
  }
</style>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const artItems = document.querySelectorAll('.art-item img');
    artItems.forEach(img => {
      img.onload = function() {
        if (this.naturalWidth > this.naturalHeight) {
          this.parentElement.classList.add('horizontal');
        }
      };
      // Trigger for cached images
      if (img.complete) {
        img.onload();
      }
    });
  });
</script>

<div class="art-gallery">
  <div class="art-item">
    <img src="{{ base_path }}/images/art/alive.jpg" alt="Alive">
    <h3>Alive</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/chances.jpg" alt="Chances">
    <h3>Chances</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/cycle.jpg" alt="Cycle">
    <h3>Cycle</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/freedom.jpg" alt="Freedom">
    <h3>Freedom</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/Dream.jpeg" alt="Dream">
    <h3>Dream</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/Hero.jpeg" alt="Hero">
    <h3>Hero</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/Justice.jpeg" alt="Justice">
    <h3>Justice</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/StudyofCaravaggioDisposition.jpeg" alt="Study of Caravaggio Disposition">
    <h3>Study of Caravaggio's Deposition</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/TheManWhoSoldTheWorld.jpeg" alt="The Man Who Sold The World">
    <h3>The Man Who Sold The World</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/TheWheelOfKarma.jpeg" alt="The Wheel Of Karma">
    <h3>The Wheel Of Karma</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/TrustFall.jpeg" alt="Trust Fall">
    <h3>Trust Fall</h3>
  </div>
  
  <div class="art-item">
    <img src="{{ base_path }}/images/art/Water.jpeg" alt="Water">
    <h3>Water</h3>
  </div>
</div>