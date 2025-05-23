# on-je
<!DOCTYPE html>
<html lang="bs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Freestyle Video Pro - Profesionalno Video Uređivanje</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #0f0f1e 0%, #1a1a2e 50%, #16213e 100%);
            color: #ffffff;
            overflow-x: hidden;
        }

        /* Animated background particles */
        .bg-particles {
            position: fixed;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background: rgba(99, 102, 241, 0.3);
            border-radius: 50%;
            animation: float 8s infinite ease-in-out;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); opacity: 0; }
            50% { transform: translateY(-20px) rotate(180deg); opacity: 1; }
        }

        /* Glassmorphism utility */
        .glass {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
        }

        /* Header */
        .header {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1rem 2rem;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        .header.scrolled {
            background: rgba(15, 15, 30, 0.9);
            backdrop-filter: blur(20px);
        }

        .nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, #6366f1, #8b5cf6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-link {
            color: #e5e7eb;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-link:hover {
            color: #6366f1;
        }

        .nav-link::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: #6366f1;
            transition: width 0.3s ease;
        }

        .nav-link:hover::after {
            width: 100%;
        }

        .cta-button {
            padding: 0.75rem 1.5rem;
            background: linear-gradient(135deg, #6366f1, #8b5cf6);
            border: none;
            border-radius: 25px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(99, 102, 241, 0.3);
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 2rem;
            position: relative;
        }

        .hero-content {
            max-width: 800px;
            z-index: 2;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 700;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, #ffffff, #e5e7eb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1.2;
        }

        .hero-subtitle {
            font-size: 1.25rem;
            color: #9ca3af;
            margin-bottom: 2rem;
            line-height: 1.6;
        }

        .hero-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .button-primary {
            padding: 1rem 2rem;
            font-size: 1.1rem;
            background: linear-gradient(135deg, #6366f1, #8b5cf6);
            border: none;
            border-radius: 30px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .button-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 40px rgba(99, 102, 241, 0.4);
        }

        .button-secondary {
            padding: 1rem 2rem;
            font-size: 1.1rem;
            background: transparent;
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 30px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .button-secondary:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: rgba(255, 255, 255, 0.3);
        }

        /* 3D floating elements */
        .floating-element {
            position: absolute;
            background: rgba(99, 102, 241, 0.1);
            border: 1px solid rgba(99, 102, 241, 0.2);
            border-radius: 20px;
            backdrop-filter: blur(10px);
            animation: floatSlow 6s ease-in-out infinite;
        }

        .floating-element:nth-child(1) {
            top: 20%;
            left: 10%;
            width: 60px;
            height: 60px;
            animation-delay: 0s;
        }

        .floating-element:nth-child(2) {
            top: 60%;
            right: 15%;
            width: 80px;
            height: 80px;
            animation-delay: 2s;
        }

        .floating-element:nth-child(3) {
            bottom: 30%;
            left: 5%;
            width: 40px;
            height: 40px;
            animation-delay: 4s;
        }

        @keyframes floatSlow {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-15px) rotate(180deg); }
        }

        /* Sections */
        .section {
            padding: 5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
            text-align: center;
            margin-bottom: 3rem;
            background: linear-gradient(135deg, #ffffff, #e5e7eb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* Features Grid */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .feature-card {
            padding: 2rem;
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.5), transparent);
        }

        .feature-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.05);
            box-shadow: 0 20px 40px rgba(99, 102, 241, 0.1);
        }

        .feature-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #6366f1, #8b5cf6);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
            font-size: 1.5rem;
        }

        .feature-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 1rem;
            color: #ffffff;
        }

        .feature-description {
            color: #9ca3af;
            line-height: 1.6;
        }

        /* Pricing Section */
        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .pricing-card {
            padding: 2.5rem;
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            text-align: center;
            position: relative;
            transition: all 0.3s ease;
        }

        .pricing-card.featured {
            border: 2px solid #6366f1;
            transform: scale(1.05);
        }

        .pricing-card.featured::before {
            content: 'NAJPOPULARNIJI';
            position: absolute;
            top: -15px;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(135deg, #6366f1, #8b5cf6);
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .pricing-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(99, 102, 241, 0.15);
        }

        .pricing-card.featured:hover {
            transform: scale(1.05) translateY(-5px);
        }

        .plan-name {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 1rem;
        }

        .plan-price {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            background: linear-gradient(135deg, #6366f1, #8b5cf6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .plan-period {
            color: #9ca3af;
            margin-bottom: 2rem;
        }

        .plan-features {
            list-style: none;
            margin-bottom: 2rem;
        }

        .plan-features li {
            padding: 0.5rem 0;
            color: #e5e7eb;
            position: relative;
            padding-left: 1.5rem;
        }

        .plan-features li::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: #10b981;
            font-weight: bold;
        }

        /* Security Section */
        .security-features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .security-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            background: rgba(255, 255, 255, 0.02);
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .security-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #10b981, #059669);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }

        /* Footer */
        .footer {
            background: rgba(0, 0, 0, 0.3);
            padding: 3rem 2rem 1rem;
            text-align: center;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .footer-link {
            color: #9ca3af;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-link:hover {
            color: #6366f1;
        }

        .footer-bottom {
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #6b7280;
        }

        /* Mobile Responsiveness */
        @media (max-width: 768px) {
            .nav-menu {
                display: none;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .section {
                padding: 3rem 1rem;
            }

            .features-grid,
            .pricing-grid {
                grid-template-columns: 1fr;
            }

            .pricing-card.featured {
                transform: none;
            }

            .pricing-card.featured:hover {
                transform: translateY(-5px);
            }
        }

        /* Scroll animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Background particles -->
    <div class="bg-particles" id="particles"></div>

    <!-- Header -->
    <header class="header" id="header">
        <nav class="nav">
            <div class="logo">Freestyle Video Pro</div>
            <ul class="nav-menu">
                <li><a href="#features" class="nav-link">Funkcije</a></li>
                <li><a href="#pricing" class="nav-link">Cene</a></li>
                <li><a href="#security" class="nav-link">Sigurnost</a></li>
                <li><a href="#contact" class="nav-link">Kontakt</a></li>
            </ul>
            <a href="#pricing" class="cta-button">Počni Besplatno</a>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="floating-element"></div>
        <div class="floating-element"></div>
        <div class="floating-element"></div>
        
        <div class="hero-content fade-in">
            <h1>Budućnost Video Uređivanja</h1>
            <p class="hero-subtitle">
                Profesionalno video uređivanje sa naprednom AI tehnologijom. 
                Adaptivno 3D okruženje koje se prilagođava vašem radu kroz inteligentne kontrole i prediktivne predloge.
            </p>
            <div class="hero-buttons">
                <a href="#" class="button-primary">Počni 7-Dnevno Testiranje</a>
                <a href="#features" class="button-secondary">Pogledaj Funkcije</a>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section class="section" id="features">
        <h2 class="section-title fade-in">Napredne AI Funkcije</h2>
        <div class="features-grid">
            <div class="feature-card fade-in">
                <div class="feature-icon">🎬</div>
                <h3 class="feature-title">Adaptivno 3D Okruženje</h3>
                <p class="feature-description">
                    Morfno pozadina koje se adaptira kontekstu uređivanja sa plutajućim staklenim panelima i pametnom transparentnošću.
                </p>
            </div>
            <div class="feature-card fade-in">
                <div class="feature-icon">🤖</div>
                <h3 class="feature-title">AI Prediktivni Alati</h3>
                <p class="feature-description">
                    Kontekstno svesni alati sa radijalnim menijem za brz pristup i AI predlozima koji predviđaju vaše potrebe.
                </p>
            </div>
            <div class="feature-card fade-in">
                <div class="feature-icon">⚡</div>
                <h3 class="feature-title">GPU Ubrzanje</h3>
                <p class="feature-description">
                    Multi-threaded procesiranje sa GPU ubrzanjem za profesionalne kodeke i optimizaciju za društvene mreže.
                </p>
            </div>
            <div class="feature-card fade-in">
                <div class="feature-icon">🌍</div>
                <h3 class="feature-title">100+ Jezika</h3>
                <p class="feature-description">
                    Automatska detekcija i prevod na više od 100 jezika sa regionalnom adaptacijom sadržaja.
                </p>
            </div>
            <div class="feature-card fade-in">
                <div class="feature-icon">☁️</div>
                <h3 class="feature-title">Cloud Sinhronizacija</h3>
                <p class="feature-description">
                    Automatski backup u cloud sa sinhronizacijom kroz uređaje i pametnom alokacijom resursa.
                </p>
            </div>
            <div class="feature-card fade-in">
                <div class="feature-icon">🎯</div>
                <h3 class="feature-title">Profesionalna Preciznost</h3>
                <p class="feature-description">
                    Profesionalne kontrole preciznosti optimizovane za dodir sa automatskim otkrivanjem i ispravkom grešaka.
                </p>
            </div>
        </div>
    </section>

    <!-- Pricing Section -->
    <section class="section" id="pricing">
        <h2 class="section-title fade-in">Fleksibilne Cene</h2>
        <div class="pricing-grid">
            <div class="pricing-card fade-in">
                <h3 class="plan-name">Bosna i Hercegovina</h3>
                <div class="plan-price">15 KM</div>
                <div class="plan-period">mesečno</div>
                <ul class="plan-features">
                    <li>Sve profesionalne funkcije</li>
                    <li>AI napredni alati</li>
                    <li>Neograničeni eksport</li>
                    <li>Cloud storage 100GB</li>
                    <li>Prioritetna podrška</li>
                    <li>Regionalna optimizacija</li>
                </ul>
                <a href="#" class="button-primary">Započni Sada</a>
            </div>
            <div class="pricing-card featured fade-in">
                <h3 class="plan-name">Međunarodna</h3>
                <div class="plan-price">$30</div>
                <div class="plan-period">mesečno</div>
                <ul class="plan-features">
                    <li>Sve profesionalne funkcije</li>
                    <li>AI napredni alati</li>
                    <li>Neograničeni eksport</li>
                    <li>Cloud storage 500GB</li>
                    <li>24/7 prioritetna podrška</li>
                    <li>Globalna optimizacija</li>
                    <li>Rani pristup novim funkcijama</li>
                </ul>
                <a href="#" class="button-primary">Započni Sada</a>
            </div>
        </div>
        <div style="text-align: center; margin-top: 2rem; color: #9ca3af;">
            <p>✨ 7-dnevno besplatno testiranje za sve planove</p>
            <p>🔒 Striktna politika jednog naloga po korisniku</p>
        </div>
    </section>

    <!-- Security Section -->
    <section class="section" id="security">
        <h2 class="section-title fade-in">Vojna Sigurnost</h2>
        <div class="security-features fade-in">
            <div class="security-item">
                <div class="security-icon">🔐</div>
                <div>
                    <h4>Militar-Grade Enkripcija</h4>
                    <p>Napredna enkripcija za maksimalnu sigurnost podataka</p>
                </div>
            </div>
            <div class="security-item">
                <div class="security-icon">📱</div>
                <div>
                    <h4>Jedinstveni Device Fingerprint</h4>
                    <p>Napredna zaštita od pravljenja duplikata naloga</p>
                </div>
            </div>
            <div class="security-item">
                <div class="security-icon">🛡️</div>
                <div>
                    <h4>Multi-Factor Autentifikacija</h4>
                    <p>Dodatni sloj sigurnosti za vaš nalog</p>
                </div>
            </div>
            <div class="security-item">
                <div class="security-icon">🌐</div>
                <div>
                    <h4>IP/VPN Detekcija</h4>
                    <p>Napredna detekcija i sprečavanje zloupotrebe</p>
                </div>
            </div>
            <div class="security-item">
                <div class="security-icon">💳</div>
                <div>
                    <h4>Sigurno Plaćanje</h4>
                    <p>PCI DSS sertifikovano procesiranje plaćanja</p>
                </div>
            </div>
            <div class="security-item">
                <div class="security-icon">🔍</div>
                <div>
                    <h4>Real-Time Fraud Detekcija</h4>
                    <p>Automatska detekcija i sprečavanje prevara</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer" id="contact">
        <div class="footer-content">
            <div class="footer-links">
                <a href="#" class="footer-link">Uslovi Korišćenja</a>
                <a href="#" class="footer-link">Privatnost</a>
                <a href="#" class="footer-link">Podrška</a>
                <a href="#" class="footer-link">API Dokumentacija</a>
                <a href="#" class="footer-link">Blog</a>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2025 Freestyle Video Pro. Sva prava zadržana.</p>
                <p>Profesionalno video uređivanje sa AI tehnologijom</p>
            </div>
        </div>
    </footer>

    <script>
        // Create animated background particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 8 + 's';
                particle.style.animationDuration = (Math.random() * 3 + 5) + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // Header scroll effect
        function handleScroll() {
            const header = document.getElementById('header');
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        }

        // Intersection Observer for fade-in animations
        function setupScrollAnimations() {
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            };

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                    }
                });
            }, observerOptions);

            document.querySelectorAll('.fade-in').forEach(el => {
                observer.observe(el);
            });
        }

        // Smooth scrolling for navigation links
        function setupSmoothScrolling() {
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    const target = document.querySelector(this.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth',
                            block: 'start'
                        });
                    }
                });
            });
        }

        // Initialize everything when DOM is loaded
        document.addEventListener('DOMContentLoaded', function() {
            createParticles();
            setupScrollAnimations();
            setupSmoothScrolling();
            
            // Initial fade-in for hero content
            setTimeout(() => {
                document.querySelector('.hero .fade-in').classList.add('visible');
            }, 500);
        });

        // Add scroll event listener
        window.addEventListener('scroll', handleScroll);

        // Add some interactive hover effects to feature cards
        document.addEventListener('DOMContentLoaded', function() {
            const featureCards = document.querySelectorAll('.feature-card');
            
            featureCards.forEach(card => {
                card.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-10px) rotateY(5deg)';
                });
                
                card.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0) rotateY(0deg)';
                });
            });
        });
    </script>
</body>
</html>
