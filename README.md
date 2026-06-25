<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض أعمال المهندس محمد الحارون | احترافي</title>
    <!-- استدعاء خط Cairo المميز والتحديثي -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --main-color: #0f172a; /* لون داكن فاخر للنصوص والخلفيات الأساسية */
            --accent-color: #059669; /* لون أخضر زمردي يعبر عن الاستدامة المعمارية */
            --accent-hover: #047857;
            --bg-color: #f8fafc;
            --text-color: #334155;
            --card-bg: #ffffff;
            --vodafone-color: #e60000; /* لون فودافون الرسمي */
        }
        
        * {
            box-sizing: border-box;
            transition: all 0.3s ease;
        }

        body {
            font-family: 'Cairo', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.7;
        }

        /* الهيدر وبانر الترحيب */
        header {
            background: linear-gradient(135deg, var(--main-color) 0%, #1e293b 100%);
            color: white;
            padding: 80px 20px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        header::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 8px;
            background: linear-gradient(90deg, var(--accent-color), var(--vodafone-color));
        }
        header h1 {
            margin: 0;
            font-size: 2.8rem;
            font-weight: 700;
        }
        header p {
            margin: 15px 0 0 0;
            font-size: 1.25rem;
            color: #94a3b8;
            font-weight: 300;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 50px 20px;
        }
        
        /* قسم السيرة الذاتية */
        .about-section {
            background: var(--card-bg);
            padding: 40px;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.03);
            margin-bottom: 50px;
            border-right: 6px solid var(--accent-color);
        }
        .about-section h2 {
            color: var(--main-color);
            margin-top: 0;
            font-size: 1.8rem;
            margin-bottom: 15px;
        }
        .about-section p {
            font-size: 1.05rem;
            color: #475569;
        }

        /* قسم المهارات */
        .section-title {
            text-align: center;
            margin-top: 40px;
            margin-bottom: 40px;
            font-size: 2rem;
            color: var(--main-color);
            position: relative;
            font-weight: 700;
        }
        .section-title::after {
            content: '';
            display: block;
            width: 50px;
            height: 4px;
            background: var(--accent-color);
            border-radius: 2px;
            margin: 12px auto 0 auto;
        }
        
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-bottom: 60px;
        }
        .skill-card {
            background: var(--card-bg);
            color: var(--main-color);
            padding: 25px 20px;
            border-radius: 12px;
            text-align: center;
            font-weight: 600;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -1px rgba(0, 0, 0, 0.03);
            border: 1px solid #e2e8f0;
        }
        .skill-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            box-shadow: 0 10px 15px -3px rgba(5, 150, 105, 0.1);
        }
        .skill-card.ai {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: #34d399;
            border: none;
        }

        /* شبكة المشاريع */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 35px;
        }
        .card {
            background: var(--card-bg);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0,0,0,0.02);
            border: 1px solid #f1f5f9;
            display: flex;
            flex-direction: column;
            position: relative;
        }
        .card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.07);
        }
        
        /* الأيقونات الدائرية فوق الصور */
        .circle-icon {
            position: absolute;
            top: 15px;
            left: 15px;
            width: 45px;
            height: 45px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.15);
            z-index: 10;
            border: 2px solid var(--accent-color);
        }
        .circle-icon svg {
            width: 22px;
            height: 22px;
            fill: none;
            stroke: var(--accent-color);
            stroke-width: 2;
        }
        
        /* ضبط وعرض صور المشاريع */
        .card img {
            width: 100%;
            height: 240px;
            object-fit: cover;
            background-color: #cbd5e1;
            border-bottom: 1px solid #f1f5f9;
        }
        
        .card-content {
            padding: 30px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }
        .tag {
            align-self: flex-start;
            background: #d1fae5;
            color: var(--accent-color);
            padding: 4px 14px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 700;
            margin-bottom: 12px;
        }
        .card-title {
            font-size: 1.4rem;
            margin: 0 0 12px 0;
            color: var(--main-color);
            font-weight: 700;
        }
        .card-desc {
            font-size: 0.98rem;
            color: #64748b;
            margin-bottom: 25px;
            flex-grow: 1;
        }
        .action-area {
            margin-top: auto;
        }
        .price {
            font-weight: 700;
            color: #d97706;
            font-size: 1.25rem;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        /* أزرار الاتصال والشراء */
        .btn {
            display: block;
            padding: 14px 20px;
            text-decoration: none;
            border-radius: 8px;
            text-align: center;
            font-weight: bold;
            font-size: 1rem;
            cursor: pointer;
            border: none;
            width: 100%;
        }
        .btn-primary {
            background-color: var(--main-color);
            color: white;
        }
        .btn-primary:hover {
            background-color: var(--accent-color);
        }
        .btn-cash {
            background-color: var(--vodafone-color);
            color: white;
        }
        .btn-cash:hover {
            background-color: #b30000;
        }

        /* كارت الخدمات المستقل */
        .service-card {
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            color: white;
            border: none;
            text-align: center;
            justify-content: center;
            align-items: center;
            padding: 40px 30px;
        }
        .service-card .circle-icon-large {
            width: 70px;
            height: 70px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
            border: 2px solid #34d399;
        }
        .service-card .circle-icon-large svg {
            width: 35px;
            height: 35px;
            fill: none;
            stroke: #34d399;
            stroke-width: 2;
        }
        .service-card .card-title {
            color: white;
            font-size: 1.6rem;
        }
        .service-card .card-desc {
            color: #94a3b8;
        }
        .btn-whatsapp-service {
            background-color: #25d366;
            color: white;
        }
        .btn-whatsapp-service:hover {
            background-color: #20ba5a;
            transform: scale(1.02);
        }

        /* قسم تواصل معنا */
        .contact-section {
            background: var(--main-color);
            color: white;
            padding: 60px 20px;
            text-align: center;
            margin-top: 60px;
            border-top: 4px solid var(--accent-color);
        }
        .contact-container {
            max-width: 600px;
            margin: 0 auto;
        }
        .contact-title {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 15px;
        }
        .contact-desc {
            color: #94a3b8;
            margin-bottom: 30px;
        }
        .whatsapp-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            background-color: #25d366;
            color: white;
            padding: 15px 35px;
            font-size: 1.2rem;
            font-weight: bold;
            text-decoration: none;
            border-radius: 50px;
            box-shadow: 0 10px 20px rgba(37, 211, 102, 0.2);
        }
        .whatsapp-link:hover {
            transform: scale(1.05);
            background-color: #20ba5a;
        }

        footer {
            text-align: center;
            padding: 30px;
            background: #0b111e;
            color: #64748b;
            font-size: 0.9rem;
            border-top: 1px solid #1e293b;
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
            background-color: rgba(15, 23, 42, 0.7);
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(5px);
        }
        .modal-content {
            background-color: white;
            padding: 35px;
            border-radius: 16px;
            width: 90%;
            max-width: 450px;
            text-align: center;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            animation: modalSlide 0.3s ease;
        }
        @keyframes modalSlide {
            from { transform: translateY(-30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        .modal-header {
            color: var(--vodafone-color);
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        .modal-header .circle-icon-modal {
            width: 40px;
            height: 40px;
            background: #fee2e2;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .modal-header .circle-icon-modal svg {
            width: 20px;
            height: 20px;
            stroke: var(--vodafone-color);
            fill: none;
            stroke-width: 2;
        }
        .wallet-number {
            background: #f1f5f9;
            padding: 12px;
            border-radius: 8px;
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--main-color);
            letter-spacing: 2px;
            margin: 20px 0;
            border: 2px dashed #cbd5e1;
            user-select: all;
        }
        .modal-steps {
            text-align: right;
            padding-right: 20px;
            margin-bottom: 25px;
            font-size: 0.95rem;
        }
        .modal-steps li {
            margin-bottom: 8px;
        }
        .close-btn {
            background: #e2e8f0;
            color: #475569;
            margin-top: 10px;
        }
        .close-btn:hover {
            background: #cbd5e1;
        }
    </style>
</head>
<body>

    <header>
        <h1>المهندس المعماري / محمد الحارون</h1>
        <p>طالب عمارة | شغوف بالتخطيط العمراني، الاستدامة، وتطوير البيئة المبنية</p>
    </header>

    <div class="container">
        
        <!-- قسم السيرة الذاتية -->
        <section class="about-section">
            <h2>نبذة عني (سيرتي الذاتية)</h2>
            <p>
                طالب عمارة لديّ شغف قوي بالتصميم المعماري، التخطيط العمراني، والتنمية المستدامة. أسعى دائماً لابتكار حلول مستدامة ومبتكرة تعزز كفاءة البيئة المبنية وتلبي احتياجات المجتمع. 
                خلال مسيرتي الأكاديمية، قمت بإعداد وتطوير مشاريع متنوعة تشمل التخطيط البيئي المعماري، وتصميم لاندسكيب متكامل، بالإضافة إلى مشاريع تطوير وتحديث شبكات الطرق والمباني السكنية والإدارية والتعليمية لرفع جودة الحياة العمرانية.
            </p>
        </section>

        <!-- مهاراتك وقدراتك -->
        <h2 class="section-title">مجالات التميز والقدرات</h2>
        <div class="skills-grid">
            <div class="skill-card">التصميم المعماري المستدام</div>
            <div class="skill-card">التخطيط والتصميم العمراني</div>
            <div class="skill-card">تنسيق المواقع (Landscape)</div>
            <div class="skill-card">تطوير شبكات الطرق والمباني</div>
            <div class="skill-card ai">دمج أدوات الذكاء الاصطناعي (AI)</div>
        </div>

        <!-- معرض المشاريع والمنشورات -->
        <h2 class="section-title">معرض المشاريع المنفذة والخدمات</h2>
        <main class="grid">
            
            <!-- المشروع الأول: القرية البدوية -->
            <article class="card">
                <div class="circle-icon">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 12l8.954-8.955c.44-.439 1.152-.439 1.591 0L21.75 12M4.5 9.75v10.125c0 .621.504 1.125 1.125 1.125H9.75v-4.875c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21h4.125c.621 0 1.125-.504 1.125-1.125V9.75M8.25 21h8.25" /></svg>
                </div>
                <img src="1c6dc5a7-b564-4191-9808-2520c4dcae7a.jpg" alt="مشروع القرية البدوية المستدامة">
                <div class="card-content">
                    <span class="tag">تم التنفيذ</span>
                    <h3 class="card-title">مشروع القرية البدوية المستدامة في الصحراء</h3>
                    <p class="card-desc">مشروع متكامل يدمج التخطيط المعماري وتصميم اللاندسكيب مع استراتيجيات التصميم المستجيب للبيئة الصحراوية وتلبية احتياجات المجتمع المحلي.</p>
                    <div class="action-area">
                        <span class="price">10 - 30 $</span>
                        <a href="https://wa.me/201021788838?text=أريد_الاستفسار_عن_مشروع_القرية_البدوية" target="_blank" class="btn btn-primary">طلب المخططات المعمارية</a>
                    </div>
                </div>
            </article>

            <!-- المشروع الثاني: التصميم الحضري والطرق -->
            <article class="card">
                <div class="circle-icon">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M9 6.75V15m6-6v8.25m.503 3.498l4.875-2.437c.381-.19.622-.58.622-1.006V4.82c0-.836-.88-1.38-1.628-1.006l-3.869 1.934c-.317.159-.69.159-1.006 0L9.503 3.252a1.125 1.125 0 00-1.006 0L3.622 5.689C3.24 5.88 3 6.27 3 6.695V19.18c0 .836.88 1.38 1.628 1.006l3.869-1.934c.317-.159.69-.159 1.006 0l4.994 2.497c.317.158.69.158 1.006 0z" /></svg>
                </div>
                <img src="hgw1_8 - Photo.jpg" alt="مشروع تطوير البيئة الحضرية">
                <div class="card-content">
                    <span class="tag">تم التنفيذ</span>
                    <h3 class="card-title">مشروع تطوير كفاءة البيئة الحضرية</h3>
                    <p class="card-desc">دراسة وتصميم لتطوير شبكات الطرق والمباني السكنية، الإدارية، والتعليمية لرفع الكفاءة العمرانية وتحسين جودة الحياة داخل المدينة.</p>
                    <div class="action-area">
                        <span class="price">10 - 30 $</span>
                        <button onclick="openPaymentModal('مشروع تطوير البيئة الحضرية', '10 - 30 $')" class="btn btn-cash">شراء المخططات عبر فودافون كاش</button>
                    </div>
                </div>
            </article>

            <!-- المشروع الثالث: النادي الرياضي والمنشآت الحضرية -->
            <article class="card">
                <div class="circle-icon">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m0 12.75h7.5m-7.5 3H12M10.5 2.25H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9z" /></svg>
                </div>
                <img src="1_16 - Photo.jpg" alt="تصاميم النادي الرياضي والمنشآت الحضرية">
                <div class="card-content">
                    <span class="tag">تم التنفيذ</span>
                    <h3 class="card-title">تصاميم النادي الرياضي والمنشآت الحضرية</h3>
                    <p class="card-desc">مجموعة من التصاميم المعمارية المتنوعة التي تشمل نادياً رياضياً ترفيهياً متكاملاً، وتصميم بيئة عمرانية ومساحات مفتوحة مريحة وعصرية.</p>
                    <div class="action-area">
                        <span class="price">10 - 30 $</span>
                        <button onclick="openPaymentModal('تصاميم النادي والمنشآت الحضرية', '10 - 30 $')" class="btn btn-cash">شراء الملفات الهندسية</button>
                    </div>
                </div>
            </article>

            <!-- الأيقونة والبطاقة المستقلة المخصصة للاستشارات والتنفيذ المعماري -->
            <article class="card service-card">
                <div class="circle-icon-large">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M11.42 15.17L17.25 21A1.5 1.5 0 1019.5 18.75l-5.83-5.83M11.42 15.17l2.43-2.43m-2.43 2.43H3.75A1.5 1.5 0 012.25 13.67v-3.42A1.5 1.5 0 013.75 8.75h7.67a1.5 1.5 0 011.5 1.5v3.42a1.5 1.5 0 01-1.5 1.5zm6.83-11l3.58 3.58a1.5 1.5 0 010 2.12l-5.3 5.3a1.5 1.5 0 01-2.12 0L9.36 10.36a1.5 1.5 0 010-2.12l5.3-5.3a1.5 1.5 0 012.12 0z" /></svg>
                </div>
                <h3 class="card-title">طلب استشارة أو تنفيذ مشروع معماري</h3>
                <p class="card-desc">متاح بالكامل لتقديم الاستشارات المعمارية المتخصصة، التخطيط العمراني، وتصميم وتجسييد المشاريع الهندسية المتكاملة بأسلوب حديث ومستدام بناءً على رغبتك.</p>
                <div class="action-area" style="width: 100%;">
                    <a href="https://wa.me/201021788838?text=مرحباً_مهندس_محمد،_أريد_طلب_استشارة_معمارية_/_تنفيذ_مشروع_جديد" target="_blank" class="btn btn-whatsapp-service">تواصل معي مباشرة عبر واتساب</a>
                </div>
            </article>

        </main>
    </div>

    <!-- قسم تواصل معنا الإضافي للفوتر -->
    <section class="contact-section">
        <div class="contact-container">
            <div class="contact-title">للتواصل المباشر</div>
            <p class="contact-desc">اضغط على الزر بالأسفل للتحدث معي مباشرة عبر الواتساب ومناقشة تفاصيل مشروعك أو استشارتك.</p>
            <a href="https://wa.me/201021788838" target="_blank" class="whatsapp-link">
                <span>تواصل عبر الواتساب</span>
            </a>
        </div>
    </section>

    <footer>
        <p>جميع الحقوق محفوظة © 2026 | معرض أعمال المهندس محمد الحارون</p>
    </footer>

    <!-- نافذة الدفع المنبثقة الذكية (Vodafone Cash Modal) -->
    <div id="paymentModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="circle-icon-modal">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z" /></svg>
                </div>
                <span>الدفع عبر فودافون كاش</span>
            </div>
            <p>لإتمام شراء <strong id="modalProjectName"></strong> بقيمة تتراوح بين <strong id="modalProjectPrice"></strong>:</p>
            <p>قم بتحويل المبلغ المتفق عليه بالجنيه المصري إلى الرقم التالي:</p>
            
            <div class="wallet-number" title="اضغط لنسخ الرقم">01021788838</div>
            
            <ol class="modal-steps">
                <li>قم بتحويل قيمة الملف إلى الرقم أعلاه.</li>
                <li>خذ لقطة شاشة (Screenshot) لرسالة التأكيد.</li>
                <li>اضغط على زر التأكيد بالأسفل لإرسال الصورة واستلام ملفاتك فوراً.</li>
            </ol>

            <button id="confirmPaymentBtn" class="btn btn-primary">تأكيد التحويل وإرسال الصورة</button>
            <button onclick="closePaymentModal()" class="btn close-btn">إلغاء</button>
        </div>
    </div>

    <!-- كود الجافا سكريبت لتشغيل نافذة الدفع -->
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
