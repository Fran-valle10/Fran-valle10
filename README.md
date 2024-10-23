<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Delicias de Pastel</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Bienvenidos a Delicias de Pastel</h1>
        <nav>
            <ul>
                <li><a href="#inicio">Inicio</a></li>
                <li><a href="#menu">Menú</a></li>
                <li><a href="#nosotros">Sobre Nosotros</a></li>
                <li><a href="#contacto">Contacto</a></li>
            </ul>
        </nav>
    </header>

    <section id="inicio" class="hero">
        <h2>Pasteles deliciosos para cada ocasión</h2>
        <p>Descubre nuestros productos frescos y hechos a mano.</p>
    </section>

    <section id="menu">
        <h2>Menú</h2>
        <div class="productos">
            <div class="producto">
                <img src="pastel1.jpg" alt="Pastel de Chocolate">
                <h3>Pastel de Chocolate</h3>
                <p>$30.00</p>
            </div>
            <div class="producto">
                <img src="pastel2.jpg" alt="Pastel de Fresa">
                <h3>Pastel de Fresa</h3>
                <p>$25.00</p>
            </div>
            <!-- Añade más productos aquí -->
        </div>
    </section>

    <section id="nosotros">
        <h2>Sobre Nosotros</h2>
        <p>Somos una pastelería familiar dedicada a crear los mejores pasteles artesanales con ingredientes de alta calidad.</p>
    </section>

    <section id="contacto">
        <h2>Contacto</h2>
        <form action="submit_form.php" method="POST">
            <label for="nombre">Nombre:</label>
            <input type="text" id="nombre" name="nombre" required>
            <label for="email">Correo Electrónico:</label>
            <input type="email" id="email" name="email" required>
            <label for="mensaje">Mensaje:</label>
            <textarea id="mensaje" name="mensaje" required></textarea>
            <button type="submit">Enviar</button>
        </form>
    </section>

    <footer>
        <p>&copy; 2024 Delicias de Pastel. Todos los derechos reservados.</p>
    </footer>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #fdf2e9;
}

header {
    background-color: #ffccbc;
    padding: 20px;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

nav ul li a {
    text-decoration: none;
    color: #333;
    font-weight: bold;
}

.hero {
    background-image: url('pastel-hero.jpg');
    background-size: cover;
    color: white;
    text-align: center;
    padding: 100px 20px;
}

h2 {
    color: #ff7043;
}

.productos {
    display: flex;
    justify-content: space-around;
    margin: 20px;
}

.producto {
    text-align: center;
}

.producto img {
    width: 200px;
    height: 200px;
}

footer {
    background-color: #ffccbc;
    text-align: center;
    padding: 20px;
    margin-top: 20px;
}
<section id="menu">
    <h2>Menú</h2>
    <div class="productos">
        <div class="producto">
            <img src="pastel1.jpg" alt="Pastel de Chocolate">
            <h3>Pastel de Chocolate</h3>
            <p>$30.00</p>
            <button onclick="agregarAlCarrito('Pastel de Chocolate', 30)">Agregar al Carrito</button>
        </div>
        <div class="producto">
            <img src="pastel2.jpg" alt="Pastel de Fresa">
            <h3>Pastel de Fresa</h3>
            <p>$25.00</p>
            <button onclick="agregarAlCarrito('Pastel de Fresa', 25)">Agregar al Carrito</button>
        </div>
        <!-- Añade más productos aquí -->
    </div>
</section>

<!-- Sección del carrito -->
<section id="carrito">
    <h2>Carrito de Compras</h2>
    <ul id="lista-carrito"></ul>
    <p>Total: $<span id="total-carrito">0.00</span></p>
</section>
<script>
    let carrito = [];
    let totalCarrito = 0;

    function agregarAlCarrito(producto, precio) {
        carrito.push({producto, precio});
        actualizarCarrito();
    }

    function actualizarCarrito() {
        const listaCarrito = document.getElementById('lista-carrito');
        const totalCarritoElement = document.getElementById('total-carrito');
        
        // Limpiar lista de carrito
        listaCarrito.innerHTML = '';

        // Mostrar productos en el carrito
        carrito.forEach(item => {
            const li = document.createElement('li');
            li.textContent = `${item.producto} - $${item.precio}`;
            listaCarrito.appendChild(li);
        });

        // Actualizar total
        totalCarrito = carrito.reduce((total, item) => total + item.precio, 0);
        totalCarritoElement.textContent = totalCarrito.toFixed(2);
    }
</scrip/>
<section id="galeria">
    <h2>Galería de Pasteles</h2>
    <div class="galeria">
        <img src="pastel1.jpg" alt="Pastel de Chocolate" onclick="abrirImagen('pastel1.jpg')">
        <img src="pastel2.jpg" alt="Pastel de Fresa" onclick="abrirImagen('pastel2.jpg')">
        <!-- Añadir más imágenes -->
    </div>
</section>

<!-- Modal para mostrar imágenes en grande -->
<div id="modal" class="modal" onclick="cerrarImagen()">
    <span class="cerrar">&times;</span>
    <img class="modal-contenido" id="img-grande">
</div>
.galeria {
    display: flex;
    justify-content: space-around;
    margin: 20px;
}

.galeria img {
    width: 150px;
    height: 150px;
    cursor: pointer;
    transition: transform 0.2s;
}

.galeria img:hover {
    transform: scale(1.1);
}

/* Estilo del modal */
.modal {
    display: none;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.8);
}

.modal-contenido {
    margin: auto;
    display: block;
    max-width: 80%;
}

.cerrar {
    position: absolute;
    top: 10px;
    right: 25px;
    color: white;
    font-size: 35px;
    cursor: pointer;
}
<script>
    function abrirImagen(src) {
        const modal = document.getElementById('modal');
        const imgGrande = document.getElementById('img-grande');
        modal.style.display = 'block';
        imgGrande.src = src;
    }

    function cerrarImagen() {
        document.getElementById('modal').style.display = 'none';
    }
</script>
