<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Support My Work | Crypto Donations</title>
    <script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    },
                    colors: {
                        binance: {
                            yellow: '#F0B90B',
                            yellowLight: '#FCD535',
                            yellowDark: '#C99400',
                            dark: '#1E2026',
                            darker: '#14151A',
                            card: '#2B3139',
                            text: '#EAECEF',
                            muted: '#848E9C',
                        }
                    },
                    animation: {
                        'float': 'float 6s ease-in-out infinite',
                        'pulse-slow': 'pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                        'shimmer': 'shimmer 2s linear infinite',
                        'fade-in-up': 'fadeInUp 0.8s ease-out forwards',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-20px)' },
                        },
                        shimmer: {
                            '0%': { backgroundPosition: '-200% 0' },
                            '100%': { backgroundPosition: '200% 0' },
                        },
                        fadeInUp: {
                            '0%': { opacity: '0', transform: 'translateY(30px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        }
                    }
                }
            }
        }
    </script>
    <style>
        * { scroll-behavior: smooth; }
        body { 
            background-color: #0B0E11; 
            color: #EAECEF;
            font-family: 'Inter', system-ui, sans-serif;
        }
        .glass {
            background: rgba(43, 49, 57, 0.6);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(240, 185, 11, 0.1);
        }
        .glass-strong {
            background: rgba(20, 21, 26, 0.95);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
        }
        .gradient-text {
            background: linear-gradient(135deg, #F0B90B 0%, #FCD535 50%, #F0B90B 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .btn-primary {
            background: linear-gradient(135deg, #F0B90B 0%, #FCD535 100%);
            color: #14151A;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(240, 185, 11, 0.3);
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(240, 185, 11, 0.5);
        }
        .card-hover {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .card-hover:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(240, 185, 11, 0.15);
            border-color: rgba(240, 185, 11, 0.3);
        }
        .progress-bar {
            background: linear-gradient(90deg, #F0B90B 0%, #FCD535 100%);
            box-shadow: 0 0 20px rgba(240, 185, 11, 0.5);
        }
        .qr-glow {
            box-shadow: 0 0 60px rgba(240, 185, 11, 0.2), 0 0 100px rgba(240, 185, 11, 0.1);
        }
        .modal-enter {
            animation: modalEnter 0.3s ease-out forwards;
        }
        @keyframes modalEnter {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }
        .scroll-reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease-out;
        }
        .scroll-reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .bg-grid {
            background-image: radial-gradient(circle, rgba(240, 185, 11, 0.08) 1px, transparent 1px);
            background-size: 50px 50px;
        }
        .noise {
            position: relative;
        }
        .noise::before {
            content: '';
            position: absolute;
            inset: 0;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
            pointer-events: none;
            z-index: 1;
        }
        .nav-blur {
            background: rgba(11, 14, 17, 0.8);
            backdrop-filter: blur(20px);
        }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useEffect, useRef } = React;
        
        // Icons
        const Icons = {
            Bitcoin: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <path d="M11.767 19.089c4.924.868 6.14-6.025 1.216-6.894m-1.216 6.894L5.86 18.047m5.908 1.042-.347 1.97m1.563-8.864c4.924.869 6.14-6.025 1.215-6.893m-1.215 6.893-3.94-.694m5.155-6.2L8.29 4.26m5.908 1.042L16.9 2.75"/>
                </svg>
            ),
            Shield: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
                </svg>
            ),
            Heart: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
                </svg>
            ),
            Rocket: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <path d="M4.5 16.5c-1.5 1.26-2 5-2 5s3.74-.5 5-2c.71-.84.7-2.13-.09-2.91a2.18 2.18 0 0 0-2.91-.09z"/>
                    <path d="m12 15-3-3a22 22 0 0 1 2-3.95A12.88 12.88 0 0 1 22 2c0 2.72-.78 7.5-6 11a22.35 22.35 0 0 1-4 2z"/>
                    <path d="M9 12H4s.55-3.03 2-4c1.62-1.08 5 0 5 0"/>
                    <path d="M12 15v5s3.03-.55 4-2c1.08-1.62 0-5 0-5"/>
                </svg>
            ),
            Zap: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/>
                </svg>
            ),
            Globe: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <circle cx="12" cy="12" r="10"/>
                    <line x1="2" y1="12" x2="22" y2="12"/>
                    <path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/>
                </svg>
            ),
            ChevronDown: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <polyline points="6 9 12 15 18 9"/>
                </svg>
            ),
            X: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <line x1="18" y1="6" x2="6" y2="18"/>
                    <line x1="6" y1="6" x2="18" y2="18"/>
                </svg>
            ),
            Copy: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <rect x="9" y="9" width="13" height="13" rx="2" ry="2"/>
                    <path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/>
                </svg>
            ),
            Check: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <polyline points="20 6 9 17 4 12"/>
                </svg>
            ),
            Send: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <line x1="22" y1="2" x2="11" y2="13"/>
                    <polygon points="22 2 15 22 11 13 2 9 22 2"/>
                </svg>
            ),
            Menu: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <line x1="3" y1="12" x2="21" y2="12"/>
                    <line x1="3" y1="6" x2="21" y2="6"/>
                    <line x1="3" y1="18" x2="21" y2="18"/>
                </svg>
            ),
            Twitter: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
                </svg>
            ),
            Github: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                </svg>
            ),
            Linkedin: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                </svg>
            ),
            ExternalLink: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/>
                    <polyline points="15 3 21 3 21 9"/>
                    <line x1="10" y1="14" x2="21" y2="3"/>
                </svg>
            ),
            QrCode: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <rect x="3" y="3" width="5" height="5"/>
                    <rect x="16" y="3" width="5" height="5"/>
                    <rect x="3" y="16" width="5" height="5"/>
                    <line x1="21" y1="16" x2="21" y2="16.01"/>
                    <line x1="21" y1="21" x2="21" y2="21.01"/>
                    <line x1="16" y1="21" x2="16" y2="21.01"/>
                    <line x1="16" y1="16" x2="16" y2="16.01"/>
                    <line x1="11" y1="21" x2="11" y2="21.01"/>
                    <line x1="11" y1="16" x2="11" y2="16.01"/>
                    <line x1="21" y1="11" x2="21" y2="11.01"/>
                    <line x1="16" y1="11" x2="16" y2="11.01"/>
                    <line x1="11" y1="11" x2="11" y2="11.01"/>
                    <line x1="8" y1="11" x2="8" y2="11.01"/>
                    <line x1="3" y1="11" x2="3" y2="11.01"/>
                    <line x1="11" y1="3" x2="11" y2="3.01"/>
                    <line x1="11" y1="8" x2="11" y2="8.01"/>
                    <line x1="8" y1="8" x2="8" y2="8.01"/>
                    <line x1="8" y1="3" x2="8" y2="3.01"/>
                    <line x1="21" y1="8" x2="21" y2="8.01"/>
                    <line x1="16" y1="8" x2="16" y2="8.01"/>
                </svg>
            ),
            Maximize2: () => (
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                    <polyline points="15 3 21 3 21 9"/>
                    <polyline points="9 21 3 21 3 15"/>
                    <line x1="21" y1="3" x2="14" y2="10"/>
                    <line x1="3" y1="21" x2="10" y2="14"/>
                </svg>
            )
        };

        // Scroll Reveal Hook
        const useScrollReveal = () => {
            useEffect(() => {
                const observer = new IntersectionObserver((entries) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            entry.target.classList.add('visible');
                        }
                    });
                }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });

                document.querySelectorAll('.scroll-reveal').forEach(el => observer.observe(el));
                return () => observer.disconnect();
            }, []);
        };

        // Navigation
        const Navbar = () => {
            const [scrolled, setScrolled] = useState(false);
            const [mobileOpen, setMobileOpen] = useState(false);

            useEffect(() => {
                const handleScroll = () => setScrolled(window.scrollY > 50);
                window.addEventListener('scroll', handleScroll);
                return () => window.removeEventListener('scroll', handleScroll);
            }, []);

            const navLinks = [
                { href: '#donate', label: 'Donate' },
                { href: '#why', label: 'Why Donate' },
                { href: '#progress', label: 'Progress' },
                { href: '#faq', label: 'FAQ' },
                { href: '#contact', label: 'Contact' },
            ];

            return (
                <nav className={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 ${scrolled ? 'nav-blur shadow-lg shadow-black/20' : 'bg-transparent'}`}>
                    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="flex items-center justify-between h-16">
                            <a href="#" className="flex items-center gap-2 group">
                                <div className="w-8 h-8 bg-gradient-to-br from-binance-yellow to-binance-yellowLight rounded-lg flex items-center justify-center group-hover:scale-110 transition-transform">
                                    <Icons.Bitcoin />
                                </div>
                                <span className="font-bold text-lg tracking-tight">Support<span className="text-binance-yellow">MyWork</span></span>
                            </a>
                            
                            <div className="hidden md:flex items-center gap-8">
                                {navLinks.map(link => (
                                    <a key={link.href} href={link.href} className="text-sm font-medium text-binance-muted hover:text-binance-yellow transition-colors relative group">
                                        {link.label}
                                        <span className="absolute -bottom-1 left-0 w-0 h-0.5 bg-binance-yellow transition-all group-hover:w-full"/>
                                    </a>
                                ))}
                                <a href="#donate" className="btn-primary px-5 py-2 rounded-full text-sm font-bold">
                                    Donate Now
                                </a>
                            </div>

                            <button 
                                className="md:hidden text-binance-text p-2"
                                onClick={() => setMobileOpen(!mobileOpen)}
                            >
                                <Icons.Menu />
                            </button>
                        </div>
                    </div>

                    {/* Mobile Menu */}
                    <div className={`md:hidden overflow-hidden transition-all duration-300 ${mobileOpen ? 'max-h-96' : 'max-h-0'}`}>
                        <div className="nav-blur px-4 py-4 space-y-3 border-t border-white/5">
                            {navLinks.map(link => (
                                <a 
                                    key={link.href} 
                                    href={link.href} 
                                    className="block text-sm font-medium text-binance-muted hover:text-binance-yellow transition-colors py-2"
                                    onClick={() => setMobileOpen(false)}
                                >
                                    {link.label}
                                </a>
                            ))}
                            <a href="#donate" className="block btn-primary px-5 py-3 rounded-full text-sm font-bold text-center mt-4">
                                Donate Now
                            </a>
                        </div>
                    </div>
                </nav>
            );
        };

        // Hero Section
        const Hero = () => {
            return (
                <section className="relative min-h-screen flex items-center justify-center overflow-hidden noise">
                    <div className="absolute inset-0 bg-grid opacity-30" />
                    
                    {/* Animated Background Elements */}
                    <div className="absolute top-20 left-10 w-72 h-72 bg-binance-yellow/10 rounded-full blur-3xl animate-pulse-slow" />
                    <div className="absolute bottom-20 right-10 w-96 h-96 bg-binance-yellow/5 rounded-full blur-3xl animate-pulse-slow" style={{ animationDelay: '2s' }} />
                    
                    <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
                        <div className="animate-fade-in-up">
                            <div className="inline-flex items-center gap-2 px-4 py-2 rounded-full glass mb-8 border-binance-yellow/20">
                                <span className="w-2 h-2 rounded-full bg-binance-yellow animate-pulse" />
                                <span className="text-sm font-medium text-binance-yellow">Accepting Crypto Donations</span>
                            </div>
                            
                            <h1 className="text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-black tracking-tight mb-6">
                                Support <span className="gradient-text">My Work</span>
                            </h1>
                            
                            <p className="text-lg sm:text-xl md:text-2xl text-binance-muted max-w-3xl mx-auto mb-10 leading-relaxed">
                                Your donations help me create more content, projects, and resources. 
                                Every contribution is appreciated.
                            </p>
                            
                            <div className="flex flex-col sm:flex-row items-center justify-center gap-4">
                                <a href="#donate" className="btn-primary px-8 py-4 rounded-full text-lg font-bold flex items-center gap-2 group">
                                    <Icons.Heart />
                                    Donate Now
                                    <Icons.ExternalLink />
                                </a>
                                <a href="#why" className="px-8 py-4 rounded-full text-lg font-bold border border-binance-card hover:border-binance-yellow/50 hover:bg-binance-card/50 transition-all flex items-center gap-2">
                                    Learn More
                                    <Icons.ChevronDown />
                                </a>
                            </div>
                        </div>

                        {/* Floating Stats */}
                        <div className="mt-20 grid grid-cols-2 md:grid-cols-4 gap-4 max-w-4xl mx-auto">
                            {[
                                { label: 'Supporters', value: '150+' },
                                { label: 'Raised', value: '$250' },
                                { label: 'Projects', value: '12' },
                                { label: 'Goal', value: '$1,000' },
                            ].map((stat, i) => (
                                <div key={i} className="glass rounded-2xl p-4 animate-fade-in-up" style={{ animationDelay: `${0.2 * (i + 1)}s` }}>
                                    <div className="text-2xl font-bold text-binance-yellow">{stat.value}</div>
                                    <div className="text-sm text-binance-muted">{stat.label}</div>
                                </div>
                            ))}
                        </div>
                    </div>

                    <div className="absolute bottom-8 left-1/2 -translate-x-1/2 animate-bounce">
                        <a href="#donate" className="text-binance-muted hover:text-binance-yellow transition-colors">
                            <Icons.ChevronDown />
                        </a>
                    </div>
                </section>
            );
        };

        // QR Code Modal
        const QRModal = ({ isOpen, onClose }) => {
            const [copied, setCopied] = useState(false);
            const binanceId = 'User-183f7';

            if (!isOpen) return null;

            const handleCopy = () => {
                navigator.clipboard.writeText(binanceId);
                setCopied(true);
                setTimeout(() => setCopied(false), 2000);
            };

            return (
                <div className="fixed inset-0 z-[100] flex items-center justify-center p-4" onClick={onClose}>
                    <div className="absolute inset-0 bg-black/80 backdrop-blur-sm" />
                    <div className="relative glass-strong rounded-3xl p-8 max-w-md w-full modal-enter border border-binance-yellow/20" onClick={e => e.stopPropagation()}>
                        <button 
                            onClick={onClose}
                            className="absolute top-4 right-4 p-2 rounded-full hover:bg-white/10 transition-colors text-binance-muted hover:text-white"
                        >
                            <Icons.X />
                        </button>
                        
                        <div className="text-center mb-6">
                            <h3 className="text-2xl font-bold mb-2">Scan to Donate</h3>
                            <p className="text-binance-muted text-sm">Use the Binance App to scan this QR code</p>
                        </div>

                        <div className="bg-white rounded-2xl p-4 mb-6 qr-glow mx-auto w-fit">
                            <img 
                                src="qr-code.jpg" 
                                alt="Binance Pay QR Code" 
                                className="w-64 h-64 object-contain"
                            />
                        </div>

                        <div className="glass rounded-xl p-4 mb-4">
                            <div className="flex items-center justify-between mb-2">
                                <span className="text-sm text-binance-muted">Binance Pay ID</span>
                                <button 
                                    onClick={handleCopy}
                                    className="flex items-center gap-1 text-sm text-binance-yellow hover:text-binance-yellowLight transition-colors"
                                >
                                    {copied ? <Icons.Check /> : <Icons.Copy />}
                                    {copied ? 'Copied!' : 'Copy'}
                                </button>
                            </div>
                            <div className="font-mono text-lg font-bold text-binance-text">{binanceId}</div>
                        </div>

                        <p className="text-center text-xs text-binance-muted">
                            Secure payments powered by Binance Pay
                        </p>
                    </div>
                </div>
            );
        };

        // Donation Section
        const DonationSection = () => {
            const [modalOpen, setModalOpen] = useState(false);

            return (
                <section id="donate" className="py-24 relative">
                    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="text-center mb-16 scroll-reveal">
                            <div className="inline-flex items-center gap-2 px-4 py-2 rounded-full glass mb-6">
                                <Icons.QrCode />
                                <span className="text-sm font-medium text-binance-yellow">Quick & Easy</span>
                            </div>
                            <h2 className="text-4xl md:text-5xl font-bold mb-4">Make a <span className="gradient-text">Donation</span></h2>
                            <p className="text-binance-muted text-lg max-w-2xl mx-auto">
                                Scan the QR code using the Binance App to make a donation instantly and securely.
                            </p>
                        </div>

                        <div className="max-w-lg mx-auto scroll-reveal">
                            <div className="glass rounded-3xl p-8 md:p-12 relative overflow-hidden group cursor-pointer" onClick={() => setModalOpen(true)}>
                                {/* Glow Effect */}
                                <div className="absolute inset-0 bg-gradient-to-br from-binance-yellow/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500" />
                                
                                <div className="relative z-10 text-center">
                                    <div className="bg-white rounded-2xl p-4 mb-8 qr-glow inline-block transform group-hover:scale-105 transition-transform duration-500">
                                        <img 
                                            src="qr-code.jpg" 
                                            alt="Binance Pay QR Code" 
                                            className="w-56 h-56 object-contain"
                                        />
                                    </div>
                                    
                                    <div className="flex items-center justify-center gap-2 mb-4 text-binance-yellow">
                                        <Icons.Maximize2 />
                                        <span className="text-sm font-medium">Click to enlarge</span>
                                    </div>

                                    <h3 className="text-xl font-bold mb-2">Scan with Binance App</h3>
                                    <p className="text-binance-muted text-sm mb-6">
                                        Open your Binance app, tap the scan icon, and point your camera at this QR code.
                                    </p>

                                    <div className="flex items-center justify-center gap-2 px-4 py-2 rounded-full bg-binance-yellow/10 border border-binance-yellow/20">
                                        <div className="w-2 h-2 rounded-full bg-binance-yellow animate-pulse" />
                                        <span className="text-sm font-bold text-binance-yellow">Binance Pay Accepted</span>
                                    </div>
                                </div>
                            </div>

                            {/* Quick Copy ID */}
                            <div className="mt-6 glass rounded-2xl p-6 scroll-reveal">
                                <div className="flex flex-col sm:flex-row items-center justify-between gap-4">
                                    <div>
                                        <div className="text-sm text-binance-muted mb-1">Or send directly to</div>
                                        <div className="font-mono text-lg font-bold text-binance-text">User-183f7</div>
                                    </div>
                                    <CopyButton text="User-183f7" />
                                </div>
                            </div>
                        </div>
                    </div>

                    <QRModal isOpen={modalOpen} onClose={() => setModalOpen(false)} />
                </section>
            );
        };

        // Copy Button Component
        const CopyButton = ({ text }) => {
            const [copied, setCopied] = useState(false);

            const handleCopy = () => {
                navigator.clipboard.writeText(text);
                setCopied(true);
                setTimeout(() => setCopied(false), 2000);
            };

            return (
                <button 
                    onClick={handleCopy}
                    className="flex items-center gap-2 px-4 py-2 rounded-full bg-binance-card hover:bg-binance-yellow/20 border border-binance-card hover:border-binance-yellow/30 transition-all text-sm font-medium"
                >
                    {copied ? <Icons.Check /> : <Icons.Copy />}
                    {copied ? 'Copied!' : 'Copy ID'}
                </button>
            );
        };

        // Why Donate Section
        const WhyDonate = () => {
            const cards = [
                {
                    icon: <Icons.Rocket />,
                    title: 'Support Future Projects',
                    description: 'Your contributions directly fund the development of new tools, applications, and open-source projects that benefit the community.',
                    color: 'from-yellow-500/20 to-orange-500/20'
                },
                {
                    icon: <Icons.Zap />,
                    title: 'Help Maintain Services',
                    description: 'Keep existing services, websites, and resources running smoothly. Server costs and maintenance require ongoing support.',
                    color: 'from-blue-500/20 to-cyan-500/20'
                },
                {
                    icon: <Icons.Heart />,
                    title: 'Encourage More Content',
                    description: 'Motivate the creation of more tutorials, articles, videos, and educational content for the crypto and tech community.',
                    color: 'from-red-500/20 to-pink-500/20'
                }
            ];

            return (
                <section id="why" className="py-24 relative bg-binance-darker/50">
                    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="text-center mb-16 scroll-reveal">
                            <h2 className="text-4xl md:text-5xl font-bold mb-4">Why <span className="gradient-text">Donate?</span></h2>
                            <p className="text-binance-muted text-lg max-w-2xl mx-auto">
                                Every contribution, no matter how small, makes a significant impact on what I can create and share.
                            </p>
                        </div>

                        <div className="grid md:grid-cols-3 gap-6">
                            {cards.map((card, i) => (
                                <div 
                                    key={i} 
                                    className="glass rounded-2xl p-8 card-hover scroll-reveal border border-white/5"
                                    style={{ transitionDelay: `${i * 100}ms` }}
                                >
                                    <div className={`w-14 h-14 rounded-2xl bg-gradient-to-br ${card.color} flex items-center justify-center mb-6 text-binance-yellow`}>
                                        {card.icon}
                                    </div>
                                    <h3 className="text-xl font-bold mb-3">{card.title}</h3>
                                    <p className="text-binance-muted leading-relaxed">
                                        {card.description}
                                    </p>
                                </div>
                            ))}
                        </div>
                    </div>
                </section>
            );
        };

        // Progress Section
        const ProgressSection = () => {
            const goal = 1000;
            const current = 250;
            const percentage = (current / goal) * 100;

            return (
                <section id="progress" className="py-24 relative">
                    <div className="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="text-center mb-12 scroll-reveal">
                            <h2 className="text-4xl md:text-5xl font-bold mb-4">Donation <span className="gradient-text">Progress</span></h2>
                            <p className="text-binance-muted">Help us reach our monthly goal</p>
                        </div>

                        <div className="glass rounded-3xl p-8 md:p-12 scroll-reveal">
                            <div className="flex justify-between items-end mb-4">
                                <div>
                                    <div className="text-sm text-binance-muted mb-1">Current</div>
                                    <div className="text-3xl font-bold text-binance-yellow">${current.toLocaleString()}</div>
                                </div>
                                <div className="text-right">
                                    <div className="text-sm text-binance-muted mb-1">Goal</div>
                                    <div className="text-3xl font-bold">${goal.toLocaleString()}</div>
                                </div>
                            </div>

                            <div className="relative h-6 bg-binance-card rounded-full overflow-hidden mb-6">
                                <div 
                                    className="absolute top-0 left-0 h-full progress-bar rounded-full transition-all duration-1000 ease-out"
                                    style={{ width: `${percentage}%` }}
                                />
                                <div className="absolute top-0 left-0 h-full w-full bg-gradient-to-r from-transparent via-white/10 to-transparent animate-shimmer" style={{ backgroundSize: '200% 100%' }} />
                            </div>

                            <div className="flex justify-between items-center text-sm">
                                <span className="text-binance-muted">{percentage.toFixed(1)}% completed</span>
                                <span className="text-binance-yellow font-bold">${(goal - current).toLocaleString()} to go</span>
                            </div>

                            <div className="mt-8 grid grid-cols-3 gap-4 text-center">
                                <div className="glass rounded-xl p-4">
                                    <div className="text-2xl font-bold text-binance-yellow">25%</div>
                                    <div className="text-xs text-binance-muted mt-1">Completed</div>
                                </div>
                                <div className="glass rounded-xl p-4">
                                    <div className="text-2xl font-bold">12</div>
                                    <div className="text-xs text-binance-muted mt-1">Donors</div>
                                </div>
                                <div className="glass rounded-xl p-4">
                                    <div className="text-2xl font-bold">$21</div>
                                    <div className="text-xs text-binance-muted mt-1">Avg. Donation</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </section>
            );
        };

        // FAQ Section
        const FAQ = () => {
            const [openIndex, setOpenIndex] = useState(null);

            const faqs = [
                {
                    question: 'How do I donate?',
                    answer: 'Simply open your Binance app, tap the scan icon in the top right corner, and point your camera at the QR code displayed on this page. You can also copy the Binance Pay ID (User-183f7) and paste it directly in the Binance Pay section of your app.'
                },
                {
                    question: 'Is Binance Pay secure?',
                    answer: 'Yes, Binance Pay is a secure payment system built by Binance, one of the world\'s largest cryptocurrency exchanges. All transactions are encrypted and protected by Binance\'s industry-leading security infrastructure. Your payment information is never shared with the recipient.'
                },
                {
                    question: 'Can I donate any amount?',
                    answer: 'Absolutely! There is no minimum or maximum donation amount. Whether it\'s $1 or $1000, every contribution is deeply appreciated and helps support the creation of more content and projects. You can donate any cryptocurrency supported by Binance Pay.'
                }
            ];

            return (
                <section id="faq" className="py-24 relative bg-binance-darker/50">
                    <div className="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="text-center mb-16 scroll-reveal">
                            <h2 className="text-4xl md:text-5xl font-bold mb-4">Frequently Asked <span className="gradient-text">Questions</span></h2>
                            <p className="text-binance-muted">Everything you need to know about donating</p>
                        </div>

                        <div className="space-y-4">
                            {faqs.map((faq, i) => (
                                <div 
                                    key={i} 
                                    className="glass rounded-2xl overflow-hidden scroll-reveal border border-white/5"
                                    style={{ transitionDelay: `${i * 100}ms` }}
                                >
                                    <button
                                        className="w-full px-6 py-5 flex items-center justify-between text-left hover:bg-white/5 transition-colors"
                                        onClick={() => setOpenIndex(openIndex === i ? null : i)}
                                    >
                                        <span className="font-semibold text-lg pr-4">{faq.question}</span>
                                        <span className={`transform transition-transform duration-300 flex-shrink-0 ${openIndex === i ? 'rotate-180' : ''}`}>
                                            <Icons.ChevronDown />
                                        </span>
                                    </button>
                                    <div 
                                        className={`overflow-hidden transition-all duration-300 ${openIndex === i ? 'max-h-96' : 'max-h-0'}`}
                                    >
                                        <div className="px-6 pb-5 text-binance-muted leading-relaxed">
                                            {faq.answer}
                                        </div>
                                    </div>
                                </div>
                            ))}
                        </div>
                    </div>
                </section>
            );
        };

        // Contact Section
        const Contact = () => {
            const [formData, setFormData] = useState({ name: '', email: '', message: '' });
            const [submitted, setSubmitted] = useState(false);

            const handleSubmit = (e) => {
                e.preventDefault();
                setSubmitted(true);
                setTimeout(() => {
                    setSubmitted(false);
                    setFormData({ name: '', email: '', message: '' });
                }, 3000);
            };

            return (
                <section id="contact" className="py-24 relative">
                    <div className="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="text-center mb-16 scroll-reveal">
                            <h2 className="text-4xl md:text-5xl font-bold mb-4">Get In <span className="gradient-text">Touch</span></h2>
                            <p className="text-binance-muted">Have questions or want to collaborate? Reach out!</p>
                        </div>

                        <div className="grid md:grid-cols-5 gap-8">
                            <div className="md:col-span-2 space-y-6 scroll-reveal">
                                <div className="glass rounded-2xl p-6">
                                    <div className="w-10 h-10 rounded-xl bg-binance-yellow/10 flex items-center justify-center text-binance-yellow mb-4">
                                        <Icons.Globe />
                                    </div>
                                    <h3 className="font-bold mb-2">Response Time</h3>
                                    <p className="text-sm text-binance-muted">I typically respond within 24-48 hours.</p>
                                </div>
                                <div className="glass rounded-2xl p-6">
                                    <div className="w-10 h-10 rounded-xl bg-binance-yellow/10 flex items-center justify-center text-binance-yellow mb-4">
                                        <Icons.Shield />
                                    </div>
                                    <h3 className="font-bold mb-2">Privacy</h3>
                                    <p className="text-sm text-binance-muted">Your information is kept confidential and never shared.</p>
                                </div>
                            </div>

                            <form onSubmit={handleSubmit} className="md:col-span-3 glass rounded-2xl p-8 scroll-reveal border border-white/5">
                                {submitted ? (
                                    <div className="h-full flex flex-col items-center justify-center text-center py-12">
                                        <div className="w-16 h-16 rounded-full bg-binance-yellow/20 flex items-center justify-center text-binance-yellow mb-4">
                                            <Icons.Check />
                                        </div>
                                        <h3 className="text-xl font-bold mb-2">Message Sent!</h3>
                                        <p className="text-binance-muted">Thank you for reaching out. I'll get back to you soon.</p>
                                    </div>
                                ) : (
                                    <div className="space-y-5">
                                        <div>
                                            <label className="block text-sm font-medium mb-2">Name</label>
                                            <input
                                                type="text"
                                                required
                                                value={formData.name}
                                                onChange={e => setFormData({...formData, name: e.target.value})}
                                                className="w-full px-4 py-3 rounded-xl bg-binance-dark border border-binance-card focus:border-binance-yellow focus:outline-none focus:ring-1 focus:ring-binance-yellow/50 transition-all text-binance-text placeholder-binance-muted"
                                                placeholder="Your name"
                                            />
                                        </div>
                                        <div>
                                            <label className="block text-sm font-medium mb-2">Email</label>
                                            <input
                                                type="email"
                                                required
                                                value={formData.email}
                                                onChange={e => setFormData({...formData, email: e.target.value})}
                                                className="w-full px-4 py-3 rounded-xl bg-binance-dark border border-binance-card focus:border-binance-yellow focus:outline-none focus:ring-1 focus:ring-binance-yellow/50 transition-all text-binance-text placeholder-binance-muted"
                                                placeholder="your@email.com"
                                            />
                                        </div>
                                        <div>
                                            <label className="block text-sm font-medium mb-2">Message</label>
                                            <textarea
                                                required
                                                rows={4}
                                                value={formData.message}
                                                onChange={e => setFormData({...formData, message: e.target.value})}
                                                className="w-full px-4 py-3 rounded-xl bg-binance-dark border border-binance-card focus:border-binance-yellow focus:outline-none focus:ring-1 focus:ring-binance-yellow/50 transition-all text-binance-text placeholder-binance-muted resize-none"
                                                placeholder="Your message..."
                                            />
                                        </div>
                                        <button type="submit" className="w-full btn-primary py-3 rounded-xl font-bold flex items-center justify-center gap-2">
                                            <Icons.Send />
                                            Send Message
                                        </button>
                                    </div>
                                )}
                            </form>
                        </div>
                    </div>
                </section>
            );
        };

        // Footer
        const Footer = () => {
            return (
                <footer className="py-12 border-t border-white/5 bg-binance-darker">
                    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="text-center mb-8">
                            <h3 className="text-2xl font-bold mb-2">Thank You for Your <span className="gradient-text">Support</span></h3>
                            <p className="text-binance-muted">Every donation helps me continue creating valuable content and projects.</p>
                        </div>

                        <div className="flex justify-center gap-4 mb-8">
                            {[
                                { icon: <Icons.Twitter />, label: 'Twitter', href: '#' },
                                { icon: <Icons.Github />, label: 'GitHub', href: '#' },
                                { icon: <Icons.Linkedin />, label: 'LinkedIn', href: '#' },
                            ].map((social, i) => (
                                <a
                                    key={i}
                                    href={social.href}
                                    className="w-12 h-12 rounded-full glass flex items-center justify-center text-binance-muted hover:text-binance-yellow hover:border-binance-yellow/30 transition-all border border-white/5"
                                    aria-label={social.label}
                                >
                                    {social.icon}
                                </a>
                            ))}
                        </div>

                        <div className="text-center text-sm text-binance-muted border-t border-white/5 pt-8">
                            <p>© {new Date().getFullYear()} Support My Work. All rights reserved.</p>
                            <p className="mt-2">Powered by <span className="text-binance-yellow">Binance Pay</span></p>
                        </div>
                    </div>
                </footer>
            );
        };

        // Main App
        const App = () => {
            useScrollReveal();

            return (
                <div className="min-h-screen bg-[#0B0E11] text-binance-text overflow-x-hidden">
                    <Navbar />
                    <Hero />
                    <DonationSection />
                    <WhyDonate />
                    <ProgressSection />
                    <FAQ />
                    <Contact />
                    <Footer />
                </div>
            );
        };

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
