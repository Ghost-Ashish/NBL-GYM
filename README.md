<!doctype html>
<html lang="en" class="h-full w-full">
 <head>
  <meta charset="UTF-8">
  <title>NBL Gym Portal</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <style>
    body {
      box-sizing: border-box;
    }
    html, body {
      height: 100%;
      width: 100%;
      margin: 0;
      padding: 0;
    }
    
    /* Glass morphism effect - Dark Mode */
    .glass {
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid rgba(255, 255, 255, 0.1);
      box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
    }
    
    .glass-strong {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(25px);
      -webkit-backdrop-filter: blur(25px);
      border: 1px solid rgba(255, 255, 255, 0.18);
      box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.5);
    }
    
    .glass-hover {
      transition: all 0.3s ease;
    }
    
    .glass-hover:hover {
      background: rgba(255, 255, 255, 0.15);
      transform: translateY(-4px);
      box-shadow: 0 12px 40px 0 rgba(0, 0, 0, 0.5);
    }
    
    /* Glass morphism effect - Light Mode */
    body.light-mode .glass {
      background: rgba(255, 255, 255, 0.7);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid rgba(0, 0, 0, 0.1);
      box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.1);
    }
    
    body.light-mode .glass-strong {
      background: rgba(255, 255, 255, 0.85);
      backdrop-filter: blur(25px);
      -webkit-backdrop-filter: blur(25px);
      border: 1px solid rgba(0, 0, 0, 0.15);
      box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.15);
    }
    
    body.light-mode .glass-hover:hover {
      background: rgba(255, 255, 255, 0.95);
      transform: translateY(-4px);
      box-shadow: 0 12px 40px 0 rgba(0, 0, 0, 0.2);
    }
    
    /* Text colors for light mode */
    body.light-mode .text-white {
      color: #111827 !important;
    }
    
    body.light-mode .text-white\/90 {
      color: rgba(17, 24, 39, 0.9) !important;
    }
    
    body.light-mode .text-white\/80 {
      color: rgba(17, 24, 39, 0.8) !important;
    }
    
    body.light-mode .text-white\/70 {
      color: rgba(17, 24, 39, 0.7) !important;
    }
    
    body.light-mode .text-white\/60 {
      color: rgba(17, 24, 39, 0.6) !important;
    }
    
    body.light-mode .text-white\/50 {
      color: rgba(17, 24, 39, 0.5) !important;
    }
    
    body.light-mode input,
    body.light-mode textarea,
    body.light-mode select {
      color: #111827 !important;
    }
    
    body.light-mode input::placeholder,
    body.light-mode textarea::placeholder {
      color: rgba(17, 24, 39, 0.5) !important;
    }
    
    /* Animated gradient background */
    .gradient-bg {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 25%, #f093fb 50%, #4facfe 75%, #00f2fe 100%);
      background-size: 400% 400%;
      animation: gradientShift 15s ease infinite;
    }
    
    @keyframes gradientShift {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    
    /* Fitness background with real gym photo */
    .fitness-bg {
      position: relative;
      background-image: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1920 1080"><defs><linearGradient id="gymGrad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" style="stop-color:%23111827;stop-opacity:1" /><stop offset="50%" style="stop-color:%231f2937;stop-opacity:1" /><stop offset="100%" style="stop-color:%23374151;stop-opacity:1" /></linearGradient><pattern id="gymEquipment" x="0" y="0" width="400" height="400" patternUnits="userSpaceOnUse"><rect width="400" height="400" fill="url(%23gymGrad)"/><g opacity="0.4"><rect x="50" y="150" width="80" height="200" rx="10" fill="%23000" stroke="%23666" stroke-width="3"/><rect x="140" y="150" width="80" height="200" rx="10" fill="%23000" stroke="%23666" stroke-width="3"/><circle cx="90" cy="130" r="20" fill="%23333" stroke="%23888" stroke-width="4"/><circle cx="180" cy="130" r="20" fill="%23333" stroke="%23888" stroke-width="4"/><rect x="85" y="125" width="100" height="10" rx="5" fill="%23555"/><ellipse cx="135" cy="250" rx="60" ry="15" fill="%23000" opacity="0.3"/><rect x="280" y="180" width="60" height="150" rx="8" fill="%23222" stroke="%23777" stroke-width="2"/><rect x="290" y="190" width="40" height="20" rx="3" fill="%23444"/><rect x="290" y="220" width="40" height="20" rx="3" fill="%23444"/><rect x="290" y="250" width="40" height="20" rx="3" fill="%23444"/><rect x="290" y="280" width="40" height="20" rx="3" fill="%23444"/><rect x="290" y="310" width="40" height="20" rx="3" fill="%23444"/></g><g opacity="0.2"><circle cx="100" cy="80" r="8" fill="%23fff"/><circle cx="300" cy="100" r="6" fill="%23fff"/><circle cx="200" cy="350" r="10" fill="%23fff"/></g></pattern></defs><rect width="1920" height="1080" fill="url(%23gymEquipment)"/><g opacity="0.15"><rect x="100" y="400" width="300" height="400" fill="%23000"/><rect x="1500" y="300" width="300" height="500" fill="%23000"/><ellipse cx="960" cy="900" rx="800" ry="150" fill="%23000"/></g><text x="960" y="540" font-family="Arial Black" font-size="180" fill="%23fff" opacity="0.03" text-anchor="middle" dominant-baseline="middle">FITNESS</text></svg>');
      background-size: cover;
      background-position: center;
      background-attachment: fixed;
    }
    
    .fitness-bg::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(135deg, rgba(17, 24, 39, 0.85) 0%, rgba(31, 41, 55, 0.85) 50%, rgba(55, 65, 81, 0.75) 100%);
      z-index: 0;
    }
    
    .fitness-bg > * {
      position: relative;
      z-index: 1;
    }
    
    /* Light mode styles */
    body.light-mode .fitness-bg::before {
      background: linear-gradient(135deg, rgba(249, 250, 251, 0.95) 0%, rgba(243, 244, 246, 0.95) 50%, rgba(229, 231, 235, 0.90) 100%);
    }
    
    body.light-mode .gradient-bg {
      background: linear-gradient(135deg, #f9fafb 0%, #e5e7eb 50%, #d1d5db 100%);
    }
    
    /* Hero section styles */
    .hero-pattern {
      background-image: 
        repeating-linear-gradient(45deg, transparent, transparent 35px, rgba(255,255,255,.03) 35px, rgba(255,255,255,.03) 70px);
    }
    
    /* Smooth transitions */
    .transition-all {
      transition: all 0.3s ease;
    }
    
    /* Focus styles */
    .focus-ring:focus-visible {
      outline: 3px solid rgba(255, 255, 255, 0.6);
      outline-offset: 2px;
    }
    
    /* Custom scrollbar */
    .custom-scroll::-webkit-scrollbar {
      width: 8px;
    }
    
    .custom-scroll::-webkit-scrollbar-track {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 10px;
    }
    
    .custom-scroll::-webkit-scrollbar-thumb {
      background: rgba(255, 255, 255, 0.2);
      border-radius: 10px;
    }
    
    .custom-scroll::-webkit-scrollbar-thumb:hover {
      background: rgba(255, 255, 255, 0.3);
    }
    
    /* Notification badge pulse */
    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.5; }
    }
    
    .pulse {
      animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
 </head>
 <body class="h-full w-full m-0 p-0">
  <div id="app-root" class="w-full h-full gradient-bg overflow-auto custom-scroll"><!-- Floating Theme Toggle Button --> <button id="floating-theme-toggle" onclick="toggleTheme()" class="fixed bottom-6 right-6 glass-strong rounded-full p-4 text-white glass-hover focus-ring shadow-lg z-50 transition-all hover:scale-110" title="Toggle theme"> <span id="theme-icon" class="text-2xl">🌙</span> </button> <!-- Sidebar Menu Overlay -->
   <div id="sidebar-overlay" class="hidden fixed inset-0 bg-black/50 backdrop-blur-sm z-50" onclick="closeSidebar()"></div><!-- Sidebar Menu -->
   <div id="sidebar-menu" class="fixed top-0 right-0 h-full w-80 glass-strong transform translate-x-full transition-transform duration-300 ease-in-out z-50 overflow-y-auto">
    <div class="p-6"><!-- Close Button -->
     <div class="flex items-center justify-between mb-8">
      <div class="flex items-center gap-3">
       <div class="w-10 h-10 rounded-full glass flex items-center justify-center text-xl">
        💪
       </div>
       <h3 class="text-white font-bold text-lg">Menu</h3>
      </div><button onclick="closeSidebar()" class="glass rounded-full p-2 text-white glass-hover focus-ring">
       <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
       </svg></button>
     </div><!-- Navigation Links -->
     <nav class="space-y-3 mb-8"><a href="#home" onclick="closeSidebar(); scrollToSection('home')" class="block glass rounded-xl px-5 py-3 text-white font-medium glass-hover focus-ring"> 🏠 Home </a> <a href="#about" onclick="closeSidebar(); scrollToSection('about')" class="block glass rounded-xl px-5 py-3 text-white font-medium glass-hover focus-ring"> ℹ️ About </a> <a href="#programs" onclick="closeSidebar(); scrollToSection('programs')" class="block glass rounded-xl px-5 py-3 text-white font-medium glass-hover focus-ring"> 🏋️ Programs </a> <a href="#trainers" onclick="closeSidebar(); scrollToSection('trainers')" class="block glass rounded-xl px-5 py-3 text-white font-medium glass-hover focus-ring"> 👨‍🏫 Trainers </a> <a href="#contact" onclick="closeSidebar(); scrollToSection('contact')" class="block glass rounded-xl px-5 py-3 text-white font-medium glass-hover focus-ring"> 📞 Contact </a>
     </nav><!-- Divider -->
     <div class="border-t border-white/10 my-6"></div><!-- Auth Buttons -->
     <div class="space-y-3"><button onclick="closeSidebar(); showPage('login')" class="w-full glass rounded-xl px-5 py-3 text-white font-medium glass-hover focus-ring"> 🔐 Login </button> <button onclick="closeSidebar(); showPage('register')" class="w-full glass-strong rounded-xl px-5 py-3 text-white font-semibold glass-hover focus-ring"> ✨ Join Now </button>
     </div><!-- Contact Info -->
     <div class="mt-8 glass rounded-2xl p-4">
      <h4 class="text-white font-semibold text-sm mb-3">Quick Contact</h4>
      <div class="space-y-2 text-white/70 text-xs">
       <p>📞 +91 98765 43210</p>
       <p>✉️ info@nblgym.com</p>
       <p>⏰ Open 24/7</p>
      </div>
     </div>
    </div>
   </div><!-- Landing Page -->
   <div id="page-landing" class="min-h-full w-full flex flex-col fitness-bg"><!-- Header -->
    <header id="main-header" class="glass-strong sticky top-0 z-50 transition-all">
     <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-20"><!-- Logo -->
       <div class="flex items-center gap-3">
        <div class="w-12 h-12 rounded-full glass flex items-center justify-center text-2xl">
         💪
        </div>
        <div>
         <h1 id="header-gym-name" class="text-2xl font-bold text-white tracking-tight">NBL GYM</h1>
         <p class="text-white/60 text-xs">Transform Yourself</p>
        </div>
       </div><!-- Menu Toggle Button --> <button id="menu-toggle-btn" class="glass rounded-lg p-2 text-white focus-ring">
        <svg id="menu-icon" class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg></button>
      </div>
     </div>
    </header><!-- Hero Section -->
    <section id="home" class="flex items-center justify-center px-4 py-12 sm:py-16 lg:py-20 hero-pattern">
     <div class="max-w-7xl w-full">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-12 items-center"><!-- Left Content -->
       <div class="text-center lg:text-left">
        <div class="inline-block glass rounded-full px-4 py-2 mb-6">
         <p class="text-white/90 text-sm font-medium">🔥 #1 Gym in the City</p>
        </div>
        <h1 id="gym-name" class="text-5xl sm:text-6xl lg:text-7xl font-bold text-white mb-6 tracking-tight leading-tight">NBL GYM</h1>
        <p id="tagline" class="text-xl sm:text-2xl lg:text-3xl text-white/90 mb-6 font-medium">Transform Your Body, Elevate Your Mind</p>
        <p id="welcome-message" class="text-white/70 text-base sm:text-lg mb-8 max-w-xl mx-auto lg:mx-0">Join hundreds of fitness enthusiasts achieving their goals at NBL Gym</p><!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start mb-8"><button onclick="showPage('register')" class="glass-strong rounded-full px-8 py-4 text-white text-base font-bold glass-hover focus-ring shadow-lg"> Start Your Journey → </button> <button onclick="showPage('login')" class="glass rounded-full px-8 py-4 text-white text-base font-semibold glass-hover focus-ring"> Member Login </button>
        </div><!-- Stats -->
        <div class="grid grid-cols-3 gap-4 max-w-md mx-auto lg:mx-0">
         <div class="glass rounded-2xl p-4 text-center">
          <p class="text-2xl sm:text-3xl font-bold text-white mb-1">500+</p>
          <p class="text-white/70 text-xs sm:text-sm">Members</p>
         </div>
         <div class="glass rounded-2xl p-4 text-center">
          <p class="text-2xl sm:text-3xl font-bold text-white mb-1">15+</p>
          <p class="text-white/70 text-xs sm:text-sm">Trainers</p>
         </div>
         <div class="glass rounded-2xl p-4 text-center">
          <p class="text-2xl sm:text-3xl font-bold text-white mb-1">24/7</p>
          <p class="text-white/70 text-xs sm:text-sm">Access</p>
         </div>
        </div>
       </div><!-- Right Content - Features Grid -->
       <div class="grid grid-cols-2 gap-4">
        <div class="glass-strong rounded-3xl p-6 glass-hover text-center">
         <div class="text-5xl sm:text-6xl mb-4">
          💪
         </div>
         <h3 class="text-white font-bold text-base sm:text-lg mb-2">Strength Training</h3>
         <p class="text-white/70 text-xs sm:text-sm">Build muscle with expert guidance</p>
        </div>
        <div class="glass-strong rounded-3xl p-6 glass-hover text-center">
         <div class="text-5xl sm:text-6xl mb-4">
          🏃
         </div>
         <h3 class="text-white font-bold text-base sm:text-lg mb-2">Cardio Zone</h3>
         <p class="text-white/70 text-xs sm:text-sm">Boost endurance &amp; burn calories</p>
        </div>
        <div class="glass-strong rounded-3xl p-6 glass-hover text-center">
         <div class="text-5xl sm:text-6xl mb-4">
          🧘
         </div>
         <h3 class="text-white font-bold text-base sm:text-lg mb-2">Yoga &amp; Flexibility</h3>
         <p class="text-white/70 text-xs sm:text-sm">Improve mobility &amp; balance</p>
        </div>
        <div class="glass-strong rounded-3xl p-6 glass-hover text-center">
         <div class="text-5xl sm:text-6xl mb-4">
          🏋️
         </div>
         <h3 class="text-white font-bold text-base sm:text-lg mb-2">Power Lifting</h3>
         <p class="text-white/70 text-xs sm:text-sm">Maximize strength gains</p>
        </div>
       </div>
      </div>
     </div>
    </section><!-- About Section -->
    <section id="about" class="px-4 py-16 sm:py-20">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-12">
       <h2 class="text-4xl sm:text-5xl font-bold text-white mb-4">About NBL Gym</h2>
       <p class="text-white/80 text-lg max-w-2xl mx-auto">Your premier fitness destination with world-class facilities and expert trainers</p>
      </div>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-12"><!-- Gym Info -->
       <div class="glass-strong rounded-3xl p-8">
        <h3 class="text-2xl font-bold text-white mb-4">Our Story</h3>
        <p class="text-white/80 text-base mb-4">Founded in 2015, NBL Gym has been transforming lives through fitness for over 8 years. We believe in creating a supportive community where everyone, from beginners to advanced athletes, can achieve their fitness goals.</p>
        <p class="text-white/80 text-base mb-6">Our state-of-the-art facility spans 15,000 sq ft with cutting-edge equipment, dedicated zones for strength training, cardio, functional fitness, and group classes. We're committed to providing the best fitness experience in the city.</p>
        <div class="space-y-3">
         <div class="flex items-start gap-3"><span class="text-2xl">📍</span>
          <div>
           <p class="text-white font-semibold">Location</p>
           <p class="text-white/70 text-sm">123 Fitness Street, Gym City, GC 12345</p>
          </div>
         </div>
         <div class="flex items-start gap-3"><span class="text-2xl">⏰</span>
          <div>
           <p class="text-white font-semibold">Hours</p>
           <p class="text-white/70 text-sm">Open 24/7 - Train on your schedule</p>
          </div>
         </div>
         <div class="flex items-start gap-3"><span class="text-2xl">🏆</span>
          <div>
           <p class="text-white font-semibold">Achievements</p>
           <p class="text-white/70 text-sm">Best Gym Award 2023 | 500+ Success Stories</p>
          </div>
         </div>
        </div>
       </div><!-- Stats -->
       <div class="grid grid-cols-2 gap-4">
        <div class="glass-strong rounded-2xl p-6 text-center glass-hover">
         <p class="text-4xl font-bold text-white mb-2">500+</p>
         <p class="text-white/70">Active Members</p>
        </div>
        <div class="glass-strong rounded-2xl p-6 text-center glass-hover">
         <p class="text-4xl font-bold text-white mb-2">15+</p>
         <p class="text-white/70">Expert Trainers</p>
        </div>
        <div class="glass-strong rounded-2xl p-6 text-center glass-hover">
         <p class="text-4xl font-bold text-white mb-2">8</p>
         <p class="text-white/70">Years Experience</p>
        </div>
        <div class="glass-strong rounded-2xl p-6 text-center glass-hover">
         <p class="text-4xl font-bold text-white mb-2">24/7</p>
         <p class="text-white/70">Access</p>
        </div>
        <div class="glass-strong rounded-2xl p-6 text-center glass-hover col-span-2">
         <p class="text-4xl font-bold text-white mb-2">15,000</p>
         <p class="text-white/70">Sq Ft Facility</p>
        </div>
       </div>
      </div><!-- Trainers -->
      <div id="trainers" class="mb-8">
       <h3 class="text-3xl font-bold text-white mb-8 text-center">Meet Our Expert Trainers</h3>
       <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6"><!-- Trainer 1 -->
        <div class="glass-strong rounded-3xl p-6 text-center glass-hover">
         <div class="w-32 h-32 rounded-full glass mx-auto mb-4 flex items-center justify-center text-6xl">
          👨‍🏫
         </div>
         <h4 class="text-xl font-bold text-white mb-2">Rajesh Kumar</h4>
         <p class="text-white/70 text-sm mb-3">Head Trainer | 10 Years Exp</p>
         <p class="text-white/60 text-xs mb-4">Specializes in strength training and bodybuilding. Certified personal trainer with multiple national awards.</p>
         <div class="flex gap-2 justify-center flex-wrap"><span class="glass rounded-full px-3 py-1 text-xs text-white">Strength</span> <span class="glass rounded-full px-3 py-1 text-xs text-white">Nutrition</span>
         </div>
        </div><!-- Trainer 2 -->
        <div class="glass-strong rounded-3xl p-6 text-center glass-hover">
         <div class="w-32 h-32 rounded-full glass mx-auto mb-4 flex items-center justify-center text-6xl">
          👩‍🏫
         </div>
         <h4 class="text-xl font-bold text-white mb-2">Priya Sharma</h4>
         <p class="text-white/70 text-sm mb-3">Yoga &amp; Flexibility | 8 Years Exp</p>
         <p class="text-white/60 text-xs mb-4">Expert in yoga, pilates, and flexibility training. Helps members achieve balance and mindfulness.</p>
         <div class="flex gap-2 justify-center flex-wrap"><span class="glass rounded-full px-3 py-1 text-xs text-white">Yoga</span> <span class="glass rounded-full px-3 py-1 text-xs text-white">Pilates</span>
         </div>
        </div><!-- Trainer 3 -->
        <div class="glass-strong rounded-3xl p-6 text-center glass-hover">
         <div class="w-32 h-32 rounded-full glass mx-auto mb-4 flex items-center justify-center text-6xl">
          👨‍🏫
         </div>
         <h4 class="text-xl font-bold text-white mb-2">Amit Patel</h4>
         <p class="text-white/70 text-sm mb-3">HIIT &amp; Cardio | 6 Years Exp</p>
         <p class="text-white/60 text-xs mb-4">High-intensity interval training specialist. Helps members burn fat and build endurance fast.</p>
         <div class="flex gap-2 justify-center flex-wrap"><span class="glass rounded-full px-3 py-1 text-xs text-white">HIIT</span> <span class="glass rounded-full px-3 py-1 text-xs text-white">Cardio</span>
         </div>
        </div>
       </div>
      </div>
     </div>
    </section><!-- Programs Section -->
    <section id="programs" class="px-4 py-16 sm:py-20">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-12">
       <h2 class="text-4xl sm:text-5xl font-bold text-white mb-4">Our Programs</h2>
       <p class="text-white/80 text-lg max-w-2xl mx-auto">Join our specialized programs designed to help you achieve specific fitness goals</p>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6"><!-- Marathon Program -->
       <div class="glass-strong rounded-3xl p-6 glass-hover">
        <div class="text-5xl mb-4 text-center">
         🏃‍♂️
        </div>
        <h3 class="text-2xl font-bold text-white mb-3 text-center">5K Marathon Training</h3>
        <p class="text-white/70 text-sm mb-4 text-center">12-week program to prepare you for your first 5K run</p>
        <div class="space-y-3 mb-6">
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Week 1-4: Foundation</p>
          <p class="text-white/70 text-xs">Build base endurance with walk-run intervals</p>
         </div>
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Week 5-8: Building</p>
          <p class="text-white/70 text-xs">Increase running time and distance gradually</p>
         </div>
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Week 9-12: Peak</p>
          <p class="text-white/70 text-xs">Complete 5K runs and race preparation</p>
         </div>
        </div>
        <div class="flex items-center justify-between text-white/80 text-sm mb-4"><span>⏱️ 12 Weeks</span> <span>📅 3x per week</span>
        </div><button onclick="showPage('register')" class="w-full glass rounded-xl px-4 py-3 text-white font-semibold glass-hover focus-ring"> Join Program </button>
       </div><!-- Weight Loss Program -->
       <div class="glass-strong rounded-3xl p-6 glass-hover">
        <div class="text-5xl mb-4 text-center">
         🔥
        </div>
        <h3 class="text-2xl font-bold text-white mb-3 text-center">Weight Loss Challenge</h3>
        <p class="text-white/70 text-sm mb-4 text-center">8-week intensive fat burning program</p>
        <div class="space-y-3 mb-6">
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">HIIT Workouts</p>
          <p class="text-white/70 text-xs">High-intensity interval training 4x/week</p>
         </div>
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Nutrition Plan</p>
          <p class="text-white/70 text-xs">Customized meal plans and tracking</p>
         </div>
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Progress Tracking</p>
          <p class="text-white/70 text-xs">Weekly measurements and adjustments</p>
         </div>
        </div>
        <div class="flex items-center justify-between text-white/80 text-sm mb-4"><span>⏱️ 8 Weeks</span> <span>📅 4x per week</span>
        </div><button onclick="showPage('register')" class="w-full glass rounded-xl px-4 py-3 text-white font-semibold glass-hover focus-ring"> Join Program </button>
       </div><!-- Muscle Building Program -->
       <div class="glass-strong rounded-3xl p-6 glass-hover">
        <div class="text-5xl mb-4 text-center">
         💪
        </div>
        <h3 class="text-2xl font-bold text-white mb-3 text-center">Muscle Building</h3>
        <p class="text-white/70 text-sm mb-4 text-center">16-week hypertrophy focused program</p>
        <div class="space-y-3 mb-6">
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Progressive Overload</p>
          <p class="text-white/70 text-xs">Systematic strength and size gains</p>
         </div>
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Split Training</p>
          <p class="text-white/70 text-xs">Targeted muscle group workouts</p>
         </div>
         <div class="glass rounded-xl p-3">
          <p class="text-white font-medium text-sm mb-1">Recovery Protocol</p>
          <p class="text-white/70 text-xs">Optimal rest and nutrition guidance</p>
         </div>
        </div>
        <div class="flex items-center justify-between text-white/80 text-sm mb-4"><span>⏱️ 16 Weeks</span> <span>📅 5x per week</span>
        </div><button onclick="showPage('register')" class="w-full glass rounded-xl px-4 py-3 text-white font-semibold glass-hover focus-ring"> Join Program </button>
       </div>
      </div>
     </div>
    </section><!-- Contact Section -->
    <section id="contact" class="px-4 py-16 sm:py-20">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-12">
       <h2 class="text-4xl sm:text-5xl font-bold text-white mb-4">Get In Touch</h2>
       <p class="text-white/80 text-lg max-w-2xl mx-auto">Have questions? We're here to help you start your fitness journey</p>
      </div>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8"><!-- Contact Form -->
       <div class="glass-strong rounded-3xl p-8">
        <h3 class="text-2xl font-bold text-white mb-6">Send us a message</h3>
        <form id="contact-form" class="space-y-4">
         <div><label for="contact-name" class="block text-white text-sm font-medium mb-2">Your Name</label> <input id="contact-name" type="text" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="John Doe">
         </div>
         <div><label for="contact-email" class="block text-white text-sm font-medium mb-2">Email</label> <input id="contact-email" type="email" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="your@email.com">
         </div>
         <div><label for="contact-phone" class="block text-white text-sm font-medium mb-2">Phone</label> <input id="contact-phone" type="tel" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="9876543210">
         </div>
         <div><label for="contact-message" class="block text-white text-sm font-medium mb-2">Message</label> <textarea id="contact-message" required rows="4" class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring resize-none" placeholder="Tell us how we can help you..."></textarea>
         </div>
         <div id="contact-success" class="hidden glass rounded-xl px-4 py-3 text-green-300 text-sm">
          ✅ Message sent successfully! We'll get back to you soon.
         </div><button type="submit" id="contact-btn" class="w-full glass-strong rounded-xl px-6 py-3 text-white font-semibold glass-hover focus-ring"> Send Message </button>
        </form>
       </div><!-- Contact Info -->
       <div class="space-y-6">
        <div class="glass-strong rounded-3xl p-8">
         <h3 class="text-2xl font-bold text-white mb-6">Contact Information</h3>
         <div class="space-y-4">
          <div class="flex items-start gap-4">
           <div class="glass rounded-full w-12 h-12 flex items-center justify-center text-2xl flex-shrink-0">
            📍
           </div>
           <div>
            <p class="text-white font-semibold mb-1">Address</p>
            <p class="text-white/70 text-sm">123 Fitness Street, Gym City, GC 12345</p>
           </div>
          </div>
          <div class="flex items-start gap-4">
           <div class="glass rounded-full w-12 h-12 flex items-center justify-center text-2xl flex-shrink-0">
            📞
           </div>
           <div>
            <p class="text-white font-semibold mb-1">Phone</p>
            <p class="text-white/70 text-sm">+91 98765 43210</p>
            <p class="text-white/70 text-sm">+91 98765 43211</p>
           </div>
          </div>
          <div class="flex items-start gap-4">
           <div class="glass rounded-full w-12 h-12 flex items-center justify-center text-2xl flex-shrink-0">
            ✉️
           </div>
           <div>
            <p class="text-white font-semibold mb-1">Email</p>
            <p class="text-white/70 text-sm">info@nblgym.com</p>
            <p class="text-white/70 text-sm">support@nblgym.com</p>
           </div>
          </div>
          <div class="flex items-start gap-4">
           <div class="glass rounded-full w-12 h-12 flex items-center justify-center text-2xl flex-shrink-0">
            ⏰
           </div>
           <div>
            <p class="text-white font-semibold mb-1">Hours</p>
            <p class="text-white/70 text-sm">Open 24/7</p>
            <p class="text-white/70 text-sm">Staff Available: 6 AM - 10 PM</p>
           </div>
          </div>
         </div>
        </div><!-- Map Placeholder -->
        <div class="glass-strong rounded-3xl p-8 text-center">
         <div class="text-6xl mb-4">
          🗺️
         </div>
         <h4 class="text-white font-bold text-lg mb-2">Find Us</h4>
         <p class="text-white/70 text-sm mb-4">Located in the heart of Gym City with easy access and ample parking</p><a href="https://maps.google.com" target="_blank" rel="noopener noreferrer" class="inline-block glass rounded-xl px-6 py-3 text-white font-semibold glass-hover focus-ring"> Open in Maps </a>
        </div>
       </div>
      </div>
     </div>
    </section><!-- Footer -->
    <footer class="glass-strong mt-auto">
     <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 sm:py-12">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 mb-8"><!-- About -->
       <div>
        <div class="flex items-center gap-2 mb-4">
         <div class="w-10 h-10 rounded-full glass flex items-center justify-center text-xl">
          💪
         </div>
         <h3 class="text-white font-bold text-lg">NBL GYM</h3>
        </div>
        <p class="text-white/70 text-sm mb-4">Your ultimate fitness destination. Transform your body and mind with us.</p>
        <div class="flex gap-3"><a href="https://facebook.com" target="_blank" rel="noopener noreferrer" class="glass rounded-full w-10 h-10 flex items-center justify-center text-white glass-hover focus-ring">
          <svg class="w-5 h-5" fill="currentColor" viewbox="0 0 24 24">
           <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z" />
          </svg></a> <a href="https://instagram.com" target="_blank" rel="noopener noreferrer" class="glass rounded-full w-10 h-10 flex items-center justify-center text-white glass-hover focus-ring">
          <svg class="w-5 h-5" fill="currentColor" viewbox="0 0 24 24">
           <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z" />
          </svg></a> <a href="https://twitter.com" target="_blank" rel="noopener noreferrer" class="glass rounded-full w-10 h-10 flex items-center justify-center text-white glass-hover focus-ring">
          <svg class="w-5 h-5" fill="currentColor" viewbox="0 0 24 24">
           <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z" />
          </svg></a> <a href="https://youtube.com" target="_blank" rel="noopener noreferrer" class="glass rounded-full w-10 h-10 flex items-center justify-center text-white glass-hover focus-ring">
          <svg class="w-5 h-5" fill="currentColor" viewbox="0 0 24 24">
           <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z" />
          </svg></a>
        </div>
       </div><!-- Quick Links -->
       <div>
        <h4 class="text-white font-bold text-base mb-4">Quick Links</h4>
        <ul class="space-y-2">
         <li><a href="#about" class="text-white/70 hover:text-white text-sm transition-all">About Us</a></li>
         <li><a href="#programs" class="text-white/70 hover:text-white text-sm transition-all">Programs</a></li>
         <li><a href="#trainers" class="text-white/70 hover:text-white text-sm transition-all">Our Trainers</a></li>
         <li><a href="#pricing" class="text-white/70 hover:text-white text-sm transition-all">Membership</a></li>
         <li><a href="#contact" class="text-white/70 hover:text-white text-sm transition-all">Contact</a></li>
        </ul>
       </div><!-- Services -->
       <div>
        <h4 class="text-white font-bold text-base mb-4">Services</h4>
        <ul class="space-y-2">
         <li><a href="#" class="text-white/70 hover:text-white text-sm transition-all">Personal Training</a></li>
         <li><a href="#" class="text-white/70 hover:text-white text-sm transition-all">Group Classes</a></li>
         <li><a href="#" class="text-white/70 hover:text-white text-sm transition-all">Nutrition Plans</a></li>
         <li><a href="#" class="text-white/70 hover:text-white text-sm transition-all">Online Coaching</a></li>
         <li><a href="#" class="text-white/70 hover:text-white text-sm transition-all">Yoga Sessions</a></li>
        </ul>
       </div><!-- Contact Info -->
       <div>
        <h4 class="text-white font-bold text-base mb-4">Contact Us</h4>
        <ul class="space-y-3">
         <li class="flex items-start gap-2 text-white/70 text-sm"><span class="text-lg">📍</span> <span>123 Fitness Street, Gym City, GC 12345</span></li>
         <li class="flex items-center gap-2 text-white/70 text-sm"><span class="text-lg">📞</span> <span>+91 98765 43210</span></li>
         <li class="flex items-center gap-2 text-white/70 text-sm"><span class="text-lg">✉️</span> <span>info@nblgym.com</span></li>
         <li class="flex items-center gap-2 text-white/70 text-sm"><span class="text-lg">⏰</span> <span>Open 24/7</span></li>
        </ul>
       </div>
      </div><!-- Bottom Bar -->
      <div class="border-t border-white/10 pt-6">
       <div class="flex flex-col sm:flex-row justify-between items-center gap-4">
        <p class="text-white/60 text-sm text-center sm:text-left">© 2024 NBL Gym. All rights reserved.</p>
        <div class="flex gap-6"><a href="#" class="text-white/60 hover:text-white text-sm transition-all">Privacy Policy</a> <a href="#" class="text-white/60 hover:text-white text-sm transition-all">Terms of Service</a> <a href="#" class="text-white/60 hover:text-white text-sm transition-all">Cookie Policy</a>
        </div>
       </div>
      </div>
     </div>
    </footer>
   </div><!-- Login Page -->
   <div id="page-login" class="hidden min-h-full w-full flex items-center justify-center px-4 py-12">
    <div class="max-w-md w-full">
     <div class="glass-strong rounded-3xl p-8"><button onclick="showPage('landing')" class="glass rounded-full px-4 py-2 text-white text-sm mb-6 glass-hover focus-ring"> ← Back </button>
      <h2 class="text-3xl font-bold text-white mb-2">Welcome Back</h2>
      <p class="text-white/70 text-sm mb-6">Login to access your profile</p>
      <form id="login-form" class="space-y-4">
       <div><label for="login-email" class="block text-white text-sm font-medium mb-2">Email</label> <input id="login-email" type="email" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="your@email.com">
       </div>
       <div><label for="login-password" class="block text-white text-sm font-medium mb-2">Password</label> <input id="login-password" type="password" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="Enter password">
       </div>
       <div id="login-error" class="hidden glass rounded-xl px-4 py-3 text-red-300 text-sm">
        Invalid credentials. Please try again.
       </div><button type="submit" id="login-btn" class="w-full glass-strong rounded-xl px-6 py-3 text-white font-semibold glass-hover focus-ring"> Login </button>
      </form>
      <p class="text-white/60 text-sm text-center mt-6">Don't have an account? <button onclick="showPage('register')" class="text-white font-semibold underline">Register</button></p>
     </div>
    </div>
   </div><!-- Registration Page -->
   <div id="page-register" class="hidden min-h-full w-full flex items-center justify-center px-4 py-12">
    <div class="max-w-2xl w-full">
     <div class="glass-strong rounded-3xl p-8"><button onclick="showPage('landing')" class="glass rounded-full px-4 py-2 text-white text-sm mb-6 glass-hover focus-ring"> ← Back </button>
      <h2 class="text-3xl font-bold text-white mb-2">Join NBL Gym</h2>
      <p class="text-white/70 text-sm mb-6">Start your fitness journey today</p>
      <form id="register-form" class="space-y-4">
       <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div><label for="reg-name" class="block text-white text-sm font-medium mb-2">Full Name</label> <input id="reg-name" type="text" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="John Doe">
        </div>
        <div><label for="reg-phone" class="block text-white text-sm font-medium mb-2">Phone</label> <input id="reg-phone" type="tel" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="9876543210">
        </div>
       </div>
       <div><label for="reg-email" class="block text-white text-sm font-medium mb-2">Email</label> <input id="reg-email" type="email" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="your@email.com">
       </div>
       <div><label for="reg-password" class="block text-white text-sm font-medium mb-2">Password</label> <input id="reg-password" type="password" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="Create password">
       </div>
       <div><label for="reg-goal" class="block text-white text-sm font-medium mb-2">Fitness Goal</label> <select id="reg-goal" required class="w-full glass rounded-xl px-4 py-3 text-white focus-ring"> <option value="weight_loss">Weight Loss</option> <option value="muscle_gain">Muscle Gain</option> <option value="fitness">General Fitness</option> <option value="strength">Strength Training</option> </select>
       </div>
       <div><label for="reg-shift" class="block text-white text-sm font-medium mb-2">Preferred Shift</label> <select id="reg-shift" required class="w-full glass rounded-xl px-4 py-3 text-white focus-ring"> <option value="morning">Morning (6 AM - 12 PM)</option> <option value="evening">Evening (4 PM - 10 PM)</option> </select>
       </div>
       <div><label class="block text-white text-sm font-medium mb-2">Preferred Training Days</label>
        <div class="grid grid-cols-3 gap-2"><label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Monday" class="reg-day"> Mon </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Tuesday" class="reg-day"> Tue </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Wednesday" class="reg-day"> Wed </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Thursday" class="reg-day"> Thu </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Friday" class="reg-day"> Fri </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Saturday" class="reg-day"> Sat </label>
        </div>
       </div>
       <div><label for="reg-subscription" class="block text-white text-sm font-medium mb-2">Subscription Plan</label> <select id="reg-subscription" required class="w-full glass rounded-xl px-4 py-3 text-white focus-ring"> <option value="1">1 Month - ₹1,500</option> <option value="3">3 Months - ₹4,000 (Save ₹500)</option> <option value="6">6 Months - ₹7,500 (Save ₹1,500)</option> <option value="12">12 Months - ₹14,000 (Save ₹4,000)</option> </select>
       </div>
       <div id="register-error" class="hidden glass rounded-xl px-4 py-3 text-red-300 text-sm"></div><button type="submit" id="register-btn" class="w-full glass-strong rounded-xl px-6 py-3 text-white font-semibold glass-hover focus-ring"> Register &amp; Join </button>
      </form>
      <p class="text-white/60 text-sm text-center mt-6">Already a member? <button onclick="showPage('login')" class="text-white font-semibold underline">Login</button></p>
     </div>
    </div>
   </div><!-- Dashboard (After Login) -->
   <div id="page-dashboard" class="hidden min-h-full w-full"><!-- Top Navigation -->
    <nav class="glass-strong sticky top-0 z-50">
     <div class="max-w-7xl mx-auto px-4 py-4">
      <div class="flex items-center justify-between">
       <div class="flex items-center gap-4">
        <h1 class="text-2xl font-bold text-white">NBL GYM</h1><span id="user-name-nav" class="text-white/70 text-sm"></span>
       </div>
       <div class="flex items-center gap-3"><button onclick="toggleTheme()" class="glass rounded-full p-3 glass-hover focus-ring" title="Toggle theme"> <span id="theme-icon-dash" class="text-xl">🌙</span> </button> <button onclick="showDashboardSection('notifications')" class="glass rounded-full p-3 glass-hover focus-ring relative"> <span class="text-xl">🔔</span> <span id="notif-badge" class="hidden absolute -top-1 -right-1 bg-red-500 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center pulse">3</span> </button> <button onclick="logout()" class="glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring"> Logout </button>
       </div>
      </div><!-- Tab Navigation -->
      <div class="flex gap-2 mt-4 overflow-x-auto"><button onclick="showDashboardSection('profile')" class="dash-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-section="profile"> Profile </button> <button onclick="showDashboardSection('schedule')" class="dash-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-section="schedule"> Weekly Schedule </button> <button onclick="showDashboardSection('workouts')" class="dash-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-section="workouts"> Workout Library </button> <button onclick="showDashboardSection('custom-plan')" class="dash-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-section="custom-plan"> Custom Plan </button> <button onclick="showDashboardSection('plans')" class="dash-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-section="plans"> Workout Plans </button> <button onclick="showDashboardSection('notifications')" class="dash-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-section="notifications"> Notifications </button>
      </div>
     </div>
    </nav>
    <main class="max-w-7xl mx-auto px-4 py-6"><!-- Profile Section -->
     <section id="dash-profile" class="dashboard-section">
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6"><!-- Profile Card -->
       <div class="lg:col-span-1">
        <div class="glass-strong rounded-3xl p-6">
         <div class="text-center mb-6">
          <div class="w-24 h-24 rounded-full glass mx-auto mb-4 flex items-center justify-center text-5xl">
           👤
          </div>
          <h3 id="profile-name" class="text-2xl font-bold text-white mb-1"></h3>
          <p id="profile-email" class="text-white/70 text-sm"></p>
         </div>
         <div class="space-y-3">
          <div class="glass rounded-xl p-4">
           <p class="text-white/70 text-xs mb-1">Phone</p>
           <p id="profile-phone" class="text-white font-medium"></p>
          </div>
          <div class="glass rounded-xl p-4">
           <p class="text-white/70 text-xs mb-1">Fitness Goal</p>
           <p id="profile-goal" class="text-white font-medium"></p>
          </div>
          <div class="glass rounded-xl p-4">
           <p class="text-white/70 text-xs mb-1">Preferred Shift</p>
           <p id="profile-shift" class="text-white font-medium"></p>
          </div>
          <div class="glass rounded-xl p-4">
           <p class="text-white/70 text-xs mb-1">Training Days</p>
           <p id="profile-days" class="text-white font-medium text-sm"></p>
          </div>
         </div>
        </div>
       </div><!-- Subscription Info -->
       <div class="lg:col-span-2">
        <div class="glass-strong rounded-3xl p-6 mb-6">
         <h3 class="text-2xl font-bold text-white mb-4">Subscription Status</h3>
         <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div class="glass rounded-2xl p-6 text-center">
           <p class="text-white/70 text-sm mb-2">Plan Duration</p>
           <p id="sub-duration" class="text-3xl font-bold text-white"></p>
          </div>
          <div class="glass rounded-2xl p-6 text-center">
           <p class="text-white/70 text-sm mb-2">Days Remaining</p>
           <p id="sub-days-left" class="text-3xl font-bold text-green-400"></p>
          </div>
          <div class="glass rounded-2xl p-6 text-center">
           <p class="text-white/70 text-sm mb-2">Expires On</p>
           <p id="sub-end-date" class="text-lg font-bold text-white"></p>
          </div>
         </div>
         <div class="mt-6">
          <div class="glass rounded-full h-4 overflow-hidden">
           <div id="sub-progress" class="h-full bg-gradient-to-r from-green-400 to-blue-500 transition-all" style="width: 0%"></div>
          </div>
          <p class="text-white/60 text-xs text-center mt-2">Subscription Progress</p>
         </div>
        </div><!-- Quick Stats -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
         <div class="glass rounded-2xl p-4 text-center glass-hover">
          <div class="text-3xl mb-2">
           💪
          </div>
          <p class="text-white text-sm font-medium">Strength</p>
         </div>
         <div class="glass rounded-2xl p-4 text-center glass-hover">
          <div class="text-3xl mb-2">
           🔥
          </div>
          <p class="text-white text-sm font-medium">Cardio</p>
         </div>
         <div class="glass rounded-2xl p-4 text-center glass-hover">
          <div class="text-3xl mb-2">
           🧘
          </div>
          <p class="text-white text-sm font-medium">Flexibility</p>
         </div>
         <div class="glass rounded-2xl p-4 text-center glass-hover">
          <div class="text-3xl mb-2">
           ⚡
          </div>
          <p class="text-white text-sm font-medium">Energy</p>
         </div>
        </div>
       </div>
      </div>
     </section><!-- Weekly Schedule Section -->
     <section id="dash-schedule" class="dashboard-section hidden">
      <div class="glass-strong rounded-3xl p-6 mb-6">
       <h3 class="text-2xl font-bold text-white mb-4">Your Weekly Schedule</h3>
       <p class="text-white/70 text-sm mb-6">Based on your <span id="schedule-shift" class="text-white font-semibold"></span> shift preference</p>
       <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4"><!-- Monday -->
        <div class="glass rounded-2xl p-5 glass-hover">
         <h4 class="text-white font-bold text-lg mb-2">Monday</h4>
         <p class="text-white/70 text-sm mb-3">Strength Training</p>
         <ul class="space-y-2 text-white/90 text-sm">
          <li>• Warm-up: 10 min</li>
          <li>• Compound lifts: 40 min</li>
          <li>• Core work: 10 min</li>
          <li>• Cool down: 5 min</li>
         </ul>
        </div><!-- Tuesday -->
        <div class="glass rounded-2xl p-5 glass-hover">
         <h4 class="text-white font-bold text-lg mb-2">Tuesday</h4>
         <p class="text-white/70 text-sm mb-3">Cardio &amp; HIIT</p>
         <ul class="space-y-2 text-white/90 text-sm">
          <li>• Warm-up: 5 min</li>
          <li>• HIIT intervals: 30 min</li>
          <li>• Steady cardio: 15 min</li>
          <li>• Stretch: 10 min</li>
         </ul>
        </div><!-- Wednesday -->
        <div class="glass rounded-2xl p-5 glass-hover">
         <h4 class="text-white font-bold text-lg mb-2">Wednesday</h4>
         <p class="text-white/70 text-sm mb-3">Upper Body Focus</p>
         <ul class="space-y-2 text-white/90 text-sm">
          <li>• Warm-up: 10 min</li>
          <li>• Push exercises: 25 min</li>
          <li>• Pull exercises: 25 min</li>
          <li>• Cool down: 5 min</li>
         </ul>
        </div><!-- Thursday -->
        <div class="glass rounded-2xl p-5 glass-hover">
         <h4 class="text-white font-bold text-lg mb-2">Thursday</h4>
         <p class="text-white/70 text-sm mb-3">Legs &amp; Glutes</p>
         <ul class="space-y-2 text-white/90 text-sm">
          <li>• Warm-up: 10 min</li>
          <li>• Squats &amp; lunges: 30 min</li>
          <li>• Isolation work: 15 min</li>
          <li>• Stretch: 10 min</li>
         </ul>
        </div><!-- Friday -->
        <div class="glass rounded-2xl p-5 glass-hover">
         <h4 class="text-white font-bold text-lg mb-2">Friday</h4>
         <p class="text-white/70 text-sm mb-3">Full Body Circuit</p>
         <ul class="space-y-2 text-white/90 text-sm">
          <li>• Warm-up: 5 min</li>
          <li>• Circuit training: 40 min</li>
          <li>• Abs: 10 min</li>
          <li>• Cool down: 5 min</li>
         </ul>
        </div><!-- Saturday -->
        <div class="glass rounded-2xl p-5 glass-hover">
         <h4 class="text-white font-bold text-lg mb-2">Saturday</h4>
         <p class="text-white/70 text-sm mb-3">Active Recovery</p>
         <ul class="space-y-2 text-white/90 text-sm">
          <li>• Light cardio: 20 min</li>
          <li>• Yoga/Stretching: 30 min</li>
          <li>• Mobility work: 10 min</li>
          <li>��� Relaxation: 5 min</li>
         </ul>
        </div>
       </div>
      </div><!-- Shift Timings -->
      <div class="glass-strong rounded-3xl p-6">
       <h3 class="text-xl font-bold text-white mb-4">Shift Timings</h3>
       <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="glass rounded-2xl p-5">
         <h4 class="text-white font-semibold mb-3">🌅 Morning Shift</h4>
         <ul class="space-y-2 text-white/80 text-sm">
          <li>• 6:00 AM - 8:00 AM: Peak hours</li>
          <li>• 8:00 AM - 10:00 AM: Moderate</li>
          <li>• 10:00 AM - 12:00 PM: Light</li>
         </ul>
        </div>
        <div class="glass rounded-2xl p-5">
         <h4 class="text-white font-semibold mb-3">🌆 Evening Shift</h4>
         <ul class="space-y-2 text-white/80 text-sm">
          <li>• 4:00 PM - 6:00 PM: Moderate</li>
          <li>• 6:00 PM - 8:00 PM: Peak hours</li>
          <li>• 8:00 PM - 10:00 PM: Moderate</li>
         </ul>
        </div>
       </div>
      </div>
     </section><!-- Workout Library Section -->
     <section id="dash-workouts" class="dashboard-section hidden">
      <div class="glass-strong rounded-3xl p-6 mb-6">
       <h3 class="text-2xl font-bold text-white mb-4">Workout Library</h3>
       <p class="text-white/70 text-sm mb-6">Browse exercises by muscle group</p><!-- Muscle Group Tabs -->
       <div class="flex gap-2 mb-6 overflow-x-auto"><button onclick="showWorkoutCategory('chest')" class="workout-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-category="chest"> Chest </button> <button onclick="showWorkoutCategory('back')" class="workout-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-category="back"> Back </button> <button onclick="showWorkoutCategory('shoulders')" class="workout-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-category="shoulders"> Shoulders </button> <button onclick="showWorkoutCategory('arms')" class="workout-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-category="arms"> Arms </button> <button onclick="showWorkoutCategory('legs')" class="workout-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-category="legs"> Legs </button> <button onclick="showWorkoutCategory('core')" class="workout-tab glass rounded-full px-4 py-2 text-white text-sm glass-hover focus-ring whitespace-nowrap" data-category="core"> Core </button>
       </div><!-- Chest Exercises -->
       <div id="workout-chest" class="workout-category">
        <h4 class="text-xl font-bold text-white mb-4">💪 Chest Exercises</h4>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Barbell Bench Press</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-10</p>
          <p class="text-white/60 text-xs">Primary compound movement for chest development</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Incline Dumbbell Press</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
          <p class="text-white/60 text-xs">Targets upper chest muscles</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Cable Flyes</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Isolation exercise for chest definition</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Push-ups</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 15-20</p>
          <p class="text-white/60 text-xs">Bodyweight exercise for overall chest</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Dips</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 8-12</p>
          <p class="text-white/60 text-xs">Compound movement for lower chest</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Pec Deck Machine</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Machine isolation for chest squeeze</p>
         </div>
        </div>
       </div><!-- Back Exercises -->
       <div id="workout-back" class="workout-category hidden">
        <h4 class="text-xl font-bold text-white mb-4">🦾 Back Exercises</h4>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Deadlifts</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 6-8</p>
          <p class="text-white/60 text-xs">King of back exercises, full posterior chain</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Pull-ups</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-12</p>
          <p class="text-white/60 text-xs">Bodyweight exercise for lat width</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Barbell Rows</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-10</p>
          <p class="text-white/60 text-xs">Compound movement for back thickness</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Lat Pulldowns</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
          <p class="text-white/60 text-xs">Machine exercise for lat development</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Seated Cable Rows</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
          <p class="text-white/60 text-xs">Mid-back and rhomboid focus</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Face Pulls</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 15-20</p>
          <p class="text-white/60 text-xs">Rear delts and upper back</p>
         </div>
        </div>
       </div><!-- Shoulders Exercises -->
       <div id="workout-shoulders" class="workout-category hidden">
        <h4 class="text-xl font-bold text-white mb-4">🏋️ Shoulder Exercises</h4>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Overhead Press</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-10</p>
          <p class="text-white/60 text-xs">Primary compound for shoulder mass</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Lateral Raises</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Isolation for side delts</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Front Raises</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Front deltoid focus</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Reverse Flyes</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Rear deltoid isolation</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Arnold Press</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
          <p class="text-white/60 text-xs">All three deltoid heads</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Upright Rows</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
          <p class="text-white/60 text-xs">Shoulders and traps</p>
         </div>
        </div>
       </div><!-- Arms Exercises -->
       <div id="workout-arms" class="workout-category hidden">
        <h4 class="text-xl font-bold text-white mb-4">💪 Arms Exercises</h4>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
         <div>
          <h5 class="text-white font-semibold mb-3">Biceps</h5>
          <div class="space-y-3">
           <div class="glass rounded-2xl p-4">
            <h6 class="text-white font-semibold mb-2">Barbell Curls</h6>
            <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-12</p>
            <p class="text-white/60 text-xs">Primary bicep mass builder</p>
           </div>
           <div class="glass rounded-2xl p-4">
            <h6 class="text-white font-semibold mb-2">Hammer Curls</h6>
            <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
            <p class="text-white/60 text-xs">Targets brachialis and forearms</p>
           </div>
           <div class="glass rounded-2xl p-4">
            <h6 class="text-white font-semibold mb-2">Preacher Curls</h6>
            <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
            <p class="text-white/60 text-xs">Isolation for bicep peak</p>
           </div>
          </div>
         </div>
         <div>
          <h5 class="text-white font-semibold mb-3">Triceps</h5>
          <div class="space-y-3">
           <div class="glass rounded-2xl p-4">
            <h6 class="text-white font-semibold mb-2">Close-Grip Bench</h6>
            <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-10</p>
            <p class="text-white/60 text-xs">Compound tricep builder</p>
           </div>
           <div class="glass rounded-2xl p-4">
            <h6 class="text-white font-semibold mb-2">Tricep Pushdowns</h6>
            <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
            <p class="text-white/60 text-xs">Cable isolation for triceps</p>
           </div>
           <div class="glass rounded-2xl p-4">
            <h6 class="text-white font-semibold mb-2">Overhead Extension</h6>
            <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12</p>
            <p class="text-white/60 text-xs">Long head tricep focus</p>
           </div>
          </div>
         </div>
        </div>
       </div><!-- Legs Exercises -->
       <div id="workout-legs" class="workout-category hidden">
        <h4 class="text-xl font-bold text-white mb-4">�� Leg Exercises</h4>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Back Squats</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-10</p>
          <p class="text-white/60 text-xs">King of leg exercises</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Romanian Deadlifts</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 8-10</p>
          <p class="text-white/60 text-xs">Hamstring and glute focus</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Leg Press</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Machine compound for quads</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Lunges</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 10-12 each</p>
          <p class="text-white/60 text-xs">Unilateral leg development</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Leg Curls</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Hamstring isolation</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Calf Raises</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 4 | Reps: 15-20</p>
          <p class="text-white/60 text-xs">Calf muscle development</p>
         </div>
        </div>
       </div><!-- Core Exercises -->
       <div id="workout-core" class="workout-category hidden">
        <h4 class="text-xl font-bold text-white mb-4">🎯 Core Exercises</h4>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Planks</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Time: 60s</p>
          <p class="text-white/60 text-xs">Isometric core stability</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Russian Twists</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 20 each</p>
          <p class="text-white/60 text-xs">Oblique rotational strength</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Hanging Leg Raises</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12-15</p>
          <p class="text-white/60 text-xs">Lower abs focus</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Cable Crunches</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 15-20</p>
          <p class="text-white/60 text-xs">Weighted ab exercise</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Mountain Climbers</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 20 each</p>
          <p class="text-white/60 text-xs">Dynamic core and cardio</p>
         </div>
         <div class="glass rounded-2xl p-4">
          <h5 class="text-white font-semibold mb-2">Dead Bug</h5>
          <p class="text-white/70 text-sm mb-2">Sets: 3 | Reps: 12 each</p>
          <p class="text-white/60 text-xs">Core stability and control</p>
         </div>
        </div>
       </div>
      </div>
     </section><!-- Custom Plan Builder Section -->
     <section id="dash-custom-plan" class="dashboard-section hidden">
      <div class="glass-strong rounded-3xl p-6">
       <h3 class="text-2xl font-bold text-white mb-4">Build Your Custom Plan</h3>
       <p class="text-white/70 text-sm mb-6">Create a personalized workout plan tailored to your goals</p>
       <form id="custom-plan-form" class="space-y-6">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
         <div><label for="plan-name" class="block text-white text-sm font-medium mb-2">Plan Name</label> <input id="plan-name" type="text" required class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="My Custom Plan">
         </div>
         <div><label for="plan-duration" class="block text-white text-sm font-medium mb-2">Duration (weeks)</label> <input id="plan-duration" type="number" required min="1" max="52" class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring" placeholder="8">
         </div>
        </div>
        <div><label class="block text-white text-sm font-medium mb-2">Training Days per Week</label>
         <div class="grid grid-cols-3 md:grid-cols-7 gap-2"><label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Monday" class="custom-plan-day"> Mon </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Tuesday" class="custom-plan-day"> Tue </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Wednesday" class="custom-plan-day"> Wed </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Thursday" class="custom-plan-day"> Thu </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Friday" class="custom-plan-day"> Fri </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Saturday" class="custom-plan-day"> Sat </label> <label class="glass rounded-lg px-3 py-2 text-white text-sm flex items-center gap-2 cursor-pointer glass-hover"> <input type="checkbox" value="Sunday" class="custom-plan-day"> Sun </label>
         </div>
        </div>
        <div><label for="plan-focus" class="block text-white text-sm font-medium mb-2">Primary Focus</label> <select id="plan-focus" required class="w-full glass rounded-xl px-4 py-3 text-white focus-ring"> <option value="strength">Strength Building</option> <option value="hypertrophy">Muscle Growth</option> <option value="endurance">Endurance</option> <option value="fat_loss">Fat Loss</option> <option value="athletic">Athletic Performance</option> </select>
        </div>
        <div><label for="plan-notes" class="block text-white text-sm font-medium mb-2">Notes &amp; Goals</label> <textarea id="plan-notes" rows="4" class="w-full glass rounded-xl px-4 py-3 text-white placeholder-white/50 focus-ring resize-none" placeholder="Describe your goals and any specific requirements..."></textarea>
        </div>
        <div id="custom-plan-success" class="hidden glass rounded-xl px-4 py-3 text-green-300 text-sm">
         ✅ Custom plan created successfully!
        </div><button type="submit" id="custom-plan-btn" class="w-full glass-strong rounded-xl px-6 py-3 text-white font-semibold glass-hover focus-ring"> Create Custom Plan </button>
       </form><!-- Saved Custom Plans -->
       <div id="saved-plans-container" class="mt-8">
        <h4 class="text-xl font-bold text-white mb-4">Your Custom Plans</h4>
        <div id="saved-plans-list" class="space-y-4"><!-- Plans will be rendered here -->
        </div>
        <div id="no-plans" class="text-center py-8 text-white/70">
         No custom plans yet. Create your first plan above!
        </div>
       </div>
      </div>
     </section><!-- Workout Plans Section -->
     <section id="dash-plans" class="dashboard-section hidden">
      <div class="glass-strong rounded-3xl p-6">
       <h3 class="text-2xl font-bold text-white mb-4">Recommended Workout Plans</h3>
       <p class="text-white/70 text-sm mb-6">Choose a plan that matches your fitness goal</p>
       <div class="grid grid-cols-1 lg:grid-cols-3 gap-6"><!-- Beginner Plan -->
        <div class="glass rounded-2xl p-6 glass-hover">
         <div class="flex items-center justify-between mb-4">
          <h4 class="text-white font-bold text-lg">Beginner Build</h4><span class="glass rounded-full px-3 py-1 text-xs text-white">3 Days</span>
         </div>
         <p class="text-white/70 text-sm mb-4">Perfect for newcomers to build foundation</p>
         <div class="space-y-3">
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Monday</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Squats: 3×10</li>
            <li>• Push-ups: 3×8</li>
            <li>• Plank: 3×20s</li>
           </ul>
          </div>
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Wednesday</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Leg Press: 3×12</li>
            <li>• Dumbbell Press: 3×10</li>
            <li>• Dead Bug: 3×10</li>
           </ul>
          </div>
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Friday</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Lunges: 3×10</li>
            <li>• Shoulder Press: 3×10</li>
            <li>• Crunches: 3×20</li>
           </ul>
          </div>
         </div>
        </div><!-- Muscle Gain Plan -->
        <div class="glass rounded-2xl p-6 glass-hover">
         <div class="flex items-center justify-between mb-4">
          <h4 class="text-white font-bold text-lg">Muscle Builder</h4><span class="glass rounded-full px-3 py-1 text-xs text-white">4 Days</span>
         </div>
         <p class="text-white/70 text-sm mb-4">Upper/lower split for muscle growth</p>
         <div class="space-y-3">
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Mon - Upper</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Bench Press: 4×8</li>
            <li>• Barbell Row: 4×8</li>
            <li>• Shoulder Press: 3×10</li>
           </ul>
          </div>
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Tue - Lower</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Back Squat: 4×8</li>
            <li>• Romanian DL: 3×8</li>
            <li>• Leg Curl: 3×12</li>
           </ul>
          </div>
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Thu/Fri - Repeat</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Similar pattern</li>
            <li>• Different exercises</li>
            <li>• Progressive overload</li>
           </ul>
          </div>
         </div>
        </div><!-- Fat Loss Plan -->
        <div class="glass rounded-2xl p-6 glass-hover">
         <div class="flex items-center justify-between mb-4">
          <h4 class="text-white font-bold text-lg">Fat Burner</h4><span class="glass rounded-full px-3 py-1 text-xs text-white">5 Days</span>
         </div>
         <p class="text-white/70 text-sm mb-4">High intensity for maximum calorie burn</p>
         <div class="space-y-3">
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Mon/Wed/Fri</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Full body circuit</li>
            <li>• 5 exercises × 3 rounds</li>
            <li>• 10-12 reps each</li>
           </ul>
          </div>
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Tue/Thu</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• 20 min HIIT</li>
            <li>• 40s work / 20s rest</li>
            <li>• 10 min cool down</li>
           </ul>
          </div>
          <div class="glass rounded-xl p-3">
           <p class="text-white font-medium text-sm mb-2">Nutrition Tip</p>
           <ul class="text-white/80 text-xs space-y-1">
            <li>• Calorie deficit</li>
            <li>• High protein intake</li>
            <li>• Stay hydrated</li>
           </ul>
          </div>
         </div>
        </div>
       </div>
      </div>
     </section><!-- Notifications Section -->
     <section id="dash-notifications" class="dashboard-section hidden">
      <div class="glass-strong rounded-3xl p-6">
       <h3 class="text-2xl font-bold text-white mb-6">Notifications</h3>
       <div id="notifications-list" class="space-y-4"><!-- Notifications will be rendered here -->
       </div>
       <div id="no-notifications" class="hidden text-center py-12">
        <div class="text-6xl mb-4">
         🔔
        </div>
        <p class="text-white/70">No new notifications</p>
       </div>
      </div>
     </section>
    </main>
   </div>
  </div>
  <script>
    // Global state
    let currentUser = null;
    let allUsers = [];
    let customPlans = [];
    let isDarkMode = true;
    
    // Theme toggle function
    function toggleTheme() {
      isDarkMode = !isDarkMode;
      
      if (isDarkMode) {
        document.body.classList.remove('light-mode');
        document.getElementById('theme-icon').textContent = '🌙';
        const dashIcon = document.getElementById('theme-icon-dash');
        if (dashIcon) dashIcon.textContent = '🌙';
        localStorage.setItem('theme', 'dark');
      } else {
        document.body.classList.add('light-mode');
        document.getElementById('theme-icon').textContent = '☀️';
        const dashIcon = document.getElementById('theme-icon-dash');
        if (dashIcon) dashIcon.textContent = '☀️';
        localStorage.setItem('theme', 'light');
      }
    }
    
    // Load saved theme preference
    function loadTheme() {
      const savedTheme = localStorage.getItem('theme');
      if (savedTheme === 'light') {
        isDarkMode = true; // Set to true so toggle switches to light
        toggleTheme();
      }
    }
    
    // Sample members data (10 members)
    const sampleMembers = [
      {
        id: '1001',
        name: 'Rahul Sharma',
        email: 'rahul.sharma@email.com',
        phone: '9876543210',
        password: 'password123',
        subscription_months: 6,
        start_date: '2024-01-15T00:00:00.000Z',
        shift: 'morning',
        goal: 'muscle_gain',
        preferred_days: 'Monday, Wednesday, Friday',
        notifications: JSON.stringify([]),
        created_at: '2024-01-15T00:00:00.000Z'
      },
      {
        id: '1002',
        name: 'Priya Patel',
        email: 'priya.patel@email.com',
        phone: '9876543211',
        password: 'password123',
        subscription_months: 12,
        start_date: '2024-02-01T00:00:00.000Z',
        shift: 'evening',
        goal: 'weight_loss',
        preferred_days: 'Tuesday, Thursday, Saturday',
        notifications: JSON.stringify([]),
        created_at: '2024-02-01T00:00:00.000Z'
      },
      {
        id: '1003',
        name: 'Amit Kumar',
        email: 'amit.kumar@email.com',
        phone: '9876543212',
        password: 'password123',
        subscription_months: 3,
        start_date: '2024-03-10T00:00:00.000Z',
        shift: 'morning',
        goal: 'fitness',
        preferred_days: 'Monday, Tuesday, Wednesday, Thursday, Friday',
        notifications: JSON.stringify([]),
        created_at: '2024-03-10T00:00:00.000Z'
      },
      {
        id: '1004',
        name: 'Sneha Reddy',
        email: 'sneha.reddy@email.com',
        phone: '9876543213',
        password: 'password123',
        subscription_months: 6,
        start_date: '2024-01-20T00:00:00.000Z',
        shift: 'evening',
        goal: 'strength',
        preferred_days: 'Monday, Wednesday, Friday, Saturday',
        notifications: JSON.stringify([]),
        created_at: '2024-01-20T00:00:00.000Z'
      },
      {
        id: '1005',
        name: 'Vikram Singh',
        email: 'vikram.singh@email.com',
        phone: '9876543214',
        password: 'password123',
        subscription_months: 12,
        start_date: '2023-12-01T00:00:00.000Z',
        shift: 'morning',
        goal: 'muscle_gain',
        preferred_days: 'Monday, Tuesday, Thursday, Friday',
        notifications: JSON.stringify([]),
        created_at: '2023-12-01T00:00:00.000Z'
      },
      {
        id: '1006',
        name: 'Anjali Verma',
        email: 'anjali.verma@email.com',
        phone: '9876543215',
        password: 'password123',
        subscription_months: 1,
        start_date: '2024-03-25T00:00:00.000Z',
        shift: 'evening',
        goal: 'weight_loss',
        preferred_days: 'Monday, Wednesday, Friday',
        notifications: JSON.stringify([]),
        created_at: '2024-03-25T00:00:00.000Z'
      },
      {
        id: '1007',
        name: 'Rohan Gupta',
        email: 'rohan.gupta@email.com',
        phone: '9876543216',
        password: 'password123',
        subscription_months: 6,
        start_date: '2024-02-15T00:00:00.000Z',
        shift: 'morning',
        goal: 'fitness',
        preferred_days: 'Tuesday, Thursday, Saturday',
        notifications: JSON.stringify([]),
        created_at: '2024-02-15T00:00:00.000Z'
      },
      {
        id: '1008',
        name: 'Kavya Nair',
        email: 'kavya.nair@email.com',
        phone: '9876543217',
        password: 'password123',
        subscription_months: 3,
        start_date: '2024-03-01T00:00:00.000Z',
        shift: 'evening',
        goal: 'strength',
        preferred_days: 'Monday, Wednesday, Friday, Saturday',
        notifications: JSON.stringify([]),
        created_at: '2024-03-01T00:00:00.000Z'
      },
      {
        id: '1009',
        name: 'Arjun Mehta',
        email: 'arjun.mehta@email.com',
        phone: '9876543218',
        password: 'password123',
        subscription_months: 12,
        start_date: '2023-11-15T00:00:00.000Z',
        shift: 'morning',
        goal: 'muscle_gain',
        preferred_days: 'Monday, Tuesday, Wednesday, Thursday, Friday',
        notifications: JSON.stringify([]),
        created_at: '2023-11-15T00:00:00.000Z'
      },
      {
        id: '1010',
        name: 'Divya Iyer',
        email: 'divya.iyer@email.com',
        phone: '9876543219',
        password: 'password123',
        subscription_months: 6,
        start_date: '2024-01-05T00:00:00.000Z',
        shift: 'evening',
        goal: 'weight_loss',
        preferred_days: 'Tuesday, Thursday, Saturday',
        notifications: JSON.stringify([]),
        created_at: '2024-01-05T00:00:00.000Z'
      }
    ];
    
    // Page navigation
    function showPage(pageName) {
      const pages = ['landing', 'login', 'register', 'dashboard'];
      pages.forEach(p => {
        const el = document.getElementById(`page-${p}`);
        if (el) {
          el.classList.toggle('hidden', p !== pageName);
        }
      });
      
      if (pageName === 'dashboard' && currentUser) {
        renderDashboard();
        showDashboardSection('profile');
      }
    }
    
    // Dashboard section navigation
    function showDashboardSection(section) {
      const sections = ['profile', 'schedule', 'workouts', 'custom-plan', 'plans', 'notifications'];
      sections.forEach(s => {
        const el = document.getElementById(`dash-${s}`);
        if (el) {
          el.classList.toggle('hidden', s !== section);
        }
      });
      
      // Update tab styles
      document.querySelectorAll('.dash-tab').forEach(tab => {
        if (tab.dataset.section === section) {
          tab.classList.add('glass-strong');
        } else {
          tab.classList.remove('glass-strong');
        }
      });
      
      if (section === 'notifications') {
        renderNotifications();
      } else if (section === 'workouts') {
        showWorkoutCategory('chest');
      } else if (section === 'custom-plan') {
        renderSavedPlans();
      }
    }
    
    // Workout category navigation
    function showWorkoutCategory(category) {
      const categories = ['chest', 'back', 'shoulders', 'arms', 'legs', 'core'];
      categories.forEach(c => {
        const el = document.getElementById(`workout-${c}`);
        if (el) {
          el.classList.toggle('hidden', c !== category);
        }
      });
      
      // Update tab styles
      document.querySelectorAll('.workout-tab').forEach(tab => {
        if (tab.dataset.category === category) {
          tab.classList.add('glass-strong');
        } else {
          tab.classList.remove('glass-strong');
        }
      });
    }
    
    // Calculate days remaining
    function calculateDaysRemaining(startDate, months) {
      const start = new Date(startDate);
      const end = new Date(start);
      end.setMonth(end.getMonth() + months);
      
      const now = new Date();
      const diffTime = end - now;
      const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
      
      return {
        daysLeft: Math.max(0, diffDays),
        endDate: end,
        totalDays: Math.ceil((end - start) / (1000 * 60 * 60 * 24))
      };
    }
    
    // Render dashboard
    function renderDashboard() {
      if (!currentUser) return;
      
      // Profile section
      document.getElementById('user-name-nav').textContent = currentUser.name;
      document.getElementById('profile-name').textContent = currentUser.name;
      document.getElementById('profile-email').textContent = currentUser.email;
      document.getElementById('profile-phone').textContent = currentUser.phone;
      
      const goalMap = {
        'weight_loss': 'Weight Loss',
        'muscle_gain': 'Muscle Gain',
        'fitness': 'General Fitness',
        'strength': 'Strength Training'
      };
      document.getElementById('profile-goal').textContent = goalMap[currentUser.goal] || currentUser.goal;
      
      const shiftMap = {
        'morning': 'Morning (6 AM - 12 PM)',
        'evening': 'Evening (4 PM - 10 PM)'
      };
      document.getElementById('profile-shift').textContent = shiftMap[currentUser.shift] || currentUser.shift;
      document.getElementById('schedule-shift').textContent = shiftMap[currentUser.shift] || currentUser.shift;
      
      document.getElementById('profile-days').textContent = currentUser.preferred_days || 'Not set';
      
      // Subscription info
      const subInfo = calculateDaysRemaining(currentUser.start_date, currentUser.subscription_months);
      
      document.getElementById('sub-duration').textContent = `${currentUser.subscription_months} ${currentUser.subscription_months === 1 ? 'Month' : 'Months'}`;
      document.getElementById('sub-days-left').textContent = subInfo.daysLeft;
      document.getElementById('sub-end-date').textContent = subInfo.endDate.toLocaleDateString('en-IN', { 
        day: 'numeric', 
        month: 'short', 
        year: 'numeric' 
      });
      
      // Progress bar
      const progress = ((subInfo.totalDays - subInfo.daysLeft) / subInfo.totalDays) * 100;
      document.getElementById('sub-progress').style.width = `${progress}%`;
      
      // Show warning if less than 7 days
      if (subInfo.daysLeft <= 7 && subInfo.daysLeft > 0) {
        addNotification('���️ Subscription Expiring Soon', `Your subscription expires in ${subInfo.daysLeft} days. Renew now!`, 'warning');
      }
    }
    
    // Render notifications
    function renderNotifications() {
      const container = document.getElementById('notifications-list');
      const noNotif = document.getElementById('no-notifications');
      
      const notifications = currentUser.notifications ? JSON.parse(currentUser.notifications) : [];
      
      if (notifications.length === 0) {
        container.classList.add('hidden');
        noNotif.classList.remove('hidden');
        document.getElementById('notif-badge').classList.add('hidden');
        return;
      }
      
      container.classList.remove('hidden');
      noNotif.classList.add('hidden');
      document.getElementById('notif-badge').textContent = notifications.length;
      document.getElementById('notif-badge').classList.remove('hidden');
      
      container.innerHTML = notifications.map((notif, idx) => `
        <div class="glass rounded-2xl p-5 glass-hover">
          <div class="flex items-start justify-between gap-4">
            <div class="flex-1">
              <div class="flex items-center gap-2 mb-2">
                <span class="text-2xl">${notif.icon}</span>
                <h4 class="text-white font-semibold">${notif.title}</h4>
              </div>
              <p class="text-white/70 text-sm">${notif.message}</p>
              <p class="text-white/50 text-xs mt-2">${notif.time}</p>
            </div>
            <button onclick="removeNotification(${idx})" class="glass rounded-full p-2 text-white/70 hover:text-white glass-hover text-sm">
              ✕
            </button>
          </div>
        </div>
      `).join('');
    }
    
    // Add notification
    function addNotification(title, message, type = 'info') {
      if (!currentUser) return;
      
      const icons = {
        'info': 'ℹ️',
        'warning': '⚠️',
        'success': '���',
        'alert': '🔔'
      };
      
      const notifications = currentUser.notifications ? JSON.parse(currentUser.notifications) : [];
      notifications.unshift({
        icon: icons[type] || icons.info,
        title,
        message,
        time: new Date().toLocaleString('en-IN', { 
          day: 'numeric', 
          month: 'short', 
          hour: '2-digit', 
          minute: '2-digit' 
        })
      });
      
      currentUser.notifications = JSON.stringify(notifications.slice(0, 10)); // Keep last 10
      
      // Update in database
      if (window.dataSdk) {
        window.dataSdk.update(currentUser);
      }
    }
    
    // Remove notification
    async function removeNotification(index) {
      if (!currentUser) return;
      
      const notifications = JSON.parse(currentUser.notifications);
      notifications.splice(index, 1);
      currentUser.notifications = JSON.stringify(notifications);
      
      if (window.dataSdk) {
        const result = await window.dataSdk.update(currentUser);
        if (result.isOk) {
          renderNotifications();
        }
      }
    }
    
    // Render saved custom plans
    function renderSavedPlans() {
      const container = document.getElementById('saved-plans-list');
      const noPlans = document.getElementById('no-plans');
      
      const userPlans = customPlans.filter(p => p.user_id === currentUser.id);
      
      if (userPlans.length === 0) {
        container.classList.add('hidden');
        noPlans.classList.remove('hidden');
        return;
      }
      
      container.classList.remove('hidden');
      noPlans.classList.add('hidden');
      
      container.innerHTML = userPlans.map(plan => `
        <div class="glass rounded-2xl p-5">
          <div class="flex items-start justify-between mb-3">
            <div>
              <h5 class="text-white font-bold text-lg mb-1">${plan.plan_name}</h5>
              <p class="text-white/70 text-sm">${plan.duration} weeks • ${plan.training_days}</p>
            </div>
            <span class="glass rounded-full px-3 py-1 text-xs text-white">${plan.focus}</span>
          </div>
          ${plan.notes ? `<p class="text-white/60 text-sm mb-3">${plan.notes}</p>` : ''}
          <p class="text-white/50 text-xs">Created: ${new Date(plan.created_at).toLocaleDateString('en-IN')}</p>
        </div>
      `).join('');
    }
    
    // Logout
    function logout() {
      currentUser = null;
      showPage('landing');
    }
    
    // Contact form
    document.getElementById('contact-form').addEventListener('submit', (e) => {
      e.preventDefault();
      
      const successEl = document.getElementById('contact-success');
      const btn = document.getElementById('contact-btn');
      
      btn.textContent = 'Sending...';
      btn.disabled = true;
      
      setTimeout(() => {
        successEl.classList.remove('hidden');
        document.getElementById('contact-form').reset();
        btn.textContent = 'Send Message';
        btn.disabled = false;
        
        setTimeout(() => {
          successEl.classList.add('hidden');
        }, 5000);
      }, 1000);
    });
    
    // Login form
    document.getElementById('login-form').addEventListener('submit', async (e) => {
      e.preventDefault();
      
      const email = document.getElementById('login-email').value.trim();
      const password = document.getElementById('login-password').value;
      const errorEl = document.getElementById('login-error');
      const btn = document.getElementById('login-btn');
      
      btn.textContent = 'Logging in...';
      btn.disabled = true;
      
      // Find user
      const user = allUsers.find(u => u.email === email && u.password === password);
      
      if (user) {
        currentUser = user;
        errorEl.classList.add('hidden');
        showPage('dashboard');
        
        // Welcome notification
        addNotification('👋 Welcome Back!', `Good to see you, ${user.name}!`, 'success');
      } else {
        errorEl.classList.remove('hidden');
      }
      
      btn.textContent = 'Login';
      btn.disabled = false;
    });
    
    // Registration form
    document.getElementById('register-form').addEventListener('submit', async (e) => {
      e.preventDefault();
      
      if (allUsers.length >= 999) {
        const errorEl = document.getElementById('register-error');
        errorEl.textContent = 'Maximum member limit reached (999). Please contact gym administration.';
        errorEl.classList.remove('hidden');
        return;
      }
      
      const name = document.getElementById('reg-name').value.trim();
      const phone = document.getElementById('reg-phone').value.trim();
      const email = document.getElementById('reg-email').value.trim();
      const password = document.getElementById('reg-password').value;
      const goal = document.getElementById('reg-goal').value;
      const shift = document.getElementById('reg-shift').value;
      const subscription = parseInt(document.getElementById('reg-subscription').value);
      
      const dayCheckboxes = document.querySelectorAll('.reg-day:checked');
      const preferredDays = Array.from(dayCheckboxes).map(cb => cb.value).join(', ');
      
      const errorEl = document.getElementById('register-error');
      const btn = document.getElementById('register-btn');
      
      // Check if email exists
      if (allUsers.find(u => u.email === email)) {
        errorEl.textContent = 'Email already registered. Please login.';
        errorEl.classList.remove('hidden');
        return;
      }
      
      btn.textContent = 'Registering...';
      btn.disabled = true;
      errorEl.classList.add('hidden');
      
      const newUser = {
        id: Date.now().toString(),
        name,
        email,
        phone,
        password,
        subscription_months: subscription,
        start_date: new Date().toISOString(),
        shift,
        goal,
        preferred_days: preferredDays,
        notifications: JSON.stringify([
          {
            icon: '🎉',
            title: 'Welcome to NBL Gym!',
            message: 'Your fitness journey starts now. Check out your weekly schedule and workout plans.',
            time: new Date().toLocaleString('en-IN', { 
              day: 'numeric', 
              month: 'short', 
              hour: '2-digit', 
              minute: '2-digit' 
            })
          }
        ]),
        created_at: new Date().toISOString()
      };
      
      if (window.dataSdk) {
        const result = await window.dataSdk.create(newUser);
        
        if (result.isOk) {
          currentUser = newUser;
          showPage('dashboard');
        } else {
          errorEl.textContent = 'Registration failed. Please try again.';
          errorEl.classList.remove('hidden');
        }
      }
      
      btn.textContent = 'Register & Join';
      btn.disabled = false;
    });
    
    // Custom plan form
    document.getElementById('custom-plan-form').addEventListener('submit', async (e) => {
      e.preventDefault();
      
      if (customPlans.length >= 999) {
        const successEl = document.getElementById('custom-plan-success');
        successEl.textContent = '⚠️ Maximum plan limit reached (999).';
        successEl.classList.remove('hidden');
        successEl.classList.add('text-red-300');
        return;
      }
      
      const planName = document.getElementById('plan-name').value.trim();
      const duration = parseInt(document.getElementById('plan-duration').value);
      const focus = document.getElementById('plan-focus').value;
      const notes = document.getElementById('plan-notes').value.trim();
      
      const dayCheckboxes = document.querySelectorAll('.custom-plan-day:checked');
      const trainingDays = Array.from(dayCheckboxes).map(cb => cb.value).join(', ');
      
      const successEl = document.getElementById('custom-plan-success');
      const btn = document.getElementById('custom-plan-btn');
      
      btn.textContent = 'Creating...';
      btn.disabled = true;
      
      const newPlan = {
        id: Date.now().toString(),
        user_id: currentUser.id,
        plan_name: planName,
        duration: duration,
        training_days: trainingDays,
        focus: focus,
        notes: notes,
        created_at: new Date().toISOString()
      };
      
      if (window.dataSdk) {
        const result = await window.dataSdk.create(newPlan);
        
        if (result.isOk) {
          successEl.classList.remove('hidden', 'text-red-300');
          successEl.classList.add('text-green-300');
          successEl.textContent = '✅ Custom plan created successfully!';
          document.getElementById('custom-plan-form').reset();
          
          setTimeout(() => {
            successEl.classList.add('hidden');
            renderSavedPlans();
          }, 2000);
        }
      }
      
      btn.textContent = 'Create Custom Plan';
      btn.disabled = false;
    });
    
    // Sidebar toggle functionality
    function openSidebar() {
      const sidebar = document.getElementById('sidebar-menu');
      const overlay = document.getElementById('sidebar-overlay');
      
      sidebar.classList.remove('translate-x-full');
      overlay.classList.remove('hidden');
      document.body.style.overflow = 'hidden';
    }
    
    function closeSidebar() {
      const sidebar = document.getElementById('sidebar-menu');
      const overlay = document.getElementById('sidebar-overlay');
      
      sidebar.classList.add('translate-x-full');
      overlay.classList.add('hidden');
      document.body.style.overflow = '';
    }
    
    function scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      if (section) {
        section.scrollIntoView({ behavior: 'smooth', block: 'start' });
      }
    }
    

    
    // Load sample members into database if empty
    async function loadSampleMembers() {
      if (!window.dataSdk) return;
      
      // Wait a bit for SDK to initialize
      await new Promise(resolve => setTimeout(resolve, 500));
      
      // Check if database is empty
      if (allUsers.length === 0) {
        for (const member of sampleMembers) {
          await window.dataSdk.create(member);
        }
      }
    }
    
    // Data SDK initialization
    (async function initDataSdk() {
      if (!window.dataSdk) return;
      
      const dataHandler = {
        onDataChanged(data) {
          // Separate users and custom plans
          allUsers = data.filter(item => item.email && item.password);
          customPlans = data.filter(item => item.plan_name && item.user_id);
          
          // Update current user if logged in
          if (currentUser) {
            const updated = allUsers.find(u => u.id === currentUser.id);
            if (updated) {
              currentUser = updated;
              if (document.getElementById('page-dashboard').classList.contains('hidden') === false) {
                renderDashboard();
              }
            }
          }
        }
      };
      
      const initResult = await window.dataSdk.init(dataHandler);
      if (!initResult.isOk) {
        console.error('Failed to initialize Data SDK');
      } else {
        // Load sample members if database is empty
        await loadSampleMembers();
      }
    })();
    
    // Element SDK initialization
    (async function initElementSdk() {
      if (!window.elementSdk) return;
      
      const defaultConfig = {
        gym_name: 'NBL GYM',
        tagline: 'Transform Your Body, Elevate Your Mind',
        welcome_message: 'Join hundreds of fitness enthusiasts achieving their goals at NBL Gym',
        background_color_1: '#667eea',
        background_color_2: '#764ba2',
        glass_color: '#ffffff',
        text_color: '#ffffff',
        accent_color: '#f093fb',
        font_family: 'Inter',
        font_size: 16
      };
      
      async function onConfigChange(config) {
        const merged = { ...defaultConfig, ...config };
        
        // Update text content
        const gymNameEl = document.getElementById('gym-name');
        const headerGymNameEl = document.getElementById('header-gym-name');
        const taglineEl = document.getElementById('tagline');
        const welcomeEl = document.getElementById('welcome-message');
        
        if (gymNameEl) gymNameEl.textContent = merged.gym_name;
        if (headerGymNameEl) headerGymNameEl.textContent = merged.gym_name;
        if (taglineEl) taglineEl.textContent = merged.tagline;
        if (welcomeEl) welcomeEl.textContent = merged.welcome_message;
        
        // Update colors
        const root = document.getElementById('app-root');
        if (root) {
          root.style.background = `linear-gradient(135deg, ${merged.background_color_1} 0%, ${merged.background_color_2} 50%, ${merged.accent_color} 100%)`;
          root.style.backgroundSize = '400% 400%';
        }
        
        // Update font
        const fontStack = `${merged.font_family}, system-ui, -apple-system, sans-serif`;
        const baseSize = merged.font_size;
        
        document.body.style.fontFamily = fontStack;
        document.body.style.fontSize = `${baseSize}px`;
        
        // Scale typography
        document.querySelectorAll('h1').forEach(el => {
          el.style.fontSize = `${baseSize * 2.5}px`;
        });
        document.querySelectorAll('h2').forEach(el => {
          el.style.fontSize = `${baseSize * 1.75}px`;
        });
        document.querySelectorAll('h3').forEach(el => {
          el.style.fontSize = `${baseSize * 1.25}px`;
        });
        document.querySelectorAll('p, button, input, select').forEach(el => {
          el.style.fontSize = `${baseSize * 0.875}px`;
        });
      }
      
      function mapToCapabilities(config) {
        const merged = { ...defaultConfig, ...config };
        
        return {
          recolorables: [
            {
              get: () => merged.background_color_1,
              set: (value) => window.elementSdk.setConfig({ background_color_1: value })
            },
            {
              get: () => merged.background_color_2,
              set: (value) => window.elementSdk.setConfig({ background_color_2: value })
            },
            {
              get: () => merged.accent_color,
              set: (value) => window.elementSdk.setConfig({ accent_color: value })
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => merged.font_family,
            set: (value) => window.elementSdk.setConfig({ font_family: value })
          },
          fontSizeable: {
            get: () => merged.font_size,
            set: (value) => window.elementSdk.setConfig({ font_size: value })
          }
        };
      }
      
      function mapToEditPanelValues(config) {
        const merged = { ...defaultConfig, ...config };
        return new Map([
          ['gym_name', merged.gym_name],
          ['tagline', merged.tagline],
          ['welcome_message', merged.welcome_message]
        ]);
      }
      
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
      
      await onConfigChange(window.elementSdk.config || defaultConfig);
    })();
    
    // Menu toggle button event
    const menuToggleBtn = document.getElementById('menu-toggle-btn');
    if (menuToggleBtn) {
      menuToggleBtn.addEventListener('click', openSidebar);
    }
    
    // Initialize
    loadTheme();
    showPage('landing');
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9a502269f32bc1c5',t:'MTc2NDIzMDg3My4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
