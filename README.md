<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Veré Studio — Curated for the woman you're becoming.</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --ivory: #FAF8F5;
            --warm-cream: #F5F0E8;
            --chocolate: #3D2B1F;
            --charcoal: #2C2C2C;
            --black: #1A1A1A;
            --forest-green: #2D4A3E;
            --burgundy: #6B2737;
            --sage: #8A9A7B;
            --camel: #C4A77D;
            --gold: #C9A96E;
            --soft-brown: #5C4033;
            --text-muted: #8A8A8A;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--ivory);
            color: var(--charcoal);
            overflow-x: hidden;
            line-height: 1.7;
        }

        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: var(--warm-cream); }
        ::-webkit-scrollbar-thumb { background: var(--camel); border-radius: 3px; }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes gentlePulse { 0%, 100% { opacity: 0.6; } 50% { opacity: 1; } }

        .animate-on-scroll {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.9s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .animate-on-scroll.visible { opacity: 1; transform: translateY(0); }
        .delay-1 { transition-delay: 0.1s; }
        .delay-2 { transition-delay: 0.2s; }
        .delay-3 { transition-delay: 0.3s; }
        .delay-4 { transition-delay: 0.4s; }

        /* Navigation */
        nav {
            position: fixed;
            top: 0; left: 0; right: 0;
            z-index: 1000;
            padding: 24px 48px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.5s ease;
            background: transparent;
        }
        nav.scrolled {
            background: rgba(250, 248, 245, 0.95);
            backdrop-filter: blur(20px);
            padding: 16px 48px;
            box-shadow: 0 1px 20px rgba(0,0,0,0.05);
        }
        .nav-logo {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.5rem;
            font-weight: 400;
            letter-spacing: 3px;
            color: var(--ivory);
            text-decoration: none;
            transition: color 0.3s;
        }
        nav.scrolled .nav-logo { color: var(--chocolate); }
        .nav-links {
            display: flex;
            gap: 40px;
            list-style: none;
        }
        .nav-links a {
            font-family: 'Inter', sans-serif;
            font-size: 0.75rem;
            font-weight: 400;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--ivory);
            text-decoration: none;
            position: relative;
            transition: color 0.3s;
        }
        nav.scrolled .nav-links a { color: var(--charcoal); }
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -4px; left: 0;
            width: 0; height: 1px;
            background: var(--gold);
            transition: width 0.4s ease;
        }
        .nav-links a:hover::after { width: 100%; }
        .nav-links a:hover { color: var(--gold); }

        /* Hero */
        .hero {
            height: 100vh;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            background: linear-gradient(135deg, var(--chocolate) 0%, var(--soft-brown) 50%, var(--charcoal) 100%);
        }
        .hero-bg {
            position: absolute;
            inset: 0;
            background:
                radial-gradient(ellipse at 20% 50%, rgba(201, 169, 110, 0.15) 0%, transparent 50%),
                radial-gradient(ellipse at 80% 20%, rgba(139, 90, 43, 0.1) 0%, transparent 50%);
        }
        .hero-content {
            position: relative;
            z-index: 2;
            text-align: center;
            color: var(--ivory);
            max-width: 900px;
            padding: 0 24px;
        }
        .hero-eyebrow {
            font-family: 'Inter', sans-serif;
            font-size: 0.7rem;
            font-weight: 400;
            letter-spacing: 5px;
            text-transform: uppercase;
            color: var(--gold);
            margin-bottom: 32px;
            animation: fadeInUp 1s ease 0.3s both;
        }
        .hero-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(3rem, 8vw, 6.5rem);
            font-weight: 300;
            letter-spacing: 8px;
            margin-bottom: 24px;
            animation: fadeInUp 1.2s ease 0.5s both;
        }
        .hero-title span { font-style: italic; font-weight: 400; color: var(--gold); }
        .hero-tagline {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(1.1rem, 2.5vw, 1.6rem);
            font-weight: 300;
            font-style: italic;
            letter-spacing: 1px;
            margin-bottom: 48px;
            color: rgba(250, 248, 245, 0.85);
            animation: fadeInUp 1s ease 0.8s both;
        }
        .hero-divider {
            width: 60px; height: 1px;
            background: var(--gold);
            margin: 0 auto 48px;
            animation: fadeIn 1.5s ease 1s both;
        }
        .hero-cta {
            display: inline-flex;
            align-items: center;
            gap: 12px;
            padding: 16px 40px;
            border: 1px solid rgba(250, 248, 245, 0.4);
            color: var(--ivory);
            text-decoration: none;
            font-size: 0.75rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            transition: all 0.4s ease;
            animation: fadeInUp 1s ease 1.2s both;
        }
        .hero-cta:hover {
            background: var(--ivory);
            color: var(--chocolate);
            border-color: var(--ivory);
        }
        .scroll-indicator {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            animation: fadeIn 2s ease 2s both;
        }
        .scroll-indicator span {
            font-size: 0.6rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: rgba(250, 248, 245, 0.5);
        }
        .scroll-line {
            width: 1px; height: 40px;
            background: linear-gradient(to bottom, var(--gold), transparent);
            animation: gentlePulse 2s infinite;
        }

        /* Sections */
        section { padding: 120px 48px; position: relative; }
        .section-header { text-align: center; margin-bottom: 80px; }
        .section-eyebrow {
            font-family: 'Inter', sans-serif;
            font-size: 0.65rem;
            font-weight: 400;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--gold);
            margin-bottom: 20px;
        }
        .section-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(2rem, 4vw, 3.5rem);
            font-weight: 300;
            color: var(--chocolate);
            letter-spacing: 2px;
        }
        .section-title em { font-style: italic; color: var(--soft-brown); }

        /* Brand Story */
        .brand-story { background: var(--warm-cream); }
        .story-grid {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 80px;
            align-items: center;
        }
        .story-text { padding-right: 40px; }
        .story-text p {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.15rem;
            font-weight: 300;
            line-height: 2;
            color: var(--soft-brown);
            margin-bottom: 24px;
        }
        .story-text .lead {
            font-size: 1.4rem;
            font-weight: 400;
            color: var(--chocolate);
            line-height: 1.8;
        }
        .story-image {
            position: relative;
            overflow: hidden;
        }
        .story-image img {
            width: 100%;
            height: 600px;
            object-fit: cover;
            transition: transform 0.8s ease;
        }
        .story-image:hover img { transform: scale(1.03); }
        .story-image::after {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(61, 43, 31, 0.2), transparent);
            pointer-events: none;
        }

        /* Philosophy */
        .philosophy { background: var(--ivory); }
        .philosophy-grid {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 48px;
        }
        .philosophy-card {
            text-align: center;
            padding: 48px 32px;
            border: 1px solid rgba(61, 43, 31, 0.08);
            transition: all 0.5s ease;
            position: relative;
            overflow: hidden;
        }
        .philosophy-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 2px;
            background: var(--gold);
            transform: scaleX(0);
            transition: transform 0.5s ease;
        }
        .philosophy-card:hover::before { transform: scaleX(1); }
        .philosophy-card:hover {
            border-color: rgba(61, 43, 31, 0.15);
            transform: translateY(-4px);
            box-shadow: 0 20px 60px rgba(61, 43, 31, 0.06);
        }
        .philosophy-card .card-number {
            font-family: 'Cormorant Garamond', serif;
            font-size: 0.9rem;
            font-weight: 300;
            color: var(--gold);
            letter-spacing: 2px;
            margin-bottom: 24px;
        }
        .philosophy-card h3 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.6rem;
            font-weight: 400;
            color: var(--chocolate);
            margin-bottom: 20px;
            letter-spacing: 1px;
        }
        .philosophy-card p {
            font-size: 0.9rem;
            color: var(--text-muted);
            line-height: 1.8;
            font-weight: 300;
        }

        /* Style Blend */
        .style-blend {
            background: var(--chocolate);
            color: var(--ivory);
            padding: 140px 48px;
        }
        .style-blend .section-title { color: var(--ivory); }
        .style-blend .section-eyebrow { color: var(--gold); }
        .blend-container { max-width: 1200px; margin: 0 auto; }
        .blend-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 2px;
            margin-top: 60px;
        }
        .blend-item {
            padding: 48px 32px;
            text-align: center;
            background: rgba(250, 248, 245, 0.03);
            border: 1px solid rgba(250, 248, 245, 0.06);
            transition: all 0.5s ease;
            cursor: default;
        }
        .blend-item:hover {
            background: rgba(250, 248, 245, 0.08);
            transform: translateY(-4px);
        }
        .blend-item h4 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.3rem;
            font-weight: 400;
            margin-bottom: 12px;
            letter-spacing: 1px;
        }
        .blend-item p {
            font-size: 0.8rem;
            color: rgba(250, 248, 245, 0.5);
            font-weight: 300;
            line-height: 1.7;
        }

        /* Color Palette */
        .color-palette { background: var(--ivory); padding: 120px 48px; }
        .palette-container { max-width: 1000px; margin: 0 auto; }
        .palette-row {
            display: flex;
            gap: 16px;
            margin-bottom: 16px;
            justify-content: center;
            flex-wrap: wrap;
        }
        .color-swatch {
            width: 140px; height: 180px;
            border-radius: 2px;
            position: relative;
            overflow: hidden;
            cursor: pointer;
            transition: all 0.5s ease;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }
        .color-swatch:hover {
            transform: translateY(-8px) scale(1.05);
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        }
        .color-swatch .swatch-info {
            position: absolute;
            bottom: 0; left: 0; right: 0;
            padding: 16px;
            background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);
            color: white;
            transform: translateY(100%);
            transition: transform 0.4s ease;
        }
        .color-swatch:hover .swatch-info { transform: translateY(0); }
        .color-swatch .swatch-name {
            font-family: 'Cormorant Garamond', serif;
            font-size: 0.95rem;
            font-weight: 400;
            letter-spacing: 1px;
        }
        .color-swatch .swatch-hex {
            font-size: 0.65rem;
            opacity: 0.7;
            letter-spacing: 1px;
            margin-top: 4px;
        }
        .swatch-ivory { background: var(--ivory); border: 1px solid rgba(0,0,0,0.1); }
        .swatch-ivory .swatch-info { color: var(--chocolate); background: linear-gradient(to top, rgba(250,248,245,0.9), transparent); }
        .swatch-cream { background: var(--warm-cream); }
        .swatch-cream .swatch-info { color: var(--chocolate); background: linear-gradient(to top, rgba(245,240,232,0.9), transparent); }
        .swatch-chocolate { background: var(--chocolate); }
        .swatch-charcoal { background: var(--charcoal); }
        .swatch-black { background: var(--black); }
        .swatch-forest { background: var(--forest-green); }
        .swatch-burgundy { background: var(--burgundy); }
        .swatch-sage { background: var(--sage); }
        .swatch-camel { background: var(--camel); }
        .swatch-gold { background: var(--gold); }
        .swatch-gold .swatch-info { color: var(--chocolate); background: linear-gradient(to top, rgba(201,169,110,0.9), transparent); }
        .palette-label {
            text-align: center;
            margin: 48px 0 24px;
            font-family: 'Inter', sans-serif;
            font-size: 0.65rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--gold);
        }

        /* Lookbook V2 — Even Card Grid */
        .lookbook { background: var(--warm-cream); padding: 120px 48px; }
        .lookbook-grid-v2 {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 24px;
        }
        .lookbook-card {
            background: var(--ivory);
            border-radius: 2px;
            overflow: hidden;
            box-shadow: 0 4px 20px rgba(61, 43, 31, 0.06);
            transition: all 0.5s ease;
            cursor: pointer;
        }
        .lookbook-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 50px rgba(61, 43, 31, 0.12);
        }
        .lookbook-card .card-image {
            width: 100%;
            aspect-ratio: 3/4;
            overflow: hidden;
            position: relative;
        }
        .lookbook-card .card-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.8s ease;
        }
        .lookbook-card:hover .card-image img {
            transform: scale(1.05);
        }
        .lookbook-card .card-info {
            padding: 20px 24px 24px;
            text-align: center;
        }
        .lookbook-card .card-info h4 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.2rem;
            font-weight: 400;
            color: var(--chocolate);
            letter-spacing: 1px;
            margin-bottom: 6px;
        }
        .lookbook-card .card-info span {
            font-size: 0.65rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--gold);
        }

        /* Audience */
        .audience { background: var(--ivory); padding: 120px 48px; }
        .audience-grid {
            max-width: 1100px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 48px;
        }
        .audience-card {
            padding: 48px;
            border: 1px solid rgba(61, 43, 31, 0.08);
            transition: all 0.5s ease;
            position: relative;
        }
        .audience-card:hover {
            border-color: rgba(61, 43, 31, 0.2);
            background: var(--warm-cream);
        }
        .audience-card .card-icon {
            font-size: 1.5rem;
            margin-bottom: 24px;
            opacity: 0.6;
        }
        .audience-card h4 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.4rem;
            font-weight: 400;
            color: var(--chocolate);
            margin-bottom: 16px;
            letter-spacing: 1px;
        }
        .audience-card p {
            font-size: 0.9rem;
            color: var(--text-muted);
            line-height: 1.8;
            font-weight: 300;
        }

        /* Values */
        .values {
            background: var(--chocolate);
            color: var(--ivory);
            padding: 140px 48px;
            text-align: center;
        }
        .values .section-title { color: var(--ivory); }
        .values .section-eyebrow { color: var(--gold); }
        .values-grid {
            max-width: 900px;
            margin: 60px auto 0;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 16px;
        }
        .value-tag {
            padding: 14px 32px;
            border: 1px solid rgba(250, 248, 245, 0.15);
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.1rem;
            font-weight: 300;
            letter-spacing: 2px;
            transition: all 0.4s ease;
            cursor: default;
        }
        .value-tag:hover {
            background: var(--ivory);
            color: var(--chocolate);
            border-color: var(--ivory);
        }

        /* Mood */
        .mood {
            background: var(--warm-cream);
            padding: 0;
            display: grid;
            grid-template-columns: 1fr 1fr;
            min-height: 600px;
        }
        .mood-image {
            position: relative;
            overflow: hidden;
        }
        .mood-image img {
            width: 100%; height: 100%;
            object-fit: cover;
            transition: transform 1s ease;
        }
        .mood-image:hover img { transform: scale(1.03); }
        .mood-content {
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 80px 64px;
        }
      
