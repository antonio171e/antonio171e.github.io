<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cotización y Pedidos - ABC Catering Services</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #2d3a3a;
            color: white;
            text-align: center;
            padding: 20px 0;
        }
        section {
            padding: 20px;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        form input, form select, form textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: #2d3a3a;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #1a2626;
        }
        h2 {
            color: #2d3a3a;
        }
        .quote-summary {
            background-color: #e7f4f4;
            padding: 15px;
            border-radius: 6px;
            margin-top: 20px;
        }
        .quote-summary p {
            margin: 5px 0;
        }
    </style>
</head>
<body>

<header>
    <h1>ABC Catering Services</h1>
    <p>Automatiza tu cotización y pedidos para eventos</p>
</header>

<section>
    <div class="container">
        <h2>Formulario de Solicitud de Cotización</h2>
        <form id="cotizacion-form">
            <label for="nombre">Nombre del Cliente:</label>
            <input type="text" id="nombre" name="nombre" required>

            <label for="email">Correo Electrónico:</label>
            <input type="email" id="email" name="email" required>

            <label for="telefono">Teléfono:</label>
            <input type="tel" id="telefono" name="telefono" required>

            <label for="fecha-evento">Fecha del Evento:</label>
            <input type="date" id="fecha-evento" name="fecha-evento" required>

            <label for="hora-evento">Hora del Evento:</label>
            <input type="time" id="hora-evento" name="hora-evento" required>

            <label for="tipo-evento">Tipo de Evento:</label>
            <select id="tipo-evento" name="tipo-evento" required>
                <option value="boda">Boda</option>
                <option value="fiesta">Fiesta</option>
                <option value="corporativo">Fiesta Corporativa</option>
                <option value="conferencia">Conferencia</option>
            </select>

            <label for="ubicacion">Ubicación del Evento:</label>
            <input type="text" id="ubicacion" name="ubicacion" required>

            <label for="numero-personas">Número de Personas Esperadas:</label>
            <input type="number" id="numero-personas" name="numero-personas" min="1" required>

            <label for="servicios-adicionales">Servicios Adicionales:</label>
            <textarea id="servicios-adicionales" name="servicios-adicionales"></textarea>

            <button type="submit">Generar Cotización</button>
        </form>
    </div>
</section>

<section>
    <div class="container quote-summary" id="quote-summary" style="display: none;">
        <h2>Resumen de la Cotización</h2>
        <p><strong>Cliente:</strong> <span id="summary-nombre"></span></p>
        <p><strong>Fecha del Evento:</strong> <span id="summary-fecha"></span></p>
        <p><strong>Hora del Evento:</strong> <span id="summary-hora"></span></p>
        <p><strong>Tipo de Evento:</strong> <span id="summary-tipo"></span></p>
        <p><strong>Ubicación:</strong> <span id="summary-ubicacion"></span></p>
        <p><strong>Número de Personas:</strong> <span id="summary-personas"></span></p>
        <p><strong>Servicios Adicionales:</strong> <span id="summary-servicios"></span></p>
        <p><strong>Total Cotización:</strong> $<span id="summary-total">0.00</span></p>
    </div>
</section>

<script>
    document.getElementById("cotizacion-form").addEventListener("submit", function(event) {
        event.preventDefault();

        // Obtener los datos del formulario
        const nombre = document.getElementById("nombre").value;
        const email = document.getElementById("email").value;
        const telefono = document.getElementById("telefono").value;
        const fechaEvento = document.getElementById("fecha-evento").value;
        const horaEvento = document.getElementById("hora-evento").value;
        const tipoEvento = document.getElementById("tipo-evento").value;
        const ubicacion = document.getElementById("ubicacion").value;
        const numeroPersonas = document.getElementById("numero-personas").value;
        const serviciosAdicionales = document.getElementById("servicios-adicionales").value;

        // Cálculo de la cotización
        const costoMenuPorPersona = 25.00; // Ejemplo de costo fijo por persona
        const costoAdicional = 500.00; // Ejemplo de costos adicionales fijos
        const descuento = 200.00; // Ejemplo de descuento
        const total = (numeroPersonas * costoMenuPorPersona) + costoAdicional - descuento;

        // Mostrar resumen de cotización
        document.getElementById("summary-nombre").textContent = nombre;
        document.getElementById("summary-fecha").textContent = fechaEvento;
        document.getElementById("summary-hora").textContent = horaEvento;
        document.getElementById("summary-tipo").textContent = tipoEvento;
        document.getElementById("summary-ubicacion").textContent = ubicacion;
        document.getElementById("summary-personas").textContent = numeroPersonas;
        document.getElementById("summary-servicios").textContent = serviciosAdicionales;
        document.getElementById("summary-total").textContent = total.toFixed(2);

        // Mostrar el resumen de la cotización
        document.getElementById("quote-summary").style.display = "block";
    });
</script>

</body>
</html>
