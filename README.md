<DOCTYPE html>
<html lang="et">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PixelForge - Software Design Agency</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #6366f1;
            --primary-dark: #4f46e5;
            --secondary: #ec4899;
            --dark: #0f172a;
            --dark-light: #1e293b;
            --light: #f8fafc;
            --gray: #64748b;
            --gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--dark);
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav.scrolled {
            padding: 10px 0;
            background: rgba(255, 255, 255, 0.98);
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 40px;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        .mobile-menu {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
        }

        .mobile-menu span {
            width: 25px;
            height: 3px;
            background: var(--dark);
            transition: all 0.3s ease;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            position: relative;
            overflow: hidden;
            padding-top: 80px;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg"><defs><pattern id="grid" width="100" height="100" patternUnits="userSpaceOnUse"><path d="M 100 0 L 0 0 0 100" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="1"/></pattern></defs><rect width="100%" height="100%" fill="url(%23grid)"/></svg>');
            opacity: 0.3;
        }

        .hero-content {
            position: relative;
            z-index: 1;
            color: white;
            max-width: 800px;
        }

        .hero h1 {
            font-size: 64px;
            margin-bottom: 20px;
            animation: fadeInUp 1s ease;
        }

        .hero p {
            font-size: 24px;
            margin-bottom: 40px;
            opacity: 0.9;
            animation: fadeInUp 1s ease 0.2s backwards;
        }

        .cta-buttons {
            display: flex;
            gap: 20px;
            animation: fadeInUp 1s ease 0.4s backwards;
        }

        .btn {
            padding: 15px 40px;
            border: none;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background: white;
            color: var(--primary);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            border: 2px solid white;
        }

        .btn-secondary:hover {
            background: white;
            color: var(--primary);
        }

        /* Floating shapes */
        .shapes {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
        }

        .shape {
            position: absolute;
            opacity: 0.1;
            animation: float 20s infinite ease-in-out;
        }

        .shape:nth-child(1) {
            top: 20%;
            left: 10%;
            width: 80px;
            height: 80px;
            background: white;
            border-radius: 50%;
            animation-delay: 0s;
        }

        .shape:nth-child(2) {
            top: 60%;
            right: 15%;
            width: 120px;
            height: 120px;
            background: white;
            clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
            animation-delay: 2s;
        }

        .shape:nth-child(3) {
            bottom: 20%;
            left: 20%;
            width: 100px;
            height: 100px;
            background: white;
            clip-path: polygon(50% 0%, 100% 100%, 0% 100%);
            animation-delay: 4s;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            50% {
                transform: translateY(-30px) rotate(180deg);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Services Section */
        .services {
            padding: 100px 0;
            background: var(--light);
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }

        .section-title h2 {
            font-size: 48px;
            margin-bottom: 15px;
            color: var(--dark);
        }

        .section-title p {
            font-size: 18px;
            color: var(--gray);
            max-width: 600px;
            margin: 0 auto;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
            margin-top: 60px;
        }

        .service-card {
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 5px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.15);
        }

        .service-icon {
            width: 70px;
            height: 70px;
            background: var(--gradient);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            margin-bottom: 25px;
            color: white;
        }

        .service-card h3 {
            font-size: 24px;
            margin-bottom: 15px;
            color: var(--dark);
        }

        .service-card p {
            color: var(--gray);
            line-height: 1.8;
        }

        /* Portfolio Section */
        .portfolio {
            padding: 100px 0;
            background: white;
        }

        .portfolio-filters {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 50px;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 10px 30px;
            border: 2px solid var(--primary);
            background: transparent;
            color: var(--primary);
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
        }

        .filter-btn:hover,
        .filter-btn.active {
            background: var(--primary);
            color: white;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .portfolio-item {
            position: relative;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 30px rgba(0, 0, 0, 0.1);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .portfolio-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
        }

        .portfolio-image {
            width: 100%;
            height: 300px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
            color: white;
        }

        .portfolio-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(99, 102, 241, 0.95);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s ease;
            padding: 30px;
            text-align: center;
            color: white;
        }

        .portfolio-item:hover .portfolio-overlay {
            opacity: 1;
        }

        .portfolio-overlay h3 {
            font-size: 28px;
            margin-bottom: 10px;
        }

        .portfolio-overlay p {
            font-size: 16px;
            margin-bottom: 20px;
        }

        .portfolio-tags {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .tag {
            padding: 5px 15px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 20px;
            font-size: 12px;
        }

        /* Team Section */
        .team {
            padding: 100px 0;
            background: var(--light);
        }

        .team-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-top: 60px;
        }

        .team-member {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 5px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            text-align: center;
        }

        .team-member:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.15);
        }

        .team-image {
            width: 100%;
            height: 280px;
            background: var(--gradient);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 72px;
            color: white;
        }

        .team-info {
            padding: 30px;
        }

        .team-info h3 {
            font-size: 22px;
            margin-bottom: 5px;
            color: var(--dark);
        }

        .team-info p {
            color: var(--gray);
            margin-bottom: 15px;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .social-links a {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            background: var(--primary);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            background: var(--primary-dark);
            transform: translateY(-3px);
        }

        /* Testimonials */
        .testimonials {
            padding: 100px 0;
            background: white;
        }

        .testimonials-slider {
            max-width: 800px;
            margin: 60px auto 0;
            position: relative;
        }

        .testimonial {
            background: var(--light);
            padding: 50px;
            border-radius: 20px;
            text-align: center;
            display: none;
        }

        .testimonial.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        .testimonial-text {
            font-size: 20px;
            font-style: italic;
            color: var(--dark);
            margin-bottom: 30px;
            line-height: 1.8;
        }

        .testimonial-author {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
        }

        .author-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--gradient);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            font-weight: bold;
        }

        .author-info h4 {
            font-size: 18px;
            color: var(--dark);
            margin-bottom: 5px;
        }

        .author-info p {
            color: var(--gray);
            font-size: 14px;
        }

        .slider-dots {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 30px;
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: var(--gray);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .dot.active {
            background: var(--primary);
            width: 30px;
            border-radius: 10px;
        }

        /* Stats Section */
        .stats {
            padding: 80px 0;
            background: var(--gradient);
            color: white;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            text-align: center;
        }

        .stat-item h3 {
            font-size: 48px;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .stat-item p {
            font-size: 18px;
            opacity: 0.9;
        }

        /* Contact Section */
        .contact {
            padding: 100px 0;
            background: var(--light);
        }

        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            margin-top: 60px;
        }

        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        .contact-item {
            display: flex;
            gap: 20px;
            align-items: flex-start;
        }

        .contact-icon {
            width: 50px;
            height: 50px;
            background: var(--primary);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            flex-shrink: 0;
        }

        .contact-details h3 {
            font-size: 20px;
            margin-bottom: 5px;
            color: var(--dark);
        }

        .contact-details p {
            color: var(--gray);
        }

        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            margin-bottom: 8px;
            color: var(--dark);
            font-weight: 600;
        }

        .form-group input,
        .form-group textarea {
            padding: 15px;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
            font-family: inherit;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 150px;
        }

        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            padding: 60px 0 30px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }

        .footer-section h3 {
            font-size: 20px;
            margin-bottom: 20px;
        }

        .footer-section p {
            color: var(--gray);
            line-height: 1.8;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 12px;
        }

        .footer-links a {
            color: var(--gray);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: white;
        }

        .footer-bottom {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--gray);
        }

        /* Scroll to top button */
        .scroll-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            font-size: 24px;
            cursor: pointer;
            display: none;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            z-index: 999;
        }

        .scroll-top:hover {
            background: var(--primary-dark);
            transform: translateY(-5px);
        }

        .scroll-top.visible {
            display: flex;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu {
                display: flex;
            }

            .hero h1 {
                font-size: 36px;
            }

            .hero p {
                font-size: 18px;
            }

            .cta-buttons {
                flex-direction: column;
            }

            .section-title h2 {
                font-size: 32px;
            }

            .contact-content {
                grid-template-columns: 1fr;
            }

            .portfolio-grid,
            .services-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav id="navbar">
        <div class="nav-container">
            <div class="logo">PixelForge</div>
            <ul class="nav-links">
                <li><a href="#home">Avaleht</a></li>
                <li><a href="#services">Teenused</a></li>
                <li><a href="#portfolio">Portfoolio</a></li>
                <li><a href="#team">Meeskond</a></li>
                <li><a href="#contact">Kontakt</a></li>
            </ul>
            <div class="mobile-menu">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="shapes">
            <div class="shape"></div>
            <div class="shape"></div>
            <div class="shape"></div>
        </div>
        <div class="container">
            <div class="hero-content">
                <h1>Loome digitaalseid lahendusi, mis muudavad maailma</h1>
                <p>Oleme innovaatiline software design agentuur, mis aitab ettevõtetel muuta ideed tegelikkuseks läbi kauni disaini ja võimsa tehnoloogia.</p>
                <div class="cta-buttons">
                    <a href="#contact" class="btn btn-primary">Alusta projekti</a>
                    <a href="#portfolio" class="btn btn-secondary">Vaata tööd</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section class="services" id="services">
        <div class="container">
            <div class="section-title">
                <h2>Meie teenused</h2>
                <p>Pakume täielikku teenuste valikut digitaalsete lahenduste loomiseks</p>
            </div>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">🎨</div>
                    <h3>UI/UX Disain</h3>
                    <p>Loome kasutajasõbralikke ja visuaalselt ligitõmbavaid kasutajaliideseid, mis parandavad kasutajakogemust ja tõstavad konversioonimäärasid.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">💻</div>
                    <h3>Veebirakendused</h3>
                    <p>Arendame kaasaegseid ja kiireid veebirakendusi, kasutades uusimaid tehnoloogiaid nagu React, Vue ja Node.js.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">📱</div>
                    <h3>Mobiilirakendused</h3>
                    <p>Ehitame natiivset kasutajakogemust pakkuvaid mobiilirakendusi nii iOS kui ka Android platvormidele.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">🚀</div>
                    <h3>Brändi strateegia</h3>
                    <p>Aitame luua tugeva brändi identiteedi, mis eristub konkurentidest ja jääb klientidele meelde.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">⚡</div>
                    <h3>Digitaliseerimine</h3>
                    <p>Viime teie äriprotsessid digitaalsel ajastul uuele tasemele läbi automatiseerimise ja optimeerimise.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">🔧</div>
                    <h3>Tehnline tugi</h3>
                    <p>Pakume pidevat tehnilist tuge ja hooldust, et teie rakendused töötaksid alati sujuvalt.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Portfolio Section -->
    <section class="portfolio" id="portfolio">
        <div class="container">
            <div class="section-title">
                <h2>Meie tööd</h2>
                <p>Vaata mõningaid meie viimaste projektide näiteid</p>
            </div>
            <div class="portfolio-filters">
                <button class="filter-btn active" data-filter="all">Kõik</button>
                <button class="filter-btn" data-filter="web">Veeb</button>
                <button class="filter-btn" data-filter="mobile">Mobiil</button>
                <button class="filter-btn" data-filter="design">Disain</button>
            </div>
            <div class="portfolio-grid">
                <div class="portfolio-item" data-category="web">
                    <div class="portfolio-image">🛒</div>
                    <div class="portfolio-overlay">
                        <h3>E-kaubanduse platvorm</h3>
                        <p>Kaasaegne veebirakendus müügi optimeerimiseks</p>
                        <div class="portfolio-tags">
                            <span class="tag">React</span>
                            <span class="tag">Node.js</span>
                            <span class="tag">MongoDB</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="mobile">
                    <div class="portfolio-image">🏋️</div>
                    <div class="portfolio-overlay">
                        <h3>Fitness rakendus</h3>
                        <p>Mobiilirakendus treeningu jälgimiseks</p>
                        <div class="portfolio-tags">
                            <span class="tag">React Native</span>
                            <span class="tag">Firebase</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="design">
                    <div class="portfolio-image">🎭</div>
                    <div class="portfolio-overlay">
                        <h3>Brändi identiteet</h3>
                        <p>Täielik brändi disaini pakett</p>
                        <div class="portfolio-tags">
                            <span class="tag">Branding</span>
                            <span class="tag">UI/UX</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="web">
                    <div class="portfolio-image">📊</div>
                    <div class="portfolio-overlay">
                        <h3>Analüütika platvorm</h3>
                        <p>Andmete visualiseerimise tööriist</p>
                        <div class="portfolio-tags">
                            <span class="tag">Vue.js</span>
                            <span class="tag">D3.js</span>
                            <span class="tag">Python</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="mobile">
                    <div class="portfolio-image">🍕</div>
                    <div class="portfolio-overlay">
                        <h3>Toidu tellimise app</h3>
                        <p>Kiire ja mugav toidutellimise rakendus</p>
                        <div class="portfolio-tags">
                            <span class="tag">Flutter</span>
                            <span class="tag">Stripe</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="design">
                    <div class="portfolio-image">🏠</div>
                    <div class="portfolio-overlay">
                        <h3>Kinnisvara veebileht</h3>
                        <p>Kaasaegne kinnisvaraportaali disain</p>
                        <div class="portfolio-tags">
                            <span class="tag">UI Design</span>
                            <span class="tag">Figma</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Team Section -->
    <section class="team" id="team">
        <div class="container">
            <div class="section-title">
                <h2>Meie meeskond</h2>
                <p>Tutvuge professionaalidega, kes muudavad teie visiooni tegelikkuseks</p>
            </div>
            <div class="team-grid">
                <div class="team-member">
                    <div class="team-image">👨‍💼</div>
                    <div class="team-info">
                        <h3>Martin Kask</h3>
                        <p>Tegevjuht & Strateegia juht</p>
                        <div class="social-links">
                            <a href="#">in</a>
                            <a href="#">𝕏</a>
                            <a href="#">@</a>
                        </div>
                    </div>
                </div>
                <div class="team-member">
                    <div class="team-image">👩‍🎨</div>
                    <div class="team-info">
                        <h3>Laura Tamm</h3>
                        <p>Lead Designer</p>
                        <div class="social-links">
                            <a href="#">in</a>
                            <a href="#">𝕏</a>
                            <a href="#">@</a>
                        </div>
                    </div>
                </div>
                <div class="team-member">
                    <div class="team-image">👨‍💻</div>
                    <div class="team-info">
                        <h3>Kristjan Mägi</h3>
                        <p>Lead Developer</p>
                        <div class="social-links">
                            <a href="#">in</a>
                            <a href="#">𝕏</a>
                            <a href="#">@</a>
                        </div>
                    </div>
                </div>
                <div class="team-member">
                    <div class="team-image">👩‍💼</div>
                    <div class="team-info">
                        <h3>Kati Lepik</h3>
                        <p>Projektijuht</p>
                        <div class="social-links">
                            <a href="#">in</a>
                            <a href="#">𝕏</a>
                            <a href="#">@</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section class="testimonials">
        <div class="container">
            <div class="section-title">
                <h2>Mida meie kliendid ütlevad</h2>
                <p>Oleme uhked oma klientide rahulolu üle</p>
            </div>
            <div class="testimonials-slider">
                <div class="testimonial active">
                    <p class="testimonial-text">"PixelForge muutis meie äri täielikult. Nende loodud veebirakendus on intuitiivne, kiire ja on tõstnud meie müüki 300%. Soovitame soojalt!"</p>
                    <div class="testimonial-author">
                        <div class="author-avatar">AS</div>
                        <div class="author-info">
                            <h4>Andres Sepp</h4>
                            <p>Tegevjuht, TechStart OÜ</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial">
                    <p class="testimonial-text">"Meie mobiilirakendus valmis täpselt plaanitud ajaks ja eelarves. Meeskond oli professionaalne ning suhtlus oli kogu projekti vältel suurepärane."</p>
                    <div class="testimonial-author">
                        <div class="author-avatar">MV</div>
                        <div class="author-info">
                            <h4>Maria Viik</h4>
                            <p>Tooteomanik, HealthTech AS</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial">
                    <p class="testimonial-text">"PixelForge aitas meil luua tugeva brändi identiteedi, mis eristub turul selgelt. Nende loovus ja professionaalsus on tipptasemel!"</p>
                    <div class="testimonial-author">
                        <div class="author-avatar">JK</div>
                        <div class="author-info">
                            <h4>Jaan Kukk</h4>
                            <p>Turundusjuht, Fashion Hub</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="slider-dots">
                <span class="dot active" data-slide="0"></span>
                <span class="dot" data-slide="1"></span>
                <span class="dot" data-slide="2"></span>
            </div>
        </div>
    </section>

    <!-- Stats Section -->
    <section class="stats">
        <div class="container">
            <div class="stats-grid">
                <div class="stat-item">
                    <h3 class="counter" data-target="150">0</h3>
                    <p>Lõpetatud projekti</p>
                </div>
                <div class="stat-item">
                    <h3 class="counter" data-target="98">0</h3>
                    <p>Rahulolu määr %</p>
                </div>
                <div class="stat-item">
                    <h3 class="counter" data-target="50">0</h3>
                    <p>Rahvusvahelist klienti</p>
                </div>
                <div class="stat-item">
                    <h3 class="counter" data-target="15">0</h3>
                    <p>Aastat kogemust</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <div class="container">
            <div class="section-title">
                <h2>Võta ühendust</h2>
                <p>Alustame koos teie järgmist suurepärast projekti</p>
            </div>
            <div class="contact-content">
                <div class="contact-info">
                    <div class="contact-item">
                        <div class="contact-icon">📍</div>
                        <div class="contact-details">
                            <h3>Meie asukoht</h3>
                            <p>Telliskivi 60a<br>Tallinn 10412, Eesti</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">📧</div>
                        <div class="contact-details">
                            <h3>Email</h3>
                            <p>info@pixelforge.ee<br>projekti@pixelforge.ee</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">📞</div>
                        <div class="contact-details">
                            <h3>Telefon</h3>
                            <p>+372 5555 5555<br>E-R 9:00 - 18:00</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">⏰</div>
                        <div class="contact-details">
                            <h3>Lahtiolekuajad</h3>
                            <p>Esmaspäev - Reede: 9:00 - 18:00<br>Nädalavahetus: Suletud</p>
                        </div>
                    </div>
                </div>
                <form class="contact-form" id="contactForm">
                    <div class="form-group">
                        <label for="name">Nimi *</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email *</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="subject">Teema *</label>
                        <input type="text" id="subject" name="subject" required>
                    </div>
                    <div class="form-group">
                        <label for="message">Sõnum *</label>
                        <textarea id="message" name="message" required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary">Saada sõnum</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>PixelForge</h3>
                    <p>Oleme innovaatiline software design agentuur, mis aitab ettevõtetel muuta ideed tegelikkuseks läbi kauni disaini ja võimsa tehnoloogia.</p>
                </div>
                <div class="footer-section">
                    <h3>Kiirlingid</h3>
                    <ul class="footer-links">
                        <li><a href="#home">Avaleht</a></li>
                        <li><a href="#services">Teenused</a></li>
                        <li><a href="#portfolio">Portfoolio</a></li>
                        <li><a href="#team">Meeskond</a></li>
                        <li><a href="#contact">Kontakt</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h3>Teenused</h3>
                    <ul class="footer-links">
                        <li><a href="#">UI/UX Disain</a></li>
                        <li><a href="#">Veebirakendused</a></li>
                        <li><a href="#">Mobiilirakendused</a></li>
                        <li><a href="#">Brändi strateegia</a></li>
                        <li><a href="#">Digitaliseerimine</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h3>Jälgi meid</h3>
                    <ul class="footer-links">
                        <li><a href="#">LinkedIn</a></li>
                        <li><a href="#">Facebook</a></li>
                        <li><a href="#">Instagram</a></li>
                        <li><a href="#">Twitter</a></li>
                        <li><a href="#">Dribbble</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2025 PixelForge. Kõik õigused kaitstud.</p>
            </div>
        </div>
    </footer>

    <!-- Scroll to top button -->
    <button class="scroll-top" id="scrollTop">↑</button>

    <script>
        // Navbar scroll effect
        window.addEventListener('scroll', function() {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Smooth scrolling
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

        // Portfolio filter
        const filterButtons = document.querySelectorAll('.filter-btn');
        const portfolioItems = document.querySelectorAll('.portfolio-item');

        filterButtons.forEach(button => {
            button.addEventListener('click', function() {
                // Remove active class from all buttons
                filterButtons.forEach(btn => btn.classList.remove('active'));
                // Add active class to clicked button
                this.classList.add('active');

                const filterValue = this.getAttribute('data-filter');

                portfolioItems.forEach(item => {
                    if (filterValue === 'all' || item.getAttribute('data-category') === filterValue) {
                        item.style.display = 'block';
                        setTimeout(() => {
                            item.style.opacity = '1';
                            item.style.transform = 'scale(1)';
                        }, 10);
                    } else {
                        item.style.opacity = '0';
                        item.style.transform = 'scale(0.8)';
                        setTimeout(() => {
                            item.style.display = 'none';
                        }, 300);
                    }
                });
            });
        });

        // Testimonials slider
        let currentSlide = 0;
        const testimonials = document.querySelectorAll('.testimonial');
        const dots = document.querySelectorAll('.dot');

        function showSlide(index) {
            testimonials.forEach(testimonial => {
                testimonial.classList.remove('active');
            });
            dots.forEach(dot => {
                dot.classList.remove('active');
            });

            testimonials[index].classList.add('active');
            dots[index].classList.add('active');
        }

        dots.forEach((dot, index) => {
            dot.addEventListener('click', () => {
                currentSlide = index;
                showSlide(currentSlide);
            });
        });

        // Auto-play testimonials
        setInterval(() => {
            currentSlide = (currentSlide + 1) % testimonials.length;
            showSlide(currentSlide);
        }, 5000);

        // Counter animation
        const counters = document.querySelectorAll('.counter');
        const speed = 200;
        let counterAnimated = false;

        function animateCounters() {
            if (counterAnimated) return;

            counters.forEach(counter => {
                const updateCount = () => {
                    const target = +counter.getAttribute('data-target');
                    const count = +counter.innerText;
                    const increment = target / speed;

                    if (count < target) {
                        counter.innerText = Math.ceil(count + increment);
                        setTimeout(updateCount, 1);
                    } else {
                        counter.innerText = target;
                    }
                };
                updateCount();
            });
            counterAnimated = true;
        }

        // Trigger counter animation on scroll
        window.addEventListener('scroll', () => {
            const statsSection = document.querySelector('.stats');
            const sectionPos = statsSection.getBoundingClientRect().top;
            const screenPos = window.innerHeight / 1.3;

            if (sectionPos < screenPos) {
                animateCounters();
            }
        });

        // Scroll to top button
        const scrollTopBtn = document.getElementById('scrollTop');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 300) {
                scrollTopBtn.classList.add('visible');
            } else {
                scrollTopBtn.classList.remove('visible');
            }
        });

        scrollTopBtn.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        // Contact form submission
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Täname! Teie sõnum on saadetud. Võtame teiega peagi ühendust.');
            this.reset();
        });

        // Add animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe elements
        document.querySelectorAll('.service-card, .portfolio-item, .team-member').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>

