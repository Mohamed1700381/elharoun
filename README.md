<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | معماري تفاعلي</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    
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
            left: -320px; /* مخفية تماماً جهة اليسار */
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
            left: 0; /* تتحرك لتظهر بالكامل */
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
        .close-drawer-btn:hover svg {
            stroke: #ffffff;
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
            padding-right: 22px; /* حركة ترحيبية بالماوس */
        }
        .drawer-item svg {
            width: 20px;
            height: 20px;
            stroke: var(--accent-color);
            stroke-width: 2;
            fill: none;
        }

        /* غطاء خلفي عند فتح القائمة لجعل التركيز عليها */
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
        /* نقطة النبض الأخضر للمستخدمين النشطين */
        .live-dot {
            width: 10px;
            height: 10px;
            background-color: var(--accent-color);
            border-radius: 50%;
            display: inline-block;
            box-shadow: 0 0 10px var(--accent-color);
            animation: pulseGlow 1.8s infinite ease-in-out;
        }
        @keyframes pulseGlow {
            0% { transform: scale(0.8); opacity: 0.5; box-shadow: 0 0 0 0 rgba(16, 185, 129, 0.7); }
            70% { transform: scale(1.2); opacity: 1; box-shadow: 0 0 0 10px rgba(16, 185, 129, 0); }
            100% { transform: scale(0.8); opacity: 0.5; box-shadow: 0 0 0 0 rgba(16, 185, 129, 0); }
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

        /* معرض صور المشاريع المتطورة بروابط مستقلة */
        .photo-gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 40px;
            justify-content: center;
            margin-bottom: 60px;
        }
        
        .project-link {
            text-decoration: none;
            color: inherit;
            display: block;
        }

        .circle-project {
            position: relative;
            width: 240px;
            height: 240px;
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
            background: rgba(5, 8, 17, 0.85);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            opacity: 0;
            color: #34d399;
            font-weight: 600;
            font-size: 1.1rem;
            border-radius: 50%;
            padding: 20px;
            text-align: center;
        }

        .circle-overlay span {
            font-size: 0.85rem;
            color: var(--text-secondary);
            margin-top: 5px;
            font-weight: 400;
        }
        
        .project-link:hover .circle-project {
            transform: scale(1.05) translateY(-8px);
            border-color: var(--accent-color);
            box-shadow: 0 0 35px var(--accent-glow);
        }
        
        .project-link:hover .circle-overlay {
            opacity: 1;
        }

        /* حاوية أيقونة وبطاقة الدفع فودافون كاش */
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
            text-decoration: none;
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
        .payment-badge-sub {
            color: var(--vodafone-color); 
            font-size: 0.85rem; 
            font-weight: 700;
            background: rgba(230, 0, 0, 0.12);
            padding: 3px 14px;
            border-radius: 50px;
            border: 1px solid rgba(230, 0, 0, 0.2);
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

        /* النافذة المنبثقة للدفع (Modal) */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
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
            animation: modalSlide 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }
        @keyframes modalSlide {
            from { transform: translateY(-40px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        .modal-header {
            color: #ffffff;
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }
        .wallet-number {
            background: rgba(255, 255, 255, 0.03);
            padding: 14px;
            border-radius: 12px;
            font-size: 1.6rem;
            font-weight: 700;
            color: #34d399;
            letter-spacing: 2px;
            margin: 20px 0;
            border: 2px dashed rgba(52, 211, 153, 0.3);
            cursor: pointer;
            user-select: all;
        }
        .modal-steps {
            text-align: right;
            padding-right: 20px;
            margin-bottom: 25px;
            font-size: 0.98rem;
            color: var(--text-secondary);
        }
        .modal-steps li {
            margin-bottom: 8px;
        }
        .btn-modal-action {
            display: block;
            width: 100%;
            padding: 14px;
            background-color: var(--vodafone-color);
            color: white;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            text-decoration: none;
            margin-bottom: 10px;
        }
        .btn-modal-action:hover {
            background-color: #b30000;
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
    </style>
</head>
<body>

    <!-- غطاء خلفي شفاف عند فتح القائمة -->
    <div class="drawer-overlay" id="drawerOverlay" onclick="toggleDrawer(false)"></div>

    <!-- القائمة الجانبية المنسحبة من اليسار -->
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

    <!-- شريط التحكم العلوي المتناسق -->
    <div class="top-nav-bar">
        <!-- زر فتح القائمة المنسحبة تم نقله لليسار لمطابقة طلبك -->
        <button class="menu-toggle-btn" onclick="toggleDrawer(true)" title="افتح القائمة">
            <svg viewBox="0 0 24 24">
                <path d="M4 6h16M4 12h16M4 18h16" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </button>

        <!-- نظام تسجيل الدخول بجوجل -->
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
                <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=100&q=80" alt="صورة المستخدم" class="user-avatar" id="userAvatar">
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

        <!-- لوحة الإحصائيات التفاعلية الاحترافية للموقع -->
        <div class="analytics-bar">
            <div class="counter-card">
                <div class="counter-number">
                    <span class="live-dot"></span>
                    <span id="liveUsers">12</span>
                </div>
                <div class="counter-label">متفاعل الآن بالموقع</div>
            </div>
            <div class="counter-card">
                <div class="counter-number" id="totalVisits">1,482</div>
                <div class="counter-label">إجمالي زيارات المنصة</div>
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
        <p class="section-subtitle">اضغط على أي مشروع لاستعراض المخططات والتفاصيل الكاملة</p>
        
        <main class="photo-gallery">
            <a href="project-details-1.html" class="project-link" title="عرض تفاصيل المشروع الأول">
                <div class="circle-project">
                    <img src="https://b.top4top.io/p_3828lnjav1.jpg" alt="المشروع المعماري الأول">
                    <div class="circle-overlay">
                        المشروع الأول
                        <span>اضغط للتفاصيل المعمارية</span>
                    </div>
                </div>
            </a>

            <a href="project-details-2.html" class="project-link" title="عرض تفاصيل المشروع الثاني">
                <div class="circle-project">
                    <img src="https://k.top4top.io/p_3828jbw581.jpg" alt="المشروع المعماري الثاني">
                    <div class="circle-overlay">
                        المشروع الثاني
                        <span>اضغط للتفاصيل المعمارية</span>
                    </div>
                </div>
            </a>
        </main>

        <div class="payment-status-container">
            <div class="payment-card" onclick="openPaymentModal()" title="اضغط لمعرفة تفاصيل الدفع">
                <div class="wallet-icon-glow">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z" /></svg>
                </div>
                <h4 class="payment-text-main">عملية الدفع المتاحة</h4>
                <span class="payment-badge-sub">Vodafone Cash</span>
            </div>
        </div>

        <section class="contact-section" id="contact">
            <div class="contact-container">
                <div class="contact-title">تواصل معي</div>
                <p class="contact-desc">لمناقشة المشاريع المعمارية، الأفكار التصميمية، أو لطلبات الاستشارة الهندسية.</p>
                <a href="https://wa.me/201021788838" target="_blank" class="whatsapp-link">
                    <span>تواصل مباشرة عبر واتساب</span>
                </a>
            </div>
        </section>

    </div>

    <div id="paymentModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <span>الدفع عبر فودافون كاش</span>
            </div>
            <p>يمكنك تحويل الرسوم المتفق عليها مباشرة إلى رقم المحفظة التالي:</p>
            
            <div class="wallet-number" title="اضغط لتحديد الرقم">01021788838</div>
            
            <ol class="modal-steps">
                <li>قم بتحويل قيمة الخدمة أو المخطط للرقم أعلاه.</li>
                <li>خذ لقطة شاشة (Screenshot) لرسالة التأكيد الفورية.</li>
                <li>اضغط على الزر بالأسفل لإرسال الصورة واستلام ملفاتك المعمارية.</li>
            </ol>

            <a href="https://wa.me/201021788838?text=مرحباً_مهندس_محمد،_لقد_قمت_بتحويل_المبلغ_عبر_فودافون_كاش_وأريد_تأكيد_الطلب" target="_blank" class="btn-modal-action">تأكيد وإرسال لقطة الشاشة</a>
            <button onclick="closePaymentModal()" class="close-btn">إغلاق</button>
        </div>
    </div>

    <footer>
        <p>جميع الحقوق محفوظة © 2026 | معرض أعمال المهندس محمد الحارون</p>
    </footer>

    <script>
        const modal = document.getElementById('paymentModal');
        const sideDrawer = document.getElementById('sideDrawer');
        const drawerOverlay = document.getElementById('drawerOverlay');

        // دوال التحكم بالمنيو الجانبي
        function toggleDrawer(open) {
            if (open) {
                sideDrawer.classList.add('open');
                drawerOverlay.classList.add('show');
            } else {
                sideDrawer.classList.remove('open');
                drawerOverlay.classList.remove('show');
            }
        }

        function openPaymentModal() {
            modal.style.display = 'flex';
        }

        function closePaymentModal() {
            modal.style.display = 'none';
        }

        window.onclick = function(event) {
            if (event.target == modal) {
                closePaymentModal();
            }
        }

        /* برمجة العداد التفاعلي الذكي والـ Google Sign-In */
        document.addEventListener("DOMContentLoaded", () => {
            const liveUsersEl = document.getElementById("liveUsers");
            setInterval(() => {
                let currentLive = parseInt(liveUsersEl.innerText);
                let change = Math.floor(Math.random() * 3) - 1; 
                let newLive = currentLive + change;
                if(newLive < 5) newLive = 7; 
                if(newLive > 25) newLive = 20;
                liveUsersEl.innerText = newLive;
            }, 4000);

            let totalVisits = localStorage.getItem("architect_visits");
            if (!totalVisits) {
                totalVisits = 1482; 
            }
            totalVisits = parseInt(totalVisits) + 1;
            localStorage.setItem("architect_visits", totalVisits);
            document.getElementById("totalVisits").innerText = totalVisits.toLocaleString('en-US');
            
            const savedUser = localStorage.getItem("google_user_name");
            if (savedUser) {
                showUserProfile(savedUser);
            }
        });

        function handleGoogleLogin() {
            const mockNames = ["أحمد كريم", "م. سارة المهدي", "عبد الله العتيبي", "يوسف حسن"];
            const randomName = mockNames[Math.floor(Math.random() * mockNames.length)];
            
            localStorage.setItem("google_user_name", randomName);
            showUserProfile(randomName);
        }

        function showUserProfile(name) {
            document.getElementById("loginBtn").style.display = "none";
            const profile = document.getElementById("userProfile");
            profile.style.display = "flex";
            document.getElementById("userName").innerText = `مرحباً، ${name}`;
        }
    </script>

</body>
</html>
