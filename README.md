<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Скелет Умод - Моды на Bedrock</title>
    <style>
        :root {
            --primary-color: #00ff88; /* Неоновый зеленый */
            --bg-color: #121212;
            --card-bg: #1e1e1e;
            --text-color: #ffffff;
            --secondary-text: #b3b3b3;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
        }

        /* Шапка */
        header {
            background-color: #000;
            padding: 20px;
            text-align: center;
            border-bottom: 2px solid var(--primary-color);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        h1 {
            margin: 0;
            font-size: 24px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        h1 span {
            color: var(--primary-color);
        }

        /* Поиск */
        .search-container {
            margin-top: 15px;
            display: flex;
            justify-content: center;
        }

        input[type="text"] {
            width: 90%;
            max-width: 500px;
            padding: 12px;
            border-radius: 25px;
            border: none;
            background-color: #333;
            color: white;
            font-size: 16px;
            outline: none;
            transition: 0.3s;
        }

        input[type="text"]:focus {
            box-shadow: 0 0 10px var(--primary-color);
        }

        /* Сетка модов */
        .container {
            max-width: 1200px;
            margin: 20px auto;
            padding: 0 15px;
        }

        .mods-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
        }

        /* Карточка мода */
        .mod-card {
            background-color: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            transition: transform 0.2s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.3);
        }

        .mod-card:hover {
            transform: translateY(-5px);
        }

        .mod-image {
            width: 100%;
            height: 160px;
            background-color: #333;
            object-fit: cover;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #555;
            font-size: 40px;
        }

        .mod-content {
            padding: 15px;
        }

        .mod-title {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 5px;
            color: var(--primary-color);
        }

        .mod-desc {
            font-size: 14px;
            color: var(--secondary-text);
            margin-bottom: 15px;
            line-height: 1.4;
        }

        .download-btn {
            display: block;
            width: 100%;
            padding: 10px;
            background-color: var(--primary-color);
            color: #000;
            text-align: center;
            text-decoration: none;
            border-radius: 8px;
            font-weight: bold;
            transition: 0.3s;
        }

        .download-btn:hover {
            background-color: #fff;
        }

        footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            color: var(--secondary-text);
            font-size: 12px;
        }

        /* Анимация отсутствия результатов */
        .no-results {
            text-align: center;
            grid-column: 1 / -1;
            padding: 20px;
            color: var(--secondary-text);
        }
    </style>
</head>
<body>

<header>
    <h1>💀 Скелет <span>Умод</span></h1>
    <div class="search-container">
        <input type="text" id="searchInput" placeholder="Поиск модов (например: Драконы, Оружие)...">
    </div>
</header>

<div class="container">
    <div class="mods-grid" id="modsContainer">
        <!-- Сюда JavaScript будет добавлять моды -->
    </div>
</div>

<footer>
    &copy; 2026 Скелет Умод. Все права защищены.<br>
    Сайт создан для фанатов Minecraft Bedrock Edition.
</footer>

<script>
    // База данных модов (можно добавлять сюда свои)
    const modsData = [
        {
            title: "Драконы и Рюкзаки",
            desc: "Добавляет реалистичных драконов, которые растут и летают, а также удобные рюкзаки.",
            version: "1.21+",
            link: "#" 
        },
        {
            title: "Оружие будущего",
            desc: "Лазерные мечи, бластеры и новая броня. Полная переработка PvP.",
            version: "1.20+",
            link: "#"
        },
        {
            title: "Магия Эндера",
            desc: "Новые заклинания, посохи и мобы из измерения Края.",
            version: "1.21.50",
            link: "#"
        },
        {
            title: "Реалистичные машины",
            desc: "Машины, мотоциклы и автобусы, которые можно крафтить и водить.",
            version: "1.20+",
            link: "#"
        },
        {
            title: "Биомы Океана",
            desc: "Расширяет подводный мир новыми кораллами, рыбами и руинами.",
            version: "1.21+",
            link: "#"
        },
        {
            title: "Зомби Апокалипсис",
            desc: "Хардкорный мод. Зомби становятся умнее, быстрее и опаснее ночью.",
            version: "Любая",
            link: "#"
        }
    ];

    const container = document.getElementById('modsContainer');
    const searchInput = document.getElementById('searchInput');

    // Функция отрисовки модов
    function renderMods(mods) {
        container.innerHTML = ''; // Очистить контейнер
        
        if (mods.length === 0) {
            container.innerHTML = '<div class="no-results">Ничего не найдено 😔</div>';
            return;
        }

        mods.forEach(mod => {
            const card = document.createElement('div');
            card.className = 'mod-card';
            
            // В реальном сайте здесь была бы картинка <img>
            // Для примера используем заглушку с эмодзи
            card.innerHTML = `
                <div class="mod-image">📦</div>
                <div class="mod-content">
                    <div class="mod-title">${mod.title}</div>
                    <div class="mod-desc">${mod.desc} <br> <small style="color:#666">Версия: ${mod.version}</small></div>
                    <a href="${mod.link}" class="download-btn" download>Скачать .mcaddon</a>
                </div>
            `;
            container.appendChild(card);
        });
    }

    // Инициализация (показать все моды при загрузке)
    renderMods(modsData);

    // Логика поиска
    searchInput.addEventListener('input', (e) => {
        const searchTerm = e.target.value.toLowerCase();
        const filteredMods = modsData.filter(mod => 
            mod.title.toLowerCase().includes(searchTerm) || 
            mod.desc.toLowerCase().includes(searchTerm)
        );
        renderMods(filteredMods);
    });
</script>

</body>
</html>
