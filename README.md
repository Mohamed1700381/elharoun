<html lang="ar" dir="rtl"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | معماري تفاعلي</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght=300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --main-dark: #030712; 
            --card-glass: rgba(17, 24, 39, 0.7); 
            --accent-color: #10b981; 
            --accent-glow: rgba(16, 185, 129, 0.25);
            --vodafone-color: #e60000;
            --text-primary: #f9fafb;
            --text-secondary: #9ca3af;
            --error-color: #ef4444;
        }
        
        * {
            box-sizing: border-box;
            transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
        }

        body {
            font-family: 'Cairo', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--main-dark);
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(16, 185, 129, 0.05) 0%, transparent 80%),
                linear-gradient(rgba(255, 255, 255, 0.01) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255, 255, 255, 0.01) 1px, transparent 1px);
            background-size: 100% 100%, 40px 40px, 40px 40px;
            color: var(--text-primary);
            line-height: 1.8;
            overflow-x: hidden;
        }

        /* مؤشر الماوس المعماري المخصص */
        .custom-cursor {
            width: 20px;
            height: 20px;
            border: 2px solid var(--accent-color);
            border-radius: 50%;
            position: fixed;
            transform: translate(-50%, -50%);
            pointer-events: none;
            z-index: 9999;
            mix-blend-mode: difference;
            display: none;
        }
        @media (min-width: 1024px) {
            .custom-cursor { display: block; }
        }

        /* الهيدر السريالي المعزز */
        header {
            position: relative;
            padding: 140px 20px 80px 20px;
            text-align: center;
            background: radial-gradient(circle at top, #111827 0%, var(--main-dark) 100%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }
        header::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(16, 185, 129, 0.4), transparent);
        }

        header h1 {
            margin: 30px 0 0 0;
            font-size: 3.5rem;
            font-weight: 700;
            letter-spacing: -1px;
            background: linear-gradient(to left, #ffffff 30%, #34d399 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        header p {
            margin: 15px 0 0 0;
            font-size: 1.3rem;
            color: var(--text-secondary);
            font-weight: 300;
            max-width: 700px;
        }

        .top-nav-bar {
            position: absolute;
            top: 25px;
            left: 25px;
            right: 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 100;
        }

        .menu-toggle-btn {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.08);
            width: 46px;
            height: 46px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            backdrop-filter: blur(12px);
        }
        .menu-toggle-btn:hover {
            background: rgba(16, 185, 129, 0.15);
            border-color: var(--accent-color);
            box-shadow: 0 0 20px var(--accent-glow);
        }
        .menu-toggle-btn svg {
            width: 24px;
            height: 24px;
            stroke: #ffffff;
            stroke-width: 2;
        }

        .auth-container { display: flex; align-items: center; }
        .custom-auth-btn {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(16, 185, 129, 0.05);
            border: 1px solid rgba(16, 185, 129, 0.2);
            padding: 10px 22px;
            border-radius: 14px;
            cursor: pointer;
            backdrop-filter: blur(12px);
            color: #ffffff;
            font-family: 'Cairo', sans-serif;
            font-size: 0.95rem;
            font-weight: 600;
        }
        .custom-auth-btn:hover {
            background: rgba(16, 185, 129, 0.15);
            border-color: var(--accent-color);
            box-shadow: 0 0 20px var(--accent-glow);
            transform: translateY(-2px);
        }
        .custom-auth-btn svg {
            width: 18px;
            height: 18px;
            stroke: var(--accent-color);
            fill: none;
            stroke-width: 2;
        }
        
        .user-profile {
            display: none;
            align-items: center;
            gap: 12px;
            background: rgba(17, 24, 39, 0.85);
            padding: 8px 18px;
            border-radius: 14px;
            border: 1px solid rgba(16, 185, 129, 0.3);
        }
        .user-avatar-initials {
            width: 34px;
            height: 34px;
            border-radius: 10px;
            background: linear-gradient(135deg, var(--accent-color), #059669);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
        }
        .logout-btn {
            background: rgba(239, 68, 68, 0.1);
            border: 1px solid rgba(239, 68, 68, 0.2);
            color: #ef4444;
            cursor: pointer;
            width: 24px;
            height: 24px;
            border-radius: 6px;
            display: flex; align-items: center; justify-content: center;
        }
        .logout-btn:hover { background: #ef4444; color: white; }

        /* حاسبة التكلفة الذكية التفاعلية */
        .calculator-section {
            background: var(--card-glass);
            border: 1px solid rgba(255,255,255,0.05);
            border-radius: 24px; padding: 40px;
            max-width: 650px; margin: 60px auto;
            backdrop-filter: blur(15px);
        }
        .calc-grid {
            display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 25px;
        }
        .calc-field label {
            display: block; font-size: 0.95rem; color: var(--text-secondary); margin-bottom: 8px; font-weight: 600;
        }
        .calc-field select, .calc-field input {
            width: 100%; padding: 14px; background: rgba(5,8,17,0.7);
            border: 1px solid rgba(255,255,255,0.08); border-radius: 12px;
            color: white; font-family: 'Cairo'; font-size: 0.95rem;
        }
        .calc-field select:focus, .calc-field input:focus {
            border-color: var(--accent-color); outline: none;
        }
        .calc-full-width {
            grid-column: span 2; margin-top: 10px;
        }
        .outputs-checkbox-group {
            display: grid; grid-template-columns: 1fr 1fr; gap: 12px; background: rgba(5,8,17,0.4); padding: 15px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.05);
        }
        .output-item {
            display: flex; align-items: center; gap: 10px; cursor: pointer; color: var(--text-primary); font-size: 0.9rem;
        }
        .output-item input {
            width: auto; accent-color: var(--accent-color); cursor: pointer;
        }
        .calc-result-box {
            background: rgba(16, 185, 129, 0.05); border: 1px solid rgba(16, 185, 129, 0.15);
            padding: 20px; border-radius: 16px; text-align: center; margin-top: 30px;
        }
        .calc-price {
            font-size: 2rem; font-weight: 700; color: var(--accent-color); margin: 10px 0;
        }

        /* بقية التصاميم الأساسية المحسنة */
        .container { max-width: 1200px; margin: 0 auto; padding: 40px 20px; }
        .about-section {
            background: var(--card-glass); backdrop-filter: blur(12px);
            padding: 40px; border-radius: 24px; box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            margin-bottom: 60px; border: 1px solid rgba(255, 255, 255, 0.05); border-right: 5px solid var(--accent-color);
        }
        .section-title { text-align: center; margin-top: 70px; margin-bottom: 10px; font-size: 2.4rem; color: #ffffff; font-weight: 700; }
        .section-subtitle { text-align: center; color: var(--text-secondary); font-size: 1.1rem; margin-bottom: 45px; }
        .section-title::after { content: ''; display: block; width: 60px; height: 4px; background: var(--accent-color); border-radius: 2px; margin: 12px auto 0 auto; box-shadow: 0 0 15px var(--accent-color); }

        .skills-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; margin-bottom: 60px; }
        .skill-card { background: rgba(31, 41, 55, 0.4); color: #e5e7eb; padding: 22px; border-radius: 16px; text-align: center; font-weight: 600; border: 1px solid rgba(255, 255, 255, 0.02); }
        .skill-card:hover { transform: translateY(-5px); border-color: var(--accent-color); background: rgba(16, 185, 129, 0.08); box-shadow: 0 15px 30px var(--accent-glow); }

        .photo-gallery { display: flex; flex-wrap: wrap; gap: 60px; justify-content: center; margin-bottom: 60px; }
        .circle-project { position: relative; width: 270px; height: 270px; border-radius: 50%; overflow: hidden; border: 3px solid rgba(255, 255, 255, 0.08); box-shadow: 0 20px 40px rgba(0,0,0,0.5); cursor: pointer; }
        .circle-project img { width: 100%; height: 100%; object-fit: cover; }
        .circle-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(3, 7, 18, 0.9); display: flex; flex-direction: column; align-items: center; justify-content: center; opacity: 0; color: #34d399; font-weight: 700; font-size: 1.3rem; border-radius: 50%; padding: 20px; text-align: center; }
        .circle-overlay span { font-size: 0.85rem; color: var(--text-secondary); margin-top: 8px; }
        .circle-project:hover { transform: scale(1.05) translateY(-8px); border-color: var(--accent-color); box-shadow: 0 0 40px var(--accent-glow); }
        .circle-project:hover .circle-overlay { opacity: 1; }

        .payment-status-container { text-align: center; margin: 60px auto; max-width: 340px; }
        .payment-card { background: rgba(230, 0, 0, 0.03); border: 1px solid rgba(230, 0, 0, 0.15); padding: 30px 20px; border-radius: 24px; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 14px; cursor: pointer; }
        .payment-card:hover { transform: translateY(-5px); border-color: var(--vodafone-color); background: rgba(230, 0, 0, 0.06); box-shadow: 0 20px 40px rgba(230, 0, 0, 0.15); }
        .wallet-icon-glow { width: 65px; height: 65px; background: var(--vodafone-color); border-radius: 50%; display: flex; align-items: center; justify-content: center; box-shadow: 0 0 25px rgba(230, 0, 0, 0.4); }
        .wallet-icon-glow svg { width: 32px; height: 32px; fill: none; stroke: #ffffff; stroke-width: 2; }

        .contact-section { background: radial-gradient(ellipse at bottom, #111827 0%, var(--main-dark) 100%); border: 1px solid rgba(255, 255, 255, 0.03); padding: 80px 20px; text-align: center; border-radius: 32px; margin-top: 40px; }
        .whatsapp-link { display: inline-flex; align-items: center; justify-content: center; background-color: #25d366; color: white; padding: 16px 45px; font-size: 1.2rem; font-weight: 700; text-decoration: none; border-radius: 50px; box-shadow: 0 10px 25px rgba(37, 211, 102, 0.3); }
        .whatsapp-link:hover { transform: scale(1.05) translateY(-3px); background-color: #20ba5a; box-shadow: 0 15px 30px rgba(37, 211, 102, 0.4); }

        /* النوافذ واللوحات المنبثقة */
        .modal { display: none; position: fixed; z-index: 3000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(3, 7, 18, 0.9); align-items: center; justify-content: center; backdrop-filter: blur(12px); }
        .modal-content { background-color: #0b0f19; border: 1px solid rgba(255, 255, 255, 0.08); padding: 35px; border-radius: 24px; width: 90%; max-width: 440px; text-align: center; box-shadow: 0 30px 70px rgba(0,0,0,0.8); }
        .close-btn { background: rgba(255, 255, 255, 0.04); color: #9ca3af; border: 1px solid rgba(255, 255, 255, 0.05); width: 100%; padding: 14px; border-radius: 12px; cursor: pointer; font-weight: 600; margin-top: 15px; font-family: 'Cairo'; }
        .close-btn:hover { background: rgba(255, 255, 255, 0.08); color: #ffffff; }

        .input-group { text-align: right; margin-bottom: 18px; }
        .input-group label { display: block; color: var(--text-secondary); font-size: 0.9rem; margin-bottom: 8px; font-weight: 600; }
        .input-group input { width: 100%; padding: 14px; background: rgba(5, 8, 17, 0.8); border: 1px solid rgba(255, 255, 255, 0.08); border-radius: 12px; color: white; font-family: 'Cairo'; }
        .input-group input:focus { border-color: var(--accent-color); outline: none; box-shadow: 0 0 12px rgba(16, 185, 129, 0.2); }
        
        .auth-alert { display: none; padding: 10px 14px; border-radius: 8px; font-size: 0.9rem; margin-bottom: 15px; text-align: right; font-weight: 600; }
        .auth-alert.error { display: block; background: rgba(239, 68, 68, 0.1); border: 1px solid rgba(239, 68, 68, 0.2); color: #f87171; }
        .auth-alert.success { display: block; background: rgba(16, 185, 129, 0.1); border: 1px solid rgba(16, 185, 129, 0.2); color: #34d399; }

        .submit-auth-btn { width: 100%; padding: 14px; background: linear-gradient(135deg, var(--accent-color), #059669); color: white; border: none; border-radius: 12px; font-weight: 700; font-size: 1rem; cursor: pointer; font-family: 'Cairo'; margin-top: 5px; }
        .toggle-auth-text { margin-top: 20px; font-size: 0.9rem; color: var(--text-secondary); }
        .toggle-auth-text a { color: var(--accent-color); text-decoration: none; font-weight: 600; margin-right: 5px; }

        /* القائمة الجانبية المتقدمة */
        .side-drawer { position: fixed; top: 0; left: -320px; width: 300px; height: 100%; background: rgba(5, 8, 17, 0.95); backdrop-filter: blur(20px); border-right: 1px solid rgba(255, 255, 255, 0.05); z-index: 2000; padding: 40px 24px; display: flex; flex-direction: column; gap: 40px; box-shadow: 20px 0 50px rgba(0, 0, 0, 0.8); }
        .side-drawer.open { left: 0; }
        .drawer-header { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid rgba(255, 255, 255, 0.08); padding-bottom: 15px; }
        .drawer-title { font-size: 1.2rem; font-weight: 700; color: var(--accent-color); }
        .close-drawer-btn { background: transparent; border: none; cursor: pointer; }
        .close-drawer-btn svg { width: 24px; height: 24px; stroke: var(--text-secondary); stroke-width: 2; }
        .drawer-menu { list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 15px; }
        .drawer-item a { display: flex; align-items: center; gap: 15px; color: #cbd5e1; text-decoration: none; font-size: 1.1rem; font-weight: 600; padding: 12px 16px; border-radius: 12px; background: rgba(255, 255, 255, 0.01); }
        .drawer-item a:hover { color: #ffffff; background: rgba(16, 185, 129, 0.1); padding-right: 22px; }
        .drawer-item svg { width: 20px; height: 20px; stroke: var(--accent-color); stroke-width: 2; fill: none; }
        .drawer-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.7); backdrop-filter: blur(5px); z-index: 1999; }
        .drawer-overlay.show { display: block; }

        /* مجسم المكعب ثلاثي الأبعاد */
        .cube-scene { width: 100px; height: 100px; perspective: 400px; margin-bottom: 10px; }
        .cube { width: 100%; height: 100%; position: relative; transform-style: preserve-3d; animation: rotateCube 16s infinite linear; }
        .cube-face { position: absolute; width: 100px; height: 100px; border: 1.5px solid var(--accent-color); background: rgba(16, 185, 129, 0.08); box-shadow: inset 0 0 15px rgba(16, 185, 129, 0.15); }
        .face-front  { transform: rotateY(0deg) translateZ(50px); }
        .face-back   { transform: rotateY(180deg) translateZ(50px); }
        .face-right  { transform: rotateY(90deg) translateZ(50px); }
        .face-left   { transform: rotateY(-90deg) translateZ(50px); }
        .face-top    { transform: rotateX(90deg) translateZ(50px); }
        .face-bottom { transform: rotateX(-90deg) translateZ(50px); }
        @keyframes rotateCube { 0% { transform: rotateX(0deg) rotateY(0deg); } 100% { transform: rotateX(360deg) rotateY(360deg); } }

        /* ألبوم السلايدر المطور */
        .lightbox-content { position: relative; max-width: 850px; width: 92%; display: flex; flex-direction: column; align-items: center; gap: 15px; }
        .lightbox-image-container { position: relative; display: flex; align-items: center; justify-content: center; width: 100%; background: #020408; border-radius: 20px; overflow: hidden; border: 1px solid rgba(255,255,255,0.08); }
        .lightbox-image-container img { max-width: 100%; max-height: 72vh; object-fit: contain; display: block; }
        .nav-arrow { position: absolute; top: 50%; transform: translateY(-50%); background: rgba(15, 23, 42, 0.8); border: 1px solid rgba(255,255,255,0.1); color: white; width: 50px; height: 50px; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center; }
        .nav-arrow:hover { background: var(--accent-color); box-shadow: 0 0 15px var(--accent-glow); }
        .prev-arrow { right: 20px; } .next-arrow { left: 20px; }
        .lightbox-close { position: absolute; top: -50px; left: 0; background: rgba(255,255,255,0.1); border: none; color: white; font-size: 1.2rem; cursor: pointer; width: 40px; height: 40px; border-radius: 50%; display: flex; align-items: center; justify-content: center; }
        .lightbox-counter { color: var(--text-primary); background: rgba(255,255,255,0.05); padding: 6px 20px; border-radius: 30px; font-weight: 600; }

        footer { text-align: center; padding: 40px 20px; color: #4b5563; font-size: 0.95rem; }
    </style></head>
    
    <body>

    <div class="custom-cursor" id="customCursor"></div>

    <div class="drawer-overlay" id="drawerOverlay" onclick="toggleDrawer(false)"></div>

    <nav class="side-drawer" id="sideDrawer">
        <div class="drawer-header">
            <div class="drawer-title">خريطة المنصة</div>
            <button class="close-drawer-btn" onclick="toggleDrawer(false)">
                <svg viewBox="0 0 24 24" fill="none"><path d="M6 18L18 6M6 6l12 12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </button>
        </div>
        <ul class="drawer-menu">
            <li class="drawer-item"><a href="#" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" stroke-linecap="round" stroke-linejoin="round"/></svg><span>الرئيسية</span></a></li>
            <li class="drawer-item"><a href="#about" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>نبذة عني</span></a></li>
            <li class="drawer-item"><a href="#gallery" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>معرض المشاريع</span></a></li>
            <li class="drawer-item"><a href="#calculator" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M9 7h6m0 10v-3m-3 3h.01M9 17h.01M9 14h.01M12 14h.01M15 11h.01M12 11h.01M9 11h.01M7 21h10a2 2 0 002-2V5a2 2 0 00-2-2H7a2 2 0 00-2 2v14a2 2 0 002 2z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>حاسبة التكلفة</span></a></li>
            <li class="drawer-item"><a href="#contact" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>تواصل معي</span></a></li>
        </ul>
    </nav>

    <div class="top-nav-bar">
        <button class="menu-toggle-btn" onclick="toggleDrawer(true)">
            <svg viewBox="0 0 24 24"><path d="M4 6h16M4 12h16M4 18h16" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </button>

        <div class="auth-container">
            <button class="custom-auth-btn" id="authBtn" onclick="openAuthModal()">
                <svg viewBox="0 0 24 24"><path d="M11 16l-4-4m0 0l4-4m-4 4h14m-5 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h7a3 3 0 013 3v1" stroke-linecap="round" stroke-linejoin="round"/></svg>
                <span>حسابي المحتفظ به</span>
            </button>
            <div class="user-profile" id="userProfile">
                <div class="user-avatar-initials" id="userInitials">U</div>
                <span class="user-name" id="userName">مرحباً بك</span>
                <button class="logout-btn" onclick="handleLogout()">✕</button>
            </div>
        </div>
    </div>

    <header>
        <div class="cube-scene">
            <div class="cube">
                <div class="cube-face face-front"></div>
                <div class="cube-face face-back"></div>
                <div class="cube-face face-right"></div>
                <div class="cube-face face-left"></div>
                <div class="cube-face face-top"></div>
                <div class="cube-face face-bottom"></div>
            </div>
        </div>
        <h1>المهندس المعماري / محمد الحارون</h1>
        <p>معماري | شغوف بالتخطيط العمراني، الاستدامة، وتطوير البيئة المبنية</p>
    </header>

    <div class="container">
        
        <section class="about-section" id="about">
            <h2>نبذة عني</h2>
            <p>
                معماري لديّ شغف قوي بالتصميم المعماري، التخطيط العمراني، والتنمية المستدامة. أسعى دائماً لابتكار حلول مستدامة ومبتكرة تعزز كفاءة البيئة المبنية وتلبي احتياجات المجتمع. 
                خلال مسيرتي الأكاديمية، قمت بإعداد وتطوير مشاريع متنوعة تشمل التخطيط البيئي المعماري، وتصميم لاندسكيب متكامل، بالإضافة إلى مشاريع تطوير وتحديث شبكات الطرق والمباني السكنية والإدارية والتعليمية لرفع جودة الحياة العمرانية.
            </p>
        </section>

        <h2 class="section-title" id="skills">مهاراتي ومخرجات العمل</h2>
        <section class="skills-grid">
            <div class="skill-card">مساقط أفقية دقيقة (Floor Plans)</div>
            <div class="skill-card">قطاعات رأسية وسكاشن (Sections)</div>
            <div class="skill-card">واجهات معمارية حديثة (Elevations)</div>
            <div class="skill-card">المخطط العام واللاي أوت (Layout)</div>
            <div class="skill-card">التصميم المعماري المستدام</div>
            <div class="skill-card">تنسيق المواقع (Landscape)</div>
        </section>

        <h2 class="section-title" id="gallery">معرض المشاريع المنفذة</h2>
        <p class="section-subtitle">تتكون المنصة من مشروعين رئيسيين، اضغط لتصفح الـ 5 صور الخاصة بكل مشروع بالكامل</p>
        
        <main class="photo-gallery">
            <div class="circle-project" title="مشروع معماري 1" onclick="openGalleryLightbox(1)">
                <img src="https://b.top4top.io/p_3828lnjav1.jpg" alt="مشروع معماري 1">
                <div class="circle-overlay">المشروع الأول<span>elharoun (يحتوي على 5 صور)</span></div>
            </div>
            <div class="circle-project" title="مشروع معماري 2" onclick="openGalleryLightbox(2)">
                <img src="https://h.top4top.io/p_3828kfxcl1.jpg" alt="مشروع معماري 2">
                <div class="circle-overlay">المشروع الثاني<span>elharoun (يحتوي على 5 صور)</span></div>
            </div>
        </main>

        <h2 class="section-title" id="calculator">حاسبة التكلفة المبدئية والطلبات</h2>
        <p class="section-subtitle">حدد نوع التصميم، المساحة، والمخرجات الهندسية المطلوبة للحصول على تقدير فوري</p>
        <section class="calculator-section">
            <div class="calc-grid">
                <div class="calc-field">
                    <label>نوع التصميم الرئيسي</label>
                    <select id="calcType" onchange="calculateProjectCost()">
                        <option value="50">تصميم معماري خارجي (واجهات)</option>
                        <option value="80">تصميم داخلي متكامل (Interior)</option>
                        <option value="120">تصميم معماري ولاندسكيب معاً</option>
                        <option value="40">تخطيط عمراني وتطوير شبكات</option>
                    </select>
                </div>
                <div class="calc-field">
                    <label>المساحة الإجمالية (متر مربع)</label>
                    <input type="number" id="calcArea" value="150" min="10" oninput="calculateProjectCost()">
                </div>
                
                <div class="calc-field calc-full-width">
                    <label>المخرجات والمخططات الهندسية المطلوبة (الطلبات):</label>
                    <div class="outputs-checkbox-group">
                        <label class="output-item">
                            <input type="checkbox" id="outPlan" checked onchange="calculateProjectCost()">
                            <span>مساقط أفقية (Floor Plans)</span>
                        </label>
                        <label class="output-item">
                            <input type="checkbox" id="outSection" checked onchange="calculateProjectCost()">
                            <span>قطاعات رأسية (سكاشن)</span>
                        </label>
                        <label class="output-item">
                            <input type="checkbox" id="outElevation" checked onchange="calculateProjectCost()">
                            <span>واجهات معمارية (Elevations)</span>
                        </label>
                        <label class="output-item">
                            <input type="checkbox" id="outLayout" checked onchange="calculateProjectCost()">
                            <span>المخطط العام (لاي أوت)</span>
                        </label>
                    </div>
                </div>
            </div>
            <div class="calc-result-box">
                <div style="font-weight: 600; color: var(--text-secondary);">التكلفة التقديرية المبدئية للعمل:</div>
                <div class="calc-price" id="calcPriceDisplay">12,000 ج.م</div>
                <button class="submit-auth-btn" style="background: rgba(255,255,255,0.05); color: #ffffff; border: 1px solid var(--accent-color); margin-top: 15px;" onclick="sendEstimateToWhatsapp()">مناقشة التقرير والطلبات عبر واتساب</button>
            </div>
        </section>

        <div class="payment-status-container">
            <div class="payment-card" onclick="openPaymentModal()">
                <div class="wallet-icon-glow">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z" /></svg>
                </div>
                <h4 class="payment-text-main">بوابة الدفع الإلكتروني</h4>
            </div>
        </div>

        <section class="contact-section" id="contact">
            <div class="contact-container">
                <h2 class="contact-title">هل لديك مشروع ترغب في تطويره؟</h2>
                <p class="contact-desc">يسعدني دائماً تواصلك لمناقشة الأفكار المعمارية وتحويلها إلى واقع مستدام.</p>
                <a href="https://wa.me/201050758773" class="whatsapp-link" target="_blank" id="mainWhatsappBtn">تواصل عبر واتساب</a>
            </div>
        </section>

    </div>

    <div id="paymentModal" class="modal">
        <div class="modal-content">
            <div style="font-size: 1.3rem; font-weight: 700; margin-bottom: 10px;">تفاصيل الدفع عبر فودافون كاش</div>
            <p style="color: var(--text-secondary);">يمكنك تحويل الرسوم المتفق عليها إلى الرقم التالي:</p>
            <div style="font-size: 1.8rem; font-weight: 700; color: var(--vodafone-color); margin: 15px 0; letter-spacing: 2px;">01050758773</div>
            <button class="close-btn" onclick="closePaymentModal()">إغلاق</button>
        </div>
    </div>

    <div id="authModal" class="modal">
        <div class="modal-content">
            <h3 id="authTitle" style="margin-top: 0; font-size: 1.4rem; color: #ffffff; margin-bottom: 15px;">تسجيل الدخول للموقع</h3>
            <div id="authAlert" class="auth-alert"></div>
            <form id="customAuthForm" onsubmit="handleCustomAuth(event)">
                <div class="input-group" id="nameGroup" style="display: none;">
                    <label>الاسم الكامل</label>
                    <input type="text" id="authName" placeholder="أدخل اسمك الكامل">
                </div>
                <div class="input-group">
                    <label>البريد الإلكتروني</label>
                    <input type="email" id="authEmail" required placeholder="name@example.com">
                </div>
                <div class="input-group">
                    <label>كلمة المرور الخاصة بك</label>
                    <input type="password" id="authPassword" required placeholder="••••••••">
                </div>
                <button type="submit" class="submit-auth-btn" id="authSubmitBtn">تسجيل الدخول</button>
            </form>
            <p class="toggle-auth-text">
                <span id="authToggleMsg">ليس لديك حساب؟</span> 
                <a href="javascript:void(0)" onclick="toggleAuthMode()" id="authToggleLink">إنشاء حساب جديد آمن</a>
            </p>
            <button class="close-btn" onclick="closeAuthModal()">إغلاق اللوحة</button>
        </div>
    </div>

    <div id="galleryLightbox" class="modal">
        <div class="lightbox-content">
            <button class="lightbox-close" onclick="closeGalleryLightbox()">✕</button>
            <div class="lightbox-image-container">
                <button class="nav-arrow prev-arrow" onclick="changeLightboxImage(1)">❯</button>
                <img id="lightboxImg" src="">
                <button class="nav-arrow next-arrow" onclick="changeLightboxImage(-1)">❮</button>
            </div>
            <div class="lightbox-counter" id="lightboxCounter">1 / 5</div>
        </div>
    </div>

    <footer>
        <p>جميع الحقوق محفوظة © المهندس محمد الحارون 2026</p>
    </footer>

    <script>
        // تتبع حركة الماوس المخصص للمنصة الهندسية
        const cursor = document.getElementById('customCursor');
        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
        });

        // دالة حاسبة تكاليف المشاريع المحدثة بضرب وحساب الطلبات والمخططات المعمارية
        function calculateProjectCost() {
            const costPerMeter = parseFloat(document.getElementById('calcType').value);
            const area = parseFloat(document.getElementById('calcArea').value) || 0;
            
            let baseCost = costPerMeter * area;
            
            // إضافة وزن نسبي بناءً على المخططات المختارة من العميل
            let multiplier = 0.6; // التكلفة الأساسية للفكرة ثلاثية الأبعاد بدون مخططات تفصيلية
            if (document.getElementById('outPlan').checked) multiplier += 0.15;
            if (document.getElementById('outSection').checked) multiplier += 0.10;
            if (document.getElementById('outElevation').checked) multiplier += 0.10;
            if (document.getElementById('outLayout').checked) multiplier += 0.05;
            
            const totalCost = Math.round(baseCost * multiplier);
            document.getElementById('calcPriceDisplay').innerText = totalCost.toLocaleString('ar-EG') + " ج.م";
        }

        function sendEstimateToWhatsapp() {
            const typeText = document.getElementById('calcType').options[document.getElementById('calcType').selectedIndex].text;
            const area = document.getElementById('calcArea').value;
            const price = document.getElementById('calcPriceDisplay').innerText;
            
            // تجميع المخرجات الهندسية المختارة لإرسالها في رسالة الواتساب للطلب المباشر
            let selectedOutputs = [];
            if (document.getElementById('outPlan').checked) selectedOutputs.push("مساقط أفقية");
            if (document.getElementById('outSection').checked) selectedOutputs.push("سكاشن / قطاعات");
            if (document.getElementById('outElevation').checked) selectedOutputs.push("واجهات معمارية");
            if (document.getElementById('outLayout').checked) selectedOutputs.push("المخطط العام (لاي أوت)");
            
            const outputsText = selectedOutputs.length > 0 ? selectedOutputs.join(" + ") : "تصميم بدون مخططات تفصيلية";

            const message = encodeURIComponent(`مرحباً مهندس محمد، أود طلب تصميم معماري عبر موقعك بالبيانات التالية:\n- نوع التصميم: ${typeText}\n- المساحة: ${area} متر مربع\n- الطلبات والمخرجات المطلوبة: [ ${outputsText} ]\n- التكلفة التقديرية المحسوبة: ${price}\nبرجاء مراجعة الطلب لبدء العمل المباشر.`);
            window.open(`https://wa.me/201050758773?text=${message}`, '_blank');
        }

        // الحفاظ على كود الحساب المحلي والخصوصية بدون خادم خارجي
        document.addEventListener("DOMContentLoaded", () => {
            calculateProjectCost();
            const cachedUser = localStorage.getItem('haroun_current_user');
            if (cachedUser) {
                const user = JSON.parse(cachedUser);
                applyUserLoggedInUI(user.name);
            }
        });

        function toggleDrawer(open) {
            const drawer = document.getElementById('sideDrawer');
            const overlay = document.getElementById('drawerOverlay');
            if (open) { drawer.classList.add('open'); overlay.classList.add('show'); }
            else { drawer.classList.remove('open'); overlay.classList.remove('show'); }
        }

        let isSignUpMode = false;
        function openAuthModal() { clearAlert(); document.getElementById('authModal').style.display = 'flex'; }
        function closeAuthModal() { document.getElementById('authModal').style.display = 'none'; }
        function showAlert(message, type) { const alertBox = document.getElementById('authAlert'); alertBox.innerText = message; alertBox.className = 'auth-alert ' + type; }
        function clearAlert() { const alertBox = document.getElementById('authAlert'); alertBox.innerText = ''; alertBox.className = 'auth-alert'; }

        function toggleAuthMode() {
            isSignUpMode = !isSignUpMode;
            clearAlert();
            const authTitle = document.getElementById('authTitle');
            const nameGroup = document.getElementById('nameGroup');
            const authSubmitBtn = document.getElementById('authSubmitBtn');
            const authToggleMsg = document.getElementById('authToggleMsg');
            const authToggleLink = document.getElementById('authToggleLink');

            if (isSignUpMode) {
                authTitle.innerText = "إنشاء حساب محلي آمن";
                nameGroup.style.display = "block";
                document.getElementById('authName').setAttribute('required', 'required');
                authSubmitBtn.innerText = "تفعيل وحفظ الحساب في جهازي";
                authToggleMsg.innerText = "لديك حساب محلي؟";
                authToggleLink.innerText = "تسجيل الدخول";
            } else {
                authTitle.innerText = "تسجيل الدخول للموقع";
                nameGroup.style.display = "none";
                document.getElementById('authName').removeAttribute('required');
                authSubmitBtn.innerText = "تسجيل الدخول";
                authToggleMsg.innerText = "ليس لديك حساب؟";
                authToggleLink.innerText = "إنشاء حساب جديد آمن";
            }
        }

        function handleCustomAuth(event) {
            event.preventDefault();
            clearAlert();
            const email = document.getElementById('authEmail').value.trim().toLowerCase();
            const password = document.getElementById('authPassword').value;
            let localDB = JSON.parse(localStorage.getItem('haroun_local_db')) || [];

            if (isSignUpMode) {
                const name = document.getElementById('authName').value.trim();
                if (localDB.some(user => user.email === email)) {
                    showAlert("هذا الحساب مسجل مسبقاً بجهازك!", "error"); return;
                }
                const newUser = { name, email, password };
                localDB.push(newUser);
                localStorage.setItem('haroun_local_db', JSON.stringify(localDB));
                localStorage.setItem('haroun_current_user', JSON.stringify(newUser));
                showAlert("تم حفظ الحساب بخصوصية تامة في جهازك بنجاح!", "success");
                setTimeout(() => { applyUserLoggedInUI(name); closeAuthModal(); }, 1000);
            } else {
                const matchedUser = localDB.find(user => user.email === email && user.password === password);
                if (matchedUser) {
                    localStorage.setItem('haroun_current_user', JSON.stringify(matchedUser));
                    showAlert("مرحباً بعودتك الآمنة للموقع...", "success");
                    setTimeout(() => { applyUserLoggedInUI(matchedUser.name); closeAuthModal(); }, 1000);
                } else {
                    showAlert("البيانات غير متطابقة مع المسجل محلياً في جهازي.", "error");
                }
            }
        }

        function applyUserLoggedInUI(name) {
            document.getElementById('authBtn').style.display = 'none';
            document.getElementById('userProfile').style.display = 'flex';
            document.getElementById('userName').innerText = 'مرحباً، ' + name;
            document.getElementById('userInitials').innerText = name.charAt(0).toUpperCase();
        }

        function handleLogout() {
            localStorage.removeItem('haroun_current_user');
            document.getElementById('userProfile').style.display = 'none';
            document.getElementById('authBtn').style.display = 'flex';
            document.getElementById('customAuthForm').reset();
            if(isSignUpMode) toggleAuthMode();
        }

        // سلايدر الصور
        const projectGalleries = {
            1: ["https://b.top4top.io/p_3828lnjav1.jpg", "https://k.top4top.io/p_3828jbw581.jpg", "https://d.top4top.io/p_38285y97w1.jpg", "https://g.top4top.io/p_38288wnor1.jpg", "https://g.top4top.io/p_3828f4bqz1.jpg"],
            2: ["https://h.top4top.io/p_3828kfxcl1.jpg", "https://k.top4top.io/p_3828clele1.jpg", "https://c.top4top.io/p_3828gvugl1.jpg", "https://k.top4top.io/p_3828qrim11.jpg", "https://b.top4top.io/p_3828lgvbq1.jpg"]
        };
        let activeProjectId = 1, activeImageIndex = 0;

        function openGalleryLightbox(projectId) { activeProjectId = projectId; activeImageIndex = 0; updateLightboxUI(); document.getElementById('galleryLightbox').style.display = 'flex'; }
        function closeGalleryLightbox() { document.getElementById('galleryLightbox').style.display = 'none'; }
        function changeLightboxImage(direction) { const imagesList = projectGalleries[activeProjectId]; activeImageIndex += direction; if (activeImageIndex >= imagesList.length) activeImageIndex = 0; else if (activeImageIndex < 0) activeImageIndex = imagesList.length - 1; updateLightboxUI(); }
        function updateLightboxUI() { const imagesList = projectGalleries[activeProjectId]; document.getElementById('lightboxImg').src = imagesList[activeImageIndex]; document.getElementById('lightboxCounter').innerText = `${activeImageIndex + 1} / ${imagesList.length}`; }

        function openPaymentModal() { document.getElementById('paymentModal').style.display = 'flex'; }
        function closePaymentModal() { document.getElementById('paymentModal').style.display = 'none'; }
    </script>
</body>
</html>
