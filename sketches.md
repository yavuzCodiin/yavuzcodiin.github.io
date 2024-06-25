---
layout: page
title: Digital Art
permalink: /sketches/
---

<!-- Include color palette -->
<link rel="stylesheet" href="D:\github\yavuzcodiin.github.io\_sass\gradient_colors.scss">
<link rel="stylesheet" href="D:\github\yavuzcodiin.github.io\_sass\base_colors.scss">
<!-- Include color palette -->

<p class="gradient-text_8">To see original size click on the image</p>

<div class="art-gallery">
    <div class="art-item"><img src="/images/sketch-library/altair.png" alt="Altair" onclick="openLightbox('/images/sketch-library/altair.png')"></div>
    <div class="art-item"><img src="/images/sketch-library/baby_yoda.jpg" alt="Baby Yoda" onclick="openLightbox('/images/sketch-library/baby_yoda.jpg')"></div>
    <div class="art-item"><img src="/images/sketch-library/bd-1.png" alt="BD-1" onclick="openLightbox('/images/sketch-library/bd-1.png')"></div>
    <div class="art-item"><img src="/images/sketch-library/muppet.jpg" alt="Muppet" onclick="openLightbox('/images/sketch-library/muppet.jpg')"></div>
    <div class="art-item"><img src="/images/sketch-library/pink_panther.jpg" alt="Pink Panther" onclick="openLightbox('/images/sketch-library/pink_panther.jpg')"></div>
    <div class="art-item"><img src="/images/sketch-library/pixel_dream.jpg" alt="Pixel Dream" onclick="openLightbox('/images/sketch-library/pixel_dream.jpg')"></div>
    <div class="art-item"><img src="/images/sketch-library/city.jpg" alt="Pixel Dream" onclick="openLightbox('/images/sketch-library/city.jpg')"></div>
    <div class="art-item"><img src="/images/sketch-library/creepy_lion.jpg" alt="Pixel Dream" onclick="openLightbox('/images/sketch-library/creepy_lion.jpg')"></div>
    <div class="art-item"><img src="/images/sketch-library/pixel_drone.jpeg" alt="Pixel Drone" onclick="openLightbox('/images/sketch-library/pixel_drone.jpeg')"></div>
    <div class="art-item"><img src="/images/sketch-library/pixel_jungle.jpeg" alt="Pixel Jungle" onclick="openLightbox('/images/sketch-library/pixel_jungle.jpeg')"></div>
    <div class="art-item"><img src="/images/sketch-library/pixel_cube.jpeg" alt="Pixel Cube" onclick="openLightbox('/images/sketch-library/pixel_cube.jpeg')"></div>
    <div class="art-item"><img src="/images/sketch-library/beach.png" alt="Beach" onclick="openLightbox('/images/sketch-library/beach.png')"></div>
    <div class="art-item"><img src="/images/sketch-library/last_dance.png" alt="Last Dance" onclick="openLightbox('/images/sketch-library/last_dance.png')"></div>
    <div class="art-item"><img src="/images/sketch-library/random_thoughts.png" alt="Random Thoughts" onclick="openLightbox('/images/sketch-library/random_thoughts.png')"></div>
    <div class="art-item"><img src="/images/sketch-library/blue_knight.png" alt="Blue Knight" onclick="openLightbox('/images/sketch-library/blue_knight.png')"></div>
    <div class="art-item"><img src="/images/sketch-library/back_to_black.png" alt="Back to Black" onclick="openLightbox('/images/sketch-library/back_to_black.png')"></div>
    <div class="art-item"><img src="/images/sketch-library/bbgd.png" alt="BBGD" onclick="openLightbox('/images/sketch-library/bbgd.png')"></div>

</div>

<!-- Lightbox Container -->
<div id="lightbox" class="lightbox" onclick="closeLightbox()">
    <span class="close">&times;</span>
    <img class="lightbox-content" id="lightbox-img">
</div>

<style>
.art-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); /* Increased minmax value to make images larger */
    gap: 10px;
    max-width: 100%;
    padding: 10px;
    box-sizing: border-box;
}

.art-item {
    position: relative;
    overflow: hidden;
    background-color: #000;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-top: 100%; /* This creates a square container */
}

.art-item img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover; /* Ensures the image covers the container */
    cursor: pointer;
}

/* Lightbox styles */
.lightbox {
    display: none; /* Hidden by default */
    position: fixed;
    z-index: 1000;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(0,0,0,0.9);
    justify-content: center;
    align-items: center;
}

.lightbox-content {
    max-width: 90%;
    max-height: 90%;
}

.close {
    position: absolute;
    top: 10px;
    right: 25px;
    color: #fff;
    font-size: 35px;
    font-weight: bold;
    transition: 0.3s;
}

.close:hover,
.close:focus {
    color: #bbb;
    text-decoration: none;
    cursor: pointer;
}
</style>

<script>
document.addEventListener("DOMContentLoaded", function() {
    var lightbox = document.getElementById('lightbox');
    var lightboxImg = document.getElementById('lightbox-img');

    function openLightbox(src) {
        lightbox.style.display = 'flex';  // Show the lightbox
        lightboxImg.src = src;
    }

    function closeLightbox() {
        lightbox.style.display = 'none';  // Hide the lightbox
    }

    window.openLightbox = openLightbox;
    window.closeLightbox = closeLightbox;

    // Ensure the lightbox is hidden on page load
    closeLightbox();
});
</script>
