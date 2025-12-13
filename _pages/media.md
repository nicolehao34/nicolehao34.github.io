---
layout: archive
title: "Media"
permalink: /media/
author_profile: true
---

{% include base_path %}

<style>
  .media-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
  }
  
  .media-item {
    text-align: center;
  }
  
  .media-item a {
    display: block;
    text-decoration: none;
  }
  
  .media-item img {
    width: 100%;
    height: 250px;
    object-fit: cover;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
  }
  
  .media-item img:hover {
    transform: scale(1.05);
  }
  
  .media-item h3 {
    margin-top: 1rem;
    font-size: 1.1rem;
    color: #333;
  }
</style>

<div class="media-gallery">
  <div class="media-item">
    <a href="https://as.cornell.edu/news/nexus-scholar-alumni-profile-nicole-hao-24-meng-25" target="_blank">
      <img src="https://as.cornell.edu/sites/default/files/styles/4_5/public/2025-11/nicole-hao-headshotsmaller.jpg" alt="Nexus Scholar Alumni Profile">
      <h3>Nexus Scholar Alumni Profile: Nicole Hao '24, MEng '25</h3>
    </a>
  </div>
  
  <div class="media-item">
    <a href="https://scl.cornell.edu/news-events/news/program-house-spotlight-hilc" target="_blank">
      <img src="https://scl.cornell.edu/sites/scl/files/inline-images/HILCStudentSpotlight_20241113_dm927_0375_1.jpg" alt="Program House Spotlight HILC">
      <h3>Program House Spotlight: Holland International Living Center</h3>
    </a>
  </div>
  
  <div class="media-item">
    <a href="https://as.cornell.edu/news/nexus-scholar-applications-open-summer-2023" target="_blank">
      <img src="https://as.cornell.edu/sites/default/files/styles/4_5/public/2022-11/nicolenexusphotoweb.jpg" alt="Nexus Scholar Applications">
      <h3>Nexus Scholar Applications Open for Summer 2023</h3>
    </a>
  </div>
  
  <div class="media-item">
    <a href="https://eship.cornell.edu/elab-welcomes-24-student-startup-teams-to-fall-cohort/" target="_blank">
      <img src="{{ base_path }}/images/elab-cohort-2024.jpg" alt="eLab Student Startup Teams">
      <h3>eLab Welcomes 24 Student Startup Teams to Fall Cohort - InkSight Featured</h3>
    </a>
  </div>
  
  <div class="media-item">
    <a href="https://alumni.cornell.edu/snack-bar/building-partnerships-in-and-outside-the-classroom/" target="_blank">
      <img src="https://scl.cornell.edu/sites/scl/files/inline-images/HILCStudentSpotlight_20241113_dm927_0500-Enhanced-NR.jpg" alt="Building Partnerships">
      <h3>Building Partnerships In and Outside the Classroom - HILC Featured</h3>
    </a>
  </div>
</div>
