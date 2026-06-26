<html lang="ar" dir="rtl"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | معماري تفاعلي</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --main-dark: #050811; /* لون أسود عميق وفخم */
            --card-glass: rgba(13, 20, 38, 0.65); /* تأثير زجاجي داكن */
            --accent-color: #10b981; /* أخضر زمردي يرمز للاستدامة المعمارية */
            --accent-glow: rgba(16, 185, 129, 0.3);
            --vodafone-color: #e60000;
            --text-primary: #f8fafc;
            --text-secondary: #94a3b8;
        }
        
        * {
            box-sizing: border-box;
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        body {
            font-family: 'Cairo', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--main-dark);
            /* خلفية شبكية هندسية تشبه لوحات الأوتوكاد والريفت */
            background-image: 
                linear-gradient(rgba(255, 255, 255, 0.015) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255, 255, 255, 0.015) 1px, transparent 1px);
            background-size: 35px 35px;
            color: var(--text-primary);
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* الهيدر والمكعب المعماري ثلاثي الأبعاد */
        header {
            position: relative;
            padding: 100px 20px 60px 20px;
            text-align: center;
            background: radial-gradient(circle at top, #0f172a 0%, var(--main-dark) 80%);
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
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
        }
        header h1 {
            margin: 25px 0 0 0;
            font-size: 3rem;
            font-weight: 700;
            background: linear-gradient(to left, #ffffff, #a7f3d0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        header p {
            margin: 12px 0 0 0;
            font-size: 1.25rem;
            color: var(--text-secondary);
            font-weight: 300;
            max-width: 600px;
        }

        /* حاوية الأزرار العلوية */
        .top-nav-bar {
            position: absolute;
            top: 20px;
            left: 20px;
            right: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 100;
        }

        /* أيقونة القائمة المنسحبة من اليسار */
        .menu-toggle-btn {
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.1);
            width: 42px;
            height: 42px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            backdrop-filter: blur(10px);
        }
        .menu-toggle-btn:hover {
            background: rgba(16, 185, 129, 0.2);
            border-color: var(--accent-color);
            box-shadow: 0 0 15px var(--accent-glow);
        }
        .menu-toggle-btn svg {
            width: 22px;
            height: 22px;
            fill: none;
            stroke: #ffffff;
            stroke-width: 2;
        }

        /* زر تسجيل الدخول الخاص بالمنصة */
        .auth-container {
            display: flex;
            align-items: center;
        }
        .custom-auth-btn {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(16, 185, 129, 0.1);
            border: 1px solid rgba(16, 185, 129, 0.3);
            padding: 8px 18px;
            border-radius: 50px;
            cursor: pointer;
            backdrop-filter: blur(10px);
            color: #ffffff;
            font-family: 'Cairo', sans-serif;
            font-size: 0.9rem;
            font-weight: 600;
        }
        .custom-auth-btn:hover {
            background: rgba(16, 185, 129, 0.25);
            border-color: var(--accent-color);
            box-shadow: 0 0 15px var(--accent-glow);
            transform: translateY(-2px);
        }
        .custom-auth-btn svg {
            width: 18px;
            height: 18px;
            stroke: var(--accent-color);
            fill: none;
            stroke-width: 2;
        }
        
        /* حالة المستخدم بعد تسجيل الدخول للموقع */
        .user-profile {
            display: none;
            align-items: center;
            gap: 12px;
            background: var(--card-glass);
            padding: 6px 16px;
            border-radius: 50px;
            border: 1px solid rgba(16, 185, 129, 0.4);
        }
        .user-avatar-initials {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: var(--accent-color);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 0.95rem;
            box-shadow: 0 0 10px var(--accent-glow);
        }
        .user-name {
            font-size: 0.9rem;
            font-weight: 600;
            color: #ffffff;
        }
        .logout-btn {
            background: none;
            border: none;
            color: #ef4444;
            cursor: pointer;
            font-weight: 700;
            font-size: 0.9rem;
            padding: 0 4px;
        }

        /* حقول إدخال لوحة التسجيل والاشتراك المخصصة */
        .input-group {
            text-align: right;
            margin-bottom: 18px;
        }
        .input-group label {
            display: block;
            color: var(--text-secondary);
            font-size: 0.9rem;
            margin-bottom: 6px;
            font-weight: 600;
        }
        .input-group input {
            width: 100%;
            padding: 12px;
            background: rgba(5, 8, 17, 0.7);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            color: white;
            font-family: 'Cairo', sans-serif;
            font-size: 0.95rem;
        }
        .input-group input:focus {
            border-color: var(--accent-color);
            outline: none;
            box-shadow: 0 0 10px rgba(16, 185, 129, 0.2);
        }
        .submit-auth-btn {
            width: 100%;
            padding: 12px;
            background: var(--accent-color);
            color: white;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            font-family: 'Cairo', sans-serif;
            margin-top: 10px;
        }
        .submit-auth-btn:hover {
            background: #059669;
            box-shadow: 0 5px 15px var(--accent-glow);
        }
        .toggle-auth-text {
            margin-top: 15px;
            font-size: 0.9rem;
            color: var(--text-secondary);
        }
        .toggle-auth-text a {
            color: var(--accent-color);
            text-decoration: none;
            font-weight: 600;
        }

        /* القائمة الجانبية المنسحبة من اليسار */
        .side-drawer {
            position: fixed;
            top: 0;
            left: -320px;
            width: 300px;
            height: 100%;
            background: rgba(5, 8, 17, 0.92);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-right: 1px solid rgba(255, 255, 255, 0.05);
            z-index: 2000;
            padding: 40px 24px;
            display: flex;
            flex-direction: column;
            gap: 40px;
            box-shadow: 20px 0 50px rgba(0, 0, 0, 0.8);
        }
        .side-drawer.open {
            left: 0;
        }
        .drawer-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
            padding-bottom: 15px;
        }
        .drawer-title {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--accent-color);
        }
        .close-drawer-btn {
            background: transparent;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .close-drawer-btn svg {
            width: 24px;
            height: 24px;
            stroke: var(--text-secondary);
            stroke-width: 2;
        }

        /* مسارات وروابط القائمة */
        .drawer-menu {
            list-style: none;
            padding: 0;
            margin: 0;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        .drawer-item a {
            display: flex;
            align-items: center;
            gap: 15px;
            color: #cbd5e1;
            text-decoration: none;
            font-size: 1.1rem;
            font-weight: 600;
            padding: 12px 16px;
            border-radius: 12px;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid transparent;
        }
        .drawer-item a:hover {
            color: #ffffff;
            background: rgba(16, 185, 129, 0.1);
            border-color: rgba(16, 185, 129, 0.3);
            padding-right: 22px;
        }
        .drawer-item svg {
            width: 20px;
            height: 20px;
            stroke: var(--accent-color);
            stroke-width: 2;
            fill: none;
        }

        /* غطاء خلفي عند فتح القائمة */
        .drawer-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(4px);
            z-index: 1999;
        }
        .drawer-overlay.show {
            display: block;
        }

        /* مشهد ومجسم المكعب 3D */
        .cube-scene {
            width: 100px;
            height: 100px;
            perspective: 400px;
            margin-bottom: 10px;
        }
        .cube {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            animation: rotateCube 14s infinite linear;
        }
        .cube-face {
            position: absolute;
            width: 100px;
            height: 100px;
            border: 1.5px solid var(--accent-color);
            background: rgba(16, 185, 129, 0.1);
            box-shadow: inset 0 0 15px rgba(16, 185, 129, 0.2);
        }
        .face-front  { transform: rotateY(0deg) translateZ(50px); }
        .face-back   { transform: rotateY(180deg) translateZ(50px); }
        .face-right  { transform: rotateY(90deg) translateZ(50px); }
        .face-left   { transform: rotateY(-90deg) translateZ(50px); }
        .face-top    { transform: rotateX(90deg) translateZ(50px); }
        .face-bottom { transform: rotateX(-90deg) translateZ(50px); }

        @keyframes rotateCube {
            0% { transform: rotateX(0deg) rotateY(0deg); }
            100% { transform: rotateX(360deg) rotateY(360deg); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
        }
        
        /* قسم نبذة عني */
        .about-section {
            background: var(--card-glass);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            margin-bottom: 60px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-right: 5px solid var(--accent-color);
        }
        .about-section h2 {
            color: #ffffff;
            margin-top: 0;
            font-size: 1.8rem;
            margin-bottom: 15px;
        }
        .about-section p {
            font-size: 1.1rem;
            color: #cbd5e1;
            margin: 0;
        }

        /* العناوين الرئيسية للأقسام */
        .section-title {
            text-align: center;
            margin-top: 60px;
            margin-bottom: 10px;
            font-size: 2.2rem;
            color: #ffffff;
            font-weight: 700;
        }
        .section-subtitle {
            text-align: center;
            color: var(--text-secondary);
            font-size: 1.1rem;
            margin-bottom: 45px;
            font-weight: 300;
        }
        .section-title::after {
            content: '';
            display: block;
            width: 50px;
            height: 4px;
            background: var(--accent-color);
            border-radius: 2px;
            margin: 12px auto 0 auto;
            box-shadow: 0 0 10px var(--accent-color);
        }

        /* قسم مهاراتي */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-bottom: 60px;
        }
        .skill-card {
            background: rgba(30, 41, 59, 0.3);
            color: #e2e8f0;
            padding: 20px;
            border-radius: 14px;
            text-align: center;
            font-weight: 600;
            border: 1px solid rgba(255, 255, 255, 0.03);
        }
        .skill-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            background: rgba(16, 185, 129, 0.08);
            box-shadow: 0 10px 25px var(--accent-glow);
        }

        /* معرض صور المشاريع المنفذة (مشروعين متباعدين بشكل ممتاز ومتناسق) */
        .photo-gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 60px;
            justify-content: center;
            margin-bottom: 60px;
        }

        .circle-project {
            position: relative;
            width: 260px;
            height: 260px;
            border-radius: 50%;
            overflow: hidden;
            border: 3px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
            cursor: pointer;
        }
        
        .circle-project img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .circle-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(5, 8, 17, 0.88);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            opacity: 0;
            color: #34d399;
            font-weight: 700;
            font-size: 1.3rem;
            border-radius: 50%;
            padding: 20px;
            text-align: center;
        }
        .circle-overlay span {
            font-size: 0.85rem;
            color: var(--text-secondary);
            margin-top: 8px;
            font-weight: 400;
        }
        
        .circle-project:hover {
            transform: scale(1.05) translateY(-8px);
            border-color: var(--accent-color);
            box-shadow: 0 0 35px var(--accent-glow);
        }
        
        .circle-project:hover .circle-overlay {
            opacity: 1;
        }

        /* حاوية بطاقة فودافون كاش */
        .payment-status-container {
            text-align: center; 
            margin: 60px auto; 
            max-width: 340px;
        }
        .payment-card {
            background: rgba(230, 0, 0, 0.04); 
            border: 1px solid rgba(230, 0, 0, 0.2); 
            padding: 30px 20px; 
            border-radius: 24px; 
            box-shadow: 0 15px 35px rgba(230, 0, 0, 0.03), inset 0 0 20px rgba(230, 0, 0, 0.05);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 14px;
            cursor: pointer;
        }
        .payment-card:hover {
            transform: translateY(-5px) scale(1.02);
            border-color: var(--vodafone-color);
            background: rgba(230, 0, 0, 0.08);
            box-shadow: 0 20px 40px rgba(230, 0, 0, 0.15);
        }
        .wallet-icon-glow {
            width: 65px; 
            height: 65px; 
            background: var(--vodafone-color); 
            border-radius: 50%; 
            display: flex; 
            align-items: center; 
            justify-content: center;
            box-shadow: 0 0 25px rgba(230, 0, 0, 0.45);
        }
        .wallet-icon-glow svg {
            width: 32px; 
            height: 32px; 
            fill: none; 
            stroke: #ffffff; 
            stroke-width: 2;
        }
        .payment-text-main {
            color: #ffffff; 
            font-size: 1.15rem; 
            font-weight: 600;
            margin: 0;
        }

        /* قسم التواصل عبر واتساب */
        .contact-section {
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.4) 0%, rgba(5, 8, 17, 0.6) 100%);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            padding: 80px 20px;
            text-align: center;
            border-radius: 24px;
            margin-top: 40px;
        }
        .contact-container {
            max-width: 600px;
            margin: 0 auto;
        }
        .contact-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 15px;
            color: #ffffff;
        }
        .contact-desc {
            color: var(--text-secondary);
            margin-bottom: 35px;
            font-size: 1.1rem;
        }
        .whatsapp-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            background-color: #25d366;
            color: white;
            padding: 16px 45px;
            font-size: 1.2rem;
            font-weight: 700;
            text-decoration: none;
            border-radius: 50px;
            box-shadow: 0 10px 25px rgba(37, 211, 102, 0.3);
        }
        .whatsapp-link:hover {
            transform: scale(1.05) translateY(-3px);
            background-color: #20ba5a;
            box-shadow: 0 15px 30px rgba(37, 211, 102, 0.4);
        }

        /* النوافذ المنبثقة العامة (Modals) */
        .modal {
            display: none;
            position: fixed;
            z-index: 3000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(4, 6, 11, 0.88);
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
        }
        .modal-content {
            background-color: #0f172a;
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 35px;
            border-radius: 24px;
            width: 90%;
            max-width: 450px;
            text-align: center;
            box-shadow: 0 30px 60px rgba(0,0,0,0.6);
        }
        .close-btn {
            background: rgba(255, 255, 255, 0.05);
            color: #94a3b8;
            border: 1px solid rgba(255, 255, 255, 0.05);
            width: 100%;
            padding: 12px;
            border-radius: 10px;
            cursor: pointer;
            font-weight: 600;
            margin-top: 15px;
            font-family: 'Cairo', sans-serif;
        }
        .close-btn:hover {
            background: rgba(255, 255, 255, 0.1);
            color: #ffffff;
        }

        /* تصميم الألبوم والـ Slider للمشاريع */
        .lightbox-content {
            position: relative;
            max-width: 850px;
            width: 92%;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
        }
        .lightbox-image-container {
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 100%;
            background: #020408;
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid rgba(255,255,255,0.08);
            box-shadow: 0 25px 50px rgba(0,0,0,0.8);
        }
        .lightbox-image-container img {
            max-width: 100%;
            max-height: 72vh;
            object-fit: contain;
            display: block;
        }
        .nav-arrow {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(15, 23, 42, 0.75);
            border: 1px solid rgba(255,255,255,0.1);
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 10;
        }
        .nav-arrow:hover {
            background: var(--accent-color);
            border-color: var(--accent-color);
            box-shadow: 0 0 15px var(--accent-glow);
        }
        .prev-arrow { right: 20px; }
        .next-arrow { left: 20px; }
        .lightbox-close {
            position: absolute;
            top: -50px;
            left: 0;
            background: rgba(255,255,255,0.1);
            border: none;
            color: white;
            font-size: 1.3rem;
            cursor: pointer;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .lightbox-close:hover {
            background: #ef4444;
        }
        .lightbox-counter {
            color: var(--text-primary);
            background: rgba(255,255,255,0.05);
            padding: 6px 18px;
            border-radius: 30px;
            font-size: 0.95rem;
            font-weight: 600;
            border: 1px solid rgba(255,255,255,0.05);
        }

        footer {
            text-align: center;
            padding: 40px 20px;
            color: #475569;
            font-size: 0.95rem;
        }
    </style></head>
    
    <body>

    <div class="drawer-overlay" id="drawerOverlay" onclick="toggleDrawer(false)"></div>

    <nav class="side-drawer" id="sideDrawer">
        <div class="drawer-header">
            <div class="drawer-title">خريطة المنصة</div>
            <button class="close-drawer-btn" onclick="toggleDrawer(false)">
                <svg viewBox="0 0 24 24" fill="none"><path d="M6 18L18 6M6 6l12 12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </button>
        </div>
        <ul class="drawer-menu">
            <li class="drawer-item">
                <a href="#" onclick="toggleDrawer(false)">
                    <svg viewBox="0 0 24 24"><path d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    <span>الرئيسية</span>
                </a>
            </li>
            <li class="drawer-item">
                <a href="#about" onclick="toggleDrawer(false)">
                    <svg viewBox="0 0 24 24"><path d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    <span>نبذة عني</span>
                </a>
            </li>
            <li class="drawer-item">
                <a href="#skills" onclick="toggleDrawer(false)">
                    <svg viewBox="0 0 24 24"><path d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    <span>المهارات الهندسية</span>
                </a>
            </li>
            <li class="drawer-item">
                <a href="#gallery" onclick="toggleDrawer(false)">
                    <svg viewBox="0 0 24 24"><path d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    <span>معرض المشاريع</span>
                </a>
            </li>
            <li class="drawer-item">
                <a href="#contact" onclick="toggleDrawer(false)">
                    <svg viewBox="0 0 24 24"><path d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    <span>تواصل معي</span>
                </a>
            </li>
        </ul>
    </nav>

    <div class="top-nav-bar">
        <button class="menu-toggle-btn" onclick="toggleDrawer(true)" title="افتح القائمة">
            <svg viewBox="0 0 24 24">
                <path d="M4 6h16M4 12h16M4 18h16" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </button>

        <div class="auth-container">
            <button class="custom-auth-btn" id="authBtn" onclick="openAuthModal()">
                <svg viewBox="0 0 24 24">
                    <path d="M11 16l-4-4m0 0l4-4m-4 4h14m-5 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h7a3 3 0 013 3v1" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                <span>تسجيل الدخول / الاشتراك</span>
            </button>
            
            <div class="user-profile" id="userProfile">
                <div class="user-avatar-initials" id="userInitials">U</div>
                <span class="user-name" id="userName">مرحباً بك</span>
                <button class="logout-btn" onclick="handleLogout()" title="تسجيل الخروج">✕</button>
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

        <h2 class="section-title" id="skills">مهاراتي</h2>
        <p class="section-subtitle">القدرات والخبرات الهندسية والأكاديمية</p>
        <section class="skills-grid">
            <div class="skill-card">التصميم المعماري المستدام</div>
            <div class="skill-card">التخطيط والتصميم العمراني</div>
            <div class="skill-card">تنسيق المواقع (Landscape)</div>
            <div class="skill-card">تطوير شبكات الطرق والمباني</div>
            <div class="skill-card">دمج أدوات الذكاء الاصطناعي (AI)</div>
        </section>

        <h2 class="section-title" id="gallery">معرض المشاريع المنفذة</h2>
        <p class="section-subtitle">تتكون المنصة من مشروعين رئيسيين، اضغط لتصفح الـ 5 صور الخاصة بكل مشروع بالكامل</p>
        
        <main class="photo-gallery">
            <div class="circle-project" title="مشروع معماري 1" onclick="openGalleryLightbox(1)">
                <img src="https://b.top4top.io/p_3828lnjav1.jpg" alt="مشروع معماري 1">
                <div class="circle-overlay">
                    المشروع الأول
                    <span>elharoun (يحتوي على 5 صور)</span>
                </div>
            </div>

            <div class="circle-project" title="مشروع معماري 2" onclick="openGalleryLightbox(2)">
                <img src="https://h.top4top.io/p_3828kfxcl1.jpg" alt="مشروع معماري 2">
                <div class="circle-overlay">
                    المشروع الثاني
                    <span>elharoun (يحتوي على 5 صور)</span>
                </div>
            </div>
        </main>

        <div class="payment-status-container">
            <div class="payment-card" onclick="openPaymentModal()" title="اضغط لمعرفة تفاصيل الدفع">
                <div class="wallet-icon-glow">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z" /></svg>
                </div>
                <h4 class="payment-text-main">بوابة الدفع الإلكتروني</h4>
            </div>
        </div>

        <section class="contact-section" id="contact">
            <div class="contact-container">
                <h2 class="contact-title">هل لديك مشروع ترغب في تطويره?</h2>
                <p class="contact-desc">يسعدني دائماً تواصلك لمناقشة الأفكار المعمارية وتحويلها إلى واقع مستدام.</p>
                <a href="https://wa.me/201000000000" class="whatsapp-link" target="_blank">تواصل عبر واتساب</a>
            </div>
        </section>

    </div>

    <div id="paymentModal" class="modal">
        <div class="modal-content">
            <div class="modal-header" style="font-size: 1.3rem; font-weight: 700; margin-bottom: 10px;">تفاصيل الدفع عبر فودافون كاش</div>
            <p style="color: var(--text-secondary);">يمكنك تحويل الرسوم المتفق عليها إلى الرقم التالي:</p>
            <div class="wallet-number" style="font-size: 1.8rem; font-weight: 700; color: var(--vodafone-color); margin: 15px 0; letter-spacing: 2px;">010XXXXXXXX</div>
            <button class="close-btn" onclick="closePaymentModal()">إغلاق</button>
        </div>
    </div>

    <div id="authModal" class="modal">
        <div class="modal-content" style="max-width: 400px;">
            <h3 id="authTitle" style="margin-top: 0; font-size: 1.4rem; color: #ffffff;">تسجيل الدخول للموقع</h3>
            <form id="customAuthForm" onsubmit="handleCustomAuth(event)">
                <div class="input-group" id="nameGroup" style="display: none;">
                    <label>الاسم الكامل</label>
                    <input type="text" id="authName" placeholder="أدخل اسمك الكريم">
                </div>
                <div class="input-group">
                    <label>البريد الإلكتروني أو اسم المستخدم</label>
                    <input type="text" id="authEmail" required placeholder="username / email">
                </div>
                <div class="input-group">
                    <label>كلمة المرور</label>
                    <input type="password" id="authPassword" required placeholder="••••••••">
                </div>
                <button type="submit" class="submit-auth-btn" id="authSubmitBtn">تسجيل الدخول</button>
            </form>
            <p class="toggle-auth-text">
                <span id="authToggleMsg">ليس لديك حساب؟</span> 
                <a href="javascript:void(0)" onclick="toggleAuthMode()" id="authToggleLink">إنشاء حساب جديد</a>
            </p>
            <button class="close-btn" onclick="closeAuthModal()">إغلاق</button>
        </div>
    </div>

    <div id="galleryLightbox" class="modal">
        <div class="lightbox-content">
            <button class="lightbox-close" onclick="closeGalleryLightbox()">✕</button>
            <div class="lightbox-image-container">
                <button class="nav-arrow prev-arrow" onclick="changeLightboxImage(1)">❯</button>
                <img id="lightboxImg" src="" alt="صورة المشروع المعماري">
                <button class="nav-arrow next-arrow" onclick="changeLightboxImage(-1)">❮</button>
            </div>
            <div class="lightbox-counter" id="lightboxCounter">1 / 5</div>
        </div>
    </div>

    <footer>
        <p>جميع الحقوق محفوظة © المهندس محمد الحارون 2026</p>
    </footer>

    <script>
        // إدارة فتح وإغلاق القائمة الجانبية
        function toggleDrawer(open) {
            const drawer = document.getElementById('sideDrawer');
            const overlay = document.getElementById('drawerOverlay');
            if (open) {
                drawer.classList.add('open');
                overlay.classList.add('show');
            } else {
                drawer.classList.remove('open');
                overlay.classList.remove('show');
            }
        }

        // --- نظام لوحة التسجيل الخاصة بالموقع والتحكم بأنماطها ---
        let isSignUpMode = false;

        function openAuthModal() {
            document.getElementById('authModal').style.display = 'flex';
        }
        function closeAuthModal() {
            document.getElementById('authModal').style.display = 'none';
        }

        function toggleAuthMode() {
            isSignUpMode = !isSignUpMode;
            const authTitle = document.getElementById('authTitle');
            const nameGroup = document.getElementById('nameGroup');
            const authSubmitBtn = document.getElementById('authSubmitBtn');
            const authToggleMsg = document.getElementById('authToggleMsg');
            const authToggleLink = document.getElementById('authToggleLink');
            const authNameInput = document.getElementById('authName');

            if (isSignUpMode) {
                authTitle.innerText = "إنشاء حساب جديد بالمنصة";
                nameGroup.style.display = "block";
                authNameInput.setAttribute('required', 'required');
                authSubmitBtn.innerText = "إنشاء الحساب";
                authToggleMsg.innerText = "لديك حساب بالفعل؟";
                authToggleLink.innerText = "تسجيل الدخول";
            } else {
                authTitle.innerText = "تسجيل الدخول للموقع";
                nameGroup.style.display = "none";
                authNameInput.removeAttribute('required');
                authSubmitBtn.innerText = "تسجيل الدخول";
                authToggleMsg.innerText = "ليس لديك حساب؟";
                authToggleLink.innerText = "إنشاء حساب جديد";
            }
        }

        // معالجة تسجيل الحساب والدخول داخلياً وحفظه بالذاكرة
        function handleCustomAuth(event) {
            event.preventDefault();
            const email = document.getElementById('authEmail').value;
            const name = isSignUpMode ? document.getElementById('authName').value : email.split('@')[0];

            // إخفاء زر الدخول الأولي وإظهار بروفايل المستخدم بالاسم المدخل
            document.getElementById('authBtn').style.display = 'none';
            document.getElementById('userProfile').style.display = 'flex';
            document.getElementById('userName').innerText = 'مرحباً، ' + name;
            document.getElementById('userInitials').innerText = name.charAt(0).toUpperCase();
            
            closeAuthModal();
        }

        function handleLogout() {
            document.getElementById('userProfile').style.display = 'none';
            document.getElementById('authBtn').style.display = 'flex';
            document.getElementById('customAuthForm').reset();
        }

        // --- نظام تصفح وألبوم الـ 10 صور المقسمة على مشروعين بدقة ---
        const projectGalleries = {
            1: [
                "https://b.top4top.io/p_3828lnjav1.jpg",
                "https://k.top4top.io/p_3828jbw581.jpg",
                "https://d.top4top.io/p_38285y97w1.jpg",
                "https://g.top4top.io/p_38288wnor1.jpg",
                "https://g.top4top.io/p_3828f4bqz1.jpg"
            ],
            2: [
                "https://h.top4top.io/p_3828kfxcl1.jpg",
                "https://k.top4top.io/p_3828clele1.jpg",
                "https://c.top4top.io/p_3828gvugl1.jpg",
                "https://k.top4top.io/p_3828qrim11.jpg",
                "https://b.top4top.io/p_3828lgvbq1.jpg"
            ]
        };

        let activeProjectId = 1;
        let activeImageIndex = 0;

        function openGalleryLightbox(projectId) {
            activeProjectId = projectId;
            activeImageIndex = 0;
            updateLightboxUI();
            document.getElementById('galleryLightbox').style.display = 'flex';
        }

        function closeGalleryLightbox() {
            document.getElementById('galleryLightbox').style.display = 'none';
        }

        function changeLightboxImage(direction) {
            const imagesList = projectGalleries[activeProjectId];
            activeImageIndex += direction;
            
            // الدوران اللانهائي للصور عند الوصول للنهاية أو البداية
            if (activeImageIndex >= imagesList.length) {
                activeImageIndex = 0;
            } else if (activeImageIndex < 0) {
                activeImageIndex = imagesList.length - 1;
            }
            updateLightboxUI();
        }

        function updateLightboxUI() {
            const imagesList = projectGalleries[activeProjectId];
            document.getElementById('lightboxImg').src = imagesList[activeImageIndex];
            document.getElementById('lightboxCounter').innerText = `${activeImageIndex + 1} / ${imagesList.length}`;
        }

        // تحكم مودال الدفع
        function openPaymentModal() {
            document.getElementById('paymentModal').style.display = 'flex';
        }
        function closePaymentModal() {
            document.getElementById('paymentModal').style.display = 'none';
        }
    </script>
</body>
</html>
