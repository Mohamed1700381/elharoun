<style>
    :root {
        --main-color: #0f172a; 
        --accent-color: #059669; 
        --accent-hover: #047857;
        --bg-color: #f8fafc;
        --text-color: #334155;
        --card-bg: #ffffff;
        --vodafone-color: #e60000; 
    }
    
    * {
        box-sizing: border-box;
        /* تم حذف الـ transition العشوائي من هنا لرفع أداء الصفحة */
    }

    body {
        font-family: 'Cairo', sans-serif;
        margin: 0;
        padding: 0;
        background-color: var(--bg-color);
        color: var(--text-color);
        line-height: 1.7;
        direction: rtl; /* دعم الاتجاه العربي بشكل صحيح */
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
        transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
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
        transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
    .card:hover {
        transform: translateY(-8px);
        box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.07);
    }
    
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
        transition: background-color 0.3s ease, transform 0.3s ease;
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
        display: flex; /* تم إصلاحها بإضافة الـ flex */
        flex-direction: column; /* ترتيب العناصر عمودياً */
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
        transition: transform 0.3s ease, background-color 0.3s ease;
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
