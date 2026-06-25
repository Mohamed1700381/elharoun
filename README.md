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
