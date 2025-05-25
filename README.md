<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="icon" href="images/online-resume.png" type="image/png">
    <title>My Portfolio</title>
    <link
      href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.0/css/bootstrap.min.css"
      rel="stylesheet"
    />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
    />
    <link
      href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Roboto:wght@400;500;700&display=swap"
      rel="stylesheet"
    />
    <style>
      :root {
        --primary-color: #e50914; /* Netflix red */
        --secondary-color: #b20710; /* Darker red for hover */
        --dark-color: #141414; /* Netflix dark background */
        --light-color: #ffffff; /* White for text */
        --accent-color: #6c63ff; /* Original primary color as accent */
        --text-color: #ffffff;
        --bg-color: #141414;
        --card-bg: #181818; /* Netflix card background */
        --section-bg-light: #1c1c1c;
        --section-bg-dark: #141414;
        --navbar-bg: rgba(20, 20, 20, 0.9);
        --footer-bg: #0f0f0f;
      }

      [data-theme="light"] {
        --text-color: #141414;
        --bg-color: #ffffff;
        --card-bg: #f5f5f5;
        --section-bg-light: #f0f0f0;
        --section-bg-dark: #ffffff;
        --navbar-bg: rgba(255, 255, 255, 0.95);
        --footer-bg: #f0f0f0;
        --primary-color: #e50914; /* Keep Netflix red */
        --secondary-color: #b20710;
        --light-color: #141414; /* Dark text for light mode */
      }

      [data-theme="dark"] {
        --text-color: #ffffff;
        --bg-color: #141414;
        --card-bg: #181818;
        --section-bg-light: #1c1c1c;
        --section-bg-dark: #141414;
        --navbar-bg: rgba(20, 20, 20, 0.9);
        --footer-bg: #0f0f0f;
      }

      body {
        font-family: "Roboto", sans-serif;
        position: relative;
        min-height: 100vh;
        color: var(--text-color);
        background-color: var(--bg-color);
        transition: background-color 0.3s ease, color 0.3s ease;
      }

      h1, h2, h3, h4, h5, h6 {
        font-family: "Bebas Neue", sans-serif;
        text-transform: uppercase;
      }

      /* Netflix Animations */
      @keyframes slideInLeft {
        0% { transform: translateX(-100%); opacity: 0; }
        100% { transform: translateX(0); opacity: 1; }
      }

      @keyframes slideInRight {
        0% { transform: translateX(100%); opacity: 0; }
        100% { transform: translateX(0); opacity: 1; }
      }

      @keyframes contentFadeIn {
        0% { opacity: 0; filter: blur(5px); }
        100% { opacity: 1; filter: blur(0); }
      }

      @keyframes shimmer {
        0% { background-position: -200%; }
        100% { background-position: 200%; }
      }

      @keyframes pulse {
        0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(229, 9, 20, 0.7); }
        50% { transform: scale(1.05); box-shadow: 0 0 20px 10px rgba(229, 9, 20, 0); }
        100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(229, 9, 20, 0); }
      }

      .slide-in-left {
        opacity: 0;
        transform: translateX(-100%);
        animation: slideInLeft 0.6s ease-out forwards;
      }

      .slide-in-right {
        opacity: 0;
        transform: translateX(100%);
        animation: slideInRight 0.6s ease-out forwards;
      }

      .content-fade-in {
        opacity: 0;
        animation: contentFadeIn 1s ease-out forwards;
      }

      .shimmer-effect {
        position: relative;
        overflow: hidden;
      }

      .shimmer-effect:hover::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(
          90deg,
          transparent,
          rgba(255, 255, 255, 0.2),
          transparent
        );
        background-size: 200%;
        animation: shimmer 1.5s linear;
        pointer-events: none;
      }

      /* Navigation */
      .navbar {
        background-color: var(--navbar-bg);
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        transition: all 0.3s ease;
      }

      .navbar.scrolled {
        padding: 5px 0;
      }

      .navbar-brand {
        font-weight: 700;
        color: var(--primary-color) !important;
        font-family: "Bebas Neue", sans-serif;
        font-size: 1.8rem;
      }

      .nav-link {
        font-weight: 500;
        margin: 0 10px;
        position: relative;
        color: var(--text-color) !important;
        font-family: "Bebas Neue", sans-serif;
        font-size: 1.1rem;
      }

      .nav-link:after {
        content: "";
        position: absolute;
        width: 0;
        height: 2px;
        background-color: var(--primary-color);
        bottom: -2px;
        left: 0;
        transition: width 0.3s ease;
      }

      .nav-link:hover:after {
        width: 100%;
      }

      .theme-toggle {
        cursor: pointer;
        font-size: 1.2rem;
        color: var(--primary-color);
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100%;
      }

      .navbar-nav .nav-item {
        display: flex;
        align-items: center;
      }

      /* Hero Section */
      #hero {
        height: 100vh;
        display: flex;
        align-items: center;
        position: relative;
        background: linear-gradient(to bottom, var(--section-bg-dark), var(--section-bg-light));
        overflow: hidden;
      }

      .hero-text h1 {
        font-size: 3.5rem;
        line-height: 1.2;
        white-space: normal;
      }

      .hero-text .typed-text {
        display: inline-block;
        white-space: normal;
        word-break: break-word;
        color: var(--primary-color);
        font-weight: 600;
      }

      .hero-image img {
        border: 2px solid var(--primary-color);
        box-shadow: 0 0 10px rgba(229, 9, 20, 0.5);
      }

      .hero-btns .btn {
        margin-right: 15px;
        padding: 10px 25px;
        border-radius: 50px;
        transition: all 0.3s ease;
        background: var(--primary-color);
        border: none;
        color: #ffffff;
        animation: pulse 2s infinite;
      }

      .hero-btns .btn:hover {
        background: var(--secondary-color);
        transform: translateY(-3px);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.7);
        animation: none;
      }

      .btn-outline-primary {
        border-color: var(--primary-color);
        color: var(--primary-color);
      }

      .btn-outline-primary:hover {
        background-color: var(--primary-color);
        color: #ffffff;
        transform: translateY(-3px);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.7);
        animation: none;
      }

      /* Section Styling */
      .section-title {
        position: relative;
        margin-bottom: 50px;
      }

      .section-title h2 {
        font-weight: 700;
        display: inline-block;
        position: relative;
        margin-bottom: 20px;
        color: var(--text-color);
        font-size: 2.5rem;
      }

      .section-title h2:after {
        content: "";
        position: absolute;
        width: 50%;
        height: 3px;
        background: linear-gradient(to right, var(--primary-color), transparent);
        bottom: -10px;
        left: 0;
      }

      .section-title p {
        color: var(--text-color);
        opacity: 0.7;
      }

      /* About Section */
      #about {
        padding: 100px 0;
        background-color: var(--bg-color);
      }

      .about-img img {
        border: 2px solid var(--primary-color);
        box-shadow: 0 0 10px rgba(229, 9, 20, 0.5);
      }

      .skill-item {
        margin-bottom: 15px;
      }

      .skill-name {
        font-weight: 600;
        margin-bottom: 5px;
        color: var(--text-color);
      }

      .skill-bar {
        height: 10px;
        background-color: #333;
        border-radius: 5px;
        overflow: hidden;
      }

      [data-theme="light"] .skill-bar {
        background-color: #d0d0d0;
      }

      .skill-progress {
        background-color: var(--primary-color);
        height: 100%;
        border-radius: 5px;
        transition: width 1.5s ease;
      }

      /* Coding Skills Section */
      #coding-skills {
        padding: 100px 0;
        background-color: var(--bg-color);
      }

      .platform-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 20px;
        justify-items: center;
      }

      .platform-card {
        width: 100%;
        max-width: 400px;
        background: var(--card-bg);
        border-radius: 8px;
        padding: 20px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        text-align: center;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        box-sizing: border-box;
        position: relative;
        overflow: hidden;
      }

      .platform-card:hover .overlay {
        opacity: 1;
      }

      .platform-card a {
        animation: pulse 2s infinite;
      }

      /* Education Section */
      #education {
        padding: 100px 0;
        background-color: var(--section-bg-light);
      }

      .education-item {
        padding: 20px;
        border-left: 3px solid var(--primary-color);
        position: relative;
        margin-bottom: 30px;
        background-color: var(--card-bg);
        border-radius: 8px;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        transition: transform 0.3s ease, box-shadow 0.3s ease;
      }

      .education-item:hover {
        transform: scale(1.05);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.5);
      }

      [data-theme="light"] .education-item:hover {
        box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
      }

      .education-item::before {
        content: "";
        position: absolute;
        width: 15px;
        height: 15px;
        background-color: var(--primary-color);
        border-radius: 50%;
        left: -9px;
        top: 20px;
      }

      .education-item h4, .education-item p {
        color: var(--text-color);
      }

      .education-item .year {
        font-style: italic;
        color: var(--primary-color);
      }

      /* Services Section */
      #services {
        padding: 100px 0;
        background-color: var(--section-bg-light);
      }

      .service-box {
        padding: 40px 30px;
        border-radius: 8px;
        background-color: var(--card-bg);
        box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
        transition: all 0.3s ease;
        margin: 30px 15px;
        height: 100%;
      }

      .service-box:hover {
        transform: scale(1.05);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.5);
      }

      [data-theme="light"] .service-box:hover {
        box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
      }

      .service-icon {
        width: 70px;
        height: 70px;
        background-color: var(--primary-color);
        color: white;
        border-radius: 50%;
        font-size: 24px;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 20px;
      }

      .service-box h4, .service-box p {
        color: var(--text-color);
      }

      .typed-text-1, .typed-text-2, .typed-text-3 {
        color: var(--primary-color) !important;
      }

      /* Portfolio Section */
      #portfolio {
        padding: 100px 0;
        background-color: var(--bg-color);
      }

      .portfolio-filter {
        margin-bottom: 30px;
      }

      .filter-btn {
        border: none;
        background-color: transparent;
        font-weight: 500;
        padding: 8px 15px;
        margin: 0 5px;
        cursor: pointer;
        transition: all 0.3s ease;
        border-radius: 5px;
        color: var(--text-color);
        font-family: "Bebas Neue", sans-serif;
      }

      .filter-btn.active, .filter-btn:hover {
        background-color: var(--primary-color);
        color: white;
      }

      .portfolio-item {
        margin-bottom: 30px;
        position: relative;
        overflow: hidden;
        border-radius: 8px;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
      }

      .portfolio-img {
        transition: all 0.4s ease;
      }

      .portfolio-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(to top, rgba(0, 0, 0, 0.7), transparent);
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        opacity: 0;
        transition: all 0.4s ease;
      }

      [data-theme="light"] .portfolio-overlay {
        background: linear-gradient(to top, rgba(255, 255, 255, 0.7), transparent);
      }

      .portfolio-item:hover .portfolio-overlay {
        opacity: 1;
      }

      .portfolio-item:hover .portfolio-img {
        transform: scale(1.1);
      }

      .portfolio-overlay h4, .portfolio-overlay p {
        color: var(--light-color);
        transform: translateY(20px);
        transition: all 0.4s ease;
      }

      .portfolio-item:hover .portfolio-overlay h4,
      .portfolio-item:hover .portfolio-overlay p {
        transform: translateY(0);
      }

      .portfolio-overlay .btn {
        background: var(--primary-color);
        color: white;
        border: none;
        border-radius: 5px;
        animation: pulse 2s infinite;
      }

      .portfolio-overlay .btn:hover {
        background: var(--secondary-color);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.7);
        animation: none;
      }

      /* Testimonials */
      #testimonials {
        padding: 100px 0;
        background-color: var(--section-bg-light);
      }

      .testimonial-item {
        padding: 30px;
        background-color: var(--card-bg);
        border-radius: 8px;
        box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
        position: relative;
        margin-top: 40px;
        margin-bottom: 20px;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
      }

      .testimonial-item:hover {
        transform: scale(1.05);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.5);
      }

      [data-theme="light"] .testimonial-item:hover {
        box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
      }

      .testimonial-img {
        width: 80px;
        height: 80px;
        border-radius: 50%;
        overflow: hidden;
        position: absolute;
        top: -40px;
        left: 30px;
        border: 5px solid var(--card-bg);
        box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
      }

      .testimonial-text, .testimonial-position {
        color: var(--text-color);
      }

      .testimonial-name {
        font-weight: 600;
        color: var(--primary-color);
      }

      .typed-text-4, .typed-text-5, .typed-text-6 {
        color: var(--primary-color) !important;
      }

      /* Contact Section */
      #contact {
        padding: 100px 0;
        background-color: var(--bg-color);
      }

      .contact-info {
        margin-bottom: 20px;
      }

      .contact-icon {
        width: 50px;
        height: 50px;
        background-color: var(--primary-color);
        color: white;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 18px;
        margin-right: 15px;
      }

      .contact-info h5, .contact-info p {
        color: var(--text-color);
      }

      .contact-form .form-control {
        padding: 12px 15px;
        border-radius: 5px;
        margin-bottom: 20px;
        border: 1px solid var(--primary-color);
        background-color: var(--card-bg);
        color: var(--text-color);
        transition: all 0.3s ease;
      }

      .contact-form .form-control:focus {
        box-shadow: 0 0 10px rgba(229, 9, 20, 0.5);
        border-color: var(--primary-color);
      }

      [data-theme="light"] .contact-form .form-control:focus {
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
      }

      .contact-form .btn {
        background: var(--primary-color);
        color: white;
        border-radius: 5px;
        animation: pulse 2s infinite;
      }

      .contact-form .btn:hover {
        background: var(--secondary-color);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.7);
        animation: none;
      }

      /* Footer */
      footer {
        background-color: var(--footer-bg);
        padding: 30px 0;
        color: var(--text-color);
      }

      .social-links a {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        background-color: rgba(0, 0, 0, 0.1);
        display: inline-flex;
        align-items: center;
        justify-content: center;
        color: var(--text-color);
        margin: 0 5px;
        transition: all 0.3s ease;
      }

      [data-theme="light"] .social-links a {
        background-color: rgba(0, 0, 0, 0.05);
      }

      .social-links a:hover {
        background-color: var(--primary-color);
        transform: translateY(-3px);
        box-shadow: 0 0 15px rgba(229, 9, 20, 0.7);
      }

      [data-theme="light"] .social-links a:hover {
        box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
      }

      /* Back to top button */
      .back-to-top {
        position: fixed;
        bottom: 30px;
        right: 30px;
        width: 50px;
        height: 50px;
        background-color: var(--primary-color);
        color: white;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 24px;
        z-index: 99;
        box-shadow: 0 5px 20px rgba(229, 9, 20, 0.4);
        cursor: pointer;
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease;
        animation: pulse 2s infinite;
      }

      .back-to-top.active {
        opacity: 1;
        visibility: visible;
      }

      /* Preloader */
      .preloader {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: var(--bg-color);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000;
        transition: all 0.5s ease;
      }

      .preloader.loaded {
        opacity: 0;
        visibility: hidden;
      }

      .spinner {
        width: 40px;
        height: 40px;
        border: 4px solid var(--text-color);
        border-top: 4px solid var(--primary-color);
        border-radius: 50%;
        animation: spin 1s linear infinite;
      }

      @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
      }

      /* Responsive adjustments */
      @media (max-width: 991px) {
        .navbar-collapse {
          background-color: var(--navbar-bg);
          padding: 15px;
          border-radius: 5px;
          box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
          margin-top: 15px;
        }

        #hero {
          height: auto;
          padding: 100px 0;
        }

        .hero-image {
          margin-top: 50px;
        }

        .portfolio-filter {
          overflow-x: auto;
          white-space: nowrap;
          padding-bottom: 15px;
        }
      }

      @media (max-width: 767px) {
        .hero-text h1 {
          font-size: 2rem;
        }

        .hero-text .typed-text {
          font-size: 1.8rem;
        }

        .section-title h2 {
          font-size: 1.8rem;
        }

        .about-img {
          margin-bottom: 30px;
        }

        .contact-info {
          margin-bottom: 40px;
        }

        .service-box, .platform-card {
          margin-left: 0;
          margin-right: 0;
        }

        .platform-grid {
          grid-template-columns: 1fr; /* Single column on mobile */
        }

        .platform-card {
          max-width: 100%;
        }

        .platform-card[onmousemove], .hero-image img[onmousemove], .about-img img[onmousemove] {
          transform: none !important;
          box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2) !important;
          filter: none !important;
        }

        .platform-card:hover, .service-box:hover, .education-item:hover, .testimonial-item:hover {
          transform: scale(1.02);
        }

        .shimmer-effect:hover::before {
          animation: none; /* Disable shimmer on mobile */
        }
      }

      @media (max-width: 576px) {
        .hero-text h1 {
          font-size: 1.8rem;
        }

        .hero-text .typed-text {
          font-size: 1.6rem;
        }
      }
    </style>
  </head>
  <body>
    <!-- Preloader -->
    <div class="preloader">
      <div class="spinner"></div>
    </div>

    <!-- Navigation -->
    <nav class="navbar navbar-expand-lg navbar-light fixed-top">
      <div class="container">
        <a class="navbar-brand" href="#">Portfolio</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <a class="nav-link" href="#hero">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#about">About</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#coding-skills">Coding Skills</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="https://10fingersfasttyping.netlify.app/">Typing</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#education">Education</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#services">Services</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#portfolio">Portfolio</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#testimonials">Experience</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#contact">Contact</a>
            </li>
            <li class="nav-item">
              <i class="fas fa-moon theme-toggle" id="theme-toggle"></i>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="hero" class="content-fade-in">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-6 hero-text slide-in-left">
            <h1 class="mb-4">
              Hello, I'm <span class="typed-text"></span>
            </h1>
            <p class="lead mb-4">
              A passionate developer creating stunning web experiences with a
              focus on design and functionality.
            </p>
            <div class="hero-btns">
              <a href="#portfolio" class="btn btn-primary">View My Work</a>
              <a href="#contact" class="btn btn-outline-primary">Contact Me</a>
            </div>
          </div>
          <div class="col-lg-6 hero-image slide-in-right">
            <img
              src="/images/IMG_0015 2.png"
              alt="Hero Image"
              style="
                width: 100%;
                height: auto;
                max-width: 100%;
                object-fit: contain;
                border-radius: 20px;
                transform: perspective(1000px) rotateY(0deg) rotateX(0deg);
                transition: transform 0.3s ease, box-shadow 0.3s ease;
                box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
                animation: float 3s ease-in-out infinite;
              "
              onmousemove="const rect=this.getBoundingClientRect(),x=(event.clientX-rect.left)/rect.width,y=(event.clientY-rect.top)/rect.height,rotY=(x<0.3?-10:x>0.7?10:0),rotX=(y<0.3?10:y>0.7?-10:0),shadowX=rotY*3,shadowY=rotX*3,shadowIntensity=0.4+Math.abs(rotY+rotX)/50;this.style.transform=`perspective(1000px) rotateY(${rotY}deg) rotateX(${rotX}deg) scale(${1+Math.abs(rotY+rotX)/100})`;this.style.boxShadow=`${shadowX}px ${shadowY}px 30px 5px rgba(229,9,20,${shadowIntensity})`;"
              onmouseout="this.style.transform='perspective(1000px) rotateY(0deg) rotateX(0deg) scale(1)';this.style.boxShadow='0 10px 20px rgba(0,0,0,0.3)';"
            />
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="content-fade-in">
      <div class="container">
        <div class="section-title text-center slide-in-left">
          <h2>About Me</h2>
          <p>Get to know more about me and my skills</p>
        </div>
        <div class="row">
          <div class="col-lg-5 slide-in-left">
            <div class="about-img">
              <img
                src="images/Photo.jpg"
                alt="About Me"
                class="img-fluid"
                style="
                  width: 100%;
                  height: auto;
                  max-width: 100%;
                  object-fit: contain;
                  border-radius: 20px;
                  box-sizing: border-box;
                  transform: perspective(1000px) rotateY(0deg) rotateX(0deg);
                  transition: transform 0.3s ease, box-shadow 0.3s ease,
                    filter 0.3s ease;
                  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
                  animation: float 3s ease-in-out infinite;
                "
                onmousemove="const rect=this.getBoundingClientRect(),x=(event.clientX-rect.left)/rect.width,y=(event.clientY-rect.top)/rect.height,rotY=(x<0.3?-12:x>0.7?12:0),rotX=(y<0.3?12:y>0.7?-12:0),shadowX=rotY*3,shadowY=rotX*3,shadowIntensity=0.4+Math.abs(rotY+rotX)/50,persp=1000+Math.abs(rotY+rotX)*10,skew=(Math.abs(rotY+rotX)/10),glow=x<0.3&&y<0.3?'sepia(0.2)':x>0.7&&y<0.3?'brightness(1.1)':x<0.3&&y>0.7?'saturate(1.2)':x>0.7&&y>0.7?'contrast(1.1)':'none';this.style.transform=`perspective(${persp}px) rotateY(${rotY}deg) rotateX(${rotX}deg) skew(${skew}deg) scale(${1-Math.abs(rotY+rotX)/100})`;this.style.boxShadow=`${shadowX}px ${shadowY}px 25px 3px rgba(229,9,20,${shadowIntensity}), 0 0 10px rgba(255,255,255,${shadowIntensity/2})`;this.style.filter=`drop-shadow(0 0 8px rgba(255,255,255,${shadowIntensity/2})) ${glow}`;"
                onmouseout="this.style.transform='perspective(1000px) rotateY(0deg) rotateX(0deg) scale(1)';this.style.boxShadow='0 10px 20px rgba(0,0,0,0.3)';this.style.filter='none';"
              />
            </div>
          </div>
          <div class="col-lg-7 slide-in-right">
            <h3 class="mb-4">Front-end Developer & Designer</h3>
            <p>
              I'm a passionate Front-End Developer with expertise in HTML, CSS,
              JavaScript, and Bootstrap. I build responsive, user-friendly web
              applications that enhance business presence online. I've interned
              as a Software Development Intern at Bluestock Fintech,
              contributing to scalable front-end features, and as a Web
              Developer Intern at TechSonix Solutions, where I focused on
              responsive design and real-world web projects. Always eager to
              learn and create seamless digital experiences.
            </p>
            <p>
              My goal is to create beautiful, functional websites that provide
              an exceptional user experience. I'm constantly learning new
              technologies to stay up-to-date with the latest industry trends.
            </p>

            <div class="skills mt-5">
              <h4 class="mb-4">My Skills</h4>
              <div class="skill-item">
                <div class="skill-name d-flex justify-content-between">
                  <span>Web-Dev: HTML5, CSS3 & JavaScript</span>
                  <span>96%</span>
                </div>
                <div class="skill-bar">
                  <div class="skill-progress" style="width: 0%"></div>
                </div>
              </div>

              <div class="skill-item">
                <div class="skill-name d-flex justify-content-between">
                  <span>Coding / DSA: C++, Python & Java</span>
                  <span>90%</span>
                </div>
                <div class="skill-bar">
                  <div class="skill-progress" style="width: 0%"></div>
                </div>
              </div>

              <div class="skill-item">
                <div class="skill-name d-flex justify-content-between">
                  <span>Data Analytics: Power BI & Tableau</span>
                  <span>88%</span>
                </div>
                <div class="skill-bar">
                  <div class="skill-progress" style="width: 0%"></div>
                </div>
              </div>

              <div class="skill-item">
                <div class="skill-name d-flex justify-content-between">
                  <span>English: Speaking, Reading & Writing</span>
                  <span>94%</span>
                </div>
                <div class="skill-bar">
                  <div class="skill-progress" style="width: 0%"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Coding Skills Section -->
    <section id="coding-skills" class="content-fade-in">
      <div class="container">
        <div class="section-title text-center slide-in-left">
          <h2>Coding Skills</h2>
          <p>Explore my competitive programming journey through a Netflix-inspired interface, showcasing problems solved, ratings, and achievements across top platforms.</p>
        </div>
        <div class="platform-grid">
                    <!-- CodeStudio Card -->
          <div
            class="platform-card slide-in-left shimmer-effect"
            style="animation-delay: 0.6s;"
            onmousemove="const rect=this.getBoundingClientRect(),x=(event.clientX-rect.left)/rect.width,y=(event.clientY-rect.top)/rect.height,rotY=(x<0.3?-10:x>0.7?10:0),rotX=(y<0.3?10:y>0.7?-10:0),shadowX=rotY*2,shadowY=rotX*2,shadowIntensity=0.3+Math.abs(rotY+rotX)/50;this.style.transform=`perspective(1000px) rotateY(${rotY}deg) rotateX(${rotX}deg) scale(1.05)`;this.style.boxShadow=`${shadowX}px ${shadowY}px 20px rgba(229,9,20,${shadowIntensity})`;"
            onmouseout="this.style.transform='perspective(1000px) rotateY(0deg) rotateX(0deg) scale(1)';this.style.boxShadow='0 2px 5px rgba(0,0,0,0.2)';"
          >
            <div
              class="overlay"
              style="
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);
                opacity: 0;
                transition: opacity 0.3s ease;
                pointer-events: none;
              "
            ></div>
            <i
              class="fas fa-laptop-code"
              style="
                font-size: 2rem;
                color: var(--primary-color);
                margin-bottom: 15px;
              "
            ></i>
            <h4
              style="
                font-size: 1.5rem;
                font-weight: 700;
                color: var(--text-color);
                margin-bottom: 15px;
                text-transform: uppercase;
              "
            >
              CodeStudio
            </h4>
            <div
              style="
                font-size: 0.9rem;
                color: var(--text-color);
                margin-bottom: 20px;
                text-align: left;
                display: grid;
                grid-template-columns: 1fr 1fr;
                gap: 10px;
              "
            >
              <p style="margin: 5px 0;">
                <i class="fas fa-check-circle" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Solved:</strong> 433
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-trophy" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Rating:</strong> 11700
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-user" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Level:</strong> Advanced
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-star" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Stars:</strong>                 <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
              </p>
            </div>
            <a
              href="https://www.naukri.com/code360/profile/makki_27"
              target="_blank"
              style="
                display: inline-block;
                padding: 8px 20px;
                background: var(--primary-color);
                color: white;
                font-size: 0.9rem;
                font-weight: 500;
                text-decoration: none;
                border-radius: 4px;
                transition: transform 0.3s ease, box-shadow 0.3s ease;
              "
              onmouseover="this.style.transform='scale(1.1)';this.style.boxShadow='0 0 15px rgba(229,9,20,0.7)';this.style.animation='none';"
              onmouseout="this.style.transform='scale(1)';this.style.boxShadow='none';this.style.animation='pulse 2s infinite';"
            >View Profile</a>
          </div>


          <!-- LeetCode Card -->
          <div
            class="platform-card slide-in-left shimmer-effect"
            style="animation-delay: 0.2s;"
            onmousemove="const rect=this.getBoundingClientRect(),x=(event.clientX-rect.left)/rect.width,y=(event.clientY-rect.top)/rect.height,rotY=(x<0.3?-10:x>0.7?10:0),rotX=(y<0.3?10:y>0.7?-10:0),shadowX=rotY*2,shadowY=rotX*2,shadowIntensity=0.3+Math.abs(rotY+rotX)/50;this.style.transform=`perspective(1000px) rotateY(${rotY}deg) rotateX(${rotX}deg) scale(1.05)`;this.style.boxShadow=`${shadowX}px ${shadowY}px 20px rgba(229,9,20,${shadowIntensity})`;"
            onmouseout="this.style.transform='perspective(1000px) rotateY(0deg) rotateX(0deg) scale(1)';this.style.boxShadow='0 2px 5px rgba(0,0,0,0.2)';"
          >
            <div
              class="overlay"
              style="
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);
                opacity: 0;
                transition: opacity 0.3s ease;
                pointer-events: none;
              "
            ></div>
            <i
              class="fas fa-code"
              style="
                font-size: 2rem;
                color: var(--primary-color);
                margin-bottom: 15px;
              "
            ></i>
            <h4
              style="
                font-size: 1.5rem;
                font-weight: 700;
                color: var(--text-color);
                margin-bottom: 15px;
                text-transform: uppercase;
              "
            >
              LeetCode
            </h4>
            <div
              style="
                font-size: 0.9rem;
                color: var(--text-color);
                margin-bottom: 20px;
                text-align: left;
                display: grid;
                grid-template-columns: 1fr 1fr;
                gap: 10px;
              "
            >
              <p style="margin: 5px 0;">
                <i class="fas fa-check-circle" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Solved:</strong> 62
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-trophy" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Rating:</strong> 1,70,137
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-user" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Level:</strong> Knight
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-medal" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Badges:</strong> 0
              </p>
            </div>
            <a
              href="https://leetcode.com/u/MohdMakki/"
              target="_blank"
              style="
                display: inline-block;
                padding: 8px 20px;
                background: var(--primary-color);
                color: white;
                font-size: 0.9rem;
                font-weight: 500;
                text-decoration: none;
                border-radius: 4px;
                transition: transform 0.3s ease, box-shadow 0.3s ease;
              "
              onmouseover="this.style.transform='scale(1.1)';this.style.boxShadow='0 0 15px rgba(229,9,20,0.7)';this.style.animation='none';"
              onmouseout="this.style.transform='scale(1)';this.style.boxShadow='none';this.style.animation='pulse 2s infinite';"
            >View Profile</a>
          </div>

          <!-- CodeChef Card -->
          <div
            class="platform-card slide-in-right shimmer-effect"
            style="animation-delay: 0.4s;"
            onmousemove="const rect=this.getBoundingClientRect(),x=(event.clientX-rect.left)/rect.width,y=(event.clientY-rect.top)/rect.height,rotY=(x<0.3?-10:x>0.7?10:0),rotX=(y<0.3?10:y>0.7?-10:0),shadowX=rotY*2,shadowY=rotX*2,shadowIntensity=0.3+Math.abs(rotY+rotX)/50;this.style.transform=`perspective(1000px) rotateY(${rotY}deg) rotateX(${rotX}deg) scale(1.05)`;this.style.boxShadow=`${shadowX}px ${shadowY}px 20px rgba(229,9,20,${shadowIntensity})`;"
            onmouseout="this.style.transform='perspective(1000px) rotateY(0deg) rotateX(0deg) scale(1)';this.style.boxShadow='0 2px 5px rgba(0,0,0,0.2)';"
          >
            <div
              class="overlay"
              style="
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);
                opacity: 0;
                transition: opacity 0.3s ease;
                pointer-events: none;
              "
            ></div>
            <i
              class="fas fa-trophy"
              style="
                font-size: 2rem;
                color: var(--primary-color);
                margin-bottom: 15px;
              "
            ></i>
            <h4
              style="
                font-size: 1.5rem;
                font-weight: 700;
                color: var(--text-color);
                margin-bottom: 15px;
                text-transform: uppercase;
              "
            >
              CodeChef
            </h4>
            <div
              style="
                font-size: 0.9rem;
                color: var(--text-color);
                margin-bottom: 20px;
                text-align: left;
                display: grid;
                grid-template-columns: 1fr 1fr;
                gap: 10px;
              "
            >
              <p style="margin: 5px 0;">
                <i class="fas fa-check-circle" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Solved:</strong> 137
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-trophy" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Rating:</strong> 14628
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-user" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Level:</strong> Division 2
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-star" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Stars:</strong>                 <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
              </p>
            </div>
            <a
              href="https://www.codechef.com/users/cunnp_1526"
              target="_blank"
              style="
                display: inline-block;
                padding: 8px 20px;
                background: var(--primary-color);
                color: white;
                font-size: 0.9rem;
                font-weight: 500;
                text-decoration: none;
                border-radius: 4px;
                transition: transform 0.3s ease, box-shadow 0.3s ease;
              "
              onmouseover="this.style.transform='scale(1.1)';this.style.boxShadow='0 0 15px rgba(229,9,20,0.7)';this.style.animation='none';"
              onmouseout="this.style.transform='scale(1)';this.style.boxShadow='none';this.style.animation='pulse 2s infinite';"
            >View Profile</a>
          </div>

          <!-- HackerRank Card -->
          <div
            class="platform-card slide-in-right shimmer-effect"
            style="animation-delay: 0.8s;"
            onmousemove="const rect=this.getBoundingClientRect(),x=(event.clientX-rect.left)/rect.width,y=(event.clientY-rect.top)/rect.height,rotY=(x<0.3?-10:x>0.7?10:0),rotX=(y<0.3?10:y>0.7?-10:0),shadowX=rotY*2,shadowY=rotX*2,shadowIntensity=0.3+Math.abs(rotY+rotX)/50;this.style.transform=`perspective(1000px) rotateY(${rotY}deg) rotateX(${rotX}deg) scale(1.05)`;this.style.boxShadow=`${shadowX}px ${shadowY}px 20px rgba(229,9,20,${shadowIntensity})`;"
            onmouseout="this.style.transform='perspective(1000px) rotateY(0deg) rotateX(0deg) scale(1)';this.style.boxShadow='0 2px 5px rgba(0,0,0,0.2)';"
          >
            <div
              class="overlay"
              style="
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);
                opacity: 0;
                transition: opacity 0.3s ease;
                pointer-events: none;
              "
            ></div>
            <i
              class="fas fa-medal"
              style="
                font-size: 2rem;
                color: var(--primary-color);
                margin-bottom: 15px;
              "
            ></i>
            <h4
              style="
                font-size: 1.5rem;
                font-weight: 700;
                color: var(--text-color);
                margin-bottom: 15px;
                text-transform: uppercase;
              "
            >
              HackerRank
            </h4>
            <div
              style="
                font-size: 0.9rem;
                color: var(--text-color);
                margin-bottom: 20px;
                text-align: left;
                display: grid;
                grid-template-columns: 1fr 1fr;
                gap: 10px;
              "
            >
              <p style="margin: 5px 0;">
                <i class="fas fa-check-circle" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Solved:</strong> 446
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-trophy" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Rating:</strong> N/A
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-user" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Level:</strong> Gold
              </p>
              <p style="margin: 5px 0;">
                <i class="fas fa-star" style="color: var(--primary-color); margin-right: 5px;"></i>
                <strong>Stars:</strong>                 <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
              </p>
            </div>
            <a
              href="https://www.hackerrank.com/profile/mohdmakki27"
              target="_blank"
              style="
                display: inline-block;
                padding: 8px 20px;
                background: var(--primary-color);
                color: white;
                font-size: 0.9rem;
                font-weight: 500;
                text-decoration: none;
                border-radius: 4px;
                transition: transform 0.3s ease, box-shadow 0.3s ease;
              "
              onmouseover="this.style.transform='scale(1.1)';this.style.boxShadow='0 0 15px rgba(229,9,20,0.7)';this.style.animation='none';"
              onmouseout="this.style.transform='scale(1)';this.style.boxShadow='none';this.style.animation='pulse 2s infinite';"
            >View Profile</a>
          </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Typing Project -->
    <div class="container content-fade-in">
      <div class="section-title text-center slide-in-left">
        <h2>10 Finger Fast</h2>
        <p>A typing test Website / Platform</p>
      </div>
      <div
        class="project-section shimmer-effect"
        style="
          padding: 40px 55px 60px 55px;
          background: var(--card-bg);
          border-radius: 15px;
          box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
          margin: 30px auto;
          margin-bottom: 100px;
          max-width: 1300px;
          text-align: center;
          transition: transform 0.3s ease;
        "
      >
        <h3
          style="
            font-size: 32px;
            font-weight: 700;
            color: var(--text-color);
            margin-bottom: 15px;
            text-transform: uppercase;
          "
        >
          Typing Text Master
        </h3>
        <p
          style="
            font-size: 18px;
            color: var(--text-color);
            line-height: 1.7;
            max-width: 800px;
            margin: 0 auto 25px;
            text-align: justify;
            opacity: 0.7;
          "
        >
          Step into the world of <strong>Typing Text Master</strong> — an
          interactive web application designed to enhance typing speed and
          accuracy. Featuring a sleek, user-friendly interface, this project
          showcases real-time performance tracking, dynamic animations, and full
          responsiveness across all devices. Developed using HTML, CSS,
          JavaScript, and Bootstrap, it delivers both functionality and a smooth
          user experience.
        </p>

        <div
          class="project-features"
          style="
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-bottom: 30px;
          "
        >
          <div
            class="slide-in-left shimmer-effect"
            style="
              flex: 1;
              min-width: 250px;
              padding: 20px;
              background: var(--card-bg);
              border-radius: 10px;
              box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
              transition: transform 0.3s ease, box-shadow 0.3s ease;
              animation-delay: 0.2s;
            "
            onmouseover="this.style.transform='translateY(-5px)'; this.style.boxShadow='0 8px 25px rgba(229,9,20,0.5)';"
            onmouseout="this.style.transform='translateY(0)'; this.style.boxShadow='0 4px 15px rgba(0,0,0,0.2)';"
          >
            <h4
              style="
                font-size: 20px;
                font-weight: 600;
                color: var(--primary-color);
                margin-bottom: 10px;
              "
            >
              Real-Time Metrics
            </h4>
            <p
              style="
                font-size: 16px;
                color: var(--text-color);
                margin: 0;
                text-align: justify;
                opacity: 0.7;
              "
            >
              Track words-per-minute (WPM) and accuracy with instant feedback,
              empowering users to improve their typing skills dynamically.
            </p>
          </div>
          <div
            class="slide-in-right shimmer-effect"
            style="
              flex: 1;
              min-width: 250px;
              padding: 20px;
              background: var(--card-bg);
              border-radius: 10px;
              box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
              transition: transform 0.3s ease, box-shadow 0.3s ease;
              animation-delay: 0.4s;
            "
            onmouseover="this.style.transform='translateY(-5px)'; this.style.boxShadow='0 8px 25px rgba(229,9,20,0.5)';"
            onmouseout="this.style.transform='translateY(0)'; this.style.boxShadow='0 4px 15px rgba(0,0,0,0.2)';"
          >
            <h4
              style="
                font-size: 20px;
                font-weight: 600;
                color: var(--primary-color);
                margin-bottom: 10px;
              "
            >
              Responsive Design
            </h4>
            <p
              style="
                font-size: 16px;
                color: var(--text-color);
                margin: 0;
                text-align: justify;
                opacity: 0.7;
              "
            >
              Seamlessly adapts to desktops, tablets, and mobiles using
              Bootstrap, ensuring a flawless experience on any device.
            </p>
          </div>
          <div
            class="slide-in-left shimmer-effect"
            style="
              flex: 1;
              min-width: 250px;
              padding: 20px;
              background: var(--card-bg);
              border-radius: 10px;
              box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
              transition: transform 0.3s ease, box-shadow 0.3s ease;
              animation-delay: 0.6s;
            "
            onmouseover="this.style.transform='translateY(-5px)'; this.style.boxShadow='0 8px 25px rgba(229,9,20,0.5)';"
            onmouseout="this.style.transform='translateY(0)'; this.style.boxShadow='0 4px 15px rgba(0,0,0,0.2)';"
          >
            <h4
              style="
                font-size: 20px;
                font-weight: 600;
                color: var(--primary-color);
                margin-bottom: 10px;
              "
            >
              Engaging UI
            </h4>
            <p
              style="
                font-size: 16px;
                color: var(--text-color);
                margin: 0;
                text-align: justify;
                opacity: 0.7;
              "
            >
              Features smooth animations and intuitive feedback, making typing
              practice both fun and visually captivating.
            </p>
          </div>
        </div>

        <a
          href="https://10fingersfasttyping.netlify.app/"
          style="
            display: inline-block;
            padding: 12px 30px;
            background: var(--primary-color);
            color: white;
            font-size: 18px;
            font-weight: 500;
            text-decoration: none;
            border-radius: 50px;
            box-shadow: 0 4px 15px rgba(229, 9, 20, 0.4);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            animation: pulse 2s infinite;
          "
          onmouseover="this.style.transform='scale(1.05)'; this.style.boxShadow='0 6px 20px rgba(229,9,20,0.6)'; this.style.animation='none';"
          onmouseout="this.style.transform='scale(1)'; this.style.boxShadow='0 4px 15px rgba(229,9,20,0.4)'; this.style.animation='pulse 2s infinite';"
        >Launch Typing Test</a>
      </div>
    </div>

    <!-- Education Section -->
    <section id="education" class="content-fade-in">
      <div class="container">
        <div class="section-title text-center slide-in-left">
          <h2>My Academic Education</h2>
          <p>My educational journey and qualifications</p>
        </div>
        <div class="row justify-content-center">
          <div class="col-lg-8">
            <div class="education-item slide-in-left shimmer-effect" style="animation-delay: 0.2s;">
              <h4>BE / B.Tech: Computer Science & Engineering</h4>
              <p>Chandigarh University, Mohali, PB</p>
              <p class="year">2021 - 2025</p>
              <p>
                CGPA:
                <span class="year" style="font-weight: bold; color: var(--primary-color)">7.12</span>
              </p>
            </div>
            <div class="education-item slide-in-right shimmer-effect" style="animation-delay: 0.4s;">
              <h4>12th Grade (Higher Secondary)</h4>
              <p>Ramp Sewak Yadav Smarak Inter College, Barabanki, UP</p>
              <p class="year">2018 - 2019</p>
              <p>
                Percentage:
                <span class="year" style="font-weight: bold; color: var(--primary-color)">75%</span>
              </p>
            </div>
            <div class="education-item slide-in-left shimmer-effect" style="animation-delay: 0.6s;">
              <h4>10th Grade (High School)</h4>
              <p>Ramp Sewak Yadav Smarak Inter College, Barabanki, UP</p>
              <p class="year">2016 - 2017</p>
              <p>
                Percentage:
                <span class="year" style="font-weight: bold; color: var(--primary-color)">85.6%</span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="content-fade-in">
      <div class="container">
        <div class="section-title text-center slide-in-left">
          <h2>My Services</h2>
          <p>High-quality services that I offer to my clients</p>
        </div>
        <div class="row">
          <div class="col-lg-4 col-md-6 slide-in-left shimmer-effect" style="animation-delay: 0.2s;">
            <div class="service-box">
              <div class="service-icon">
                <i class="fas fa-desktop"></i>
              </div>
              <br />
              <div class="container">
                <span class="typed-text-1" style="font-size: 20px; margin: 0; padding: 0;"></span>
              </div>
              <br />
              <p style="text-align: justify">
                Crafting visually captivating, fully responsive websites that
                deliver exceptional user experiences, seamlessly blending modern
                design trends with intuitive functionality.
              </p>
              <p style="text-align: justify">
                Specializing in custom UI/UX design, mobile-first optimization,
                and integration with cutting-edge frameworks like React, Vue.js,
                and WordPress to create high-performance, scalable web solutions
                tailored to your brand’s vision.
              </p>
            </div>
          </div>
          <div class="col-lg-4 col-md-6 slide-in-right shimmer-effect" style="animation-delay: 0.4s;">
            <div class="service-box">
              <div class="service-icon">
                <i class="fas fa-code"></i>
              </div>
              <br />
              <span class="typed-text-2" style="font-size: 20px; margin: 0; padding: 0;"></span>
              <br />
              <br />
              <p style="text-align: justify">
                Developing high-performance, responsive web applications with
                clean, optimized code to drive your business forward.
              </p>
              <p style="text-align: justify">
                Proficient in JavaScript, HTML5, CSS3, and frameworks like
                Bootstrap and Tailwind CSS, I deliver robust solutions with a
                focus on scalability, cross-browser compatibility, and seamless
                API integrations for dynamic, data-driven applications.
              </p>
            </div>
          </div>
          <div class="col-lg-4 col-md-6 slide-in-left shimmer-effect" style="animation-delay: 0.6s;">
            <div class="service-box">
              <div class="service-icon">
                <i class="fas fa-mobile-alt"></i>
              </div>
              <br />
              <span class="typed-text-3" style="font-size: 20px; margin: 0; padding: 0;"></span>
              <br />
              <br />
              <p style="text-align: justify">
                Designing mobile-first, adaptive interfaces that ensure flawless
                performance across all devices and screen sizes.
              </p>
              <p style="text-align: justify">
                Leveraging responsive design principles and progressive web app
                (PWA) techniques, I create fast, accessible, and engaging
                experiences optimized for mobile users, with a focus on
                performance and user retention.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Portfolio Section -->
    <section id="portfolio">
      <div class="container">
        <div class="section-title text-center fade-in">
          <h2>My Portfolio</h2>
          <p>Check out some of my recent projects</p>
        </div>

        <div class="portfolio-filter text-center fade-in">
          <button class="filter-btn active" data-filter="all">All</button>
          <button class="filter-btn" data-filter="web">Web Design</button>
          <button class="filter-btn" data-filter="app">App Development</button>
          <button class="filter-btn" data-filter="ui">UI/UX Design</button>
        </div>

        <div class="row portfolio-container">
          <div class="col-lg-4 col-md-6 portfolio-item web fade-in">
            <div class="position-relative overflow-hidden">
              <img
                src="images/searching-visualization copy.svg"
                alt="Portfolio 1"
                class="img-fluid portfolio-img"
                style="
                  width: 500px;
                  height: 250px;
                  max-width: 100%;
                  object-fit: cover;
                  border-radius: 15px;
                "
              />
              <div class="portfolio-overlay" style="padding: 10px">
                <h4 style="font-style: italic">Searching Visualization</h4>
                <p style="text-align: justify">
                  Linear & Binary Search: Developed a Searching Visualization
                  project to demonstrate search algorithms like Linear and
                  Binary Search. The interactive interface helps users
                  understand algorithm behavior with real-time animations.
                </p>
                <a
                  href="https://github.com/MohdMakki/Searching-Visualization"
                  class="btn btn-sm btn-light mt-2"
                  >View Details</a
                >
              </div>
            </div>
          </div>
          <div class="col-lg-4 col-md-6 portfolio-item app fade-in">
            <div class="position-relative overflow-hidden">
              <img
                src="images/fibonacci-visualizer copy.svg"
                alt="Portfolio 2"
                class="img-fluid portfolio-img"
                style="
                  width: 500px;
                  height: 250px;
                  max-width: 100%;
                  object-fit: cover;
                  border-radius: 15px;
                "
              />
              <div class="portfolio-overlay" style="padding: 10px">
                <h4 style="font-style: italic">Fibonacci Visualizer</h4>
                <p style="text-align: justify">
                  Fibonacci Visualizer: The Fibonacci sequence is a mathematical
                  pattern where each number is the sum of the two preceding
                  ones. Introduced to the West by Leonardo Fibonacci in 1202 but
                  known earlier in India, this sequence appears throughout
                  nature and connects to the golden ratio.
                </p>
                <a
                  href="https://github.com/MohdMakki/Fibonacci-Visualizer"
                  class="btn btn-sm btn-light mt-2"
                  >View Details</a
                >
              </div>
            </div>
          </div>
          <div class="col-lg-4 col-md-6 portfolio-item ui fade-in">
            <div class="position-relative overflow-hidden">
              <img
                src="images/coffee-shop-dashboard copy.svg"
                alt="Portfolio 3"
                class="img-fluid portfolio-img"
                style="
                  width: 500px;
                  height: 250px;
                  max-width: 100%;
                  object-fit: cover;
                  border-radius: 15px;
                "
              />
              <div class="portfolio-overlay" style="padding: 10px">
                <h4 style="font-style: italic">
                  Data Visualization & Business Intelligence
                </h4>
                <p style="text-align: justify">
                  Proficient in Power BI and Tableau for data visualization,
                  creating interactive dashboards and reports. Skilled in
                  transforming complex data into insights with analytics, data
                  modeling, and custom visualizations to drive decision-making.
                </p>
                <a
                  href="https://github.com/MohdMakki?tab=repositories"
                  class="btn btn-sm btn-light mt-2"
                  >View Details</a
                >
              </div>
            </div>
          </div>
          <div class="col-lg-4 col-md-6 portfolio-item web fade-in">
            <div class="position-relative overflow-hidden">
              <img
                src="images/flappy copy.svg"
                alt="Portfolio 4"
                class="img-fluid portfolio-img"
                style="
                  width: 500px;
                  height: 250px;
                  max-width: 100%;
                  object-fit: cover;
                  border-radius: 15px;
                "
              />
              <div class="portfolio-overlay" style="padding: 10px">
                <h4 style="font-style: italic">Flappy Bird Game</h4>
                <p style="text-align: justify">
                  Develop a responsive HTML5 Canvas-based Flappy Bird clone with
                  pure JavaScript that features gravity physics, collision
                  detection, and animated graphics. Include power-up system,
                  difficulty settings, and score tracking while ensuring
                  cross-browser compatibility and mobile-friendly controls.
                </p>
                <a
                  href="https://github.com/MohdMakki/Buddy4Plant"
                  class="btn btn-sm btn-light mt-2"
                  >View Details</a
                >
              </div>
            </div>
          </div>
          <div class="col-lg-4 col-md-6 portfolio-item app fade-in">
            <div class="position-relative overflow-hidden">
              <img
                src="images/traffic-flow-analysis-system copy.svg"
                alt="Portfolio 5"
                class="img-fluid portfolio-img"
                style="
                  width: 500px;
                  height: 250px;
                  max-width: 100%;
                  object-fit: cover;
                  border-radius: 15px;
                "
              />
              <div class="portfolio-overlay" style="padding: 10px">
                <h4 style="font-style: italic">
                  Real-Time Traffic Flow Analysis system using AI and computer
                  vision
                </h4>
                <p style="text-align: justify">
                  Developed a Real-Time Traffic Flow Analysis system using AI
                  and computer vision. The project processes live traffic data
                  to detect congestion patterns, enhancing traffic management
                  and optimization.
                </p>
                <a href="#" class="btn btn-sm btn-light mt-2">View Details</a>
              </div>
            </div>
          </div>
          <div class="col-lg-4 col-md-6 portfolio-item ui fade-in">
            <div class="position-relative overflow-hidden">
              <img
                src="images/buddy copy.svg"
                alt="Portfolio 6"
                class="img-fluid portfolio-img"
                style="
                  width: 500px;
                  height: 250px;
                  max-width: 100%;
                  object-fit: cover;
                  border-radius: 15px;
                "
              />
              <div class="portfolio-overlay" style="padding: 10px">
                <h4 style="font-style: italic">Buddy4Plant</h4>
                <p style="text-align: justify">
                  Buddy4Plant is an innovative project designed to assist
                  farmers in the field by leveraging technology for better plant
                  care and agricultural efficiency. This system provides
                  real-time insights, crop monitoring, and smart recommendations
                  to enhance productivity and sustainability.
                </p>
                <a
                  href="https://github.com/MohdMakki/Buddy4Plant"
                  class="btn btn-sm btn-light mt-2"
                  >View Details</a
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section id="testimonials">
      <div class="container">
        <div class="section-title text-center fade-in">
          <h2>Experience</h2>
          <p>Where I've worked and what I've contributed</p>
        </div>

        <div class="row">
          <div class="col-lg-4 col-md-6 fade-in">
            <div class="testimonial-item">
              <div class="testimonial-img">
                <img
                  src="https://pbs.twimg.com/profile_images/1711275061414699008/7RFqZYlp_400x400.png"
                  alt="Testimonial 2"
                  class="img-fluid"
                />
              </div>
              <div class="testimonial-rating">
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
              </div>
              <p class="testimonial-text" style="text-align: justify">
                "Working as a Software Development Engineer (SDE) at Bluestock
                Fintech was a valuable experience. I contributed to building
                scalable front-end components and enhancing the UI/UX of
                financial web applications to meet real-world business needs."
              </p>
              <h5 class="testimonial-name">MOHD MAKKI</h5>
              <p class="testimonial-position">
                <span class="typed-text-5"></span>
              </p>
            </div>
          </div>

          <div class="col-lg-4 col-md-6 fade-in">
            <div class="testimonial-item">
              <div class="testimonial-img">
                <img
                  src="https://media.licdn.com/dms/image/v2/D560BAQHbHAG2z6lDFg/company-logo_400_400/company-logo_400_400/0/1735494292241/techsonix_solutions_logo?e=2147483647&v=beta&t=GWXzIYOPzJeQgZi_IemlXjxsVoIfR7wu7ezJMqoCwUU"
                  alt="Testimonial 2"
                  class="img-fluid"
                />
              </div>
              <div class="testimonial-rating">
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star-half-alt text-warning"></i>
              </div>
              <p class="testimonial-text" style="text-align: justify">
                "As a Web Developer Intern at TechSonix Solutions, I worked on
                creating responsive and dynamic websites. I focused on
                implementing clean UI designs, optimizing performance, and
                ensuring cross-browser compatibility for real-world client
                projects."
              </p>

              <h5 class="testimonial-name">MOHD MAKKI</h5>
              <p class="testimonial-position">
                <span class="typed-text-4"></span>
              </p>
            </div>
          </div>

          <div class="col-lg-4 col-md-6 fade-in">
            <div class="testimonial-item">
              <div class="testimonial-img">
                <img
                  src="https://seeklogo.com/images/C/chandigarh-university-cu-logo-BD80DC39BC-seeklogo.com.png"
                  alt="Testimonial 2"
                  class="img-fluid"
                />
              </div>
              <div class="testimonial-rating">
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star text-warning"></i>
                <i class="fas fa-star-half-alt text-warning"></i>
              </div>
              <p class="testimonial-text" style="text-align: justify">
                "Built projects like a Real-Time Traffic Monitoring System using
                AI, Searching Visualizer, Fibonacci Visualizer, Buddy4Plant, a
                smart farming assistant—enhancing my skills in front-end
                development, AI, and real-world problem-solving, and working on
                a Real Time Typing Test website etc."
              </p>
              <h5 class="testimonial-name">MOHD MAKKI</h5>
              <p class="testimonial-position">
                <span class="typed-text-6"></span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
      <div class="container">
        <div class="section-title text-center fade-in">
          <h2>Contact Me</h2>
          <p>Let's get in touch and discuss your project</p>
        </div>
        <div class="row">
          <div class="col-lg-4 fade-in">
            <div class="contact-info d-flex align-items-center">
              <div class="contact-icon">
                <i class="fas fa-phone-alt"></i>
              </div>
              <div>
                <h5>Phone</h5>
                <p>+91 7071760851</p>
              </div>
            </div>
            <div class="contact-info d-flex align-items-center">
              <div class="contact-icon">
                <i class="fas fa-envelope"></i>
              </div>
              <div>
                <h5>Email</h5>
                <p>mohdmakki27@gmail.com</p>
              </div>
            </div>
            <div class="contact-info d-flex align-items-center">
              <div class="contact-icon">
                <i class="fas fa-map-marker-alt"></i>
              </div>
              <div>
                <h5>Location</h5>
                <p>Lucknow, UP, IN</p>
              </div>
            </div>
            <a
              href="MOHD_MAKKI_IT.pdf"
              download
              style="
                display: inline-block;
                padding: 12px 30px;
                background: linear-gradient(45deg, #007bff, #00ddeb);
                color: #fff;
                font-size: 16px;
                font-weight: 500;
                text-decoration: none;
                border-radius: 50px;
                box-shadow: 0 4px 15px rgba(4, 66, 133, 0.4);
                transition: transform 0.3s ease, box-shadow 0.3s ease;
                margin-top: 20px;
              "
              onmouseover="this.style.transform='scale(1.05)'; this.style.boxShadow='0 6px 20px rgba(0, 123, 255, 0.6)';"
              onmouseout="this.style.transform='scale(1)'; this.style.boxShadow='0 4px 15px rgba(0, 123, 255, 0.4)';"
              >Download My Resume</a
            >
          </div>
          <div class="col-lg-8 fade-in" style="margin-top: 30px;">
            <form class="contact-form">
              <div class="row">
                <div class="col-md-6">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Your Name"
                    required
                  />
                </div>
                <div class="col-md-6">
                  <input
                    type="email"
                    class="form-control"
                    placeholder="Your Email"
                    required
                  />
                </div>
              </div>
              <input
                type="text"
                class="form-control"
                placeholder="Subject"
                required
              />
              <textarea
                class="form-control"
                rows="5"
                placeholder="Message"
                required
              ></textarea>
              <button type="submit" class="btn btn-primary">
                Send Message
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer>
      <div class="container text-center">
        <div class="social-links mb-3">
          <a href="https://github.com/MohdMakki?tab=repositories"
            ><i class="fab fa-github"></i
          ></a>
          <a href="https://www.instagram.com/mohdmakki27/"
            ><i class="fab fa-instagram"></i
          ></a>
          <a href="https://www.linkedin.com/in/mohd-makki-a3a886223/"
            ><i class="fab fa-linkedin-in"></i
          ></a>
          <a href="https://www.facebook.com/mohd.makki.503"
            ><i class="fab fa-facebook-f"></i
          ></a>
          <a href="https://www.youtube.com/channel/UCKFaR1EjjqME7U3fChj1ODw"
            ><i class="fab fa-youtube"></i
          ></a>
        </div>
        <p>© 2025 My Portfolio. All Rights Reserved.</p>
      </div>
    </footer>

    <!-- Back to Top Button -->
    <div class="back-to-top">
      <i class="fas fa-arrow-up"></i>
    </div>

    <!-- Scripts -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.0/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/typed.js/2.0.12/typed.min.js"></script>
    <script>
      // Theme Toggle
      const themeToggle = document.getElementById("theme-toggle");
      const currentTheme = localStorage.getItem("theme") || "light";
      document.documentElement.setAttribute("data-theme", currentTheme);
      if (currentTheme === "dark") {
        themeToggle.classList.remove("fa-moon");
        themeToggle.classList.add("fa-sun");
      }

      themeToggle.addEventListener("click", () => {
        let theme = document.documentElement.getAttribute("data-theme");
        if (theme === "light") {
          document.documentElement.setAttribute("data-theme", "dark");
          localStorage.setItem("theme", "dark");
          themeToggle.classList.remove("fa-moon");
          themeToggle.classList.add("fa-sun");
        } else {
          document.documentElement.setAttribute("data-theme", "light");
          localStorage.setItem("theme", "light");
          themeToggle.classList.remove("fa-sun");
          themeToggle.classList.add("fa-moon");
        }
      });

      // Preloader
      window.addEventListener("load", function () {
        document.querySelector(".preloader").classList.add("loaded");
      });

      // Navbar Scroll Effect
      window.addEventListener("scroll", function () {
        const navbar = document.querySelector(".navbar");
        if (window.scrollY > 50) {
          navbar.classList.add("scrolled");
        } else {
          navbar.classList.remove("scrolled");
        }
      });

      // Typed.js for Hero Section
      new Typed(".typed-text", {
        strings: ["MOHD MAKKI", "a Developer", "a Designer", "a Creator"],
        typeSpeed: 50,
        backSpeed: 30,
        loop: true,
      });

      // Fade-in Animation on Scroll
      const fadeElements = document.querySelectorAll(".fade-in");
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add("visible");
            }
          });
        },
        { threshold: 0.1 }
      );

      fadeElements.forEach((element) => observer.observe(element));

      // Skills Progress Animation
      const skillBars = document.querySelectorAll(".skill-progress");
      const skillObserver = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              const progress = entry.target;
              const percentage =
                progress.parentElement.previousElementSibling.querySelector(
                  "span:last-child"
                ).textContent;
              progress.style.width = percentage;
            }
          });
        },
        { threshold: 0.5 }
      );

      skillBars.forEach((bar) => skillObserver.observe(bar));

      // Portfolio Filter
      const filterButtons = document.querySelectorAll(".filter-btn");
      const portfolioItems = document.querySelectorAll(".portfolio-item");

      filterButtons.forEach((button) => {
        button.addEventListener("click", () => {
          filterButtons.forEach((btn) => btn.classList.remove("active"));
          button.classList.add("active");

          const filter = button.getAttribute("data-filter");
          portfolioItems.forEach((item) => {
            if (filter === "all" || item.classList.contains(filter)) {
              item.style.display = "block";
            } else {
              item.style.display = "none";
            }
          });
        });
      });

      // Back to Top Button
      const backToTop = document.querySelector(".back-to-top");
      window.addEventListener("scroll", () => {
        if (window.scrollY > 300) {
          backToTop.classList.add("active");
        } else {
          backToTop.classList.remove("active");
        }
      });

      backToTop.addEventListener("click", () => {
        window.scrollTo({ top: 0, behavior: "smooth" });
      });

      // Form Submission
      document
        .querySelector(".contact-form")
        .addEventListener("submit", function (e) {
          e.preventDefault();
          alert("Message sent successfully! (This is a demo)");
          this.reset();
        });

      new Typed(".typed-text-1", {
        strings: ["Web Designer", "&", "Web Solutions "],
        typeSpeed: 50,
        backSpeed: 30,
        loop: true,
      });
      new Typed(".typed-text-2", {
        strings: ["Robust Web Development"],
        typeSpeed: 50,
        backSpeed: 30,
        loop: true,
      });
      new Typed(".typed-text-3", {
        strings: ["Adaptive", "&", "Responsive Design"],
        typeSpeed: 50,
        backSpeed: 30,
        loop: true,
      });

      new Typed(".typed-text-4", {
        strings: [
          "Web Developer Intern",
          "TechSonix Solutions",
          "Pune, Maharastra",
        ],
        typeSpeed: 50,
        backSpeed: 30,
        loop: true,
      });

      new Typed(".typed-text-5", {
        strings: ["SDE Intern", "Bluestock Fintech", "Pune, Maharastra"],
        typeSpeed: 50,
        backSpeed: 30,
        loop: true,
      });

      new Typed(".typed-text-6", {
        strings: [
          "B.E. / B.Tech CSE",
          "Chandigarh University",
          "Mohali, Punjab",
        ],
        typeSpeed: 50,
        backSpeed: 30,
        loop: true,
      });
    </script>
  </body>
</html>
