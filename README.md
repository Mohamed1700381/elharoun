<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معماري | المشاريع المعمارية</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800&family=Tajawal:wght@400;500;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --main-color: #0f172a;
            --accent-color: #059669;
            --accent-hover: #047857;
            --accent-glow: rgba(5, 150, 105, 0.4);
            --bg-color: #f8fafc;
            --text-color: #334155;
            --card-bg: rgba(255, 255, 255, 0.85);
            --vodafone-color: #e60000;
            --gold: #d4a574;
            --glass-border: rgba(255, 255, 255, 0.2);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Cairo', 'Tajawal', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* ===== خلفية 3D معمارية ===== */
        #canvas-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(135deg, #0f172a 0%, #1a2a3a 50%, #0d1b2a 100%);
        }

        /* ===== الهيدر ===== */
        header {
            position: relative;
            color: white;
            padding: 100px 20px 80px;
            text-align: center;
            overflow: hidden;
            background: transparent;
        }
        header::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: radial-gradient(ellipse at center, rgba(5,150,105,0.15) 0%, transparent 70%);
            pointer-events: none;
        }
        header::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-color), var(--gold), var(--vodafone-color));
            animation: gradientShift 5s ease infinite;
            background-size: 200% 200%;
        }
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        header h1 {
            margin: 0;
            font-size: 3.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, #fff 0%, var(--gold) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: none;
            letter-spacing: 1px;
        }
        header p {
            margin: 20px 0 0 0;
            font-size: 1.3rem;
            color: #94a3b8;
            font-weight: 300;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        /* ===== حاوية المحتوى ===== */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 50px 20px;
            position: relative;
            z-index: 1;
        }

        /* ===== قسم السيرة الذاتية - Glassmorphism ===== */
        .about-section {
            background: var(--card-bg);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            padding: 45px;
            border-radius: 24px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.1), 0 0 0 1px var(--glass-border);
            margin-bottom: 60px;
            border-right: 4px solid var(--accent-color);
            position: relative;
            overflow: hidden;
        }
        .about-section::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(5,150,105,0.05) 0%, transparent 60%);
            pointer-events: none;
        }
        .about-section h2 {
            color: var(--main-color);
            margin-top: 0;
            font-size: 2rem;
            margin-bottom: 20px;
            font-weight: 700;
            position: relative;
        }
        .about-section h2::after {
            content: '';
            display: block;
            width: 60px;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-color), var(--gold));
            border-radius: 2px;
            margin-top: 12px;
        }
        .about-section p {
            font-size: 1.1rem;
            color: #475569;
            line-height: 2;
        }

        /* ===== قسم المهارات ===== */
        .section-title {
            text-align: center;
            margin-top: 60px;
            margin-bottom: 50px;
            font-size: 2.2rem;
            color: white;
            position: relative;
            font-weight: 800;
            text-shadow: 0 2px 20px rgba(0,0,0,0.3);
        }
        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-color), var(--gold));
            border-radius: 2px;
            margin: 15px auto 0;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
            margin-bottom: 70px;
        }
        .skill-card {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            color: var(--main-color);
            padding: 30px 20px;
            border-radius: 16px;
            text-align: center;
            font-weight: 700;
            font-size: 1.1rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08), 0 0 0 1px rgba(255,255,255,0.3);
            border: 1px solid rgba(255,255,255,0.4);
            position: relative;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-color), var(--gold));
            transform: scaleX(0);
            transition: transform 0.4s ease;
        }
        .skill-card:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 20px 40px rgba(5, 150, 105, 0.15), 0 0 30px var(--accent-glow);
            border-color: var(--accent-color);
        }
        .skill-card:hover::before {
            transform: scaleX(1);
        }
        .skill-card.ai {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: #34d399;
            border: 1px solid rgba(52, 211, 153, 0.3);
        }
        .skill-card.ai:hover {
            box-shadow: 0 20px 40px rgba(52, 211, 153, 0.2);
        }

        /* ===== شبكة المشاريع ===== */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 35px;
        }
        .card {
            background: var(--card-bg);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0,0,0,0.08), 0 0 0 1px var(--glass-border);
            border: 1px solid rgba(255,255,255,0.3);
            display: flex;
            flex-direction: column;
            position: relative;
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .card::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            border-radius: 20px;
            box-shadow: 0 0 0 0 rgba(5, 150, 105, 0);
            transition: box-shadow 0.4s ease;
            pointer-events: none;
        }
        .card:hover {
            transform: translateY(-12px) rotateX(2deg);
            box-shadow: 0 30px 60px rgba(0,0,0,0.12);
        }
        .card:hover::after {
            box-shadow: 0 0 30px 5px var(--accent-glow);
        }

        .card img {
            width: 100%;
            height: 240px;
            object-fit: cover;
            background: linear-gradient(135deg, #1e293b 0%, #334155 100%);
            border-bottom: 1px solid rgba(255,255,255,0.1);
            transition: transform 0.5s ease;
        }
        .card:hover img {
            transform: scale(1.05);
        }

        .card-content {
            padding: 30px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
            position: relative;
            z-index: 1;
        }
        .tag {
            align-self: flex-start;
            background: linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%);
            color: var(--accent-color);
            padding: 6px 16px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 700;
            margin-bottom: 15px;
            box-shadow: 0 2px 10px rgba(5,150,105,0.15);
        }
        .card-title {
            font-size: 1.5rem;
            margin: 0 0 15px 0;
            color: var(--main-color);
            font-weight: 800;
        }
        .card-desc {
            font-size: 1rem;
            color: #64748b;
            margin-bottom: 25px;
            flex-grow: 1;
            line-height: 1.8;
        }
        .action-area {
            margin-top: auto;
        }
        .price {
            font-weight: 800;
            color: #d97706;
            font-size: 1.4rem;
            margin-bottom: 18px;
            display: flex;
            align-items: center;
            gap: 8px;
            text-shadow: 0 1px 2px rgba(0,0,0,0.05);
        }

        /* ===== أزرار ===== */
        .btn {
            display: block;
            padding: 16px 24px;
            text-decoration: none;
            border-radius: 12px;
            text-align: center;
            font-weight: 700;
            font-size: 1.05rem;
            cursor: pointer;
            border: none;
            width: 100%;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }
        .btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.6s ease, height 0.6s ease;
        }
        .btn:hover::before {
            width: 300px;
            height: 300px;
        }
        .btn-primary {
            background: linear-gradient(135deg, var(--main-color) 0%, #1e293b 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(15, 23, 42, 0.3);
        }
        .btn-primary:hover {
            background: linear-gradient(135deg, var(--accent-color) 0%, var(--accent-hover) 100%);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(5, 150, 105, 0.4);
        }
        .btn-cash {
            background: linear-gradient(135deg, var(--vodafone-color) 0%, #b30000 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(230, 0, 0, 0.3);
        }
        .btn-cash:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(230, 0, 0, 0.4);
        }

        /* ===== كارت الخدمات المستقل ===== */
        .service-card {
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            color: white;
            border: 1px solid rgba(52, 211, 153, 0.2);
            text-align: center;
            justify-content: center;
            align-items: center;
            padding: 50px 35px;
            position: relative;
            overflow: hidden;
        }
        .service-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(52,211,153,0.08) 0%, transparent 60%);
            pointer-events: none;
        }
        .service-card .circle-icon-large {
            width: 80px;
            height: 80px;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 25px;
            border: 2px solid #34d399;
            box-shadow: 0 0 30px rgba(52, 211, 153, 0.2);
            animation: pulseGlow 2s ease-in-out infinite;
        }
        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(52, 211, 153, 0.2); }
            50% { box-shadow: 0 0 40px rgba(52, 211, 153, 0.4); }
        }
        .service-card .circle-icon-large svg {
            width: 40px;
            height: 40px;
            fill: none;
            stroke: #34d399;
            stroke-width: 2;
        }
        .service-card .card-title {
            color: white;
            font-size: 1.8rem;
            font-weight: 800;
        }
        .service-card .card-desc {
            color: #94a3b8;
            font-size: 1.05rem;
        }
        .btn-whatsapp-service {
            background: linear-gradient(135deg, #25d366 0%, #128C7E 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(37, 211, 102, 0.3);
        }
        .btn-whatsapp-service:hover {
            transform: scale(1.03) translateY(-2px);
            box-shadow: 0 8px 25px rgba(37, 211, 102, 0.4);
        }

        /* ===== قسم تواصل معنا ===== */
        .contact-section {
            background: linear-gradient(135deg, rgba(15,23,42,0.95) 0%, rgba(30,41,59,0.95) 100%);
            backdrop-filter: blur(20px);
            color: white;
            padding: 80px 20px;
            text-align: center;
            margin-top: 80px;
            border-top: 4px solid var(--accent-color);
            position: relative;
            overflow: hidden;
        }
        .contact-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 20% 50%, rgba(5,150,105,0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 50%, rgba(212,165,116,0.1) 0%, transparent 50%);
            pointer-events: none;
        }
        .contact-container {
            max-width: 600px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }
        .contact-title {
            font-size: 2.2rem;
            font-weight: 800;
            margin-bottom: 20px;
            background: linear-gradient(135deg, #fff 0%, var(--gold) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
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
            background: linear-gradient(135deg, #25d366 0%, #128C7E 100%);
            color: white;
            padding: 18px 45px;
            font-size: 1.3rem;
            font-weight: 800;
            text-decoration: none;
            border-radius: 50px;
            box-shadow: 0 15px 35px rgba(37, 211, 102, 0.3);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }
        .whatsapp-link:hover {
            transform: scale(1.08) translateY(-3px);
            box-shadow: 0 20px 50px rgba(37, 211, 102, 0.4);
        }
        .whatsapp-link::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.2) 0%, transparent 60%);
            pointer-events: none;
        }

        footer {
            text-align: center;
            padding: 35px;
            background: rgba(11, 17, 30, 0.95);
            color: #64748b;
            font-size: 0.95rem;
            border-top: 1px solid rgba(30, 41, 59, 0.8);
            backdrop-filter: blur(10px);
        }

        /* ===== النافذة المنبثقة ===== */
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
            background: linear-gradient(135deg, #ffffff 0%, #f8fafc 100%);
            padding: 45px;
            border-radius: 24px;
            width: 90%;
            max-width: 480px;
            text-align: center;
            box-shadow: 0 25px 60px -12px rgba(0, 0, 0, 0.3);
            animation: modalSlide 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid rgba(255,255,255,0.5);
            position: relative;
        }
        .modal-content::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(90deg, var(--vodafone-color), var(--gold));
            border-radius: 24px 24px 0 0;
        }
        @keyframes modalSlide {
            from { transform: translateY(-50px) scale(0.9); opacity: 0; }
            to { transform: translateY(0) scale(1); opacity: 1; }
        }
        .modal-header {
            color: var(--vodafone-color);
            font-size: 1.6rem;
            font-weight: 800;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }
        .modal-header .circle-icon-modal {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #fee2e2 0%, #fecaca 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 15px rgba(230,0,0,0.15);
        }
        .modal-header .circle-icon-modal svg {
            width: 24px;
            height: 24px;
            stroke: var(--vodafone-color);
            fill: none;
            stroke-width: 2.5;
        }
        .wallet-number {
            background: linear-gradient(135deg, #f1f5f9 0%, #e2e8f0 100%);
            padding: 16px;
            border-radius: 12px;
            font-size: 1.6rem;
            font-weight: 800;
            color: var(--main-color);
            letter-spacing: 3px;
            margin: 25px 0;
            border: 2px dashed #cbd5e1;
            user-select: all;
            font-family: 'Courier New', monospace;
            box-shadow: inset 0 2px 10px rgba(0,0,0,0.05);
        }
        .modal-steps {
            text-align: right;
            padding-right: 25px;
            margin-bottom: 30px;
            font-size: 1rem;
            color: #475569;
            
