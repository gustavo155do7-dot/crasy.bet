<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crasy Win - Bolão Virtual</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #fafafa;
            color: #1a1a1a;
        }

        /* HEADER */
        .header {
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 15px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 10px;
        }

        .logo {
            font-size: 26px;
            font-weight: bold;
            color: #FF69B4;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* NOVO: Logo personalizada do site */
        .site-logo-img {
            width: 40px;
            height: 40px;
            object-fit: contain;
            border-radius: 8px;
        }

        .site-logo-placeholder {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #FF69B4, #FF1493);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 20px;
        }

        .site-logo-text {
            font-size: 26px;
            font-weight: bold;
            color: #FF69B4;
        }

        .nav-links {
            display: flex;
            gap: 10px;
            align-items: center;
            flex-wrap: wrap;
        }

        .nav-links a {
            text-decoration: none;
            color: #1a1a1a;
            font-weight: 500;
            padding: 8px 12px;
            border-radius: 8px;
            cursor: pointer;
        }

        .nav-links a:hover {
            color: #FF69B4;
            background: #FFF0F5;
        }

        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            font-weight: 600;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.3s;
        }

        .btn-pink {
            background: #FF69B4;
            color: white;
        }

        .btn-pink:hover {
            background: #FF1493;
            transform: translateY(-2px);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid #FF69B4;
            color: #FF69B4;
        }

        .btn-outline:hover {
            background: #FFF0F5;
        }

        /* BANNER */
        .banner {
            max-width: 1200px;
            margin: 20px auto;
            background: linear-gradient(135deg, #FF69B4, #FF1493);
            border-radius: 12px;
            padding: 60px 20px;
            text-align: center;
            color: white;
            box-shadow: 0 4px 15px rgba(255,105,180,0.3);
        }

        .banner h1 {
            font-size: 36px;
            margin-bottom: 10px;
        }

        .banner p {
            font-size: 18px;
            opacity: 0.9;
        }

        /* CONTAINER */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .section-title {
            font-size: 22px;
            margin: 30px 0 20px;
        }

        /* MATCHES GRID */
        .matches-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .match-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s;
            position: relative;
        }

        .match-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }

        .match-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
        }

        .badge {
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 12px;
            font-weight: 600;
        }

        .badge-champ {
            background: #FFF0F5;
            color: #FF69B4;
        }

        .badge-live {
            background: #ff4444;
            color: white;
            animation: pulse 2s infinite;
        }

        .badge-done {
            background: #4CAF50;
            color: white;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.6; }
        }

        .match-teams {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 20px 0;
        }

        .team {
            text-align: center;
            flex: 1;
        }

        .team-logo {
            width: 60px;
            height: 60px;
            object-fit: contain;
            margin-bottom: 8px;
            border-radius: 8px;
            background: #f5f5f5;
            padding: 5px;
        }

        .team-logo-placeholder {
            width: 60px;
            height: 60px;
            margin: 0 auto 8px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 14px;
            text-transform: uppercase;
        }

        .team-name {
            font-weight: 600;
            font-size: 14px;
        }

        .match-vs {
            font-size: 24px;
            font-weight: bold;
            color: #ccc;
        }

        .match-score {
            font-size: 28px;
            font-weight: bold;
            color: #FF69B4;
        }

        .match-info {
            text-align: center;
            color: #666;
            font-size: 13px;
            margin: 10px 0;
        }

        .match-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid #f0f0f0;
        }

        .prize {
            font-weight: 600;
            color: #FF69B4;
        }

        .btn-bet {
            background: linear-gradient(135deg, #FF69B4, #FF1493);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 25px;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            margin-top: 12px;
            font-size: 15px;
            transition: all 0.3s;
        }

        .btn-bet:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255,105,180,0.4);
        }

        .btn-bet:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
        }

        .already-bet {
            background: #FFF0F5;
            color: #FF69B4;
            padding: 12px;
            border-radius: 25px;
            text-align: center;
            font-weight: 600;
            margin-top: 12px;
            font-size: 14px;
        }

        /* BET MODAL */
        .bet-form {
            background: #FFF0F5;
            padding: 15px;
            border-radius: 12px;
            margin-top: 12px;
        }

        .score-inputs {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-bottom: 15px;
        }

        .score-input-group {
            text-align: center;
        }

        .score-input-group label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            margin-bottom: 5px;
            color: #666;
        }

        .score-input-group input {
            width: 70px;
            padding: 10px;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            border: 2px solid #FFB6D5;
            border-radius: 10px;
            color: #FF69B4;
        }

        .score-input-group input:focus {
            outline: none;
            border-color: #FF69B4;
            box-shadow: 0 0 0 3px rgba(255,105,180,0.2);
        }

        .bet-amount-group {
            text-align: center;
            margin: 15px 0;
        }

        .bet-amount-group label {
            display: block;
            font-size: 13px;
            font-weight: 600;
            margin-bottom: 8px;
            color: #666;
        }

        .bet-controls {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }

        .bet-btn-ctrl {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 2px solid #FF69B4;
            background: white;
            color: #FF69B4;
            font-size: 20px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .bet-btn-ctrl:hover {
            background: #FF69B4;
            color: white;
        }

        .bet-value {
            font-size: 24px;
            font-weight: bold;
            color: #FF69B4;
            min-width: 70px;
            text-align: center;
        }

        .btn-confirm-bet {
            background: #FF69B4;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            font-size: 15px;
            transition: all 0.3s;
        }

        .btn-confirm-bet:hover {
            background: #FF1493;
            transform: translateY(-2px);
        }

        /* RANKING */
        .ranking-list {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        .ranking-item {
            display: flex;
            align-items: center;
            padding: 15px 20px;
            border-bottom: 1px solid #f0f0f0;
            gap: 12px;
        }

        .ranking-item:hover {
            background: #FFF0F5;
        }

        .rank-num {
            font-size: 22px;
            font-weight: bold;
            min-width: 40px;
            text-align: center;
        }

        .gold { color: #FFD700; }
        .silver { color: #C0C0C0; }
        .bronze { color: #CD7F32; }

        .user-avatar-img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #FF69B4;
        }

        .user-avatar-placeholder {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, #FF69B4, #FF1493);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 18px;
        }

        .user-info {
            flex: 1;
        }

        .user-name {
            font-weight: 600;
        }

        .user-stats {
            font-size: 12px;
            color: #666;
        }

        .user-coins {
            font-weight: 700;
            color: #FF69B4;
        }

        /* MODAL */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: 12px;
            padding: 30px;
            max-width: 450px;
            width: 90%;
            animation: slideUp 0.3s;
            max-height: 90vh;
            overflow-y: auto;
        }

        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .modal-title {
            font-size: 24px;
            color: #FF69B4;
            text-align: center;
            margin-bottom: 20px;
            font-weight: bold;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            font-size: 14px;
        }

        .form-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 14px;
        }

        .form-group input:focus {
            outline: none;
            border-color: #FF69B4;
        }

        .btn-full {
            width: 100%;
            margin-top: 10px;
        }

        .text-center {
            text-align: center;
        }

        .mt-15 {
            margin-top: 15px;
        }

        .link {
            color: #FF69B4;
            cursor: pointer;
            font-weight: 500;
        }

        /* TOAST */
        #toastContainer {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 3000;
        }

        .toast {
            background: white;
            padding: 15px 20px;
            border-radius: 12px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
            margin-top: 10px;
            animation: slideIn 0.3s;
            border-left: 4px solid #FF69B4;
            font-weight: 500;
            min-width: 250px;
        }

        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .toast-success { border-left-color: #4CAF50; }
        .toast-error { border-left-color: #f44336; }

        /* HIDDEN */
        .hidden {
            display: none !important;
        }

        /* PROFILE */
        .profile-card {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: 30px;
            text-align: center;
            margin-bottom: 30px;
        }

        .profile-avatar-img {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid #FF69B4;
            margin-bottom: 15px;
        }

        .profile-avatar-placeholder {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: linear-gradient(135deg, #FF69B4, #FF1493);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 32px;
            margin: 0 auto 15px;
        }

        .profile-name {
            font-size: 24px;
            font-weight: bold;
        }

        .profile-balance {
            font-size: 32px;
            color: #FF69B4;
            font-weight: bold;
            margin: 15px 0;
        }

        .stats-row {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin: 20px 0;
        }

        .stat-item {
            background: #FFF0F5;
            padding: 15px;
            border-radius: 12px;
        }

        .stat-num {
            font-size: 24px;
            font-weight: bold;
            color: #FF69B4;
        }

        .stat-label {
            font-size: 11px;
            color: #666;
            margin-top: 5px;
        }

        /* ADMIN */
        .admin-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .admin-tab {
            padding: 10px 20px;
            background: white;
            border: 2px solid #e0e0e0;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 500;
        }

        .admin-tab.active {
            background: #FF69B4;
            color: white;
            border-color: #FF69B4;
        }

        .admin-table {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            overflow-x: auto;
        }

        .admin-table table {
            width: 100%;
            border-collapse: collapse;
        }

        .admin-table th {
            background: #FFF0F5;
            padding: 12px;
            text-align: left;
            font-size: 13px;
        }

        .admin-table td {
            padding: 10px 12px;
            border-bottom: 1px solid #f0f0f0;
            font-size: 13px;
        }

        .btn-sm {
            padding: 6px 14px;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            font-size: 11px;
            font-weight: 600;
            margin: 2px;
            transition: all 0.3s;
        }

        .btn-sm:hover {
            transform: translateY(-1px);
        }

        .btn-blue { background: #2196F3; color: white; }
        .btn-red { background: #f44336; color: white; }
        .btn-green { background: #4CAF50; color: white; }
        .btn-orange { background: #ff9800; color: white; }

        /* RESULT MODAL */
        .result-form {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            margin: 20px 0;
        }

        .result-input {
            text-align: center;
        }

        .result-input label {
            display: block;
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 14px;
        }

        .result-input input {
            width: 80px;
            padding: 12px;
            text-align: center;
            font-size: 28px;
            font-weight: bold;
            border: 2px solid #FFB6D5;
            border-radius: 10px;
            color: #FF69B4;
        }

        .result-input input:focus {
            outline: none;
            border-color: #FF69B4;
        }

        .result-vs {
            font-size: 24px;
            font-weight: bold;
            color: #999;
        }

        /* FILTERS */
        .filters {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .search-input {
            padding: 10px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 25px;
            font-size: 14px;
            min-width: 250px;
        }

        .search-input:focus {
            outline: none;
            border-color: #FF69B4;
        }

        .filter-select {
            padding: 10px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 25px;
            font-size: 14px;
            cursor: pointer;
        }

        .prediction-badge {
            background: #FFF0F5;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 12px;
            color: #FF69B4;
            font-weight: 600;
            margin-top: 8px;
            text-align: center;
        }

        /* BANNER DE AVISO DE SALVAMENTO */
        .save-indicator {
            position: fixed;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
            background: #4CAF50;
            color: white;
            padding: 8px 20px;
            border-radius: 20px;
            font-size: 13px;
            font-weight: 600;
            z-index: 4000;
            opacity: 0;
            transition: all 0.5s;
            pointer-events: none;
        }

        .save-indicator.show {
            opacity: 1;
            top: 20px;
        }

        /* CONFIGURAÇÕES DO SITE */
        .config-section {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: 25px;
            margin-bottom: 20px;
        }

        .config-section h3 {
            color: #FF69B4;
            margin-bottom: 15px;
        }

        .logo-preview {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 15px;
            background: #f5f5f5;
            border-radius: 8px;
            margin: 15px 0;
        }

        .logo-preview-label {
            font-weight: 600;
            color: #666;
            min-width: 100px;
        }

        @media (max-width: 768px) {
            .matches-grid {
                grid-template-columns: 1fr;
            }
            .banner {
                padding: 30px 15px;
            }
            .banner h1 {
                font-size: 24px;
            }
            .stats-row {
                grid-template-columns: 1fr;
            }
            .score-inputs {
                gap: 10px;
            }
        }
    </style>
</head>
<body>
    <!-- INDICADOR DE SALVAMENTO -->
    <div class="save-indicator" id="saveIndicator">💾 Alterações salvas permanentemente!</div>

    <!-- HEADER -->
    <header class="header">
        <div class="header-content">
            <div class="logo" onclick="showPage('home')" id="siteLogoContainer">
                <!-- Logo será carregada dinamicamente -->
            </div>
            <nav class="nav-links" id="navLinks">
                <a onclick="showPage('home')">Início</a>
                <a onclick="showPage('matches')">Partidas</a>
                <a onclick="showPage('ranking')">Ranking</a>
                <button class="btn btn-outline" onclick="openModal('loginModal')">Login</button>
                <button class="btn btn-pink" onclick="openModal('registerModal')">Cadastrar</button>
            </nav>
        </div>
    </header>

    <!-- BANNER -->
    <div class="banner">
        <h1>⚽ Bem-vindo ao <span id="bannerSiteName">Crasy Win</span>!</h1>
        <p>Faça seus palpites e ganhe Web Coins! 🏆</p>
        <p style="margin-top: 10px; font-size: 14px;">Aposta mínima: 20 WC | Ganhe 20 WC ao se cadastrar</p>
        <p style="margin-top: 5px; font-size: 12px; opacity: 0.8;">💾 Todas as alterações são salvas automaticamente!</p>
    </div>

    <!-- CONTAINER -->
    <div class="container">
        <!-- HOME PAGE -->
        <div id="homePage">
            <div class="section-title">🔥 Partidas em Destaque</div>
            <div class="matches-grid" id="featuredMatches"></div>
            <div class="section-title">🏆 Últimos Vencedores</div>
            <div class="ranking-list" id="recentWinners"></div>
        </div>

        <!-- MATCHES PAGE -->
        <div id="matchesPage" class="hidden">
            <div class="section-title">⚽ Todas as Partidas</div>
            <div class="filters">
                <input type="text" placeholder="🔍 Pesquisar..." class="search-input" onkeyup="filterMatches(this.value)">
                <select class="filter-select" onchange="filterChamp(this.value)">
                    <option value="">Todos os Campeonatos</option>
                    <option value="Brasileirão">Brasileirão</option>
                    <option value="Premier League">Premier League</option>
                    <option value="La Liga">La Liga</option>
                    <option value="Champions League">Champions League</option>
                </select>
            </div>
            <div class="matches-grid" id="allMatches"></div>
        </div>

        <!-- RANKING PAGE -->
        <div id="rankingPage" class="hidden">
            <div class="section-title">📊 Ranking Global</div>
            <div class="ranking-list" id="fullRanking"></div>
        </div>

        <!-- PROFILE PAGE -->
        <div id="profilePage" class="hidden">
            <div class="profile-card">
                <div id="profileAvatar"></div>
                <div class="profile-name" id="profileName">Usuário</div>
                <div class="profile-balance" id="profileBalance">💰 0 WC</div>
                <button class="btn btn-pink" onclick="claimBonus()">🎁 Resgatar Bônus Diário (100 WC)</button>
                <div class="stats-row">
                    <div class="stat-item">
                        <div class="stat-num" id="totalPred">0</div>
                        <div class="stat-label">Palpites</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-num" id="totalWin">0</div>
                        <div class="stat-label">Vitórias</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-num" id="winRate">0%</div>
                        <div class="stat-label">Aproveitamento</div>
                    </div>
                </div>
            </div>
            <div class="section-title">📜 Histórico de Palpites</div>
            <div class="matches-grid" id="predHistory"></div>
        </div>

        <!-- ADMIN PANEL -->
        <div id="adminPanel" class="hidden">
            <div class="profile-card" style="background: #1a1a1a; color: white;">
                <div style="font-size: 40px;">🔧</div>
                <h2>Painel Administrativo</h2>
                <p style="font-size: 12px; opacity: 0.7;">Todas as alterações são salvas automaticamente</p>
            </div>
            
            <div class="admin-tabs">
                <button class="admin-tab active" onclick="showAdmin('config', this)">⚙️ Configurações</button>
                <button class="admin-tab" onclick="showAdmin('users', this)">👥 Usuários</button>
                <button class="admin-tab" onclick="showAdmin('matches', this)">⚽ Partidas</button>
                <button class="admin-tab" onclick="showAdmin('stats', this)">📊 Estatísticas</button>
            </div>
            
            <!-- NOVO: Painel de Configurações -->
            <div id="adminConfig">
                <div class="config-section">
                    <h3>🎨 Personalização do Site</h3>
                    
                    <div class="form-group">
                        <label>Nome do Site</label>
                        <input type="text" id="siteName" placeholder="Crasy Win" value="Crasy Win">
                    </div>
                    
                    <div class="form-group">
                        <label>URL da Logo do Site (recomendado: 40x40px)</label>
                        <input type="url" id="siteLogoUrl" placeholder="https://exemplo.com/logo.png">
                        <small style="color: #666; display: block; margin-top: 5px;">Deixe em branco para usar o logo padrão</small>
                    </div>
                    
                    <div class="logo-preview">
                        <span class="logo-preview-label">Pré-visualização:</span>
                        <div id="logoPreview"></div>
                    </div>
                    
                    <div class="form-group">
                        <label>Ícone da Aba (Favicon) - URL</label>
                        <input type="url" id="siteFavicon" placeholder="https://exemplo.com/favicon.ico">
                        <small style="color: #666; display: block; margin-top: 5px;">URL do ícone que aparece na aba do navegador</small>
                    </div>
                    
                    <button class="btn btn-pink btn-full" onclick="saveSiteConfig()">💾 Salvar Configurações</button>
                </div>
            </div>
            
            <div id="adminUsers" class="hidden">
                <div class="admin-table">
                    <table>
                        <thead>
                            <tr>
                                <th>Usuário</th>
                                <th>Email</th>
                                <th>WC</th>
                                <th>Status</th>
                                <th>Ações</th>
                            </tr>
                        </thead>
                        <tbody id="adminUsersTable"></tbody>
                    </table>
                </div>
            </div>
            
            <div id="adminMatches" class="hidden">
                <button class="btn btn-pink" onclick="addMatch()" style="margin-bottom: 15px;">➕ Nova Partida</button>
                <div class="admin-table">
                    <table>
                        <thead>
                            <tr>
                                <th>Partida</th>
                                <th>Campeonato</th>
                                <th>Data</th>
                                <th>Status</th>
                                <th>Placar</th>
                                <th>Ações</th>
                            </tr>
                        </thead>
                        <tbody id="adminMatchesTable"></tbody>
                    </table>
                </div>
            </div>

            <div id="adminStats" class="hidden">
                <div class="profile-card">
                    <h3>Estatísticas do Sistema</h3>
                    <p style="margin-top: 15px;"><strong>Usuários:</strong> <span id="statUsers">0</span></p>
                    <p><strong>Partidas:</strong> <span id="statMatches">0</span></p>
                    <p><strong>Palpites:</strong> <span id="statPredictions">0</span></p>
                    <p><strong>Web Coins em circulação:</strong> <span id="statCoins">0</span> WC</p>
                </div>
            </div>
        </div>
    </div>

    <!-- LOGIN MODAL -->
    <div class="modal" id="loginModal">
        <div class="modal-content">
            <div class="modal-title">🔐 Login</div>
            <form onsubmit="doLogin(event)">
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" id="loginEmail" placeholder="seu@email.com" required>
                </div>
                <div class="form-group">
                    <label>Senha</label>
                    <input type="password" id="loginPassword" placeholder="Sua senha" required>
                </div>
                <button type="submit" class="btn btn-pink btn-full">Entrar</button>
            </form>
            <p class="text-center mt-15">
                Não tem conta? <span class="link" onclick="closeModal('loginModal'); openModal('registerModal');">Cadastre-se</span>
            </p>
            <button class="btn btn-outline btn-full mt-15" onclick="closeModal('loginModal')">Cancelar</button>
        </div>
    </div>

    <!-- REGISTER MODAL -->
    <div class="modal" id="registerModal">
        <div class="modal-content">
            <div class="modal-title">✨ Cadastro</div>
            <p style="text-align: center; margin-bottom: 15px; color: #FF69B4;">Ganhe 20 Web Coins!</p>
            <form onsubmit="doRegister(event)">
                <div class="form-group">
                    <label>Nome</label>
                    <input type="text" id="regName" placeholder="Seu nome" required>
                </div>
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" id="regEmail" placeholder="seu@email.com" required>
                </div>
                <div class="form-group">
                    <label>Senha</label>
                    <input type="password" id="regPass" placeholder="Mínimo 6 caracteres" required minlength="6">
                </div>
                <div class="form-group">
                    <label>URL da Foto de Perfil (opcional)</label>
                    <input type="url" id="regAvatar" placeholder="https://exemplo.com/foto.jpg">
                </div>
                <button type="submit" class="btn btn-pink btn-full">Criar Conta</button>
            </form>
            <button class="btn btn-outline btn-full mt-15" onclick="closeModal('registerModal')">Cancelar</button>
        </div>
    </div>

    <!-- RESULT MODAL -->
    <div class="modal" id="resultModal">
        <div class="modal-content">
            <div class="modal-title">📝 Definir Placar Final</div>
            <p style="text-align: center; margin-bottom: 15px; color: #666;" id="resultMatchInfo"></p>
            <form onsubmit="saveResult(event)">
                <div class="result-form">
                    <div class="result-input">
                        <label id="resultHomeLabel"></label>
                        <input type="number" id="resultHomeScore" min="0" max="99" required>
                    </div>
                    <div class="result-vs">X</div>
                    <div class="result-input">
                        <label id="resultAwayLabel"></label>
                        <input type="number" id="resultAwayScore" min="0" max="99" required>
                    </div>
                </div>
                <input type="hidden" id="resultMatchId">
                <button type="submit" class="btn btn-pink btn-full">✅ Confirmar Resultado</button>
            </form>
            <button class="btn btn-outline btn-full mt-15" onclick="closeModal('resultModal')">Cancelar</button>
        </div>
    </div>

    <!-- TOAST CONTAINER -->
    <div id="toastContainer"></div>

    <script>
        // ============ CONFIGURAÇÕES DO SITE ============
        let siteConfig = JSON.parse(localStorage.getItem('cw_site_config')) || {
            siteName: 'Crasy Win',
            logoUrl: '',
            favicon: ''
        };

        function saveSiteConfigToStorage() {
            localStorage.setItem('cw_site_config', JSON.stringify(siteConfig));
        }

        // ============ DATA ============
        let currentUser = null;
        let users = JSON.parse(localStorage.getItem('cw_users')) || [];
        let matches = JSON.parse(localStorage.getItem('cw_matches')) || [];
        let predictions = JSON.parse(localStorage.getItem('cw_predictions')) || [];

        // ============ FUNÇÕES AUXILIARES PARA LOGOS ============
        function getTeamLogo(logoUrl, teamName) {
            if (logoUrl && logoUrl.startsWith('http')) {
                return `<img src="${logoUrl}" alt="${teamName}" class="team-logo" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';">`;
            } else {
                const initials = teamName.split(' ').map(w => w[0]).join('').substring(0, 2).toUpperCase();
                return `<div class="team-logo-placeholder">${initials}</div>`;
            }
        }

        function getUserAvatar(avatarUrl, username) {
            if (avatarUrl && avatarUrl.startsWith('http')) {
                return `<img src="${avatarUrl}" alt="${username}" class="user-avatar-img" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';">`;
            } else {
                const initial = username.charAt(0).toUpperCase();
                return `<div class="user-avatar-placeholder">${initial}</div>`;
            }
        }

        function getProfileAvatar(avatarUrl, username) {
            if (avatarUrl && avatarUrl.startsWith('http')) {
                return `<img src="${avatarUrl}" alt="${username}" class="profile-avatar-img" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';">`;
            } else {
                const initial = username.charAt(0).toUpperCase();
                return `<div class="profile-avatar-placeholder">${initial}</div>`;
            }
        }

        // ============ FUNÇÃO DA LOGO DO SITE ============
        function updateSiteLogo() {
            const logoContainer = document.getElementById('siteLogoContainer');
            const bannerSiteName = document.getElementById('bannerSiteName');
            
            // Atualiza nome do site no banner
            if (bannerSiteName) {
                bannerSiteName.textContent = siteConfig.siteName;
            }
            
            // Atualiza título da página
            document.title = siteConfig.siteName;
            
            // Atualiza favicon
            if (siteConfig.favicon && siteConfig.favicon.startsWith('http')) {
                let faviconLink = document.getElementById('dynamicFavicon');
                if (!faviconLink) {
                    faviconLink = document.createElement('link');
                    faviconLink.id = 'dynamicFavicon';
                    faviconLink.rel = 'icon';
                    document.head.appendChild(faviconLink);
                }
                faviconLink.href = siteConfig.favicon;
            }
            
            // Monta a logo
            let logoHTML = '';
            if (siteConfig.logoUrl && siteConfig.logoUrl.startsWith('http')) {
                logoHTML = `
                    <img src="${siteConfig.logoUrl}" alt="${siteConfig.siteName}" class="site-logo-img" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';">
                    <span class="site-logo-text" style="display:none;">${siteConfig.siteName}</span>
                `;
            } else {
                logoHTML = `
                    <div class="site-logo-placeholder">🎯</div>
                    <span class="site-logo-text">${siteConfig.siteName}</span>
                `;
            }
            
            logoContainer.innerHTML = logoHTML;
        }

        function updateLogoPreview() {
            const logoUrl = document.getElementById('siteLogoUrl').value;
            const preview = document.getElementById('logoPreview');
            
            if (logoUrl && logoUrl.startsWith('http')) {
                preview.innerHTML = `
                    <img src="${logoUrl}" alt="Preview" class="site-logo-img" onerror="this.src='data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%2240%22 height=%2240%22><rect fill=%22%23ddd%22 width=%2240%22 height=%2240%22/><text x=%2250%%22 y=%2250%%22 text-anchor=%22middle%22 dy=%22.3em%22 fill=%22%23999%22 font-size=%2212%22>ERRO</text></svg>';">
                    <span style="margin-left:10px;color:#4CAF50;">✅ Logo carregada</span>
                `;
            } else {
                preview.innerHTML = `
                    <div class="site-logo-placeholder">🎯</div>
                    <span style="margin-left:10px;color:#666;">Logo padrão</span>
                `;
            }
        }

        function saveSiteConfig() {
            const siteName = document.getElementById('siteName').value.trim();
            const logoUrl = document.getElementById('siteLogoUrl').value.trim();
            const favicon = document.getElementById('siteFavicon').value.trim();
            
            if (!siteName) {
                toast('O nome do site é obrigatório!', 'error');
                return;
            }
            
            siteConfig.siteName = siteName;
            siteConfig.logoUrl = logoUrl;
            siteConfig.favicon = favicon;
            
            saveSiteConfigToStorage();
            updateSiteLogo();
            showSaveIndicator();
            
            toast('✅ Configurações salvas com sucesso!', 'success');
        }

        function loadSiteConfigToForm() {
            document.getElementById('siteName').value = siteConfig.siteName;
            document.getElementById('siteLogoUrl').value = siteConfig.logoUrl;
            document.getElementById('siteFavicon').value = siteConfig.favicon;
            updateLogoPreview();
        }

        // Event listener para preview em tempo real
        document.addEventListener('DOMContentLoaded', function() {
            const logoUrlInput = document.getElementById('siteLogoUrl');
            if (logoUrlInput) {
                logoUrlInput.addEventListener('input', updateLogoPreview);
            }
        });

        // ============ INIT DEFAULT DATA ============
        function initData() {
            if (users.length === 0) {
                users = [
                    { 
                        id: 1, 
                        username: 'admin', 
                        email: 'admin@crasywin.com', 
                        password: 'admin123', 
                        avatar: '',
                        webCoins: 20, 
                        totalWins: 50, 
                        totalPredictions: 100, 
                        isBlocked: false, 
                        isAdmin: true, 
                        lastBonus: null 
                    },
                    { 
                        id: 2, 
                        username: 'jogador1', 
                        email: 'jogador1@email.com', 
                        password: '123456', 
                        avatar: 'https://i.pravatar.cc/150?img=1',
                        webCoins: 20, 
                        totalWins: 15, 
                        totalPredictions: 30, 
                        isBlocked: false, 
                        isAdmin: false, 
                        lastBonus: null 
                    },
                    { 
                        id: 3, 
                        username: 'craque', 
                        email: 'craque@email.com', 
                        password: '123456', 
                        avatar: 'https://i.pravatar.cc/150?img=2',
                        webCoins: 20, 
                        totalWins: 25, 
                        totalPredictions: 40, 
                        isBlocked: false, 
                        isAdmin: false, 
                        lastBonus: null 
                    }
                ];
                saveUsers();
            } else {
                let updated = false;
                users.forEach(u => {
                    if (u.webCoins < 20) {
                        u.webCoins = 20;
                        updated = true;
                    }
                    if (!u.avatar) {
                        u.avatar = '';
                        updated = true;
                    }
                });
                if (updated) saveUsers();
            }

            if (matches.length === 0) {
                const now = new Date();
                matches = [
                    { 
                        id: 1, 
                        homeTeam: 'Flamengo', 
                        awayTeam: 'Palmeiras', 
                        homeLogo: 'https://logodetimes.com/times/flamengo/logo-flamengo-256.png',
                        awayLogo: 'https://logodetimes.com/times/palmeiras/logo-palmeiras-256.png',
                        championship: 'Brasileirão', 
                        date: new Date(now.getTime() + 3600000).toISOString(), 
                        status: 'scheduled', 
                        homeScore: 0, 
                        awayScore: 0, 
                        participants: 45, 
                        prizePool: 450 
                    },
                    { 
                        id: 2, 
                        homeTeam: 'Man City', 
                        awayTeam: 'Liverpool', 
                        homeLogo: 'https://logodetimes.com/times/manchester-city/logo-manchester-city-256.png',
                        awayLogo: 'https://logodetimes.com/times/liverpool/logo-liverpool-256.png',
                        championship: 'Premier League', 
                        date: new Date(now.getTime() + 7200000).toISOString(), 
                        status: 'live', 
                        homeScore: 1, 
                        awayScore: 0, 
                        participants: 120, 
                        prizePool: 2400 
                    },
                    { 
                        id: 3, 
                        homeTeam: 'Barcelona', 
                        awayTeam: 'Real Madrid', 
                        homeLogo: 'https://logodetimes.com/times/barcelona/logo-barcelona-256.png',
                        awayLogo: 'https://logodetimes.com/times/real-madrid/logo-real-madrid-256.png',
                        championship: 'La Liga', 
                        date: new Date(now.getTime() + 86400000).toISOString(), 
                        status: 'scheduled', 
                        homeScore: 0, 
                        awayScore: 0, 
                        participants: 200, 
                        prizePool: 5000 
                    },
                    { 
                        id: 4, 
                        homeTeam: 'PSG', 
                        awayTeam: 'Bayern', 
                        homeLogo: 'https://logodetimes.com/times/psg/logo-psg-256.png',
                        awayLogo: 'https://logodetimes.com/times/bayern-munique/logo-bayern-munique-256.png',
                        championship: 'Champions League', 
                        date: new Date(now.getTime() + 172800000).toISOString(), 
                        status: 'scheduled', 
                        homeScore: 0, 
                        awayScore: 0, 
                        participants: 300, 
                        prizePool: 9000 
                    },
                    { 
                        id: 5, 
                        homeTeam: 'Santos', 
                        awayTeam: 'Corinthians', 
                        homeLogo: 'https://logodetimes.com/times/santos/logo-santos-256.png',
                        awayLogo: 'https://logodetimes.com/times/corinthians/logo-corinthians-256.png',
                        championship: 'Brasileirão', 
                        date: new Date(now.getTime() - 86400000).toISOString(), 
                        status: 'finished', 
                        homeScore: 2, 
                        awayScore: 1, 
                        participants: 80, 
                        prizePool: 1600 
                    }
                ];
                saveMatches();
            } else {
                let updated = false;
                matches.forEach(m => {
                    if (!m.homeLogo) {
                        m.homeLogo = '';
                        updated = true;
                    }
                    if (!m.awayLogo) {
                        m.awayLogo = '';
                        updated = true;
                    }
                });
                if (updated) saveMatches();
            }
        }

        // ============ FUNÇÕES DE SALVAMENTO PERMANENTE ============
        function saveUsers() { 
            localStorage.setItem('cw_users', JSON.stringify(users)); 
            showSaveIndicator();
        }
        
        function saveMatches() { 
            localStorage.setItem('cw_matches', JSON.stringify(matches)); 
            showSaveIndicator();
        }
        
        function savePredictions() { 
            localStorage.setItem('cw_predictions', JSON.stringify(predictions)); 
            showSaveIndicator();
        }

        let saveTimeout;
        function showSaveIndicator() {
            const indicator = document.getElementById('saveIndicator');
            indicator.classList.add('show');
            clearTimeout(saveTimeout);
            saveTimeout = setTimeout(() => {
                indicator.classList.remove('show');
            }, 2000);
        }

        // ============ NAVIGATION ============
        function showPage(page) {
            document.querySelectorAll('#homePage, #matchesPage, #rankingPage, #profilePage').forEach(el => el.classList.add('hidden'));
            document.getElementById(page + 'Page').classList.remove('hidden');

            if (page === 'home') { loadFeatured(); loadWinners(); }
            if (page === 'matches') loadAllMatches();
            if (page === 'ranking') loadRanking();
            if (page === 'profile') {
                if (!currentUser) { openModal('loginModal'); return; }
                loadProfile();
            }
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function updateNav() {
            const nav = document.getElementById('navLinks');
            if (currentUser) {
                nav.innerHTML = `
                    <a onclick="showPage('home')">Início</a>
                    <a onclick="showPage('matches')">Partidas</a>
                    <a onclick="showPage('ranking')">Ranking</a>
                    <a onclick="showPage('profile')">${getUserAvatar(currentUser.avatar, currentUser.username)} ${currentUser.username}</a>
                    <span style="background:#FFF0F5; padding:8px 15px; border-radius:20px; font-weight:600; color:#FF69B4;">💰 ${currentUser.webCoins} WC</span>
                    <button class="btn btn-outline" onclick="logout()">Sair</button>
                `;
                if (currentUser.isAdmin) document.getElementById('adminPanel').classList.remove('hidden');
            } else {
                nav.innerHTML = `
                    <a onclick="showPage('home')">Início</a>
                    <a onclick="showPage('matches')">Partidas</a>
                    <a onclick="showPage('ranking')">Ranking</a>
                    <button class="btn btn-outline" onclick="openModal('loginModal')">Login</button>
                    <button class="btn btn-pink" onclick="openModal('registerModal')">Cadastrar</button>
                `;
                document.getElementById('adminPanel').classList.add('hidden');
            }
        }

        // ============ AUTH ============
        function doLogin(e) {
            e.preventDefault();
            const email = document.getElementById('loginEmail').value.trim();
            const pass = document.getElementById('loginPassword').value;
            const user = users.find(u => u.email === email && u.password === pass);
            if (!user) { toast('Email ou senha inválidos!', 'error'); return; }
            if (user.isBlocked) { toast('Usuário bloqueado!', 'error'); return; }
            currentUser = user;
            closeModal('loginModal');
            updateNav();
            showPage('home');
            toast('Bem-vindo, ' + user.username + '!', 'success');
            document.getElementById('loginEmail').value = '';
            document.getElementById('loginPassword').value = '';
        }

        function doRegister(e) {
            e.preventDefault();
            const name = document.getElementById('regName').value.trim();
            const email = document.getElementById('regEmail').value.trim();
            const pass = document.getElementById('regPass').value;
            const avatarUrl = document.getElementById('regAvatar').value.trim();
            
            if (users.find(u => u.email === email)) { toast('Email já cadastrado!', 'error'); return; }
            
            const newUser = { 
                id: Date.now(), 
                username: name, 
                email, 
                password: pass, 
                avatar: avatarUrl,
                webCoins: 20,
                totalWins: 0, 
                totalPredictions: 0, 
                isBlocked: false, 
                isAdmin: false, 
                lastBonus: null 
            };
            
            users.push(newUser);
            saveUsers();
            currentUser = newUser;
            closeModal('registerModal');
            updateNav();
            showPage('home');
            toast('Conta criada! +20 WC 🎉', 'success');
            document.getElementById('regName').value = '';
            document.getElementById('regEmail').value = '';
            document.getElementById('regPass').value = '';
            document.getElementById('regAvatar').value = '';
        }

        function logout() {
            currentUser = null;
            updateNav();
            showPage('home');
            toast('Logout realizado! Sessão encerrada.', 'info');
        }

        // ============ MATCHES ============
        function matchCard(m) {
            const d = new Date(m.date);
            const dateStr = d.toLocaleDateString('pt-BR');
            const timeStr = d.toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' });
            
            let statusBadge = '';
            if (m.status === 'live') statusBadge = '<span class="badge badge-live">🔴 AO VIVO</span>';
            else if (m.status === 'finished') statusBadge = '<span class="badge badge-done">✅ Encerrado</span>';

            const center = m.status === 'finished' 
                ? `<div class="match-score">${m.homeScore} - ${m.awayScore}</div>`
                : '<div class="match-vs">VS</div>';

            let betSection = '';
            if (m.status === 'scheduled' && currentUser && !currentUser.isAdmin) {
                const existingBet = predictions.find(p => p.userId === currentUser.id && p.matchId === m.id);
                if (existingBet) {
                    betSection = `<div class="already-bet">✅ Você apostou ${existingBet.bet} WC<br>Placar: ${existingBet.homeScore} x ${existingBet.awayScore}</div>`;
                } else {
                    betSection = `<button class="btn-bet" onclick="openBetForm(${m.id}, '${m.homeTeam}', '${m.awayTeam}')">🎯 Apostar Agora</button>`;
                }
            }

            return `
                <div class="match-card">
                    <div class="match-header">
                        <span class="badge badge-champ">${m.championship}</span>
                        ${statusBadge}
                    </div>
                    <div class="match-teams">
                        <div class="team">
                            ${getTeamLogo(m.homeLogo, m.homeTeam)}
                            <div class="team-name">${m.homeTeam}</div>
                        </div>
                        ${center}
                        <div class="team">
                            ${getTeamLogo(m.awayLogo, m.awayTeam)}
                            <div class="team-name">${m.awayTeam}</div>
                        </div>
                    </div>
                    <div class="match-info">📅 ${dateStr} | 🕐 ${timeStr}</div>
                    <div class="match-footer">
                        <span>👥 ${m.participants} palpites</span>
                        <span class="prize">🏆 ${m.prizePool} WC</span>
                    </div>
                    ${betSection}
                </div>
            `;
        }

        function loadFeatured() {
            const c = document.getElementById('featuredMatches');
            const list = matches.filter(m => m.status !== 'finished').slice(0, 3);
            c.innerHTML = list.length ? list.map(matchCard).join('') : '<p style="text-align:center;padding:40px;">Nenhuma partida no momento.</p>';
        }

        function loadAllMatches(f = '') {
            const c = document.getElementById('allMatches');
            let list = matches;
            if (f) {
                const t = f.toLowerCase();
                list = matches.filter(m => m.homeTeam.toLowerCase().includes(t) || m.awayTeam.toLowerCase().includes(t) || m.championship.toLowerCase().includes(t));
            }
            c.innerHTML = list.length ? list.map(matchCard).join('') : '<p style="text-align:center;padding:40px;">Nenhuma partida.</p>';
        }

        function filterMatches(v) { loadAllMatches(v); }
        function filterChamp(v) {
            const c = document.getElementById('allMatches');
            const list = v ? matches.filter(m => m.championship === v) : matches;
            c.innerHTML = list.length ? list.map(matchCard).join('') : '<p style="text-align:center;padding:40px;">Nenhuma partida.</p>';
        }

        // ============ BET SYSTEM ============
        function openBetForm(matchId, homeTeam, awayTeam) {
            if (!currentUser) { openModal('loginModal'); return; }
            
            const match = matches.find(m => m.id === matchId);
            if (!match) return;
            
            const betForm = document.createElement('div');
            betForm.className = 'bet-form';
            betForm.id = 'betForm-' + matchId;
            betForm.innerHTML = `
                <h4 style="text-align:center; margin-bottom:15px; color:#FF69B4;">🎯 Seu Palpite</h4>
                <div class="score-inputs">
                    <div class="score-input-group">
                        <label>${homeTeam}</label>
                        <input type="number" id="betHome-${matchId}" min="0" max="99" value="0" required>
                    </div>
                    <div style="font-size:24px;font-weight:bold;color:#ccc;">X</div>
                    <div class="score-input-group">
                        <label>${awayTeam}</label>
                        <input type="number" id="betAway-${matchId}" min="0" max="99" value="0" required>
                    </div>
                </div>
                <div class="bet-amount-group">
                    <label>💰 Valor da Aposta (mínimo 20 WC)</label>
                    <div class="bet-controls">
                        <button class="bet-btn-ctrl" onclick="changeBetValue(${matchId}, -10)">-</button>
                        <span class="bet-value" id="betValue-${matchId}">20</span>
                        <button class="bet-btn-ctrl" onclick="changeBetValue(${matchId}, 10)">+</button>
                        <span style="font-weight:bold;color:#FF69B4;">WC</span>
                    </div>
                    <p style="font-size:11px;color:#666;margin-top:5px;">Seu saldo: ${currentUser.webCoins} WC</p>
                </div>
                <button class="btn-confirm-bet" onclick="confirmBet(${matchId}, '${homeTeam}', '${awayTeam}')">✅ Confirmar Aposta</button>
                <button class="btn btn-outline btn-full mt-15" onclick="cancelBet(${matchId})">Cancelar</button>
            `;
            
            const matchCards = document.querySelectorAll('.match-card');
            matchCards.forEach(card => {
                const btn = card.querySelector(`[onclick*="openBetForm(${matchId}"]`);
                if (btn) {
                    btn.style.display = 'none';
                    card.appendChild(betForm);
                }
            });
        }

        function changeBetValue(matchId, amount) {
            const valueEl = document.getElementById('betValue-' + matchId);
            let current = parseInt(valueEl.textContent);
            current = Math.max(20, Math.min(current + amount, currentUser ? currentUser.webCoins : 20));
            valueEl.textContent = current;
        }

        function confirmBet(matchId, homeTeam, awayTeam) {
            const homeScore = parseInt(document.getElementById('betHome-' + matchId).value);
            const awayScore = parseInt(document.getElementById('betAway-' + matchId).value);
            const betAmount = parseInt(document.getElementById('betValue-' + matchId).textContent);
            
            if (isNaN(homeScore) || isNaN(awayScore)) {
                toast('Preencha o placar!', 'error');
                return;
            }
            
            if (betAmount < 20) {
                toast('Aposta mínima: 20 WC', 'error');
                return;
            }
            
            if (currentUser.webCoins < betAmount) {
                toast('Saldo insuficiente!', 'error');
                return;
            }
            
            const match = matches.find(m => m.id === matchId);
            if (!match) return;
            
            const prediction = {
                id: Date.now(),
                userId: currentUser.id,
                matchId,
                homeScore,
                awayScore,
                bet: betAmount,
                isCorrect: false,
                date: new Date().toISOString()
            };
            
            predictions.push(prediction);
            currentUser.webCoins -= betAmount;
            currentUser.totalPredictions++;
            match.participants++;
            match.prizePool += betAmount;
            
            const idx = users.findIndex(u => u.id === currentUser.id);
            if (idx !== -1) users[idx] = currentUser;
            
            savePredictions();
            saveUsers();
            saveMatches();
            updateNav();
            
            toast(`Aposta de ${betAmount} WC registrada e salva! 🎯`, 'success');
            
            if (!document.getElementById('matchesPage').classList.contains('hidden')) {
                loadAllMatches();
            } else {
                loadFeatured();
            }
        }

        function cancelBet(matchId) {
            const betForm = document.getElementById('betForm-' + matchId);
            if (betForm) {
                betForm.remove();
                const matchCards = document.querySelectorAll('.match-card');
                matchCards.forEach(card => {
                    const btn = card.querySelector(`[onclick*="openBetForm(${matchId}"]`);
                    if (btn) btn.style.display = 'block';
                });
            }
        }

        // ============ RANKING ============
        function loadWinners() {
            const c = document.getElementById('recentWinners');
            const list = [...users].filter(u => !u.isBlocked).sort((a, b) => b.webCoins - a.webCoins).slice(0, 5);
            c.innerHTML = list.map((u, i) => {
                let cls = '', icon = `#${i+1}`;
                if (i === 0) { cls = 'gold'; icon = '🥇'; }
                else if (i === 1) { cls = 'silver'; icon = '🥈'; }
                else if (i === 2) { cls = 'bronze'; icon = '🥉'; }
                return `<div class="ranking-item">
                    <div class="rank-num ${cls}">${icon}</div>
                    ${getUserAvatar(u.avatar, u.username)}
                    <div class="user-info"><div class="user-name">${u.username}</div><div class="user-stats">${u.totalWins} vitórias</div></div>
                    <div class="user-coins">💰 ${u.webCoins} WC</div>
                </div>`;
            }).join('');
        }

        function loadRanking() {
            const c = document.getElementById('fullRanking');
            const list = [...users].filter(u => !u.isBlocked).sort((a, b) => b.webCoins - a.webCoins);
            c.innerHTML = list.map((u, i) => {
                let cls = '', icon = `#${i+1}`;
                if (i === 0) { cls = 'gold'; icon = '🥇'; }
                else if (i === 1) { cls = 'silver'; icon = '🥈'; }
                else if (i === 2) { cls = 'bronze'; icon = '🥉'; }
                const rate = u.totalPredictions > 0 ? Math.round((u.totalWins / u.totalPredictions) * 100) : 0;
                return `<div class="ranking-item">
                    <div class="rank-num ${cls}">${icon}</div>
                    ${getUserAvatar(u.avatar, u.username)}
                    <div class="user-info"><div class="user-name">${u.username}</div><div class="user-stats">${u.totalWins} vitórias | ${rate}% | ${u.totalPredictions} palpites</div></div>
                    <div class="user-coins">💰 ${u.webCoins} WC</div>
                </div>`;
            }).join('');
        }

        // ============ PROFILE ============
        function loadProfile() {
            if (!currentUser) return;
            document.getElementById('profileAvatar').innerHTML = getProfileAvatar(currentUser.avatar, currentUser.username);
            document.getElementById('profileName').textContent = currentUser.username;
            document.getElementById('profileBalance').textContent = `💰 ${currentUser.webCoins} WC`;
            document.getElementById('totalPred').textContent = currentUser.totalPredictions;
            document.getElementById('totalWin').textContent = currentUser.totalWins;
            document.getElementById('winRate').textContent = (currentUser.totalPredictions > 0 ? Math.round((currentUser.totalWins / currentUser.totalPredictions) * 100) : 0) + '%';
            
            const hist = predictions.filter(p => p.userId === currentUser.id).sort((a, b) => new Date(b.date) - new Date(a.date));
            const c = document.getElementById('predHistory');
            if (!hist.length) { c.innerHTML = '<p style="text-align:center;padding:40px;">Nenhum palpite ainda.</p>'; return; }
            c.innerHTML = hist.map(p => {
                const m = matches.find(x => x.id === p.matchId);
                if (!m) return '';
                const col = p.isCorrect ? '#4CAF50' : '#f44336';
                return `<div class="match-card" style="border-left:4px solid ${col};">
                    <div class="match-header">
                        <span class="badge badge-champ">${m.championship}</span>
                        <span style="color:${col};font-weight:bold;">${p.isCorrect ? '✅ GANHOU ' + (p.bet * 2) + ' WC' : '❌ PERDEU'}</span>
                    </div>
                    <p><strong>${m.homeTeam} ${m.homeScore} x ${m.awayScore} ${m.awayTeam}</strong></p>
                    <p style="color:#666;font-size:13px;">
                        Seu palpite: ${p.homeScore} x ${p.awayScore} | 
                        Aposta: ${p.bet} WC | 
                        ${new Date(p.date).toLocaleDateString('pt-BR')}
                    </p>
                </div>`;
            }).join('');
        }

        function claimBonus() {
            if (!currentUser) return;
            const today = new Date().toDateString();
            if (currentUser.lastBonus === today) { toast('Bônus já resgatado hoje!', 'info'); return; }
            currentUser.webCoins += 100;
            currentUser.lastBonus = today;
            const idx = users.findIndex(u => u.id === currentUser.id);
            if (idx !== -1) users[idx] = currentUser;
            saveUsers();
            updateNav();
            loadProfile();
            toast('🎁 +100 WC! Bônus salvo!', 'success');
        }

        // ============ ADMIN ============
        function showAdmin(tab, btn) {
            document.querySelectorAll('#adminConfig, #adminUsers, #adminMatches, #adminStats').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.admin-tab').forEach(el => el.classList.remove('active'));
            if (btn) btn.classList.add('active');
            if (tab === 'config') { 
                document.getElementById('adminConfig').classList.remove('hidden'); 
                loadSiteConfigToForm();
            }
            if (tab === 'users') { document.getElementById('adminUsers').classList.remove('hidden'); loadAdminUsers(); }
            if (tab === 'matches') { document.getElementById('adminMatches').classList.remove('hidden'); loadAdminMatches(); }
            if (tab === 'stats') { document.getElementById('adminStats').classList.remove('hidden'); loadStats(); }
        }

        function loadAdminUsers() {
            document.getElementById('adminUsersTable').innerHTML = users.map(u => `
                <tr>
                    <td>${getUserAvatar(u.avatar, u.username)} <strong>${u.username}</strong> ${u.isAdmin ? '<span style="background:gold;padding:2px 8px;border-radius:10px;font-size:10px;">ADMIN</span>' : ''}</td>
                    <td>${u.email}</td>
                    <td><strong>${u.webCoins} WC</strong></td>
                    <td><span style="color:${u.isBlocked ? '#f44336' : '#4CAF50'};font-weight:bold;">${u.isBlocked ? 'Bloqueado' : 'Ativo'}</span></td>
                    <td>
                        <button class="btn-sm ${u.isBlocked ? 'btn-green' : 'btn-orange'}" onclick="toggleBlock(${u.id})">${u.isBlocked ? 'Desbloquear' : 'Bloquear'}</button>
                        <button class="btn-sm btn-blue" onclick="editCoins(${u.id})">💰</button>
                    </td>
                </tr>
            `).join('');
        }

        function toggleBlock(id) {
            const u = users.find(x => x.id === id);
            if (u && !u.isAdmin) { 
                u.isBlocked = !u.isBlocked; 
                saveUsers(); 
                loadAdminUsers(); 
                toast('Status alterado e salvo!', 'info'); 
            }
        }

        function editCoins(id) {
            const u = users.find(x => x.id === id);
            if (!u) return;
            const v = prompt(`Saldo de ${u.username}: ${u.webCoins} WC\nNovo valor:`);
            if (v !== null && !isNaN(v) && parseInt(v) >= 0) {
                u.webCoins = parseInt(v);
                saveUsers();
                loadAdminUsers();
                if (currentUser && currentUser.id === id) { currentUser = u; updateNav(); }
                toast('Saldo atualizado e salvo!', 'success');
            }
        }

        function loadAdminMatches() {
            document.getElementById('adminMatchesTable').innerHTML = matches.map(m => {
                const scoreDisplay = m.status === 'finished' ? `<strong style="color:#FF69B4;">${m.homeScore} x ${m.awayScore}</strong>` : '<span style="color:#999;">-</span>';
                return `
                <tr>
                    <td><strong>${m.homeTeam}</strong> vs <strong>${m.awayTeam}</strong></td>
                    <td>${m.championship}</td>
                    <td>${new Date(m.date).toLocaleString('pt-BR')}</td>
                    <td>
                        <select onchange="updStatus(${m.id}, this.value)" style="padding:5px;border-radius:5px;">
                            <option value="scheduled" ${m.status === 'scheduled' ? 'selected' : ''}>Agendado</option>
                            <option value="live" ${m.status === 'live' ? 'selected' : ''}>Ao Vivo</option>
                            <option value="finished" ${m.status === 'finished' ? 'selected' : ''}>Encerrado</option>
                        </select>
                    </td>
                    <td>${scoreDisplay}</td>
                    <td>
                        <button class="btn-sm btn-blue" onclick="openResultModal(${m.id})">📝 Definir Placar</button>
                        <button class="btn-sm btn-red" onclick="delMatch(${m.id})">🗑️</button>
                    </td>
                </tr>
            `}).join('');
        }

        function updStatus(id, s) {
            const m = matches.find(x => x.id === id);
            if (m) { 
                m.status = s; 
                saveMatches(); 
                loadAdminMatches(); 
                toast('Status atualizado e salvo!', 'success'); 
            }
        }

        function openResultModal(matchId) {
            const m = matches.find(x => x.id === matchId);
            if (!m) return;
            
            document.getElementById('resultMatchInfo').textContent = `${m.homeTeam} vs ${m.awayTeam} - ${m.championship}`;
            document.getElementById('resultHomeLabel').textContent = m.homeTeam;
            document.getElementById('resultAwayLabel').textContent = m.awayTeam;
            document.getElementById('resultHomeScore').value = m.homeScore || 0;
            document.getElementById('resultAwayScore').value = m.awayScore || 0;
            document.getElementById('resultMatchId').value = matchId;
            
            openModal('resultModal');
        }

        function saveResult(e) {
            e.preventDefault();
            
            const matchId = parseInt(document.getElementById('resultMatchId').value);
            const homeScore = parseInt(document.getElementById('resultHomeScore').value);
            const awayScore = parseInt(document.getElementById('resultAwayScore').value);
            
            const m = matches.find(x => x.id === matchId);
            if (!m) return;
            
            m.homeScore = homeScore;
            m.awayScore = awayScore;
            m.status = 'finished';
            
            let winnersCount = 0;
            predictions.filter(p => p.matchId === matchId).forEach(p => {
                const u = users.find(x => x.id === p.userId);
                if (!u) return;
                
                p.isCorrect = (p.homeScore === homeScore && p.awayScore === awayScore);
                
                if (p.isCorrect) {
                    const prize = p.bet * 2;
                    u.webCoins += prize;
                    u.totalWins++;
                    winnersCount++;
                }
            });
            
            saveMatches();
            savePredictions();
            saveUsers();
            loadAdminMatches();
            closeModal('resultModal');
            
            if (currentUser) {
                currentUser = users.find(x => x.id === currentUser.id);
                updateNav();
            }
            
            toast(`✅ Placar definido! ${winnersCount} vencedor(es)! Dados salvos permanentemente!`, 'success');
        }

        function delMatch(id) {
            if (confirm('Excluir esta partida e todos os palpites relacionados? Esta ação é permanente!')) {
                matches = matches.filter(m => m.id !== id);
                predictions = predictions.filter(p => p.matchId !== id);
                saveMatches();
                savePredictions();
                loadAdminMatches();
                toast('Partida excluída permanentemente!', 'success');
            }
        }

        function addMatch() {
            const ht = prompt('Time mandante:');
            if (!ht) return;
            const at = prompt('Time visitante:');
            if (!at) return;
            const ch = prompt('Campeonato:');
            if (!ch) return;
            const hrs = prompt('Horas até a partida:', '24');
            if (!hrs) return;
            const homeLogoUrl = prompt('URL do logo do time mandante (opcional):', '');
            const awayLogoUrl = prompt('URL do logo do time visitante (opcional):', '');
            
            matches.push({
                id: Date.now(), 
                homeTeam: ht, 
                awayTeam: at, 
                homeLogo: homeLogoUrl, 
                awayLogo: awayLogoUrl,
                championship: ch, 
                date: new Date(Date.now() + parseInt(hrs) * 3600000).toISOString(),
                status: 'scheduled', 
                homeScore: 0, 
                awayScore: 0, 
                participants: 0, 
                prizePool: 0
            });
            saveMatches();
            loadAdminMatches();
            toast('Partida adicionada e salva!', 'success');
        }

        function loadStats() {
            document.getElementById('statUsers').textContent = users.length;
            document.getElementById('statMatches').textContent = matches.length;
            document.getElementById('statPredictions').textContent = predictions.length;
            document.getElementById('statCoins').textContent = users.reduce((s, u) => s + u.webCoins, 0);
        }

        // ============ MODALS ============
        function openModal(id) { document.getElementById(id).classList.add('active'); }
        function closeModal(id) { document.getElementById(id).classList.remove('active'); }

        // ============ TOAST ============
        function toast(msg, type) {
            const c = document.getElementById('toastContainer');
            const t = document.createElement('div');
            t.className = `toast toast-${type}`;
            t.textContent = msg;
            c.appendChild(t);
            setTimeout(() => { t.style.opacity = '0'; t.style.transition = '0.3s'; setTimeout(() => t.remove(), 300); }, 3000);
        }

        // ============ EVENTS ============
        window.addEventListener('click', (e) => {
            if (e.target.classList.contains('modal') && e.target.classList.contains('active')) {
                e.target.classList.remove('active');
            }
        });

        // ============ START ============
        initData();
        updateSiteLogo();
        updateNav();
        showPage('home');
        
        console.log('✅ Crasy Win pronto!');
        console.log('💾 SISTEMA DE SALVAMENTO PERMANENTE ATIVO');
        console.log('💰 20 WC INICIAIS PARA NOVAS CONTAS');
        console.log('🖼️ SISTEMA DE LOGOS POR URL ATIVADO');
        console.log('⚙️ PAINEL DE CONFIGURAÇÕES DISPONÍVEL NO ADMIN');
        console.log('👑 Admin: admin@crasywin.com / admin123');
        console.log('👤 User: jogador1@email.com / 123456');
    </script>
</body>
</html>
