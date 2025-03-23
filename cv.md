---
layout: page
title: "CV"
permalink: /cv/
---

<!-- Include color palette -->
<link rel="stylesheet" href="D:\github\yavuzcodiin.github.io\_sass\gradient_colors.scss">
<link rel="stylesheet" href="D:\github\yavuzcodiin.github.io\_sass\base_colors.scss">
<link rel="stylesheet" type="text/css" href="_sass/cv.scss">
<!-- Include color palette -->

<div class="cv-container">
    <div class="cv-header">
        <h1 class="gradient-text_31">Yavuz Ertuğrul</h1>
        <p class="gradient-text_24">Robotics Software Engineer</p>
        <p class="gradient-text_4"> <a href="mailto:yavuz.coding@gmail.com">yavuz.coding@gmail.com</a></p>
        <p>
            <a href="https://www.linkedin.com/in/yavuz-ertuğrul123">LinkedIn</a> |
            <a href="https://www.yavuzertugrul.com/">Personal Website/Portfolio/Blog</a> |
            <a href="https://www.github.com/yavuzCodiin">GitHub</a> |
            <a href="https://linktr.ee/yavuzertugrul">All Other Links</a>
        </p>
    </div>

    <div class="cv-section">
        <h2 class="gradient-text_4">Skills</h2>
        <ul>
            <li>ROS/ROS2, Docker, Python, ML, Linux, Matplotlib, Scikit-learn, OOP, Bash Scripting, QT, Scrapy, Pandas, NumPy, Seaborn</li>
        </ul>
    </div>

    <div class="cv-section">
        <h2 class="gradient-text_4">Professional Experience</h2>
        <div class="typing-container">
            <h3 class="typing gradient-text_24">Robotics Software Engineer at Kindhelm (İstanbul, Turkey)</h3>
        </div>
        <p class="gradient-text_8"><i>July 2024 - Present</i></p>
        <ul>
            <li>Docker and Linux:</li>
            <br>
            <li>ROS/ROS2 Framework:</li>
            <br>
            <li>Jetson Orin NX and Sensor Integration:</li>
            <br>
            <li>Python Programming</li>
        </ul>
    </div>

    <div class="cv-section">
        <div class="typing-container">
            <h3 class="typing gradient-text_24">Robotics Software Engineer at NH Tech Robotics (Istanbul, Turkey)</h3>
        </div>
        <p class="gradient-text_8"><i>April 2024 - July 2024</i></p>
        <ul>
            <li>Robotics Development and Simulation: Design, develop, and simulate advanced robotic systems to enhance functionality and efficiency, ensuring reliability and performance through comprehensive testing in virtual environments using Rviz2 and Gazebo.</li>
            <br>
            <li>Docker and Linux: Utilize Docker for containerization to streamline development processes and ensure consistent environments across different stages of deployment, while leveraging Linux-based systems for robust and reliable operation of robotic applications.</li>
            <br>
            <li>ROS/ROS2 Framework: Implement and manage robot software using the Robot Operating System, enabling seamless communication between robotic components and systems. Develop ROS2 driver for IMU and use the Kalibr tool for camera-camera and camera-IMU temporal calibration (1 ms sync). ros1_bridge(ROS and ROS2 communication), used various Isaac ROS packages such as Isaac ROS Argus Camera, image_proc, and v4l2_camera.</li>
            <br>
            <li>Jetson Orin NX and Sensor Integration: Integrate NVIDIA Jetson Orin NX for AI-powered robotic applications, utilizing IMX477 and AR0234 cameras and IMU for precise calibration. Develop packages, custom conversion, and publishing nodes for AR0234 cameras, IMU, created stereo from mono vision system, and leveraged Isaac ROS Argus for enhanced image processing capabilities. I2C for communication with various sensors such as IMU.</li>
            <br>
            <li>Python Programming: Develop scripts and applications in Python for various robotic functionalities.</li>
        </ul>
        <div class="art-gallery-wrapper">
            <div class="art-gallery">
                <div class="art-item">
                    <img src="/images/experience_visual_library/nh_tech_robotics_job_1.jpg" alt="nh_tech_job_1" onclick="openLightbox('/images/experience_visual_library/nh_tech_robotics_job_1.jpg')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/nh_tech_robotics_job_2.jpg" alt="nh_tech_job_2" onclick="openLightbox('/images/experience_visual_library/nh_tech_robotics_job_2.jpg')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/nh_tech_robotics_job_3.jpg" alt="nh_tech_job_3" onclick="openLightbox('/images/experience_visual_library/nh_tech_robotics_job_3.jpg')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/nh_tech_robotics_job_4.jpg" alt="nh_tech_job_4" onclick="openLightbox('/images/experience_visual_library/nh_tech_robotics_job_4.jpg')">
                </div>
            </div>
            <button class="nav prev" onclick="moveGallery(this, -1)">&#10094;</button>
            <button class="nav next" onclick="moveGallery(this, 1)">&#10095;</button>
        </div>
    </div>


    <div class="cv-section">
        <div class="typing-container">
            <h3 class="typing gradient-text_24">Robotics Application Engineer at ACROME Robotics (Istanbul, Turkey)</h3>
        </div>
        <p class="gradient-text_8"><i>February 2023 - October 2023</i></p>
        <ul>
            <li>Responsible for product development & process of SMD (Smart Motor Driver) family. Our first R&D device which is a smart motor driver.</li>
            <br>
            <li>Responsible for GUI development with Python for SMD to manipulate, control, analyze, and observe our motors and to use specific applications (e.g., sync motor driving application).</li>
            <br>
            <li>Getting familiar with embedded-side protocols like RS-485, I2C, sensors, and control theory, etc.</li>
            <br>
            <li>Responsible for ROS & Python development/configuration of our products. Familiar with monolithic structure, refactoring, clean code, and keeping up to date with the embedded side, etc.</li>
            <br>
            <li>Worked with our mobile robot equipped with Lidar. Developed/experienced SLAM mapping, obstacle avoidance algorithms in real life.</li>
            <br>
            <li>Learned AWS environment to control/configure our physical mobile robot through our subsidiary company riders.ai's web-app, virtual robotic simulation environment. Developed a docker image using gzWeb, Eclipse Theia, and learned beginner-level Docker usage during the process.</li>
            <br>
            <li>Responsible for content side (user manual, growth marketing, design, analysis process), created how-to-use videos, wrote technical blog posts related to our products, especially with SMD.</li>
            <br>
        </ul>
        <table class="link-table">
            <tr>
                <td><a href="https://acrome.net/post/synchronizing-linear-motors-and-dc-motors">Synchronizing Linear Motors and DC Motors</a></td>
                <td><a href="https://acrome.net/post/essentials-of-building-a-mobile-robot-all-you-need-to-know">Essentials of Building a Mobile Robot: All You Need to Know</a></td>
                <td><a href="https://acrome.net/post/exploring-acromes-stewart-platform-capabilities-deliverables-and-usage">Exploring ACROME's Stewart Platform: Capabilities, Deliverables and Usage</a></td>
                <td><a href="https://acrome.net/post/applications-that-you-can-do-with-brushed-dc-motors">Applications That You Can Do With Brushed DC Motors</a></td>
            </tr>
            <tr>
                <td><a href="https://acrome.net/post/exploring-control-systems-and-stability-a-comprehensive-guide-to-ball-balancing-tables-and-bode-diagrams">Exploring Control Systems and Stability: A Comprehensive Guide to Ball Balancing Tables and Bode Diagrams</a></td>
                <td><a href="https://acrome.net/post/where-to-use-and-how-to-use-brushed-dc-motors">Where to and How to use Brushed DC Motors Drivers?</a></td>
                <td><a href="https://acrome.net/post/beginners-guide-to-actuators">Beginners Guide to Actuators</a></td>
                <td><a href="https://acrome.net/post/acrome-products-role-in-prof-claudia-yasars-teaching-approach">Acrome Products Role in Prof. Claudia Yaşar's Teaching Approach</a></td>
            </tr>
            <tr>
                <td><a href="https://acrome.net/post/from-gaming-to-engineering-joystick-control-of-stewart-platform">From Gaming to Engineering: Joystick Control of Stewart Platform</a></td>
                <td><a href="https://acrome.net/post/what-are-delta-robots-used-for">What Are Delta Robots Used For?</a></td>
                <td><a href="https://www.youtube.com/watch?v=bypRvJEKuLU&t=290s">ACROME SMD Tutorial Video</a></td>
                <td><a href="https://acrome.net/post/introduction-to-robotic-manipulators">Introduction to Robotic Manipulators</a></td>
            </tr>
        </table>
        <div class="art-gallery-wrapper">
            <div class="art-gallery">
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_1.png" alt="acrome_job_1" onclick="openLightbox('/images/experience_visual_library/acrome_job_1.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_2.png" alt="acrome_job_2" onclick="openLightbox('/images/experience_visual_library/acrome_job_2.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_3.jpg" alt="acrome_job_3" onclick="openLightbox('/images/experience_visual_library/acrome_job_3.jpg')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_4.png" alt="acrome_job_4" onclick="openLightbox('/images/experience_visual_library/acrome_job_4.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_5.png" alt="acrome_job_5" onclick="openLightbox('/images/experience_visual_library/acrome_job_5.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_6.png" alt="acrome_job_6" onclick="openLightbox('/images/experience_visual_library/acrome_job_6.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_7.png" alt="acrome_job_7" onclick="openLightbox('/images/experience_visual_library/acrome_job_7.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_job_8.png" alt="acrome_job_8" onclick="openLightbox('/images/experience_visual_library/acrome_job_8.png')">
                </div>
            </div>
            <button class="nav prev" onclick="moveGallery(this, -1)">&#10094;</button>
            <button class="nav next" onclick="moveGallery(this, 1)">&#10095;</button>
        </div>
    </div>

    <div class="cv-section">
        <div class="typing-container">
            <h3 class="typing gradient-text_24">Research & Development Intern at ACROME Robotics (Istanbul, Turkey)</h3>
        </div>
        <p class="gradient-text_8"><i>July 2022 - August 2022</i></p>
        <ul>
            <li>Worked with Stewart Pro 6-DOF parallel robot used for positioning and motion control in professional photography, quality assurance positioner, and calibration applications. Also worked with Delta Robot, a 3-DOF parallel robot used for pick & place, robotic surgery, harvesting, and welding.</li>
            <br>
            <li>Gained experience in image processing with OpenCV, inverse kinematics, Linux environment, connections and permissions, bash scripting, embedded software development, SSH, Acrome controller, Raspberry Pi, MyRIO devices, ROS framework, and Python.</li>
        </ul>
        <div class="art-gallery-wrapper">
            <div class="art-gallery">
                <div class="art-item">
                    <img src="/images/experience_visual_library/acrome_intern.png" alt="Stewart Pro" onclick="openLightbox('/images/experience_visual_library/acrome_intern.png')">
                </div>
            </div>
            <button class="nav prev" onclick="moveGallery(this, -1)">&#10094;</button>
            <button class="nav next" onclick="moveGallery(this, 1)">&#10095;</button>
        </div>
    </div>

    <div class="cv-section">
        <div class="typing-container">
            <h3 class="typing gradient-text_24">Robotics Intern at Inovasyon Mühendislik Ltd. Sti. (Eskisehir, Turkey)</h3>
        </div>
        <p class="gradient-text_8"><i>July 2021 - August 2021</i></p>
        <ul>
            <li>Developed embedded programming skills using ROS (Robot Operating System) framework, RViz, Gazebo, and Python, and learned Linux operating system and its distribution Ubuntu.</li>
            <br>
            <li>Programmed an obstacle avoidance robot using Python, ROS, and object-oriented structure.</li>
        </ul>
        <div class="art-gallery-wrapper">
            <div class="art-gallery">
                <div class="art-item">
                    <img src="/images/experience_visual_library/inovasyon_intern_1.png" alt="inovasyon_intern" onclick="openLightbox('/images/experience_visual_library/inovasyon_intern_1.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/inovasyon_intern_2.png" alt="inovasyon_intern_2" onclick="openLightbox('/images/experience_visual_library/inovasyon_intern_2.png')">
                </div>
            </div>
            <button class="nav prev" onclick="moveGallery(this, -1)">&#10094;</button>
            <button class="nav next" onclick="moveGallery(this, 1)">&#10095;</button>
        </div>
    </div>

    <div class="cv-section">
        <div class="typing-container">
            <h3 class="typing gradient-text_24">Developer Experiences and Evangelism Intern at Microsoft (Istanbul, Turkey)</h3>
        </div>
        <p class="gradient-text_8"><i>July 2017 - August 2017</i></p>
        <ul>
            <li>Responsible for creating a project using Microsoft technologies and services (e.g., Azure, Chatbot Framework, Cognitive Services).</li>
        </ul>
        <div class="art-gallery-wrapper">
            <div class="art-gallery">
                <div class="art-item">
                    <img src="/images/experience_visual_library/microsoft_intern_1.png" alt="microsoft_intern_1" onclick="openLightbox('/images/experience_visual_library/microsoft_intern_1.png')">
                </div>
                <div class="art-item">
                    <img src="/images/experience_visual_library/microsoft_intern_2.png" alt="microsoft_intern_2" onclick="openLightbox('/images/experience_visual_library/microsoft_intern_2.png')">
                </div>
            </div>
            <button class="nav prev" onclick="moveGallery(this, -1)">&#10094;</button>
            <button class="nav next" onclick="moveGallery(this, 1)">&#10095;</button>
        </div>
    </div>

    <div class="cv-section">
        <div class="typing-container">
            <h3 class="typing gradient-text_24">Tech Author at Dijitolog (product.blog) (Istanbul, Turkey)</h3>
        </div>
        <p class="gradient-text_8"><i>February 2017 - June 2017</i></p>
    </div>

    <div class="cv-section">
        <h2 class="gradient-text_4">Education</h2>
        <p><strong>BS Electrical and Electronics Engineering</strong></p>
        <p>Orta Doğu Teknik Üniversitesi (2023/July)</p>
    </div>

    <div class="cv-section">
        <h2 class="gradient-text_4">Honors and Awards</h2>
        <ul>
            <li>Honor Student of the Spring Semester of the Academic Year 2020-2021 at Orta Doğu Teknik Üniversitesi.</li>
        </ul>
    </div>

    <div class="cv-section">
        <h2 class="gradient-text_4">Voluntary Work</h2>
        <ul>
            <li>IEEE METU: Trainer, CS(Member), PES(Member), RAS(Chair), AESS(Chair).</li>
            <li>IEEEXtreme 11.0 Student Ambassador, Career and Management (Member).</li>
        </ul>
    </div>
</div>

<!-- Lightbox Container -->
<div id="lightbox" class="lightbox" onclick="closeLightbox()">
    <span class="close">&times;</span>
    <img class="lightbox-content" id="lightbox-img">
</div>

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

    function moveGallery(button, direction) {
        var galleryWrapper = button.closest('.art-gallery-wrapper');
        var gallery = galleryWrapper.querySelector('.art-gallery');
        var items = gallery.querySelectorAll('.art-item');
        var currentIndex = parseInt(gallery.getAttribute('data-current-index')) || 0;
        var itemWidth = items[0].offsetWidth + 20; // 20px for margin

        currentIndex += direction;
        if (currentIndex < 0) {
            currentIndex = items.length - 3; // Wrap around to the end
        } else if (currentIndex > items.length - 3) { // Wrap around to the start
            currentIndex = 0;
        }

        gallery.style.transform = `translateX(${-currentIndex * itemWidth}px)`;
        gallery.setAttribute('data-current-index', currentIndex);
    }

    window.moveGallery = moveGallery;

    // Hide navigation buttons if there are 3 or fewer items
    document.querySelectorAll('.art-gallery-wrapper').forEach(function(wrapper) {
        var items = wrapper.querySelectorAll('.art-item');
        if (items.length <= 3) {
            wrapper.querySelector('.nav.prev').style.display = 'none';
            wrapper.querySelector('.nav.next').style.display = 'none';
        }
    });
});
</script>
<script>
document.addEventListener("DOMContentLoaded", function() {
    var elements = document.querySelectorAll('.typing');
    var options = {
        root: null,
        rootMargin: '0px',
        threshold: 0.1
    };

    function typeWriter(element, text, i, callback) {
        if (i < text.length) {
            element.innerHTML += text.charAt(i);
            i++;
            setTimeout(function() {
                typeWriter(element, text, i, callback);
            }, 50);
        } else if (typeof callback == 'function') {
            callback();
        }
    }

    var observer = new IntersectionObserver(function(entries, observer) {
        entries.forEach(function(entry) {
            if (entry.isIntersecting) {
                var element = entry.target;
                var text = element.textContent;
                element.textContent = '';
                typeWriter(element, text, 0);
                observer.unobserve(element);
            }
        });
    }, options);

    elements.forEach(function(element) {
        observer.observe(element);
    });
});
</script>
