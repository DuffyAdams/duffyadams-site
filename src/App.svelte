<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Duffy Adams - Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
            color: #333;
        }

        .background-blur {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(120, 119, 198, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(255, 119, 198, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 40% 80%, rgba(120, 219, 255, 0.3) 0%, transparent 50%);
            z-index: -1;
            animation: backgroundFloat 20s ease-in-out infinite;
        }

        @keyframes backgroundFloat {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(1deg); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        .header {
            text-align: center;
            margin-bottom: 50px;
            padding: 40px 0;
        }

        .header h1 {
            font-size: 3.5rem;
            font-weight: 700;
            color: white;
            text-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
            margin-bottom: 10px;
            opacity: 0;
            animation: fadeInUp 1s ease-out 0.2s forwards;
        }

        .header p {
            font-size: 1.2rem;
            color: rgba(255, 255, 255, 0.8);
            opacity: 0;
            animation: fadeInUp 1s ease-out 0.4s forwards;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 24px;
            padding: 30px;
            margin: 25px 0;
            box-shadow: 
                0 8px 32px rgba(0, 0, 0, 0.1),
                inset 0 1px 0 rgba(255, 255, 255, 0.2);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.8s ease-out forwards;
        }

        .glass-card:nth-child(2) { animation-delay: 0.6s; }
        .glass-card:nth-child(3) { animation-delay: 0.8s; }
        .glass-card:nth-child(4) { animation-delay: 1s; }

        .glass-card:hover {
            transform: translateY(-5px);
            box-shadow: 
                0 12px 40px rgba(0, 0, 0, 0.15),
                inset 0 1px 0 rgba(255, 255, 255, 0.3);
            border-color: rgba(255, 255, 255, 0.3);
        }

        .section-title {
            font-size: 2rem;
            font-weight: 600;
            color: white;
            margin-bottom: 20px;
            text-align: center;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 20px;
            padding: 25px;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .project-card:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.2);
            border-color: rgba(255, 255, 255, 0.4);
        }

        .project-image {
            width: 100%;
            height: 250px;
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.1) 0%, rgba(255, 255, 255, 0.05) 100%);
            border-radius: 16px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .project-image::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(255, 255, 255, 0.1) 50%, transparent 70%);
            transform: translateX(-100%);
            transition: transform 0.6s ease;
        }

        .project-card:hover .project-image::before {
            transform: translateX(100%);
        }

        .project-image img {
            max-width: 100%;
            max-height: 100%;
            border-radius: 12px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
            object-fit: cover;
        }

        .project-placeholder {
            text-align: center;
            color: rgba(255, 255, 255, 0.6);
            font-size: 1rem;
            font-weight: 500;
        }

        .project-title {
            font-size: 1.4rem;
            font-weight: 600;
            color: white;
            margin-bottom: 10px;
        }

        .project-description {
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.6;
            margin-bottom: 15px;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 15px;
        }

        .tag {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
        }

        /* Technology-specific tag colors */
        .tag.react { 
            background: rgba(97, 218, 251, 0.05); 
            border-color: rgba(97, 218, 251, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.node { 
            background: rgba(104, 160, 99, 0.05); 
            border-color: rgba(104, 160, 99, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.vue { 
            background: rgba(76, 175, 80, 0.05); 
            border-color: rgba(76, 175, 80, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.laravel { 
            background: rgba(255, 45, 32, 0.05); 
            border-color: rgba(255, 45, 32, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.javascript { 
            background: rgba(247, 223, 30, 0.05); 
            border-color: rgba(247, 223, 30, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.firebase { 
            background: rgba(255, 193, 7, 0.05); 
            border-color: rgba(255, 193, 7, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.stripe { 
            background: rgba(99, 91, 255, 0.05); 
            border-color: rgba(99, 91, 255, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.mysql { 
            background: rgba(0, 123, 191, 0.05); 
            border-color: rgba(0, 123, 191, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.maps { 
            background: rgba(66, 133, 244, 0.05); 
            border-color: rgba(66, 133, 244, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.realtime { 
            background: rgba(156, 39, 176, 0.05); 
            border-color: rgba(156, 39, 176, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.native { 
            background: rgba(0, 172, 193, 0.05); 
            border-color: rgba(0, 172, 193, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.redux { 
            background: rgba(118, 74, 188, 0.05); 
            border-color: rgba(118, 74, 188, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }
        .tag.notifications { 
            background: rgba(255, 87, 34, 0.05); 
            border-color: rgba(255, 87, 34, 0.15);
            color: rgba(255, 255, 255, 0.95);
        }

        .project-links {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .project-link {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
        }

        .project-link:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .resume-section {
            text-align: center;
        }

        .resume-card {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 16px;
            padding: 30px;
            margin: 20px 0;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .resume-card:hover {
            background: rgba(255, 255, 255, 0.15);
            border-color: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        .resume-icon {
            font-size: 3rem;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 15px;
        }

        .resume-title {
            color: white;
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 10px;
        }

        .resume-description {
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 20px;
        }

        .resume-button {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
            text-decoration: none;
            display: inline-block;
        }

        .resume-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.3);
        }

        .about-section {
            text-align: center;
            color: rgba(255, 255, 255, 0.9);
            line-height: 1.6;
            font-size: 1.1rem;
        }

        .contact-section {
            text-align: center;
        }

        .contact-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .contact-link {
            background: rgba(255, 255, 255, 0.15);
            color: white;
            padding: 12px 24px;
            border-radius: 50px;
            text-decoration: none;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
            font-weight: 500;
            position: relative;
            overflow: hidden;
        }

        .contact-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .contact-link:hover::before {
            left: 100%;
        }

        .contact-link:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
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

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2.5rem;
            }
            
            .glass-card {
                padding: 20px;
                margin: 15px 0;
            }
            
            .projects-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .contact-links {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <div class="background-blur"></div>
    
    <div class="container">
        <header class="header">
            <h1>Duffy Adams</h1>
            <p>Full Stack Developer & UI/UX Designer</p>
        </header>

        <div class="glass-card">
            <h2 class="section-title">About Me</h2>
            <div class="about-section">
                <p>
                    I'm a passionate full-stack developer with a keen eye for design and user experience. 
                    I specialize in creating modern, responsive applications that solve real-world problems 
                    while maintaining beautiful, intuitive interfaces.
                </p>
            </div>
        </div>

        <div class="glass-card">
            <h2 class="section-title">Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-image">
                        <div class="project-placeholder">
                            🚦 Traffic Management App
                        </div>
                    </div>
                    <h3 class="project-title">Traffic App</h3>
                    <p class="project-description">
                        A comprehensive traffic management application featuring real-time traffic data, 
                        route optimization, and intelligent congestion prediction to help users navigate 
                        efficiently through urban environments.
                    </p>
                    <div class="project-tags">
                        <span class="tag react">React</span>
                        <span class="tag node">Node.js</span>
                        <span class="tag maps">Maps API</span>
                        <span class="tag realtime">Real-time Data</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Demo</a>
                        <a href="#" class="project-link">GitHub</a>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-image">
                        <div class="project-placeholder">
                            💼 E-Commerce Platform
                        </div>
                    </div>
                    <h3 class="project-title">E-Commerce Solution</h3>
                    <p class="project-description">
                        Modern e-commerce platform with advanced product filtering, secure payment processing, 
                        and an intuitive admin dashboard for inventory management and analytics.
                    </p>
                    <div class="project-tags">
                        <span class="tag vue">Vue.js</span>
                        <span class="tag laravel">Laravel</span>
                        <span class="tag stripe">Stripe API</span>
                        <span class="tag mysql">MySQL</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Demo</a>
                        <a href="#" class="project-link">GitHub</a>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-image">
                        <div class="project-placeholder">
                            📱 Mobile Task Manager
                        </div>
                    </div>
                    <h3 class="project-title">Task Management App</h3>
                    <p class="project-description">
                        Cross-platform mobile application for task management with collaborative features, 
                        deadline tracking, and productivity analytics designed for modern teams.
                    </p>
                    <div class="project-tags">
                        <span class="tag native">React Native</span>
                        <span class="tag firebase">Firebase</span>
                        <span class="tag redux">Redux</span>
                        <span class="tag notifications">Push Notifications</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View Demo</a>
                        <a href="#" class="project-link">GitHub</a>
                    </div>
                </div>
            </div>
        </div>

        <div class="glass-card">
            <h2 class="section-title">Resume</h2>
            <div class="resume-section">
                <div class="resume-card">
                    <div class="resume-icon">📄</div>
                    <div class="resume-title">Download My Resume</div>
                    <div class="resume-description">
                        View my complete professional experience, education, and technical skills
                    </div>
                    <a href="#" class="resume-button">Download PDF</a>
                </div>
            </div>
        </div>

        <div class="glass-card">
            <h2 class="section-title">Let's Connect</h2>
            <div class="contact-section">
                <p style="color: rgba(255, 255, 255, 0.8); margin-bottom: 20px;">
                    I'm always interested in new opportunities and collaborations
                </p>
                <div class="contact-links">
                    <a href="mailto:duffy@duffyadams.com" class="contact-link">✉️ Email</a>
                    <a href="https://linkedin.com/in/duffyadams" class="contact-link">💼 LinkedIn</a>
                    <a href="https://github.com/duffyadams" class="contact-link">🐙 GitHub</a>
                    <a href="https://twitter.com/duffyadams" class="contact-link">🐦 Twitter</a>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Add smooth scrolling and parallax effect
        window.addEventListener('scroll', () => {
            const scrollY = window.scrollY;
            const cards = document.querySelectorAll('.glass-card');
            
            cards.forEach((card, index) => {
                const rect = card.getBoundingClientRect();
                const isVisible = rect.top < window.innerHeight && rect.bottom > 0;
                
                if (isVisible) {
                    const speed = 0.5 + (index * 0.1);
                    card.style.transform = `translateY(${scrollY * speed * 0.02}px)`;
                }
            });
        });

        // Add intersection observer for scroll animations
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

        // Observe all project cards for staggered animations
        document.querySelectorAll('.project-card').forEach((card, index) => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(30px)';
            card.style.transition = `all 0.6s ease ${index * 0.2}s`;
            observer.observe(card);
        });
    </script>
</body>
</html>