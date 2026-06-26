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
            background: var(--card-glass); backdrop-filter: blur(12px);
            padding: 40px; border-radius: 24px; box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            margin-bottom: 60px; border: 1px solid var(--border-glass); border-right: 5px solid var(--accent-color);
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
            background: rgba(5, 8, 17, 0.6); border: 1px solid var(--border-glass); 
            padding: 25px; border-radius: 16px;
        }
        .student-service-card:hover { border-color: var(--accent-color); transform: translateY(-4px); }
        .student-service-card h3 { color: #ffffff; font-size: 1.25rem; margin-top: 0; margin-bottom: 12px; display: flex; align-items: center; gap: 10px; }
        .student-service-card h3 svg { width: 22px; height: 22px; fill: var(--accent-color); }
        .student-service-card p { color: var(--text-secondary); font-size: 0.95rem; margin: 0; }
        
        .programs-container { display: flex; flex-wrap: wrap; justify-content: center; gap: 15px; margin-top: 35px; }
        .program-badge {
            background: rgba(255, 255, 255, 0.03); border: 1px solid var(--border-glass);
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
            background: var(--card-glass); border: 1px solid var(--border-glass);
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
            width: 100%; padding: 14px; background: rgba(5,8,17,0.7);
            border: 1px solid rgba(255,255,255,0.08); border-radius: 12px;
            color: white; font-family: 'Cairo'; font-size: 0.95rem;
        }
        .calc-field select:focus, .calc-field input:focus { border-color: var(--accent-color); outline: none; }
        .calc-full-width { grid-column: span 2; }
        
        .currency-switch-wrapper { display: flex; justify-content: flex-end; gap: 10px; margin-bottom: -10px; }
        .currency-btn {
            background: rgba(255,255,255,0.03); border: 1px solid var(--border-glass); color: var(--text-secondary);
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
            position: fixed; bottom: 30px; right: 30px; width: 60px; height: 60px;
            background: var(--accent-color); border-radius: 50%; display: flex;
            align-items: center; justify-content: center; cursor: pointer; z-index: 1500;
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
            position: fixed; top: 0; right: -380px; width: 360px; height: 100%;
            background: rgba(7, 11, 22, 0.98); backdrop-filter: blur(20px);
            border-left: 1px solid var(--border-glass); z-index: 2500; padding: 30px 20px;
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
            width: 100%; background: rgba(255,255,255,0.03); border: 1px solid var(--border-glass);
            border-radius: 10px; padding: 12px; color: white; font-family: 'Cairo'; font-size: 0.9rem;
        }
        .comment-textarea { resize: none; height: 80px; }
        .comment-input:focus, .comment-textarea:focus { border-color: var(--accent-color); outline: none; background: rgba(255,255,255,0.05); }
        .comment-submit-btn {
            background: var(--accent-color); color: #000000; font-family: 'Cairo'; font-weight: 700;
            padding: 10px; border: none; border-radius: 10px; cursor: pointer; font-size: 0.95rem;
        }
        .comment-submit-btn:hover { background: #34d399; transform: translateY(-2px); }

        /* حاوية التعليقات المتراكمة المحدثة لدنيا */
        .comments-list-box { flex-grow: 1; overflow-y: auto; display: flex; flex-direction: column; gap: 15px; padding-right: 5px; }
        .comments-list-box::-webkit-scrollbar { width: 4px; }
        .comments-list-box::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.1); border-radius: 10px; }
        
        .single-comment-card {
            background: rgba(255,255,255,0.02); border: 1px solid var(--border-glass);
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
        @keyframes rotateCube { 0% { transform: rotateX(0deg) rotateY(0deg); } 100% { transform: rotateX(360deg) rotateY(360deg); } }

        /* سلايدر استعراض الصور */
        .lightbox-content { position: relative; max-width: 850px; width: 92%; display: flex; flex-direction: column; align-items: center; gap: 15px; }
        .lightbox-image-container { position: relative; display: flex; align-items: center; justify-content: center; width: 100%; background: #020408; border-radius: 20px; overflow: hidden; border: 1px solid rgba(255,255,255,0.08); }
        .lightbox-image-container img { max-width: 100%; max-height: 72vh; object-fit: contain; display: block; }
        .nav-arrow { position: absolute; top: 50%; transform: translateY(-50%); background: rgba(15, 23, 42, 0.8); border: 1px solid rgba(255,255,255,0.1); color: white; width: 50px; height: 50px; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center; }
        .nav-arrow:hover { background: var(--accent-color); box-shadow: 0 0 15px var(--accent-glow); }
        .prev-arrow { right: 20px; } .next-arrow { left: 20px; }
        .lightbox-close { position: absolute; top: -50px; left: 0; background: rgba(255,255,255,0.1); border: none; color: white; font-size: 1.2rem; cursor: pointer; width: 40px; height: 40px; border-radius: 50%; display: flex; align-items: center; justify-content: center; }
        .lightbox-counter { color: var(--text-primary); background: rgba(255,255,255,0.05); padding: 6px 20px; border-radius: 30px; font-weight: 600; }

        footer { text-align: center; padding: 40px 20px; color: #4b5563; font-size: 0.95rem; border-top: 1px solid var(--border-glass); margin-top: 40px; }
    </style></head>
    
    <body>

    <div class="custom-cursor" id="customCursor"></div>
    <div class="drawer-overlay" id="drawerOverlay" onclick="toggleDrawer(false)"></div>
    <div class="drawer-overlay" id="commentsOverlay" onclick="toggleCommentsDrawer(false)"></div>

    <!-- الأيقونة المتحركة العائمة للتعليقات الحقيقية المتراكمة -->
    <div class="comments-fab" onclick="toggleCommentsDrawer(true)" title="شاهد تعليقات وآراء العملاء والطلاب">
        <svg viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zM6 9h12v2H6V9zm8 5H6v-2h8v2zm4-6H6V6h12v2z"/></svg>
    </div>

    <!-- لوحة التعليقات المتراكمة الجانبية من المستخدمين فقط -->
    <div class="comments-drawer" id="commentsDrawer">
        <div class="comments-header">
            <div class="comments-title">
                <span>آراء وتعليقات الزوار</span>
                <span class="comments-count-badge" id="commentCount">0</span>
            </div>
            <button class="close-comments-btn" onclick="toggleCommentsDrawer(false)">✕</button>
        </div>

        <!-- قائمة عرض التعليقات -->
        <div class="comments-list-box" id="commentsListBox">
            <!-- فارغ افتراضياً ولا يمتلئ إلا عبر إدخال المستخدمين -->
        </div>

        <!-- نموذج إضافة تعليق جديد -->
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
            <li class="drawer-item"><a href="#" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" stroke-linecap="round" stroke-linejoin="round"/></svg><span>الرئيسية</span></a></li>
            <li class="drawer-item"><a href="#about" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>نبذة عني</span></a></li>
            <li class="drawer-item"><a href="#students" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M12 14l9-5-9-5-9 5 9 5zm0 0l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 14zm-6 1.341c0-1.802.434-3.5 1.196-5L2 13l7 4 1-.57V19a2 2 0 002 2h2a2 2 0 002-2v-2.57l1 .57 1.196-1c.762 1.5 1.196 3.198 1.196 5H6v-3.659z" /></svg><span>مشاريع الطلاب</span></a></li>
            <li class="drawer-item"><a href="#lifecycle" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>مراحل العمل</span></a></li>
            <li class="drawer-item"><a href="#gallery" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>معرض المشاريع</span></a></li>
            <li class="drawer-item"><a href="#calculator" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M9 7h6m0 10v-3m-3 3h.01M9 17h.01M9 14h.01M12 14h.01M15 11h.01M12 11h.01M9 11h.01M7 21h10a2 2 0 002-2V5a2 2 0 00-2-2H7a2 2 0 00-2 2v14a2 2 0 002 2z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>حاسبة التكلفة</span></a></li>
            <li class="drawer-item"><a href="#faq" onclick="toggleDrawer(false)"><svg viewBox="0 0 24 24"><path d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" stroke-linecap="round" stroke-linejoin="round"/></svg><span>الأسئلة الشائعة</span></a></li>
        </ul>
    </nav>

    <div class="top-nav-bar">
        <button class="menu-toggle-btn" onclick="toggleDrawer(true)">
            <svg viewBox="0 0 24 24"><path d="M4 6h16M4 12h16M4 18h16" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </button>
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
        <p>معماري | شغوف بالتخطيط العمراني، الاستدامة، وتطوير البيئة المبنية ومشاريع التخرج الطلابية</p>
    </header>

    <div class="container">
        
        <section class="about-section" id="about">
            <h2>نبذة عني</h2>
            <p>
                معماري لديّ شغف قوي بالتصميم المعماري، التخطيط العمراني، والتنمية المستدامة. أسعى دائماً لابتكار حلول مستدامة ومبتكرة تعزز كفاءة البيئة المبنية وتلبي احتياجات المجتمع. 
                خلال مسيرتي الأكاديمية والعملية، قمت بإعداد وتطوير مشاريع متنوعة تشمل التخطيط البيئي المعماري، وتصميم لاندسكيب متكامل، بالإضافة إلى دعم ومساعدة طلاب كليات الهندسة والعمارة في إنهاء مشاريع فصولهم الدراسية وتخرجهم بأفضل إخراج ممكن.
            </p>
        </section>

        <!-- قسم مساعدة الطلاب والأكاديميين المطور حديثاً -->
        <h2 class="section-title" id="students">مساعدات ومشاريع الطلاب</h2>
        <p class="section-subtitle">مزنوق في الفاينل؟ شايل هم الإخراج والرصة؟ إحنا هنا علشان نشيل عنك الضغط ونطلع مشروعك بأعلى جودة تضمن لك التقدير!</p>
        <section class="students-section">
            <div class="students-grid">
                <div class="student-service-card">
                    <h3>
                        <svg viewBox="0 0 24 24"><path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/></svg>
                        تطوير ومساعدة المشاريع
                    </h3>
                    <p>مساعدتك خطوة بخطوة في بلورة فكرة المشروع (الـ Concept) وتطوير الرسومات التنفيذية والمعمارية وتعديلها بمرونة أكاديمية كاملة تتماشى مع طلبات الدكاترة والمناقشين.</p>
                </div>
                <div class="student-service-card">
                    <h3>
                        <svg viewBox="0 0 24 24"><path d="M21 19V5c0-1.1-.9-2-2-2H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2zM8.5 13.5l2.5 3.01L14.5 12l4.5 6H5l3.5-4.5z"/></svg>
                        الإخراج المعماري المتكامل
                    </h3>
                    <p>توليد وإنتاج كافة الإخراجات واللقطات المعمارية الفاخرة، مناظير داخلية وخارجية ببيئة ضوئية متكاملة لاندسكيب ومواد واقعية تبرز جمال وقوة تصميمك.</p>
                </div>
                <div class="student-service-card">
                    <h3>
                        <svg viewBox="0 0 24 24"><path d="M4 6H2v14c0 1.1.9 2 2 2h14v-2H4V6zm16-4H8c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm0 14H8V4h12v12z"/></svg>
                        تنسيق ورصة البانر النهائي
                    </h3>
                    <p>نقوم بتجميع ورص شاسيهات التسليم النهائي للفاينل وبنرات التخرج (Final Layout/Postering) وفق تكوين بصري (Composition) مريح ومقروء يبرز تسلسل المشروع بشكل علمي واحترافي أمام لجنة التحكيم.</p>
                </div>
            </div>

            <div class="programs-container">
                <div class="program-badge"><span>AutoCAD</span> للرسومات الثنائية والمساقط 2D</div>
                <div class="program-badge"><span>Revit</span> للنمذجة ثلاثية الأبعاد الـ 3D BIM</div>
                <div class="program-badge"><span>D5 Render</span> لإخراج الريندرات والمناظير الفائقة الواقعية</div>
                <div class="program-badge"><span>Photoshop</span> للبوست برودكشن وتنسيق البانر النهائي</div>
            </div>
        </section>

        <h2 class="section-title" id="skills">مهاراتي ومخرجات العمل</h2>
        <section class="skills-grid">
            <div class="skill-card">مساقط أفقية دقيقة (Floor Plans)</div>
            <div class="skill-card">قطاعات رأسية وسكاشن (Sections)</div>
            <div class="skill-card">واجهات معمارية حديثة (Elevations)</div>
            <div class="skill-card">المخطط العام واللاي أوت (Layout)</div>
            <div class="skill-card">التصميم المعماري المستدام</div>
            <div class="skill-card">تنسيق المواقع (Landscape)</div>
        </section>

        <!-- خطة ومراحل سير العمل الهندسية -->
        <h2 class="section-title" id="lifecycle">مراحل سير العمل الهندسي</h2>
        <p class="section-subtitle">خطوات منهجية واضحة ومدروسة نتبعها لتحويل رؤيتك المعمارية إلى واقع ملموس</p>
        <section class="timeline-container">
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 01</span>
                    <h3 class="timeline-title">جمع البيانات والبرنامج المعماري</h3>
                    <p class="timeline-desc">مناقشة متطلباتك، أبعاد قطعة الأرض، الارتدادات القانونية، والأسلوب المعماري المفضل (مودرن، كلاسيك، نيومودرن) لإنشاء وثيقة المشروع المبدئية.</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 02</span>
                    <h3 class="timeline-title">التخطيط المبدئي والمساقط (2D)</h3>
                    <p class="timeline-desc">دراسة التوجيه الشمسي وحركة الرياح لتوزيع الفراغات الداخلية بذكاء واستغلال كل متر مربع، ثم عرض المساقط الأفقية لاعتمادها وعمل التعديلات.</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 03</span>
                    <h3 class="timeline-title">الكتل ثلاثية الأبعاد والواجهات (3D)</h3>
                    <p class="timeline-desc">تجسيد المساقط الصامتة إلى مجسمات حية، وتصميم الواجهات الخارجية وتنسيق المسطحات الخضراء وعناصر الـ Landscape لتشاهد مشروعك قبل بنائه.</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="timeline-content">
                    <span class="timeline-num">المرحلة 04</span>
                    <h3 class="timeline-title">المخططات التنفيذية والتسليم النهائي</h3>
                    <p class="timeline-desc">إعداد وتجهيز لوحات الـ Working والقطاعات والواجهات التنفيذية الشاملة للأبعاد والمواد بدقة عالية لتسليمها لمهندسي المقاولات والبدء في التنفيذ مباشرة.</p>
                </div>
            </div>
        </section>

        <h2 class="section-title" id="gallery">معرض المشاريع المنفذة</h2>
        <p class="section-subtitle">تتكون المنصة من مشروعين رئيسيين، اضغط لتصفح الـ 5 صور الخاصة بكل مشروع بالكامل</p>
        
        <main class="photo-gallery">
            <div class="circle-project" title="مشروع معماري 1" onclick="openGalleryLightbox(1)">
                <img src="https://b.top4top.io/p_3828lnjav1.jpg" alt="مشروع معماري 1">
                <div class="circle-overlay">المشروع الأول<span>elharoun (يحتوي على 5 صور)</span></div>
            </div>
            <div class="circle-project" title="مشروع معماري 2" onclick="openGalleryLightbox(2)">
                <img src="https://h.top4top.io/p_3828kfxcl1.jpg" alt="مشروع معماري 2">
                <div class="circle-overlay">المشروع الثاني<span>elharoun (يحتوي على 5 صور)</span></div>
            </div>
        </main>

        <!-- حاسبة التكلفة -->
        <h2 class="section-title" id="calculator">حاسبة التكلفة المبدئية والباقات الهندسية</h2>
        <p class="section-subtitle">اختر باقة التصميم والمخرجات المطلوبة مع إدخال المساحة للحصول على تقرير دقيق حياً</p>
        <section class="calculator-section">
            <div class="currency-switch-wrapper">
                <button id="btnEGP" class="currency-btn active" onclick="setCurrency('EGP')">ج.م (EGP)</button>
                <button id="btnUSD" class="currency-btn" onclick="setCurrency('USD')">دولار ($)</button>
            </div>
            
            <div class="calc-grid">
                <div class="calc-field calc-full-width">
                    <label>باقة التصميم المعماري والمخرجات المطلوبة</label>
                    <select id="calcPackage" onchange="calculateProjectCost()">
                        <option value="45" data-sheets="4" data-hours="25" data-days="5">باقة التصميم الخارجي المبدئي (مساقط أفقية + كتل خارجية مبدئية)</option>
                        <option value="75" data-sheets="8" data-hours="45" data-days="10">باقة التصميم الخارجي المتكامل (مساقط + قطاعات + واجهات + رندر 3D)</option>
                        <option value="110" data-sheets="12" data-hours="70" data-days="15">باقة التصميم الداخلي الشامل (مساقط توزيع الأثاث + لقطات رندر مجسمة لكل الفراغات)</option>
                        <option value="140" data-sheets="16" data-hours="100" data-days="22">الباقة الذهبية المدمجة (معماري خارجي + لاندسكيب حدائق + مخططات تنفيذية ووركينج)</option>
                        <option value="35" data-sheets="5" data-hours="35" data-days="7">باقة التخطيط العمراني (دراسة شبكات الطرق وتوزيع الأراضي واللاي أوت المبدئي)</option>
                    </select>
                </div>
                
                <div class="calc-field calc-full-width" style="margin-top: 10px;">
                    <label>المساحة الإجمالية للمشروع (متر مربع)</label>
                    <input type="number" id="calcArea" value="150" min="10" oninput="calculateProjectCost()">
                </div>

                <div class="live-stats-panel">
                    <div class="stat-box">
                        <div class="stat-value" id="statSheets">0</div>
                        <div class="stat-label">عدد اللوحات المتوقعة</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value" id="statHours">0 ساعة</div>
                        <div class="stat-label">ساعات العمل المقدرة</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value" id="statDays">0 أيام</div>
                        <div class="stat-label">زمن التسليم المتوقع</div>
                    </div>
                </div>
            </div>
            
            <div class="calc-result-box">
                <div style="font-weight: 600; color: var(--text-secondary);">التكلفة التقديرية المقدرة للباقة بالكامل:</div>
                <div class="calc-price" id="calcPriceDisplay">0 ج.م</div>
                <button class="submit-auth-btn" style="background: rgba(255,255,255,0.05); color: #ffffff; border: 1px solid var(--accent-color); margin-top: 15px;" onclick="sendEstimateToWhatsapp()">مناقشة تفاصيل الباقة والمشروع عبر واتساب</button>
            </div>
        </section>

        <!-- الأسئلة الشائعة الأكورديون -->
        <h2 class="section-title" id="faq">الأسئلة الشائعة (FAQ)</h2>
        <p class="section-subtitle">إجابات سريعة وواضحة على أكثر الأسئلة المعمارية والفنية تداولاً</p>
        <section class="faq-wrapper">
            <div class="faq-item" onclick="toggleFaq(this)">
                <div class="faq-question">
                    <span>هل يمكنني إجراء تعديلات على التصاميم بعد تسليمها؟</span>
                    <svg viewBox="0 0 24 24"><path d="M19 9l-7 7-7-7" stroke-linecap="round" stroke-linejoin="round"/></svg>
                </div>
                <div class="faq-answer">نعم بكل تأكيد، نتيح جولتين من التعديلات المجانية على المساقط الأفقية والكتل المبدئية لضمان تلبية التصاميم بالكامل لتطلعاتك قبل إخراج اللوحات النهائية والتنفيذية.</div>
            </div>
            <div class="faq-item" onclick="toggleFaq(this)">
                <div class="faq-question">
                    <span>ما هي الصيغ والملفات التي يتم تسليمها للعميل؟</span>
                    <svg viewBox="0 0 24 24"><path d="M19 9l-7 7-7-7" stroke-linecap="round" stroke-linejoin="round"/></svg>
                </div>
                <div class="faq-answer">يتم تسليم لوحات ومخططات العمل بصيغة PDF عالية الجودة وصور رندر فائقة الدقة للواجهات والكتل، بالإضافة للملفات المصدرية للأوتوكاد (DWG) عند طلب المخططات التنفيذية.</div>
            </div>
            <div class="faq-item" onclick="toggleFaq(this)">
                <div class="faq-question">
                    <span>هل التصاميم واللوحات تكون متوافقة مع شروط البناء المعتمدة؟</span>
                    <svg viewBox="0 0 24 24"><path d="M19 9l-7 7-7-7" stroke-linecap="round" stroke-linejoin="round"/></svg>
                </div>
                <div class="faq-answer">نعم، جميع التصاميم المعمارية يتم إعدادها بدقة بالغة بالاعتماد على كود البناء وشروط الارتدادات والمساحات المعتمدة محلياً لضمان سهولة ترخيصها وتنفيذها دون أي معوقات قانونية.</div>
            </div>
        </section>

        <div class="payment-status-container">
            <div class="payment-card" onclick="openPaymentModal()">
                <div class="wallet-icon-glow">
                    <svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z" /></svg>
                </div>
                <h4 class="payment-text-main">بوابة الدفع الإلكتروني</h4>
            </div>
        </div>

        <section class="contact-section" id="contact">
            <div class="contact-container">
                <h2 class="contact-title">هل لديك مشروع ترغب في تطويره؟</h2>
                <p class="contact-desc">يسعدني دائماً تواصلك لمناقشة الأفكار المعمارية وتحويلها إلى واقع مستدام.</p>
                <a href="https://wa.me/201050758773" class="whatsapp-link" target="_blank" id="mainWhatsappBtn">تواصل عبر واتساب</a>
            </div>
        </section>

    </div>

    <!-- فودافون كاش -->
    <div id="paymentModal" class="modal">
        <div class="modal-content">
            <div style="font-size: 1.3rem; font-weight: 700; margin-bottom: 10px;">تفاصيل الدفع عبر فودافون كاش</div>
            <p style="color: var(--text-secondary);">يمكنك تحويل الرسوم المتفق عليها إلى الرقم التالي:</p>
            <div style="font-size: 1.8rem; font-weight: 700; color: var(--vodafone-color); margin: 15px 0; letter-spacing: 2px;">01050758773</div>
            <button class="close-btn" onclick="closePaymentModal()">إغلاق</button>
        </div>
    </div>

    <!-- سلايدر استعراض المشاريع -->
    <div id="galleryLightbox" class="modal">
        <div class="lightbox-content">
            <button class="lightbox-close" onclick="closeGalleryLightbox()">✕</button>
            <div class="lightbox-image-container">
                <button class="nav-arrow prev-arrow" onclick="changeLightboxImage(1)">❯</button>
                <img id="lightboxImg" src="">
                <button class="nav-arrow next-arrow" onclick="changeLightboxImage(-1)">❮</button>
            </div>
            <div class="lightbox-counter" id="lightboxCounter">1 / 5</div>
        </div>
    </div>

    <footer>
        <p>جميع الحقوق محفوظة © المهندس محمد الحارون 2026</p>
    </footer>

    <script>
        // تتبع حركة الماوس المعماري
        const cursor = document.getElementById('customCursor');
        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
        });

        // نظام التخزين المتراكم للتعليقات الحقيقية (LocalStorage) بدون تعليقات افتراضية
        let commentsArray = JSON.parse(localStorage.getItem('haroun_comments')) || [];

        function toggleCommentsDrawer(open) {
            const drawer = document.getElementById('commentsDrawer');
            const overlay = document.getElementById('commentsOverlay');
            if (open) { drawer.classList.add('open'); overlay.classList.add('show'); renderComments(); }
            else { drawer.classList.remove('open'); overlay.classList.remove('show'); }
        }

        function renderComments() {
            const box = document.getElementById('commentsListBox');
            box.innerHTML = '';
            document.getElementById('commentCount').innerText = commentsArray.length;

            if (commentsArray.length === 0) {
                box.innerHTML = '<div class="empty-comments-notice">لا توجد تعليقات بعد. كن أول من يترك تعليقه المعماري أو رأيه هنا!</div>';
                return;
            }

            commentsArray.forEach(item => {
                const card = document.createElement('div');
                card.className = 'single-comment-card';
                card.innerHTML = `
                    <div class="comment-user-meta">
                        <span class="comment-username">${item.name}</span>
                        <span class="comment-date">${item.date}</span>
                    </div>
                    <p class="comment-text-content">${item.text}</p>
                `;
                box.appendChild(card);
            });
            box.scrollTop = box.scrollHeight; // التمرير التلقائي لآخر تعليق مضاف بالأسفل
        }

        function addNewComment() {
            const nameInput = document.getElementById('commenterName');
            const textInput = document.getElementById('commenterText');

            if (!nameInput.value.trim() || !textInput.value.trim()) {
                alert('فضلاً، املأ حقل الاسم والتعليق أولاً!');
                return;
            }

            const today = new Date().toISOString().split('T')[0];
            const newComment = {
                name: nameInput.value.trim(),
                text: textInput.value.trim(),
                date: today
            };

            commentsArray.push(newComment);
            localStorage.setItem('haroun_comments', JSON.stringify(commentsArray)); // تخزين دائم ومتراكم

            nameInput.value = '';
            textInput.value = '';
            renderComments();
        }

        // نظام حساب التكلفة والباقات
        let currentCurrency = 'EGP';
        const exchangeRate = 0.021; 

        function setCurrency(currency) {
            currentCurrency = currency;
            document.getElementById('btnEGP').classList.toggle('active', currency === 'EGP');
            document.getElementById('btnUSD').classList.toggle('active', currency === 'USD');
            calculateProjectCost();
        }

        function calculateProjectCost() {
            const selectElement = document.getElementById('calcPackage');
            const selectedOption = selectElement.options[selectElement.selectedIndex];
            
            const costPerMeter = parseFloat(selectedOption.value);
            const area = parseFloat(document.getElementById('calcArea').value) || 0;
            
            let finalCostEGP = Math.round(costPerMeter * area);

            const baseSheets = parseInt(selectedOption.getAttribute('data-sheets'));
            const baseHours = parseInt(selectedOption.getAttribute('data-hours'));
            const baseDays = parseInt(selectedOption.getAttribute('data-days'));

            const scaleFactor = Math.max(0.6, area / 150); 
            const calculatedSheets = Math.max(3, Math.round(baseSheets * Math.sqrt(scaleFactor)));
            const calculatedHours = Math.max(10, Math.round(baseHours * scaleFactor));
            const calculatedDays = Math.max(2, Math.round(baseDays * Math.sqrt(scaleFactor)));

            document.getElementById('statSheets').innerText = `${calculatedSheets} لوحات`;
            document.getElementById('statHours').innerText = `${calculatedHours} ساعة`;
            document.getElementById('statDays').innerText = `${calculatedDays} يوم`;
            
            if (currentCurrency === 'EGP') {
                document.getElementById('calcPriceDisplay').innerText = finalCostEGP.toLocaleString('ar-EG') + " ج.م";
            } else {
                let finalCostUSD = Math.round(finalCostEGP * exchangeRate);
                document.getElementById('calcPriceDisplay').innerText = finalCostUSD.toLocaleString('en-US') + " $";
            }
        }

        function sendEstimateToWhatsapp() {
            const packageText = document.getElementById('calcPackage').options[document.getElementById('calcPackage').selectedIndex].text;
            const area = document.getElementById('calcArea').value;
            const price = document.getElementById('calcPriceDisplay').innerText;
            const sheets = document.getElementById('statSheets').innerText;
            const days = document.getElementById('statDays').innerText;
            
            const message = encodeURIComponent(`مرحباً مهندس محمد، أود الاستفسار وبدء العمل على مشروع بالبيانات الآتية:\n- الباقة المختارة: ${packageText}\n- المساحة الإجمالية: ${area} متر مربع\n- التقدير الإحصائي: [ ${sheets} | خلال ${days} ]\n- التكلفة الإجمالية: ${price}\nبرجاء مراجعة البيانات للبدء.`);
            window.open(`https://wa.me/201050758773?text=${message}`, '_blank');
        }

        function toggleFaq(element) {
            const isActive = element.classList.contains('active');
            document.querySelectorAll('.faq-item').forEach(item => item.classList.remove('active'));
            if (!isActive) { element.classList.add('active'); }
        }

        document.addEventListener("DOMContentLoaded", () => {
            calculateProjectCost();
            document.getElementById('commentCount').innerText = commentsArray.length;
        });

        function toggleDrawer(open) {
            const drawer = document.getElementById('sideDrawer');
            const overlay = document.getElementById('drawerOverlay');
            if (open) { drawer.classList.add('open'); overlay.classList.add('show'); }
            else { drawer.classList.remove('open'); overlay.classList.remove('show'); }
        }

        // سلايدر صور المشاريع
        const projectGalleries = {
            1: ["https://b.top4top.io/p_3828lnjav1.jpg", "https://k.top4top.io/p_3828jbw581.jpg", "https://d.top4top.io/p_38285y97w1.jpg", "https://g.top4top.io/p_38288wnor1.jpg", "https://g.top4top.io/p_3828f4bqz1.jpg"],
            2: ["https://h.top4top.io/p_3828kfxcl1.jpg", "https://k.top4top.io/p_3828clele1.jpg", "https://c.top4top.io/p_3828gvugl1.jpg", "https://k.top4top.io/p_3828qrim11.jpg", "https://b.top4top.io/p_3828lgvbq1.jpg"]
        };
        let activeProjectId = 1, activeImageIndex = 0;

        function openGalleryLightbox(projectId) { activeProjectId = projectId; activeImageIndex = 0; updateLightboxUI(); document.getElementById('galleryLightbox').style.display = 'flex'; }
        function closeGalleryLightbox() { document.getElementById('galleryLightbox').style.display = 'none'; }
        function changeLightboxImage(direction) { const imagesList = projectGalleries[activeProjectId]; activeImageIndex += direction; if (activeImageIndex >= imagesList.length) activeImageIndex = 0; else if (activeImageIndex < 0) activeImageIndex = imagesList.length - 1; updateLightboxUI(); }
        function updateLightboxUI() { const imagesList = projectGalleries[activeProjectId]; document.getElementById('lightboxImg').src = imagesList[activeImageIndex]; document.getElementById('lightboxCounter').innerText = `${activeImageIndex + 1} / ${imagesList.length}`; }

        function openPaymentModal() { document.getElementById('paymentModal').style.display = 'flex'; }
        function closePaymentModal() { document.getElementById('paymentModal').style.display = 'none'; }
    </script>
</body>
</html>
