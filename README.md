<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Royal Bar - Premium Cocktail Experience</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #fff;
            background: #0d0d0d;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, rgba(13,13,13,0.98), rgba(26,26,26,0.98));
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            padding: 1rem 0;
            backdrop-filter: blur(15px);
            transition: all 0.3s ease;
            border-bottom: 2px solid #ffd700;
            box-shadow: 0 4px 20px rgba(255,215,0,0.2);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            color: #ffd700;
            text-shadow: 2px 2px 8px rgba(255,215,0,0.3);
            letter-spacing: 1px;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            position: relative;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .nav-links a:hover {
            color: #ffd700;
            transform: translateY(-2px);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background: linear-gradient(90deg, #ffd700, #ffec8b);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Mobile Menu */
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: #ffd700;
            font-size: 1.8rem;
            cursor: pointer;
            padding: 8px;
            border-radius: 5px;
            transition: all 0.3s ease;
        }

        .mobile-menu-btn:hover {
            background: rgba(255,215,0,0.1);
            transform: scale(1.1);
        }

        .mobile-nav {
            display: none;
            position: fixed;
            top: 76px;
            left: 0;
            width: 100%;
            background: linear-gradient(135deg, rgba(13,13,13,0.98), rgba(26,26,26,0.98));
            backdrop-filter: blur(20px);
            border-bottom: 2px solid #ffd700;
            z-index: 999;
            box-shadow: 0 8px 25px rgba(255,215,0,0.2);
        }

        .mobile-nav.active {
            display: block;
            animation: slideDown 0.4s ease;
        }

        .mobile-nav ul {
            list-style: none;
            padding: 25px;
        }

        .mobile-nav ul li {
            margin: 18px 0;
            text-align: center;
        }

        .mobile-nav ul li a {
            color: #fff;
            text-decoration: none;
            font-size: 1.2rem;
            font-weight: 600;
            padding: 15px;
            display: block;
            border-bottom: 1px solid rgba(255,215,0,0.2);
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
            border-radius: 8px;
        }

        .mobile-nav ul li a:hover {
            color: #ffd700;
            background: rgba(255,215,0,0.1);
            border-color: #ffd700;
            transform: scale(1.05);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(135deg, rgba(13,13,13,0.8), rgba(26,26,26,0.6)), 
                        radial-gradient(circle at 30% 40%, rgba(255,215,0,0.15), transparent 70%),
                        radial-gradient(circle at 80% 10%, rgba(255,215,0,0.1), transparent 50%),
                        radial-gradient(circle at 40% 80%, rgba(255,215,0,0.08), transparent 60%),
                        linear-gradient(45deg, #0d0d0d, #1a1a1a);
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: repeating-linear-gradient(
                45deg,
                transparent,
                transparent 2px,
                rgba(255,215,0,0.02) 2px,
                rgba(255,215,0,0.02) 4px
            );
        }

        .hero-content {
            color: #fff;
            max-width: 900px;
            animation: fadeInUp 1.2s ease;
            padding: 0 20px;
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: 4.5rem;
            margin-bottom: 1.5rem;
            background: linear-gradient(45deg, #ffd700, #fff, #ffd700, #ffec8b);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 4s ease-in-out infinite;
            text-shadow: 0 0 30px rgba(255,215,0,0.3);
            font-weight: 900;
            letter-spacing: 2px;
        }

        .hero p {
            font-size: 1.4rem;
            margin-bottom: 2.5rem;
            opacity: 0.95;
            color: #fff;
            font-weight: 400;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.7);
        }

        .cta-button {
            display: inline-block;
            padding: 18px 45px;
            background: linear-gradient(135deg, #ffd700, #ffb347);
            color: #0d0d0d;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            transition: all 0.4s ease;
            box-shadow: 0 10px 35px rgba(255,215,0,0.4);
            border: 2px solid #ffd700;
            position: relative;
            overflow: hidden;
        }

        .cta-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.6s;
        }

        .cta-button:hover::before {
            left: 100%;
        }

        .cta-button:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 20px 50px rgba(255,215,0,0.6);
            background: linear-gradient(135deg, #ffec8b, #ffd700);
        }

        /* Sections */
        .section {
            padding: 100px 0;
            position: relative;
        }

        .about {
            background: linear-gradient(135deg, #0d0d0d, #1a1a1a);
            color: #fff;
        }

        .menu {
            background: linear-gradient(135deg, #1a1a1a, #262626);
            color: #fff;
        }

        .contact {
            background: linear-gradient(135deg, #0d0d0d, #1a1a1a);
            color: #fff;
        }

        .section-title {
            text-align: center;
            font-size: 3.5rem;
            margin-bottom: 4rem;
            color: #ffd700;
            position: relative;
            font-weight: 800;
            text-shadow: 2px 2px 8px rgba(255,215,0,0.2);
        }

        .section-title::after {
            content: '';
            position: absolute;
            width: 120px;
            height: 4px;
            background: linear-gradient(90deg, #ffd700, #ffec8b, #ffd700);
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        /* Menu Categories */
        .menu-categories {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2.5rem;
            margin-bottom: 4rem;
        }

        .category-card {
            background: linear-gradient(135deg, rgba(255,215,0,0.15), rgba(255,215,0,0.08));
            padding: 2.5rem;
            border-radius: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.4s ease;
            border: 2px solid rgba(255,215,0,0.3);
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(10px);
        }

        .category-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,215,0,0.2), transparent);
            transition: left 0.6s;
        }

        .category-card:hover::before {
            left: 100%;
        }

        .category-card:hover {
            transform: translateY(-15px) scale(1.03);
            border-color: #ffd700;
            box-shadow: 0 20px 50px rgba(255,215,0,0.4);
            background: linear-gradient(135deg, rgba(255,215,0,0.25), rgba(255,215,0,0.15));
        }

        .category-icon {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            filter: drop-shadow(0 0 15px rgba(255,215,0,0.6));
        }

        .category-card h3 {
            color: #ffd700;
            font-size: 1.6rem;
            margin-bottom: 0.8rem;
            font-weight: 700;
        }

        .category-card p {
            color: rgba(255,255,255,0.9);
            font-size: 1rem;
            font-weight: 500;
        }

        /* Menu Items Sections */
        .menu-items-section {
            display: none;
            margin-top: 3rem;
            padding: 3rem;
            background: rgba(13,13,13,0.4);
            border-radius: 25px;
            border: 2px solid rgba(255,215,0,0.3);
            animation: slideIn 0.6s ease;
            backdrop-filter: blur(10px);
        }

        .menu-items-section.active {
            display: block;
        }

        .category-title {
            color: #ffd700;
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
            font-weight: 700;
        }

        .category-title::after {
            content: '';
            position: absolute;
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, #ffd700, #ffec8b);
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        /* Updated Menu Grid */
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2.5rem;
            margin-top: 2rem;
        }

        .menu-item {
            background: rgba(13,13,13,0.6);
            padding: 2.5rem;
            border-radius: 18px;
            border: 2px solid rgba(255,215,0,0.3);
            transition: all 0.4s ease;
            backdrop-filter: blur(8px);
            position: relative;
            overflow: hidden;
        }

        .menu-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent, rgba(255,215,0,0.05), transparent);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .menu-item:hover::before {
            opacity: 1;
        }

        .menu-item:hover {
            transform: translateY(-12px) scale(1.02);
            box-shadow: 0 25px 50px rgba(255,215,0,0.3);
            border-color: #ffd700;
            background: rgba(255,215,0,0.1);
        }

        .menu-item h3 {
            color: #ffd700;
            margin-bottom: 1.2rem;
            font-size: 1.6rem;
            font-weight: 700;
        }

        .menu-item h4 {
            color: #ffd700;
            margin-bottom: 1rem;
            font-size: 1.4rem;
            font-weight: 600;
        }

        .menu-item p {
            color: rgba(255,255,255,0.9);
            margin-bottom: 1.5rem;
            line-height: 1.6;
            font-weight: 400;
        }

        .menu-item .price {
            color: #ffd700;
            font-weight: bold;
            font-size: 1.3rem;
            float: right;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.5);
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text {
            font-size: 1.2rem;
            line-height: 1.9;
            color: #fff;
            font-weight: 400;
        }

        .about-features {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        .feature {
            padding: 2rem;
            background: rgba(255,215,0,0.15);
            border-radius: 15px;
            text-align: center;
            transition: all 0.4s ease;
            border: 2px solid rgba(255,215,0,0.3);
            backdrop-filter: blur(5px);
        }

        .feature:hover {
            background: rgba(255,215,0,0.25);
            transform: scale(1.08) translateY(-5px);
            border-color: #ffd700;
            box-shadow: 0 15px 30px rgba(255,215,0,0.3);
        }

        .feature-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            filter: drop-shadow(0 0 10px rgba(255,215,0,0.5));
        }

        .feature h4 {
            color: #ffd700;
            margin-bottom: 0.8rem;
            font-weight: 600;
        }

        .feature p {
            color: rgba(255,255,255,0.9);
            font-size: 0.95rem;
            font-weight: 400;
        }

        /* Contact Section */
        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
        }

        .contact-info {
            background: rgba(13,13,13,0.4);
            padding: 3rem;
            border-radius: 20px;
            border: 2px solid rgba(255,215,0,0.3);
            backdrop-filter: blur(10px);
        }

        .contact-item {
            margin-bottom: 2rem;
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .contact-icon {
            color: #ffd700;
            font-size: 1.8rem;
            filter: drop-shadow(0 0 5px rgba(255,215,0,0.5));
        }

        .contact-item div {
            color: #fff;
            font-weight: 400;
        }

        .contact-item strong {
            color: #ffd700;
            font-weight: 600;
        }

        .hours {
            background: rgba(13,13,13,0.4);
            padding: 3rem;
            border-radius: 20px;
            border: 2px solid rgba(255,215,0,0.3);
            backdrop-filter: blur(10px);
        }

        .hours h3 {
            color: #ffd700;
            margin-bottom: 1.5rem;
            text-align: center;
            font-weight: 700;
        }

        .hours-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.8rem;
            padding: 0.8rem 0;
            border-bottom: 1px solid rgba(255,215,0,0.2);
            color: #fff;
            font-weight: 500;
        }

        /* Footer */
        footer {
            background: #0d0d0d;
            padding: 3rem 0;
            text-align: center;
            border-top: 3px solid #ffd700;
            color: #fff;
            box-shadow: 0 -5px 20px rgba(255,215,0,0.1);
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes gradientShift {
            0%, 100% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Mobile Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu-btn {
                display: block;
            }
            
            .hero h1 {
                font-size: 3rem;
            }

            .hero p {
                font-size: 1.2rem;
                margin-bottom: 2rem;
            }

            .cta-button {
                padding: 15px 35px;
                font-size: 0.9rem;
            }
            
            .about-content,
            .contact-content {
                grid-template-columns: 1fr;
                gap: 3rem;
            }
            
            .about-features {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }
            
            .section-title {
                font-size: 2.5rem;
            }

            .menu-categories {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .category-card {
                padding: 2rem;
            }

            .menu-grid {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .menu-item {
                padding: 2rem;
            }

            .menu-item .price {
                float: none;
                display: block;
                margin-top: 1rem;
                text-align: right;
            }

            .section {
                padding: 80px 0;
            }

            .container {
                padding: 0 20px;
            }

            .hero-content {
                padding: 0 20px;
            }

            .logo {
                font-size: 1.8rem;
            }

            .category-title {
                font-size: 2rem;
            }

            .menu-items-section {
                padding: 2rem;
            }

            .contact-info,
            .hours {
                padding: 2rem;
            }
        }

        @media (max-width: 480px) {
            .hero h1 {
                font-size: 2.5rem;
                margin-bottom: 1rem;
            }

            .hero p {
                font-size: 1.1rem;
                margin-bottom: 1.5rem;
            }

            .section-title {
                font-size: 2rem;
                margin-bottom: 3rem;
            }

            .category-card {
                padding: 1.5rem;
            }

            .category-icon {
                font-size: 3rem;
            }

            .menu-item {
                padding: 1.5rem;
            }

            .contact-info,
            .hours {
                padding: 1.5rem;
            }

            .section {
                padding: 60px 0;
            }

            .container {
                padding: 0 15px;
            }

            .menu-items-section {
                padding: 1.5rem;
            }
        }

        /* Ensure consistent colors across all devices */
        @media (-webkit-min-device-pixel-ratio: 1) {
            body {
                -webkit-text-size-adjust: 100%;
            }
        }

        /* Force hardware acceleration on mobile */
        @media only screen and (max-width: 768px) {
            .category-card,
            .menu-item,
            .feature,
            .cta-button {
                -webkit-transform: translate3d(0,0,0);
                transform: translate3d(0,0,0);
                -webkit-backface-visibility: hidden;
                backface-visibility: hidden;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav class="container">
            <div class="logo">The Royal Bar</div>
            <ul class="nav-links">
                <li><a href="#home">Ana Sayfa</a></li>
                <li><a href="#about">Hakkımızda</a></li>
                <li><a href="#menu">Menü</a></li>
                <li><a href="#contact">İletişim</a></li>
            </ul>
            <button class="mobile-menu-btn" onclick="toggleMobileMenu()">☰</button>
        </nav>
        <div class="mobile-nav" id="mobileNav">
            <ul>
                <li><a href="#home" onclick="closeMobileMenu()">Ana Sayfa</a></li>
                <li><a href="#about" onclick="closeMobileMenu()">Hakkımızda</a></li>
                <li><a href="#menu" onclick="closeMobileMenu()">Menü</a></li>
                <li><a href="#contact" onclick="closeMobileMenu()">İletişim</a></li>
            </ul>
        </div>
    </header>

    <section id="home" class="hero">
        <div class="hero-content">
            <h1>The Royal Bar</h1>
            <p>Premium kokteyller ve unutulmaz deneyimler için en seçkin adres</p>
            <a href="#menu" class="cta-button">Menümüzü İnceleyin</a>
        </div>
    </section>

    <section id="about" class="section about">
        <div class="container">
            <h2 class="section-title">Hakkımızda</h2>
            <div class="about-content">
                <div class="about-text">
                    <p>The Royal Bar, şehrin kalbinde yer alan premium bir kokteyl barıdır. Uzman barmenlerimiz, en kaliteli malzemelerle hazırladığı özel kokteyller ile misafirlerimize unutulmaz bir deneyim sunmaktadır.</p>
                    <p>Sofistike atmosferimiz ve mükemmel müzik seçimimiz ile hem iş görüşmeleriniz hem de özel kutlamalarınız için ideal bir ortam yaratmaktayız.</p>
                </div>
                <div class="about-features">
                    <div class="feature">
                        <div class="feature-icon">🍸</div>
                        <h4>Premium Kokteyller</h4>
                        <p>El yapımı özel kokteyller</p>
                    </div>
                    <div class="feature">
                        <div class="feature-icon">🎵</div>
                        <h4>Canlı Müzik</h4>
                        <p>Hafta sonları canlı performanslar</p>
                    </div>
                    <div class="feature">
                        <div class="feature-icon">🎉</div>
                        <h4>Özel Etkinlikler</h4>
                        <p>Kurumsal ve özel organizasyonlar</p>
                    </div>
                    <div class="feature">
                        <div class="feature-icon">⭐</div>
                        <h4>VIP Hizmet</h4>
                        <p>Özel masa rezervasyonları</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="menu" class="section menu">
        <div class="container">
            <h2 class="section-title">Menümüz</h2>
            
            <!-- Menu Categories -->
            <div class="menu-categories">
                <div class="category-card" onclick="toggleCategory('cold-coffee')">
                    <div class="category-icon">🧊</div>
                    <h3>Soğuk Kahveler</h3>
                    <p>Serinletici kahve çeşitleri</p>
                </div>
                <div class="category-card" onclick="toggleCategory('hot-coffee')">
                    <div class="category-icon">☕</div>
                    <h3>Sıcak Kahveler</h3>
                    <p>Geleneksel sıcak içecekler</p>
                </div>
                <div class="category-card" onclick="toggleCategory('cocktails')">
                    <div class="category-icon">🍸</div>
                    <h3>Kokteyller</h3>
                    <p>Premium kokteyl çeşitleri</p>
                </div>
                <div class="category-card" onclick="toggleCategory('soft-drinks')">
                    <div class="category-icon">🥤</div>
                    <h3>Soft İçecekler</h3>
                    <p>Alkolsüz seçenekler</p>
                </div>
                <div class="category-card" onclick="toggleCategory('beers')">
                    <div class="category-icon">🍺</div>
                    <h3>Biralar</h3>
                    <p>Yerli ve ithal bira çeşitleri</p>
                </div>
                <div class="category-card" onclick="toggleCategory('snacks')">
                    <div class="category-icon">🥜</div>
                    <h3>Çerezler</h3>
                    <p>Lezzetli atıştırmalıklar</p>
                </div>
            </div>

            <!-- Menu Items (Initially Hidden) -->
            <div id="cold-coffee" class="menu-items-section">
                <h3 class="category-title">Soğuk Kahveler</h3>
                <div class="menu-grid">
                    <div class="menu-item">
                        <h4>Iced Latte</h4>
                        <p>Soğuk espresso, buzlu süt, vanilya şurubu</p>
                        <span class="price">₺45</span>
                    </div>
                    <div class="menu-item">
                        <h4>Cold Brew</h4>
                        <p>12 saat soğuk demleme, kremsi doku</p>
                        <span class="price">₺40</span>
                    </div>
                    <div class="menu-item">
                        <h4>Frappuccino</h4>
                        <p>Buzlu kahve, krema, çikolata sosu</p>
                        <span class="price">₺50</span>
                    </div>
                    <div class="menu-item">
                        <h4>Iced Americano</h4>
                        <p>Çifte espresso, buzlu su, limon dilimi</p>
                        <span class="price">₺35</span>
                    </div>
                    <div class="menu-item">
                        <h4>Iced Caramel Macchiato</h4>
                        <p>Vanilya şurubu, buzlu süt, espresso, karamel sos</p>
                        <span class="price">₺55</span>
                    </div>
                    <div class="menu-item">
                        <h4>Nitro Cold Brew</h4>
                        <p>Azot gazı ile servis edilen özel soğuk kahve</p>
                        <span class="price">₺60</span>
                    </div>
                </div>
            </div>

            <div id="hot-coffee" class="menu-items-section">
                <h3 class="category-title">Sıcak Kahveler</h3>
                <div class="menu-grid">
                    <div class="menu-item">
                        <h4>Espresso</h4>
                        <p>Klasik İtalyan espressosu</p>
                        <span class="price">₺25</span>
                    </div>
                    <div class="menu-item">
                        <h4>Cappuccino</h4>
                        <p>Espresso, sıcak süt, süt köpüğü</p>
                        <span class="price">₺40</span>
                    </div>
                    <div class="menu-item">
                        <h4>Latte</h4>
                        <p>Espresso, buharlanmış süt, latte art</p>
                        <span class="price">₺42</span>
                    </div>
                    <div class="menu-item">
                        <h4>Mocha</h4>
                        <p>Espresso, çikolata, sıcak süt, krema</p>
                        <span class="price">₺45</span>
                    </div>
                    <div class="menu-item">
                        <h4>Turkish Coffee</h4>
                        <p>Geleneksel Türk kahvesi, lokum ile servis</p>
                        <span class="price">₺30</span>
                    </div>
                    <div class="menu-item">
                        <h4>Flat White</h4>
                        <p>Çifte espresso, mikroköpük süt</p>
                        <span class="price">₺48</span>
                    </div>
                </div>
            </div>

            <div id="cocktails" class="menu-items-section">
                <h3 class="category-title">Kokteyller</h3>
                <div class="menu-grid">
                    <div class="menu-item">
                        <h4>Royal Mojito</h4>
                        <p>Premium rom, taze nane, limon, soda</p>
                        <span class="price">₺85</span>
                    </div>
                    <div class="menu-item">
                        <h4>Cosmopolitan</h4>
                        <p>Vodka, cranberry, limon suyu, triple sec</p>
                        <span class="price">₺90</span>
                    </div>
                    <div class="menu-item">
                        <h4>Old Fashioned</h4>
                        <p>Bourbon whiskey, şeker, angostura bitter</p>
                        <span class="price">₺95</span>
                    </div>
                    <div class="menu-item">
                        <h4>Margarita</h4>
                        <p>Tequila, lime juice, triple sec, tuz kenarı</p>
                        <span class="price">₺80</span>
                    </div>
                    <div class="menu-item">
                        <h4>Whiskey Sour</h4>
                        <p>Bourbon, limon suyu, şurup, egg white</p>
                        <span class="price">₺85</span>
                    </div>
                    <div class="menu-item">
                        <h4>Negroni</h4>
                        <p>Gin, campari, sweet vermouth, portakal</p>
                        <span class="price">₺90</span>
                    </div>
                </div>
            </div>

            <div id="soft-drinks" class="menu-items-section">
                <h3 class="category-title">Soft İçecekler</h3>
                <div class="menu-grid">
                    <div class="menu-item">
                        <h4>Fresh Orange Juice</h4>
                        <p>Taze sıkılmış portakal suyu</p>
                        <span class="price">₺25</span>
                    </div>
                    <div class="menu-item">
                        <h4>Limonata</h4>
                        <p>Taze limon, nane, soda</p>
                        <span class="price">₺20</span>
                    </div>
                    <div class="menu-item">
                        <h4>Virgin Mojito</h4>
                        <p>Nane, limon, şeker, soda</p>
                        <span class="price">₺30</span>
                    </div>
                    <div class="menu-item">
                        <h4>Smoothie</h4>
                        <p>Mevsim meyveli smoothie çeşitleri</p>
                        <span class="price">₺35</span>
                    </div>
                    <div class="menu-item">
                        <h4>İced Tea</h4>
                        <p>Soğuk çay, limon, nane</p>
                        <span class="price">₺18</span>
                    </div>
                    <div class="menu-item">
                        <h4>Gazlı İçecekler</h4>
                        <p>Coca Cola, Fanta, Sprite, Soda</p>
                        <span class="price">₺15</span>
                    </div>
                </div>
            </div>

            <div id="beers" class="menu-items-section">
                <h3 class="category-title">Biralar</h3>
                <div class="menu-grid">
                    <div class="menu-item">
                        <h4>Efes Pilsen</h4>
                        <p>Klasik Türk birası (500ml)</p>
                        <span class="price">₺35</span>
                    </div>
                    <div class="menu-item">
                        <h4>Bomonti Filtresiz</h4>
                        <p>Özel üretim filtresiz bira (500ml)</p>
                        <span class="price">₺40</span>
                    </div>
                    <div class="menu-item">
                        <h4>Heineken</h4>
                        <p>Hollanda birası (500ml)</p>
                        <span class="price">₺45</span>
                    </div>
                    <div class="menu-item">
                        <h4>Corona</h4>
                        <p>Meksika birası, limon ile (355ml)</p>
                        <span class="price">₺50</span>
                    </div>
                    <div class="menu-item">
                        <h4>Guinness</h4>
                        <p>İrlanda stout birası (500ml)</p>
                        <span class="price">₺55</span>
                    </div>
                    <div class="menu-item">
                        <h4>Craft Beer Selection</h4>
                        <p>Günlük değişen craft bira seçkisi</p>
                        <span class="price">₺60</span>
                    </div>
                </div>
            </div>

            <div id="snacks" class="menu-items-section">
                <h3 class="category-title">Çerezler</h3>
                <div class="menu-grid">
                    <div class="menu-item">
                        <h4>Mixed Nuts</h4>
                        <p>Karışık kuruyemiş tabağı</p>
                        <span class="price">₺30</span>
                    </div>
                    <div class="menu-item">
                        <h4>Cheese Platter</h4>
                        <p>Seçme peynir tabağı, crackers ile</p>
                        <span class="price">₺65</span>
                    </div>
                    <div class="menu-item">
                        <h4>Olive Selection</h4>
                        <p>Özel marinasyon zeytin çeşitleri</p>
                        <span class="price">₺25</span>
                    </div>
                    <div class="menu-item">
                        <h4>Bruschetta</h4>
                        <p>Domates, fesleğen, mozzarella (4 adet)</p>
                        <span class="price">₺45</span>
                    </div>
                    <div class="menu-item">
                        <h4>Chicken Wings</h4>
                        <p>BBQ soslu tavuk kanatları (8 adet)</p>
                        <span class="price">₺55</span>
                    </div>
                    <div class="menu-item">
                        <h4>Nachos</h4>
                        <p>Cheddar peynirli nachos, salsa sos</p>
                        <span class="price">₺40</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="contact" class="section contact">
        <div class="container">
            <h2 class="section-title">İletişim</h2>
            <div class="contact-content">
                <div class="contact-info">
                    <div class="contact-item">
                        <span class="contact-icon">📍</span>
                        <div>
                            <strong>Adres:</strong><br>
                            Kılıçali Paşa Mahallesi, Royal Street No:123<br>
                            Beyoğlu/İstanbul
                        </div>
                    </div>
                    <div class="contact-item">
                        <span class="contact-icon">📞</span>
                        <div>
                            <strong>Telefon:</strong><br>
                            +90 212 555 0123
                        </div>
                    </div>
                    <div class="contact-item">
                        <span class="contact-icon">✉️</span>
                        <div>
                            <strong>Email:</strong><br>
                            info@theroyalbar.com
                        </div>
                    </div>
                    <div class="contact-item">
                        <span class="contact-icon">🌐</span>
                        <div>
                            <strong>Instagram:</strong><br>
                            @theroyalbar_istanbul
                        </div>
                    </div>
                </div>
                
                <div class="hours">
                    <h3>Çalışma Saatleri</h3>
                    <div class="hours-item">
                        <span>Pazartesi - Perşembe</span>
                        <span>17:00 - 02:00</span>
                    </div>
                    <div class="hours-item">
                        <span>Cuma - Cumartesi</span>
                        <span>17:00 - 03:00</span>
                    </div>
                    <div class="hours-item">
                        <span>Pazar</span>
                        <span>18:00 - 01:00</span>
                    </div>
                    <div class="hours-item">
                        <span>Happy Hour</span>
                        <span>17:00 - 19:00</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <div class="container">
            <p>&copy; 2024 The Royal Bar. Tüm hakları saklıdır. | Premium kokteyl deneyimi için en seçkin adres.</p>
        </div>
    </footer>

    <script>
        // Mobile Menu Toggle
        function toggleMobileMenu() {
            const mobileNav = document.getElementById('mobileNav');
            mobileNav.classList.toggle('active');
        }

        function closeMobileMenu() {
            const mobileNav = document.getElementById('mobileNav');
            mobileNav.classList.remove('active');
        }

        // Menu Category Toggle
        function toggleCategory(categoryId) {
            // Hide all menu sections first
            const allSections = document.querySelectorAll('.menu-items-section');
            allSections.forEach(section => {
                section.classList.remove('active');
            });

            // Show the selected category
            const selectedSection = document.getElementById(categoryId);
            if (selectedSection) {
                selectedSection.classList.add('active');
                
                // Smooth scroll to the menu items
                setTimeout(() => {
                    selectedSection.scrollIntoView({ 
                        behavior: 'smooth', 
                        block: 'start',
                        inline: 'nearest'
                    });
                }, 100);
            }
        }

        // Smooth scrolling for navigation links
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

        // Header background change on scroll
        window.addEventListener('scroll', function() {
            const header = document.querySelector('header');
            if (window.scrollY > 100) {
                header.style.background = 'linear-gradient(135deg, rgba(13,13,13,0.95), rgba(26,26,26,0.95))';
                header.style.backdropFilter = 'blur(20px)';
            } else {
                header.style.background = 'linear-gradient(135deg, rgba(13,13,13,0.98), rgba(26,26,26,0.98))';
                header.style.backdropFilter = 'blur(15px)';
            }
        });

        // Close mobile menu when clicking outside
        document.addEventListener('click', function(event) {
            const mobileNav = document.getElementById('mobileNav');
            const mobileMenuBtn = document.querySelector('.mobile-menu-btn');
            
            if (!mobileNav.contains(event.target) && !mobileMenuBtn.contains(event.target)) {
                mobileNav.classList.remove('active');
            }
        });

        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe elements for animation
        document.addEventListener('DOMContentLoaded', function() {
            const animatedElements = document.querySelectorAll('.menu-item, .feature, .category-card');
            animatedElements.forEach(el => {
                el.style.opacity = '0';
                el.style.transform = 'translateY(30px)';
                el.style.transition = 'all 0.6s ease';
                observer.observe(el);
            });
        });

        // Add some interactive effects
        document.querySelectorAll('.category-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-15px) scale(1.03)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });

        // Prevent menu from closing when clicking inside menu items
        document.querySelectorAll('.menu-items-section').forEach(section => {
            section.addEventListener('click', function(e) {
                e.stopPropagation();
            });
        });
    </script>
</body>
</html>
