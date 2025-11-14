<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CyberClean Solutions - Pencucian Uang Digital</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #00d4ff;
            --secondary: #ff00ff;
            --accent: #00ff88;
            --dark: #0a0a0a;
            --darker: #050505;
            --light: #f0f0f0;
            --gray: #2a2a2a;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            background-color: var(--darker);
            color: var(--light);
            overflow-x: hidden;
            line-height: 1.6;
            position: relative;
        }

        /* Money Rain Animation */
        .money-rain {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            overflow: hidden;
        }

        .money {
            position: absolute;
            width: 50px;
            height: 25px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 50"><rect width="100" height="50" fill="%2300a859" rx="5"/><text x="50" y="30" font-family="Arial" font-size="20" fill="white" text-anchor="middle">$</text></svg>');
            background-size: contain;
            background-repeat: no-repeat;
            opacity: 0.7;
            animation: fall linear infinite;
        }

        @keyframes fall {
            0% {
                transform: translateY(-100px) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(calc(100vh + 100px)) rotate(360deg);
                opacity: 0;
            }
        }

        h1, h2, h3, h4 {
            font-family: 'Orbitron', monospace;
            font-weight: 700;
            margin-bottom: 20px;
            text-transform: uppercase;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, rgba(10,10,10,0.9) 0%, rgba(5,5,5,0.95) 100%);
            padding: 20px 0;
            position: fixed;
            width: 100%;
            z-index: 1000;
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(0, 212, 255, 0.3);
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
        }

        .logo-text {
            font-size: 24px;
            font-weight: 900;
            background: linear-gradient(45deg, var(--primary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 1px;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        nav a {
            color: var(--light);
            text-decoration: none;
            font-weight: 600;
            font-size: 18px;
            transition: all 0.3s ease;
            position: relative;
        }

        nav a:hover {
            color: var(--primary);
        }

        nav a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background: var(--primary);
            bottom: -5px;
            left: 0;
            transition: width 0.3s ease;
        }

        nav a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, rgba(10,10,10,0.8) 0%, rgba(5,5,5,0.9) 100%);
        }

        .hero-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://images.unsplash.com/photo-1633412802994-5c058f151b66?ixlib=rb-4.0.3&auto=format&fit=crop&w=1950&q=80') no-repeat center center/cover;
            filter: brightness(0.3) saturate(1.2);
            z-index: -1;
        }

        .hero-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
            position: relative;
            z-index: 1;
        }

        .hero-text h1 {
            font-size: 4rem;
            line-height: 1.1;
            margin-bottom: 30px;
            background: linear-gradient(45deg, var(--primary), var(--secondary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 0 0 10px rgba(0, 212, 255, 0.5); }
            to { text-shadow: 0 0 20px rgba(0, 212, 255, 0.8), 0 0 30px rgba(255, 0, 255, 0.6); }
        }

        .hero-text p {
            font-size: 1.4rem;
            margin-bottom: 30px;
            color: #ccc;
        }

        .btn {
            display: inline-block;
            padding: 15px 35px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 700;
            font-size: 18px;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 212, 255, 0.4);
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 212, 255, 0.6);
        }

        .hero-image {
            position: relative;
        }

        .hero-image img {
            width: 100%;
            border-radius: 10px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
            border: 2px solid rgba(0, 212, 255, 0.3);
        }

        /* Services Section */
        .services {
            padding: 100px 0;
            background: var(--dark);
            position: relative;
            z-index: 1;
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }

        .section-title h2 {
            font-size: 3rem;
            background: linear-gradient(45deg, var(--primary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            position: relative;
            display: inline-block;
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            width: 100px;
            height: 4px;
            background: var(--primary);
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .service-card {
            background: rgba(42, 42, 42, 0.3);
            border: 1px solid rgba(0, 212, 255, 0.2);
            border-radius: 15px;
            padding: 40px 30px;
            text-align: center;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .service-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
            box-shadow: 0 15px 30px rgba(0, 212, 255, 0.2);
        }

        .service-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 25px;
            font-size: 36px;
            color: white;
        }

        .service-card h3 {
            font-size: 1.8rem;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .service-card p {
            color: #ccc;
            font-size: 1.1rem;
        }

        /* About Section */
        .about {
            padding: 100px 0;
            background: linear-gradient(135deg, rgba(10,10,10,0.9) 0%, rgba(5,5,5,0.95) 100%);
            position: relative;
            z-index: 1;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }

        .about-image {
            position: relative;
        }

        .about-image img {
            width: 100%;
            border-radius: 10px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
            border: 2px solid rgba(0, 212, 255, 0.3);
        }

        .about-text h2 {
            font-size: 2.8rem;
            margin-bottom: 30px;
            background: linear-gradient(45deg, var(--secondary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .about-text p {
            font-size: 1.2rem;
            margin-bottom: 25px;
            color: #ccc;
        }

        .features {
            margin-top: 30px;
        }

        .feature {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .feature i {
            color: var(--accent);
            font-size: 24px;
            margin-right: 15px;
        }

        .feature span {
            font-size: 1.1rem;
        }

        /* Contact Section */
        .contact {
            padding: 100px 0;
            background: var(--dark);
            position: relative;
            z-index: 1;
        }

        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
        }

        .contact-form {
            background: rgba(42, 42, 42, 0.3);
            padding: 40px;
            border-radius: 15px;
            border: 1px solid rgba(0, 212, 255, 0.2);
            backdrop-filter: blur(10px);
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: var(--primary);
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 15px;
            background: rgba(10, 10, 10, 0.7);
            border: 1px solid rgba(0, 212, 255, 0.3);
            border-radius: 8px;
            color: white;
            font-size: 16px;
            font-family: 'Rajdhani', sans-serif;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 10px rgba(0, 212, 255, 0.3);
        }

        .contact-info {
            padding: 40px;
        }

        .contact-info h3 {
            font-size: 2rem;
            margin-bottom: 30px;
            color: var(--accent);
        }

        .contact-item {
            display: flex;
            align-items: flex-start;
            margin-bottom: 30px;
        }

        .contact-item i {
            color: var(--primary);
            font-size: 24px;
            margin-right: 20px;
            margin-top: 5px;
        }

        .contact-item div h4 {
            font-size: 1.3rem;
            margin-bottom: 5px;
            color: var(--light);
        }

        .contact-item div p {
            color: #ccc;
            font-size: 1.1rem;
        }

        /* Footer */
        footer {
            background: var(--darker);
            padding: 50px 0 30px;
            text-align: center;
            border-top: 1px solid rgba(0, 212, 255, 0.2);
            position: relative;
            z-index: 1;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .social-links {
            display: flex;
            gap: 20px;
        }

        .social-links a {
            color: var(--light);
            font-size: 24px;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            color: var(--primary);
            transform: translateY(-3px);
        }

        .copyright {
            color: #888;
            font-size: 1rem;
        }

        /* Responsive */
        @media (max-width: 992px) {
            .hero-content,
            .about-content,
            .contact-content {
                grid-template-columns: 1fr;
            }
            
            .hero-text h1 {
                font-size: 3rem;
            }
            
            .section-title h2 {
                font-size: 2.5rem;
            }
        }

        @media (max-width: 768px) {
            nav ul {
                display: none;
            }
            
            .hero-text h1 {
                font-size: 2.5rem;
            }
            
            .footer-content {
                flex-direction: column;
                gap: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Money Rain Background -->
    <div class="money-rain" id="moneyRain"></div>

    <!-- Header -->
    <header>
        <div class="container header-container">
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-shield-alt"></i>
                </div>
                <div class="logo-text">CyberClean</div>
            </div>
            <nav>
                <ul>
                    <li><a href="#home">Beranda</a></li>
                    <li><a href="#services">Layanan</a></li>
                    <li><a href="#about">Tentang</a></li>
                    <li><a href="#contact">Kontak</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-bg"></div>
        <div class="container">
            <div class="hero-content">
                <div class="hero-text">
                    <h1>Pencucian Uang Digital Terpercaya</h1>
                    <p>Lindungi aset digital Anda dengan solusi keamanan tingkat enterprise</p>
                    <a href="#contact" class="btn">Mulai Sekarang</a>
                </div>
                <div class="hero-image">
                    <img src="https://images.unsplash.com/photo-1614064641938-3bbee52942c7?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80" alt="Digital Security">
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section class="services" id="services">
        <div class="container">
            <div class="section-title">
                <h2>Layanan Kami</h2>
            </div>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-lock"></i>
                    </div>
                    <h3>Enkripsi Tingkat Militer</h3>
                    <p>Perlindungan data dengan enkripsi AES-256 untuk keamanan maksimal</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <h3>Keamanan Multi-Lapis</h3>
                    <p>Sistem keamanan berlapis dengan deteksi ancaman real-time</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-user-secret"></i>
                    </div>
                    <h3>Anonimitas Penuh</h3>
                    <p>Transaksi sepenuhnya anonim dengan teknologi blockchain canggih</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-server"></i>
                    </div>
                    <h3>Infrastruktur Global</h3>
                    <p>Jaringan server global dengan uptime 99.99% untuk akses tanpa batas</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <h3>Analitik Real-Time</h3>
                    <p>Dashboard analitik canggih untuk monitoring transaksi 24/7</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-headset"></i>
                    </div>
                    <h3>Dukungan 24/7</h3>
                    <p>Tim ahli siap membantu Anda kapan saja melalui berbagai kanal</p>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="container">
            <div class="about-content">
                <div class="about-image">
                    <img src="https://images.unsplash.com/photo-1558494949-ef010cbdcc31?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80" alt="About Us">
                </div>
                <div class="about-text">
                    <h2>Tentang CyberClean</h2>
                    <p>Kami adalah perusahaan teknologi terdepan yang mengkhususkan diri dalam solusi keamanan digital dan perlindungan aset kripto. Didirikan pada 2015 oleh tim ahli keamanan siber dan blockchain.</p>
                    <p>Dengan pengalaman lebih dari 8 tahun, kami telah membantu ribuan klien melindungi aset digital mereka dari berbagai ancaman siber dan pencurian identitas.</p>
                    <div class="features">
                        <div class="feature">
                            <i class="fas fa-check-circle"></i>
                            <span>Lebih dari 50,000 transaksi aman diproses setiap hari</span>
                        </div>
                        <div class="feature">
                            <i class="fas fa-check-circle"></i>
                            <span>Jaringan global di 15 negara dengan 30+ data center</span>
                        </div>
                        <div class="feature">
                            <i class="fas fa-check-circle"></i>
                            <span>Sertifikasi keamanan ISO 27001 dan SOC 2 Type II</span>
                        </div>
                        <div class="feature">
                            <i class="fas fa-check-circle"></i>
                            <span>Tim ahli dengan rata-rata pengalaman 10+ tahun</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <div class="container">
            <div class="section-title">
                <h2>Hubungi Kami</h2>
            </div>
            <div class="contact-content">
                <div class="contact-form">
                    <form>
                        <div class="form-group">
                            <label for="name">Nama Lengkap</label>
                            <input type="text" id="name" placeholder="Masukkan nama Anda">
                        </div>
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input type="email" id="email" placeholder="Masukkan email Anda">
                        </div>
                        <div class="form-group">
                            <label for="message">Pesan</label>
                            <textarea id="message" rows="5" placeholder="Ceritakan kebutuhan Anda"></textarea>
                        </div>
                        <button type="submit" class="btn">Kirim Pesan</button>
                    </form>
                </div>
                <div class="contact-info">
                    <h3>Informasi Kontak</h3>
                    <div class="contact-item">
                        <i class="fas fa-map-marker-alt"></i>
                        <div>
                            <h4>Alamat</h4>
                            <p>Cyber Tower, Lantai 42<br>Jl. Teknologi No. 88, papua0951</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-phone-alt"></i>
                        <div>
                            <h4>Telepon</h4>
                            <p>+62 21 1234 5678</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-envelope"></i>
                        <div>
                            <h4>Email</h4>
                            <p>info@cyberclean.id</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-clock"></i>
                        <div>
                            <h4>Jam Operasional</h4>
                            <p>Senin - Jumat: 08:00 - 20:00<br>Sabtu: 09:00 - 17:00</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="logo">
                    <div class="logo-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <div class="logo-text">CyberClean</div>
                </div>
                <div class="social-links">
                    <a href="#"><i class="fab fa-facebook"></i></a>
                    <a href="#"><i class="fab fa-twitter"></i></a>
                    <a href="#"><i class="fab fa-instagram"></i></a>
                    <a href="#"><i class="fab fa-linkedin"></i></a>
                    <a href="#"><i class="fab fa-telegram"></i></a>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2023 CyberClean Solutions. hak Cipta Dilindungi oleh papua0951.</p>
            </div>
        </div>
    </footer>

    <script>
        // Create money rain effect
        function createMoneyRain() {
            const moneyRainContainer = document.getElementById('moneyRain');
            const moneyCount = 30; // Number of money elements
            
            for (let i = 0; i < moneyCount; i++) {
                const money = document.createElement('div');
                money.className = 'money';
                
                // Random horizontal position
                const leftPosition = Math.random() * 100;
                money.style.left = `${leftPosition}%`;
                
                // Random animation duration (speed)
                const duration = 5 + Math.random() * 10; // Between 5-15 seconds
                money.style.animationDuration = `${duration}s`;
                
                // Random animation delay
                const delay = Math.random() * 5; // Up to 5 seconds delay
                money.style.animationDelay = `${delay}s`;
                
                // Random size
                const size = 0.5 + Math.random() * 0.5; // Between 0.5-1.0
                money.style.transform = `scale(${size})`;
                
                moneyRainContainer.appendChild(money);
            }
        }

        // Initialize money rain when page loads
        window.addEventListener('load', createMoneyRain);

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Form submission
        document.querySelector('form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Terima kasih! Pesan Anda telah terkirim. Tim kami akan segera menghubungi Anda.');
            this.reset();
        });
    </script>
</body>
</html> 
