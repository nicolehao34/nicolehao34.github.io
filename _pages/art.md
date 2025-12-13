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
  
  .art-item img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
  }
  
  .art-item img:hover {
    transform: scale(1.05);
  }
  
  .art-item h3 {
    margin-top: 1rem;
    font-size: 1.2rem;
    text-transform: capitalize;
  }
</style>

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
</div>