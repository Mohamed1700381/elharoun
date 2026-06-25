<!-- استيراد الخطوط لتظهر بشكل معماري حاد وأنيق -->
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
        --grid-color: rgba(15, 23, 42, 0.03); /* لون الشبكة المعمارية */
    }
    
    * {
        box-sizing: border-box;
        transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1); /* حركة أنعم تليق بالـ 3D */
    }

    body {
        font-family: 'Cairo', sans-serif;
        margin: 0;
        padding: 0;
        background-color: var(--bg-color);
        /* تأثير الخلفية الهندسية: شبكة رسم معماري متحركة */
        background-image: 
            linear-gradient(var(--grid-color) 1px, transparent 1px),
            linear-gradient(90deg, var(--grid-color) 1px, transparent 1px);
        background-size: 30px 30px;
        color: var(--text-color);
        line-height: 1.7;
        position: relative;
    }

    /* هيدر وبانر الترحيب بتأثير عمق وثلاثي الأبعاد */
    header {
        background: linear-gradient(135deg, var(--main-color) 0%, #1e293b 100%);
        color: white;
        padding: 100px 20px;
        text-align: center;
        position: relative;
        overflow: hidden;
        box-shadow: inset 0 -10px 20px rgba(0,0,0,0.2);
    }
    
    /* شبكة منظور هندسي داخل الهيدر */
    header::before {
        content: '';
        position: absolute;
        top: 0; left: 0; right: 0; bottom: 0;
        background-image: linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
        background-size: 20px 20px;
        transform: perspective(500px) rotateX(60deg) translateY(-50px);
        opacity: 0.7;
        pointer-events: none;
    }

    header::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        height: 6px;
        background: linear-gradient(90deg, var(--accent-color), var(--vodafone-color));
    }

    header h1 {
        margin: 0;
        font-size: 3rem;
        font-weight: 700;
        text-shadow: 0 4px 12px rgba(0,0,0,0.3);
        letter-spacing: -0.5px;
    }
    header p {
        margin: 15px 0 0 0;
        font-size: 1.3rem;
        color: #34d399; /* تغيير اللون ليتماشى مع طابع الذكاء الاصطناعي والاستدامة */
        font-weight: 300;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 60px 20px;
    }
    
    /* قسم السيرة الذاتية - تطفو بظل 3D ناعم */
    .about-section {
        background: var(--card-bg);
        padding: 45px;
        border-radius: 20px;
        box-shadow: 0 20px 40px rgba(15, 23, 42, 0.04);
        margin-bottom: 60px;
        border-right: 6px solid var(--accent-color);
        transform: translateY(0);
    }
    
    .about-section h2 {
        color: var(--main-color);
        margin-top: 0;
        font-size: 2rem;
        margin-bottom: 20px;
    }
    .about-section p {
        font-size: 1.1rem;
        color: #475569;
    }

    /* قسم المهارات */
    .section-title {
        text-align: center;
        margin-top: 50px;
        margin-bottom: 50px;
        font-size: 2.2rem;
        color: var(--main-color);
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
        margin: 14px auto 0 auto;
    }
    
    .skills-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 25px;
        margin-bottom: 70px;
        perspective: 1000px; /* تفعيل البيئة ثلاثية الأبعاد للكروت الداخلية */
    }
    
    .skill-card {
        background: var(--card-bg);
        color: var(--main-color);
        padding: 30px 20px;
        border-radius: 16px;
        text-align: center;
        font-weight: 600;
        box-shadow: 0 10px 20px rgba(0,0,0,0.02);
        border: 1px solid #e2e8f0;
        transform-style: preserve-3d;
    }
    
    /* تأثير الـ 3D عند التمرير على المهارات */
    .skill-card:hover {
        transform: translateY(-8px) rotateX(5deg) rotateY(-5deg);
        border-color: var(--accent-color);
        box-shadow: 0 20px 30px rgba(5, 150, 105, 0.12);
    }
    
    .skill-card.ai {
        background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
        color: #34d399;
        border: none;
        box-shadow: 0 10px 25px rgba(15, 23, 42, 0.15);
    }
    .skill-card.ai:hover {
        box-shadow: 0 25px 35px rgba(52, 211, 153, 0.2);
    }

    /* شبكة المشاريع */
    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
        gap: 40px;
        perspective: 1000px;
    }
    
    /* كارت المشروع بتصميم مجسم وثلاثي الأبعاد */
    .card {
        background: var(--card-bg);
        border-radius: 20px;
        overflow: hidden;
        box-shadow: 0 15px 35px rgba(0,0,0,0.03);
        border: 1px solid #e2e8f0;
        display: flex;
        flex-direction: column;
        position: relative;
        transform-style: preserve-3d;
    }
    
    /* تأثير الارتفاع والميلان المعماري للكارت */
    .card:hover {
        transform: translateY(-12px) scale(1.02) rotateX(3deg);
        box-shadow: 0 30px 50px rgba(15, 23, 42, 0.1);
        border-color: #cbd5e1;
    }
    
    .card img {
        width: 100%;
        height: 250px;
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
        padding: 6px 16px;
        border-radius: 50px;
        font-size: 0.85rem;
        font-weight: 700;
        margin-bottom: 15px;
    }
    .card-title {
        font-size: 1.45rem;
        margin: 0 0 12px 0;
        color: var(--main-color);
        font-weight: 700;
    }
    .card-desc {
        font-size: 1rem;
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
        font-size: 1.35rem;
        margin-bottom: 18px;
        display: flex;
        align-items: center;
        gap: 6px;
    }
    
    /* أزرار الاتصال والشراء */
    .btn {
        display: block;
        padding: 14px 20px;
        text-decoration: none;
        border-radius: 10px;
        text-align: center;
        font-weight: bold;
        font-size: 1rem;
        cursor: pointer;
        border: none;
        width: 100%;
        box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    }
    .btn-primary {
        background-color: var(--main-color);
        color: white;
    }
    .btn-primary:hover {
        background-color: var(--accent-color);
        transform: translateY(-2px);
    }
    .btn-cash {
        background-color: var(--vodafone-color);
        color: white;
    }
    .btn-cash:hover {
        background-color: #b30000;
        transform: translateY(-2px);
    }

    /* كارت الخدمات المستقل (مظهر زجاجي 3D غامق) */
    .service-card {
        background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
        color: white;
        border: none;
        text-align: center;
        justify-content: center;
        align-items: center;
        padding: 45px 35px;
    }
    .service-card .circle-icon-large {
        width: 75px;
        height: 75px;
        background: rgba(255, 255, 255, 0.05);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 25px;
        border: 2px solid #34d399;
        box-shadow: 0 0 15px rgba(52, 211, 153, 0.3);
    }
    .service-card .circle-icon-large svg {
        width: 38px;
        height: 38px;
        fill: none;
        stroke: #34d399;
        stroke-width: 2;
    }
    .service-card .card-title {
        color: white;
        font-size: 1.65rem;
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
        transform: scale(1.04);
        box-shadow: 0 10px 20px rgba(37, 211, 102, 0.3);
    }

    /* قسم تواصل معنا المطور */
    .contact-section {
        background: linear-gradient(135deg, var(--main-color) 0%, #0b111e 100%);
        color: white;
        padding: 80px 20px;
        text-align: center;
        margin-top: 80px;
        border-top: 4px solid var(--accent-color);
        position: relative;
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
        color: #94a3b8;
        margin-bottom: 35px;
        font-size: 1.1rem;
    }
    .whatsapp-link {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 12px;
        background-color: #25d366;
        color: white;
        padding: 16px 40px;
        font-size: 1.25rem;
        font-weight: bold;
        text-decoration: none;
        border-radius: 50px;
        box-shadow: 0 12px 24px rgba(37, 211, 102, 0.25);
    }
    .whatsapp-link:hover {
        transform: translateY(-4px) scale(1.03);
        background-color: #20ba5a;
        box-shadow: 0 18px 30px rgba(37, 211, 102, 0.4);
    }

    footer {
        text-align: center;
        padding: 35px;
        background: #060b13;
        color: #64748b;
        font-size: 0.95rem;
        border-top: 1px solid #1e293b;
    }

    /* النافذة المنبثقة المحسنة للدفع (Modal 3D Pop) */
    .modal {
        display: none;
        position: fixed;
        z-index: 1000;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(15, 23, 42, 0.8);
        align-items: center;
        justify-content: center;
        backdrop-filter: blur(8px);
    }
    .modal-content {
        background-color: white;
        padding: 40px;
        border-radius: 24px;
        width: 90%;
        max-width: 460px;
        text-align: center;
        box-shadow: 0 30px 70px rgba(0, 0, 0, 0.4);
        transform: scale(0.9);
        animation: modal3D 0.4s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
    }
    
    @keyframes modal3D {
        to { transform: scale(1); opacity: 1; }
    }
    
    .modal-header {
        color: var(--vodafone-color);
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
        background: #fee2e2;
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
        background: #f8fafc;
        padding: 14px;
        border-radius: 12px;
        font-size: 1.5rem;
        font-weight: 700;
        color: var(--main-color);
        letter-spacing: 2px;
        margin: 25px 0;
        border: 2px dashed #cbd5e1;
        user-select: all;
    }
    .modal-steps {
        text-align: right;
        padding-right: 15px;
        margin-bottom: 30px;
        font-size: 1rem;
        color: #475569;
    }
    .modal-steps li {
        margin-bottom: 10px;
    }
    .close-btn {
        background: #e2e8f0;
        color: #475569;
        margin-top: 12px;
        border-radius: 10px;
    }
    .close-btn:hover {
        background: #cbd5e1;
    }
</style>
