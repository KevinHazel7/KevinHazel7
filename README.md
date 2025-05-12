<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simulador REcalza - Expansión Estratégica</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 2em; }
    .question { margin-bottom: 2em; }
    .result { font-weight: bold; margin-top: 2em; }
    button { padding: 10px 20px; font-size: 1em; }
  </style>
</head>
<body>
  <h1>Simulador de Decisiones Estratégicas – REcalza</h1>
  <p>Bienvenido/a. Este simulador te guiará a través de decisiones clave en la expansión de REcalza, una marca de calzado ecológico, modular y vegano. Al final obtendrás un perfil estratégico con base en tus elecciones.</p>

  <form id="simForm">
    <div class="question">
      <p><strong>Ciclo 1: ¿A qué ciudad decides expandirte primero?</strong></p>
      <label><input type="radio" name="q1" value="A"> Guadalajara (jóvenes, moda ética, buen ecosistema)</label><br>
      <label><input type="radio" name="q1" value="B"> CDMX (gran mercado, alta competencia, costos altos)</label><br>
      <label><input type="radio" name="q1" value="C"> Mérida (turismo, premium, bajo competencia)</label><br>
      <label><input type="radio" name="q1" value="D"> Puebla (universitaria, logística, eco-alianzas)</label>
    </div>

    <div class="question">
      <p><strong>Ciclo 2: ¿Qué estrategia de entrada al mercado eliges?</strong></p>
      <label><input type="radio" name="q2" value="A"> Tienda física propia</label><br>
      <label><input type="radio" name="q2" value="B"> Showroom temporal</label><br>
      <label><input type="radio" name="q2" value="C"> Solo tienda en línea</label><br>
      <label><input type="radio" name="q2" value="D"> Alianzas con boutiques ecológicas</label>
    </div>

    <div class="question">
      <p><strong>Ciclo 3: ¿Cómo reaccionas a una prohibición de importación de materiales reciclados?</strong></p>
      <label><input type="radio" name="q3" value="A"> Buscar otro proveedor extranjero</label><br>
      <label><input type="radio" name="q3" value="B"> Usar materiales nuevos no reciclados</label><br>
      <label><input type="radio" name="q3" value="C"> Desarrollar proveedor nacional</label><br>
      <label><input type="radio" name="q3" value="D"> Invertir en certificación de materiales</label>
    </div>

    <div class="question">
      <p><strong>Ciclo 4: ¿Qué estrategia de fidelización implementas?</strong></p>
      <label><input type="radio" name="q4" value="A"> Programa de puntos</label><br>
      <label><input type="radio" name="q4" value="B"> Descuento por devolución</label><br>
      <label><input type="radio" name="q4" value="C"> Kits de personalización</label><br>
      <label><input type="radio" name="q4" value="D"> Club de reciclaje con beneficios</label>
    </div>

    <button type="button" onclick="calcularResultado()">Ver resultado estratégico</button>
  </form>

  <div id="resultado" class="result"></div>

  <script>
    function calcularResultado() {
      const respuestas = [
        document.querySelector('input[name="q1"]:checked'),
        document.querySelector('input[name="q2"]:checked'),
        document.querySelector('input[name="q3"]:checked'),
        document.querySelector('input[name="q4"]:checked')
      ];

      if (respuestas.includes(null)) {
        document.getElementById("resultado").innerText = "Por favor responde todas las preguntas.";
        return;
      }

      let scoreConsciente = 0;

      if (respuestas[0].value === "A" || respuestas[0].value === "C" || respuestas[0].value === "D") scoreConsciente++;
      if (respuestas[1].value === "D") scoreConsciente++;
      if (respuestas[2].value === "C" || respuestas[2].value === "D") scoreConsciente++;
      if (respuestas[3].value === "D" || respuestas[3].value === "B") scoreConsciente++;

      let mensaje;
      if (scoreConsciente >= 3) {
        mensaje = "Perfil estratégico: ✳️ Consciente y sostenible. Tus decisiones promueven el impacto positivo, alianzas verdes y crecimiento a largo plazo.";
      } else if (scoreConsciente === 2) {
        mensaje = "Perfil estratégico: ⚖️ Balanceado. Combinas decisiones rentables con visión ecológica. Mantienes coherencia sin sacrificar oportunidades.";
      } else {
        mensaje = "Perfil estratégico: 📈 Comercial agresivo. Priorizas expansión rápida y rentabilidad, pero podrías comprometer los valores sostenibles de la marca.";
      }

      document.getElementById("resultado").innerText = mensaje;
    }
  </script>
</body>
</html>
