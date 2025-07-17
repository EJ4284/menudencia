# vida
Pagina de alimentacion y ejercicios beta
<div class="imc-calculator">
  <h2>Calculadora de IMC + Plan Nutricional Completo</h2>
  <form id="imc-form">
    <div class="form-group">
      <label for="weight">Peso (kg):</label>
      <input type="number" id="weight" step="0.1" min="20" max="300" required>
    </div>
    <div class="form-group">
      <label for="height">Altura (cm):</label>
      <input type="number" id="height" min="100" max="250" required>
    </div>
    <button type="submit">Calcular IMC y obtener plan nutricional</button>
  </form>
  <div id="imc-result" class="result-container" style="display: none;">
    <h3>Resultado:</h3>
    <p>Tu IMC es: <span id="imc-value">0</span></p>
    <p>Clasificación: <span id="imc-classification">-</span></p>
    <div id="imc-scale" class="scale">
      <div class="scale-labels">
        <span>Bajo peso</span>
        <span>Normal</span>
        <span>Sobrepeso</span>
        <span>Obesidad</span>
      </div>
      <div class="scale-bar">
        <div class="indicator" id="imc-indicator"></div>
      </div>
      <div class="scale-numbers">
        <span>18.5</span>
        <span>25</span>
        <span>30</span>
      </div>
    </div>
    
    <div class="nutrition-recommendations">
      <div class="nutrition-tabs">
        <button class="tab-btn active" data-tab="breakfast">Desayunos</button>
        <button class="tab-btn" data-tab="lunch">Almuerzos</button>
        <button class="tab-btn" data-tab="dinner">Cenas</button>
      </div>
      
      <div id="breakfast" class="tab-content active">
        <h3><i class="icon">🍳</i> Recomendaciones de Desayuno</h3>
        <div id="breakfast-content" class="recommendation-content"></div>
      </div>
      
      <div id="lunch" class="tab-content">
        <h3><i class="icon">🍲</i> Recomendaciones de Almuerzo</h3>
        <div id="lunch-content" class="recommendation-content"></div>
      </div>
      
      <div id="dinner" class="tab-content">
        <h3><i class="icon">🥗</i> Recomendaciones de Cena</h3>
        <div id="dinner-content" class="recommendation-content"></div>
      </div>
    </div>
  </div>
</div>

<style>
  .imc-calculator {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    max-width: 600px;
    margin: 30px auto;
    padding: 25px;
    border-radius: 12px;
    background: linear-gradient(135deg, #f9f9f9 0%, #eef2f5 100%);
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    border: 1px solid #e0e0e0;
  }
  
  h2 {
    color: #2c3e50;
    text-align: center;
    margin-bottom: 25px;
    font-size: 24px;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    margin-bottom: 8px;
    font-weight: 600;
    color: #34495e;
  }
  
  input {
    width: 100%;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 6px;
    box-sizing: border-box;
    font-size: 16px;
    transition: border 0.3s;
  }
  
  input:focus {
    border-color: #4CAF50;
    outline: none;
    box-shadow: 0 0 0 2px rgba(76, 175, 80, 0.2);
  }
  
  button[type="submit"] {
    background: linear-gradient(to right, #4CAF50, #2E8B57);
    color: white;
    padding: 14px 20px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-size: 16px;
    width: 100%;
    transition: all 0.3s;
    font-weight: 600;
    margin-top: 10px;
  }
  
  button[type="submit"]:hover {
    background: linear-gradient(to right, #45a049, #267445);
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
  
  .result-container {
    margin-top: 30px;
    padding: 25px;
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    animation: fadeIn 0.5s ease-out;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  .scale {
    margin-top: 25px;
  }
  
  .scale-labels {
    display: flex;
    justify-content: space-between;
    font-size: 13px;
    margin-bottom: 8px;
    color: #555;
    font-weight: 500;
  }
  
  .scale-bar {
    height: 22px;
    background: linear-gradient(to right, #3498db, #2ecc71, #f39c12, #e74c3c);
    border-radius: 11px;
    position: relative;
    margin-bottom: 8px;
    overflow: hidden;
  }
  
  .indicator {
    position: absolute;
    top: -6px;
    width: 12px;
    height: 34px;
    background-color: #2c3e50;
    transform: translateX(-6px);
    border-radius: 3px;
    z-index: 2;
    box-shadow: 0 0 5px rgba(0,0,0,0.2);
  }
  
  .scale-numbers {
    display: flex;
    justify-content: space-between;
    font-size: 13px;
    margin-top: 5px;
    color: #555;
  }
  
  #imc-value {
    font-weight: bold;
    font-size: 22px;
    color: #2c3e50;
  }
  
  #imc-classification {
    font-weight: bold;
    text-transform: capitalize;
    color: #2c3e50;
    font-size: 18px;
  }
  
  .nutrition-recommendations {
    margin-top: 30px;
  }
  
  .nutrition-tabs {
    display: flex;
    border-bottom: 2px solid #e0e0e0;
    margin-bottom: 20px;
  }
  
  .tab-btn {
    padding: 12px 20px;
    background: none;
    border: none;
    cursor: pointer;
    font-size: 15px;
    font-weight: 600;
    color: #7f8c8d;
    position: relative;
    transition: all 0.3s;
  }
  
  .tab-btn.active {
    color: #2c3e50;
  }
  
  .tab-btn.active:after {
    content: '';
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 100%;
    height: 3px;
    background: linear-gradient(to right, #4CAF50, #2E8B57);
    border-radius: 3px 3px 0 0;
  }
  
  .tab-btn:hover:not(.active) {
    color: #4CAF50;
    background-color: #f5f5f5;
  }
  
  .tab-content {
    display: none;
    animation: fadeIn 0.5s ease-out;
  }
  
  .tab-content.active {
    display: block;
  }
  
  .recommendation-content {
    background-color: #f8f9fa;
    border-radius: 8px;
    padding: 20px;
    margin-top: 15px;
  }
  
  .recommendation-content h4 {
    color: #2c3e50;
    margin-top: 0;
    margin-bottom: 15px;
    font-size: 18px;
    border-bottom: 1px solid #e0e0e0;
    padding-bottom: 10px;
  }
  
  .recommendation-content ul {
    padding-left: 20px;
    margin-bottom: 0;
  }
  
  .recommendation-content li {
    margin-bottom: 12px;
    line-height: 1.5;
    color: #34495e;
  }
  
  .recommendation-content strong {
    color: #2c3e50;
  }
  
  .icon {
    margin-right: 10px;
  }
  
  .general-tips {
    background-color: #e8f4f8;
    border-left: 4px solid #3498db;
    padding: 15px;
    margin-top: 20px;
    border-radius: 0 6px 6px 0;
  }
  
  .general-tips h4 {
    margin-top: 0;
    color: #2c3e50;
  }
  
  .general-tips p {
    margin-bottom: 0;
    color: #34495e;
  }
  
  @media (max-width: 600px) {
    .imc-calculator {
      padding: 15px;
      margin: 15px;
    }
    
    .nutrition-tabs {
      flex-wrap: wrap;
    }
    
    .tab-btn {
      flex: 1;
      min-width: 100px;
      padding: 10px 5px;
      font-size: 14px;
    }
  }
</style>

<script>
  document.getElementById('imc-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const weight = parseFloat(document.getElementById('weight').value);
    const height = parseInt(document.getElementById('height').value) / 100;
    
    if (weight && height) {
      const imc = weight / (height * height);
      const roundedImc = Math.round(imc * 10) / 10;
      
      document.getElementById('imc-value').textContent = roundedImc;
      
      let classification = '';
      let indicatorPosition = 0;
      let breakfastRec = '';
      let lunchRec = '';
      let dinnerRec = '';
      
      if (imc < 18.5) {
        classification = 'Bajo peso';
        indicatorPosition = (imc / 18.5) * 25;
        
        // Desayunos
        breakfastRec = `
          <h4>Para aumentar energía y nutrientes</h4>
          <ul>
            <li><strong>Avena hipercalórica:</strong> Avena cocida con leche entera, miel, nueces, almendras y trozos de plátano</li>
            <li><strong>Tostadas integrales con aguacate y huevo:</strong> Pan integral con aguacate machacado, huevos revueltos y queso fresco</li>
            <li><strong>Batido energético:</strong> Leche entera, plátano, mantequilla de maní, avena y miel</li>
            <li><strong>Yogur griego con granola:</strong> Yogur griego natural con granola casera, miel y frutas frescas</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Incluye siempre proteínas y grasas saludables en cada desayuno. Añade frutos secos y semillas para aumentar calorías saludables.</p>
          </div>
        `;
        
        // Almuerzos
        lunchRec = `
          <h4>Almuerzos nutritivos y calóricos</h4>
          <ul>
            <li><strong>Pasta integral con atún:</strong> Pasta integral con atún al natural, aceite de oliva, tomate cherry y espinacas</li>
            <li><strong>Arroz con pollo y aguacate:</strong> Arroz integral con pechuga de pollo a la plancha, aguacate y vegetales salteados</li>
            <li><strong>Ensalada de quinoa:</strong> Quinoa con garbanzos, aguacate, tomate, pepino y aderezo de tahini</li>
            <li><strong>Crema de legumbres:</strong> Crema de lentejas o garbanzos con patata y trozos de jamón serrano</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Incluye carbohidratos complejos en cada comida junto con proteínas de calidad. Añade grasas saludables como aceite de oliva o aguacate.</p>
          </div>
        `;
        
        // Cenas
        dinnerRec = `
          <h4>Cenas nutritivas y fáciles de digerir</h4>
          <ul>
            <li><strong>Salmon al horno:</strong> Salmón con patatas asadas y brócoli al vapor</li>
            <li><strong>Tortilla española:</strong> Tortilla de patata con cebolla y pan integral</li>
            <li><strong>Sándwich nutritivo:</strong> Pan integral con pechuga de pavo, queso y aguacate</li>
            <li><strong>Crema de calabaza:</strong> Con trozos de pollo y semillas de calabaza</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Incluye proteínas en cada cena. Puedes añadir carbohidratos complejos para aumentar las calorías. Evita acostarte inmediatamente después de cenar.</p>
          </div>
        `;
        
      } else if (imc < 25) {
        classification = 'Peso normal';
        indicatorPosition = 25 + ((imc - 18.5) / (25 - 18.5)) * 25;
        
        // Desayunos
        breakfastRec = `
          <h4>Para mantener tu peso saludable</h4>
          <ul>
            <li><strong>Bowl de yogur y frutas:</strong> Yogur natural con fresas, arándanos, semillas de chía y granola</li>
            <li><strong>Tortilla de espinacas:</strong> Tortilla de 2 huevos con espinacas frescas, tomate y pan integral</li>
            <li><strong>Smoothie verde:</strong> Espinaca, plátano, leche de almendras y mantequilla de maní</li>
            <li><strong>Tostadas con hummus:</strong> Pan integral con hummus casero, pepino y tomate</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Mantén una variedad de alimentos en tus desayunos. Incluye proteínas, carbohidratos complejos y grasas saludables.</p>
          </div>
        `;
        
        // Almuerzos
        lunchRec = `
          <h4>Almuerzos equilibrados</h4>
          <ul>
            <li><strong>Ensalada completa:</strong> Lechuga, quinoa, pollo a la plancha, aguacate y nueces</li>
            <li><strong>Pescado al horno:</strong> Merluza o salmón con arroz integral y vegetales al vapor</li>
            <li><strong>Wraps integrales:</strong> Tortillas integrales con pavo, vegetales frescos y guacamole</li>
            <li><strong>Lentejas vegetales:</strong> Con zanahoria, calabaza y acompañadas de arroz</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>La mitad de tu plato deberían ser vegetales, un cuarto proteínas magras y otro cuarto carbohidratos complejos. Varía tus fuentes de proteína.</p>
          </div>
        `;
        
        // Cenas
        dinnerRec = `
          <h4>Cenas ligeras pero nutritivas</h4>
          <ul>
            <li><strong>Crema de verduras:</strong> Calabaza, zanahoria o brócoli con trozos de pavo</li>
            <li><strong>Revuelto de setas:</strong> Huevo con champiñones y espárragos trigueros</li>
            <li><strong>Ensalada caprese:</strong> Mozzarella fresca, tomate y albahaca con un chorrito de aceite</li>
            <li><strong>Salmón a la plancha:</strong> Con espárragos y puré de coliflor</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Las cenas deben ser más ligeras que el almuerzo pero igualmente nutritivas. Incluye proteínas y vegetales. Limita los carbohidratos por la noche.</p>
          </div>
        `;
        
      } else if (imc < 30) {
        classification = 'Sobrepeso';
        indicatorPosition = 50 + ((imc - 25) / (30 - 25)) * 25;
        
        // Desayunos
        breakfastRec = `
          <h4>Para controlar el peso</h4>
          <ul>
            <li><strong>Huevos pochados con espárragos:</strong> 1-2 huevos sobre espárragos salteados con aguacate</li>
            <li><strong>Porridge de chía:</strong> Semillas de chía remojadas en leche desnatada con canela y frutos rojos</li>
            <li><strong>Tostada integral con queso cottage:</strong> Pan integral con queso cottage, tomate y pimienta</li>
            <li><strong>Smoothie de proteína:</strong> Leche desnatada, proteína en polvo sin azúcar y 1/2 plátano</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Controla las porciones y prioriza proteínas y fibra para mantenerte saciado. Limita los azúcares añadidos.</p>
          </div>
        `;
        
        // Almuerzos
        lunchRec = `
          <h4>Almuerzos saciantes bajos en calorías</h4>
          <ul>
            <li><strong>Ensalada de garbanzos:</strong> Garbanzos con pepino, tomate, cebolla morada y vinagreta de limón</li>
            <li><strong>Pollo al curry light:</strong> Pechuga de pollo con curry light, leche de coco light y vegetales</li>
            <li><strong>Merluza en salsa verde:</strong> Con espárragos y guisantes</li>
            <li><strong>Calabacines rellenos:</strong> Calabacín relleno de carne magra picada y quinoa</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Llena la mitad del plato con vegetales sin almidón. Elige métodos de cocción como horno, plancha o vapor en lugar de fritos.</p>
          </div>
        `;
        
        // Cenas
        dinnerRec = `
          <h4>Cenas ligeras y proteicas</h4>
          <ul>
            <li><strong>Sopa de miso con tofu:</strong> Sopa japonesa ligera con tofu y algas</li>
            <li><strong>Tortilla de claras:</strong> Con espinacas y champiñones</li>
            <li><strong>Ensalada de atún:</strong> Lechuga, atún al natural, huevo duro y pepino</li>
            <li><strong>Pescado blanco al horno:</strong> Con pimentón y limón, acompañado de brócoli</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Las cenas deben ser las comidas más ligeras del día. Incluye proteínas magras y vegetales. Evita carbohidratos refinados por la noche.</p>
          </div>
        `;
        
      } else {
        classification = 'Obesidad';
        indicatorPosition = 75 + ((Math.min(imc, 40) - 30) / (40 - 30)) * 25;
        
        // Desayunos
        breakfastRec = `
          <h4>Para comenzar el día de forma saludable</h4>
          <ul>
            <li><strong>Revuelto de claras:</strong> 3 claras de huevo con espinacas, champiñones y tomate cherry</li>
            <li><strong>Yogur desnatado con semillas:</strong> Yogur griego 0% con semillas de linaza y 5 almendras</li>
            <li><strong>Tortilla de avena:</strong> Avena molida mezclada con claras de huevo y canela</li>
            <li><strong>Pan integral con pavo:</strong> 1 rebanada de pan integral con pechuga de pavo y té verde</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Enfócate en proteínas magras y fibra para controlar el apetito. Evita jugos y azúcares añadidos. Bebe agua en lugar de bebidas calóricas.</p>
          </div>
        `;
        
        // Almuerzos
        lunchRec = `
          <h4>Almuerzos saludables para control de peso</h4>
          <ul>
            <li><strong>Ensalada de lentejas:</strong> Lentejas con zanahoria, apio y vinagreta de mostaza</li>
            <li><strong>Pechuga a la plancha:</strong> Con puré de coliflor y ensalada verde</li>
            <li><strong>Crema de calabacín:</strong> Sin patata, con trozos de pollo desmenuzado</li>
            <li><strong>Merluza al vapor:</strong> Con espárragos y brócoli</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Controla las porciones. Usa platos más pequeños. Mastica lentamente. Prioriza vegetales sin almidón y proteínas magras.</p>
          </div>
        `;
        
        // Cenas
        dinnerRec = `
          <h4>Cenas muy ligeras y nutritivas</h4>
          <ul>
            <li><strong>Sopa de verduras:</strong> Con trozos de pavo o pollo</li>
            <li><strong>Ensalada de atún:</strong> Lechuga, atún al natural, pepino y vinagre</li>
            <li><strong>Omelette de claras:</strong> Con espinacas y tomate</li>
            <li><strong>Pescado blanco al papillote:</strong> Con limón y especias, acompañado de espárragos</li>
          </ul>
          <div class="general-tips">
            <h4>Consejos generales:</h4>
            <p>Cena temprano (antes de las 8pm). Evita carbohidratos por la noche. Las cenas deben ser las comidas más ligeras del día.</p>
          </div>
        `;
      }
      
      document.getElementById('imc-classification').textContent = classification;
      document.getElementById('imc-indicator').style.left = `${Math.min(100, Math.max(0, indicatorPosition))}%`;
      document.getElementById('breakfast-content').innerHTML = breakfastRec;
      document.getElementById('lunch-content').innerHTML = lunchRec;
      document.getElementById('dinner-content').innerHTML = dinnerRec;
      
      document.getElementById('imc-result').style.display = 'block';
      
      // Activar pestañas
      const tabBtns = document.querySelectorAll('.tab-btn');
      const tabContents = document.querySelectorAll('.tab-content');
      
      tabBtns.forEach(btn => {
        btn.addEventListener('click', () => {
          tabBtns.forEach(b => b.classList.remove('active'));
          tabContents.forEach(c => c.classList.remove('active'));
          
          btn.classList.add('active');
          document.getElementById(btn.dataset.tab).classList.add('active');
        });
      });
    }
  });
</script>
