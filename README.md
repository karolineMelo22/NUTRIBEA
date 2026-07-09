<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🍏Painel do Nutricionista BEATRIZ XAVIER LEAL🧀🍞 </title>
    <!-- Google Fonts & FontAwesome -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #2ec4b6;
            --secondary: #ff9f1c;
            --dark: #011627;
            --light: #fbfbff;
            --success: #20bf6b;
            --danger: #ef476f;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #e0f2f1 0%, #fff3e0 100%);
            color: var(--dark);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(12px);
            border-radius: 24px;
            border: 1px solid rgba(255, 255, 255, 0.4);
            box-shadow: 0 16px 32px rgba(0, 0, 0, 0.1);
            padding: 40px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

        header h1 {
            font-size: 2.3rem;
            font-weight: 700;
        }

        header h1 span { color: var(--primary); }
        header p { color: #666; }

        /* Dashboard de Macros */
        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .dash-card {
            background: #fff;
            padding: 15px;
            border-radius: 16px;
            text-align: center;
            box-shadow: 0 8px 16px rgba(0,0,0,0.02);
            border-bottom: 4px solid var(--primary);
        }

        .dash-card.kcal { border-color: var(--secondary); }
        .dash-card.ptn { border-color: var(--danger); }
        .dash-card.cho { border-color: #06d6a0; }
        .dash-card.lip { border-color: #118ab2; }

        .dash-card h3 { font-size: 0.85rem; text-transform: uppercase; color: #777; }
        .dash-card p { font-size: 1.3rem; font-weight: 600; }

        /* Layout em Duas Colunas */
        .workspace {
            display: grid;
            grid-template-columns: 1fr 1.5fr;
            gap: 30px;
        }

        @media (max-width: 900px) {
            .workspace { grid-template-columns: 1fr; }
        }

        /* Formulário de Criação */
        .form-section {
            background: #fff;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.02);
            height: fit-content;
        }

        .form-section h2 {
            font-size: 1.2rem;
            margin-bottom: 20px;
            color: var(--dark);
            border-bottom: 2px solid #f0f0f0;
            padding-bottom: 10px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 5px;
            color: #555;
        }

        .form-control {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: 10px;
            font-size: 0.9rem;
            outline: none;
            transition: 0.3s;
        }

        .form-control:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(46, 196, 182, 0.15);
        }

        .macro-inputs {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
        }

        .btn-add {
            width: 100%;
            background: var(--primary);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 12px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
            margin-top: 10px;
        }

        .btn-add:hover { background: #24a195; }

        /* Lista de Refeições Geradas */
        .meals-section {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .meal-card {
            background: #fff;
            border-radius: 18px;
            padding: 20px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.02);
            position: relative;
            border-left: 5px solid var(--primary);
            animation: fadeIn 0.4s ease forwards;
        }

        .meal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .meal-title {
            font-size: 1.15rem;
            font-weight: 600;
        }

        .meal-time {
            font-size: 0.85rem;
            color: #aaa;
        }

        .food-text {
            font-size: 0.95rem;
            color: #444;
            white-space: pre-line; /* Mantém as quebras de linha */
            background: #f9f9f9;
            padding: 12px;
            border-radius: 10px;
            margin-bottom: 15px;
        }

        .meal-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.8rem;
            color: #666;
            border-top: 1px solid #f5f5f5;
            padding-top: 10px;
        }

        .btn-delete {
            background: none;
            border: none;
            color: var(--danger);
            cursor: pointer;
            font-size: 0.95rem;
            transition: 0.2s;
        }

        .btn-delete:hover { transform: scale(1.1); }

        .actions-footer {
            grid-column: 1 / -1;
            text-align: center;
            margin-top: 20px;
        }

        .btn-export {
            background: var(--dark);
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
            transition: 0.3s;
        }

        .btn-export:hover {
            background: var(--secondary);
            transform: translateY(-2px);
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="container">
        <header>
            <h1>🍇BEATRIZ LEAL SILVA XAVIER🧀🍞 <span>PROFISSIONAL</span></h1>
            <p>Monte o plano alimentar exclusivo do seu paciente em tempo real</p>
        </header>

        <!-- Contador Dinâmico de Calorias do Dia -->
        <div class="dashboard">
            <div class="dash-card kcal"><h3>Total Calorias</h3><p id="total-kcal">0 kcal</p></div>
            <div class="dash-card ptn"><h3>Proteínas</h3><p id="total-ptn">0g</p></div>
            <div class="dash-card cho"><h3>Carboidratos</h3><p id="total-cho">0g</p></div>
            <div class="dash-card lip"><h3>Gorduras</h3><p id="total-lip">0g</p></div>
        </div>

        <div class="workspace">
            <!-- Coluna 1: Formulário onde o Nutri digita -->
            <div class="form-section">
                <h2><i class="fa-solid fa-plus-circle"></i> Adicionar Refeição</h2>
                
                <div class="form-group">
                    <label>Nome da Refeição</label>
                    <input type="text" id="meal-name" class="form-control" placeholder="Ex: Café da Manhã, Almoço, Pré-Treino">
                </div>

                <div class="form-group">
                    <label>Horário</label>
                    <input type="text" id="meal-time" class="form-control" placeholder="Ex: 08:00">
                </div>

                <div class="form-group">
                    <label>Alimentos e Quantidades (Uma por linha)</label>
                    <textarea id="meal-foods" class="form-control" rows="5" placeholder="3 Ovos mexidos&#10;1 Fatia de pão integral&#10;100g de Frutas"></textarea>
                </div>

                <div class="macro-inputs">
                    <div class="form-group">
                        <label>Calorias (kcal)</label>
                        <input type="number" id="macro-kcal" class="form-control" value="0">
                    </div>
                    <div class="form-group">
                        <label>Proteínas (g)</label>
                        <input type="number" id="macro-ptn" class="form-control" value="0">
                    </div>
                    <div class="form-group">
                        <label>Carbos (g)</label>
                        <input type="number" id="macro-cho" class="form-control" value="0">
                    </div>
                    <div class="form-group">
                        <label>Gorduras (g)</label>
                        <input type="number" id="macro-lip" class="form-control" value="0">
                    </div>
                </div>

                <button class="btn-add" onclick="addMeal()"><i class="fa-solid fa-check"></i> Inserir na Dieta</button>
            </div>

            <!-- Coluna 2: Visualização da Dieta Ficando Pronta -->
            <div class="meals-section" id="meals-container">
                <!-- As refeições criadas vão aparecer aqui magicamente -->
            </div>

            <!-- Botão de exportação final -->
            <div class="actions-footer">
                <button class="btn-export" onclick="copyFullDiet()"><i class="fa-solid fa-copy"></i> Copiar Dieta Pronta para o WhatsApp</button>
            </div>
        </div>
    </div>

    <script>
        // Array que vai guardar as refeições criadas pelo nutricionista
        let patientDiet = [];

        // Função para adicionar a refeição
        function addMeal() {
            const name = document.getElementById('meal-name').value;
            const time = document.getElementById('meal-time').value;
            const foods = document.getElementById('meal-foods').value;
            const kcal = parseFloat(document.getElementById('macro-kcal').value) || 0;
            const ptn = parseFloat(document.getElementById('macro-ptn').value) || 0;
            const cho = parseFloat(document.getElementById('macro-cho').value) || 0;
            const lip = parseFloat(document.getElementById('macro-lip').value) || 0;

            if(!name || !foods) {
                alert("Por favor, preencha o Nome da refeição e os Alimentos!");
                return;
            }

            // Criando o objeto da refeição
            const newMeal = {
                id: Date.now(),
                name,
                time,
                foods,
                macros: { kcal, ptn, cho, lip }
            };

            patientDiet.push(newMeal);
            updateUI();
            clearForm();
        }

        // Deletar uma refeição criada de forma errada
        function deleteMeal(id) {
            patientDiet = patientDiet.filter(meal => meal.id !== id);
            updateUI();
        }

        // Limpa os campos para digitar a próxima refeição
        function clearForm() {
            document.getElementById('meal-name').value = '';
            document.getElementById('meal-time').value = '';
            document.getElementById('meal-foods').value = '';
            document.getElementById('macro-kcal').value = '0';
            document.getElementById('macro-ptn').value = '0';
            document.getElementById('macro-cho').value = '0';
            document.getElementById('macro-lip').value = '0';
        }

        // Atualiza a tela e os contadores de Macros
        function updateUI() {
            const container = document.getElementById('meals-container');
            container.innerHTML = '';

            let totalKcal = 0, totalPtn = 0, totalCho = 0, totalLip = 0;

            patientDiet.forEach(meal => {
                totalKcal += meal.macros.kcal;
                totalPtn += meal.macros.ptn;
                totalCho += meal.macros.cho;
                totalLip += meal.macros.lip;

                const card = document.createElement('div');
                card.className = 'meal-card';
                card.innerHTML = `
                    <div class="meal-header">
                        <span class="meal-title">${meal.name}</span>
                        <span class="meal-time"><i class="fa-regular fa-clock"></i> ${meal.time || 'Horário flexível'}</span>
                    </div>
                    <div class="food-text">${meal.foods}</div>
                    <div class="meal-footer">
                        <div>
                            <strong>${meal.macros.kcal} kcal</strong> | 
                            P: ${meal.macros.ptn}g | C: ${meal.macros.cho}g | G: ${meal.macros.lip}g
                        </div>
                        <button class="btn-delete" onclick="deleteMeal(${meal.id})"><i class="fa-solid fa-trash"></i></button>
                    </div>
                `;
                container.appendChild(card);
            });

            // Atualiza os cards superiores do dashboard
            document.getElementById('total-kcal').innerText = `${totalKcal} kcal`;
            document.getElementById('total-ptn').innerText = `${totalPtn}g`;
            document.getElementById('total-cho').innerText = `${totalCho}g`;
            document.getElementById('total-lip').innerText = `${totalLip}g`;
        }

        // Copiar o resumo gerado em formato elegante de texto
        function copyFullDiet() {
            if(patientDiet.length === 0) {
                alert("Adicione pelo menos uma refeição antes de copiar!");
                return;
            }

            let text = "📋 *PLANO ALIMENTAR PERSONALIZADO* 📋\n\n";
            
            patientDiet.forEach(meal => {
                text += `⏰ *${meal.time || '--:--'}* - *${meal.name.toUpperCase()}*\n`;
                // Divide as linhas de alimento para colocar um emoji na frente de cada um
                const foodLines = meal.foods.split('\n');
                foodLines.forEach(line => {
                    if(line.trim() !== "") text += `  🔹 ${line.trim()}\n`;
                });
                text += `  _✨ [${meal.macros.kcal} kcal | P: ${meal.macros.ptn}g | C: ${meal.macros.cho}g | G: ${meal.macros.lip}g]_\n\n`;
            });

            text += "💪 *Foco no objetivo! Vamos juntos nessa jornada.*";
            
            navigator.clipboard.writeText(text);
            alert("✨ Perfeito, Nutri! A dieta montada foi copiada com sucesso. É só colar diretamente no WhatsApp do seu paciente.");
        }
    </script>
</body>
</html>
