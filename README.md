<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | احترافي ثلاثي الأبعاد</title>
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
            --vodafone-color: #e60000;
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
            background: linear-gradient(90deg, transparent, var(--accent-color), var(--vodafone-color), transparent);
        }
        header h1 {
            margin: 20px 0 0 0;
            font-size: 3rem;
            font-weight: 700;
            letter-spacing: -1px;
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
        /* تحديد مواضع أوجه المكعب في الفراغ ثلاثي الأبعاد */
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
        
        /* قسم السيرة الذاتية بتأثير الزجاج عالي الفخامة */
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

        /* قسم المهارات والقدرات المعمارية */
        .section-title {
            text-align: center;
            margin-top: 50px;
            margin-bottom: 40px;
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
        
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-bottom: 70px;
        }
        .skill-card {
            background: rgba(30, 41, 59, 0.4);
            color: #e2e8f0;
            padding: 22px;
            border-radius: 14px;
            text-align: center;
            font-weight: 600;
            border: 1px solid rgba(255, 255, 255, 0.03);
        }
        .skill-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            background: rgba(5, 150, 105, 0.1);
            box-shadow: 0 10px 25px var(--accent-glow);
        }
        .skill-card.ai {
            background: linear-gradient(135deg, rgba(5, 150, 105, 0.2) 0%, rgba(15, 23, 42, 0.6) 100%);
            color: #34d399;
            border: 1px solid rgba(52, 211, 153, 0.3);
        }

        /* شبكة معرض الصور والمشاريع */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
            gap: 35px;
            margin-bottom: 50px;
        }
        .card {
            background: var(--card-glass);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            border: 1px solid rgba(255, 255, 255, 0.05);
            display: flex;
            flex-direction: column;
        }
        .card:hover {
            transform: translateY(-10px);
            border-color: rgba(5, 150, 105, 0.4);
            box-shadow: 0 25px 45px rgba(5, 150, 105, 0.15);
        }
        
        /* حاوي وحامي صور المشاريع لتجنب أي تلف برميجي */
        .card-image-wrapper {
            position: relative;
            width: 100%;
            height: 250px;
            background-color: #1e293b;
            overflow: hidden;
        }
        .card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .card-content {
            padding: 30px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }
        .tag {
            align-self: flex-start;
            background: rgba(5, 150, 105, 0.2);
            color: #34d399;
            padding: 4px 14px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 700;
            margin-bottom: 15px;
            border: 1px solid rgba(52, 211, 153, 0.2);
        }
        .card-title {
            font-size: 1.4rem;
            margin: 0 0 12px 0;
            color: #ffffff;
            font-weight: 700;
        }
        .card-desc {
            font-size: 0.98rem;
            color: var(--text-secondary);
            margin-bottom: 25px;
            flex-grow: 1;
        }
        .action-area {
            margin-top: auto;
        }
        .price {
            font-weight: 700;
            color: #fbbf24;
            font-size: 1.3rem;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        /* الأزرار الهندسية المحدثة */
        .btn {
            display: block;
            padding: 14px 20px;
            text-decoration: none;
            border-radius: 10px;
            text-align: center;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            border: none;
            width: 100%;
        }
        .btn-primary {
            background-color: rgba(255, 255, 255, 0.08);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .btn-primary:hover {
            background-color: var(--accent-color);
            border-color: var(--accent-color);
            box-shadow: 0 0 15px var(--accent-glow);
        }
        .btn-cash {
            background-color: var(--vodafone-color);
            color: white;
            box-shadow: 0 4px 15px rgba(230, 0, 0, 0.3);
        }
        .btn-cash:hover {
            background-color: #b30000;
            transform: translateY(-2px);
        }

        /* كارت خدمة الاستشارات المنفرد والعريض الممتد في الأسفل */
        .full-width-service {
            grid-column: 1 / -1; /* يمتد بكامل عرض الشبكة */
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
            margin-bottom: 15px;
            color: #ffffff;
        }
        .full-width-service .card-desc {
            max-width: 700px;
            color: var(--text-secondary);
            font-size: 1.05rem;
            margin-bottom: 30px;
        }
        .btn-whatsapp-service {
            background-color: #25d366;
            color: white;
            padding: 16px 40px;
            font-size: 1.1rem;
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

        /* النافذة المنبثقة للدفع الفاخرة (Modal) */
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
            font-size: 1.6rem;
            font-weight: 700;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }
        .modal-header .circle-icon-modal {
            width: 45px;
            height: 45px;
            background: rgba(230, 0, 0, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .modal-header .circle-icon-modal svg {
            width: 22px;
            height: 22px;
            stroke: var(--vodafone-color);
            fill: none;
            stroke-width: 2;
        }
        .wallet-number {
            background: rgba(255, 255, 255, 0.03);
            padding: 14px;
            border-radius: 12px;
            font-size: 1.5rem;
            font-weight: 700;
            color: #34d399;
            letter-spacing: 2px;
            margin: 25px 0;
            border: 2px dashed rgba(52, 211, 153, 0.3);
            user-select: all;
        }
        .modal-steps {
            text-align: right;
            padding-right: 20px;
            margin-bottom: 30px;
            font-size: 0.98rem;
            color: var(--text-secondary);
        }
        .modal-steps li {
            margin-bottom: 10px;
        }
        .close-btn {
            background: rgba(255, 255, 255, 0.05);
            color: #94a3b8;
            margin-top: 12px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }
        .close-btn:hover {
            background: rgba(255, 255, 255, 0.1);
            color: #ffffff;
        }
    </style>
</head>
<body>

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
        <p>طالب عمارة | شغوف بالتخطيط العمراني، الاستدامة، وتطوير البيئة المبنية</p>
    </header>

    <div class="container">
        
        <section class="about-section">
            <h2>نبذة عني (سيرتي الذاتية)</h2>
            <p>
                طالب عمارة لديّ شغف قوي بالتصميم المعماري، التخطيط العمراني، والتنمية المستدامة. أسعى دائماً لابتكار حلول مستدامة ومبتكرة تعزز كفاءة البيئة المبنية وتلبي احتياجات المجتمع. 
                خلام مسيرتي الأكاديمية، قمت بإعداد وتطوير مشاريع متنوعة تشمل التخطيط البيئي المعماري، وتصميم لاندسكيب متكامل، بالإضافة إلى مشاريع تطوير وتحديث شبكات الطرق والمباني السكنية والإدارية والتعليمية لرفع جودة الحياة العمرانية.
            </p>
        </section>

        <h2 class="section-title">مجالات التميز والقدرات</h2>
        <div class="skills-grid">
            <div class="skill-card">التصميم المعماري المستدام</div>
            <div class="skill-card">التخطيط والتصميم العمراني</div>
            <div class="skill-card">تنسيق المواقع (Landscape)</div>
            <div class="skill-card">تطوير شبكات الطرق والمباني</div>
            <div class="skill-card ai">دمج أدوات الذكاء الاصطناعي (AI)</div>
        </div>

        <h2 class="section-title">معرض المشاريع والمنشورات</h2>
        <main class="grid">
            
            <article class="card">
                <div class="card-image-wrapper">
                    <img src="1c6dc5a7-b564-4191-9808-2520c4dcae7a.jpg" alt="مشروع القرية البدوية المستدامة">
                </div>
                <div class="card-content">
                    <span class="tag">تم التنفيذ</span>
                    <h3 class="card-title">مشروع القرية البدوية المستدامة في الصحراء</h3>
                    <p class="card-desc">مشروع متكامل يدمج التخطيط المعماري وتصميم اللاندسكيب مع استراتيجيات التصميم المستجيب للبيئة الصحراوية وتلبية احتياجات المجتمع المحلي.</p>
                    <div class="action-area">
                        <div class="price">10 - 30 $</div>
                        <a href="https://wa.me/201021788838?text=أريد_الاستفسار_عن_مشروع_القرية_البدوية_المستدامة" target="_blank" class="btn btn-primary">طلب المخططات المعمارية</a>
                    </div>
                </div>
            </article>

            <article class="card">
                <div class="card-image-wrapper">
                    <img src="hgw1_8 - Photo.jpg" alt="مشروع تطوير البيئة الحضرية">
                </div>
                <div class="card-content">
                    <span class="tag">تم التنفيذ</span>
                    <h3 class="card-title">مشروع تطوير كفاءة البيئة الحضرية</h3>
                    <p class="card-desc">دراسة وتصميم لتطوير شبكات الطرق والمباني السكنية، الإدارية، والتعليمية لرفع الكفاءة العمرانية وتحسين جودة الحياة داخل المدينة.</p>
                    <div class="action-area">
                        <div class="price">10 - 30 $</div>
                        <button onclick="openPaymentModal('مشروع تطوير البيئة الحضرية', '10 - 30 $')" class="btn btn-cash">شراء المخططات عبر فودافون كاش</button>
                    </div>
                </div>
            </article>

            <article class="card">
                <div class="card-image-wrapper">
                    <img src="1_16 - Photo.jpg" alt="تصاميم النادي الرياضي والمنشآت الحضرية">
                </div>
                <div class="card-content">
                    <span class="tag">تم التنفيذ</span>
                    <h3 class="card-title">تصاميم النادي الرياضي والمنشآت الحضرية</h3>
                    <p class="card-desc">مجموعة من التصاميم المعمارية المتنوعة التي تشمل نادياً رياضياً ترفيهياً متكاملاً، وتصميم بيئة عمرانية ومساحات مفتوحة مريحة وعصرية.</p>
                    <div class="action-area">
                        <div class="price">10 - 30 $</div>
                        <button onclick="openPaymentModal('تصاميم النادي والمنشآت الحضرية', '10 - 30 $')" class="btn btn-cash">شراء الملفات الهندسية</button>
                    </div>
                </div>
            </article>

            <article class="card full-width-service">
                <div class="circle-icon-large">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M11.42 15.17L17.25 21A1.5 1.5 0 1019.5 18.75l-5.83-5.83M11.42 15.17l2.43-2.43m-2.43 2.43H3.75A1.5 1.5 0 012.25 13.67v-3.42A1.5 1.5 0 013.75 8.75h7.67a1.5 1.5 0 011.5 1.5v3.42a1.5 1.5 0 01-1.5 1.5zm6.83-11l3.58 3.58a1.5 1.5 0 010 2.12l-5.3 5.3a1.5 1.5 0 01-2.12 0L9.36 10.36a1.5 1.5 0 010-2.12l5.3-5.3a1.5 1.5 0 012.12 0z" /></svg>
                </div>
                <h3 class="card-title">طلب استشارة أو تنفيذ مشروع معماري خاص</h3>
                <p class="card-desc">أنا متاح بالكامل لتقديم الاستشارات المعمارية المتخصصة، التخطيط العمراني وتنسيق المواقع، وتصميم وتجسيد المشاريع الهندسية المتكاملة بأسلوب حديث ومستدام بناءً على رغبتك واحتياجاتك.</p>
                <a href="https://wa.me/201021788838?text=مرحباً_مهندس_محمد،_أريد_طلب_استشارة_معمارية_/_تنفيذ_مشروع_جديد" target="_blank" class="btn btn-whatsapp-service">تواصل معي مباشرة عبر واتساب</a>
            </article>

        </main>
    </div>

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

    <div id="paymentModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="circle-icon-modal">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z" /></svg>
                </div>
                <span>الدفع عبر فودافون كاش</span>
            </div>
            <p>لإتمام شراء <strong id="modalProjectName"></strong> بنطاق سعري <strong id="modalProjectPrice"></strong>:</p>
            <p>قم بتحويل المبلغ المتفق عليه بالجنيه المصري إلى الرقم التالي:</p>
            
            <div class="wallet-number" title="اضغط لنسخ الرقم">01021788838</div>
            
            <ol class="modal-steps">
                <li>قم بتحويل قيمة الملف إلى الرقم أعلاه.</li>
                <li>خذ لقطة شاشة (Screenshot) لرسالة التأكيد.</li>
                <li>اضغط على زر التأكيد بالأسفل لإرسال الصورة واستلام ملفاتك فوراً.</li>
            </ol>

            <button id="confirmPaymentBtn" class="btn btn-cash" style="width:100%;">تأكيد التحويل وإرسال الصورة</button>
            <button onclick="closePaymentModal()" class="btn close-btn">إلغاء</button>
        </div>
    </div>

    <script>
        const modal = document.getElementById('paymentModal');
        const projectNameText = document.getElementById('modalProjectName');
        const projectPriceText = document.getElementById('modalProjectPrice');
        const confirmBtn = document.getElementById('confirmPaymentBtn');

        function openPaymentModal(projectName, price) {
            projectNameText.innerText = projectName;
            projectPriceText.innerText = price;
            
            confirmBtn.onclick = function() {
                const message = encodeURIComponent(`مرحباً مهندس محمد، لقد قمت بتحويل المبلغ عبر فودافون كاش لشراء: (${projectName}). أريد إرسال لقطة الشاشة لاستلام الملفات.`);
                window.open(`https://wa.me/201021788838?text=${message}`, '_blank');
                closePaymentModal();
            };

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
    </script>

</body>
</html>
