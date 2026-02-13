<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jade & Benji — 19 December 2026</title>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500&family=Josefin+Sans:wght@300;400&family=Playfair+Display:ital,wght@0,400;0,500;1,400;1,500&display=swap" rel="stylesheet">
    <style>
        :root {
            /* Deep Christmas palette - pine-forward with elegant accents */
            --pine: #1B3A2D;
            --pine-mid: #254A3A;
            --pine-light: #2F5C48;
            --forest: #3A6B52;
            --bordeaux: #6B1D2A;
            --bordeaux-light: #8A2E3C;
            --bordeaux-soft: rgba(107, 29, 42, 0.12);
            --gold: #C4A265;
            --gold-light: #D4B87A;
            --gold-dim: rgba(196, 162, 101, 0.15);
            --blue-accent: #4A6B8A;
            --blue-light: #6B8DAE;
            --cream: #FAF7F0;
            --cream-warm: #F5EFE0;
            --cream-dark: #E8E0CF;
            --text-dark: #1E1E1A;
            --text-soft: #5A5A4E;
            --white: #FFFFFF;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; }

        body {
            font-family: 'Josefin Sans', sans-serif;
            font-weight: 300;
            color: var(--text-dark);
            background: var(--cream);
            overflow-x: hidden;
        }

        /* ============ NAVIGATION ============ */
        nav {
            position: fixed;
            top: 0; left: 0; right: 0;
            z-index: 100;
            padding: 1.2rem 2rem;
            display: flex;
            justify-content: center;
            gap: 2rem;
            transition: all 0.5s ease;
            background: transparent;
        }

        nav.scrolled {
            background: rgba(27, 58, 45, 0.95);
            backdrop-filter: blur(12px);
            box-shadow: 0 2px 30px rgba(0,0,0,0.15);
        }

        nav a {
            text-decoration: none;
            color: rgba(255,255,255,0.8);
            font-size: 0.7rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            transition: all 0.3s ease;
            position: relative;
        }

        nav a:hover { color: var(--gold-light); }

        nav a::after {
            content: '';
            position: absolute;
            bottom: -4px; left: 0;
            width: 0; height: 1px;
            background: var(--gold);
            transition: width 0.3s ease;
        }

        nav a:hover::after { width: 100%; }

        /* ============ HERO ============ */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            background: linear-gradient(170deg, #0F231A 0%, var(--pine) 30%, var(--pine-mid) 60%, var(--pine-light) 100%);
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            inset: 0;
            background:
                radial-gradient(ellipse at 20% 30%, rgba(196, 162, 101, 0.06) 0%, transparent 50%),
                radial-gradient(ellipse at 80% 70%, rgba(107, 29, 42, 0.06) 0%, transparent 50%),
                radial-gradient(ellipse at 50% 50%, rgba(255,255,255,0.02) 0%, transparent 60%);
        }

        /* Subtle winter botanical shapes */
        .botanical { position: absolute; opacity: 0.04; pointer-events: none; border: 1px solid var(--gold); }
        .botanical-1 {
            top: 8%; left: -2%;
            width: 300px; height: 300px;
            border-radius: 50% 0 50% 50%;
            transform: rotate(-30deg);
        }
        .botanical-2 {
            bottom: 10%; right: -3%;
            width: 250px; height: 250px;
            border-radius: 50% 50% 0 50%;
            transform: rotate(15deg);
        }
        .botanical-3 {
            top: 20%; right: 12%;
            width: 80px; height: 80px;
            border-radius: 50%;
        }
        .botanical-4 {
            bottom: 25%; left: 8%;
            width: 60px; height: 60px;
            border-radius: 50%;
            border-color: rgba(107, 29, 42, 0.3);
        }

        /* Star sparkle decorations */
        .star {
            position: absolute;
            width: 4px; height: 4px;
            background: var(--gold);
            border-radius: 50%;
            opacity: 0;
            animation: twinkle 3s ease-in-out infinite;
            pointer-events: none;
        }
        .star:nth-child(5) { top: 15%; left: 20%; animation-delay: 0s; }
        .star:nth-child(6) { top: 25%; right: 15%; animation-delay: 0.8s; }
        .star:nth-child(7) { bottom: 30%; left: 30%; animation-delay: 1.5s; }
        .star:nth-child(8) { top: 40%; right: 25%; animation-delay: 2.2s; }
        .star:nth-child(9) { bottom: 20%; right: 35%; animation-delay: 0.5s; }
        .star:nth-child(10) { top: 60%; left: 15%; animation-delay: 1.8s; }
        .star:nth-child(11) { top: 10%; left: 60%; animation-delay: 1s; }
        .star:nth-child(12) { bottom: 40%; right: 10%; animation-delay: 2.5s; }

        @keyframes twinkle {
            0%, 100% { opacity: 0; transform: scale(0.5); }
            50% { opacity: 0.6; transform: scale(1); }
        }

        .hero-content {
            position: relative;
            z-index: 2;
            animation: fadeUp 1.5s ease-out;
        }

        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .hero-date-top {
            font-weight: 300;
            font-size: 0.8rem;
            letter-spacing: 6px;
            text-transform: uppercase;
            color: var(--gold);
            margin-bottom: 2rem;
            animation: fadeUp 1.5s ease-out 0.2s both;
        }

        .hero-names {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 300;
            font-size: clamp(3.5rem, 10vw, 8rem);
            color: var(--cream);
            line-height: 1.1;
            animation: fadeUp 1.5s ease-out 0.4s both;
        }

        .hero-ampersand {
            font-family: 'Playfair Display', serif;
            font-style: italic;
            font-weight: 400;
            font-size: clamp(2rem, 5vw, 4rem);
            color: var(--gold-light);
            display: block;
            margin: 0.3rem 0;
            animation: fadeUp 1.5s ease-out 0.6s both;
        }

        .hero-tagline {
            font-weight: 300;
            font-size: 0.75rem;
            letter-spacing: 5px;
            text-transform: uppercase;
            color: rgba(250, 247, 240, 0.4);
            margin-top: 2.5rem;
            animation: fadeUp 1.5s ease-out 0.8s both;
        }

        .hero-ornament {
            margin-top: 1.5rem;
            color: var(--gold);
            opacity: 0.4;
            font-size: 1.2rem;
            letter-spacing: 12px;
            animation: fadeUp 1.5s ease-out 1s both;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 2.5rem; left: 50%;
            transform: translateX(-50%);
            animation: float 2.5s ease-in-out infinite;
            z-index: 2;
        }

        .scroll-indicator svg {
            width: 22px; height: 22px;
            stroke: var(--gold);
            opacity: 0.3;
            fill: none;
            stroke-width: 1.5;
        }

        @keyframes float {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(10px); }
        }

        /* ============ SECTION BASICS ============ */
        .section-label {
            font-weight: 300;
            font-size: 0.7rem;
            letter-spacing: 5px;
            text-transform: uppercase;
            color: var(--forest);
            margin-bottom: 0.8rem;
        }

        .section-title {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 300;
            font-size: clamp(2rem, 5vw, 3rem);
            color: var(--pine);
            margin-bottom: 1rem;
        }

        .section-subtitle {
            font-family: 'Cormorant Garamond', serif;
            font-style: italic;
            font-size: 1.05rem;
            color: var(--text-soft);
            margin-bottom: 3rem;
        }

        .divider {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1.5rem;
            padding: 0.5rem 0 2rem;
        }

        .divider-line { width: 50px; height: 1px; background: var(--gold); opacity: 0.3; }
        .divider-icon { color: var(--gold); font-size: 0.8rem; opacity: 0.5; }

        /* ============ COUNTDOWN ============ */
        .countdown-section {
            padding: 5rem 2rem;
            text-align: center;
            background: var(--white);
            position: relative;
        }

        .countdown-section::before {
            content: '';
            position: absolute;
            top: 0; left: 50%;
            transform: translateX(-50%);
            width: 1px; height: 50px;
            background: linear-gradient(to bottom, var(--pine-light), transparent);
        }

        .countdown-grid {
            display: flex;
            justify-content: center;
            gap: 2rem;
            flex-wrap: wrap;
            max-width: 700px;
            margin: 2rem auto 0;
        }

        .countdown-item { min-width: 100px; }

        .countdown-number {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 300;
            font-size: 3.8rem;
            color: var(--pine);
            line-height: 1;
        }

        .countdown-unit {
            font-weight: 300;
            font-size: 0.6rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--text-soft);
            margin-top: 0.3rem;
        }

        /* ============ EVENTS ============ */
        .events-section {
            padding: 6rem 2rem;
            background: var(--cream);
        }

        .events-section .section-label,
        .events-section .section-title,
        .events-section .section-subtitle {
            text-align: center;
        }

        .events-container { max-width: 1000px; margin: 0 auto; }

        .timeline { position: relative; padding-top: 1rem; }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%; top: 0; bottom: 0;
            width: 1px;
            background: linear-gradient(to bottom, transparent, var(--pine-light) 10%, var(--pine-light) 90%, transparent);
            opacity: 0.3;
        }

        .event-card {
            display: flex;
            align-items: flex-start;
            margin-bottom: 3rem;
            position: relative;
        }

        .event-card:nth-child(odd) { flex-direction: row; }
        .event-card:nth-child(even) { flex-direction: row-reverse; }

        .event-content {
            width: 44%;
            background: var(--white);
            padding: 2.5rem;
            border-radius: 2px;
            box-shadow: 0 4px 30px rgba(0,0,0,0.04);
            position: relative;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border-top: 2px solid var(--pine-light);
        }

        .event-content:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 40px rgba(0,0,0,0.07);
        }

        .event-card:nth-child(odd) .event-content { margin-right: auto; text-align: right; }
        .event-card:nth-child(even) .event-content { margin-left: auto; text-align: left; }

        .event-dot {
            position: absolute;
            left: 50%; top: 2.5rem;
            width: 14px; height: 14px;
            background: var(--bordeaux);
            border-radius: 50%;
            transform: translateX(-50%);
            border: 3px solid var(--cream);
            z-index: 2;
        }

        .event-day {
            font-weight: 300;
            font-size: 0.6rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: var(--bordeaux);
            margin-bottom: 0.3rem;
        }

        .event-time {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 500;
            font-size: 1.6rem;
            color: var(--pine);
            margin-bottom: 0.3rem;
        }

        .event-name {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 400;
            font-size: 1.3rem;
            color: var(--text-dark);
            margin-bottom: 0.8rem;
        }

        .event-venue {
            font-weight: 300;
            font-size: 0.75rem;
            color: var(--gold);
            letter-spacing: 2px;
            text-transform: uppercase;
            margin-bottom: 0.5rem;
        }

        .event-address {
            font-weight: 300;
            font-size: 0.85rem;
            color: var(--text-soft);
            line-height: 1.7;
        }

        .event-note {
            margin-top: 1rem;
            padding-top: 1rem;
            border-top: 1px solid var(--cream-dark);
            font-family: 'Cormorant Garamond', serif;
            font-style: italic;
            font-size: 0.95rem;
            color: var(--text-soft);
            line-height: 1.6;
        }

        .event-parking {
            margin-top: 0.8rem;
            font-size: 0.8rem;
            color: var(--blue-accent);
            display: flex;
            align-items: center;
            gap: 0.4rem;
        }

        .event-card:nth-child(odd) .event-parking { justify-content: flex-end; }
        .event-card:nth-child(even) .event-parking { justify-content: flex-start; }

        .parking-icon { font-size: 0.9rem; }

        .map-link {
            display: inline-block;
            margin-top: 0.8rem;
            font-weight: 300;
            font-size: 0.65rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: var(--pine-light);
            text-decoration: none;
            border-bottom: 1px solid var(--pine-light);
            padding-bottom: 2px;
            transition: all 0.3s ease;
        }

        .map-link:hover { color: var(--pine); border-color: var(--pine); }

        /* ============ ACCOMMODATION ============ */
        .accommodation-section {
            padding: 5rem 2rem;
            background: var(--white);
            text-align: center;
        }

        .accom-grid {
            max-width: 900px;
            margin: 2rem auto 0;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 1.5rem;
        }

        .accom-card {
            background: var(--cream);
            padding: 2rem;
            border-radius: 2px;
            text-align: left;
            transition: transform 0.3s ease;
            border-left: 3px solid var(--pine-light);
        }

        .accom-card:hover { transform: translateY(-3px); }

        .accom-card.highlight { border-left-color: var(--gold); background: linear-gradient(135deg, var(--cream), var(--gold-dim)); }

        .accom-icon { font-size: 1.3rem; margin-bottom: 0.6rem; }

        .accom-name {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 500;
            font-size: 1.15rem;
            color: var(--pine);
            margin-bottom: 0.5rem;
        }

        .accom-desc {
            font-size: 0.82rem;
            color: var(--text-soft);
            line-height: 1.7;
            margin-bottom: 0.8rem;
        }

        .accom-tag {
            display: inline-block;
            font-size: 0.6rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            padding: 0.3rem 0.8rem;
            border: 1px solid var(--pine-light);
            color: var(--pine-light);
            border-radius: 2px;
        }

        .accom-card.highlight .accom-tag { border-color: var(--gold); color: var(--gold); }

        /* ============ TRANSPORT (SEPARATE) ============ */
        .transport-section {
            padding: 4rem 2rem;
            background: var(--pine);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .transport-section::before {
            content: '';
            position: absolute;
            inset: 0;
            background:
                radial-gradient(ellipse at 30% 50%, rgba(196,162,101,0.04) 0%, transparent 50%),
                radial-gradient(ellipse at 70% 50%, rgba(74,107,138,0.04) 0%, transparent 50%);
        }

        .transport-section .section-label { color: var(--gold); opacity: 0.6; position: relative; z-index: 2; }
        .transport-section .section-title { color: var(--cream); position: relative; z-index: 2; }

        .transport-grid {
            max-width: 800px;
            margin: 2rem auto 0;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.5rem;
            position: relative;
            z-index: 2;
        }

        .transport-card {
            background: rgba(255,255,255,0.06);
            border: 1px solid rgba(255,255,255,0.08);
            padding: 1.8rem;
            border-radius: 2px;
            text-align: left;
        }

        .transport-card-icon { font-size: 1.5rem; margin-bottom: 0.8rem; }

        .transport-card-title {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 500;
            font-size: 1.1rem;
            color: var(--cream);
            margin-bottom: 0.5rem;
        }

        .transport-card-text {
            font-size: 0.82rem;
            color: rgba(250,247,240,0.55);
            line-height: 1.7;
        }

        .transport-card-text strong {
            color: var(--gold-light);
            font-weight: 400;
        }

        /* ============ FAQ ============ */
        .faq-section {
            padding: 5rem 2rem;
            background: var(--cream);
            text-align: center;
        }

        .faq-container {
            max-width: 720px;
            margin: 2rem auto 0;
            text-align: left;
        }

        .faq-item {
            border-bottom: 1px solid var(--cream-dark);
            padding: 1.5rem 0;
        }

        .faq-question {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 500;
            font-size: 1.15rem;
            color: var(--pine);
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 1rem;
            user-select: none;
            transition: color 0.3s ease;
        }

        .faq-question:hover { color: var(--bordeaux); }

        .faq-toggle {
            font-size: 1.2rem;
            color: var(--gold);
            transition: transform 0.3s ease;
            flex-shrink: 0;
        }

        .faq-item.open .faq-toggle { transform: rotate(45deg); }

        .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease, padding 0.4s ease;
            font-size: 0.88rem;
            color: var(--text-soft);
            line-height: 1.8;
        }

        .faq-item.open .faq-answer {
            max-height: 300px;
            padding-top: 1rem;
        }

        /* ============ RSVP ============ */
        .rsvp-section {
            padding: 6rem 2rem;
            background: linear-gradient(170deg, #0F231A 0%, var(--pine) 40%, var(--pine-mid) 100%);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .rsvp-section::before {
            content: '';
            position: absolute;
            inset: 0;
            background:
                radial-gradient(ellipse at 30% 80%, rgba(107,29,42,0.08) 0%, transparent 50%),
                radial-gradient(ellipse at 70% 20%, rgba(196,162,101,0.05) 0%, transparent 40%);
        }

        .rsvp-section .section-label { color: var(--gold); opacity: 0.5; position: relative; z-index: 2; }
        .rsvp-section .section-title { color: var(--cream); position: relative; z-index: 2; }

        .rsvp-subtitle {
            font-family: 'Cormorant Garamond', serif;
            font-style: italic;
            font-size: 1.1rem;
            color: rgba(250,247,240,0.5);
            margin-bottom: 2.5rem;
            position: relative;
            z-index: 2;
        }

        .rsvp-btn-container { position: relative; z-index: 2; }

        .rsvp-btn {
            display: inline-block;
            padding: 1.1rem 3.5rem;
            background: var(--bordeaux);
            color: var(--cream);
            font-family: 'Josefin Sans', sans-serif;
            font-weight: 300;
            font-size: 0.75rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            border: none;
            border-radius: 2px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .rsvp-btn:hover {
            background: var(--bordeaux-light);
            transform: translateY(-2px);
            box-shadow: 0 8px 30px rgba(107,29,42,0.3);
        }

        .rsvp-note {
            margin-top: 1.5rem;
            font-size: 0.78rem;
            color: rgba(250,247,240,0.35);
            position: relative;
            z-index: 2;
        }

        /* Decorative stars in RSVP */
        .rsvp-star {
            position: absolute;
            width: 3px; height: 3px;
            background: var(--gold);
            border-radius: 50%;
            opacity: 0;
            animation: twinkle 4s ease-in-out infinite;
            pointer-events: none;
        }
        .rsvp-star:nth-child(1) { top: 15%; left: 10%; animation-delay: 0s; }
        .rsvp-star:nth-child(2) { top: 30%; right: 15%; animation-delay: 1.2s; }
        .rsvp-star:nth-child(3) { bottom: 25%; left: 20%; animation-delay: 2.4s; }
        .rsvp-star:nth-child(4) { bottom: 15%; right: 25%; animation-delay: 0.6s; }

        /* ============ FOOTER ============ */
        footer {
            padding: 3rem 2rem;
            text-align: center;
            background: var(--pine);
        }

        .footer-names {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 300;
            font-size: 1.6rem;
            color: var(--cream);
        }

        .footer-date {
            font-weight: 300;
            font-size: 0.65rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--gold);
            opacity: 0.5;
            margin-top: 0.4rem;
        }

        .footer-heart {
            margin: 1.2rem 0 0;
            color: var(--bordeaux);
            font-size: 0.7rem;
            opacity: 0.5;
        }

        /* ============ SCROLL REVEAL ============ */
        .reveal {
            opacity: 0;
            transform: translateY(25px);
            transition: all 0.8s ease-out;
        }

        .reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* ============ RESPONSIVE ============ */
        @media (max-width: 768px) {
            nav { gap: 1rem; padding: 1rem 0.5rem; flex-wrap: wrap; }
            nav a { font-size: 0.6rem; letter-spacing: 2px; }

            .timeline::before { left: 20px; }

            .event-card,
            .event-card:nth-child(odd),
            .event-card:nth-child(even) { flex-direction: column; }

            .event-dot { left: 20px; top: 0; }

            .event-content,
            .event-card:nth-child(odd) .event-content,
            .event-card:nth-child(even) .event-content {
                width: calc(100% - 50px);
                margin-left: 50px;
                text-align: left;
            }

            .event-card:nth-child(odd) .event-parking { justify-content: flex-start; }

            .countdown-grid { gap: 1rem; }
            .countdown-item { min-width: 70px; }
            .countdown-number { font-size: 2.8rem; }

            .transport-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <!-- Navigation -->
    <nav id="nav">
        <a href="#home">Home</a>
        <a href="#countdown">Countdown</a>
        <a href="#details">Programme</a>
        <a href="#accommodation">Stay</a>
        <a href="#faq">FAQ</a>
        <a href="#rsvp">RSVP</a>
    </nav>

    <!-- Hero -->
    <section class="hero" id="home">
        <div class="botanical botanical-1"></div>
        <div class="botanical botanical-2"></div>
        <div class="botanical botanical-3"></div>
        <div class="botanical botanical-4"></div>
        <div class="star"></div>
        <div class="star"></div>
        <div class="star"></div>
        <div class="star"></div>
        <div class="star"></div>
        <div class="star"></div>
        <div class="star"></div>
        <div class="star"></div>

        <div class="hero-content">
            <p class="hero-date-top">Saturday, the Nineteenth of December</p>
            <h1 class="hero-names">Jade</h1>
            <span class="hero-ampersand">&amp;</span>
            <h1 class="hero-names">Benji</h1>
            <p class="hero-tagline">Normandy, France &nbsp;·&nbsp; Two Thousand and Twenty-Six</p>
            <div class="hero-ornament">✦ &nbsp; ✦ &nbsp; ✦</div>
        </div>

        <div class="scroll-indicator">
            <svg viewBox="0 0 24 24"><path d="M12 5v14M5 12l7 7 7-7"/></svg>
        </div>
    </section>

    <!-- Countdown -->
    <section class="countdown-section" id="countdown">
        <p class="section-label reveal">Counting Down To</p>
        <h2 class="section-title reveal">Our Winter Celebration</h2>
        <div class="divider reveal">
            <span class="divider-line"></span>
            <span class="divider-icon">✦</span>
            <span class="divider-line"></span>
        </div>
        <div class="countdown-grid reveal">
            <div class="countdown-item">
                <div class="countdown-number" id="days">---</div>
                <div class="countdown-unit">Days</div>
            </div>
            <div class="countdown-item">
                <div class="countdown-number" id="hours">--</div>
                <div class="countdown-unit">Hours</div>
            </div>
            <div class="countdown-item">
                <div class="countdown-number" id="minutes">--</div>
                <div class="countdown-unit">Minutes</div>
            </div>
            <div class="countdown-item">
                <div class="countdown-number" id="seconds">--</div>
                <div class="countdown-unit">Seconds</div>
            </div>
        </div>
    </section>

    <!-- Event Details -->
    <section class="events-section" id="details">
        <div class="events-container">
            <p class="section-label reveal">The Celebration</p>
            <h2 class="section-title reveal">Weekend Programme</h2>
            <p class="section-subtitle reveal">A winter weekend of love, laughter, and celebration in the heart of Normandy</p>

            <div class="timeline">

                <!-- Ceremony -->
                <div class="event-card reveal">
                    <div class="event-content">
                        <div class="event-day">Saturday 19 December</div>
                        <div class="event-time">2:30 PM — Arrival</div>
                        <div class="event-name">Church Ceremony at 3:00 PM</div>
                        <div class="event-venue">Collégiale Notre-Dame des Andelys</div>
                        <div class="event-address">
                            Rue Louis Pasteur<br>
                            27700 Les Andelys
                        </div>
                        <p class="event-note">A breathtaking 13th-century gothic church with stunning Renaissance stained-glass windows. Please arrive by 2:30 PM to be seated before the ceremony begins at 3:00 PM.</p>
                        <div class="event-parking">
                            <span class="parking-icon">🅿️</span>
                            Free street parking nearby. The town centre uses a blue-zone disc system (1h30 max during business hours) but no restrictions on Saturday afternoon for church visitors. Additional parking around Place Nicolas Poussin.
                        </div>
                        <a href="https://maps.google.com/?q=Collégiale+Notre-Dame+Les+Andelys" target="_blank" class="map-link">View on Map →</a>
                    </div>
                    <div class="event-dot"></div>
                </div>

                <!-- Reception -->
                <div class="event-card reveal">
                    <div class="event-content">
                        <div class="event-day">Saturday 19 December</div>
                        <div class="event-time">Evening → 5:00 AM</div>
                        <div class="event-name">Cocktails, Dinner &amp; Party</div>
                        <div class="event-venue">Manoir de Corny</div>
                        <div class="event-address">
                            3 Chemin de la Vieille Côte<br>
                            27700 Corny (Frenelles-en-Vexin)
                        </div>
                        <p class="event-note">An elegant 14th-century Normandy estate nestled among 2 hectares of parkland and forest. Dance the night away under the extraordinary timber-frame vault of the historic Grange Dîmière — the party goes until 5 AM!</p>
                        <div class="event-parking">
                            <span class="parking-icon">🅿️</span>
                            Large private car park on-site with ~250 spaces, 1 minute walk from the venue. Free for all guests.
                        </div>
                        <a href="https://maps.google.com/?q=Manoir+de+Corny+27700" target="_blank" class="map-link">View on Map →</a>
                    </div>
                    <div class="event-dot"></div>
                </div>

                <!-- Brunch -->
                <div class="event-card reveal">
                    <div class="event-content">
                        <div class="event-day">Sunday 20 December</div>
                        <div class="event-time">Late Morning</div>
                        <div class="event-name">Farewell Brunch</div>
                        <div class="event-venue">Manoir de Corny</div>
                        <div class="event-address">
                            A warm, relaxed morning together at the Petite Grange before saying goodbye.
                        </div>
                        <p class="event-note">The perfect way to close a magical weekend — coffee, croissants, and happy memories. Open to all guests, including those staying off-site.</p>
                        <div class="event-parking">
                            <span class="parking-icon">🅿️</span>
                            Same on-site parking as Saturday evening.
                        </div>
                    </div>
                    <div class="event-dot"></div>
                </div>

            </div>
        </div>
    </section>

    <!-- Accommodation -->
    <section class="accommodation-section" id="accommodation">
        <p class="section-label reveal">Where to Stay</p>
        <h2 class="section-title reveal">Accommodation</h2>
        <p class="section-subtitle reveal">Most guests will sleep on-site at the Manoir — others can find lovely options nearby</p>

        <div class="accom-grid">
            <div class="accom-card highlight reveal">
                <div class="accom-icon">🏡</div>
                <div class="accom-name">Manoir de Corny — On-Site</div>
                <p class="accom-desc">
                    The estate has ~119 beds across 43 charming rooms (twins, family suites, and a shared room). Staying on-site means no driving and maximum fun! Room assignments will be coordinated by us — more details to follow.
                </p>
                <span class="accom-tag">Priority · Included</span>
            </div>

            <div class="accom-card reveal">
                <div class="accom-icon">🏨</div>
                <div class="accom-name">La Chaîne d'Or</div>
                <p class="accom-desc">
                    Charming 3-star hotel on the banks of the Seine in Les Andelys, ~5 km away. Historic 18th-century building with 14 individually decorated rooms and a renowned restaurant.
                </p>
                <span class="accom-tag">~5 km · Charming</span>
            </div>

            <div class="accom-card reveal">
                <div class="accom-icon">🍷</div>
                <div class="accom-name">Hôtel de Paris — Les Andelys</div>
                <p class="accom-desc">
                    Comfortable hotel right in the town centre with bistronomy restaurant, garden, and terrace. Great value and very practical.
                </p>
                <span class="accom-tag">~5 km · Budget-friendly</span>
            </div>

            <div class="accom-card reveal">
                <div class="accom-icon">✨</div>
                <div class="accom-name">Moulin de Connelles</div>
                <p class="accom-desc">
                    For something extra special — a romantic half-timbered manor on a private island in the Seine. About 15 km from the venue.
                </p>
                <span class="accom-tag">~15 km · Luxury</span>
            </div>

            <div class="accom-card reveal">
                <div class="accom-icon">🏠</div>
                <div class="accom-name">Gîtes & B&Bs Nearby</div>
                <p class="accom-desc">
                    Several charming chambres d'hôtes and holiday rentals in and around Les Andelys and the Vexin. Perfect for families needing extra space. Check Booking.com or Airbnb.
                </p>
                <span class="accom-tag">Various · Family-friendly</span>
            </div>
        </div>
    </section>

    <!-- Transport (Separate section) -->
    <section class="transport-section reveal">
        <p class="section-label">Getting There</p>
        <h2 class="section-title">Travel Information</h2>

        <div class="transport-grid">
            <div class="transport-card">
                <div class="transport-card-icon">🚗</div>
                <div class="transport-card-title">By Car from Paris</div>
                <p class="transport-card-text">
                    <strong>~1h15</strong> via A13 (exit 17 Gaillon → Les Andelys) or via A15/RN14 through Cergy-Pontoise. From Rouen: <strong>~45 min</strong> via D6014.
                </p>
            </div>

            <div class="transport-card">
                <div class="transport-card-icon">🚆</div>
                <div class="transport-card-title">By Train</div>
                <p class="transport-card-text">
                    Nearest station: <strong>Gaillon-Aubevoye</strong> (~20 km), served from Paris Gare Saint-Lazare. We can help organise shuttles from the station — just let us know!
                </p>
            </div>

            <div class="transport-card">
                <div class="transport-card-icon">🚐</div>
                <div class="transport-card-title">Shuttles & Carpools</div>
                <p class="transport-card-text">
                    We're organising <strong>shuttle transfers</strong> between the church and the Manoir. Need a ride from Paris or the station? Let us know in your RSVP and we'll coordinate carpools.
                </p>
            </div>
        </div>
    </section>

    <!-- FAQ -->
    <section class="faq-section" id="faq">
        <p class="section-label reveal">Questions?</p>
        <h2 class="section-title reveal">Frequently Asked Questions</h2>
        <div class="divider reveal">
            <span class="divider-line"></span>
            <span class="divider-icon">✦</span>
            <span class="divider-line"></span>
        </div>

        <div class="faq-container">
            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    What is the dress code?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    Cocktail / semi-formal attire. It's a winter wedding, so think elegant and warm — cosy layers are encouraged! The Grange Dîmière has a magnificent working fireplace but do bring a shawl or jacket. Avoid white and off-white, of course.
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    Can I bring my children?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    Children are very welcome! The Manoir offers a dedicated children's play area and babysitting can be arranged on-site so you can enjoy the evening worry-free. Please mention the number and ages of children in your RSVP.
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    Where do I park at the church?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    There is free street parking around the Collégiale Notre-Dame, including along Rue Louis Pasteur and nearby Place Nicolas Poussin. The town uses a blue-zone disc system during business hours (9h–12h, 14h–19h) but Saturday afternoon parking for church visitors is generally no issue. Arrive a bit early to find a spot nearby.
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    Where do I park at the Manoir de Corny?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    The Manoir has a large private car park with around 250 spaces, just a 1-minute walk from the venue. Parking is free for all guests and available all weekend. If you're staying on-site, your car can stay parked overnight.
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    How do I get from the church to the Manoir?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    The Manoir de Corny is about 5 km from the church (~10 minutes by car). We're planning shuttle transfers between the two venues, so you won't need to worry about driving. Details will follow closer to the date.
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    What time does the party end?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    The party goes until <strong>5:00 AM</strong>! Since most guests will be sleeping on-site, there's no reason to stop early. Dance the night away and stumble to your room when you're ready.
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    I have dietary requirements — what should I do?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    Please mention any allergies, dietary restrictions, or preferences in your RSVP. The caterer is very experienced and will accommodate all needs — just let us know!
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    Is the brunch on Sunday open to everyone?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    Yes! The Sunday brunch is for all guests — whether you stayed on-site or nearby. It's a relaxed, casual affair in the Petite Grange. No set time, just come when you're up!
                </div>
            </div>

            <div class="faq-item reveal">
                <div class="faq-question" onclick="toggleFaq(this)">
                    When should I RSVP by?
                    <span class="faq-toggle">+</span>
                </div>
                <div class="faq-answer">
                    Please RSVP as early as possible, ideally by <strong>September 2026</strong>, so we can finalise room assignments, catering, and transport. The sooner the better!
                </div>
            </div>
        </div>
    </section>

    <!-- RSVP -->
    <section class="rsvp-section" id="rsvp">
        <div class="rsvp-star"></div>
        <div class="rsvp-star"></div>
        <div class="rsvp-star"></div>
        <div class="rsvp-star"></div>

        <p class="section-label reveal">Will You Join Us?</p>
        <h2 class="section-title reveal">Répondez, s'il vous plaît</h2>
        <p class="rsvp-subtitle reveal">We would be delighted to celebrate this winter evening with you</p>

        <div class="rsvp-btn-container reveal">
            <!-- REPLACE THE URL BELOW WITH YOUR GOOGLE FORMS LINK -->
            <a href="YOUR_GOOGLE_FORMS_LINK_HERE" target="_blank" class="rsvp-btn">
                Open RSVP Form
            </a>
        </div>

        <p class="rsvp-note reveal">You'll be redirected to our Google Form to confirm your attendance</p>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-names">Jade &amp; Benji</div>
        <div class="footer-date">19 · 12 · 2026 &nbsp;·&nbsp; Normandy</div>
        <div class="footer-heart">♥</div>
    </footer>

    <script>
        // ===== COUNTDOWN =====
        function updateCountdown() {
            const wedding = new Date('2026-12-19T15:00:00+01:00');
            const now = new Date();
            const diff = wedding - now;

            if (diff <= 0) {
                document.getElementById('days').textContent = '0';
                document.getElementById('hours').textContent = '0';
                document.getElementById('minutes').textContent = '0';
                document.getElementById('seconds').textContent = '0';
                return;
            }

            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);

            document.getElementById('days').textContent = days;
            document.getElementById('hours').textContent = String(hours).padStart(2, '0');
            document.getElementById('minutes').textContent = String(minutes).padStart(2, '0');
            document.getElementById('seconds').textContent = String(seconds).padStart(2, '0');
        }

        updateCountdown();
        setInterval(updateCountdown, 1000);

        // ===== NAV =====
        const nav = document.getElementById('nav');
        window.addEventListener('scroll', () => {
            nav.classList.toggle('scrolled', window.scrollY > 80);
        });

        // ===== SCROLL REVEAL =====
        const reveals = document.querySelectorAll('.reveal');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) entry.target.classList.add('visible');
            });
        }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });

        reveals.forEach(el => observer.observe(el));

        // ===== FAQ TOGGLE =====
        function toggleFaq(el) {
            const item = el.parentElement;
            // Close others
            document.querySelectorAll('.faq-item.open').forEach(i => {
                if (i !== item) i.classList.remove('open');
            });
            item.classList.toggle('open');
        }

        // ===== SMOOTH SCROLL =====
        document.querySelectorAll('nav a').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) target.scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>
</body>
</html>
