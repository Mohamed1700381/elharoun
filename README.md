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
            --border-glass: rgba(255, 255, 255, 0.05);
        }
        
        * {
            box-sizing: border-box;
            transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif;
        }

        body {
            background-color: var(--main-dark);
            color: var(--text-primary);
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* الخلفية الديناميكية المضيئة */
        .bg-glows {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            z-index: -1; pointer-events: none;
            overflow: hidden;
        }
        .glow-circle {
            position: absolute;
            border-radius: 50%;
            background: radial-gradient(circle, var(--accent-glow) 0%, transparent 70%);
            filter: blur(60px);
            animation: floatGlow 12s infinite alternate ease-in-out;
        }
        .glow-1 { top: -10%; left: -10%; width: 50vw; height: 50vw; }
        .glow-2 { bottom: -10%; right: -10%; width: 60vw; height: 60vw; animation-delay: -4s; }
        .glow-3 { top: 40%; left: 50%; width: 35vw; height: 35vw; background: radial-gradient(circle, rgba(6,182,212,0.15) 0%, transparent 70%); animation-delay: -8s; }

        @keyframes floatGlow {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(4% , 6%) scale(1.15); }
        }

        /* الهيدر والبطل الرئيسي */
        header {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 2rem;
            position: relative;
        }

        .profile-container {
            position: relative;
            margin-bottom: 2rem;
        }

        .profile-pic {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--accent-color);
            box-shadow: 0 0 30px var(--accent-glow);
        }

        .badge-status {
            position: absolute;
            bottom: 5px;
            left: 5px;
            background-color: var(--accent-color);
            color: var(--main-dark);
            font-weight: 700;
            padding: 0.3rem 0.9rem;
            border-radius: 20px;
            font-size: 0.75rem;
            box-shadow: 0 4px 12px rgba(16, 185, 129, 0.4);
            animation: pulseGlow 2s infinite;
        }

        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 4px 12px rgba(16, 185, 129, 0.4); }
            50% { box-shadow: 0 4px 25px rgba(16, 185, 129, 0.8); }
        }

        header h1 {
            font-size: 3.2rem;
            font-weight: 700;
            margin-bottom: 1rem;
            letter-spacing: -1px;
            background: linear-gradient(135deg, #fff 30%, var(--accent-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        header p {
            font-size: 1.25rem;
            color: var(--text-secondary);
            max-width: 700px;
            line-height: 1.8;
            margin-bottom: 2.5rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--accent-color), #059669);
            color: var(--main-dark);
            padding: 1rem 2.5rem;
            border-radius: 12px;
            font-weight: 700;
            text-decoration: none;
            font-size: 1.1rem;
            box-shadow: 0 10px 25px rgba(16, 185, 129, 0.3);
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            border: none;
            cursor: pointer;
        }

        .btn-primary:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px var(--accent-glow);
        }

        /* التنسيق العام للأقسام */
        section {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.2rem;
            margin-bottom: 4rem;
            position: relative;
        }
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: var(--accent-color);
            border-radius: 2px;
        }

        /* بطاقات جلاس مورفيزم */
        .glass-card {
            background: var(--card-glass);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--border-glass);
            border-radius: 24px;
            padding: 2.5rem;
        }

        /* قسم نبذة عني والمهارات */
        .about-grid {
            display: grid;
            grid-template-columns: 1.5fr 1fr;
            gap: 3rem;
            align-items: start;
        }

        @media (max-width: 900px) {
            .about-grid { grid-template-columns: 1fr; }
            header h1 { font-size: 2.3rem; }
        }

        .about-text p {
            color: var(--text-secondary);
            font-size: 1.15rem;
            line-height: 1.9;
            margin-bottom: 1.5rem;
            text-align: justify;
        }

        .skills-container h3 {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            color: #fff;
        }

        .skill-item {
            margin-bottom: 1.5rem;
        }
        .skill-info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }
        .skill-bar-bg {
            width: 100%;
            height: 8px;
            background: rgba(255,255,255,0.05);
            border-radius: 4px;
            overflow: hidden;
        }
        .skill-bar-fill {
            height: 100%;
            background: var(--accent-color);
            border-radius: 4px;
            box-shadow: 0 0 10px var(--accent-color);
        }

        /* قسم الخدمات ومشاريع الطلاب */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .service-card {
            padding: 2.5rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        .service-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(180deg, transparent 70%, rgba(16, 185, 129, 0.05));
            opacity: 0;
            transition: opacity 0.4s;
        }
        .service-card:hover::before { opacity: 1; }
        .service-card:hover { transform: translateY(-8px); border-color: rgba(16, 185, 129, 0.2); }

        .service-icon {
            width: 70px; height: 70px;
            background: rgba(16, 185, 129, 0.1);
            color: var(--accent-color);
            border-radius: 20px;
            display: flex; align-items: center; justify-content: center;
            font-size: 1.8rem; font-weight: bold;
            margin: 0 auto 1.5rem;
        }
        .service-card h3 { font-size: 1.4rem; margin-bottom: 1rem; color: #fff; }
        .service-card p { color: var(--text-secondary); line-height: 1.7; font-size: 0.95rem; }

        /* معرض المشاريع الدائري والتفاعلي */
        .carousel-container {
            position: relative;
            width: 100%;
            overflow: hidden;
            padding: 2rem 0;
        }
        .carousel-track {
            display: flex;
            gap: 2rem;
            width: max-content;
            animation: scrollCarousel 40s linear infinite;
        }
        .carousel-track:hover { animation-play-state: paused; }

        @keyframes scrollCarousel {
            0% { transform: translateX(0); }
            100% { transform: translateX(50%); }
        }

        .project-card {
            width: 350px;
            height: 450px;
            border-radius: 24px;
            overflow: hidden;
            position: relative;
            cursor: pointer;
            border: 1px solid var(--border-glass);
        }

        .project-card img {
            width: 100%; height: 100%; object-fit: cover;
        }

        .project-overlay {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(0deg, rgba(3,7,18,0.95) 20%, rgba(3,7,18,0.4) 60%, transparent);
            opacity: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 2rem;
            transition: opacity 0.4s;
        }

        .project-card:hover .project-overlay { opacity: 1; }

        .project-overlay h4 { font-size: 1.5rem; color: #fff; margin-bottom: 0.5rem; text-align: center; width: 100%; }
        .project-overlay p { color: var(--accent-color); font-weight: 600; font-size: 0.95rem; text-align: center; width: 100%; }

        /* الحاسبة التقديرية المتطورة */
        .calculator-wrapper {
            max-width: 850px;
            margin: 0 auto;
        }

        .calc-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2.5rem;
            border-bottom: 1px solid var(--border-glass);
            padding-bottom: 1.5rem;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .calc-header p.estimation-note {
            width: 100%;
            color: #ef4444;
            font-size: 1.05rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            background: rgba(239, 68, 68, 0.1);
            padding: 0.5rem 1rem;
            border-radius: 8px;
            border: 1px solid rgba(239, 68, 68, 0.2);
            text-align: center;
        }

        .currency-selector select {
            background: var(--main-dark);
            color: #fff;
            border: 1px solid var(--border-glass);
            padding: 0.6rem 1.2rem;
            border-radius: 10px;
            font-weight: 600;
            cursor: pointer;
            outline: none;
        }

        .calc-body {
            display: grid;
            grid-template-columns: 1.2fr 1fr;
            gap: 3rem;
        }

        @media (max-width: 768px) {
            .calc-body { grid-template-columns: 1fr; gap: 2rem; }
        }

        .input-group {
            margin-bottom: 2rem;
        }
        .input-group label {
            display: block;
            margin-bottom: 0.8rem;
            font-weight: 600;
            color: var(--text-primary);
        }

        /* كستوم راديو تشيكس */
        .custom-select-ui {
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
        }
        .radio-option {
            position: relative;
            cursor: pointer;
        }
        .radio-option input {
            position: absolute; opacity: 0; width: 0; height: 0;
        }
        .radio-box {
            padding: 1rem 1.2rem;
            border: 1px solid var(--border-glass);
            border-radius: 14px;
            display: flex; justify-content: space-between; align-items: center;
            background: rgba(255,255,255,0.02);
        }
        .radio-option input:checked + .radio-box {
            border-color: var(--accent-color);
            background: rgba(16, 185, 129, 0.08);
        }
        .radio-title { font-weight: 600; color: #fff; }
        .radio-desc { font-size: 0.8rem; color: var(--text-secondary); margin-top: 0.2rem; }

        /* نظام الرينج */
        .range-container {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        .range-container input[type="range"] {
            flex: 1;
            accent-color: var(--accent-color);
            cursor: pointer;
        }
        .range-val {
            font-size: 1.2rem; font-weight: 700; color: var(--accent-color);
            min-width: 60px; text-align: left;
        }

        /* بطاقة عرض السعر */
        .price-display-card {
            background: rgba(255,255,255,0.02);
            border: 1px dashed rgba(16, 185, 129, 0.3);
            border-radius: 20px;
            padding: 2rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }
        .price-label { font-size: 1.1rem; color: var(--text-secondary); margin-bottom: 0.5rem; }
        .price-amount { font-size: 2.8rem; font-weight: 800; color: var(--accent-color); margin-bottom: 0.5rem; }
        .price-currency { font-size: 1.2rem; font-weight: 600; color: #fff; margin-bottom: 1.5rem; }
        
        .calc-stats {
            width: 100%;
            border-top: 1px solid var(--border-glass);
            padding-top: 1rem;
            margin-top: 1rem;
            display: flex; justify-content: space-around;
            font-size: 0.85rem; color: var(--text-secondary);
        }
        .stat-item strong { color: #fff; display: block; font-size: 1.05rem; margin-top: 0.2rem; }

        /* الجدول الزمني لخطوات العمل */
        .timeline {
            position: relative; max-width: 800px; margin: 0 auto;
            padding-right: 2rem;
        }
        .timeline::before {
            content: ''; position: absolute; top: 0; right: 7px;
            width: 2px; height: 100%; background: var(--border-glass);
        }
        .timeline-item {
            position: relative; margin-bottom: 3rem;
        }
        .timeline-dot {
            position: absolute; right: -2rem; top: 5px;
            width: 16px; height: 16px; border-radius: 50%;
            background: var(--main-dark); border: 3px solid var(--accent-color);
            box-shadow: 0 0 10px var(--accent-color);
        }
        .timeline-content h3 { font-size: 1.3rem; margin-bottom: 0.6rem; color: #fff; }
        .timeline-content p { color: var(--text-secondary); line-height: 1.7; }

        /* الأسئلة الشائعة Accordion */
        .faq-wrapper { max-width: 800px; margin: 0 auto; display: flex; flex-direction: column; gap: 1rem; }
        .faq-item { border: 1px solid var(--border-glass); border-radius: 16px; overflow: hidden; background: var(--card-glass); }
        .faq-trigger {
            width: 100%; padding: 1.5rem; background: transparent; border: none;
            text-align: right; color: #fff; font-size: 1.1rem; font-weight: 600;
            cursor: pointer; display: flex; justify-content: space-between; align-items: center;
        }
        .faq-icon { font-size: 1.3rem; color: var(--accent-color); transition: transform 0.3s; }
        .faq-content { max-height: 0; overflow: hidden; transition: max-height 0.4s ease-out, padding 0.4s; padding: 0 1.5rem; color: var(--text-secondary); line-height: 1.8; }
        .faq-item.active .faq-content { padding: 0 1.5rem 1.5rem; }
        .faq-item.active .faq-icon { transform: rotate(45deg); }

        /* بوابة الدفع فودافون كاش */
        .payment-wrapper { max-width: 600px; margin: 0 auto; text-align: center; }
        .voda-header { display: flex; align-items: center; justify-content: center; gap: 0.8rem; margin-bottom: 1.5rem; }
        .voda-logo { width: 45px; height: 45px; background: var(--vodafone-color); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: #fff; font-weight: bold; font-size: 1.4rem; }
        .voda-header h3 { font-size: 1.6rem; color: #fff; }
        .payment-wrapper p { color: var(--text-secondary); margin-bottom: 2rem; line-height: 1.7; }
        .wallet-number-box { background: rgba(230, 0, 0, 0.05); border: 1px dashed var(--vodafone-color); padding: 1.2rem; border-radius: 16px; display: inline-flex; align-items: center; gap: 1.5rem; font-size: 1.4rem; font-weight: 700; color: #fff; letter-spacing: 1px; position: relative; margin-bottom: 1.5rem; }
        .copy-btn { background: var(--vodafone-color); border: none; color: #fff; padding: 0.4rem 1rem; border-radius: 8px; font-size: 0.85rem; cursor: pointer; font-weight: 600; }
        
        /* نظام التعليقات المتطور والآمن */
        .comments-section { max-width: 850px; margin: 5rem auto 0; border-top: 1px solid var(--border-glass); padding-top: 4rem; }
        .comment-form { display: flex; flex-direction: column; gap: 1.2rem; margin-bottom: 3rem; }
        .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
        @media (max-width: 600px) { .form-row { grid-template-columns: 1fr; } }
        .comment-form input, .comment-form textarea { background: rgba(255,255,255,0.02); border: 1px solid var(--border-glass); border-radius: 12px; padding: 1rem; color: #fff; outline: none; font-size: 0.95rem; }
        .comment-form input:focus, .comment-form textarea:focus { border-color: var(--accent-color); background: rgba(255,255,255,0.04); }
        .comment-form textarea { height: 120px; resize: none; }
        .comments-list { display: flex; flex-direction: column; gap: 1.5rem; }
        .comment-node { padding: 1.5rem; background: rgba(255,255,255,0.01); border-radius: 16px; border: 1px solid var(--border-glass); }
        .comment-meta { display: flex; justify-content: space-between; margin-bottom: 0.8rem; font-size: 0.9rem; }
        .comment-user { font-weight: 700; color: var(--accent-color); }
        .comment-date { color: var(--text-secondary); }
        .comment-text { color: var(--text-primary); line-height: 1.6; }

        /* نافذة الصور المنبثقة Lightbox */
        .lightbox-modal { position: fixed; top:0; left:0; width:100%; height:100%; background: rgba(3,7,18,0.98); z-index: 2000; display: none; justify-content: center; align-items: center; }
        .lightbox-content { position: relative; max-width: 90%; max-height: 85%; display: flex; flex-direction: column; align-items: center; }
        .lightbox-content img { max-width: 100%; max-height: 75vh; border-radius: 12px; box-shadow: 0 0 50px rgba(0,0,0,0.8); object-fit: contain; }
        .lightbox-close { position: absolute; top: -50px; left: 0; font-size: 2rem; color: #fff; cursor: pointer; background: transparent; border: none; }
        .lightbox-nav { position: absolute; top: 50%; transform: translateY(-50%); width: calc(100% + 100px); display: flex; justify-content: space-between; pointer-events: none; }
        @media (max-width: 1100px) { .lightbox-nav { width: 100%; padding: 0 1rem; position: static; transform: none; margin-top: 1rem; pointer-events: auto; } }
        .nav-arrow { width: 50px; height: 50px; background: rgba(255,255,255,0.05); border: 1px solid var(--border-glass); border-radius: 50%; color: #fff; display: flex; align-items: center; justify-content: center; cursor: pointer; font-size: 1.3rem; pointer-events: auto; font-weight: bold; }
        .nav-arrow:hover { background: var(--accent-color); color: var(--main-dark); }
        .lightbox-caption { margin-top: 1.5rem; text-align: center; color: var(--text-secondary); }
        #lightboxCounter { font-size: 0.85rem; color: var(--accent-color); margin-top: 0.3rem; font-weight: 600; }

        /* الفوتر المتناسق */
        footer { text-align: center; padding: 4rem 2rem; border-top: 1px solid var(--border-glass); color: var(--text-secondary); font-size: 0.9rem; }
        footer strong { color: var(--accent-color); }
    </style>
</head>
<body>

    <div class="bg-glows">
        <div class="glow-circle glow-1"></div>
        <div class="glow-circle glow-2"></div>
        <div class="glow-circle glow-3"></div>
    </div>

    <header>
        <div class="profile-container">
            <img src="https://j.top4top.io/p_328325n741.jpg" alt="محمد الحارون" class="profile-pic">
            <span class="badge-status">متاح للمشاريع</span>
        </div>
        <h1>المهندس المعماري / محمد الحارون</h1>
        <p>طالب هندسة معمارية بجامعة سيناء ومتبقي سنتين على التخرج | متخصص في المشاريع الهندسية المعمارية فقط لا غير</p>
        <a href="#calculator" class="btn-primary">احسب تكلفة مشروعك الآن</a>
    </header>

    <section id="about" class="glass-card">
        <h2 class="section-title">من أنا</h2>
        <div class="about-grid">
            <div class="about-text">
                <p>
                    طالب في جامعة سيناء بمرحلة الهندسة المعمارية ومتبقي سنتين على تخرجي. متخصص في المشاريع الهندسية المعمارية فقط لا غير. قمت بتنفيذ وإعداد مشاريع معمارية بالتعاون مع الدكاترة بالجامعة، وتطوير المخططات باستخدام برامج AutoCAD وRevit وD5 Render وPhotoshop، مع مساعدة طلاب كليات الهندسة والعمارة في إنهاء وإخراج مشاريعهم الدراسية والتخرج بأعلى جودة ممكنة.
                </p>
            </div>
            <div class="skills-container">
                <h3>الأدوات والبرامج الأساسية</h3>
                <div class="skill-item">
                    <div class="skill-info"><span>AutoCAD</span><span>95%</span></div>
                    <div class="skill-bar-bg"><div class="skill-bar-fill" style="width: 95%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-info"><span>Revit Architecture</span><span>90%</span></div>
                    <div class="skill-bar-bg"><div class="skill-bar-fill" style="width: 90%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-info"><span>D5 Render</span><span>88%</span></div>
                    <div class="skill-bar-bg"><div class="skill-bar-fill" style="width: 88%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-info"><span>Adobe Photoshop</span><span>85%</span></div>
                    <div class="skill-bar-bg"><div class="skill-bar-fill" style="width: 85%"></div></div>
                </div>
            </div>
        </div>
    </section>

    <section id="services">
        <h2 class="section-title">الخدمات المعمارية للطلاب</h2>
        <div class="services-grid">
            <div class="service-card glass-card">
                <div class="service-icon">01</div>
                <h3>تطوير المساقط والمخططات</h3>
                <p>رسم وتعديل المخططات المعمارية بالكامل على أوتوكاد وريفت وتوزيع الفراغات الداخلية بدقة طبقاً للمتطلبات والمعايير الأكاديمية.</p>
            </div>
            <div class="service-card glass-card">
                <div class="service-icon">02</div>
                <h3>النمذجة ثلاثية الأبعاد 3D</h3>
                <p>تحويل اللوحات ثنائية الأبعاد إلى مجسمات فراغية تفصيلية كاملة ومبهرة عبر برنامجي Revit و D5 Render لإيضاح الفكرة التصميمية.</p>
            </div>
            <div class="service-card glass-card">
                <div class="service-icon">03</div>
                <h3>الإظهار والبوسترات الدراسية</h3>
                <p>رندر لقطات داخلية وخارجية شديدة الواقعية، وتنسيق شاسيهات وبوستر المشروع (Presentation Sheets) بالفوتوشوب بأعلى مستوى تنظيمي وبصري.</p>
            </div>
        </div>
    </section>

    <section id="portfolio">
        <h2 class="section-title">معرض المشاريع والكتل</h2>
        <div class="carousel-container">
            <div class="carousel-track" id="carouselTrack">
                <div class="project-card" onclick="openGalleryLightbox(1)">
                    <img src="https://g.top4top.io/p_3283v7jfe1.jpg" alt="المشروع الأول">
                    <div class="project-overlay">
                        <h4>مشروع التصميم المستدام</h4>
                        <p>تصفح ألبوم الصور بالكامل</p>
                    </div>
                </div>
                <div class="project-card" onclick="openGalleryLightbox(2)">
                    <img src="https://h.top4top.io/p_3828kfxcl1.jpg" alt="المشروع الثاني">
                    <div class="project-overlay">
                        <h4>مشروع التخطيط الحضري</h4>
                        <p>تصفح ألبوم الصور بالكامل</p>
                    </div>
                </div>
                <div class="project-card" onclick="openGalleryLightbox(1)">
                    <img src="https://h.top4top.io/p_328325n741.jpg" alt="المشروع الثالث">
                    <div class="project-overlay">
                        <h4>الكتل واللاندسكيب</h4>
                        <p>تصفح ألبوم الصور بالكامل</p>
                    </div>
                </div>
                <div class="project-card" onclick="openGalleryLightbox(1)">
                    <img src="https://g.top4top.io/p_3283v7jfe1.jpg" alt="المشروع الأول">
                    <div class="project-overlay">
                        <h4>مشروع التصميم المستدام</h4>
                        <p>تصفح ألبوم الصور بالكامل</p>
                    </div>
                </div>
                <div class="project-card" onclick="openGalleryLightbox(2)">
                    <img src="https://h.top4top.io/p_3828kfxcl1.jpg" alt="المشروع الثاني">
                    <div class="project-overlay">
                        <h4>مشروع التخطيط الحضري</h4>
                        <p>تصفح ألبوم الصور بالكامل</p>
                    </div>
                </div>
                <div class="project-card" onclick="openGalleryLightbox(1)">
                    <img src="https://h.top4top.io/p_328325n741.jpg" alt="المشروع الثالث">
                    <div class="project-overlay">
                        <h4>الكتل واللاندسكيب</h4>
                        <p>تصفح ألبوم الصور بالكامل</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="calculator" class="glass-card">
        <div class="calculator-wrapper">
            <div class="calc-header">
                <p class="estimation-note">يرجى العلم: هذه الحاسبة هي حاسبة تقديرية وليس أكثر لتوفير قراءة مبدئية للتكلفة المتوقعة لمشروعك.</p>
                <h2>حاسبة التكلفة التقديرية</h2>
                <div class="currency-selector">
                    <select id="currencySelect" onchange="calculateProjectPrice()">
                        <option value="EGP">الجنيه المصري (EGP)</option>
                        <option value="USD">الدولار الأمريكي (USD)</option>
                        <option value="SAR">الريال السعودي (SAR)</option>
                    </select>
                </div>
            </div>
            
            <div class="calc-body">
                <div class="calc-inputs">
                    <div class="input-group">
                        <label>نوع الخدمة المطلوبة:</label>
                        <div class="custom-select-ui">
                            <label class="radio-option">
                                <input type="radio" name="serviceType" value="20" checked onchange="calculateProjectPrice()">
                                <div class="radio-box">
                                    <div>
                                        <div class="radio-title">رسم ثنائي الأبعاد 2D ومساقط</div>
                                        <div class="radio-desc">أوتوكاد وريفت بدون ريندر وتلوين</div>
                                    </div>
                                </div>
                            </label>
                            <label class="radio-option">
                                <input type="radio" name="serviceType" value="45" onchange="calculateProjectPrice()">
                                <div class="radio-box">
                                    <div>
                                        <div class="radio-title">نمذجة 3D وريندر وإظهار</div>
                                        <div class="radio-desc">لقطات واقعية ممتازة بـ D5 ريندر وفوتوشوب</div>
                                    </div>
                                </div>
                            </label>
                            <label class="radio-option">
                                <input type="radio" name="serviceType" value="60" onchange="calculateProjectPrice()">
                                <div class="radio-box">
                                    <div>
                                        <div class="radio-title">مشروع متكامل (2D + 3D + شاسيهات)</div>
                                        <div class="radio-desc">تسليم أكاديمي شامل وجاهز للتحكيم والمناقشة</div>
                                    </div>
                                </div>
                            </label>
                        </div>
                    </div>

                    <div class="input-group">
                        <label>مساحة المشروع الإجمالية (متر مربع):</label>
                        <div class="range-container">
                            <input type="range" id="areaRange" min="50" max="1000" step="10" value="150" oninput="updateAreaValue(this.value)">
                            <div class="range-val" id="areaVal">150 م²</div>
                        </div>
                    </div>
                </div>

                <div class="calc-results">
                    <div class="price-display-card">
                        <span class="price-label">التكلفة التقديرية المقترحة</span>
                        <div class="price-amount" id="totalPriceDisplay">3,000</div>
                        <div class="price-currency" id="currencyLabel">جنيه مصري</div>
                        
                        <div class="calc-stats">
                            <div class="stat-item">زمن التنفيذ المقدر<strong id="timeStat">4-6 أيام</strong></div>
                            <div class="stat-item">التعديلات المجانية<strong id="revisionsStat">3 تعديلات</strong></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="workflow">
        <h2 class="section-title">خطوات سير العمل الهندسي</h2>
        <div class="timeline">
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>1. دراسة الفكرة والاشتراطات دكتور المادة</h3>
                    <p>نبدأ بمراجعة كود وجدول طلبات المشروع وملاحظات الدكاترة والمعيدين بالكلية لضمان عدم الخروج عن الإطار المحدد للمادة.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>2. العمل الأولي والمخططات الخطية</h3>
                    <p>إعداد الخطوط الأولية والمساقط ثنائية الأبعاد (Layouts & Plans) وإرسالها لك لمراجعتها مع دكتورك قبل الدخول في التفاصيل المتقدمة.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>3. النمذجة والإخراج البصري النهائي</h3>
                    <p>رفع المشروع 3D ورندرة اللقطات المطلوبة وتجميع لوحات المشروع وتنسيقها لتكون جاهزة للطباعة الفورية بجودة وبكسل عالي.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="faq">
        <h2 class="section-title">أسئلة متكررة للطلاب</h2>
        <div class="faq-wrapper">
            <div class="faq-item">
                <button class="faq-trigger" onclick="toggleFaq(this)">
                    <span>هل تلتزم بملاحظات الدكاترة والمعيدين الخاصة بجامعتي؟</span>
                    <span class="faq-icon">+</span>
                </button>
                <div class="faq-content">
                    <p>نعم، تماماً. العمل المعماري يعتمد بشكل كلي على الاشتراطات والطلبات المحددة التي يفرضها دكاترة المادة بملف المشروع (Project Brief)، ويتم تعديل وتوجيه العمل خطوة بخطوة لضمان التوافق التام مع رؤيتهم المعمارية ونيل الدرجات العالية.</p>
                </div>
            </div>
            <div class="faq-item">
                <button class="faq-trigger" onclick="toggleFaq(this)">
                    <span>ماذا لو طلب الدكتور تعديلاً مفاجئاً بعد تسليم المشروع؟</span>
                    <span class="faq-icon">+</span>
                </button>
                <div class="faq-content">
                    <p>أوفر نظاماً مرناً للتعديلات والمراجعات؛ حيث تتضمن الخدمة باقة مخصصة من التعديلات المجانية والمدفوعة لمعالجة وتحديث أي ملاحظات تظهر في مراحل تسليم المشروع الأسبوعية (الكراتين والـ Juries).</p>
                </div>
            </div>
        </div>
    </section>

    <section id="payment" class="glass-card">
        <div class="payment-wrapper">
            <div class="voda-header">
                <div class="voda-logo">V</div>
                <h3>بوابة الدفع الإلكتروني السريع</h3>
            </div>
            <p>لتسهيل الإجراءات وحجز مواعيد العمل والمشاريع المعمارية، يمكنك تحويل الدفعات المقررة أو جدولة قيمتها مباشرة عبر محفظة فودافون كاش الرسمية التالية:</p>
            
            <div class="wallet-number-box">
                <span id="vodaNumber">01095340634</span>
                <button class="copy-btn" onclick="copyVodafoneNumber()">نسخ الرقم</button>
            </div>
            <div style="color: var(--text-secondary); font-size: 0.85rem; margin-top: 0.5rem;">بعد إتمام التحويل، يرجى إرسال لقطة شاشة التأكيد للبدء المباشر.</div>
        </div>
    </section>

    <section id="comments" class="glass-card">
        <h2 class="section-title">آراء الطلاب والزوار</h2>
        <div class="comments-section">
            <div class="comment-form">
                <div class="form-row">
                    <input type="text" id="commenterName" placeholder="الاسم الكريم أو اسم جامعتك" required>
                    <input type="text" id="commenterSubject" placeholder="المشروع المعماري المستهدف">
                </div>
                <textarea id="commenterText" placeholder="اكتب هنا رأيك في الخدمات المعمارية أو تجربتك معنا..." required></textarea>
                <button class="btn-primary" style="padding: 0.8rem 2rem; align-self: flex-start; font-size: 1rem;" onclick="submitNewVisitorComment()">نشر التعليق الآن</button>
            </div>

            <div class="comments-list" id="commentsDisplayContainer">
                <div class="comment-node">
                    <div class="comment-meta">
                        <span class="comment-user">أحمد مصطفى (هندسة حلوان)</span>
                        <span class="comment-date">منذ يومين</span>
                    </div>
                    <div class="comment-text">شغل رائع جداً، الالتزام بالوقت ودقة لوحات الأوتوكاد والريفت ساعدتني في إقناع الدكتور بفكرة المشروع وأخذت تقدير امتياز. شكراً جزيلاً لك بشمهندس محمد.</div>
                </div>
                <div class="comment-node">
                    <div class="comment-meta">
                        <span class="comment-user">منى زايد (عمارة الإسكندرية)</span>
                        <span class="comment-date">منذ أسبوع</span>
                    </div>
                    <div class="comment-text">ريندر اللقطات الخارجية واللاندسكيب على برنامج D5 كان خيالياً وواقعياً للغاية، وتنسيق البوستر بالفوتوشوب ممتاز ومنظم جداً وأنصح بشدة بالتعامل معه.</div>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <p>جميع الحقوق محفوظة © 2026 | تم تطوير وتحديث المعرض بواسطة المهندس <strong>محمد الحارون</strong></p>
        <p style="font-size: 0.75rem; margin-top: 0.5rem; color: rgba(255,255,255,0.15)">متخصص في المشاريع الهندسية المعمارية فقط لا غير</p>
    </footer>

    <div class="lightbox-modal" id="galleryLightbox">
        <div class="lightbox-content">
            <button class="lightbox-close" onclick="closeGalleryLightbox()">✕</button>
            <img src="" id="lightboxImg" alt="صورة المشروع المعماري المفتوح">
            <div class="lightbox-nav">
                <button class="nav-arrow" onclick="changeLightboxImage(-1)">➔</button>
                <button class="nav-arrow" onclick="changeLightboxImage(1)">➔</button>
            </div>
            <div class="lightbox-caption">
                <div id="lightboxCaptionText" style="font-weight: 700; color: #fff;">استعراض مخرجات المشروع المعماري</div>
                <div id="lightboxCounter">1 من 5</div>
            </div>
        </div>
    </div>

    <script>
        // قواعد البيانات الخاصة بجاليري الصور والألبومات لكل مشروع معماري
        const projectGalleries = {
            1: ["https://g.top4top.io/p_3283v7jfe1.jpg", "https://h.top4top.io/p_328325n741.jpg", "https://i.top4top.io/p_3828g02sc1.jpg", "https://g.top4top.io/p_3828wnor1.jpg", "https://g.top4top.io/p_3828f4bqz1.jpg"],
            2: ["https://h.top4top.io/p_3828kfxcl1.jpg", "https://k.top4top.io/p_3828clele1.jpg", "https://c.top4top.io/p_3828gvugl1.jpg", "https://k.top4top.io/p_3828qrim11.jpg", "https://b.top4top.io/p_3828lgvbq1.jpg"]
        };
        let activeProjectId = 1, activeImageIndex = 0;

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
            if (activeImageIndex >= imagesList.length) activeImageIndex = 0; 
            else if (activeImageIndex < 0) activeImageIndex = imagesList.length - 1; 
            updateLightboxUI(); 
        }
        function updateLightboxUI() { 
            const imagesList = projectGalleries[activeProjectId]; 
            document.getElementById('lightboxImg').src = imagesList[activeImageIndex]; 
            document.getElementById('lightboxCounter').innerText = `${activeImageIndex + 1} من ${imagesList.length}`; 
        }

        // تفاعلية الأسئلة الشائعة الأكاديمية Accordion
        function toggleFaq(buttonElement) {
            const item = buttonElement.parentElement;
            const content = item.querySelector('.faq-content');
            if (item.classList.contains('active')) {
                item.classList.remove('active');
                content.style.maxHeight = null;
            } else {
                document.querySelectorAll('.faq-item').forEach(el => {
                    el.classList.remove('active');
                    el.querySelector('.faq-content').style.maxHeight = null;
                });
                item.classList.add('active');
                content.style.maxHeight = content.scrollHeight + "px";
            }
        }

        // تحديث وعرض قيم شريط المساحة وحساب السعر التقديري
        function updateAreaValue(currentValue) {
            document.getElementById('areaVal').innerText = currentValue + " م²";
            calculateProjectPrice();
        }

        // محرك وديناميكيات حاسبة تقدير الأسعار التقديرية وتغيير العملات
        function calculateProjectPrice() {
            const selectedServiceCostPerMeter = parseFloat(document.querySelector('input[name="serviceType"]:checked').value);
            const inputAreaSize = parseFloat(document.getElementById('areaRange').value);
            const targetCurrency = document.getElementById('currencySelect').value;

            // أسعار الصرف والديناميكيات القياسية الأساسية التقديرية المقترحة
            const currencyConfig = {
                EGP: { rate: 1, symbol: "جنيه مصري", label: "جنيه مصري" },
                USD: { rate: 0.021, symbol: "دولار أمريكي", label: "USD $" },
                SAR: { rate: 0.079, symbol: "ريال سعودي", label: "ريال سعودي" }
            };

            // الحساب الأساسي التقديري بالجنيه المصري أولاً
            let calculatedBasePriceInEgp = inputAreaSize * selectedServiceCostPerMeter;
            
            // تخصيص زمن التنفيذ التقديري طبقاً لحجم ومساحة المساقط
            let calculatedEstimatedDays = "4-6 أيام";
            if (inputAreaSize > 300 && inputAreaSize <= 600) calculatedEstimatedDays = "7-10 أيام";
            else if (inputAreaSize > 600) calculatedEstimatedDays = "11-15 يوم";

            // تحويل السعر التقديري حسب العملة المختارة من القائمة
            const selectedCurrencyObj = currencyConfig[targetCurrency];
            let fullyConvertedFinalPrice = calculatedBasePriceInEgp * selectedCurrencyObj.rate;

            // إخراج الأرقام والتفاصيل بصورة منسقة ومقروءة داخل الواجهة
            document.getElementById('totalPriceDisplay').innerText = Math.round(fullyConvertedFinalPrice).toLocaleString();
            document.getElementById('currencyLabel').innerText = selectedCurrencyObj.symbol;
            document.getElementById('timeStat').innerText = calculatedEstimatedDays;
        }

        // نظام نسخ رقم فودافون كاش تلقائياً بضغطة زر مع الحماية
        function copyVodafoneNumber() {
            const walletNumberString = document.getElementById('vodaNumber').innerText;
            navigator.clipboard.writeText(walletNumberString).then(() => {
                alert("تم نسخ رقم فودافون كاش المعماري بنجاح: " + walletNumberString);
            }).catch(err => {
                alert("فشل النسخ التلقائي؛ يمكنك تحديد الرقم ونسخه يدوياً.");
            });
        }

        // نظام استقبال ونشر تعليقات الزوار والطلبة بأمان تام وحمايتها من XSS
        function submitNewVisitorComment() {
            const inputNameRaw = document.getElementById('commenterName').value.trim();
            const inputSubjectRaw = document.getElementById('commenterSubject').value.trim();
            const inputTextRaw = document.getElementById('commenterText').value.trim();

            if (!inputNameRaw || !inputTextRaw) {
                alert("فضلاً، املأ حقل الاسم وحقل التعليق الأساسي أولاً لنشر مراجعتك.");
                return;
            }

            // فلترة وتطهير البيانات لمنع حقن الأكواد الضارة الخبيثة والـ XSS بالكامل
            const secureSanitizeText = (dirtyString) => {
                return dirtyString.replace(/&/g, "&amp;")
                                  .replace(/</g, "&lt;")
                                  .replace(/>/g, "&gt;")
                                  .replace(/"/g, "&quot;")
                                  .replace(/'/g, "&#x27;");
            };

            const safeCleanName = secureSanitizeText(inputNameRaw);
            const safeCleanSubject = inputSubjectRaw ? ` (${secureSanitizeText(inputSubjectRaw)})` : '';
            const safeCleanText = secureSanitizeText(inputTextRaw);

            const newCommentNodeHTML = `
                <div class="comment-node" style="animation: slideInComment 0.5s ease-out">
                    <div class="comment-meta">
                        <span class="comment-user">${safeCleanName}${safeCleanSubject}</span>
                        <span class="comment-date">الآن</span>
                    </div>
                    <div class="comment-text">${safeCleanText}</div>
                </div>
            `;

            // إدراج التعليق النظيف الجديد مباشرة في أعلى القائمة التفاعلية للزوار والطلاب
            const parentContainer = document.getElementById('commentsDisplayContainer');
            parentContainer.insertAdjacentHTML('afterbegin', newCommentNodeHTML);

            // تصفير وتطهير حقول نموذج الكتابة بعد النشر بنجاح
            document.getElementById('commenterName').value = '';
            document.getElementById('commenterSubject').value = '';
            document.getElementById('commenterText').value = '';
        }

        // التشغيل المبدئي الفوري للحاسبة التقديرية عند اكتمال تحميل عناصر الصفحة المعمارية
        window.addEventListener('DOMContentLoaded', () => {
            calculateProjectPrice();
        });
    </script>
</body>
</html>
