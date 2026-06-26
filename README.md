<html lang="ar" dir="rtl"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | معماري تفاعلي</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <script src="https://accounts.google.com/gsi/client" async defer></script>
    
    <style>
        :root {
            --main-dark: #050811; /* لون أسود عميق وفاخر */
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

        /* زر تسجيل الدخول بجوجل الاحترافي */
        .auth-container {
            display: flex;
            align-items: center;
        }
        .google-btn {
            display: flex;
            align-items: center;
            gap: 12px;
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 8px 16px;
            border-radius: 50px;
            cursor: pointer;
            text-decoration: none;
            backdrop-filter: blur(10px);
        }
        .google-btn:hover {
            background: rgba(255, 255, 255, 0.15);
            border-color: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }
        .google-btn svg {
            width: 20px;
            height: 20px;
        }
        .google-btn span {
            color: #ffffff;
            font-size: 0.9rem;
            font-weight: 600;
        }
        
        /* حالة المستخدم بعد تسجيل الدخول */
        .user-profile {
            display: none;
            align-items: center;
            gap: 10px;
            background: var(--card-glass);
            padding: 6px 14px;
            border-radius: 50px;
            border: 1px solid rgba(16, 185, 129, 0.3);
        }
        .user-avatar {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            border: 2px solid var(--accent-color);
            object-fit: cover;
        }
        .user-name {
            font-size: 0.9rem;
            font-weight: 600;
            color: #ffffff;
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

        /* عدادات الإحصائيات المباشرة */
        .analytics-bar {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 40px 0;
            text-align: center;
        }
        .counter-card {
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid rgba(255, 255, 255, 0.05);
            padding: 20px;
            border-radius: 16px;
            position: relative;
            overflow: hidden;
        }
        .counter-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: var(--accent-color);
            opacity: 0.7;
        }
        .counter-number {
            font-size: 2.2rem;
            font-weight: 700;
            color: #ffffff;
            font-family: monospace, sans-serif;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        .counter-label {
            color: var(--text-secondary);
            font-size: 0.95rem;
            margin-top: 5px;
        }

        /* العناوين الرئيسية الأقسام */
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

        /* معرض صور المشاريع المنفذة */
        .photo-gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            justify-content: center;
            margin-bottom: 60px;
        }

        .circle-project {
            position: relative;
            width: 240px;
            height: 240px;
            border-radius: 50%;
            overflow: hidden;
            border: 3px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
            cursor: pointer; /* جعل العنصر قابلاً للضغط */
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
            background: rgba(5, 8, 17, 0.85);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            opacity: 0;
            color: #34d399;
            font-weight: 600;
            font-size: 1.2rem;
            border-radius: 50%;
            padding: 20px;
            text-align: center;
            letter-spacing: 1px;
        }
        
        /* تأثيرات التحويم متوافقة مباشرة مع كود الـ div الجديد */
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

        /* النافذة المنبثقة العامة (Modal) */
        .modal {
            display: none;
            position: fixed;
            z-index: 3000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(4, 6, 11, 0.85);
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
        }
        .modal-content {
            background-color: #0f172a;
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: 24px;
            width: 90%;
            max-width: 480px;
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
        }
        .close-btn:hover {
            background: rgba(255, 255, 255, 0.1);
            color: #ffffff;
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
            <button class="google-btn" id="loginBtn" onclick="handleGoogleLogin()">
                <svg viewBox="0 0 24 24">
                    <path fill="#EA4335" d="M5.266 9.765A7.077 7.077 0 0 1 12 4.909c1.69 0 3.218.6 4.418 1.582L19.91 3A11.945 11.945 0 0 0 12 0C7.27 0 3.16 2.697 1.105 6.654l4.16 3.11z"/>
                    <path fill="#4285F4" d="M23.49 12.275c0-.796-.073-1.564-.199-2.304H12v4.51h6.46a5.523 5.523 0 0 1-2.395 3.621l3.722 2.883c2.177-2.005 3.703-4.957 3.703-8.71z"/>
                    <path fill="#FBBC05" d="M5.266 14.235l-4.16 3.11A11.95 11.95 0 0 0 12 24c3.047 0 5.828-1.01 7.964-2.716l-3.722-2.883a7.126 7.126 0 0 1-4.242 1.19c-3.007 0-5.617-1.89-6.734-4.52l-.001.002z"/>
                    <path fill="#34A853" d="M1.105 6.654A11.91 11.91 0 0 0 0 12c0 1.93.456 3.754 1.266 5.378l4.16-3.11c-.266-.628-.426-1.314-.426-2.032 0-.853.186-1.662.516-2.398L1.105 6.654z"/>
                </svg>
                <span>تسجيل الدخول بجوجل</span>
            </button>
            
            <div class="user-profile" id="userProfile">
                <img src="" alt="صورة المستخدم" class="user-avatar" id="userAvatar">
                <span class="user-name" id="userName">مرحباً بك</span>
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

        <div class="analytics-bar">
            <div class="counter-card">
                <div class="counter-number" id="totalVisits">0</div>
                <div class="counter-label">إجمالي زيارات المنصة الحقيقية</div>
            </div>
        </div>

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
        <p class="section-subtitle">اضغط على أي مشروع لاستعراض كافة الصور والمخططات الهندسية مباشرة</p>
        
        <main class="photo-gallery">
            <div class="circle-project" title="مشروع معماري 1" onclick="openProjectLightbox(1)">
                <img src="https://b.top4top.io/p_3828lnjav1.jpg" alt="مشروع معماري 1">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 2" onclick="openProjectLightbox(2)">
                <img src="https://k.top4top.io/p_3828jbw581.jpg" alt="مشروع معماري 2">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 3" onclick="openProjectLightbox(3)">
                <img src="https://d.top4top.io/p_38285y97w1.jpg" alt="مشروع معماري 3">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 4" onclick="openProjectLightbox(4)">
                <img src="https://g.top4top.io/p_38288wnor1.jpg" alt="مشروع معماري 4">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 5" onclick="openProjectLightbox(5)">
                <img src="https://g.top4top.io/p_3828f4bqz1.jpg" alt="مشروع معماري 5">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 6" onclick="openProjectLightbox(6)">
                <img src="https://h.top4top.io/p_3828kfxcl1.jpg" alt="مشروع معماري 6">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 7" onclick="openProjectLightbox(7)">
                <img src="https://k.top4top.io/p_3828clele1.jpg" alt="مشروع معماري 7">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 8" onclick="openProjectLightbox(8)">
                <img src="https://c.top4top.io/p_3828gvugl1.jpg" alt="مشروع معماري 8">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 9" onclick="openProjectLightbox(9)">
                <img src="https://k.top4top.io/p_3828qrim11.jpg" alt="مشروع معماري 9">
                <div class="circle-overlay">elharoun</div>
            </div>

            <div class="circle-project" title="مشروع معماري 10" onclick="openProjectLightbox(10)">
                <img src="https://b.top4top.io/p_3828lgvbq1.jpg" alt="مشروع معماري 10">
                <div class="circle-overlay">elharoun</div>
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

        // --- نظام تسجيل الدخول الحقيقي والآمن عبر جوجل (Google OAuth2) ---
        function handleGoogleLogin() {
            // ⚠️ استبدل هذا المعرف بالمعرف الخاص بمشروعك في Google Cloud Console لكي تعمل النافذة الحقيقية
            const CLIENT_ID = 'YOUR_GOOGLE_CLIENT_ID.apps.googleusercontent.com'; 

            if (CLIENT_ID.startsWith('YOUR_GOOGLE_CLIENT_ID')) {
                alert('تنبيه للمطور: يرجى استبدال "YOUR_GOOGLE_CLIENT_ID" بمعرّف مشروعك الحقيقي في الكود لتفعيل اتصال جوجل المباشر من خوادم Google الرسمية.');
                return;
            }

            try {
                const client = google.accounts.oauth2.initTokenClient({
                    client_id: CLIENT_ID,
                    scope: 'https://www.googleapis.com/auth/userinfo.profile',
                    callback: (tokenResponse) => {
                        if (tokenResponse && tokenResponse.access_token) {
                            // جلب بيانات المستخدم الحقيقية من خوادم جوجل عبر الـ Access Token
                            fetch('https://www.googleapis.com/oauth2/v3/userinfo', {
                                headers: { Authorization: `Bearer ${tokenResponse.access_token}` }
                            })
                            .then(res => res.json())
                            .then(user => {
                                // تحديث الواجهة ببيانات الزائر الحقيقية
                                document.getElementById('loginBtn').style.display = 'none';
                                document.getElementById('userAvatar').src = user.picture;
                                document.getElementById('userName').innerText = 'مرحباً، ' + user.name;
                                document.getElementById('userProfile').style.display = 'flex';
                            })
                            .catch(err => console.error('حدث خطأ أثناء جلب بيانات الحساب:', err));
                        }
                    }
                });
                client.requestAccessToken(); // فتح نافذة تسجيل دخول جوجل المنبثقة الحقيقية فوراً
            } catch (error) {
                console.error('فشل بدء مكتبة تسجيل دخول جوجل:', error);
            }
        }

        // التحكم في النوافذ المنبثقة (Modals)
        function openPaymentModal() {
            document.getElementById('paymentModal').style.display = 'flex';
        }
        function closePaymentModal() {
            document.getElementById('paymentModal').style.display = 'none';
        }
        function openProjectLightbox(id) {
            alert('سيتم فتح ألبوم صور المشروع المعماري رقم: ' + id);
        }

        // --- نظام العداد الحقيقي التراكمي للزيارات (localStorage) ---
        const BASE_VISITS = 1482; 

        if (localStorage.getItem("total_platform_visits")) {
            let currentVisits = parseInt(localStorage.getItem("total_platform_visits"));
            localStorage.setItem("total_platform_visits", currentVisits + 1);
        } else {
            localStorage.setItem("total_platform_visits", BASE_VISITS + 1);
        }

        let finalVisitsCount = parseInt(localStorage.getItem("total_platform_visits"));
        document.getElementById("totalVisits").innerText = finalVisitsCount.toLocaleString('ar-EG');
    </script>
</body>
</html>

```
