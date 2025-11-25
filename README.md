# RoanaVic-Site
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ceia Natalina - RoanaVic</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Playfair+Display:wght@400;700&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* Custom Animations and Styles */
        :root {
            --gold: #FFD700;
            --red: #D42426;
            --green: #165B33;
            --dark-green: #0B2919;
        }

        body {
            margin: 0;
            overflow: hidden; /* Hide scrollbars for full immersion */
            background: radial-gradient(circle at center, #1a472a 0%, #05160d 100%);
            font-family: 'Lato', sans-serif;
            color: #fff;
        }

        /* Snow Canvas */
        #snow-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 10;
        }

        /* Hanging Lights Animation */
        .lights-string {
            position: absolute;
            top: -10px;
            left: 0;
            width: 100%;
            height: 60px;
            z-index: 20;
            display: flex;
            justify-content: space-around;
            pointer-events: none;
        }

        .light {
            width: 12px;
            height: 24px;
            border-radius: 50%;
            background: var(--gold);
            position: relative;
            animation: swing 3s ease-in-out infinite alternate;
            box-shadow: 0 5px 20px var(--gold);
        }
        
        .light::before {
            content: '';
            position: absolute;
            top: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 4px;
            height: 6px;
            background: #333;
        }

        .light:nth-child(2n) { background: var(--red); box-shadow: 0 5px 20px var(--red); animation-delay: 0.5s; }
        .light:nth-child(3n) { background: #4dabf7; box-shadow: 0 5px 20px #4dabf7; animation-delay: 1s; }
        .light:nth-child(4n) { background: #51cf66; box-shadow: 0 5px 20px #51cf66; animation-delay: 1.5s; }

        @keyframes swing {
            0% { transform: rotate(10deg) translateY(0px); }
            100% { transform: rotate(-10deg) translateY(5px); }
        }

        /* Glass Card */
        .glass-card {
            background: rgba(11, 41, 25, 0.75);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 215, 0, 0.3);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            transition: transform 0.1s ease-out;
            max-height: 90vh;
            overflow-y: auto;
            scrollbar-width: thin;
            scrollbar-color: var(--gold) transparent;
        }

        .glass-card::-webkit-scrollbar {
            width: 6px;
        }
        .glass-card::-webkit-scrollbar-thumb {
            background-color: var(--gold);
            border-radius: 20px;
        }

        /* Typography */
        .font-script {
            font-family: 'Great Vibes', cursive;
        }
        .font-serif {
            font-family: 'Playfair Display', serif;
        }

        /* Interactive Menu Items */
        .menu-item {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
            border-bottom: 1px dashed rgba(255,255,255,0.1);
        }
        
        .menu-item:hover {
            background: rgba(255, 255, 255, 0.1);
            padding-left: 1rem;
            border-color: var(--gold);
        }

        .menu-item:hover .item-icon {
            transform: rotate(15deg) scale(1.2);
            color: var(--gold);
        }

        .gold-text-glow {
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }

        /* Sparkle Effect Class (JS added) */
        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: gold;
            border-radius: 50%;
            pointer-events: none;
            animation: fadeOut 1s forwards;
        }
        @keyframes fadeOut {
            0% { transform: scale(1); opacity: 1; }
            100% { transform: scale(3); opacity: 0; }
        }

        /* Decorative Corners */
        .corner-decoration {
            position: absolute;
            width: 150px;
            height: 150px;
            pointer-events: none;
            z-index: 30;
            opacity: 0.8;
            filter: drop-shadow(0 4px 6px rgba(0,0,0,0.3));
        }
        .corner-tl { top: -20px; left: -20px; transform: rotate(0deg); }
        .corner-tr { top: -20px; right: -20px; transform: rotate(90deg); }
        
        /* Ribbon Header */
        .ribbon-title {
            position: relative;
            background: #9b1c1c;
            color: #fff;
            padding: 10px 40px;
            border-radius: 4px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            display: inline-block;
        }
        .ribbon-title::before, .ribbon-title::after {
            content: '';
            position: absolute;
            top: 10px;
            z-index: -1;
            border: 15px solid #701111;
        }
        .ribbon-title::before { left: -20px; border-left-color: transparent; }
        .ribbon-title::after { right: -20px; border-right-color: transparent; }

    </style>
</head>
<body class="flex items-center justify-center min-h-screen">

    <!-- Canvas for Snow -->
    <canvas id="snow-canvas"></canvas>

    <!-- Hanging Lights -->
    <div class="lights-string">
        <!-- Generated by JS for responsiveness -->
    </div>

    <!-- Main Container -->
    <main id="card-container" class="glass-card w-full max-w-4xl mx-4 rounded-xl p-8 relative z-20 border-t-4 border-yellow-500">
        
        <!-- Corner Decorations (CSS Art/SVGs) -->
        <div class="corner-decoration corner-tl">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 0C50 0 80 30 80 80" stroke="#FFD700" stroke-width="2"/>
                <path d="M20 10L60 30L30 60" fill="#165B33"/> 
                <circle cx="60" cy="30" r="5" fill="#D42426"/>
            </svg>
        </div>
        <div class="corner-decoration corner-tr">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 80C0 30 30 0 80 0" stroke="#FFD700" stroke-width="2"/>
                <path d="M40 30L80 10L70 60" fill="#165B33"/>
                <circle cx="40" cy="30" r="5" fill="#D42426"/>
            </svg>
        </div>

        <!-- Header -->
        <header class="text-center mb-8 relative">
            <h1 class="font-script text-6xl md:text-8xl text-yellow-400 gold-text-glow mb-2 animate-pulse">
                <i class="fa-solid fa-sleigh text-4xl text-white opacity-80 mr-4"></i>
                Feliz Natal
                <i class="fa-solid fa-tree text-4xl text-green-500 opacity-80 ml-4"></i>
            </h1>
            <h2 class="font-serif text-2xl md:text-3xl text-white italic mt-2">Ceia Natalina aqui na Lanchonete RoanaVic</h2>
            
            <div onclick="copyAddress()" class="mt-4 inline-flex items-center gap-2 bg-white/10 hover:bg-white/20 px-4 py-2 rounded-full cursor-pointer transition-colors border border-white/20 group">
                <i class="fa-solid fa-location-dot text-red-500 group-hover:animate-bounce"></i>
                <span class="text-sm md:text-base" id="address-text">Av. Manoel Teixeira Cabral, 777 - Casa Branca, Jundiaí - SP</span>
                <i class="fa-regular fa-copy text-xs opacity-50"></i>
            </div>
        </header>

        <!-- Menu Content Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 md:gap-12">
            
            <!-- Column 1: Sides & Poultry -->
            <section>
                <div class="text-center mb-6">
                    <span class="ribbon-title font-serif text-xl">Segue as opções (1kg)</span>
                </div>
                
                <div class="space-y-3">
                    <!-- Item -->
                    <div class="menu-item p-3 rounded flex justify-between items-center group cursor-pointer">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-bowl-rice text-yellow-500 item-icon transition-transform"></i>
                            <span class="text-lg">Arroz Natalino</span>
                        </div>
                        <span class="font-bold text-yellow-400 text-xl">R$ 76,00</span>
                    </div>

                    <div class="menu-item p-3 rounded flex justify-between items-center group cursor-pointer">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-drumstick-bite text-yellow-500 item-icon transition-transform"></i>
                            <span class="text-lg">Salpicão de Frango</span>
                        </div>
                        <span class="font-bold text-yellow-400 text-xl">R$ 69,00</span>
                    </div>

                    <div class="menu-item p-3 rounded flex justify-between items-center group cursor-pointer">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-bacon text-yellow-500 item-icon transition-transform"></i>
                            <span class="text-lg">Farofa Natalina</span>
                        </div>
                        <span class="font-bold text-yellow-400 text-xl">R$ 59,00</span>
                    </div>

                    <div class="menu-item p-3 rounded flex justify-between items-center group cursor-pointer">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-carrot text-yellow-500 item-icon transition-transform"></i>
                            <div class="flex flex-col">
                                <span class="text-lg leading-tight">Caponata de Berinjela</span>
                                <span class="text-xs text-gray-300 italic">com lagarto fatiado</span>
                            </div>
                        </div>
                        <span class="font-bold text-yellow-400 text-xl">R$ 75,00</span>
                    </div>

                    <div class="mt-6 border-t border-yellow-500/30 pt-4"></div>

                    <div class="menu-item p-3 rounded flex justify-between items-center group cursor-pointer">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-utensils text-red-400 item-icon transition-transform"></i>
                            <span class="text-lg">Frango assado</span>
                        </div>
                        <span class="font-bold text-yellow-400 text-xl">R$ 48,90</span>
                    </div>

                    <div class="menu-item p-3 rounded flex justify-between items-center group cursor-pointer">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-star text-red-400 item-icon transition-transform"></i>
                            <span class="text-lg">Frango Assado recheado</span>
                        </div>
                        <span class="font-bold text-yellow-400 text-xl">R$ 55,00</span>
                    </div>
                </div>
            </section>

            <!-- Column 2: Roasts & Meats -->
            <section>
                <div class="text-center mb-6">
                    <span class="ribbon-title font-serif text-xl" style="background-color: #165B33;">Carnes Assadas</span>
                </div>

                <div class="space-y-3">
                    <!-- By KG items -->
                    <div class="bg-black/20 p-4 rounded-lg border border-yellow-500/20 mb-6 transform hover:scale-105 transition-transform duration-300">
                        <h3 class="font-serif text-yellow-400 text-xl mb-3 border-b border-white/10 pb-2">Especiais por KG</h3>
                        
                        <div class="menu-item p-2 rounded flex justify-between items-center group cursor-pointer">
                            <span class="text-lg"><i class="fa-solid fa-bone mr-2 text-gray-400"></i>Joelho de porco</span>
                            <span class="font-bold text-white">R$ 25,00/kg</span>
                        </div>
                        
                        <div class="menu-item p-2 rounded flex justify-between items-center group cursor-pointer">
                            <span class="text-lg"><i class="fa-solid fa-cow mr-2 text-gray-400"></i>Costela bovina</span>
                            <span class="font-bold text-white">R$ 60,00/kg</span>
                        </div>
                    </div>

                    <!-- Premium List -->
                    <div class="bg-red-900/30 p-6 rounded-lg border border-red-500/30 relative overflow-hidden">
                         <div class="absolute -right-4 -top-4 text-6xl opacity-10 rotate-12">
                            <i class="fa-solid fa-holly-berry"></i>
                         </div>
                        <ul class="space-y-2 text-lg font-serif">
                            <li class="flex items-center gap-2"><i class="fa-solid fa-check text-green-400"></i> Pernil suíno desossado</li>
                            <li class="flex items-center gap-2"><i class="fa-solid fa-check text-green-400"></i> Costelinha de porco</li>
                            <li class="flex items-center gap-2"><i class="fa-solid fa-check text-green-400"></i> Lagarto</li>
                        </ul>
                        
                        <div class="mt-6 text-center">
                            <p class="text-sm text-gray-300 uppercase tracking-widest mb-1">Valor do quilo</p>
                            <div class="text-4xl font-bold text-yellow-400 font-script price-tag">R$ 89,90</div>
                        </div>
                    </div>

                </div>
            </section>
        </div>

        <!-- Footer -->
        <footer class="mt-12 text-center border-t border-white/10 pt-6">
            <div class="inline-block bg-red-700 text-white px-6 py-3 rounded-full shadow-lg transform hover:-translate-y-1 transition-transform animate-bounce-slow cursor-pointer">
                <i class="fa-regular fa-calendar-check mr-2"></i>
                Faça sua encomenda até o dia <strong>20/12</strong>
            </div>
            <p class="mt-4 text-sm opacity-60 font-light">CEP: 13211-224 • Jundiaí - SP</p>
        </footer>

    </main>

    <script>
        // --- 1. Dynamic Lights Generation ---
        const lightsContainer = document.querySelector('.lights-string');
        const numberOfLights = Math.floor(window.innerWidth / 40);
        
        for(let i = 0; i < numberOfLights; i++) {
            const light = document.createElement('div');
            light.classList.add('light');
            // Randomize swing duration slightly for natural feel
            light.style.animationDuration = (2.5 + Math.random()) + 's';
            lightsContainer.appendChild(light);
        }

        // --- 2. Interactive Snow System ---
        const canvas = document.getElementById('snow-canvas');
        const ctx = canvas.getContext('2d');
        
        let width, height;
        let particles = [];
        let mouseX = 0;
        let mouseY = 0;
        let wind = 0;

        function resize() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        }
        
        window.addEventListener('resize', resize);
        resize();

        class Particle {
            constructor() {
                this.reset();
                this.y = Math.random() * height; // Start anywhere on screen initially
            }

            reset() {
                this.x = Math.random() * width;
                this.y = -10;
                this.size = Math.random() * 3 + 1;
                this.speed = Math.random() * 1 + 0.5;
                this.drift = Math.random() * 2 - 1; // Natural wobble
                this.opacity = Math.random() * 0.5 + 0.3;
            }

            update() {
                this.y += this.speed;
                this.x += this.drift + wind; // Add mouse wind interaction

                // Wrap around or reset
                if (this.y > height) {
                    this.reset();
                }
                if (this.x > width) this.x = 0;
                if (this.x < 0) this.x = width;
            }

            draw() {
                ctx.fillStyle = `rgba(255, 255, 255, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function initParticles() {
            particles = [];
            const particleCount = window.innerWidth < 600 ? 50 : 150; // Less snow on mobile
            for (let i = 0; i < particleCount; i++) {
                particles.push(new Particle());
            }
        }

        function animate() {
            ctx.clearRect(0, 0, width, height);
            
            // Decay wind
            wind *= 0.95;

            particles.forEach(p => {
                p.update();
                p.draw();
            });
            requestAnimationFrame(animate);
        }

        initParticles();
        animate();

        // Mouse interaction for wind
        document.addEventListener('mousemove', (e) => {
            const movementX = e.movementX;
            // Add wind based on mouse velocity
            wind += movementX * 0.005;
            // Cap wind
            if(wind > 2) wind = 2;
            if(wind < -2) wind = -2;

            // Parallax effect on Card
            const card = document.getElementById('card-container');
            const xVal = (window.innerWidth / 2 - e.pageX) / 50;
            const yVal = (window.innerHeight / 2 - e.pageY) / 50;
            card.style.transform = `perspective(1000px) rotateY(${xVal}deg) rotateX(${-yVal}deg)`;
        });

        // --- 3. Click Sparkle Effect ---
        document.addEventListener('click', (e) => {
            createSparkle(e.clientX, e.clientY);
        });

        function createSparkle(x, y) {
            for(let i=0; i<8; i++) {
                const sparkle = document.createElement('div');
                sparkle.classList.add('sparkle');
                sparkle.style.left = x + 'px';
                sparkle.style.top = y + 'px';
                
                // Random direction
                const angle = Math.random() * Math.PI * 2;
                const velocity = Math.random() * 30 + 10;
                const tx = Math.cos(angle) * velocity;
                const ty = Math.sin(angle) * velocity;
                
                sparkle.style.transform = `translate(${tx}px, ${ty}px)`;
                sparkle.style.transition = 'all 1s ease-out';
                
                document.body.appendChild(sparkle);
                
                // Trigger animation manually after append to ensure transition works
                requestAnimationFrame(() => {
                    sparkle.style.transform = `translate(${tx * 2}px, ${ty * 2}px) scale(0)`;
                    sparkle.style.opacity = '0';
                });

                setTimeout(() => sparkle.remove(), 1000);
            }
        }

        // --- 4. Copy Address Function ---
        function copyAddress() {
            const text = "Av. Manoel Teixeira Cabral, 777 - Casa Branca, Jundiaí - SP";
            const btn = document.querySelector('#address-text');
            const originalText = btn.innerText;

            // Copy to clipboard fallback logic
            if (navigator.clipboard && window.isSecureContext) {
                navigator.clipboard.writeText(text);
            } else {
                // Fallback
                const textArea = document.createElement("textarea");
                textArea.value = text;
                textArea.style.position = "fixed";
                textArea.style.left = "-9999px";
                textArea.style.top = "0";
                document.body.appendChild(textArea);
                textArea.focus();
                textArea.select();
                try {
                    document.execCommand('copy');
                } catch (err) {
                    console.error('Unable to copy', err);
                }
                document.body.removeChild(textArea);
            }

            // Visual feedback
            btn.innerText = "Endereço Copiado! 🎄";
            btn.parentElement.classList.add('bg-green-700', 'border-green-500');
            
            setTimeout(() => {
                btn.innerText = originalText;
                btn.parentElement.classList.remove('bg-green-700', 'border-green-500');
            }, 2000);
        }

    </script>
</body>
</html>
