<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | بصري ثلاثي الأبعاد</title>
    <!-- استدعاء خط Cairo المميز والتحديثي -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --main-dark: #090d16; /* لون أسود عميق للخلفية المعمارية */
            --card-glass: rgba(15, 23, 42, 0.65); /* زجاج داكن للبطاقات */
            --accent-color: #059669; /* لون أخضر زمردي يعبر عن الاستدامة المعمارية */
            --accent-glow: rgba(5, 150, 105, 0.3);
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
                linear-gradient(rgba(255, 255, 255, 0.02) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
            background-size: 30px 30px;
            color: var(--text-primary);
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* الهيدر وقسم الترحيب المعماري */
        header {
            position: relative;
            padding: 100px 20px;
            text-align: center;
            background: radial-gradient(circle at top, #1e293b 0%, var(--main-dark) 80%);
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
            height: 4px;
            background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
        }
        header h1 {
            margin: 20px 0 0 0;
            font-size: 3rem;
            font-weight: 700;
            background: linear-gradient(to left, #ffffff, #a7f3d0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        header p {
            margin: 15px 0 0 0;
            font-size: 1.3rem;
            color: var(--text-secondary);
            font-weight: 300;
            max-width: 600px;
        }

        /* مشهد ومجسم المكعب ثلاثي الأبعاد 3D Cube Scene */
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
            animation: rotateCube 12s infinite linear;
        }
        .cube-face {
            position: absolute;
            width: 100px;
            height: 100px;
            border: 2px solid var(--accent-color);
            background: rgba(5, 150, 105, 0.15);
            box-shadow: inset 0 0 15px rgba(5, 150, 105, 0.3);
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
        
        /* قسم السيرة الذاتية الزجاجي */
        .about-section {
            background: var(--card-glass);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            margin-bottom: 60px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-right: 6px solid var(--accent-color);
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
        }

        .section-title {
            text-align: center;
            margin-top: 50px;
            margin-bottom: 50px;
            font-size: 2.2rem;
            color: #ffffff;
            position: relative;
            font-weight: 700;
        }
        .section-title::after {
            content: '';
            display: block;
            width: 60px;
            height: 4px;
            background: var(--accent-color);
            border-radius: 2px;
            margin: 12px auto 0 auto;
            box-shadow: 0 0 10px var(--accent-color);
        }

        /* شبكة الصور الدائرية الخاصة بالمشاريع */
        .photo-gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 40px;
            justify-items: center;
            margin-bottom: 80px;
        }
        
        .circle-project {
            position: relative;
            width: 250px;
            height: 250px;
            border-radius: 50%;
            overflow: hidden;
            border: 4px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 15px 35px rgba(0,0,0,0.4);
            cursor: pointer;
        }
        
        .circle-project img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        /* تأثير الطبقة الشفافة عند تمرير الماوس فوق الدائرة المعمارية */
        .circle-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(9, 13, 22, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            color: #34d399;
            font-weight: 700;
            font-size: 1.2rem;
            border-radius: 50%;
        }
        
        .circle-project:hover {
            transform: scale(1.05);
            border-color: var(--accent-color);
            box-shadow: 0 0 30px var(--accent-glow);
        }
        
        .circle-project:hover .circle-overlay {
            opacity: 1;
        }

        /* كارت خدمة الاستشارات المنفرد والعريض في الأسفل (محتفظ بالأيقونة) */
        .full-width-service {
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.9) 0%, rgba(9, 13, 22, 0.95) 100%);
            border: 1px solid rgba(52, 211, 153, 0.2);
            padding: 45px;
            border-radius: 24px;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
            margin-top: 20px;
        }
        .full-width-service:hover {
            border-color: #34d399;
            box-shadow: 0 25px 50px rgba(52, 211, 153, 0.1);
        }
        .circle-icon-large {
            width: 80px;
            height: 80px;
            background: rgba(5, 150, 105, 0.15);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 25px;
            border: 2px solid #34d399;
            box-shadow: 0 0 20px rgba(52, 211, 153, 0.2);
        }
        .circle-icon-large svg {
            width: 38px;
            height: 38px;
            fill: none;
            stroke: #34d399;
            stroke-width: 2;
        }
        .full-width-service .card-title {
            font-size: 1.8rem;
            margin: 0 0 15px 0;
            color: #ffffff;
            font-weight: 700;
        }
        .full-width-service .card-desc {
            max-width: 700px;
            color: var(--text-secondary);
            font-size: 1.05rem;
            margin-bottom: 30px;
        }
        .btn-whatsapp-service {
            display: block;
            padding: 16px 40px;
            text-decoration: none;
            border-radius: 10px;
            text-align: center;
            font-weight: 700;
            font-size: 1.1rem;
            background-color: #25d366;
            color: white;
            width: 100%;
            max-width: 350px;
            box-shadow: 0 10px 20px rgba(37, 211, 102, 0.2);
        }
        .btn-whatsapp-service:hover {
            background-color: #20ba5a;
            transform: scale(1.03) translateY(-2px);
            box-shadow: 0 15px 25px rgba(37, 211, 102, 0.3);
        }

        /* قسم تواصل معنا النهائي */
        .contact-section {
            background: #060a12;
            color: white;
            padding: 70px 20px;
            text-align: center;
            margin-top: 80px;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }
        .contact-container {
            max-width: 600px;
            margin: 0 auto;
        }
        .contact-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 15px;
        }
        .contact-desc {
            color: var(--text-secondary);
            margin-bottom: 35px;
        }
        .whatsapp-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            background-color: #25d366;
            color: white;
            padding: 16px 40px;
            font-size: 1.2rem;
            font-weight: bold;
            text-decoration: none;
            border-radius: 50px;
            box-shadow: 0 10px 25px rgba(37, 211, 102, 0.25);
        }
        .whatsapp-link:hover {
            transform: scale(1.05) translateY(-3px);
            background-color: #20ba5a;
        }

        footer {
            text-align: center;
            padding: 35px;
            background: #04060b;
            color: #475569;
            font-size: 0.95rem;
            border-top: 1px solid #0f172a;
        }
    </style>
</head>
<body>

    <header>
        <!-- مشهد ومجسم المكعب ثلاثي الأبعاد 3D Cube -->
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
        <p>طالب عمارة | شغوف بالتخطيط العمراني، الاستدامة، وتطوير البيئة المبنية</p>
    </header>

    <div class="container">
        
        <!-- قسم السيرة الذاتية الزجاجي -->
        <section class="about-section">
            <h2>نبذة عني (سيرتي الذاتية)</h2>
            <p>
                طالب عمارة لديّ شغف قوي بالتصميم المعماري، التخطيط العمراني، والتنمية المستدامة. أسعى دائماً لابتكار حلول مستدامة ومبتكرة تعزز كفاءة البيئة المبنية وتلبي احتياجات المجتمع. 
                خلال مسيرتي الأكاديمية، قمت بإعداد وتطوير مشاريع متنوعة تشمل التخطيط البيئي المعماري، وتصميم لاندسكيب متكامل، بالإضافة إلى مشاريع تطوير وتحديث شبكات الطرق والمباني السكنية والإدارية والتعليمية لرفع جودة الحياة العمرانية.
            </p>
        </section>

        <!-- معرض الصور الدائرية النقي للمشاريع -->
        <h2 class="section-title">معرض المشاريع المنفذة</h2>
        <main class="photo-gallery">
            
            <!-- الدائرة الأولى: مشروع القرية البدوية -->
            <div class="circle-project" title="مشروع القرية البدوية المستدامة">
                <img src="1c6dc5a7-b564-4191-9808-2520c4dcae7a.jpg" alt="مشروع القرية البدوية">
                <div class="circle-overlay">تم التنفيذ</div>
            </div>

            <!-- الدائرة الثانية: مشروع تطوير البيئة الحضرية -->
            <div class="circle-project" title="مشروع تطوير كفاءة البيئة الحضرية">
                <img src="hgw1_8 - Photo.jpg" alt="مشروع تطوير كفاءة البيئة الحضرية">
                <div class="circle-overlay">تم التنفيذ</div>
            </div>

            <!-- الدائرة الثالثة: تصاميم النادي والمنشآت الحضرية -->
            <div class="circle-project" title="تصاميم النادي الرياضي والمنشآت الحضرية">
                <img src="1_16 - Photo.jpg" alt="تصاميم النادي الرياضي">
                <div class="circle-overlay">تم التنفيذ</div>
            </div>

        </main>

        <!-- بطاقة خدمة الاستشارات الشاملة الاحترافية والأيقونة المستقلة -->
        <article class="card full-width-service">
            <div class="circle-icon-large">
                <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M11.42 15.17L17.25 21A1.5 1.5 0 1019.5 18.75l-5.83-5.83M11.42 15.17l2.43-2.43m-2.43 2.43H3.75A1.5 1.5 0 012.25 13.67v-3.42A1.5 1.5 0 013.75 8.75h7.67a1.5 1.5 0 011.5 1.5v3.42a1.5 1.5 0 01-1.5 1.5zm6.83-11l3.58 3.58a1.5 1.5 0 010 2.12l-5.3 5.3a1.5 1.5 0 01-2.12 0L9.36 10.36a1.5 1.5 0 010-2.12l5.3-5.3a1.5 1.5 0 012.12 0z" /></svg>
            </div>
            <h3 class="card-title">طلب استشارة أو تنفيذ مشروع معماري خاص</h3>
            <p class="card-desc">متاح بالكامل لتقديم الاستشارات المعمارية المتخصصة، التخطيط العمراني وتنسيق المواقع، وتصميم وتجسيد المشاريع الهندسية المتكاملة بأسلوب حديث ومستدام بناءً على رغبتك واحتياجاتك.</p>
            <a href="https://wa.me/201021788838?text=مرحباً_مهندس_محمد،_أريد_طلب_استشارة_معمارية_/_تنفيذ_مشروع_جديد" target="_blank" class="btn btn-whatsapp-service">تواصل معي مباشرة عبر واتساب</a>
        </article>

    </div>

    <!-- قسم تواصل معنا النهائي والفوتر -->
    <section class="contact-section">
        <div class="contact-container">
            <div class="contact-title">للتواصل المباشر</div>
            <p class="contact-desc">اضغط على الزر بالأسفل للتحدث معي مباشرة عبر الواتساب ومناقشة تفاصيل مشروعك أو استشارتك القادمة.</p>
            <a href="https://wa.me/201021788838" target="_blank" class="whatsapp-link">
                <span>تواصل عبر الواتساب</span>
            </a>
        </div>
    </section>

    <footer>
        <p>جميع الحقوق محفوظة © 2026 | معرض أعمال المهندس محمد الحارون</p>
    </footer>

</body>
</html>
