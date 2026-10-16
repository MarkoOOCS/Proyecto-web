<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Gestión Ciudadana - COPACI Granjas Guadalupe</title>
    <style>
        /* Estilos Globales */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f4f6f9;
            color: #333333;
            line-height: 1.6;
        }

        /* Clases de control de visibilidad */
        .oculto {
            display: none !important;
        }

        /* Módulo de Inicio de Sesión (Login) */
        #login-section {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #1e3a8a 0%, #0f172a 100%);
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
        }

        .login-container {
            background: #ffffff;
            padding: 40px;
            border-radius: 12px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            width: 100%;
            max-width: 400px;
        }

        .login-header {
            text-align: center;
            margin-bottom: 25px;
        }

        .login-header h2 {
            color: #1e3a8a;
            font-size: 1.5rem;
            margin-bottom: 5px;
        }

        .login-header p {
            color: #64748b;
            font-size: 0.9rem;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #1e293b;
            font-size: 0.9rem;
        }

        .form-group input, 
        .form-group select {
            width: 100%;
            padding: 12px;
            border: 1px solid #cbd5e1;
            border-radius: 6px;
            font-size: 1rem;
            outline: none;
        }

        .form-group input:focus, 
        .form-group select:focus {
            border-color: #1e3a8a;
        }

        .btn-primary {
            width: 100%;
            padding: 12px;
            background-color: #1e3a8a;
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .btn-primary:hover {
            background-color: #1d4ed8;
        }

        /* Estilos del Encabezado y Navegación Principal */
        header {
            background-color: #1e3a8a;
            color: white;
            padding: 20px 0;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .header-container {
            text-align: center;
            margin-bottom: 15px;
        }

        .header-container h1 {
            font-size: 1.8rem;
        }

        .subtitle {
            font-size: 0.95rem;
            color: #93c5fd;
        }

        nav ul {
            list-style: none;
            display: flex;
            justify-content: center;
            background-color: #1e293b;
            padding: 10px;
            flex-wrap: wrap;
        }

        nav ul li {
            margin: 0 15px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
        }

        nav ul li a:hover {
            color: #60a5fa;
        }

        .logout-link {
            color: #fca5a5 !important;
        }

        /* Contenido Principal y Secciones */
        main {
            max-width: 1200px;
            margin: 30px auto;
            padding: 0 20px;
        }

        .role-panel {
            background: #eff6ff;
            border: 1px dashed #3b82f6;
            padding: 15px;
            border-radius: 6px;
            margin-bottom: 25px;
        }

        .hero-section {
            background: white;
            padding: 40px;
            border-radius: 8px;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            margin-bottom: 30px;
        }

        .hero-section h2 {
            color: #1e3a8a;
            margin-bottom: 15px;
        }

        .btn-action {
            margin-top: 20px;
            padding: 10px 25px;
            background-color: #059669;
            color: white;
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
        }

        .content-section {
            margin-bottom: 40px;
        }

        .content-section h2 {
            margin-bottom: 20px;
            color: #1e293b;
            border-bottom: 2px solid #cbd5e1;
            padding-bottom: 8px;
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .card {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .card h3 {
            color: #1e3a8a;
            margin-bottom: 10px;
        }

        .card p {
            color: #475569;
            font-size: 0.9rem;
            margin-bottom: 15px;
        }

        .btn-card {
            padding: 8px;
            background-color: #2563eb;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
        }

        .sidebar-avisos {
            background: #e2e8f0;
            padding: 25px;
            border-radius: 8px;
            border-left: 5px solid #1e3a8a;
            margin-bottom: 40px;
        }

        .sidebar-avisos h3 {
            color: #1e3a8a;
            margin-bottom: 15px;
        }

        .sidebar-avisos ul {
            list-style-type: disc;
            padding-left: 20px;
        }

        .sidebar-avisos li {
            margin-bottom: 10px;
            color: #334155;
            font-size: 0.95rem;
        }

        /* Pie de Página */
        footer {
            background-color: #0f172a;
            color: #94a3b8;
            text-align: center;
            padding: 20px;
            font-size: 0.85rem;
        }
    </style>
</head>
<body>

    <!-- ========================================== -->
    <!-- MÓDULO 1: SECCIÓN DE INICIO DE SESIÓN      -->
    <!-- ========================================== -->
    <section id="login-section">
        <div class="login-container">
            <div class="login-header">
                <h2>COPACI Granjas Guadalupe</h2>
                <p>Sistema de Gestión Digital Ciudadana</p>
            </div>
            <form id="login-form" onsubmit="handleLogin(event)">
                <div class="form-group">
                    <label for="username">Usuario:</label>
                    <input type="text" id="username" required placeholder="Escriba su usuario">
                </div>
                <div class="form-group">
                    <label for="password">Contraseña:</label>
                    <input type="password" id="password" required placeholder="••••••••">
                </div>
                <div class="form-group">
                    <label for="role-select">Seleccione su Rol de Acceso:</label>
                    <select id="role-select" required>
                        <option value="" disabled selected>-- Elija un perfil --</option>
                        <option value="admin">Administrador del Sistema</option>
                        <option value="copaci">Miembro del COPACI</option>
                        <option value="user">Ciudadano / Usuario Regular</option>
                    </select>
                </div>
                <button type="submit" class="btn-primary">Iniciar Sesión</button>
            </form>
        </div>
    </section>

    <!-- ========================================== -->
    <!-- MÓDULO 2: PLATAFORMA PRINCIPAL DEL SISTEMA -->
    <!-- ========================================== -->
    <div id="main-app">
        
        <!-- Encabezado con etiquetas semánticas -->
        <header>
            <div class="header-container">
                <h1>Sistema de Gestión Ciudadana</h1>
                <p class="subtitle">Consejo de Participación Ciudadana (COPACI) - Granjas Guadalupe</p>
            </div>
            <nav>
                <ul>
                    <li><a href="#inicio">Inicio</a></li>
                    <li><a href="#tramites">Trámites y Servicios</a></li>
                    <li><a href="#avisos">Avisos Vecinales</a></li>
                    <li><a href="#" onclick="logout()" class="logout-link">Cerrar Sesión (<span id="user-role-display"></span>)</a></li>
                </ul>
            </nav>
        </header>

        <!-- Contenido Central -->
        <main>
            <!-- Panel dinámico según el perfil seleccionado -->
            <div id="dynamic-role-box" class="role-panel">
                <h3 id="panel-title">Panel de Control</h3>
                <p id="panel-description">Cargando privilegios del usuario...</p>
            </div>

            <!-- Sección de Bienvenida -->
            <section id="inicio" class="hero-section">
                <h2>Bienvenido al Portal Comunitario</h2>
                <p>Facilitando la gestión de servicios públicos y reportes vecinales para los habitantes de Granjas Guadalupe.</p>
                <button class="btn-action" onclick="location.href='#tramites'">Ver Trámites Disponibles</button>
            </section>

            <!-- Sección de Trámites con Artículos y Tarjetas -->
            <section id="tramites" class="content-section">
                <h2>Trámites y Reportes Disponibles</h2>
                <div class="cards-grid">
                    <article class="card">
                        <h3>Alumbrado Público</h3>
                        <p>Reporta fallas, lámparas fundidas o solicitudes de instalación de nuevas luminarias.</p>
                        <button class="btn-card" onclick="alert('Solicitud de Alumbrado registrada.')">Solicitar</button>
                    </article>
                    <article class="card">
                        <h3>Bacheo y Pavimentación</h3>
                        <p>Envía reportes de baches y daños en la cinta asfáltica para su reparación.</p>
                        <button class="btn-card" onclick="alert('Reporte de bache enviado.')">Solicitar</button>
                    </article>
                    <article class="card">
                        <h3>Recolección de Basura</h3>
                        <p>Consulta horarios de rutas especiales y reporta deficiencias en el servicio.</p>
                        <button class="btn-card" onclick="alert('Consultando rutas...')">Consultar</button>
                    </article>
                    <article class="card">
                        <h3>Seguridad Vecinal</h3>
                        <p>Organiza comités de vigilancia y solicita rondines de patrullaje preventivo.</p>
                        <button class="btn-card" onclick="alert('Módulo de seguridad abierto.')">Gestionar</button>
                    </article>
                </div>
            </section>

            <!-- Panel Lateral de Avisos -->
            <aside class="sidebar-avisos">
                <h3>Avisos Importantes COPACI</h3>
                <ul>
                    <li><strong>Asamblea General:</strong> Próximo domingo a las 10:00 AM en el kiosco principal.</li>
                    <li><strong>Corte de Agua Programado:</strong> Mantenimiento de red el martes de 8:00 a 14:00 hrs.</li>
                    <li><strong>Jornada de Vacunación:</strong> Sábado en la sede del Consejo.</li>
                </ul>
            </aside>
        </main>

        <!-- Pie de página -->
        <footer>
            <p>&copy; 2026 COPACI Granjas Guadalupe. Todos los derechos reservados.</p>
            <p>Programación Construye Apps Web[cite: 1].</p>
        </footer>

    </div>

    <!-- Script de control interactivo optimizado -->
    <script>
        function handleLogin(event) {
            event.preventDefault();
            const roleSelect = document.getElementById('role-select').value;
            let roleName = '';
            let panelTitle = '';
            let panelDesc = '';
            
            if(roleSelect === 'admin') {
                roleName = 'Administrador';
                panelTitle = '⚙️ Panel de Administración General';
                panelDesc = 'Acceso total: Gestión de usuarios, configuración del sistema y supervisión global.';
            } else if(roleSelect === 'copaci') {
                roleName = 'Miembro COPACI';
                panelTitle = '🛡️ Panel de Control - Consejo de Participación Ciudadana';
                panelDesc = 'Acceso operativo: Publicación de avisos urgentes y canalización de peticiones vecinales.';
            } else {
                roleName = 'Ciudadano';
                panelTitle = '👤 Panel Ciudadano / Vecino';
                panelDesc = 'Acceso estándar: Generación de reportes y consulta de servicios en Granjas Guadalupe.';
            }

            // Ocultar login agregando la clase que lo esconde y actualizar textos
            document.getElementById('login-section').classList.add('oculto');
            document.getElementById('user-role-display').innerText = roleName;
            document.getElementById('panel-title').innerText = panelTitle;
            document.getElementById('panel-description').innerText = panelDesc;
        }

        function logout() {
            // Mostrar de nuevo el login quitando la clase y limpiando el formulario
            document.getElementById('login-section').classList.remove('oculto');
            document.getElementById('login-form').reset();
        }
    </script>
</body>
</html>
