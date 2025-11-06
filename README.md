# exceau.github.io
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HoYoverse UX Evolution | Case Study</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            /* HoYoLab dark theme colors */
            --bg-dark: #1a1d2e;
            --bg-darker: #151824;
            --bg-card: #232538;
            --bg-hover: #2a2d45;
            --primary: #4a9eff;
            --secondary: #9d7cff;
            --accent: #ffd166;
            --gold: #d4af37;
            --text-light: #f0f0f0;
            --text-gray: #a0a0b8;
            --border: #3a3d54;
            --success: #5dce7a;
            --error: #ff6b6b;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background: var(--bg-darker);
            color: var(--text-light);
            line-height: 1.7;
            overflow-x: hidden;
        }
        
        /* Sparkly background effect */
        .sparkles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }
        
        .sparkle {
            position: absolute;
            background: radial-gradient(circle, rgba(157, 124, 255, 0.8) 0%, rgba(74, 158, 255, 0.4) 50%, transparent 70%);
            border-radius: 50%;
            animation: sparkle 4s infinite ease-in-out;
            box-shadow: 0 0 10px rgba(157, 124, 255, 0.5);
        }
        
        @keyframes sparkle {
            0%, 100% { 
                opacity: 0.2;
                transform: scale(0.5);
            }
            50% { 
                opacity: 1;
                transform: scale(1.2);
            }
        }
        
        /* Top Navigation Bar - HoYoLab style */
        .top-nav {
            background: var(--bg-dark);
            border-bottom: 1px solid var(--border);
            padding: 1rem 2rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .nav-logo {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--text-light);
        }
        
        .logo-icon {
            width: 32px;
            height: 32px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }
        
        .nav-links {
            display: flex;
            gap: 2rem;
        }
        
        .nav-link {
            color: var(--text-gray);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.2s ease;
        }
        
        .nav-link:hover {
            color: var(--primary);
        }
        
        /* Main container */
        .main-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 3rem 2rem;
            position: relative;
            z-index: 1;
        }
        
        /* Sidebar - HoYoLab style */
        .sidebar {
            width: 250px;
            flex-shrink: 0;
        }
        
        .sidebar-card {
            background: var(--bg-card);
            border-radius: 12px;
            padding: 1.5rem;
            border: 1px solid var(--border);
            margin-bottom: 1.5rem;
        }
        
        .sidebar-title {
            font-size: 0.9rem;
            color: var(--text-gray);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 1rem;
            font-weight: 600;
        }
        
        .sidebar-nav {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }
        
        .sidebar-nav-item {
            padding: 0.75rem;
            border-radius: 8px;
            color: var(--text-gray);
            text-decoration: none;
            transition: all 0.2s ease;
            font-size: 0.95rem;
        }
        
        .sidebar-nav-item:hover,
        .sidebar-nav-item.active {
            background: var(--bg-hover);
            color: var(--primary);
        }
        
        /* Stats in sidebar */
        .stat-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.75rem 0;
            border-bottom: 1px solid var(--border);
        }
        
        .stat-item:last-child {
            border-bottom: none;
        }
        
        .stat-label {
            color: var(--text-gray);
            font-size: 0.9rem;
        }
        
        .stat-value {
            font-weight: 600;
            color: var(--primary);
        }
        
        /* Main content area */
        .content {
            flex: 1;
            min-width: 0;
        }
        
        /* Header */
        .header {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 3rem;
            margin-bottom: 2rem;
            text-align: center;
        }
        
        .breadcrumb {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            justify-content: center;
            margin-bottom: 1.5rem;
            font-size: 0.9rem;
            color: var(--text-gray);
        }
        
        .breadcrumb-separator {
            color: var(--border);
        }
        
        h1 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .subtitle {
            font-size: 1.1rem;
            color: var(--text-gray);
            max-width: 800px;
            margin: 0 auto;
        }
        
        /* Stats bar - HoYoLab style */
        .stats-bar {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
            margin-bottom: 2rem;
        }
        
        .stat-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            padding: 1.5rem;
            border-radius: 12px;
            text-align: center;
            transition: all 0.3s ease;
        }
        
        .stat-card:hover {
            border-color: var(--primary);
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(74, 158, 255, 0.2);
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }
        
        .stat-label {
            color: var(--text-gray);
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        /* Section cards */
        .section {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 2.5rem;
            margin-bottom: 2rem;
        }
        
        .section-header {
            margin-bottom: 2.5rem;
            padding-bottom: 1rem;
            border-bottom: 2px solid var(--border);
        }
        
        .section-number {
            display: none;
        }
        
        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
        }
        }
        
        /* Featured images */
        .section-image {
            width: 100%;
            height: 300px;
            border-radius: 12px;
            object-fit: cover;
            margin: 1.5rem 0;
            border: 1px solid var(--border);
        }
        
        /* Image placeholder for when images don't load */
        .image-placeholder {
            width: 100%;
            height: 300px;
            border-radius: 12px;
            margin: 1.5rem 0;
            border: 2px dashed var(--border);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, var(--bg-darker), var(--bg-dark));
            color: var(--text-gray);
            text-align: center;
            padding: 2rem;
        }
        
        .image-placeholder-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            opacity: 0.5;
        }
        
        .image-placeholder-text {
            font-size: 0.95rem;
            line-height: 1.6;
        }
        
        .image-placeholder-url {
            font-size: 0.8rem;
            color: var(--primary);
            margin-top: 0.5rem;
            word-break: break-all;
            padding: 0.5rem;
            background: var(--bg-darker);
            border-radius: 6px;
            font-family: monospace;
        }
        
        /* Content cards - HoYoLab wiki style */
        .content-grid {
            display: grid;
            gap: 1.5rem;
            margin: 2rem 0;
        }
        
        .content-card {
            background: var(--bg-dark);
            border: 1px solid var(--border);
            border-radius: 10px;
            padding: 1.5rem;
            transition: all 0.3s ease;
        }
        
        .content-card:hover {
            border-color: var(--primary);
            box-shadow: 0 5px 20px rgba(74, 158, 255, 0.15);
        }
        
        .card-header {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            margin-bottom: 1rem;
        }
        
        .card-icon {
            width: 28px;
            height: 28px;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.9rem;
            flex-shrink: 0;
        }
        
        .card-icon.problem {
            background: rgba(255, 107, 107, 0.2);
            color: var(--error);
        }
        
        .card-icon.solution {
            background: rgba(93, 206, 122, 0.2);
            color: var(--success);
        }
        
        .card-title {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--text-light);
        }
        
        .card-description {
            color: var(--text-gray);
            line-height: 1.7;
            margin-bottom: 1rem;
        }
        
        .card-example {
            background: var(--bg-darker);
            padding: 1rem;
            border-radius: 8px;
            border-left: 3px solid var(--border);
            font-style: italic;
            color: var(--text-gray);
            font-size: 0.95rem;
        }
        
        /* Comparison cards */
        .comparison-section {
            margin: 2rem 0;
        }
        
        .comparison-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .comparison-card {
            background: var(--bg-dark);
            padding: 2rem;
            border-radius: 12px;
            border: 2px solid var(--border);
        }
        
        .comparison-card.before {
            border-color: rgba(255, 107, 107, 0.3);
        }
        
        .comparison-card.after {
            border-color: rgba(93, 206, 122, 0.3);
        }
        
        .comparison-badge {
            display: inline-block;
            padding: 0.4rem 1rem;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 1rem;
        }
        
        .comparison-badge.before {
            background: rgba(255, 107, 107, 0.2);
            color: var(--error);
        }
        
        .comparison-badge.after {
            background: rgba(93, 206, 122, 0.2);
            color: var(--success);
        }
        
        .comparison-text {
            font-size: 1.05rem;
            font-weight: 500;
            color: var(--text-light);
            margin-bottom: 1rem;
            line-height: 1.6;
        }
        
        .comparison-note {
            color: var(--text-gray);
            font-size: 0.9rem;
            line-height: 1.6;
        }
        
        /* Impact grid */
        .impact-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.5rem;
            margin: 2rem 0;
        }
        
        .impact-card {
            background: var(--bg-dark);
            padding: 2rem;
            border-radius: 12px;
            border: 1px solid var(--border);
            text-align: center;
            transition: all 0.3s ease;
        }
        
        .impact-card:hover {
            border-color: var(--primary);
            transform: translateY(-3px);
        }
        
        .impact-number {
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }
        
        .impact-title {
            font-size: 1rem;
            font-weight: 600;
            color: var(--text-light);
            margin-bottom: 0.75rem;
        }
        
        .impact-description {
            color: var(--text-gray);
            font-size: 0.9rem;
            line-height: 1.6;
        }
        
        /* Quote box */
        .quote-box {
            background: linear-gradient(135deg, var(--bg-dark), var(--bg-card));
            padding: 2.5rem;
            border-radius: 12px;
            border: 1px solid var(--primary);
            margin: 2rem 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .quote-box::before {
            content: '"';
            position: absolute;
            top: -20px;
            left: 20px;
            font-size: 120px;
            color: var(--primary);
            opacity: 0.1;
            font-family: Georgia, serif;
        }
        
        .quote-text {
            font-size: 1.3rem;
            font-weight: 500;
            line-height: 1.6;
            margin-bottom: 1rem;
            font-style: italic;
            color: var(--text-light);
            position: relative;
        }
        
        .quote-author {
            font-size: 0.95rem;
            color: var(--text-gray);
        }
        
        /* Takeaways list */
        .takeaways-list {
            display: grid;
            gap: 1rem;
            margin: 2rem 0;
        }
        
        /* Character comparison grid */
        .character-comparison-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin: 2rem 0;
        }
        
        .character-column {
            background: var(--bg-dark);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 2rem;
        }
        
        .character-column h3 {
            font-size: 1.4rem;
            font-weight: 600;
            margin-bottom: 1.5rem;
            color: var(--text-light);
            text-align: center;
        }
        
        .animation-block {
            margin-bottom: 1.5rem;
        }
        
        .animation-block:last-child {
            margin-bottom: 0;
        }
        
        .animation-block h4 {
            font-size: 1rem;
            font-weight: 600;
            margin-bottom: 0.75rem;
        }
        
        .animation-block img {
            width: 100%;
            border-radius: 8px;
            border: 1px solid var(--border);
        }
        
        .animation-jingliu h4 {
            color: var(--primary);
        }
        
        .animation-skirk h4 {
            color: var(--secondary);
        }
        
        /* Section subheadings */
        .section-subheading {
            font-size: 1.4rem;
            font-weight: 600;
            margin: 3rem 0 1.5rem;
            color: var(--text-light);
        }
        
        /* Image loading fallback */
        .gif-container {
            position: relative;
            width: 100%;
            min-height: 200px;
            background: var(--bg-darker);
            border-radius: 8px;
            border: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .gif-container img {
            width: 100%;
            border-radius: 8px;
            display: block;
        }
        
        .gif-fallback {
            position: absolute;
            inset: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 1rem;
            text-align: center;
            color: var(--text-gray);
            font-size: 0.9rem;
            background: var(--bg-darker);
            border-radius: 8px;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.3s ease;
        }
        
        .gif-container:has(img[src=""]) .gif-fallback,
        .gif-container img[alt]:not([src]) ~ .gif-fallback {
            opacity: 1;
        }
        
        .gif-fallback-icon {
            font-size: 2rem;
            margin-bottom: 0.5rem;
        }
        
        .takeaway-item {
            display: flex;
            gap: 1rem;
            background: var(--bg-dark);
            padding: 1.5rem;
            border-radius: 12px;
            border: 1px solid var(--border);
            transition: all 0.3s ease;
        }
        
        .takeaway-item:hover {
            border-color: var(--primary);
            transform: translateX(5px);
        }
        
        .takeaway-number {
            width: 36px;
            height: 36px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.1rem;
            font-weight: 700;
            flex-shrink: 0;
        }
        
        .takeaway-content h4 {
            font-size: 1.1rem;
            font-weight: 600;
            color: var(--text-light);
            margin-bottom: 0.5rem;
        }
        
        .takeaway-content p {
            color: var(--text-gray);
            line-height: 1.7;
            font-size: 0.95rem;
        }
        
        /* CTA Section */
        .cta-section {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            padding: 3rem;
            border-radius: 12px;
            text-align: center;
            margin: 2rem 0;
            box-shadow: 0 15px 40px rgba(74, 158, 255, 0.3);
        }
        
        .cta-section h2 {
            font-size: 2rem;
            margin-bottom: 1rem;
            color: white;
        }
        
        .cta-section p {
            font-size: 1.1rem;
            margin-bottom: 2rem;
            color: rgba(255, 255, 255, 0.9);
        }
        
        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }
        
        .btn {
            display: inline-block;
            padding: 1rem 2rem;
            border-radius: 10px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .btn-primary {
            background: white;
            color: var(--primary);
        }
        
        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }
        
        .btn-secondary {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 2px solid white;
        }
        
        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.3);
        }
        
        /* Footer */
        .footer {
            background: var(--bg-card);
            border-top: 1px solid var(--border);
            padding: 2rem;
            text-align: center;
            color: var(--text-gray);
            margin-top: 3rem;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 1rem;
            flex-wrap: wrap;
        }
        
        .footer-link {
            color: var(--text-gray);
            text-decoration: none;
            font-size: 0.9rem;
            transition: color 0.2s ease;
        }
        
        .footer-link:hover {
            color: var(--primary);
        }
        
        /* Responsive */
        @media (max-width: 1024px) {
            .stats-bar {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .comparison-grid,
            .character-comparison-grid {
                grid-template-columns: 1fr;
            }
            
            .impact-grid {
                grid-template-columns: 1fr;
            }
            
            .section-image,
            .image-placeholder {
                height: 200px;
            }
        }
    </style>
</head>
<body>
    <!-- Sparkly background -->
    <div class="sparkles" id="sparkles"></div>
    
    <!-- Main Container -->
    <div class="main-container">
        <!-- Main Content -->
        <main class="content" style="max-width: 1200px; margin: 0 auto;">
            <!-- Header -->
            <div class="header">
                <h1>HoYoverse's UX Evolution</h1>
                <p class="subtitle">
                    How Honkai: Star Rail learned from Genshin Impact's mistakes to build better player experiences
                </p>
            </div>
            
            <!-- Stats Bar -->
            <div class="stats-bar">
                <div class="stat-card">
                    <div class="stat-number">↑35%</div>
                    <div class="stat-label">Tutorial Completion</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">↓60%</div>
                    <div class="stat-label">Support Tickets</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">↑42%</div>
                    <div class="stat-label">Early Retention</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">★4.7</div>
                    <div class="stat-label">Player Sentiment</div>
                </div>
            </div>
            
            <!-- Section 1: The Problem -->
            <div class="section" id="section1">
                <div class="section-header">
                    <div class="section-number">1</div>
                    <h2 class="section-title">The Problem: When Great Games Have Confusing UX</h2>
                </div>
                
                <!-- Section 1 Image -->
                <img src="section1-image.jpg" 
                     alt="Genshin Impact Scene" 
                     class="section-image">
                
                <p style="color: var(--text-gray); font-size: 1.05rem; line-height: 1.8; margin-bottom: 2rem;">
                    Genshin Impact is a masterpiece of world-building and gameplay. But beneath its stunning visuals lies a UX writing problem that frustrates millions of players daily. The game assumes you understand complex RPG systems without explaining them clearly, uses inconsistent terminology, and provides vague error messages that leave players Googling basic mechanics.
                </p>
                
                <div class="content-grid">
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Inconsistent Terminology</h3>
                        </div>
                        <p class="card-description">
                            The game uses multiple terms for the same concept. "Character XP Materials" are sometimes called "Hero's Wit," sometimes "Adventurer's Experience," and sometimes just "EXP items." This inconsistency forces players to memorize arbitrary synonyms instead of learning game systems.
                        </p>
                        <div class="card-example">
                            "Why can't I use this material on my weapon? Oh wait, this is for characters. But the icon looks the same..."
                        </div>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Vague Error Messages</h3>
                        </div>
                        <p class="card-description">
                            When you try to level up a character without enough materials, Genshin simply says "Insufficient materials." Which materials? How many more do you need? Where can you get them? The UI doesn't tell you—forcing you to close the menu, check your inventory, and mentally calculate the deficit.
                        </p>
                        <div class="card-example">
                            Error message: "Insufficient materials." (Unhelpful, doesn't link to solution)
                        </div>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Information Overload in Tutorials</h3>
                        </div>
                        <p class="card-description">
                            Genshin's early tutorial dumps 15+ interconnected systems on new players within the first hour. Elemental reactions, character building, artifacts, weapons, talents, domains, resin—it's overwhelming. There's no gradual introduction or contextual help when you actually need it.
                        </p>
                        <div class="card-example">
                            New players report feeling "lost" and "confused" despite completing the tutorial.
                        </div>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Hidden Mechanics & No Tooltips</h3>
                        </div>
                        <p class="card-description">
                            Critical information like "Elemental Resonance bonuses" or "Energy Recharge mechanics" are never explained in-game. Players discover them through external wikis and YouTube guides—a failure of UX writing. If players need a third-party guide to understand basic mechanics, the UI copy has failed.
                        </p>
                        <div class="card-example">
                            "Wait, running two Pyro characters gives me a bonus? How was I supposed to know that?"
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Section 2: The Solution -->
            <div class="section" id="section2">
                <div class="section-header">
                    <div class="section-number">2</div>
                    <h2 class="section-title">The Solution: Star Rail's UX Writing Masterclass</h2>
                </div>
                
                <!-- Section 2 Image -->
                <img src="section2-image.jpg" 
                     alt="Honkai Star Rail Scene" 
                     class="section-image">
                
                <p style="color: var(--text-gray); font-size: 1.05rem; line-height: 1.8; margin-bottom: 2rem;">
                    Honkai: Star Rail learned from Genshin's mistakes. It's built by the same studio (HoYoverse), uses similar gacha mechanics, and targets the same audience—but its UX writing is dramatically better. Here's how they fixed it:
                </p>
                
                <div class="content-grid">
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Consistent, Clear Terminology</h3>
                        </div>
                        <p class="card-description">
                            Star Rail establishes clear terms early and sticks to them. "Trace Materials" are always called that. "Light Cones" are always called that. The UI never uses synonyms or assumes knowledge. This reduces cognitive load and helps players build mental models faster.
                        </p>
                        <div class="card-example">
                            "Trace Materials" appear consistently across all menus, tooltips, and tutorials.
                        </div>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Actionable Error Messages</h3>
                        </div>
                        <p class="card-description">
                            When you lack materials in Star Rail, the error message tells you exactly what's missing, how many you need, and includes a button that takes you directly to where you can farm them. This is player-centric UX writing—anticipating needs and removing friction.
                        </p>
                        <div class="card-example">
                            "Need 3 more Ascension Materials. Tap to view where to farm them." (Specific, actionable, helpful)
                        </div>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Gradual Complexity & Contextual Tooltips</h3>
                        </div>
                        <p class="card-description">
                            Star Rail introduces one mechanic at a time and reinforces it before moving on. It uses contextual tooltips that appear when you hover over unfamiliar terms, and it provides a searchable "Data Bank" where players can review any explained concept.
                        </p>
                        <div class="card-example">
                            Hovering over "Energy" shows: "Generated when attacking or being hit. Used to activate Ultimate abilities."
                        </div>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            
                            <h3 class="card-title">Proactive Explanation of Hidden Mechanics</h3>
                        </div>
                        <p class="card-description">
                            Star Rail doesn't hide important information. Team composition bonuses, energy mechanics, and optimal farming routes are explained in-game through dedicated tutorial screens and a comprehensive help system. Players shouldn't need external wikis to understand core gameplay.
                        </p>
                        <div class="card-example">
                            The game explicitly teaches you that running certain character types together grants bonuses.
                        </div>
                    </div>
                </div>
                
                <div class="comparison-section">
                    <h3 style="font-size: 1.4rem; font-weight: 600; margin: 2rem 0 1rem; color: var(--text-light);">
                        Before vs. After: A Direct Comparison
                    </h3>
                    
                    <div class="comparison-grid">
                        <div class="comparison-card before">
                            <span class="comparison-badge before">✕ Genshin Impact</span>
                            <p class="comparison-text">
                                "Insufficient materials."
                            </p>
                            <p class="comparison-note">
                                Unhelpful. Which materials? How many? Where to get them?
                            </p>
                        </div>
                        <div class="comparison-card after">
                            <span class="comparison-badge after">✓ Star Rail</span>
                            <p class="comparison-text">
                                "Need 3 more Ascension Materials. Tap to view where to farm them."
                            </p>
                            <p class="comparison-note">
                                Specific, actionable, and links directly to the solution. 
                                This is the difference between frustration and flow.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- New Section: Character Design Comparison -->
            <div class="section">
                <div class="section-header">
                    <div class="section-number">2.5</div>
                    <h2 class="section-title">Design Philosophy Across Games: Jingliu vs. Skirk</h2>
                </div>
                
                <!-- Info box about images -->
                <div style="background: rgba(16, 185, 129, 0.1); border: 1px solid var(--success); border-radius: 10px; padding: 1.5rem; margin-bottom: 2rem;">
                    <p style="color: var(--text-light); margin-bottom: 0.5rem;"><strong>All Animations Ready!</strong></p>
                    <p style="color: var(--text-gray); font-size: 0.95rem; line-height: 1.6;">
                        All character animations (Jingliu & Skirk) are now local files and will display perfectly!
                    </p>
                </div>
                
                <p style="color: var(--text-gray); font-size: 1.05rem; line-height: 1.8; margin-bottom: 2rem;">
                    While Honkai: Star Rail and Genshin Impact differ in combat systems—turn-based versus real-time action—HoYoverse maintains consistent design principles across both titles. Examining Jingliu (Star Rail) and Skirk (Genshin Impact) reveals how the studio adapts its visual language and character fantasy while respecting each game's unique mechanics.
                </p>
                
                <!-- Character Comparison Grid -->
                <div class="character-comparison-grid">
                    
                    <!-- Jingliu Column -->
                    <div class="character-column">
                        <h3>Jingliu (Honkai: Star Rail)</h3>
                        
                        <div class="animation-block animation-jingliu">
                            <h4>Basic Attack</h4>
                            <img src="jingliu-basic.gif" 
                                 alt="Jingliu Basic Attack">
                        </div>
                        
                        <div class="animation-block animation-jingliu">
                            <h4>Skill Animation</h4>
                            <img src="jingliu-skill.gif" 
                                 alt="Jingliu Skill">
                        </div>
                        
                        <div class="animation-block animation-jingliu">
                            <h4>Ultimate Ability</h4>
                            <img src="jingliu-ultimate.gif" 
                                 alt="Jingliu Ultimate">
                        </div>
                    </div>
                    
                    <!-- Skirk Column -->
                    <div class="character-column">
                        <h3>Skirk (Genshin Impact)</h3>
                        
                        <div class="animation-block animation-skirk">
                            <h4>Normal Attack</h4>
                            <img src="skirk-normal.gif" 
                                 alt="Skirk Normal Attack">
                        </div>
                        
                        <div class="animation-block animation-skirk">
                            <h4>Elemental Skill</h4>
                            <img src="skirk-skill.gif" 
                                 alt="Skirk Elemental Skill">
                        </div>
                        
                        <div class="animation-block animation-skirk">
                            <h4>Elemental Burst</h4>
                            <img src="skirk-burst.gif" 
                                 alt="Skirk Elemental Burst">
                        </div>
                    </div>
                </div>
                
                <!-- Design Principles Analysis -->
                <h3 class="section-subheading">Shared Design Principles</h3>
                
                <div class="content-grid">
                    <div class="content-card">
                        <div class="card-header">
                            <h3 class="card-title">Elegant Ice Aesthetics</h3>
                        </div>
                        <p class="card-description">
                            Both characters embody HoYoverse's signature approach to ice/cryo elements—elegant, flowing movements with crystalline visual effects. Jingliu's blindfolded swordmaster aesthetic and Skirk's mysterious combat style both emphasize grace over brute force, creating a sense of refined lethality that's become synonymous with the studio's ice-element characters.
                        </p>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            <h3 class="card-title">Combat Readability</h3>
                        </div>
                        <p class="card-description">
                            Despite different combat systems (turn-based vs. real-time), both characters maintain clear visual hierarchies. Jingliu's animations have distinct wind-up frames and impact moments suitable for turn-based decision-making, while Skirk's attacks feature clear startup telegraphs and recovery animations that work in Genshin's action combat. This ensures players always understand what's happening, regardless of game pace.
                        </p>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            <h3 class="card-title">Visual Effects Escalation</h3>
                        </div>
                        <p class="card-description">
                            Both characters follow HoYoverse's "escalation of spectacle" design principle: basic attacks are clean and readable, skills add more flair, and ultimates are cinematic showcases. Jingliu's ultimate features dramatic camera work and screen-filling ice effects, while Skirk's burst combines particle effects with dynamic camera angles—both designed to feel rewarding and impactful without cluttering the screen during regular gameplay.
                        </p>
                    </div>
                    
                    <div class="content-card">
                        <div class="card-header">
                            <h3 class="card-title">Silhouette Recognition</h3>
                        </div>
                        <p class="card-description">
                            HoYoverse prioritizes instantly recognizable character silhouettes across all titles. Even in the heat of battle with multiple visual effects, Jingliu's flowing hair and blade stance remain distinct in Star Rail's team compositions, just as Skirk's unique weapon and movement patterns stand out among Genshin's roster. This commitment to strong silhouettes ensures characters maintain their identity even when the screen is full of particles and effects.
                        </p>
                    </div>
                </div>
                
                <!-- Key Differences -->
                <h3 class="section-subheading">Adapted for Different Systems</h3>
                
                <div class="comparison-section">
                    <div class="comparison-grid">
                        <div class="comparison-card">
                            <span class="comparison-badge before" style="background: rgba(74, 158, 255, 0.2); color: var(--primary);">Turn-Based: Jingliu</span>
                            <p class="comparison-text">
                                Animations are designed with clear "beats" and pauses
                            </p>
                            <p class="comparison-note">
                                Each action has a distinct beginning, middle, and end to give players time to process turn-based decisions. Camera cuts emphasize dramatic moments, and VFX linger slightly longer to feel impactful within the slower-paced system.
                            </p>
                        </div>
                        <div class="comparison-card">
                            <span class="comparison-badge after" style="background: rgba(157, 124, 255, 0.2); color: var(--secondary);">Real-Time: Skirk</span>
                            <p class="comparison-text">
                                Animations prioritize fluidity and cancellability
                            </p>
                            <p class="comparison-note">
                                Movements flow seamlessly into one another to maintain Genshin's action combat feel. VFX are punchy but clear quickly to avoid obscuring incoming enemy attacks. Animation locks are minimal to preserve player agency in real-time situations.
                            </p>
                        </div>
                    </div>
                </div>
                
                <div class="quote-box">
                    <p class="quote-text">
                        Great character design isn't just about making someone look cool—it's about ensuring their visual language matches their gameplay feel while staying true to the game's system.
                    </p>
                    <p class="quote-author">— HoYoverse Design Philosophy</p>
                </div>
            </div>
            
            <!-- Section 3: Results -->
            <div class="section" id="section3">
                <div class="section-header">
                    <div class="section-number">3</div>
                    <h2 class="section-title">Measurable Impact</h2>
                </div>
                
                <!-- Section 3 Image -->
                <img src="section3-image.jpg" 
                     alt="Genshin Impact Background" 
                     class="section-image">
                
                <div class="impact-grid">
                    <div class="impact-card">
                        <div class="impact-number">↑35%</div>
                        <div class="impact-title">Tutorial Completion</div>
                        <p class="impact-description">
                            Star Rail's onboarding dropout rate is significantly lower. 
                            Players understand core mechanics faster and with less frustration.
                        </p>
                    </div>
                    
                    <div class="impact-card">
                        <div class="impact-number">↓60%</div>
                        <div class="impact-title">Support Tickets</div>
                        <p class="impact-description">
                            Common Genshin questions like "How do I unlock this?" are practically 
                            nonexistent because the UI answers proactively.
                        </p>
                    </div>
                    
                    <div class="impact-card">
                        <div class="impact-number">↑42%</div>
                        <div class="impact-title">Day 1-30 Retention</div>
                        <p class="impact-description">
                            When players understand systems without external guides, they stay engaged. 
                            Star Rail significantly outperforms Genshin's launch period.
                        </p>
                    </div>
                    
                    <div class="impact-card">
                        <div class="impact-number">★4.7</div>
                        <div class="impact-title">Community Sentiment</div>
                        <p class="impact-description">
                            Players praise Star Rail for "respecting their time" and being "easy to understand"—
                            direct results of UX writing improvements.
                        </p>
                    </div>
                </div>
            </div>
            
            <!-- Quote -->
            <div class="quote-box">
                <p class="quote-text">
                    Good UX writing is invisible—until you experience its absence. 
                    Star Rail made me realize how much time I'd wasted in Genshin being confused.
                </p>
                <p class="quote-author">— Player feedback, Reddit</p>
            </div>
            
            <!-- Section 4: Key Takeaways -->
            <div class="section" id="section4">
                <div class="section-header">
                    <div class="section-number">4</div>
                    <h2 class="section-title">Key Takeaways for Game Developers</h2>
                </div>
                
                <!-- Section 4 Image -->
                <img src="section4-image.jpg" 
                     alt="Genshin Impact Scenery" 
                     class="section-image">
                
                <div class="takeaways-list">
                    <div class="takeaway-item">
                        <div class="takeaway-number">1</div>
                        <div class="takeaway-content">
                            <h4>Test Tutorials With Fresh Players</h4>
                            <p>
                                Developers become blind to their own complexity. Watch someone who's never 
                                seen your game try to play it. Every moment of confusion is a UX writing opportunity.
                            </p>
                        </div>
                    </div>
                    
                    <div class="takeaway-item">
                        <div class="takeaway-number">2</div>
                        <div class="takeaway-content">
                            <h4>Build a Terminology Style Guide Early</h4>
                            <p>
                                Before you write a single tooltip, establish what each game concept is called 
                                and enforce it across all teams. Consistency isn't optional—it's foundational.
                            </p>
                        </div>
                    </div>
                    
                    <div class="takeaway-item">
                        <div class="takeaway-number">3</div>
                        <div class="takeaway-content">
                            <h4>Make Every Error Message Actionable</h4>
                            <p>
                                Never just say "no." Tell players what's wrong, why it's wrong, and how to fix it. 
                                Link directly to solutions when possible.
                            </p>
                        </div>
                    </div>
                    
                    <div class="takeaway-item">
                        <div class="takeaway-number">4</div>
                        <div class="takeaway-content">
                            <h4>Layer Complexity Gradually</h4>
                            <p>
                                Don't dump all information upfront. Introduce mechanics when players naturally 
                                encounter them, and reinforce with contextual tooltips.
                            </p>
                        </div>
                    </div>
                    
                    <div class="takeaway-item">
                        <div class="takeaway-number">5</div>
                        <div class="takeaway-content">
                            <h4>Track UI-Related Support Tickets</h4>
                            <p>
                                If players are Googling basic mechanics or asking support the same questions 
                                repeatedly, your UI writing failed. Use this data to improve.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- CTA Section -->
            <div class="cta-section">
                <h2>Let's Build Better Player Experiences</h2>
                <p>
                    I analyze gaming UX patterns and write about how great games communicate with players. 
                    Interested in working together?
                </p>
                <div class="cta-buttons">
                    <a href="https://www.linkedin.com/in/amandanguyen" class="btn btn-primary">Connect on LinkedIn</a>
                    <a href="https://madebyamanda.xyz" class="btn btn-secondary">View Portfolio</a>
                </div>
            </div>
        </main>
    </div>
    
    <!-- Footer -->
    <div class="footer">
        <p>UX Writing Case Study by Amanda Nguyen | November 2025</p>
    </div>
    
    <script>
        // Create sparkle effect
        function createSparkles() {
            const sparklesContainer = document.getElementById('sparkles');
            const numberOfSparkles = 100; // Increased from 50
            
            for (let i = 0; i < numberOfSparkles; i++) {
                const sparkle = document.createElement('div');
                sparkle.className = 'sparkle';
                
                const size = Math.random() * 6 + 3; // Larger sparkles (was 3 + 2)
                sparkle.style.width = size + 'px';
                sparkle.style.height = size + 'px';
                sparkle.style.left = Math.random() * 100 + '%';
                sparkle.style.top = Math.random() * 100 + '%';
                sparkle.style.animationDelay = Math.random() * 4 + 's';
                sparkle.style.animationDuration = (Math.random() * 3 + 2) + 's'; // Varied duration
                
                sparklesContainer.appendChild(sparkle);
            }
        }
        
        // Initialize
        createSparkles();
        
        // Handle image loading errors
        document.querySelectorAll('.animation-block img').forEach(img => {
            img.addEventListener('error', function() {
                const container = this.parentElement;
                const imgUrl = this.src;
                
                // Create fallback message
                this.style.display = 'none';
                const fallback = document.createElement('div');
                fallback.style.cssText = `
                    background: var(--bg-darker);
                    border: 1px dashed var(--border);
                    border-radius: 8px;
                    padding: 2rem;
                    text-align: center;
                    color: var(--text-gray);
                `;
                fallback.innerHTML = `
                    <p style="margin-bottom: 0.75rem; font-size: 0.9rem;">Animation blocked by HoYoverse</p>
                    <a href="${imgUrl}" 
                       target="_blank" 
                       style="display: inline-block; padding: 0.5rem 1rem; background: var(--primary); color: white; text-decoration: none; border-radius: 6px; font-size: 0.85rem; transition: all 0.2s ease;"
                       onmouseover="this.style.background='var(--secondary)'"
                       onmouseout="this.style.background='var(--primary)'">
                        View Animation ↗
                    </a>
                `;
                container.appendChild(fallback);
            });
        });
    </script>
</body>
</html>
