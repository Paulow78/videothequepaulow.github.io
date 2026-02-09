<!DOCTYPE html>
<html lang="fr" data-theme="dark">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Keibstream OS - Diamond Edition ✨</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg-deep: #000000;
            --glass-strong: rgba(20, 20, 20, 0.5);
            --glass-light: rgba(255, 255, 255, 0.08);
            --glass-border: rgba(255, 255, 255, 0.15);
            --glass-shine: rgba(255, 255, 255, 0.2);
            --text-main: #FFFFFF;
            --primary-glow: #0A84FF;
            --danger: #FF453A;
            --success: #30D158;
            --warning: #FFD60A;
            --app-blue: linear-gradient(135deg, #007AFF, #00C6FF);
            --app-purple: linear-gradient(135deg, #5856D6, #C644FC);
            --app-grey: linear-gradient(135deg, #8E8E93, #636366);
            --app-green: linear-gradient(135deg, #34C759, #30D158);
            --app-orange: linear-gradient(135deg, #FF9500, #FF6B35);
            --app-pink: linear-gradient(135deg, #FF2D55, #FF6B9D);
            --radius-xl: 24px;
            --radius-m: 16px;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; user-select: none; -webkit-tap-highlight-color: transparent; outline: none; }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-deep);
            color: var(--text-main);
            height: 100vh;
            overflow: hidden;
        }

        /* --- LIQUID BACKGROUND ENHANCED --- */
        .noise { position: fixed; inset: 0; opacity: 0.04; background: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='1'/%3E%3C/svg%3E"); pointer-events: none; z-index: -1; }
        .wallpaper {
            position: fixed; inset: 0; z-index: -2;
            background: radial-gradient(circle at 50% 110%, #1c1c3d 0%, #000000 80%);
        }
        .blob { 
            position: absolute; border-radius: 50%; 
            filter: blur(100px); opacity: 0.4; 
            animation: drift 25s infinite alternate ease-in-out;
            mix-blend-mode: screen;
        }
        .blob-1 { width: 700px; height: 700px; background: #0A84FF; top: -200px; left: -100px; opacity: 0.25; }
        .blob-2 { width: 600px; height: 600px; background: #BF5AF2; bottom: -150px; right: -100px; opacity: 0.2; animation-delay: -5s; }
        .blob-3 { width: 500px; height: 500px; background: #FF2D55; top: 50%; left: 50%; transform: translate(-50%, -50%); opacity: 0.15; animation-delay: -10s; }
        @keyframes drift { 
            0% { transform: translate(0,0) rotate(0deg); } 
            50% { transform: translate(40px, 60px) rotate(180deg); }
            100% { transform: translate(-20px, 30px) rotate(360deg); } 
        }

        /* --- LIQUID GLASS MIXINS --- */
        .liquid-glass {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(30px) saturate(180%);
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 
                0 8px 32px rgba(0, 0, 0, 0.3),
                inset 0 1px 0 rgba(255, 255, 255, 0.1);
        }

        .liquid-glass-hover {
            transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        .liquid-glass-hover:hover {
            background: rgba(255, 255, 255, 0.12);
            border-color: rgba(255, 255, 255, 0.25);
            box-shadow: 
                0 12px 40px rgba(0, 0, 0, 0.4),
                0 0 30px rgba(10, 132, 255, 0.15),
                inset 0 1px 0 rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        /* --- STATUS BAR (Enhanced) --- */
        .status-bar {
            position: fixed; top: 0; width: 100%; height: 44px;
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 24px; font-size: 0.8rem; z-index: 5000;
            background: rgba(10, 10, 10, 0.6); 
            backdrop-filter: blur(40px) saturate(200%);
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
        }

        .home-btn { 
            display: flex; align-items: center; gap: 10px; cursor: pointer; 
            opacity: 0.9; transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            font-weight: 700; letter-spacing: 0.5px;
            padding: 6px 12px; border-radius: 12px;
        }
        .home-btn:hover { 
            opacity: 1; 
            background: rgba(255, 255, 255, 0.08);
            text-shadow: 0 0 15px rgba(255, 255, 255, 0.5); 
        }
        .logo-box { 
            width: 24px; height: 24px; 
            background: linear-gradient(135deg, #fff, #e0e0e0); 
            color: #000; border-radius: 6px; 
            display: grid; place-items: center; 
            font-size: 0.75rem; font-weight: 900;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
        }

        .status-right { display: flex; align-items: center; gap: 12px; }
        
        /* Glass Pills Enhanced */
        .glass-pill {
            background: rgba(255, 255, 255, 0.06); 
            border: 1px solid rgba(255, 255, 255, 0.08);
            padding: 5px 12px; border-radius: 14px; 
            display: flex; align-items: center; gap: 8px;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            backdrop-filter: blur(20px);
            cursor: pointer;
        }
        .glass-pill:hover { 
            background: rgba(255, 255, 255, 0.12); 
            border-color: rgba(255, 255, 255, 0.25); 
            box-shadow: 0 4px 12px rgba(10, 132, 255, 0.2);
            transform: translateY(-1px);
        }

        .weather-info { display: flex; gap: 8px; font-weight: 500; }
        .w-red { color: #FF453A; } 
        .w-blue { color: #0A84FF; } 
        .w-hum { color: #30D158; opacity: 0.9; }

        /* Volume Slider Enhanced */
        .volume-control { display: flex; align-items: center; gap: 8px; width: 100px; }
        .vol-track { 
            flex: 1; height: 5px; 
            background: rgba(255, 255, 255, 0.15); 
            border-radius: 3px; position: relative; 
            cursor: pointer; overflow: hidden;
            box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.3);
        }
        .vol-fill { 
            height: 100%; width: 60%; 
            background: linear-gradient(90deg, #0A84FF, #00C6FF); 
            border-radius: 3px; transition: width 0.15s ease;
            box-shadow: 0 0 10px rgba(10, 132, 255, 0.5);
        }
        .volume-control:hover .vol-fill { 
            box-shadow: 0 0 15px rgba(10, 132, 255, 0.8);
        }

        /* Battery Enhanced */
        .batt-box { 
            width: 24px; height: 12px; 
            border: 1.5px solid rgba(255, 255, 255, 0.6); 
            border-radius: 3px; padding: 2px; 
            position: relative; display: flex; align-items: center;
        }
        .batt-box::after { 
            content:''; position: absolute; 
            right: -4px; top: 3px; 
            height: 6px; width: 2px; 
            background: rgba(255, 255, 255, 0.6); 
            border-radius: 0 2px 2px 0; 
        }
        .batt-in { 
            height: 100%; width: 50%; 
            background: linear-gradient(90deg, #30D158, #34C759); 
            border-radius: 1px;
            transition: all 0.3s;
        }

        /* --- TOOLBAR (New) --- */
        .toolbar {
            position: absolute; 
            top: 58px; left: 24px; right: 24px; 
            height: 56px; z-index: 100;
            display: flex; gap: 12px; align-items: center;
        }

        .search-input-glass {
            flex: 1; max-width: 450px; height: 42px;
            background: rgba(255, 255, 255, 0.06); 
            backdrop-filter: blur(40px) saturate(180%);
            border: 1px solid rgba(255, 255, 255, 0.1); 
            border-radius: 14px;
            display: flex; align-items: center; 
            padding: 0 16px; gap: 12px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2),
                        inset 0 1px 0 rgba(255, 255, 255, 0.1);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .search-input-glass:focus-within { 
            width: 500px; 
            background: rgba(40, 40, 40, 0.5); 
            border-color: var(--primary-glow); 
            box-shadow: 0 8px 30px rgba(10, 132, 255, 0.3),
                        0 0 0 4px rgba(10, 132, 255, 0.1);
        }
        .search-input-glass input { 
            flex: 1; background: transparent; 
            border: none; color: white; 
            font-size: 0.95rem; font-weight: 500;
        }
        .search-input-glass input::placeholder { 
            color: rgba(255, 255, 255, 0.4); 
        }

        .toolbar-btn {
            height: 42px; padding: 0 16px;
            background: rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(40px) saturate(180%);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 14px;
            display: flex; align-items: center; gap: 8px;
            color: white; font-size: 0.9rem; font-weight: 600;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        .toolbar-btn:hover {
            background: rgba(255, 255, 255, 0.12);
            border-color: rgba(255, 255, 255, 0.25);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
        }
        .toolbar-btn.active {
            background: var(--primary-glow);
            border-color: var(--primary-glow);
            box-shadow: 0 4px 15px rgba(10, 132, 255, 0.4);
        }

        .view-toggle {
            display: flex; gap: 4px;
            background: rgba(255, 255, 255, 0.06);
            padding: 4px; border-radius: 12px;
        }
        .view-toggle button {
            width: 36px; height: 34px;
            background: transparent;
            border: none; color: rgba(255, 255, 255, 0.5);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }
        .view-toggle button.active {
            background: rgba(255, 255, 255, 0.15);
            color: white;
        }

        /* Filter Tags */
        .filter-tags {
            display: flex; gap: 8px; overflow-x: auto;
            scrollbar-width: none;
            padding: 2px;
        }
        .filter-tags::-webkit-scrollbar { display: none; }
        .filter-tag {
            padding: 6px 14px;
            background: rgba(255, 255, 255, 0.06);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            font-size: 0.85rem;
            white-space: nowrap;
            cursor: pointer;
            transition: all 0.3s;
        }
        .filter-tag:hover {
            background: rgba(255, 255, 255, 0.12);
        }
        .filter-tag.active {
            background: var(--primary-glow);
            border-color: var(--primary-glow);
            box-shadow: 0 4px 12px rgba(10, 132, 255, 0.3);
        }

        /* --- DESKTOP GRID (Enhanced) --- */
        .desktop {
            position: absolute; 
            top: 128px; bottom: 105px; 
            left: 0; right: 0;
            padding: 0 24px; 
            overflow-y: auto; 
            scrollbar-width: thin;
            scrollbar-color: rgba(255, 255, 255, 0.2) transparent;
        }
        .desktop::-webkit-scrollbar { width: 8px; }
        .desktop::-webkit-scrollbar-track { background: transparent; }
        .desktop::-webkit-scrollbar-thumb { 
            background: rgba(255, 255, 255, 0.2); 
            border-radius: 4px; 
        }
        .desktop::-webkit-scrollbar-thumb:hover { 
            background: rgba(255, 255, 255, 0.3); 
        }
        
        .grid-container {
            display: grid; 
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 24px; padding-bottom: 40px;
            transition: all 0.3s;
        }

        .grid-container.list-view {
            grid-template-columns: 1fr;
            gap: 12px;
        }

        /* Card Styles */
        .card {
            position: relative; 
            aspect-ratio: 2/3; 
            border-radius: 18px; 
            cursor: pointer;
            transform-style: preserve-3d; 
            transition: all 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            overflow: hidden;
        }
        
        .grid-container.list-view .card {
            aspect-ratio: unset;
            height: 140px;
            display: flex;
        }

        .card-bg {
            position: absolute; inset: 0; 
            border-radius: 18px; overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.08);
            background: rgba(20, 20, 20, 0.4);
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4),
                        inset 0 1px 0 rgba(255, 255, 255, 0.05);
        }
        
        .card img { 
            width: 100%; height: 100%; 
            object-fit: cover; 
            transition: transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        
        /* Progress Bar */
        .card-progress {
            position: absolute;
            bottom: 0; left: 0; right: 0;
            height: 4px;
            background: rgba(0, 0, 0, 0.5);
            z-index: 2;
        }
        .card-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, var(--primary-glow), #00C6FF);
            width: 0%;
            transition: width 0.3s;
            box-shadow: 0 0 10px rgba(10, 132, 255, 0.6);
        }

        /* Badge */
        .card-badge {
            position: absolute;
            top: 12px; left: 12px;
            padding: 4px 10px;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            border-radius: 8px;
            font-size: 0.7rem;
            font-weight: 700;
            z-index: 3;
            display: flex; align-items: center; gap: 4px;
        }
        .card-badge.new { color: var(--success); }
        .card-badge.watched { color: var(--primary-glow); }

        /* Actions */
        .card-actions {
            position: absolute;
            top: 12px; right: 12px;
            display: flex; gap: 6px;
            opacity: 0;
            transform: translateY(-10px);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 3;
        }
        .card:hover .card-actions {
            opacity: 1;
            transform: translateY(0);
        }
        .card-action-btn {
            width: 32px; height: 32px;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            display: grid; place-items: center;
            color: white;
            cursor: pointer;
            transition: all 0.3s;
        }
        .card-action-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: scale(1.1);
        }
        .card-action-btn.favorite.active {
            color: #FF2D55;
        }

        /* Details */
        .card-details {
            position: absolute; 
            bottom: 0; left: 0; right: 0; 
            padding: 16px;
            background: linear-gradient(to top, rgba(0, 0, 0, 0.95) 0%, rgba(0, 0, 0, 0.7) 50%, transparent 100%);
            transform: translateY(100%); 
            opacity: 0; 
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 2;
        }
        .card-details h3 { 
            font-size: 1rem; 
            margin-bottom: 6px; 
            font-weight: 700;
        }
        .card-details p { 
            font-size: 0.8rem; 
            color: rgba(255, 255, 255, 0.7); 
            margin-bottom: 8px;
        }
        .card-meta {
            display: flex;
            gap: 12px;
            font-size: 0.75rem;
            color: rgba(255, 255, 255, 0.5);
        }
        .card-meta span {
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .card:hover { 
            transform: translateY(-10px) scale(1.02); 
            z-index: 10; 
        }
        .card:hover .card-bg { 
            border-color: rgba(255, 255, 255, 0.3); 
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.6), 
                        0 0 40px rgba(10, 132, 255, 0.2),
                        inset 0 1px 0 rgba(255, 255, 255, 0.1);
        }
        .card:hover img { 
            transform: scale(1.1); 
        }
        .card:hover .card-details { 
            transform: translateY(0); 
            opacity: 1; 
        }

        /* List View Specific */
        .grid-container.list-view .card {
            transform: none !important;
        }
        .grid-container.list-view .card-bg {
            display: flex;
            flex-direction: row;
        }
        .grid-container.list-view .card img {
            width: 100px;
            height: 100%;
        }
        .grid-container.list-view .card-details {
            position: relative;
            transform: none;
            opacity: 1;
            flex: 1;
            background: transparent;
        }

        /* Empty State */
        .add-new {
            border: 2px dashed rgba(255, 255, 255, 0.15); 
            display: flex; flex-direction: column; 
            align-items: center; justify-content: center; 
            gap: 12px; color: rgba(255, 255, 255, 0.3);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            background: rgba(255, 255, 255, 0.02);
        }
        .add-new:hover { 
            border-color: var(--primary-glow); 
            color: var(--primary-glow); 
            background: rgba(10, 132, 255, 0.08); 
            box-shadow: 0 8px 30px rgba(10, 132, 255, 0.2);
        }

        /* --- APPLE DOCK (Enhanced) --- */
        .dock-wrap {
            position: absolute; 
            bottom: 24px; left: 50%; 
            transform: translateX(-50%);
            padding: 14px 18px; 
            background: rgba(240, 240, 240, 0.08); 
            backdrop-filter: blur(50px) saturate(200%);
            border: 1px solid rgba(255, 255, 255, 0.2); 
            border-radius: 26px;
            display: flex; gap: 16px; 
            align-items: center; 
            z-index: 4000;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5),
                        inset 0 1px 0 rgba(255, 255, 255, 0.2);
        }
        .app-icon {
            width: 52px; height: 52px; 
            border-radius: 14px;
            display: flex; justify-content: center; 
            align-items: center;
            font-size: 1.5rem; color: white; 
            cursor: pointer;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4),
                        inset 0 1px 0 rgba(255, 255, 255, 0.2);
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative;
        }
        .app-icon::before {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: 14px;
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.2), transparent);
            opacity: 0;
            transition: opacity 0.3s;
        }
        .app-icon:hover::before {
            opacity: 1;
        }
        .app-icon:hover { 
            transform: translateY(-18px) scale(1.15); 
            box-shadow: 0 20px 35px rgba(0, 0, 0, 0.5),
                        0 0 30px rgba(255, 255, 255, 0.1);
        }
        .app-icon:active { 
            transform: translateY(-16px) scale(1.1); 
            filter: brightness(0.9); 
        }

        .icon-blue { background: var(--app-blue); }
        .icon-purple { background: var(--app-purple); }
        .icon-grey { background: var(--app-grey); }
        .icon-green { background: var(--app-green); }
        .icon-orange { background: var(--app-orange); }
        .icon-pink { background: var(--app-pink); }

        /* Dock separator */
        .dock-separator {
            width: 1px;
            height: 40px;
            background: rgba(255, 255, 255, 0.2);
        }

        /* --- MODALS (Enhanced) --- */
        .overlay {
            position: fixed; inset: 0; 
            background: rgba(0, 0, 0, 0.7); 
            backdrop-filter: blur(20px);
            z-index: 8000; 
            display: none; 
            align-items: center; 
            justify-content: center; 
            opacity: 0; 
            transition: opacity 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .overlay.visible { opacity: 1; }
        
        .liquid-window {
            width: 480px; 
            max-width: 90vw;
            padding: 36px; 
            background: rgba(25, 25, 25, 0.8);
            backdrop-filter: blur(40px) saturate(180%);
            border: 1px solid rgba(255, 255, 255, 0.15); 
            border-radius: 24px;
            box-shadow: 0 40px 100px rgba(0, 0, 0, 0.9), 
                        inset 0 1px 0 rgba(255, 255, 255, 0.1);
            text-align: center; 
            position: relative;
            transform: scale(0.9);
            transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        .overlay.visible .liquid-window {
            transform: scale(1);
        }

        .modal-close {
            position: absolute;
            top: 20px; right: 20px;
            width: 32px; height: 32px;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: grid; place-items: center;
            cursor: pointer;
            transition: all 0.3s;
            color: rgba(255, 255, 255, 0.6);
            font-size: 1.2rem;
        }
        .modal-close:hover {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            transform: rotate(90deg);
        }

        .liquid-window h2 {
            font-size: 1.8rem;
            margin-bottom: 8px;
            font-weight: 800;
        }
        .liquid-window .subtitle {
            color: rgba(255, 255, 255, 0.5);
            margin-bottom: 24px;
            font-size: 0.9rem;
        }

        .win-input { 
            width: 100%; 
            background: rgba(255, 255, 255, 0.05); 
            border: 1px solid rgba(255, 255, 255, 0.1); 
            padding: 14px 16px; 
            margin: 10px 0; 
            border-radius: 12px; 
            color: white; 
            font-size: 0.95rem;
            transition: all 0.3s;
        }
        .win-input:focus {
            background: rgba(255, 255, 255, 0.08);
            border-color: var(--primary-glow);
            box-shadow: 0 0 0 4px rgba(10, 132, 255, 0.1);
        }

        .win-select {
            width: 100%;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 14px 16px;
            margin: 10px 0;
            border-radius: 12px;
            color: white;
            font-size: 0.95rem;
            cursor: pointer;
        }

        .win-btn { 
            width: 100%; 
            padding: 14px; 
            background: linear-gradient(135deg, var(--primary-glow), #00C6FF); 
            border: none; 
            border-radius: 12px; 
            color: white; 
            font-weight: 700; 
            font-size: 1rem;
            margin-top: 16px; 
            cursor: pointer; 
            transition: all 0.3s;
            box-shadow: 0 6px 20px rgba(10, 132, 255, 0.3);
        }
        .win-btn:hover { 
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(10, 132, 255, 0.5); 
        }
        .win-btn:active {
            transform: translateY(0);
        }

        .win-btn.danger {
            background: linear-gradient(135deg, var(--danger), #FF6B35);
            box-shadow: 0 6px 20px rgba(255, 69, 58, 0.3);
        }
        .win-btn.danger:hover {
            box-shadow: 0 8px 25px rgba(255, 69, 58, 0.5);
        }

        /* --- VIDEO PLAYER (Enhanced) --- */
        #player { 
            position: fixed; 
            inset: 0; 
            background: black; 
            z-index: 9999; 
            display: none; 
        }
        
        .player-controls {
            position: absolute;
            top: 0; left: 0; right: 0;
            padding: 20px 30px;
            background: linear-gradient(to bottom, rgba(0, 0, 0, 0.8), transparent);
            display: flex;
            align-items: center;
            gap: 20px;
            z-index: 2;
        }

        .back-btn { 
            width: 50px; height: 50px; 
            border-radius: 50%; 
            background: rgba(255, 255, 255, 0.15); 
            backdrop-filter: blur(10px); 
            display: flex; align-items: center; 
            justify-content: center; 
            cursor: pointer; 
            color: white; 
            transition: all 0.3s;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        .back-btn:hover { 
            background: rgba(255, 255, 255, 0.25); 
            transform: scale(1.05);
        }

        .player-title {
            flex: 1;
            font-size: 1.2rem;
            font-weight: 700;
        }

        /* --- TOAST NOTIFICATIONS --- */
        .toast-container {
            position: fixed;
            top: 70px;
            right: 24px;
            z-index: 9000;
            display: flex;
            flex-direction: column;
            gap: 12px;
            pointer-events: none;
        }

        .toast {
            padding: 16px 20px;
            background: rgba(25, 25, 25, 0.95);
            backdrop-filter: blur(40px) saturate(180%);
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 14px;
            color: white;
            display: flex;
            align-items: center;
            gap: 12px;
            min-width: 300px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5),
                        inset 0 1px 0 rgba(255, 255, 255, 0.1);
            animation: slideIn 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            pointer-events: all;
        }

        @keyframes slideIn {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .toast.success { border-left: 4px solid var(--success); }
        .toast.error { border-left: 4px solid var(--danger); }
        .toast.info { border-left: 4px solid var(--primary-glow); }

        .toast-icon {
            font-size: 1.2rem;
        }

        .toast.success .toast-icon { color: var(--success); }
        .toast.error .toast-icon { color: var(--danger); }
        .toast.info .toast-icon { color: var(--primary-glow); }

        /* --- STATS PANEL --- */
        .stats-panel {
            padding: 20px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 16px;
            margin-bottom: 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 16px;
        }

        .stat-item {
            text-align: center;
            padding: 16px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.08);
        }

        .stat-value {
            font-size: 2rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--primary-glow), #00C6FF);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .stat-label {
            font-size: 0.85rem;
            color: rgba(255, 255, 255, 0.5);
            margin-top: 4px;
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 768px) {
            .dock-wrap { 
                bottom: 15px; 
                padding: 10px 12px; 
                gap: 10px; 
            }
            .app-icon { 
                width: 44px; 
                height: 44px; 
                font-size: 1.2rem; 
            }
            .grid-container { 
                grid-template-columns: repeat(2, 1fr); 
                gap: 16px; 
            }
            .search-input-glass { 
                max-width: 100%; 
            }
            .status-bar { 
                font-size: 0.7rem; 
                padding: 0 12px; 
            }
            .hide-mobile { 
                display: none !important; 
            }
            .toolbar {
                flex-wrap: wrap;
                height: auto;
                gap: 8px;
            }
            .toolbar-btn {
                font-size: 0.8rem;
                padding: 0 12px;
            }
            .desktop {
                top: 180px;
            }
        }

        /* --- ANIMATIONS --- */
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .loading-skeleton {
            background: linear-gradient(90deg, 
                rgba(255, 255, 255, 0.05) 0%, 
                rgba(255, 255, 255, 0.1) 50%, 
                rgba(255, 255, 255, 0.05) 100%);
            background-size: 200% 100%;
            animation: shimmer 1.5s infinite;
        }

        @keyframes shimmer {
            0% { background-position: -200% 0; }
            100% { background-position: 200% 0; }
        }
    </style>
</head>

<body oncontextmenu="return false;">

    <div class="wallpaper"></div>
    <div class="blob blob-1"></div>
    <div class="blob blob-2"></div>
    <div class="blob blob-3"></div>
    <div class="noise"></div>

    <!-- STATUS BAR -->
    <header class="status-bar">
        <div class="home-btn" onclick="OS.reset()">
            <div class="logo-box">K</div>
            <span class="hide-mobile">Keibstream</span>
        </div>

        <div class="status-right">
            <div class="glass-pill" onclick="Geo.fetchWeather()" title="Mettre à jour">
                <i class="fas fa-cloud-sun"></i>
                <div class="weather-info" id="weather-display">
                    Chargement...
                </div>
            </div>

            <div class="glass-pill hide-mobile">
                <i class="fas fa-volume-up"></i>
                <div class="volume-control" onmousedown="OS.startVolume(event)" onmousemove="OS.dragVolume(event)">
                    <div class="vol-track"><div class="vol-fill" id="vol-fill"></div></div>
                </div>
            </div>

            <div class="glass-pill" id="batt-widget">
                <div class="batt-box"><div class="batt-in" id="batt-in"></div></div>
                <span id="batt-txt" style="font-size:0.75rem">--%</span>
            </div>

            <div class="glass-pill" style="font-variant-numeric: tabular-nums;">
                <span id="date-txt" class="hide-mobile" style="opacity:0.6; margin-right:5px;">--/--</span>
                <span id="clock-txt" style="font-weight:700;">--:--:--</span>
            </div>

            <button style="background:none; border:none; color:white; cursor:pointer; font-size:1.1rem;" onclick="OS.fullscreen()" title="Plein écran">
                <i class="fas fa-expand"></i>
            </button>
        </div>
    </header>

    <!-- TOOLBAR -->
    <div class="toolbar">
        <div class="search-input-glass">
            <i class="fas fa-search" style="opacity:0.5; font-size:1.1rem;"></i>
            <input type="text" id="search" placeholder="Rechercher dans ma vidéothèque..." oninput="OS.filter()">
        </div>

        <div class="view-toggle">
            <button class="active" onclick="OS.setView('grid')" title="Grille">
                <i class="fas fa-th"></i>
            </button>
            <button onclick="OS.setView('list')" title="Liste">
                <i class="fas fa-list"></i>
            </button>
        </div>

        <div class="toolbar-btn" onclick="OS.modal('sort')">
            <i class="fas fa-sort"></i>
            <span class="hide-mobile">Trier</span>
        </div>

        <div class="toolbar-btn" onclick="OS.toggleFavoritesOnly()">
            <i class="fas fa-heart"></i>
            <span class="hide-mobile">Favoris</span>
        </div>
    </div>

    <!-- DESKTOP GRID -->
    <main class="desktop">
        <div class="grid-container" id="grid"></div>
    </main>

    <!-- DOCK -->
    <div class="dock-wrap">
        <div class="app-icon icon-blue" onclick="OS.reset()" title="Accueil">
            <i class="fas fa-home"></i>
        </div>
        <div class="app-icon icon-green" onclick="document.getElementById('local-file').click()" title="Fichier Local">
            <i class="fas fa-folder-open"></i>
        </div>
        <div class="dock-separator"></div>
        <div class="app-icon icon-purple" onclick="OS.modal('add')" title="Ajouter">
            <i class="fas fa-plus"></i>
        </div>
        <div class="app-icon icon-pink" onclick="OS.modal('categories')" title="Catégories">
            <i class="fas fa-tags"></i>
        </div>
        <div class="app-icon icon-orange" onclick="OS.modal('stats')" title="Statistiques">
            <i class="fas fa-chart-line"></i>
        </div>
        <div class="dock-separator"></div>
        <div class="app-icon icon-grey" onclick="OS.modal('settings')" title="Réglages">
            <i class="fas fa-cog"></i>
        </div>
    </div>

    <input type="file" id="local-file" accept="video/*" hidden onchange="Data.addLocal(this)">

    <!-- MODAL: Add Video -->
    <div class="overlay" id="modal-add">
        <div class="liquid-window">
            <div class="modal-close" onclick="OS.closeModal('add')">&times;</div>
            <h2>✨ Ajouter une Vidéo</h2>
            <p class="subtitle">Enrichissez votre collection</p>
            
            <input type="text" id="in-title" class="win-input" placeholder="Titre du film / série">
            <input type="text" id="in-url" class="win-input" placeholder="Lien Google Drive ou URL MP4">
            <input type="text" id="in-img" class="win-input" placeholder="URL de l'affiche (facultatif)">
            
            <select id="in-category" class="win-select">
                <option value="">Catégorie (facultatif)</option>
                <option value="Action">🎬 Action</option>
                <option value="Comédie">😂 Comédie</option>
                <option value="Drame">🎭 Drame</option>
                <option value="Science-Fiction">🚀 Science-Fiction</option>
                <option value="Horreur">👻 Horreur</option>
                <option value="Romance">💕 Romance</option>
                <option value="Documentaire">📚 Documentaire</option>
                <option value="Animation">🎨 Animation</option>
                <option value="Thriller">🔪 Thriller</option>
                <option value="Autre">📁 Autre</option>
            </select>
            
            <button class="win-btn" onclick="Data.addDrive()">
                <i class="fas fa-plus-circle"></i> Ajouter à ma collection
            </button>
        </div>
    </div>

    <!-- MODAL: Categories -->
    <div class="overlay" id="modal-categories">
        <div class="liquid-window">
            <div class="modal-close" onclick="OS.closeModal('categories')">&times;</div>
            <h2>🏷️ Catégories</h2>
            <p class="subtitle">Filtrer par genre</p>
            
            <div class="filter-tags" style="flex-wrap: wrap; justify-content: center; margin-top: 20px;">
                <div class="filter-tag active" onclick="OS.filterByCategory('all')">Tout</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Action')">🎬 Action</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Comédie')">😂 Comédie</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Drame')">🎭 Drame</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Science-Fiction')">🚀 Sci-Fi</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Horreur')">👻 Horreur</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Romance')">💕 Romance</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Documentaire')">📚 Doc</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Animation')">🎨 Animation</div>
                <div class="filter-tag" onclick="OS.filterByCategory('Thriller')">🔪 Thriller</div>
            </div>
        </div>
    </div>

    <!-- MODAL: Sort -->
    <div class="overlay" id="modal-sort">
        <div class="liquid-window">
            <div class="modal-close" onclick="OS.closeModal('sort')">&times;</div>
            <h2>🔄 Trier par</h2>
            <p class="subtitle">Organisez votre collection</p>
            
            <button class="win-btn" onclick="OS.sortBy('recent')" style="margin-top: 20px;">
                <i class="fas fa-clock"></i> Plus récents
            </button>
            <button class="win-btn" onclick="OS.sortBy('alpha')">
                <i class="fas fa-sort-alpha-down"></i> Ordre alphabétique
            </button>
            <button class="win-btn" onclick="OS.sortBy('watched')">
                <i class="fas fa-eye"></i> Visionnés
            </button>
        </div>
    </div>

    <!-- MODAL: Stats -->
    <div class="overlay" id="modal-stats">
        <div class="liquid-window" style="max-width: 600px;">
            <div class="modal-close" onclick="OS.closeModal('stats')">&times;</div>
            <h2>📊 Statistiques</h2>
            <p class="subtitle">Votre vidéothèque en chiffres</p>
            
            <div class="stats-panel">
                <div class="stats-grid">
                    <div class="stat-item">
                        <div class="stat-value" id="stat-total">0</div>
                        <div class="stat-label">Vidéos</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="stat-favorites">0</div>
                        <div class="stat-label">Favoris</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="stat-watched">0</div>
                        <div class="stat-label">Visionnés</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="stat-categories">0</div>
                        <div class="stat-label">Catégories</div>
                    </div>
                </div>
            </div>

            <button class="win-btn" onclick="OS.closeModal('stats')">
                <i class="fas fa-check"></i> Fermer
            </button>
        </div>
    </div>

    <!-- MODAL: Settings -->
    <div class="overlay" id="modal-settings">
        <div class="liquid-window">
            <div class="modal-close" onclick="OS.closeModal('settings')">&times;</div>
            <h2>⚙️ Réglages</h2>
            <p class="subtitle">Configuration du système</p>
            
            <div style="text-align: left; margin: 20px 0;">
                <p style="opacity: 0.7; margin-bottom: 16px;">
                    <i class="fas fa-database"></i> Stockage local : <strong id="storage-size">0 KB</strong>
                </p>
                <p style="opacity: 0.7; margin-bottom: 16px;">
                    <i class="fas fa-film"></i> Vidéos enregistrées : <strong id="video-count">0</strong>
                </p>
            </div>
            
            <button class="win-btn danger" onclick="Data.wipe()">
                <i class="fas fa-trash-alt"></i> Réinitialiser la vidéothèque
            </button>
        </div>
    </div>

    <!-- VIDEO PLAYER -->
    <div id="player">
        <div class="player-controls">
            <div class="back-btn" onclick="OS.closePlayer()">
                <i class="fas fa-arrow-left"></i>
            </div>
            <div class="player-title" id="player-title">Lecture en cours...</div>
        </div>
        <iframe id="iframe" src="" style="width:100%; height:100%; border:none;" allowfullscreen></iframe>
    </div>

    <!-- TOAST NOTIFICATIONS -->
    <div class="toast-container" id="toast-container"></div>

    <script>
        // Configuration
        const DEFAULT = [
            { id: 'd1', t: 'Oppenheimer', u: '1oyeiPyvB5ng5Ov4HUC0Gm82vXYBr4Kus', i: 'miniatures/Oppenheimer 2023.jpg', type: 'cloud', category: 'Drame', favorite: false, watched: false, progress: 0, addedDate: new Date('2024-01-15').getTime() },
            { id: 'd2', t: 'Dune: Part One', u: '16d0WGKlP51SO2TpP9rrxB55VfhaDum1r', i: 'miniatures/dune 1.jpg', type: 'cloud', category: 'Science-Fiction', favorite: false, watched: false, progress: 0, addedDate: new Date('2024-01-20').getTime() },
            { id: 'd3', t: 'Titanic', u: '1Nj1J1ZydGKpv7X3eaRU2kxgATANuC2uy', i: 'miniatures/titanic.jpg', type: 'cloud', category: 'Romance', favorite: false, watched: false, progress: 0, addedDate: new Date('2024-02-01').getTime() },
            { id: 'd4', t: 'Kingdom of Heaven', u: '1_SbYuHgQgUH2I6TKvmhP8uHz5_oGqgrW', i: 'miniatures/kingdomofheaven.png', type: 'cloud', category: 'Action', favorite: false, watched: false, progress: 0, addedDate: new Date('2024-02-10').getTime() },
            { id: 'd5', t: 'Gran Turismo', u: '1zGQ8bE-lPy_mpBWShUQb6GSpfDaNSNRt', i: 'miniatures/Grand%20Turismo%202023.jpeg', type: 'cloud', category: 'Action', favorite: false, watched: false, progress: 0, addedDate: new Date('2024-02-15').getTime() }
        ];

        // Data Management
        const Data = {
            list: [],
            currentFilter: 'all',
            currentSort: 'recent',
            favoritesOnly: false,
            
            init: function() {
                const s = localStorage.getItem('keib_diamond');
                this.list = s ? JSON.parse(s) : [...DEFAULT];
                
                // Migration: add new fields to existing data
                this.list = this.list.map(item => ({
                    ...item,
                    category: item.category || '',
                    favorite: item.favorite || false,
                    watched: item.watched || false,
                    progress: item.progress || 0,
                    addedDate: item.addedDate || Date.now()
                }));
                
                if(!s) this.save();
                OS.render();
                OS.updateStats();
            },
            
            save: function() { 
                localStorage.setItem('keib_diamond', JSON.stringify(this.list)); 
                OS.updateStats();
            },
            
            addDrive: function() {
                const t = document.getElementById('in-title').value.trim();
                let u = document.getElementById('in-url').value.trim();
                const i = document.getElementById('in-img').value.trim();
                const c = document.getElementById('in-category').value;
                
                if(!t || !u) {
                    Toast.show('Veuillez remplir tous les champs requis', 'error');
                    return;
                }
                
                // Extract Drive ID
                const m = u.match(/\/d\/(.+?)\//);
                if(m) u = m[1];
                
                const newItem = { 
                    id: 'u'+Date.now(), 
                    t: t, 
                    u: u, 
                    i: i || '', 
                    type: 'cloud',
                    category: c,
                    favorite: false,
                    watched: false,
                    progress: 0,
                    addedDate: Date.now()
                };
                
                this.list.unshift(newItem);
                this.save(); 
                OS.render(); 
                OS.closeModal('add');
                
                // Clear inputs
                document.getElementById('in-title').value=''; 
                document.getElementById('in-url').value='';
                document.getElementById('in-img').value='';
                document.getElementById('in-category').value='';
                
                Toast.show(`"${t}" ajouté avec succès!`, 'success');
            },
            
            addLocal: function(inp) {
                if(inp.files[0]) {
                    const f = inp.files[0];
                    const newItem = { 
                        id: 'l'+Date.now(), 
                        t: f.name.replace(/\.[^/.]+$/, ''), 
                        u: URL.createObjectURL(f), 
                        i: '', 
                        type: 'local',
                        category: '',
                        favorite: false,
                        watched: false,
                        progress: 0,
                        addedDate: Date.now()
                    };
                    this.list.unshift(newItem);
                    this.save();
                    OS.render();
                    Toast.show(`"${newItem.t}" ajouté depuis le disque local!`, 'success');
                }
            },
            
            toggleFavorite: function(id) {
                const item = this.list.find(i => i.id === id);
                if(item) {
                    item.favorite = !item.favorite;
                    this.save();
                    OS.render();
                    Toast.show(item.favorite ? 'Ajouté aux favoris ❤️' : 'Retiré des favoris', 'info');
                }
            },
            
            markAsWatched: function(id) {
                const item = this.list.find(i => i.id === id);
                if(item) {
                    item.watched = !item.watched;
                    item.progress = item.watched ? 100 : 0;
                    this.save();
                    OS.render();
                }
            },
            
            deleteItem: function(id) {
                if(confirm('Êtes-vous sûr de vouloir supprimer cette vidéo ?')) {
                    this.list = this.list.filter(i => i.id !== id);
                    this.save();
                    OS.render();
                    Toast.show('Vidéo supprimée', 'info');
                }
            },
            
            wipe: function() {
                if(confirm('⚠️ Voulez-vous vraiment réinitialiser toute la vidéothèque ? Cette action est irréversible.')) {
                    localStorage.removeItem('keib_diamond'); 
                    Toast.show('Vidéothèque réinitialisée', 'success');
                    setTimeout(() => location.reload(), 1500);
                }
            }
        };

        // Geolocation & Weather
        const Geo = {
            fetchWeather: function() {
                const disp = document.getElementById('weather-display');
                disp.innerHTML = '<i class="fas fa-sync fa-spin"></i>';
                
                if(!navigator.geolocation) { 
                    disp.innerHTML = "GPS Inactif"; 
                    return; 
                }
                
                navigator.geolocation.getCurrentPosition(async pos => {
                    const lat = pos.coords.latitude;
                    const lon = pos.coords.longitude;
                    
                    try {
                        // Get City Name
                        const cityRes = await fetch(`https://nominatim.openstreetmap.org/reverse?format=json&lat=${lat}&lon=${lon}`);
                        const cityData = await cityRes.json();
                        const city = cityData.address.city || cityData.address.town || cityData.address.village || "Localisation";

                        // Get Weather
                        const wRes = await fetch(`https://api.open-meteo.com/v1/forecast?latitude=${lat}&longitude=${lon}&current=temperature_2m,relative_humidity_2m&daily=temperature_2m_max,temperature_2m_min&timezone=auto`);
                        const wData = await wRes.json();
                        
                        const cur = Math.round(wData.current.temperature_2m);
                        const hum = wData.current.relative_humidity_2m;
                        const max = Math.round(wData.daily.temperature_2m_max[0]);
                        const min = Math.round(wData.daily.temperature_2m_min[0]);

                        disp.innerHTML = `
                            <span>${city} ${cur}°</span>
                            <span class="w-hum hide-mobile"><i class="fas fa-tint"></i> ${hum}%</span>
                            <span class="w-red hide-mobile">↑${max}</span>
                            <span class="w-blue hide-mobile">↓${min}</span>
                        `;
                    } catch(e) { 
                        disp.innerText = "Erreur réseau"; 
                    }
                }, () => { 
                    disp.innerText = "Paris 18°"; 
                });
            }
        };

        // Operating System
        const OS = {
            currentView: 'grid',
            volumeDragging: false,
            
            render: function() {
                const g = document.getElementById('grid');
                g.innerHTML = '';
                
                // Apply filters
                let filtered = [...Data.list];
                
                // Category filter
                if(Data.currentFilter !== 'all') {
                    filtered = filtered.filter(item => item.category === Data.currentFilter);
                }
                
                // Favorites filter
                if(Data.favoritesOnly) {
                    filtered = filtered.filter(item => item.favorite);
                }
                
                // Sort
                if(Data.currentSort === 'alpha') {
                    filtered.sort((a, b) => a.t.localeCompare(b.t));
                } else if(Data.currentSort === 'recent') {
                    filtered.sort((a, b) => b.addedDate - a.addedDate);
                } else if(Data.currentSort === 'watched') {
                    filtered.sort((a, b) => b.watched - a.watched);
                }
                
                // Empty state
                if(filtered.length === 0) {
                    const emp = document.createElement('div');
                    emp.className = 'card add-new';
                    emp.onclick = () => this.modal('add');
                    emp.innerHTML = '<i class="fas fa-plus fa-3x"></i><p style="margin-top: 12px; font-size: 1.1rem;">Ajouter une vidéo</p>';
                    g.appendChild(emp);
                    return;
                }

                // Render cards
                filtered.forEach(item => {
                    const d = document.createElement('div');
                    d.className = 'card';
                    const img = item.i || `https://via.placeholder.com/300x450/222/fff?text=${encodeURIComponent(item.t)}`;
                    
                    // Badge
                    let badge = '';
                    const isNew = (Date.now() - item.addedDate) < (7 * 24 * 60 * 60 * 1000); // 7 days
                    if(isNew) {
                        badge = '<div class="card-badge new"><i class="fas fa-star"></i> Nouveau</div>';
                    } else if(item.watched) {
                        badge = '<div class="card-badge watched"><i class="fas fa-check-circle"></i> Visionné</div>';
                    }
                    
                    // Progress bar
                    let progress = '';
                    if(item.progress > 0 && item.progress < 100) {
                        progress = `<div class="card-progress"><div class="card-progress-bar" style="width: ${item.progress}%"></div></div>`;
                    }
                    
                    d.innerHTML = `
                        <div class="card-bg">
                            ${badge}
                            <div class="card-actions">
                                <div class="card-action-btn favorite ${item.favorite ? 'active' : ''}" 
                                     onclick="event.stopPropagation(); Data.toggleFavorite('${item.id}')">
                                    <i class="fas fa-heart"></i>
                                </div>
                                <div class="card-action-btn" 
                                     onclick="event.stopPropagation(); Data.markAsWatched('${item.id}')">
                                    <i class="fas fa-${item.watched ? 'eye-slash' : 'eye'}"></i>
                                </div>
                                <div class="card-action-btn" 
                                     onclick="event.stopPropagation(); Data.deleteItem('${item.id}')">
                                    <i class="fas fa-trash"></i>
                                </div>
                            </div>
                            <img src="${img}" onerror="this.src='https://via.placeholder.com/300x450/222/fff?text=Erreur'" loading="lazy">
                            ${progress}
                            <div class="card-details">
                                <h3>${item.t}</h3>
                                <p>${item.category || 'Non catégorisé'}</p>
                                <div class="card-meta">
                                    <span><i class="fas fa-${item.type === 'cloud' ? 'cloud' : 'hdd'}"></i> ${item.type === 'cloud' ? 'Drive' : 'Local'}</span>
                                    ${item.favorite ? '<span><i class="fas fa-heart" style="color: #FF2D55;"></i> Favori</span>' : ''}
                                </div>
                            </div>
                        </div>
                    `;
                    d.onclick = () => this.play(item);
                    g.appendChild(d);
                });
            },
            
            play: function(item) {
                let s = item.u;
                if(item.type === 'cloud' && !s.startsWith('http')) {
                    s = `https://drive.google.com/file/d/${s}/preview`;
                }
                document.getElementById('iframe').src = s;
                document.getElementById('player-title').innerText = item.t;
                document.getElementById('player').style.display = 'block';
                
                // Mark as watched after 5 seconds
                setTimeout(() => {
                    if(!item.watched) {
                        Data.markAsWatched(item.id);
                    }
                }, 5000);
            },
            
            closePlayer: function() {
                document.getElementById('player').style.display = 'none';
                document.getElementById('iframe').src = '';
            },
            
            filter: function() {
                const v = document.getElementById('search').value.toLowerCase();
                document.querySelectorAll('.card:not(.add-new)').forEach(c => {
                    const text = c.innerText.toLowerCase();
                    c.style.display = text.includes(v) ? '' : 'none';
                });
            },
            
            reset: function() {
                document.getElementById('search').value = '';
                Data.currentFilter = 'all';
                Data.favoritesOnly = false;
                this.render();
            },
            
            setView: function(view) {
                this.currentView = view;
                const grid = document.getElementById('grid');
                const buttons = document.querySelectorAll('.view-toggle button');
                
                if(view === 'list') {
                    grid.classList.add('list-view');
                    buttons[0].classList.remove('active');
                    buttons[1].classList.add('active');
                } else {
                    grid.classList.remove('list-view');
                    buttons[0].classList.add('active');
                    buttons[1].classList.remove('active');
                }
            },
            
            sortBy: function(method) {
                Data.currentSort = method;
                this.render();
                this.closeModal('sort');
                
                const labels = {
                    recent: 'Plus récents',
                    alpha: 'Ordre alphabétique',
                    watched: 'Visionnés'
                };
                Toast.show(`Trié par: ${labels[method]}`, 'info');
            },
            
            filterByCategory: function(category) {
                Data.currentFilter = category;
                this.render();
                this.closeModal('categories');
                
                // Update active tag
                document.querySelectorAll('.filter-tag').forEach(tag => {
                    tag.classList.remove('active');
                });
                event.target.classList.add('active');
            },
            
            toggleFavoritesOnly: function() {
                Data.favoritesOnly = !Data.favoritesOnly;
                this.render();
                const btn = event.currentTarget;
                if(Data.favoritesOnly) {
                    btn.classList.add('active');
                    Toast.show('Affichage des favoris uniquement', 'info');
                } else {
                    btn.classList.remove('active');
                    Toast.show('Affichage de toutes les vidéos', 'info');
                }
            },
            
            modal: (id) => { 
                const m = document.getElementById('modal-'+id);
                m.style.display = 'flex'; 
                setTimeout(() => m.classList.add('visible'), 10);
                
                // Update stats if opening stats modal
                if(id === 'stats') {
                    OS.updateStats();
                }
                
                // Update storage info if opening settings
                if(id === 'settings') {
                    const size = new Blob([localStorage.getItem('keib_diamond') || '']).size;
                    document.getElementById('storage-size').innerText = (size / 1024).toFixed(2) + ' KB';
                    document.getElementById('video-count').innerText = Data.list.length;
                }
            },
            
            closeModal: (id) => {
                const m = document.getElementById('modal-'+id);
                m.classList.remove('visible');
                setTimeout(() => m.style.display='none', 300);
            },
            
            updateStats: function() {
                document.getElementById('stat-total').innerText = Data.list.length;
                document.getElementById('stat-favorites').innerText = Data.list.filter(i => i.favorite).length;
                document.getElementById('stat-watched').innerText = Data.list.filter(i => i.watched).length;
                
                const categories = new Set(Data.list.map(i => i.category).filter(c => c));
                document.getElementById('stat-categories').innerText = categories.size;
            },
            
            // Volume control
            startVolume: function(e) {
                this.volumeDragging = true;
                this.setVolume(e);
            },
            
            dragVolume: function(e) {
                if(this.volumeDragging) {
                    this.setVolume(e);
                }
            },
            
            setVolume: function(e) {
                const track = e.currentTarget.querySelector('.vol-track');
                const rect = track.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const pct = Math.min(100, Math.max(0, (x / rect.width) * 100));
                document.getElementById('vol-fill').style.width = pct + '%';
            },
            
            fullscreen: function() {
                if(!document.fullscreenElement) {
                    document.documentElement.requestFullscreen();
                } else if(document.exitFullscreen) {
                    document.exitFullscreen();
                }
            }
        };

        // Toast Notifications
        const Toast = {
            show: function(message, type = 'info') {
                const container = document.getElementById('toast-container');
                const toast = document.createElement('div');
                toast.className = `toast ${type}`;
                
                const icons = {
                    success: 'fa-check-circle',
                    error: 'fa-exclamation-circle',
                    info: 'fa-info-circle'
                };
                
                toast.innerHTML = `
                    <i class="fas ${icons[type]} toast-icon"></i>
                    <span>${message}</span>
                `;
                
                container.appendChild(toast);
                
                setTimeout(() => {
                    toast.style.opacity = '0';
                    toast.style.transform = 'translateX(400px)';
                    setTimeout(() => toast.remove(), 400);
                }, 3000);
            }
        };

        // Global mouse up for volume
        document.addEventListener('mouseup', () => {
            OS.volumeDragging = false;
        });

        // Clock & Date Update
        setInterval(() => {
            const n = new Date();
            document.getElementById('clock-txt').innerText = n.toLocaleTimeString('fr-FR');
            document.getElementById('date-txt').innerText = n.toLocaleDateString('fr-FR', {
                day: '2-digit', 
                month: '2-digit', 
                year: '2-digit'
            });
        }, 1000);

        // Battery Status
        if(navigator.getBattery) {
            navigator.getBattery().then(b => {
                const update = () => {
                    const level = Math.round(b.level * 100);
                    document.getElementById('batt-txt').innerText = level + '%';
                    const inDiv = document.getElementById('batt-in');
                    inDiv.style.width = level + '%';
                    
                    if(b.charging) {
                        inDiv.style.background = 'linear-gradient(90deg, var(--success), #34C759)';
                    } else if(level < 20) {
                        inDiv.style.background = 'linear-gradient(90deg, var(--danger), #FF6B35)';
                    } else {
                        inDiv.style.background = 'linear-gradient(90deg, #30D158, #34C759)';
                    }
                };
                b.addEventListener('levelchange', update); 
                b.addEventListener('chargingchange', update); 
                update();
            });
        }

        // Initialize on load
        window.onload = () => { 
            Data.init(); 
            Geo.fetchWeather();
            Toast.show('Bienvenue sur Keibstream OS! ✨', 'success');
        };

        // Prevent context menu
        document.addEventListener('contextmenu', e => e.preventDefault());
    </script>
</body>
</html>
