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
        }

        body {
            font-family: 'Cairo', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--main-dark);
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(16, 185, 129, 0.05) 0%, transparent 80%),
                linear-gradient(rgba(255, 255, 255, 0.01) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255, 255, 255, 0.01) 1px, transparent 1px);
            background-size: 100% 100%, 40px 40px, 40px 40px;
            color: var(--text-primary);
            line-height: 1.8;
            overflow-x: hidden;
        }

        /* مؤشر الماوس المعماري */
        .custom-cursor {
            width: 20px;
            height: 20px;
            border: 2px solid var(--accent-color);
            border-radius: 50%;
            position: fixed;
            transform: translate(-50%, -50%);
            pointer-events: none;
            z-index: 9999;
            mix-blend-mode: difference;
            display: none;
        }
        @media (min-width: 1024px) {
            .custom-cursor { display: block; }
        }

        /* الهيدر */
        header {
            position: relative;
            padding: 140px 20px 80px 20px;
            text-align: center;
            background: radial-gradient(circle at top, #111827 0%, var(--main-dark) 100%);
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
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(16, 185, 129, 0.4), transparent);
        }

        header h1 {
            margin: 30px 0 0 0;
            font-size: 3.5rem;
            font-weight: 700;
            letter-spacing: -1px;
            background: linear-gradient(to left, #ffffff 30%, #34d399 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        header p {
            margin: 15px 0 0 0;
            font-size: 1.3rem;
            color: var(--text-secondary);
            font-weight: 300;
            max-width: 700px;
        }

        .top-nav-bar {
            position: absolute;
            top: 25px;
            left: 25px;
            right: 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 100;
        }

        .menu-toggle-btn {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--border-glass);
            width: 46px;
            height: 46px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            backdrop-filter: blur(12px);
        }
        .menu-toggle-btn:hover {
            background: rgba(16, 185, 129, 0.15);
            border-color: var(--accent-color);
            box-shadow: 0 0 20px var(--accent-glow);
        }
        .menu-toggle-btn svg {
            width: 24px;
            height: 24px;
            stroke: #ffffff;
            stroke-width: 2;
        }

        /* الحاوية الرئيسية */
        .container { max-width: 1200px; margin: 0 auto; padding: 40px 20px; }
        
        .about-section {
            background: var(--card-glass);
            backdrop-filter: blur(12px);
            padding: 40px; border-radius: 24px; box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            margin-bottom: 60px; border: 1px solid var(--border-glass);
            border-right: 5px solid var(--accent-color);
        }
        
        .section-title { text-align: center; margin-top: 80px; margin-bottom: 10px; font-size: 2.4rem; color: #ffffff; font-weight: 700; }
        .section-subtitle { text-align: center; color: var(--text-secondary); font-size: 1.1rem; margin-bottom: 45px; }
        .section-title::after { content: ''; display: block; width: 60px; height: 4px; background: var(--accent-color); border-radius: 2px; margin: 12px auto 0 auto; box-shadow: 0 0 15px var(--accent-color); }

        /* مهارات */
        .skills-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; margin-bottom: 60px; }
        .skill-card { background: rgba(31, 41, 55, 0.4); color: #e5e7eb; padding: 22px; border-radius: 16px; text-align: center; font-weight: 600; border: 1px solid rgba(255, 255, 255, 0.02); }
        .skill-card:hover { transform: translateY(-5px); border-color: var(--accent-color); background: rgba(16, 185, 129, 0.08); box-shadow: 0 15px 30px var(--accent-glow); }

        /* قسم مشاريع الطلاب الجديد */
        .students-section {
            background: linear-gradient(135deg, rgba(16, 185, 129, 0.03) 0%, rgba(17, 24, 39, 0.8) 100%);
            border: 1px solid rgba(16, 185, 129, 0.15); border-radius: 24px; padding: 40px; margin-bottom: 60px;
            backdrop-filter: blur(12px);
        }
        .students-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 25px; margin-top: 30px; }
        .student-service-card {
            background: rgba(5, 8, 17, 0.6);
            border: 1px solid var(--border-glass); 
            padding: 25px; border-radius: 16px;
        }
        .student-service-card:hover { border-color: var(--accent-color); transform: translateY(-4px); }
        .student-service-card h3 { color: #ffffff; font-size: 1.25rem; margin-top: 0; margin-bottom: 12px; display: flex; align-items: center; gap: 10px; }
        .student-service-card h3 svg { width: 22px; height: 22px; fill: var(--accent-color); }
        .student-service-card p { color: var(--text-secondary); font-size: 0.95rem; margin: 0; }
        
        .programs-container { display: flex; flex-wrap: wrap; justify-content: center; gap: 15px; margin-top: 35px; }
        .program-badge {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--border-glass);
            padding: 8px 20px; border-radius: 30px; font-weight: 600; font-size: 0.95rem; color: #e5e7eb;
        }
        .program-badge span { color: var(--accent-color); font-weight: 700; margin-left: 4px; }

        /* معرض الصور الدائري */
        .photo-gallery { display: flex; flex-wrap: wrap; gap: 60px; justify-content: center; margin-bottom: 60px; }
        .circle-project { position: relative; width: 270px; height: 270px; border-radius: 50%; overflow: hidden; border: 3px solid rgba(255, 255, 255, 0.08); box-shadow: 0 20px 40px rgba(0,0,0,0.5); cursor: pointer; }
        .circle-project img { width: 100%; height: 100%; object-fit: cover; }
        .circle-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(3, 7, 18, 0.9); display: flex; flex-direction: column; align-items: center; justify-content: center; opacity: 0; color: #34d399; font-weight: 700; font-size: 1.3rem; border-radius: 50%; padding: 20px; text-align: center; }
        .circle-overlay span { font-size: 0.85rem; color: var(--text-secondary); margin-top: 8px; }
        .circle-project:hover { transform: scale(1.05) translateY(-8px); border-color: var(--accent-color); box-shadow: 0 0 40px var(--accent-glow); }
        .circle-project:hover .circle-overlay { opacity: 1; }

        /* حاسبة التكلفة */
        .calculator-section {
            background: var(--card-glass);
            border: 1px solid var(--border-glass);
            border-radius: 24px; padding: 40px; max-width: 800px; margin: 40px auto;
            backdrop-filter: blur(15px);
        }
        .calc-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 25px; }
        @media (max-width: 640px) {
            .calc-grid { grid-template-columns: 1fr; }
            .calc-full-width { grid-column: span 1 !important; }
            .live-stats-panel { grid-column: span 1 !important; grid-template-columns: 1fr !important; }
        }
        .calc-field label { display: block; font-size: 0.95rem; color: var(--text-secondary); margin-bottom: 8px; font-weight: 600; }
        .calc-field select, .calc-field input {
            width: 100%;
            padding: 14px; background: rgba(5,8,17,0.7);
            border: 1px solid rgba(255,255,255,0.08); border-radius: 12px;
            color: white; font-family: 'Cairo'; font-size: 0.95rem;
        }
        .calc-field select:focus, .calc-field input:focus { border-color: var(--accent-color); outline: none; }
        .calc-full-width { grid-column: span 2; }
        
        .currency-switch-wrapper { display: flex; justify-content: flex-end; gap: 10px; margin-bottom: -10px; }
        .currency-btn {
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border-glass); color: var(--text-secondary);
            padding: 5px 15px; border-radius: 8px; font-size: 0.85rem; cursor: pointer; font-family: 'Cairo';
        }
        .currency-btn.active { background: var(--accent-color); color: #000000; font-weight: 700; box-shadow: 0 0 10px var(--accent-glow); }

        .live-stats-panel { grid-column: span 2; display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; margin-top: 20px; }
        .stat-box { background: rgba(255,255,255,0.02); border: 1px solid var(--border-glass); padding: 15px; border-radius: 14px; text-align: center; }
        .stat-value { font-size: 1.4rem; font-weight: 700; color: #ffffff; }
        .stat-label { font-size: 0.8rem; color: var(--text-secondary); margin-top: 4px; }

        .calc-result-box { background: rgba(16, 185, 129, 0.05); border: 1px solid rgba(16, 185, 129, 0.15); padding: 25px; border-radius: 16px; text-align: center; margin-top: 30px; }
        .calc-price { font-size: 2.3rem; font-weight: 700; color: var(--accent-color); margin: 10px 0; }
        .submit-auth-btn { width: 100%; max-width: 320px; padding: 14px; border-radius: 12px; font-family: 'Cairo'; font-size: 1rem; font-weight: 600; cursor: pointer; }

        /* مراحل سير العمل الهندسي */
        .timeline-container { max-width: 900px; margin: 40px auto 80px auto; position: relative; padding-right: 30px; }
        .timeline-container::before { content: ''; position: absolute; right: 8px; top: 0; bottom: 0; width: 3px; background: linear-gradient(to bottom, var(--accent-color), rgba(16, 185, 129, 0.1)); border-radius: 2px; }
        .timeline-step { position: relative; margin-bottom: 40px; }
        .timeline-step::before { content: ''; position: absolute; right: -29px; top: 8px; width: 15px; height: 15px; border-radius: 50%; background: var(--main-dark); border: 3px solid var(--accent-color); box-shadow: 0 0 10px var(--accent-color); z-index: 10; }
        .timeline-content { background: var(--card-glass); border: 1px solid var(--border-glass); padding: 25px; border-radius: 16px; backdrop-filter: blur(10px); }
        .timeline-step:hover .timeline-content { border-color: var(--accent-color); transform: translateX(-5px); }
        .timeline-num { font-size: 0.85rem; font-weight: 700; color: var(--accent-color); text-transform: uppercase; margin-bottom: 5px; display: block;}
        .timeline-title { font-size: 1.2rem; font-weight: 700; color: #ffffff; margin: 0 0 10px 0; }
        .timeline-desc { font-size: 0.95rem; color: var(--text-secondary); margin: 0; }

        /* الأسئلة الشائعة الأكورديون */
        .faq-wrapper { max-width: 800px; margin: 40px auto 60px auto; display: flex; flex-direction: column; gap: 15px; }
        .faq-item { background: var(--card-glass); border: 1px solid var(--border-glass); border-radius: 14px; overflow: hidden; cursor: pointer; }
        .faq-question { padding: 20px; display: flex; justify-content: space-between; align-items: center; font-weight: 600; font-size: 1.05rem; }
        .faq-question svg { width: 18px; height: 18px; fill: none; stroke: var(--text-secondary); stroke-width: 2.5; transition: transform 0.3s; }
        .faq-answer { max-height: 0; overflow: hidden; padding: 0 20px; color: var(--text-secondary); font-size: 0.95rem; }
        .faq-item.active { border-color: rgba(16, 185, 129, 0.3); background: rgba(16, 185, 129, 0.02); }
        .faq-item.active .faq-question svg { transform: rotate(180deg); stroke: var(--accent-color); }
        .faq-item.active .faq-answer { max-height: 200px; padding-bottom: 20px; }

        /* بوابة الدفع الإلكتروني */
        .payment-status-container { text-align: center; margin: 60px auto; max-width: 340px; }
        .payment-card { background: rgba(230, 0, 0, 0.03); border: 1px solid rgba(230, 0, 0, 0.15); padding: 30px 20px; border-radius: 24px; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 14px; cursor: pointer; }
        .payment-card:hover { transform: translateY(-5px); border-color: var(--vodafone-color); background: rgba(230, 0, 0, 0.06); box-shadow: 0 20px 40px rgba(230, 0, 0, 0.15); }
        .wallet-icon-glow { width: 65px; height: 65px; background: var(--vodafone-color); border-radius: 50%; display: flex; align-items: center; justify-content: center; box-shadow: 0 0 25px rgba(230, 0, 0, 0.4); }
        .wallet-icon-glow svg { width: 32px; height: 32px; fill: none; stroke: #ffffff; stroke-width: 2; }

        /* قسم التعليقات المطور - الأيقونة العائمة المتحركة بنبضات هادئة */
        .comments-fab {
            position: fixed;
            bottom: 30px; right: 30px; width: 60px; height: 60px;
            background: var(--accent-color); border-radius: 50%; display: flex;
            align-items: center; justify-content: center; cursor: pointer;
            z-index: 1500;
            box-shadow: 0 10px 30px var(--accent-glow); animation: fabPulse 2s infinite;
        }
        .comments-fab:hover { transform: scale(1.1); background: #34d399; }
        .comments-fab svg { width: 26px; height: 26px; fill: #000000; }
        
        @keyframes fabPulse {
            0% { box-shadow: 0 0 0 0 rgba(16, 185, 129, 0.5); }
            70% { box-shadow: 0 0 0 15px rgba(16, 185, 129, 0); }
            100% { box-shadow: 0 0 0 0 rgba(16, 185, 129, 0); }
        }

        /* الدرج أو اللوحة الجانبية للتعليقات المتراكمة */
        .comments-drawer {
            position: fixed;
            top: 0; right: -380px; width: 360px; height: 100%;
            background: rgba(7, 11, 22, 0.98); backdrop-filter: blur(20px);
            border-left: 1px solid var(--border-glass);
            z-index: 2500; padding: 30px 20px;
            display: flex; flex-direction: column; gap: 20px; box-shadow: -20px 0 50px rgba(0,0,0,0.7);
        }
        .comments-drawer.open { right: 0; }
        @media (max-width: 400px) { .comments-drawer { width: 100%; right: -100%; } .comments-drawer.open { right: 0; } }

        .comments-header { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--border-glass); padding-bottom: 15px; }
        .comments-title { font-size: 1.2rem; font-weight: 700; color: white; display: flex; align-items: center; gap: 8px; }
        .comments-count-badge { background: rgba(16, 185, 129, 0.15); color: var(--accent-color); font-size: 0.85rem; padding: 2px 10px; border-radius: 20px; font-weight: 700; }
        .close-comments-btn { background: transparent; border: none; cursor: pointer; color: var(--text-secondary); font-size: 1.3rem; }
        .close-comments-btn:hover { color: white; }

        /* نموذج إرسال الآراء والتعليقات */
        .comment-form { display: flex; flex-direction: column; gap: 12px; }
        .comment-input, .comment-textarea {
            width: 100%;
            background: rgba(255,255,255,0.03); border: 1px solid var(--border-glass);
            border-radius: 10px; padding: 12px; color: white; font-family: 'Cairo'; font-size: 0.9rem;
        }
        .comment-textarea { resize: none; height: 80px; }
        .comment-input:focus, .comment-textarea:focus { border-color: var(--accent-color); outline: none; background: rgba(255,255,255,0.05); }
        .comment-submit-btn {
            background: var(--accent-color);
            color: #000000; font-family: 'Cairo'; font-weight: 700;
            padding: 10px; border: none; border-radius: 10px; cursor: pointer; font-size: 0.95rem;
        }
        .comment-submit-btn:hover { background: #34d399; transform: translateY(-2px); }

        /* حاوية التعليقات المتراكمة المحدثة لدنيا */
        .comments-list-box { flex-grow: 1; overflow-y: auto; display: flex; flex-direction: column; gap: 15px; padding-right: 5px; }
        .comments-list-box::-webkit-scrollbar { width: 4px; }
        .comments-list-box::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.1); border-radius: 10px; }
        
        .single-comment-card {
            background: rgba(255,255,255,0.02);
            border: 1px solid var(--border-glass);
            padding: 15px; border-radius: 12px; position: relative;
        }
        .comment-user-meta { display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px; }
        .comment-username { font-weight: 700; color: var(--accent-color); font-size: 0.95rem; }
        .comment-date { font-size: 0.75rem; color: var(--text-secondary); }
        .comment-text-content { color: #e5e7eb; font-size: 0.9rem; margin: 0; word-break: break-word; }
        
        .empty-comments-notice { text-align: center; color: var(--text-secondary); font-size: 0.95rem; padding: 30px 10px; }

        /* قسم التواصل التفاعلي */
        .contact-section { background: radial-gradient(ellipse at bottom, #111827 0%, var(--main-dark) 100%); border: 1px solid rgba(255, 255, 255, 0.03); padding: 80px 20px; text-align: center; border-radius: 32px; margin-top: 40px; }
        .whatsapp-link { display: inline-flex; align-items: center; justify-content: center; background-color: #25d366; color: white; padding: 16px 45px; font-size: 1.2rem; font-weight: 700; text-decoration: none; border-radius: 50px; box-shadow: 0 10px 25px rgba(37, 211, 102, 0.3); }
        .whatsapp-link:hover { transform: scale(1.05) translateY(-3px); background-color: #20ba5a; box-shadow: 0 15px 30px rgba(37, 211, 102, 0.4); }

        /* النوافذ المنبثقة */
        .modal { display: none; position: fixed; z-index: 3000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(3, 7, 18, 0.9); align-items: center; justify-content: center; backdrop-filter: blur(12px); }
        .modal-content { background-color: #0b0f19; border: 1px solid rgba(255, 255, 255, 0.08); padding: 35px; border-radius: 24px; width: 90%; max-width: 440px; text-align: center; box-shadow: 0 30px 70px rgba(0,0,0,0.8); }
        .close-btn { background: rgba(255, 255, 255, 0.04); color: #9ca3af; border: 1px solid rgba(255, 255, 255, 0.05); width: 100%; padding: 14px; border-radius: 12px; cursor: pointer; font-weight: 600; margin-top: 15px; font-family: 'Cairo'; }
        .close-btn:hover { background: rgba(255, 255, 255, 0.08); color: #ffffff; }

        /* القائمة الجانبية */
        .side-drawer { position: fixed; top: 0; left: -320px; width: 300px; height: 100%; background: rgba(5, 8, 17, 0.95); backdrop-filter: blur(20px); border-right: 1px solid rgba(255, 255, 255, 0.05); z-index: 2000; padding: 40px 24px; display: flex; flex-direction: column; gap: 40px; box-shadow: 20px 0 50px rgba(0, 0, 0, 0.8); }
        .side-drawer.open { left: 0; }
        .drawer-header { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid rgba(255, 255, 255, 0.08); padding-bottom: 15px; }
        .drawer-title { font-size: 1.2rem; font-weight: 700; color: var(--accent-color); }
        .close-drawer-btn { background: transparent; border: none; cursor: pointer; }
        .close-drawer-btn svg { width: 24px; height: 24px; stroke: var(--text-secondary); stroke-width: 2; }
        .drawer-menu { list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 15px; }
        .drawer-item a { display: flex; align-items: center; gap: 15px; color: #cbd5e1; text-decoration: none; font-size: 1.1rem; font-weight: 600; padding: 12px 16px; border-radius: 12px; background: rgba(255, 255, 255, 0.01); }
        .drawer-item a:hover { color: #ffffff; background: rgba(16, 185, 129, 0.1); padding-right: 22px; }
        .drawer-item svg { width: 20px; height: 20px; stroke: var(--accent-color); stroke-width: 2; fill: none; }
        .drawer-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.7); backdrop-filter: blur(5px); z-index: 1999; }
        .drawer-overlay.show { display: block; }

        /* المكعب ثلاثي الأبعاد */
        .cube-scene { width: 100px; height: 100px; perspective: 400px; margin-bottom: 10px; }
        .cube { width: 100%; height: 100%; position: relative; transform-style: preserve-3d; animation: rotateCube 16s infinite linear; }
        .cube-face { position: absolute; width: 100px; height: 100px; border: 1.5px solid var(--accent-color); background: rgba(16, 185, 129, 0.08); box-shadow: inset 0 0 15px rgba(16, 185, 129, 0.15); }
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

        /* سلايدر استعراض الصور */
        .lightbox-content { position: relative; max-width: 850px; width: 92%; display: flex; flex-direction: column; align-items: center; gap: 15px; }
        .lightbox-image-container { position: relative; display: flex; align-items: center; justify-content: center; width: 100%; background: #020408; border-radius: 20px; overflow: hidden; border: 1px solid rgba(255,255,255,0.08); }
        .lightbox-image-container img { max-width: 100%; max-height: 72vh; object-fit: contain; display: block; }
        .nav-arrow { position: absolute; top: 50%; transform: translateY(-50%); background: rgba(15, 23, 42, 0.8); border: 1px solid rgba(255,255,255,0.1); color: white; width: 50px; height: 50px; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center; }
        .nav-arrow:hover { background: var(--accent-color); box-shadow: 0 0 15px var(--accent-glow); }
        .prev-arrow { right: 20px; }
        .next-arrow { left: 20px; }
        .lightbox-close { position: absolute; top: -50px; left: 0; background: rgba(255,255,255,0.1); border: none; color: white; font-size: 1.2rem; cursor: pointer; width: 40px; height: 40px; border-radius: 50%; display: flex; align-items: center; justify-content: center; }
        .lightbox-counter { color: var(--text-primary); background: rgba(255,255,255,0.05); padding: 6px 20px; border-radius: 30px; font-weight: 600; }

        footer { text-align: center; padding: 40px 20px; color: #4b5563; font-size: 0.95rem; border-top: 1px solid var(--border-glass); margin-top: 40px; }
    </style>
</head>
<body>
    <div class="custom-cursor" id="customCursor"></div>
    <div class="drawer-overlay" id="drawerOverlay" onclick="toggleDrawer(false)"></div>
    <div class="drawer-overlay" id="commentsOverlay" onclick="toggleCommentsDrawer(false)"></div>

    <div class="comments-fab" onclick="toggleCommentsDrawer(true)" title="شاهد تعليقات وآراء العملاء والطلاب">
        <svg viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zM6 9h12v2H6V9zm8 5H6v-2h8v2zm4-6H6V6h12v2z"/></svg>
    </div>

    <div class="comments-drawer" id="commentsDrawer">
        <div class="comments-header">
            <div class="comments-title">
                <span>آراء وتعليقات الزوار</span>
                <span class="comments-count-badge" id="commentCount">0</span>
            </div>
            <button class="close-comments-btn" onclick="toggleCommentsDrawer(false)">✕</button>
        </div>
        
        <div class="comments-list-box" id="commentsListBox">
            </div>

        <div class="comment-form">
            <input type="text" id="commenterName" class="comment-input" placeholder="الاسم الكريم...">
            <textarea id="commenterText" class="comment-textarea" placeholder="اكتب تعليقك أو رأيك هنا..."></textarea>
            <button class="comment-submit-btn" onclick="addNewComment()">إرسال التعليق وثباته</button>
        </div>
    </div>

    <nav class="side-drawer" id="sideDrawer">
        <div class="drawer-header">
            <div class="drawer-title">خريطة المنصة</div>
            <button class="close-drawer-btn" onclick="toggleDrawer(false)">
                <svg viewBox="0 0 24 24" fill="none"><path d="M6 18L18 6M6 6l12 12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </button>
        </div>
        <ul class="drawer-menu">
            <li class="drawer-item"><a href="#" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/></svg>الرئيسية</a></li>
            <li class="drawer-item"><a href="#studentProjects" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M12 3L1 9l11 6 9-4.91V17h2V9L12 3z"/></svg>مشاريع الطلاب</a></li>
            <li class="drawer-item"><a href="#calc" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-2 10H7v-2h10v2zm0-4H7V7h10v2z"/></svg>حاسبة التكلفة</a></li>
            <li class="drawer-item"><a href="#workflow" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M23 8c0 1.1-.9 2-2 2-.18 0-.35-.02-.51-.07l-3.56 3.55c.05.16.07.33.07.52 0 1.1-.9 2-2 2s-2-.9-2-2c0-.19.02-.36.07-.52l-2.55-2.55c-.16.05-.33.07-.52.07s-.36-.02-.52-.07l-4.55 4.56c.05.16.07.33.07.51 0 1.1-.9 2-2 2s-2-.9-2-2 .9-2 2-2c.18 0 .35.02.51.07l4.56-4.55C8.02 9.36 8 9.19 8 9c0-1.1.9-2 2-2s2 .9 2 2c0 .19-.02.36-.07.52l2.55 2.55c.16-.05.33-.07.52-.07s.36.02.52.07l3.55-3.56C19.02 6.35 19 6.18 19 6c0-1.1.9-2 2-2s2 .9 2 2z"/></svg>سير العمل الهندسي</a></li>
            <li class="drawer-item"><a href="#contact" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>تواصل معي</a></li>
        </ul>
    </nav>

    <header>
        <div class="top-nav-bar">
            <button class="menu-toggle-btn" onclick="toggleDrawer(true)">
                <svg viewBox="0 0 24 24" fill="none"><path d="M4 6h16M4 12h16M4 18h16" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </button>
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
        </div>
        <h1>المهندس محمد الحارون</h1>
        <p>مـعـمـاري ومـصـمـم تـفـاعـلـي | نبتكر الفراغات برؤية هندسية معاصرة تدمج الوظيفة بالجمال التكنولوجي الساحر.</p>
    </header>

    <div class="container">
        <section class="about-section">
            <h2 style="margin-top:0; color:#fff; font-size:1.6rem; margin-bottom:15px;">من نحن؟</h2>
            <p style="margin:0; color:var(--text-secondary); font-size:1.05rem;">نحن نقدم حلولاً هندسية متكاملة تبدأ من دراسة الـ Concept الأولي للمشروع وتطوير الفكرة التصميمية، مروراً بكافة الرسومات التنفيذية التفصيلية وحسابات المساحات بدقة متناهية، وصولاً إلى إخراج اللوحات والبانرات النهائية بأعلى جودة بصرية معمارية تضمن تميز مشاريعكم في المحافل الأكاديمية والمهنية.</p>
        </section>

        <div class="section-title" id="studentProjects">خدمات مشاريع الطلاب</div>
        <div class="section-subtitle">مزنوق في الفاينل؟ شايل هم الإخراج والرصة؟ بنشيل عنك العبء وبنحول أفكارك للوحات مبهرة</div>

        <section class="students-section">
            <div class="students-grid">
                <div class="student-service-card">
                    <h3><svg viewBox="0 0 24 24"><path d="M12 2L2 22h20L12 2zm0 3.99L19.53 19H4.47L12 5.99z"/></svg>تطوير الفكرة المعمارية (Concept)</h3>
                    <p>نساعدك في بلورة وترجمة فكرتك الفلسفية إلى خطوط وتكتيلات معمارية قوية ومقنعة للجنة التحكيم.</p>
                </div>
                <div class="student-service-card">
                    <h3><svg viewBox="0 0 24 24"><path d="M4 6H2v14c0 1.1.9 2 2 2h14v-2H4V6zm16-4H8c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm0 14H8V4h12v12z"/></svg>الرسومات التنفيذية (Working Drawings)</h3>
                    <p>إعداد المساقط الأفقية، الواجهات، والقطاعات التفصيلية المطابقة للمواصفات القياسية بدقة تامة.</p>
                </div>
                <div class="student-service-card">
                    <h3><svg viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-2 10H7v-2h10v2zm0-4H7V7h10v2z"/></svg>حساب المساحات والدراسات</h3>
                    <p>عمل الجداول التحليلية الدقيقة للمساحات، النسب البنائية، وحسابات الـ Zoning للمشروع بالكامل.</p>
                </div>
                <div class="student-service-card">
                    <h3><svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 17h-2v-2h2v2zm2.07-7.75l-.9.92C13.45 12.9 13 13.5 13 15h-2v-.5c0-1.1.45-2.1 1.17-2.83l1.24-1.26c.37-.36.59-.86.59-1.41 0-1.1-.9-2-2-2s-2 .9-2 2H7c0-2.76 2.24-5 5-5s5 2.24 5 5c0 1.04-.42 1.99-1.07 2.75z"/></svg>إخراج البانر النهائي (Post-Production)</h3>
                    <p>تجميع عناصر المشروع وترتيبها في شيتات وبانرات تخرج احترافية ومبهرة بصرياً تشد العين مباشرة.</p>
                </div>
            </div>
            
            <div class="programs-container">
                <div class="program-badge">AutoCAD <span>2D/3D</span></div>
                <div class="program-badge">Revit <span>BIM</span></div>
                <div class="program-badge">3ds Max <span>V-Ray</span></div>
                <div class="program-badge">Photoshop <span>Architecture</span></div>
                <div class="program-badge">Lumion <span>Render</span></div>
            </div>
        </section>

        <div class="skills-grid">
            <div class="skill-card">التصميم المعماري المستدام</div>
            <div class="skill-card">الإظهار المعماري الاحترافي</div>
            <div class="skill-card">إعداد المخططات التنفيذية الكاملة</div>
            <div class="skill-card">التخطيط العمراني وتصميم المواقع</div>
        </div>

        <div class="section-title">معرض المشاريع البصرية</div>
        <div class="section-subtitle">انقر على أي مشروع لاستعراض صوره الهندسية في نافذة تفاعلية مكبرة</div>

        <div class="photo-gallery">
            <div class="circle-project" onclick="openGalleryLightbox(1)">
                <img src="https://g.top4top.io/p_38289k2v61.jpg" alt="المشروع الأول">
                <div class="circle-overlay">مشروع السكن المعاصر <span>اضغط للعرض 👁️</span></div>
            </div>
            <div class="circle-project" onclick="openGalleryLightbox(2)">
                <img src="https://h.top4top.io/p_3828kfxcl1.jpg" alt="المشروع الثاني">
                <div class="circle-overlay">المركز الثقافي الذكي <span>اضغط للعرض 👁️</span></div>
            </div>
        </div>

        <div class="section-title" id="calc">حاسبة التكلفة الهندسية الذكية</div>
        <div class="section-subtitle">احسب تكلفة مشروعك المعماري والوقت المتوقع فوراً وبشفافية كاملة</div>

        <section class="calculator-section">
            <div class="currency-switch-wrapper">
                <button class="currency-btn active" id="btnEGP" onclick="switchCurrency('EGP')">EGP (جنيه)</button>
                <button class="currency-btn" id="btnUSD" onclick="switchCurrency('USD')">USD ($)</button>
            </div>
            
            <div class="calc-grid">
                <div class="calc-field">
                    <label>نوع الخدمة أو الباقة المطلوبة</label>
                    <select id="calcPackage" onchange="calculateProjectCost()">
                        <option value="45">تصميم خارجي مبدئي (3D Facades) - 45 للمتر</option>
                        <option value="75" selected>تصميم خارجي متكامل ومخططات - 75 للمتر</option>
                        <option value="110">تصميم داخلي وتوزيع فراغات (Interior) - 110 للمتر</option>
                        <option value="140">الباقة الذهبية (داخلي + خارجي + لاندسكيب) - 140 للمتر</option>
                        <option value="35">التخطيط العمراني وتصميم المواقع (Urban) - 35 للمتر</option>
                    </select>
                </div>
                <div class="calc-field">
                    <label>مساحة الأرض / المبنى الإجمالية (متر مربع)</label>
                    <input type="number" id="calcArea" value="200" min="20" oninput="calculateProjectCost()">
                </div>

                <div class="live-stats-panel">
                    <div class="stat-box">
                        <div class="stat-value" id="statDays">0</div>
                        <div class="stat-label">أيام عمل متوقعة</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value" id="statDrawings">0</div>
                        <div class="stat-label">لوحة هندسية تقديرية</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value" id="statRevisions">3</div>
                        <div class="stat-label">تعديلات مجانية متاحين</div>
                    </div>
                </div>

                <div class="calc-full-width">
                    <div class="calc-result-box">
                        <div style="font-size:1.05rem; color:var(--text-secondary);">التكلفة الإجمالية التقديرية للمشروع</div>
                        <div class="calc-price" id="calcTotalPrice">0 جنيه</div>
                        <p style="font-size:0.85rem; color:var(--text-secondary); margin:5px 0 15px 0;">السعر نهائي ويشمل اللوحات المتفق عليها والتسليم بصيغ متعددة.</p>
                        <button class="submit-auth-btn comment-submit-btn" onclick="openPaymentModal()">احجز مشروعك واشحن الآن</button>
                    </div>
                </div>
            </div>
        </section>

        <div class="section-title" id="workflow">مراحل سير العمل المعماري</div>
        <div class="section-subtitle">آلية عمل هندسية دقيقة تضمن تحويل حلمك إلى حقيقة مدروسة وقابلة للتنفيذ</div>

        <div class="timeline-container">
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 01</span>
                    <h4 class="timeline-title">جمع البيانات واستلام المتطلبات (Briefing)</h4>
                    <p class="timeline-desc">نجلس معك لمناقشة الاحتياجات، فكرة المشروع، دراسة طبيعة الأرض، وتحديد الأهداف والأنماط المعمارية المفضلة لديك.</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 02</span>
                    <h4 class="timeline-title">التصميم المبدئي وتطوير الفكرة (Concept & 2D)</h4>
                    <p class="timeline-desc">نقوم بإعداد المساقط الأفقية وتوزيع الفراغات المعمارية بشكل أولي مع تقديم خطوط الـ Concept العامة لمناقشتها وتعديلها.</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 03</span>
                    <h4 class="timeline-title">النمذجة ثلاثية الأبعاد والإظهار (3D Modeling & Rendering)</h4>
                    <p class="timeline-desc">نرفع المشروع إلى مجسم ثلاثي أبعاد كامل لترى التفاصيل، المواد، الألوان، والإضاءة بواقعية مذهلة قبل أي خطوة تنفيذية.</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 04</span>
                    <h4 class="timeline-title">اللوحات التنفيذية وشيتات التسليم (Working Drawings)</h4>
                    <p class="timeline-desc">نصدر المخططات التفصيلية النهائية، القطاعات، الجداول، ورص اللوحات والبانرات الجاهزة للطباعة والتسليم الفوري.</p>
                </div>
            </div>
        </div>

        <div class="section-title">الأسئلة الشائعة (FAQ)</div>
        <div class="section-subtitle">إجابات هندسية سريعة ومباشرة على أكثر الاستفسارات التي تدور في ذهنك</div>

        <div class="faq-wrapper">
            <div class="faq-item" onclick="toggleFaq(this)">
                <div class="faq-question">ما هي البيانات المطلوبة لبدء العمل في مشروعي؟ <svg viewBox="0 0 24 24"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"/></svg></div>
                <div class="faq-answer">نحتاج أبعاد الأرض الكروكية، المتطلبات الأساسية (كم غرفة، كم دور)، وأي طراز معماري تفضله أو صور ملهمة تعجبك لبناء الفكرة عليها.</div>
            </div>
            <div class="faq-item" onclick="toggleFaq(this)">
                <div class="faq-question">هل يمكنني تعديل التصميم بعد استلامه؟ <svg viewBox="0 0 24 24"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"/></svg></div>
                <div class="faq-answer">نعم، جميع الباقات تمنحك تعديلات مجانية مرنة أثناء المراحل الأساسية لضمان خروج المشروع بالشكل الذي يرضيك تماماً.</div>
            </div>
            <div class="faq-item" onclick="toggleFaq(this)">
                <div class="faq-question">كيف يتم استلام الملفات واللوحات النهائية؟ <svg viewBox="0 0 24 24"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"/></svg></div>
                <div class="faq-answer">يتم تسليمك ملفات رقمية عالية الجودة بصيغة PDF جاهزة للطباعة مباشرة، بالإضافة إلى الملفات المصدرية الأصلية (DWG أو RVT) حسب نوع الاتفاق.</div>
            </div>
        </div>

        <div class="section-title">بوابة الشحن المالي المباشر</div>
        <div class="section-subtitle">اشحن قيمة باقتك فوراً عبر فودافون كاش لربط المعاملة وبدء حجز المهندس وتثبيت موعدك</div>

        <div class="payment-status-container">
            <div class="payment-card" onclick="openPaymentModal()">
                <div class="wallet-icon-glow">
                    <svg viewBox="0 0 24 24"><path d="M21 18v1c0 1.1-.9 2-2 2H5c-1.11 0-2-.9-2-2V5c0-1.1.89-2 2-2h14c1.1 0 2 .9 2 2v1h-9c-1.11 0-2 .9-2 2v8c0 1.1.89 2 2 2h9zm-9-2h10V8H12v8zm4-2.5c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5z"/></svg>
                </div>
                <h4 style="margin:0; font-size:1.15rem; color:#ffffff;">فودافون كاش (Vodafone Cash)</h4>
                <p style="margin:0; font-size:0.85rem; color:var(--text-secondary);">اضغط لشحن الحساب وتأكيد التعاقد</p>
            </div>
        </div>

        <section class="contact-section" id="contact">
            <h2 style="margin-top:0; font-size:2rem; margin-bottom:10px;">هل أنت جاهز لبدء مشروعك الآن؟</h2>
            <p style="color:var(--text-secondary); max-width:600px; margin:0 auto 35px auto; font-size:1.1rem;">اضغط على الزر أدناه لفتح محادثة مباشرة تفاعلية عبر واتساب مع المهندس محمد الحارون لمناقشة تفاصيل وأفكار مشروعك فوراً.</p>
            <a href="https://wa.me/201021469502" target="_blank" class="whatsapp-link">تواصل عبر الواتساب الفوري 💬</a>
        </section>
    </div>

    <div class="modal" id="galleryLightbox">
        <div class="lightbox-content">
            <button class="lightbox-close" onclick="closeGalleryLightbox()">✕</button>
            <div class="lightbox-image-container">
                <button class="nav-arrow prev-arrow" onclick="changeLightboxImage(1)">❯</button>
                <img id="lightboxImg" src="" alt="صورة المعرض المعماري المكبرة">
                <button class="nav-arrow next-arrow" onclick="changeLightboxImage(-1)">❮</button>
            </div>
            <div class="lightbox-counter" id="lightboxCounter">1 / 1</div>
        </div>
    </div>

    <div class="modal" id="paymentModal">
        <div class="modal-content">
            <div class="wallet-icon-glow" style="margin:0 auto 20px auto;">
                <svg viewBox="0 0 24 24"><path d="M21 18v1c0 1.1-.9 2-2 2H5c-1.11 0-2-.9-2-2V5c0-1.1.89-2 2-2h14c1.1 0 2 .9 2 2v1h-9c-1.11 0-2 .9-2 2v8c0 1.1.89 2 2 2h9zm-9-2h10V8H12v8zm4-2.5c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5z"/></svg>
            </div>
            <h3 style="margin:0 0 10px 0; color:white;">رقم الشحن والتحويل المباشر</h3>
            <p style="color:var(--text-secondary); font-size:0.95rem; margin:0 0 20px 0;">يرجى تحويل المبلغ المستحق التقديري أو العربون إلى الرقم التالي:</p>
            <div style="background:rgba(230, 0, 0, 0.1); border:1px dashed var(--vodafone-color); color:white; font-size:1.5rem; font-weight:700; padding:12px; border-radius:12px; letter-spacing:1px; margin-bottom:20px;">
                01021469502
            </div>
            <p style="color:var(--accent-color); font-size:0.85rem; margin:0 0 10px 0; font-weight:600;">* بعد إتمام التحويل، أرسل لقطة شاشة (Screenshot) للرسالة عبر الواتساب لتفعيل وحجز المشروع فوراً.</p>
            <button class="close-btn" onclick="closePaymentModal()">إغلاق النافذة</button>
        </div>
    </div>

    <footer>
        حقوق النشر والطبع محفوظة © 2026 | تصميم وتطوير منصة المهندس محمد الحارون التفاعلية المعمارية.
    </footer>

    <script>
        // مؤشر الماوس
        const cursor = document.getElementById('customCursor');
        document.addEventListener('mousemove', (e) => {
            if(cursor) { cursor.style.left = e.clientX + 'px'; cursor.style.top = e.clientY + 'px'; }
        });

        // التبديل والتحكم بالقوائم واللوحات الجانبية
        function toggleDrawer(open) {
            document.getElementById('sideDrawer').classList.toggle('open', open);
            document.getElementById('drawerOverlay').classList.toggle('show', open);
        }
        function toggleCommentsDrawer(open) {
            document.getElementById('commentsDrawer').classList.toggle('open', open);
            document.getElementById('commentsOverlay').classList.toggle('show', open);
            if(open) { displayComments(); }
        }

        // الأكورديون للأسئلة
        function toggleFaq(element) {
            const isActive = element.classList.contains('active');
            document.querySelectorAll('.faq-item').forEach(item => item.classList.remove('active'));
            if (!isActive) element.classList.add('active');
        }

        // نوافذ الدفع والشحن
        function openPaymentModal() { document.getElementById('paymentModal').style.display = 'flex'; }
        function closePaymentModal() { document.getElementById('paymentModal').style.display = 'none'; }

        // نظام احتساب وتثبيت العملات والأسعار
        let currentCurrency = 'EGP';
        let currentExchangeRate = 50; 

        function switchCurrency(currency) {
            currentCurrency = currency;
            document.getElementById('btnEGP').classList.toggle('active', currency === 'EGP');
            document.getElementById('btnUSD').classList.toggle('active', currency === 'USD');
            calculateProjectCost();
        }

        function calculateProjectCost() {
            const basePricePerMeter = parseFloat(document.getElementById('calcPackage').value);
            const area = parseFloat(document.getElementById('calcArea').value) || 0;
            
            if(area <= 0) {
                document.getElementById('calcTotalPrice').innerText = currentCurrency === 'EGP' ? '0 جنيه' : '0 $';
                document.getElementById('statDays').innerText = '0';
                document.getElementById('statDrawings').innerText = '0';
                return;
            }

            // حساب السعر الإجمالي الأساسي بالجنيه المصري
            let totalPriceInEGP = basePricePerMeter * area;
            
            // معادلة الـ scaleFactor المعتمدة على المساحة لعدم تضخم الأيام بشكل عشوائي
            const scaleFactor = Math.sqrt(area / 100);
            
            let days = Math.round(7 * scaleFactor);
            let drawings = Math.round(5 * scaleFactor);
            
            if(days < 3) days = 3;
            if(drawings < 2) drawings = 2;

            document.getElementById('statDays').innerText = days;
            document.getElementById('statDrawings').innerText = drawings;

            if (currentCurrency === 'USD') {
                let totalPriceInUSD = Math.round(totalPriceInEGP / currentExchangeRate);
                document.getElementById('calcTotalPrice').innerText = totalPriceInUSD + ' $';
            } else {
                document.getElementById('calcTotalPrice').innerText = Math.round(totalPriceInEGP).toLocaleString('ar-EG') + ' جنيه';
            }
        }

        // نظام التعليقات المحلي (LocalStorage) المعتمد كلياً على مدخلات زوارك فقط
        function addNewComment() {
            const nameInput = document.getElementById('commenterName');
            const textInput = document.getElementById('commenterText');
            const name = nameInput.value.trim();
            const text = textInput.value.trim();

            if(!name || !text) { alert('من فضلك املأ حقل الاسم والتعليق الكريم أولاً.'); return; }

            const newComment = {
                id: Date.now(),
                username: name,
                commentText: text,
                dateString: new Date().toLocaleDateString('ar-EG', {hour: '2-digit', minute:'2-digit'})
            };

            let commentsList = JSON.parse(localStorage.getItem('haroun_user_comments')) || [];
            commentsList.unshift(newComment);
            localStorage.setItem('haroun_user_comments', JSON.stringify(commentsList));

            nameInput.value = '';
            textInput.value = '';
            displayComments();
        }

        function displayComments() {
            const container = document.getElementById('commentsListBox');
            let commentsList = JSON.parse(localStorage.getItem('haroun_user_comments')) || [];
            document.getElementById('commentCount').innerText = commentsList.length;

            if(commentsList.length === 0) {
                container.innerHTML = `<div class="empty-comments-notice">لا توجد آراء مكتوبة حالياً. كن أول من يكتب تعليقاً أو رأياً معمارياً كريمًا!</div>`;
                return;
            }

            container.innerHTML = commentsList.map(item => `
                <div class="single-comment-card">
                    <div class="comment-user-meta">
                        <span class="comment-username">${escapeHtml(item.username)}</span>
                        <span class="comment-date">${item.dateString}</span>
                    </div>
                    <p class="comment-text-content">${escapeHtml(item.commentText)}</p>
                </div>
            `).join('');
        }

        function escapeHtml(text) {
            return text.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/"/g, "&quot;").replace(/'/g, "&#039;");
        }

        // معرض اللايتبوكس التفاعلي للصور المعمارية المرفوعة
        const projectGalleries = {
            1: ["https://g.top4top.io/p_38289k2v61.jpg", "https://i.top4top.io/p_3828nlyg81.jpg", "https://g.top4top.io/p_38288wnor1.jpg", "https://g.top4top.io/p_3828f4bqz1.jpg"],
            2: ["https://h.top4top.io/p_3828kfxcl1.jpg", "https://k.top4top.io/p_3828clele1.jpg", "https://c.top4top.io/p_3828gvugl1.jpg", "https://k.top4top.io/p_3828qrim11.jpg", "https://b.top4top.io/p_3828lgvbq1.jpg"]
        };
        let activeProjectId = 1, activeImageIndex = 0;

        function openGalleryLightbox(projectId) { activeProjectId = projectId; activeImageIndex = 0; updateLightboxUI(); document.getElementById('galleryLightbox').style.display = 'flex'; }
        function closeGalleryLightbox() { document.getElementById('galleryLightbox').style.display = 'none'; }
        function changeLightboxImage(direction) { const imagesList = projectGalleries[activeProjectId]; activeImageIndex += direction; if (activeImageIndex >= imagesList.length) activeImageIndex = 0; else if (activeImageIndex < 0) activeImageIndex = imagesList.length - 1; updateLightboxUI(); }
        function updateLightboxUI() { const imagesList = projectGalleries[activeProjectId]; document.getElementById('lightboxImg').src = imagesList[activeImageIndex]; document.getElementById('lightboxCounter').innerText = (activeImageIndex + 1) + " / " + imagesList.length; }

        // تشغيل الحاسبة بشكل تلقائي عند تحميل الصفحة للمرة الأولى
        window.addEventListener('DOMContentLoaded', () => {
            calculateProjectCost();
        });
    </script>
</body>
</html>
