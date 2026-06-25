<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | معماري تفاعلي</title>
    <!-- استدعاء خط Cairo المودرن -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --main-dark: #050811; /* لون أسود عميق وفاخر */
            --card-glass: rgba(13, 20, 38, 0.65); /* تأثير زجاجي داكن */
            --accent-color: #10b981; /* أخضر زمردي يرمز للاستدامة المعمارية */
            --accent-glow: rgba(16, 185, 129, 0.3);
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
            padding: 100px 20px;
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
        
        /* أولاً: قسم نبذة عني */
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

        /* ثانياً: قسم مهاراتي */
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

        /* ثالثاً: معرض الصور العشوائية للمشاريع (دوائر نقية) */
        .photo-gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 40px;
            justify-items: center;
            margin-bottom: 60px;
        }
        
        .circle-project {
            position: relative;
            width: 250px;
            height: 250px;
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
        
        /* تأثير التمرير الانسيابي فوق الدوائر */
        .circle-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(5, 8, 17, 0.75);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            color: #34d399;
            font-weight: 600;
            font-size: 1.1rem;
            border-radius: 50%;
        }
        
        .circle-project:hover {
            transform: scale(1.05) translateY(-5px);
            border-color: var(--accent-color);
            box-shadow: 0 0 30px var(--accent-glow);
        }
        
        .circle-project:hover .circle-overlay {
            opacity: 1;
        }

        /* رابعاً: قسم التواصل النهائي عبر واتساب */
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

        footer {
            text-align: center;
            padding: 40px 20px;
            color: #475569;
            font-size: 0.95rem;
        }
    </style>
</head>
<body>

    <!-- الهيدر والمكعب المعماري -->
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
        
        <!-- أولاً: نبذة عني -->
        <section class="about-section">
            <h2>نبذة عني</h2>
            <p>
                معماري لديّ شغف قوي بالتصميم المعماري، التخطيط العمراني، والتنمية المستدامة. أسعى دائماً لابتكار حلول مستدامة ومبتكرة تعزز كفاءة البيئة المبنية وتلبي احتياجات المجتمع. 
                خلال مسيرتي الأكاديمية، قمت بإعداد وتطوير مشاريع متنوعة تشمل التخطيط البيئي المعماري، وتصميم لاندسكيب متكامل، بالإضافة إلى مشاريع تطوير وتحديث شبكات الطرق والمباني السكنية والإدارية والتعليمية لرفع جودة الحياة العمرانية.
            </p>
        </section>

        <!-- ثانياً: مهاراتي -->
        <h2 class="section-title">مهاراتي</h2>
        <p class="section-subtitle">القدرات والخبرات الهندسية والأكاديمية</p>
        <section class="skills-grid">
            <div class="skill-card">التصميم المعماري المستدام</div>
            <div class="skill-card">التخطيط والتصميم العمراني</div>
            <div class="skill-card">تنسيق المواقع (Landscape)</div>
            <div class="skill-card">تطوير شبكات الطرق والمباني</div>
            <div class="skill-card">دمج أدوات الذكاء الاصطناعي (AI)</div>
        </section>

        <!-- ثالثاً: صور عشوائية للمشاريع مع الوصف البسيط الموحد -->
        <h2 class="section-title">معرض المشاريع المنفذة</h2>
        <p class="section-subtitle">تم الدمج بين الوظيفه والجمال في التصميم</p>
        
        <main class="photo-gallery">
            
            <!-- صورة المشروع الأول -->
            <div class="circle-project" title="مشروع معماري">
                <img src="https://f.top4top.io/p_38283kx9v1.jpg" alt="مشروع معماري">
                <div class="circle-overlay">تصفح العمل</div>
            </div>

            <!-- صورة المشروع الثاني -->
            <div class="circle-project" title="مشروع معماري">
                <img src="https://b.top4top.io/p_382845wxq1.jpg" alt="مشروع معماري">
                <div class="circle-overlay">تصفح العمل</div>
            </div>

            <!-- صورة المشروع الثالث -->
            <div class="circle-project" title="مشروع معماري">
                <img src="https://i.top4top.io/p_3828m5rs31.jpg" alt="مشروع معماري">
                <div class="circle-overlay">تصفح العمل</div>
            </div>

        </main>

        <!-- رابعاً: التواصل معي عبر واتساب -->
        <section class="contact-section">
            <div class="contact-container">
                <div class="contact-title">تواصل معي</div>
                <p class="contact-desc">لمناقشة المشاريع المعمارية، الأفكار التصميمية، أو لطلبات الاستشارة الهندسية.</p>
                <a href="https://wa.me/201021788838" target="_blank" class="whatsapp-link">
                    <span>تواصل مباشرة عبر واتساب</span>
                </a>
            </div>
        </section>

    </div>

    <footer>
        <p>جميع الحقوق محفوظة © 2026 | معرض أعمال المهندس محمد الحارون</p>
    </footer>

</body>
</html>
