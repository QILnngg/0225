<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>云瀚俱乐部 | 陪玩·电竞·社交</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0a0a;
            font-family: 'Segoe UI', 'Poppins', system-ui, -apple-system, BlinkMacSystemFont, 'Roboto', sans-serif;
            color: #e0e0e0;
            line-height: 1.5;
        }

        /* 黑金主色调 */
        :root {
            --gold: #f5b042;
            --gold-dark: #c97e0a;
            --black-bg: #0f0f0f;
            --card-bg: #1a1a1a;
            --border-gold: rgba(245, 176, 66, 0.3);
            --shadow-gold: 0 10px 25px -5px rgba(245, 176, 66, 0.1);
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 24px;
        }

        /* 导航栏 */
        .navbar {
            background: #080808;
            border-bottom: 1px solid var(--border-gold);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            backdrop-filter: blur(10px);
        }

        .nav-wrapper {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, #f5b042, #ffd966);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 1px;
        }
        .logo span {
            color: var(--gold);
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links li {
            cursor: pointer;
            font-weight: 500;
            transition: 0.2s;
            padding: 0.5rem 0;
            border-bottom: 2px solid transparent;
        }

        .nav-links li.active, .nav-links li:hover {
            color: var(--gold);
            border-bottom-color: var(--gold);
        }

        /* 汉堡菜单 */
        .hamburger {
            display: none;
            font-size: 1.8rem;
            cursor: pointer;
            color: var(--gold);
        }

        /* 页面容器 */
        .page {
            display: none;
            padding: 2rem 0 4rem;
            animation: fade 0.3s ease;
        }
        .active-page {
            display: block;
        }

        @keyframes fade {
            from { opacity: 0; transform: translateY(8px);}
            to { opacity: 1; transform: translateY(0);}
        }

        /* 卡片样式 */
        .card {
            background: var(--card-bg);
            border-radius: 1rem;
            padding: 1.5rem;
            box-shadow: 0 4px 14px rgba(0,0,0,0.4);
            border: 1px solid var(--border-gold);
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-gold);
        }

        /* 按钮 */
        .btn-gold {
            background: var(--gold);
            color: #0a0a0a;
            border: none;
            padding: 0.6rem 1.2rem;
            border-radius: 2rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
        }
        .btn-gold:hover {
            background: var(--gold-dark);
            transform: scale(1.02);
        }
        .btn-outline {
            background: transparent;
            border: 1px solid var(--gold);
            color: var(--gold);
            padding: 0.4rem 1rem;
            border-radius: 2rem;
            cursor: pointer;
        }
        .btn-sm {
            padding: 0.3rem 0.8rem;
            font-size: 0.8rem;
        }

        /* 表单 */
        input, textarea, select {
            width: 100%;
            padding: 0.75rem;
            background: #2a2a2a;
            border: 1px solid #444;
            border-radius: 0.75rem;
            color: white;
            margin-top: 0.25rem;
        }
        label {
            font-weight: 500;
            color: var(--gold);
        }

        /* 陪陪卡片网格 */
        .peipei-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        /* 留言墙木质底板 */
        .wood-board {
            background: #8b5a2b;
            background-image: repeating-linear-gradient(45deg, #a06e36 0px, #a06e36 2px, #7c4e21 2px, #7c4e21 8px);
            border-radius: 2rem;
            padding: 2rem;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.5), 0 8px 20px rgba(0,0,0,0.3);
        }
        .message-card {
            background: white;
            color: #1e1e1e;
            border-radius: 1rem;
            padding: 1rem;
            margin-bottom: 1rem;
            box-shadow: 0 2px 6px rgba(0,0,0,0.2);
            position: relative;
        }
        .message-name {
            font-weight: bold;
            color: #c97e0a;
        }
        .message-time {
            font-size: 0.7rem;
            color: #777;
        }
        .delete-msg {
            position: absolute;
            top: 8px;
            right: 12px;
            background: #b91c1c;
            color: white;
            border: none;
            border-radius: 30px;
            width: 24px;
            height: 24px;
            cursor: pointer;
            font-size: 12px;
        }

        /* 管理编辑小图标 */
        .edit-icon {
            background: rgba(245,176,66,0.2);
            border-radius: 30px;
            padding: 0 8px;
            font-size: 0.75rem;
            cursor: pointer;
            margin-left: 8px;
            display: inline-block;
            color: var(--gold);
        }
        .admin-tag {
            background: var(--gold);
            color: black;
            font-size: 0.7rem;
            padding: 2px 8px;
            border-radius: 30px;
            margin-left: 8px;
        }

        /* 响应式 */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                flex-direction: column;
                width: 100%;
                background: #0a0a0a;
                padding: 1rem 0;
                gap: 1rem;
            }
            .nav-links.show {
                display: flex;
            }
            .hamburger {
                display: block;
            }
            .container {
                padding: 0 16px;
            }
        }

        footer {
            text-align: center;
            padding: 2rem;
            border-top: 1px solid var(--border-gold);
            margin-top: 2rem;
            color: #aaa;
        }
        .flex-between {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .mt-4 { margin-top: 1rem; }
        .mt-2 { margin-top: 0.5rem; }
        .mb-2 { margin-bottom: 0.5rem; }
        .text-gold { color: var(--gold); }
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px,1fr));
            gap: 1.5rem;
        }
        .order-item, .vip-card {
            background: #222;
            border-radius: 1rem;
            padding: 1rem;
            margin-bottom: 0.8rem;
        }
        .modal {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }
        .modal-content {
            background: #1e1e1e;
            max-width: 500px;
            width: 90%;
            border-radius: 2rem;
            padding: 1.5rem;
            border: 1px solid var(--gold);
        }
        img {
            max-width: 100%;
            border-radius: 0.75rem;
        }
    </style>
    <!-- 字体图标库 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>

<div class="navbar">
    <div class="container nav-wrapper">
        <div class="logo">☁️ 云瀚俱乐部 <span>| 尊享陪玩</span></div>
        <div class="hamburger" id="hamburgerBtn">☰</div>
        <ul class="nav-links" id="navLinks">
            <li data-page="home">俱乐部首页</li>
            <li data-page="peipei">陪陪列表</li>
            <li data-page="orderForm">设计订单</li>
            <li data-page="messageWall">留言墙</li>
            <li data-page="profile">个人主页</li>
        </ul>
    </div>
</div>

<main class="container">
    <!-- 首页 -->
    <div id="homePage" class="page active-page">
        <div class="card" style="margin-bottom: 2rem;">
            <div class="flex-between">
                <h2 class="text-gold"><i class="fas fa-crown"></i> 关于云瀚</h2>
                <span class="edit-icon" id="editIntroBtn"><i class="fas fa-edit"></i> 编辑介绍</span>
            </div>
            <p id="clubIntro" class="mt-4">云瀚俱乐部成立于2025年，专注高端电竞陪玩、语音陪伴、娱乐互动与解决客户各种需求。拥有高品质服务，让每一次娱乐体验都值得回味。如果说相遇即是缘分的话，我希望你的选择是我。</p >
        </div>

        <div class="grid-2">
            <div class="card">
                <div class="flex-between"><h3><i class="fas fa-coins"></i> 价格表</h3><span class="edit-icon" id="editPriceImgBtn"><i class="fas fa-image"></i> 换图</span></div>
                <div id="priceImageArea" style="background:#2a2a2a; border-radius: 1rem; padding: 1rem; text-align: center; margin-top: 0.5rem;">
                    < img id="priceTableImg" src="https://picsum.photos/id/20/400/200" style="width:100%; border-radius: 12px;" alt="价格表占位">
                    <p class="text-gold mt-2">* 可替换图片链接</p >
                </div>
            </div>
            <div class="card">
                <div class="flex-between"><h3><i
