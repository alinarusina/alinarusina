<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Менеджмент в общественных спортивных организациях</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #0f172a;
            color: #e2e8f0;
            overflow: hidden;
        }

        .presentation {
            width: 100vw;
            height: 100vh;
            position: relative;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            display: none;
            padding: 60px;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            overflow-y: auto;
        }

        .slide.active {
            display: flex;
            flex-direction: column;
            animation: fadeIn 0.6s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .slide-header {
            margin-bottom: 40px;
            border-bottom: 3px solid #3b82f6;
            padding-bottom: 20px;
        }

        h1 {
            font-size: 3em;
            background: linear-gradient(90deg, #60a5fa, #a78bfa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
            font-weight: 800;
        }

        h2 {
            font-size: 2.2em;
            color: #60a5fa;
            margin-bottom: 30px;
            font-weight: 700;
        }

        h3 {
            font-size: 1.5em;
            color: #94a3b8;
            margin-bottom: 20px;
        }

        .content {
            flex: 1;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            align-items: start;
        }

        .full-width {
            grid-column: 1 / -1;
        }

        .card {
            background: rgba(30, 41, 59, 0.8);
            border: 1px solid #334155;
            border-radius: 16px;
            padding: 30px;
            backdrop-filter: blur(10px);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            border-color: #3b82f6;
        }

        .card-accent {
            border-left: 4px solid #3b82f6;
        }

        .card-success {
            border-left: 4px solid #10b981;
        }

        .card-warning {
            border-left: 4px solid #f59e0b;
        }

        ul {
            list-style: none;
            padding-left: 0;
        }

        li {
            padding: 12px 0;
            padding-left: 30px;
            position: relative;
            font-size: 1.1em;
            line-height: 1.6;
        }

        li:before {
            content: "▸";
            position: absolute;
            left: 0;
            color: #3b82f6;
            font-weight: bold;
            font-size: 1.2em;
        }

        .highlight {
            background: linear-gradient(90deg, rgba(59, 130, 246, 0.2), transparent);
            padding: 2px 8px;
            border-radius: 4px;
            color: #60a5fa;
            font-weight: 600;
        }

        .warning-text {
            color: #f59e0b;
            font-weight: 600;
        }

        .success-text {
            color: #10b981;
            font-weight: 600;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            font-size: 0.95em;
        }

        th {
            background: #1e40af;
            color: white;
            padding: 15px;
            text-align: left;
            font-weight: 600;
        }

        td {
            padding: 15px;
            border-bottom: 1px solid #334155;
            background: rgba(30, 41, 59, 0.5);
        }

        tr:hover td {
            background: rgba(59, 130, 246, 0.1);
        }

        .navigation {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 1000;
            background: rgba(15, 23, 42, 0.9);
            padding: 15px 30px;
            border-radius: 50px;
            border: 1px solid #334155;
            backdrop-filter: blur(10px);
        }

        button {
            background: #3b82f6;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1em;
            font-weight: 600;
            transition: all 0.3s;
        }

        button:hover {
            background: #2563eb;
            transform: scale(1.05);
        }

        button:disabled {
            background: #475569;
            cursor: not-allowed;
            transform: none;
        }

        .slide-number {
            position: fixed;
            top: 30px;
            right: 30px;
            background: rgba(59, 130, 246, 0.2);
            padding: 10px 20px;
            border-radius: 20px;
            font-weight: 600;
            color: #60a5fa;
            border: 1px solid #3b82f6;
        }

        .two-columns {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        .icon-box {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #3b82f6, #8b5cf6);
            border-radius: 12px;
            margin-right: 15px;
            font-size: 1.5em;
        }

        .flex-row {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .stat-box {
            background: linear-gradient(135deg, #1e40af, #3b82f6);
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            margin: 10px;
        }

        .stat-number {
            font-size: 2.5em;
            font-weight: 800;
            color: white;
        }

        .stat-label {
            color: #bfdbfe;
            font-size: 0.9em;
            margin-top: 5px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin: 30px 0;
        }

        @media (max-width: 1024px) {
            .content {
                grid-template-columns: 1fr;
            }
            .two-columns {
                grid-template-columns: 1fr;
            }
            h1 { font-size: 2em; }
            h2 { font-size: 1.5em; }
        }

        .fade-in {
            animation: fadeIn 0.8s ease-out;
        }

        .delay-1 { animation-delay: 0.1s; }
        .delay-2 { animation-delay: 0.2s; }
        .delay-3 { animation-delay: 0.3s; }

        .progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            height: 4px;
            background: linear-gradient(90deg, #3b82f6, #8b5cf6);
            transition: width 0.3s;
            z-index: 1001;
        }
    </style>
</head>
<body>
    <div class="progress-bar" id="progressBar"></div>
    <div class="slide-number" id="slideNumber">1 / 12</div>

    <div class="presentation">
        <!-- Slide 1: Title -->
        <div class="slide active">
            <div style="display: flex; flex-direction: column; justify-content: center; align-items: center; height: 100%; text-align: center;">
                <div style="font-size: 4em; margin-bottom: 30px;">🏛️</div>
                <h1 style="font-size: 3.5em; margin-bottom: 20px;">МЕНЕДЖМЕНТ В ОБЩЕСТВЕННЫХ<br>СПОРТИВНЫХ ОРГАНИЗАЦИЯХ</h1>
                <h3 style="font-size: 1.8em; color: #94a3b8; margin-bottom: 40px;">Лекция №6</h3>
                <div style="background: rgba(59, 130, 246, 0.1); padding: 30px; border-radius: 16px; border: 1px solid #3b82f6; max-width: 800px;">
                    <p style="font-size: 1.3em; line-height: 1.8; color: #cbd5e1;">
                        Правовые основы, организационные формы и управление<br>
                        физкультурно-спортивными объединениями в Российской Федерации
                    </p>
                </div>
                <div style="margin-top: 50px; display: flex; gap: 30px;">
                    <div class="stat-box" style="min-width: 200px;">
                        <div class="stat-number">300+</div>
                        <div class="stat-label">Общероссийских объединений</div>
                    </div>
                    <div class="stat-box" style="min-width: 200px;">
                        <div class="stat-number">5000+</div>
                        <div class="stat-label">Спортивных организаций</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 2: Legal Forms -->
        <div class="slide">
            <div class="slide-header">
                <h2>Организационно-правовые формы</h2>
                <h3>Федеральный закон №82-ФЗ «Об общественных объединениях»</h3>
            </div>
            <div class="content">
                <div class="card card-accent fade-in">
                    <div class="flex-row">
                        <div class="icon-box">👥</div>
                        <h3 style="margin: 0;">Общественная организация</h3>
                    </div>
                    <ul>
                        <li>Основана на <span class="highlight">членстве</span></li>
                        <li>ОКР, спортивные союзы, ассоциации</li>
                        <li>ДФСО, спортклубы</li>
                        <li>Совет при Президенте по физкультуре и спорту</li>
                    </ul>
                </div>

                <div class="card card-success fade-in delay-1">
                    <div class="flex-row">
                        <div class="icon-box" style="background: linear-gradient(135deg, #10b981, #059669);">🌊</div>
                        <h3 style="margin: 0;">Общественное движение</h3>
                    </div>
                    <ul>
                        <li>Массовое объединение</li>
                        <li>Участники <span class="highlight">не имеют членства</span></li>
                        <li>Достижение социальных целей</li>
                        <li>Гибкая форма координации</li>
                    </ul>
                </div>

                <div class="card card-warning fade-in delay-2">
                    <div class="flex-row">
                        <div class="icon-box" style="background: linear-gradient(135deg, #f59e0b, #d97706);">💰</div>
                        <h3 style="margin: 0;">Общественный фонд</h3>
                    </div>
                    <ul>
                        <li>Некоммерческий фонд</li>
                        <li>Без членства</li>
                        <li>Формирование имущества на добровольной основе</li>
                        <li>Целевое использование ресурсов</li>
                    </ul>
                </div>

                <div class="card fade-in delay-3" style="border-left: 4px solid #8b5cf6;">
                    <div class="flex-row">
                        <div class="icon-box" style="background: linear-gradient(135deg, #8b5cf6, #7c3aed);">🏢</div>
                        <h3 style="margin: 0;">Общественное учреждение</h3>
                    </div>
                    <ul>
                        <li>Цель — оказание услуг</li>
                        <li>Не имеет членства</li>
                        <li>Уставная деятельность</li>
                        <li>Объединения в форме союзов, ассоциаций, лиг</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Slide 3: Sport Interest -->
        <div class="slide">
            <div class="slide-header">
                <h2>Спортивный интерес</h2>
                <h3>Основа объединения граждан в спортивные организации</h3>
            </div>
            <div class="content" style="grid-template-columns: 1fr;">
                <div class="full-width">
                    <div class="card" style="margin-bottom: 30px;">
                        <p style="font-size: 1.3em; line-height: 1.8; text-align: center; font-style: italic; color: #94a3b8;">
                            «Осознанная потребность человека заниматься каким-либо видом спорта»<br>
                            <span style="font-size: 0.8em; color: #64748b;">— И.И. Переверзин</span>
                        </p>
                    </div>
                    
                    <div class="two-columns">
                        <div class="card card-accent">
                            <h3 style="color: #60a5fa; margin-bottom: 20px;">Характеристики</h3>
                            <ul>
                                <li><span class="highlight">Избирательная направленность</span> — выбор конкретного вида спорта</li>
                                <li><span class="highlight">Многообразие и взаимосвязи</span> — пересечение интересов</li>
                                <li><span class="highlight">Возрастная динамика</span> — угасание с возрастом</li>
                                <li><span class="highlight">Устойчивость</span> — переход в привычный образ жизни</li>
                                <li><span class="highlight">Стремление к достижениям</span> — мотивация роста</li>
                            </ul>
                        </div>

                        <div class="card" style="border-left: 4px solid #ec4899;">
                            <h3 style="color: #ec4899; margin-bottom: 20px;">Правовое регулирование</h3>
                            <ul>
                                <li>Конституция РФ — право на объединение</li>
                                <li>ФЗ «Об общественных объединениях»</li>
                                <li>ФЗ «О некоммерческих организациях»</li>
                                <li>Объединение физических и юридических лиц</li>
                                <li>Не менее <span class="warning-text">3 учредителей</span></li>
                            </ul>
                            <div style="background: rgba(239, 68, 68, 0.1); padding: 15px; border-radius: 8px; margin-top: 20px; border-left: 3px solid #ef4444;">
                                <p style="color: #fca5a5; margin: 0;"><strong>Важно:</strong> Государственные органы и органы местного самоуправления <strong>не могут</strong> быть учредителями общественной организации</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 4: Creation Methods -->
        <div class="slide">
            <div class="slide-header">
                <h2>Способы создания общественной организации</h2>
                <h3>Три модели правового существования</h3>
            </div>
            <div class="content" style="grid-template-columns: repeat(3, 1fr);">
                <div class="card" style="border-top: 4px solid #ef4444;">
                    <div style="text-align: center; margin-bottom: 20px;">
                        <div style="font-size: 3em; margin-bottom: 10px;">📝</div>
                        <h3 style="color: #ef4444;">Способ 1</h3>
                        <div style="font-size: 1.2em; font-weight: 600;">Без регистрации</div>
                    </div>
                    <ul style="font-size: 0.95em;">
                        <li>Форма: <span class="highlight">Общественное движение</span></li>
                        <li>Нет прав юридического лица</li>
                        <li>Невозможна финансово-хозяйственная деятельность</li>
                        <li>Нельзя открывать расчетные счета</li>
                        <li>Максимальная гибкость, минимум формальностей</li>
                    </ul>
                </div>

                <div class="card" style="border-top: 4px solid #10b981;">
                    <div style="text-align: center; margin-bottom: 20px;">
                        <div style="font-size: 3em; margin-bottom: 10px;">✅</div>
                        <h3 style="color: #10b981;">Способ 2</h3>
                        <div style="font-size: 1.2em; font-weight: 600;">С регистрацией</div>
                    </div>
                    <ul style="font-size: 0.95em;">
                        <li>Приобретение прав <span class="success-text">юридического лица</span></li>
                        <li>Государственная регистрация в органах юстиции</li>
                        <li>Возможность ведения уставной деятельности</li>
                        <li>Открытие расчетных счетов</li>
                        <li>Участие в грантовых программах</li>
                    </ul>
                </div>

                <div class="card" style="border-top: 4px solid #f59e0b;">
                    <div style="text-align: center; margin-bottom: 20px;">
                        <div style="font-size: 3em; margin-bottom: 10px;">🏗️</div>
                        <h3 style="color: #f59e0b;">Способ 3</h3>
                        <div style="font-size: 1.2em; font-weight: 600;">Структурное подразделение</div>
                    </div>
                    <ul style="font-size: 0.95em;">
                        <li>Создание на правах <span class="highlight">структурного подразделения</span></li>
                        <li>Другой организации с юридическим лицом</li>
                        <li>Не требует регистрации в органах юстиции</li>
                        <li>Работа через учредителя-юрлицо</li>
                        <li>Зависимость от головной организации</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Slide 5: OKR -->
        <div class="slide">
            <div class="slide-header">
                <h2>Олимпийский комитет России (ОКР)</h2>
                <h3>Наиболее значимое общероссийское объединение</h3>
            </div>
            <div class="content">
                <div class="card card-accent">
                    <h3 style="color: #60a5fa; margin-bottom: 20px;">Статус и структура</h3>
                    <ul>
                        <li>Создан для развития Олимпийского движения</li>
                        <li>Подразделения в <span class="highlight">34 регионах</span> России</li>
                        <li>Президент: <strong>Михаил Владимирович Дегтярев</strong></li>
                        <li>Члены: физические и юридические лица</li>
                        <li>Спортивные федерации, олимпийские академии</li>
                    </ul>
                    
                    <div style="margin-top: 20px; padding: 15px; background: rgba(30, 41, 59, 0.8); border-radius: 8px;">
                        <h4 style="color: #94a3b8; margin-bottom: 10px;">Руководящие органы:</h4>
                        <p style="margin: 5px 0;">• Олимпийское собрание (высший орган)</p>
                        <p style="margin: 5px 0;">• Исполком (оперативное управление)</p>
                        <p style="margin: 5px 0;">• Президент (представительство)</p>
                        <p style="margin: 5px 0;">• Исполнительный директор</p>
                    </div>
                </div>

                <div class="card" style="border-left: 4px solid #fbbf24;">
                    <h3 style="color: #fbbf24; margin-bottom: 20px;">Основные задачи</h3>
                    <div style="display: grid; gap: 15px;">
                        <div style="padding: 15px; background: rgba(251, 191, 36, 0.1); border-radius: 8px; border-left: 3px solid #fbbf24;">
                            <strong style="color: #fbbf24;">Стратегические</strong>
                            <p style="margin: 5px 0; font-size: 0.95em;">Развитие олимпийского движения, укрепление престижа, координация федераций</p>
                        </div>
                        <div style="padding: 15px; background: rgba(59, 130, 246, 0.1); border-radius: 8px; border-left: 3px solid #3b82f6;">
                            <strong style="color: #60a5fa;">Развитие спорта</strong>
                            <p style="margin: 5px 0; font-size: 0.95em;">Массовый спорт, спорт высших достижений, олимпийское образование</p>
                        </div>
                        <div style="padding: 15px; background: rgba(16, 185, 129, 0.1); border-radius: 8px; border-left: 3px solid #10b981;">
                            <strong style="color: #10b981;">Организационные</strong>
                            <p style="margin: 5px 0; font-size: 0.95em;">Взаимодействие с госструктурами, международное сотрудничество</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 6: OKR Structure -->
        <div class="slide">
            <div class="slide-header">
                <h2>Структура ОКР</h2>
                <h3>Территориальная и функциональная иерархия</h3>
            </div>
            <div class="content" style="grid-template-columns: 1fr;">
                <div class="full-width">
                    <div style="text-align: center; margin-bottom: 40px;">
                        <div style="display: inline-block; background: linear-gradient(135deg, #1e40af, #3b82f6); padding: 30px 60px; border-radius: 16px; margin-bottom: 20px;">
                            <div style="font-size: 2em; font-weight: 800;">ОКР</div>
                            <div style="color: #bfdbfe;">Федеральный уровень (Москва)</div>
                        </div>
                        <div style="font-size: 2em; color: #3b82f6; margin: 10px 0;">↓</div>
                        <div style="display: inline-block; background: rgba(59, 130, 246, 0.2); padding: 20px 40px; border-radius: 12px; border: 2px solid #3b82f6; margin-bottom: 20px;">
                            <div style="font-size: 1.5em; font-weight: 700;">Региональные отделения</div>
                            <div style="color: #94a3b8;">34 субъекта РФ</div>
                        </div>
                        <div style="font-size: 2em; color: #3b82f6; margin: 10px 0;">↓</div>
                        <div style="display: inline-block; background: rgba(139, 92, 246, 0.2); padding: 20px 40px; border-radius: 12px; border: 2px solid #8b5cf6; margin-bottom: 20px;">
                            <div style="font-size: 1.5em; font-weight: 700;">Муниципальные опорные центры</div>
                            <div style="color: #94a3b8;">Представительства</div>
                        </div>
                        <div style="font-size: 2em; color: #3b82f6; margin: 10px 0;">↓</div>
                        <div style="display: inline-block; background: rgba(16, 185, 129, 0.2); padding: 20px 40px; border-radius: 12px; border: 2px solid #10b981;">
                            <div style="font-size: 1.5em; font-weight: 700;">Базовые организации</div>
                            <div style="color: #94a3b8;">Спортшколы, клубы, федерации</div>
                        </div>
                    </div>

                    <div class="two-columns" style="margin-top: 30px;">
                        <div class="card">
                            <h3 style="color: #60a5fa;">Ключевые комиссии</h3>
                            <ul>
                                <li>Комиссия спортсменов</li>
                                <li>Комиссия по олимпийскому образованию</li>
                                <li>Комиссия по этике и противодействию допингу</li>
                                <li>Научно-методический совет</li>
                            </ul>
                        </div>
                        <div class="card">
                            <h3 style="color: #60a5fa;">Функциональные подразделения</h3>
                            <ul>
                                <li>Маркетинговый департамент</li>
                                <li>Международный отдел</li>
                                <li>Пресс-служба</li>
                                <li>Административно-хозяйственный отдел</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 7: National Federations -->
        <div class="slide">
            <div class="slide-header">
                <h2>Национальные федерации по видам спорта</h2>
                <h3>Особенности менеджмента и государственная аккредитация</h3>
            </div>
            <div class="content">
                <div class="card card-accent">
                    <h3 style="color: #60a5fa; margin-bottom: 20px;">Исторический контекст</h3>
                    <ul>
                        <li>Номинально существуют с момента выхода СССР на международную арену</li>
                        <li>Требовалось признание международными федерациями</li>
                        <li>Функции долго выполнялись Госкомспортом СССР</li>
                        <li>Укрепление позиций началось в период перехода к рынку</li>
                        <li>Более <span class="highlight">80 общероссийских</span> и <span class="highlight">2000+ региональных</span> федераций</li>
                    </ul>
                    
                    <div style="margin-top: 20px; padding: 15px; background: rgba(59, 130, 246, 0.1); border-radius: 8px;">
                        <p style="margin: 0; color: #93c5fd;"><strong>Аккредитация:</strong> С 2014 года утвержден порядок госаккредитации. Срок действия — <span class="highlight">4 года</span>. Возможно отзыв или приостановление (пример: Федерация спортивных танцев, 2011-2013).</p>
                    </div>
                </div>

                <div class="card" style="border-left: 4px solid #ec4899;">
                    <h3 style="color: #ec4899; margin-bottom: 20px;">Основные задачи</h3>
                    <ul>
                        <li>Популяризация и развитие вида спорта</li>
                        <li>Подготовка сборных команд</li>
                        <li>Проведение официальных соревнований</li>
                        <li>Подготовка резерва сборных</li>
                    </ul>
                    
                    <h3 style="color: #ec4899; margin: 30px 0 20px;">Рекомендации World Athletics</h3>
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; font-size: 0.9em;">
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Миссия</div>
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Руководство</div>
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Средства</div>
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Связь</div>
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Соревнования</div>
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Инфраструктура</div>
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Кадры</div>
                        <div style="padding: 8px; background: rgba(236, 72, 153, 0.1); border-radius: 6px;">• Медподдержка</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 8: Leagues -->
        <div class="slide">
            <div class="slide-header">
                <h2>Профессиональные лиги</h2>
                <h3>Независимость и взаимодействие с федерациями</h3>
            </div>
            <div class="content" style="grid-template-columns: 1fr;">
                <div class="full-width">
                    <div style="background: linear-gradient(90deg, rgba(59, 130, 246, 0.2), rgba(139, 92, 246, 0.2)); padding: 20px; border-radius: 12px; margin-bottom: 30px; border-left: 4px solid #3b82f6;">
                        <p style="margin: 0; font-size: 1.1em;"><strong style="color: #60a5fa;">Актуализация 2024 года:</strong> С июля 2024 профессиональные лиги получили право на <span class="highlight">независимость от федераций</span>. КХЛ официально объявила о независимости от ФХР и ИИХФ.</p>
                    </div>

                    <div class="two-columns">
                        <div class="card">
                            <h3 style="color: #f59e0b;">Футбол</h3>
                            <ul>
                                <li><strong>РПЛ</strong> — тесная связка с РФС, элементы автономии</li>
                                <li><strong>ФНЛ/Первая лига</strong> (ранее «Высшая лига»)</li>
                                <li>Функционирование в рамках федерации</li>
                            </ul>
                        </div>

                        <div class="card">
                            <h3 style="color: #3b82f6;">Хоккей</h3>
                            <ul>
                                <li><strong>КХЛ</strong> — независимая структура с 2024</li>
                                <li>Прямое взаимодействие с Минспортом</li>
                                <li><strong>ВХЛ</strong> — фарм-клубы и развитие</li>
                            </ul>
                        </div>

                        <div class="card">
                            <h3 style="color: #ec4899;">Баскетбол</h3>
                            <ul>
                                <li><strong>Единая лига ВТБ</strong> — топ-уровень</li>
                                <li><strong>FONBET Суперлига</strong></li>
                                <li><strong>FONBET Высшая лига</strong></li>
                                <li>Единая молодежная лига ВТБ</li>
                            </ul>
                        </div>

                        <div class="card" style="border: 2px solid #10b981;">
                            <h3 style="color: #10b981;">Права лиг</h3>
                            <ul>
                                <li>Самостоятельная разработка регламентов</li>
                                <li>Утверждение переходов игроков</li>
                                <li>Аккредитация агентов</li>
                                <li>Заключение договоров и сделок</li>
                                <li>Имущество — неделимое</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 9: OGFSC -->
        <div class="slide">
            <div class="slide-header">
                <h2>Общественно-государственные физкультурно-спортивные объединения (ОГФСО)</h2>
                <h3>Гибридная организационно-правовая форма</h3>
            </div>
            <div class="content">
                <div class="card card-accent">
                    <h3 style="color: #60a5fa;">Нормативная база (2026 г.)</h3>
                    <ul>
                        <li>ФЗ от 04.12.2007 № 329-ФЗ «О физкультуре и спорте»</li>
                        <li>ФЗ от 19.05.1995 № 82-ФЗ «Об общественных объединениях»</li>
                        <li>Постановление Правительства РФ № 1108</li>
                        <li>Уставы конкретных объединений (ВФСО «Динамо», ФСО «Юность России»)</li>
                    </ul>
                    
                    <div style="margin-top: 20px; padding: 15px; background: rgba(239, 68, 68, 0.1); border-radius: 8px; border-left: 3px solid #ef4444;">
                        <p style="margin: 0; color: #fca5a5;"><strong>Ключевое отличие:</strong> Возможное участие государственных органов (Минспорт, МВД, ФСБ, Росгвардия) в качестве учредителей наряду с общественными структурами.</p>
                    </div>
                </div>

                <div class="card">
                    <h3 style="color: #fbbf24;">Сравнительный анализ</h3>
                    <table style="font-size: 0.9em;">
                        <thead>
                            <tr>
                                <th>Характеристика</th>
                                <th>Общественная федерация</th>
                                <th>ОГФСО</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><strong>Учредители</strong></td>
                                <td>Только частные лица</td>
                                <td>Госорганы + общественность</td>
                            </tr>
                            <tr>
                                <td><strong>Финансирование</strong></td>
                                <td>Членские взносы, гранты</td>
                                <td>Целевые субсидии, бюджет</td>
                            </tr>
                            <tr>
                                <td><strong>Имущество</strong></td>
                                <td>Частная собственность</td>
                                <td>Федеральная собственность</td>
                            </tr>
                            <tr>
                                <td><strong>Цель</strong></td>
                                <td>Развитие вида спорта</td>
                                <td>Ведомственный спорт, патриотизм</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Slide 10: Dynamo and Yunost -->
        <div class="slide">
            <div class="slide-header">
                <h2>Ключевые ОГФСО России</h2>
                <h3>ВФСО «Динамо» и ФСО «Юность России»</h3>
            </div>
            <div class="content">
                <div class="card" style="border-left: 4px solid #3b82f6;">
                    <div class="flex-row">
                        <div style="font-size: 2.5em; margin-right: 15px;">🏛️</div>
                        <div>
                            <h3 style="margin: 0; color: #3b82f6;">ВФСО «Динамо»</h3>
                            <p style="margin: 5px 0; color: #94a3b8;">Крупнейшее ведомственное спортивное общество</p>
                        </div>
                    </div>
                    <ul>
                        <li><strong>Учредители:</strong> МВД, ФСБ, Росгвардия, ФСО, Минюст, ФТС, Минспорт</li>
                        <li><strong>Реформа 2021-2022:</strong> Новый Устав, оптимизация структуры, усилен контроль региональных отделений</li>
                        <li><strong>Специфика:</strong> Спорт силовых ведомств, патриотическое воспитание, массовые мероприятия («Динамо-2026»)</li>
                        <li><strong>Инфраструктура:</strong> Клубная система, детско-юношеский спорт</li>
                    </ul>
                </div>

                <div class="card" style="border-left: 4px solid #ec4899;">
                    <div class="flex-row">
                        <div style="font-size: 2.5em; margin-right: 15px;">🎓</div>
                        <div>
                            <h3 style="margin: 0; color: #ec4899;">ФСО «Юность России»</h3>
                            <p style="margin: 5px 0; color: #94a3b8;">Ведущее общество для работы с детьми и молодежью</p>
                        </div>
                    </div>
                    <ul>
                        <li><strong>Учредители:</strong> Минпросвещения России, Минспорт, общественные организации</li>
                        <li><strong>Цель:</strong> Развитие детско-юношеского спорта</li>
                        <li><strong>Направления:</strong> Школьные соревнования, студенческие клубы, работа с образовательными учреждениями</li>
                        <li><strong>База:</strong> Школы, колледжи, вузы</li>
                    </ul>
                </div>

                <div class="card full-width" style="margin-top: 20px; border-left: 4px solid #10b981;">
                    <h3 style="color: #10b981;">Другие формы</h3>
                    <p>Отраслевые общества: <span class="highlight">«Локомотив»</span> (РЖД), <span class="highlight">«Спартак»</span> (профсоюзы) — имеют смешанный статус, но классические ОГФСО с прямым госучастием — «Динамо» и «Юность России».</p>
                </div>
            </div>
        </div>

        <!-- Slide 11: Management System -->
        <div class="slide">
            <div class="slide-header">
                <h2>Система управления ОГФСО</h2>
                <h3>Трехуровневая модель и финансовый менеджмент</h3>
            </div>
            <div class="content" style="grid-template-columns: 1fr;">
                <div class="full-width">
                    <div class="two-columns">
                        <div>
                            <div class="card" style="margin-bottom: 20px;">
                                <h3 style="color: #60a5fa;">Органы управления</h3>
                                <div style="margin-bottom: 15px; padding: 15px; background: rgba(59, 130, 246, 0.1); border-radius: 8px;">
                                    <strong style="color: #60a5fa;">1. Съезд (Конференция)</strong>
                                    <p style="margin: 5px 0; font-size: 0.95em;">Не реже 1 раза в 4 года. Утверждает Устав, Стратегию, избирает Центральный совет.</p>
                                </div>
                                <div style="margin-bottom: 15px; padding: 15px; background: rgba(139, 92, 246, 0.1); border-radius: 8px;">
                                    <strong style="color: #a78bfa;">2. Центральный Совет</strong>
                                    <p style="margin: 5px 0; font-size: 0.95em;">Коллегиальный орган. Утверждает бюджет, включает представителей учредителей.</p>
                                </div>
                                <div style="padding: 15px; background: rgba(16, 185, 129, 0.1); border-radius: 8px;">
                                    <strong style="color: #10b981;">3. Исполнительный орган</strong>
                                    <p style="margin: 5px 0; font-size: 0.95em;">Председатель/Исполнительный директор. Текущая деятельность, распоряжение имуществом.</p>
                                </div>
                            </div>
                        </div>

                        <div>
                            <div class="card" style="border-left: 4px solid #f59e0b;">
                                <h3 style="color: #f59e0b;">Источники финансирования</h3>
                                <ul style="font-size: 0.95em;">
                                    <li><strong>Субсидии из федерального бюджета</strong> — по Единому календарному плану (ЕКП)</li>
                                    <li><strong>Средства учредителей</strong> — ведомственное финансирование</li>
                                    <li><strong>Членские взносы</strong> — от региональных отделений</li>
                                    <li><strong>Предпринимательская деятельность</strong> — платные услуги, аренда</li>
                                    <li><strong>Гранты и пожертвования</strong> — Президентский фонд</li>
                                    <li><strong>Лотерейная деятельность</strong> — при наличии лицензии</li>
                                </ul>
                            </div>

                            <div class="card" style="margin-top: 20px; border-left: 4px solid #ec4899;">
                                <h3 style="color: #ec4899;">Территориальная структура</h3>
                                <p style="margin: 10px 0;"><strong>Федеральный уровень:</strong> Центральное общество (Москва)</p>
                                <p style="margin: 10px 0;"><strong>Региональный:</strong> Отделения в субъектах РФ</p>
                                <p style="margin: 10px 0;"><strong>Муниципальный:</strong> Клубы, секции, коллективы физкультуры</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 12: Trends -->
        <div class="slide">
            <div class="slide-header">
                <h2>Современные тенденции развития (2024–2026)</h2>
                <h3>Цифровизация и новые вызовы</h3>
            </div>
            <div class="content" style="grid-template-columns: repeat(2, 1fr);">
                <div class="card" style="border-top: 4px solid #3b82f6;">
                    <div style="font-size: 2em; margin-bottom: 15px;">💻</div>
                    <h3 style="color: #3b82f6;">Цифровая трансформация</h3>
                    <ul>
                        <li>Цифровые профили спортсменов</li>
                        <li>Интеграция с порталом «Госуслуги»</li>
                        <li>Онлайн-запись в спортивные секции</li>
                        <li>Единые информационные системы учета</li>
                    </ul>
                </div>

                <div class="card" style="border-top: 4px solid #10b981;">
                    <div style="font-size: 2em; margin-bottom: 15px;">📊</div>
                    <h3 style="color: #10b981;">Проектное управление</h3>
                    <ul>
                        <li>Переход от сметного финансирования</li>
                        <li>Финансирование по результатам (KPI)</li>
                        <li>Метрики: охват занимающихся, медиаохват, победы</li>
                        <li>Оценка эффективности программ</li>
                    </ul>
                </div>

                <div class="card" style="border-top: 4px solid #f59e0b;">
                    <div style="font-size: 2em; margin-bottom: 15px;">🤝</div>
                    <h3 style="color: #f59e0b;">Расширение партнерства</h3>
                    <ul>
                        <li>Совместные проекты с бизнесом (корпоративный спорт)</li>
                        <li>Интеграция с образовательными учреждениями</li>
                        <li>Спорт в школе как приоритет</li>
                        <li>Государственно-частное партнерство</li>
                    </ul>
                </div>

                <div class="card" style="border-top: 4px solid #ec4899;">
                    <div style="font-size: 2em; margin-bottom: 15px;">⚖️</div>
                    <h3 style="color: #ec4899;">Нормативное укрепление</h3>
                    <ul>
                        <li>Правовая основа ОГФСО отработана и стабильна</li>
                        <li>ФЗ № 214-ФЗ «О профессиональных спортивных лигах»</li>
                        <li>Упрощенное создание новых ОГФСО</li>
                        <li>Четкое разграничение компетенций</li>
                    </ul>
                </div>

                <div class="full-width" style="grid-column: 1 / -1; margin-top: 20px;">
                    <div style="background: linear-gradient(90deg, rgba(59, 130, 246, 0.2), rgba(139, 92, 246, 0.2)); padding: 30px; border-radius: 16px; text-align: center; border: 2px solid #3b82f6;">
                        <h3 style="color: #60a5fa; margin-bottom: 15px;">Будущее спортивного менеджмента</h3>
                        <p style="font-size: 1.2em; line-height: 1.6; color: #cbd5e1;">
                            Синергия государственной поддержки, общественной инициативы и частных инвестиций<br>
                            создает устойчивую экосистему развития физической культуры и спорта в России
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="navigation">
        <button onclick="prevSlide()" id="prevBtn">← Назад</button>
        <button onclick="nextSlide()" id="nextBtn">Вперед →</button>
    </div>

    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const totalSlides = slides.length;

        function showSlide(n) {
            slides.forEach(slide => slide.classList.remove('active'));
            
            if (n >= totalSlides) currentSlide = 0;
            if (n < 0) currentSlide = totalSlides - 1;
            
            slides[currentSlide].classList.add('active');
            
            document.getElementById('slideNumber').textContent = `${currentSlide + 1} / ${totalSlides}`;
            document.getElementById('progressBar').style.width = `${((currentSlide + 1) / totalSlides) * 100}%`;
            
            document.getElementById('prevBtn').disabled = currentSlide === 0;
            document.getElementById('nextBtn').disabled = currentSlide === totalSlides - 1;
        }

        function nextSlide() {
            if (currentSlide < totalSlides - 1) {
                currentSlide++;
                showSlide(currentSlide);
            }
        }

        function prevSlide() {
            if (currentSlide > 0) {
                currentSlide--;
                showSlide(currentSlide);
            }
        }

        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight' || e.key === ' ') {
                e.preventDefault();
                nextSlide();
            } else if (e.key === 'ArrowLeft') {
                e.preventDefault();
                prevSlide();
            }
        });

        showSlide(0);
    </script>
</body>
</pptx>
