<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>W.I.N - World Information Network</title>
  
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css" rel="stylesheet">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700;800;900&display=swap" rel="stylesheet">

  <style>
    /* VARIABLES MANUAL DE MARCA W.I.N */
    :root {
      --color-marfil: #F5F1E8;
      --color-carbon: #1F1F1B;
      --color-azul-tinta: #1D3557;
      --color-rosa-maquilishuat: #FFC0CB;
      --font-mont: 'Montserrat', sans-serif;
    }

    body {
      background-color: var(--color-marfil);
      color: var(--color-carbon);
      font-family: var(--font-mont);
      overflow-x: hidden;
      position: relative;
    }

    #lavaCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      z-index: -1;
      pointer-events: none;
      opacity: 0.85;
    }

    h1, h2, h3, h4, h5, h6, .fw-bold {
      font-weight: 700;
    }

    .brand-header {
      background: rgba(245, 241, 232, 0.45);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-bottom: 2px solid var(--color-carbon);
    }
    .brand-title {
      font-weight: 900;
      letter-spacing: 8px;
      color: var(--color-carbon);
      font-size: 3rem;
    }
    .brand-slogan {
      font-size: 0.88rem;
      letter-spacing: 2px;
      color: var(--color-carbon);
      border-top: 1.5px solid var(--color-carbon);
      display: inline-block;
      padding-top: 2px;
      font-weight: 700;
    }

    .glass-header-nav {
      position: sticky;
      top: 10px;
      z-index: 1000;
      width: 95%;
      max-width: 1300px;
      margin: 0 auto 20px auto;
      background: rgba(29, 53, 87, 0.82) !important;
      backdrop-filter: blur(16px) saturate(180%);
      -webkit-backdrop-filter: blur(16px) saturate(180%);
      border: 1px solid rgba(255, 255, 255, 0.25);
      border-radius: 50px;
      box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
      padding: 4px 18px;
    }

    .navbar-win .nav-link {
      color: var(--color-marfil) !important;
      font-weight: 700;
      text-transform: uppercase;
      font-size: 0.8rem;
      letter-spacing: 0.5px;
      padding: 6px 12px !important;
      transition: all 0.3s ease;
      cursor: pointer;
    }

    .navbar-win .nav-link:hover, 
    .navbar-win .nav-link.active,
    .navbar-win .show > .nav-link {
      color: var(--color-carbon) !important;
      background-color: var(--color-rosa-maquilishuat);
      border-radius: 20px;
    }

    .dropdown-menu-win {
      background: rgba(31, 31, 27, 0.92) !important;
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid var(--color-rosa-maquilishuat);
      border-radius: 12px;
      padding: 8px 0;
      box-shadow: 0 10px 30px rgba(0,0,0,0.5);
    }
    .dropdown-menu-win .dropdown-item {
      color: var(--color-marfil) !important;
      font-size: 0.82rem;
      font-weight: 600;
      padding: 7px 18px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .dropdown-menu-win .dropdown-item:hover {
      background-color: var(--color-rosa-maquilishuat);
      color: var(--color-carbon) !important;
    }

    .hero-3d-wrapper {
      position: relative;
      height: 380px;
      perspective: 1000px;
      overflow: hidden;
      background: linear-gradient(135deg, rgba(255,192,203,0.3) 0%, rgba(29,53,87,0.1) 100%);
      border-bottom: 2px solid var(--color-carbon);
      border-top: 2px solid var(--color-carbon);
    }
    .layer-container {
      position: absolute;
      width: 100%;
      height: 100%;
      transform-style: preserve-3d;
      transition: transform 0.1s ease-out;
    }
    .layer {
      position: absolute;
      top: 0; left: 0; width: 100%; height: 100%;
      display: flex; align-items: center; justify-content: center;
      pointer-events: none;
    }
    .layer-bg-grid {
      background-image: radial-gradient(var(--color-azul-tinta) 1.5px, transparent 1.5px);
      background-size: 26px 26px;
      opacity: 0.2;
      transform: translateZ(-80px) scale(1.2);
    }
    .layer-text-front {
      transform: translateZ(60px);
      text-shadow: 0px 8px 15px rgba(0,0,0,0.15);
    }
    .badge-maquilishuat {
      background-color: var(--color-rosa-maquilishuat);
      color: var(--color-carbon);
      font-weight: 800;
      letter-spacing: 0.5px;
      border: 1px solid var(--color-carbon);
    }

    .card-win {
      background-color: #FFFFFF;
      border: 2px solid var(--color-carbon);
      border-radius: 0;
      transition: all 0.3s cubic-bezier(0.165, 0.84, 0.44, 1);
      box-shadow: 4px 4px 0px var(--color-carbon);
    }
    .card-win:hover {
      transform: translateY(-6px) translateX(-2px);
      box-shadow: 8px 8px 0px var(--color-azul-tinta);
    }
    .card-img-wrapper {
      position: relative;
      overflow: hidden;
      border-bottom: 2px solid var(--color-carbon);
      height: 200px;
    }
    .card-img-wrapper img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.4s ease;
    }
    .card-win:hover .card-img-wrapper img {
      transform: scale(1.06);
    }

    .btn-win-primary {
      background-color: var(--color-azul-tinta);
      color: var(--color-marfil);
      border-radius: 0;
      border: 1px solid var(--color-carbon);
      font-weight: 700;
      padding: 8px 16px;
      transition: all 0.2s ease;
    }
    .btn-win-primary:hover {
      background-color: var(--color-rosa-maquilishuat);
      color: var(--color-carbon);
    }
    .btn-win-accent {
      background-color: var(--color-rosa-maquilishuat);
      color: var(--color-carbon);
      border-radius: 0;
      border: 1px solid var(--color-carbon);
      font-weight: 800;
      padding: 6px 14px;
      font-size: 0.85rem;
    }
    .btn-win-accent:hover {
      background-color: var(--color-azul-tinta);
      color: #FFFFFF;
    }

    .screen-view {
      display: none;
    }
    .screen-view.active {
      display: block;
      animation: fadeInUp 0.4s ease-out;
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(12px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .table-win {
      border: 2px solid var(--color-carbon);
    }
    .table-win th {
      background-color: var(--color-azul-tinta);
      color: var(--color-marfil);
      padding: 10px;
    }

    .multimedia-box {
      border: 2px dashed var(--color-azul-tinta);
      background-color: rgba(255,255,255,0.9);
      padding: 20px;
      margin-bottom: 25px;
    }

    .article-img {
      width: 100%;
      max-height: 420px;
      object-fit: cover;
      border: 2px solid var(--color-carbon);
      margin-bottom: 25px;
    }

    footer {
      background-color: var(--color-carbon);
      color: var(--color-marfil);
      border-top: 5px solid var(--color-rosa-maquilishuat);
    }
  </style>
</head>
<body>

  <canvas id="lavaCanvas"></canvas>

  <header class="brand-header text-center py-3">
    <div class="container">
      <div class="row align-items-center">
        <div class="col-md-3 text-center text-md-start mb-2 mb-md-0"></div>
        <div class="col-md-6 text-center">
          <h1 class="brand-title mb-0">W. I. N</h1>
          <div class="brand-slogan">DONDE LA TRADICIÓN, INFORMA AL PRESENTE</div>
        </div>
        <div class="col-md-3 text-center text-md-end mt-2 mt-md-0">
          <button class="btn btn-win-accent shadow-sm" onclick="navigateTo('view-auth')" id="navAuthBtn">
            <i class="bi bi-person-circle"></i> Iniciar Sesión
          </button>
        </div>
      </div>
    </div>
  </header>

  <nav class="navbar navbar-expand-lg navbar-win glass-header-nav">
    <div class="container-fluid p-0">
      <a class="navbar-brand text-white fw-bold d-lg-none ps-3 fs-6" onclick="navigateTo('view-home')">W.I.N DIGITAL</a>
      <button class="navbar-toggler text-white border-0 me-2" type="button" data-bs-toggle="collapse" data-bs-target="#navWIN">
        <i class="bi bi-list fs-2 text-white"></i>
      </button>
      
      <div class="collapse navbar-collapse justify-content-center" id="navWIN">
        <ul class="navbar-nav align-items-center">
          <li class="nav-item"><a class="nav-link nav-btn active" onclick="navigateTo('view-home', this)">Inicio</a></li>
          
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">Deportes</a>
            <ul class="dropdown-menu dropdown-menu-win">
              <li><a class="dropdown-item" onclick="filterBySub('Balón en Juego')">⚽ Balón en Juego</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Bajo el Aro')">🏀 Bajo el Aro</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('A Fondo')">🏎️ A Fondo</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Cinco Aros')">🥇 Cinco Aros</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Modo Gamer')">🎮 Modo Gamer</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Cara a Cara')">🎙️ Cara a Cara</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Números del Juego')">📊 Números del Juego</a></li>
            </ul>
          </li>

          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">Economía</a>
            <ul class="dropdown-menu dropdown-menu-win">
              <li><a class="dropdown-item" onclick="filterBySub('Casa Adentro')">🏠 Casa Adentro</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Fuera de Fronteras')">🌐 Fuera de Fronteras</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('De Cero a Marca')">🚀 De Cero a Marca</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Jugadas de Negocio')">💼 Jugadas de Negocio</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Sembrando Capital')">🌱 Sembrando Capital</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('El Tablero')">📈 El Tablero</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Chamba Hoy')">🛠️ Chamba Hoy</a></li>
            </ul>
          </li>

          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">Cultura</a>
            <ul class="dropdown-menu dropdown-menu-win">
              <li><a class="dropdown-item" onclick="filterBySub('Trazo Libre')">🎨 Trazo Libre</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Entre Líneas')">📚 Entre Líneas</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Memoria Viva')">🏛️ Memoria Viva</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Sonido Propio')">🎵 Sonido Propio</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('A la Mesa')">🍽️ A la Mesa</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('En Vitrina')">🖼️ En Vitrina</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('De Generación en Generación')">🤝 De Generación en Generación</a></li>
            </ul>
          </li>

          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">Entretenimiento</a>
            <ul class="dropdown-menu dropdown-menu-win">
              <li><a class="dropdown-item" onclick="filterBySub('Luces, Cámara')">🎬 Luces, Cámara</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Play Directo')">📺 Play Directo</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('En Repeat')">🎧 En Repeat</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Bajo los Reflectores')">🌟 Bajo los Reflectores</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Nivel Up')">👾 Nivel Up</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('En Vivo')">🎤 En Vivo</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Lo Que se Viene')">🔮 Lo Que se Viene</a></li>
            </ul>
          </li>

          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">Salud</a>
            <ul class="dropdown-menu dropdown-menu-win">
              <li><a class="dropdown-item" onclick="filterBySub('Diagnóstico Claro')">🩺 Diagnóstico Claro</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Buena Vibra')">✨ Buena Vibra</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Mente en Paz')">🧠 Mente en Paz</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Plato Consciente')">🥗 Plato Consciente</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('Antes que Después')">🛡️ Antes que Después</a></li>
              <li><a class="dropdown-item" onclick="filterBySub('La Salud del Futuro')">🔬 La Salud del Futuro</a></li>
            </ul>
          </li>

          <li class="nav-item"><a class="nav-link nav-btn" onclick="navigateTo('view-multimedia', this)">Multimedia</a></li>
          <li class="nav-item"><a class="nav-link nav-btn" onclick="navigateTo('view-about', this)">Editorial</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <div id="view-home" class="screen-view active">
    <div class="hero-3d-wrapper" id="heroParallax">
      <div class="layer-container" id="layerContainer">
        <div class="layer layer-bg-grid"></div>
        <div class="layer layer-text-front text-center">
          <div>
            <span class="badge badge-maquilishuat px-3 py-2 mb-2">PERIODISMO DIGITAL ESPECIALIZADO</span>
            <h2 class="display-3 fw-bold" style="color: var(--color-azul-tinta);">World Information Network</h2>
          </div>
        </div>
      </div>
    </div>

    <div class="container my-5">
      <div class="d-flex justify-content-between align-items-center mb-4 border-bottom border-dark pb-2">
        <h3 class="fw-bold m-0" style="color: var(--color-azul-tinta);"><i class="bi bi-newspaper"></i> Edición Principal</h3>
        <span class="badge bg-dark text-white p-2" id="artCountBadge">Cargando...</span>
      </div>

      <div class="row g-4" id="newsGrid"></div>
    </div>
  </div>

  <div id="view-section" class="screen-view">
    <div class="container my-5">
      <button class="btn btn-outline-dark btn-sm mb-4 fw-bold" onclick="navigateTo('view-home')">
        <i class="bi bi-arrow-left"></i> Volver al Inicio
      </button>
      <h2 id="sectionTitle" class="display-5 fw-bold border-bottom border-dark pb-3 mb-4" style="color: var(--color-azul-tinta);">
        Categoría
      </h2>
      <div class="row g-4" id="sectionNewsGrid"></div>
    </div>
  </div>

  <div id="view-article" class="screen-view">
    <div class="container my-5">
      <button class="btn btn-outline-dark btn-sm mb-4 fw-bold" onclick="goBackToPrevious()">
        <i class="bi bi-arrow-left"></i> Regresar
      </button>
      <div class="row justify-content-center">
        <div class="col-lg-9 bg-white p-4 p-md-5 border border-dark shadow-sm">
          <div class="d-flex gap-2 mb-2">
            <span id="artCategory" class="badge badge-maquilishuat">Categoría</span>
            <span id="artSubCategory" class="badge bg-dark text-white">Subsección</span>
          </div>
          <h1 id="artTitle" class="fw-bold mb-3" style="color: var(--color-azul-tinta);">Título de la Noticia</h1>
          <div class="text-muted small mb-4 pb-2 border-bottom">
            Por <strong id="artAuthor">Autor</strong> | Publicado: <span id="artDate">Fecha</span> | <span id="artLocation">Lugar</span>
          </div>

          <div id="artContent" class="fs-5 lh-lg mb-4"></div>

          <div class="border-top pt-3 mb-4 text-muted small">
            <strong>Fuente principal:</strong> <span id="artSource">Fuente</span>
          </div>

          <hr class="my-5">
          <h4 class="fw-bold mb-3"><i class="bi bi-chat-dots-fill"></i> Comentarios de Lectores</h4>
          <div id="commentsList" class="mb-4"></div>

          <form id="commentForm" onsubmit="saveComment(event)">
            <div class="mb-3">
              <input type="text" id="commentUser" class="form-control rounded-0 border-dark" placeholder="Tu Nombre Completo" required>
            </div>
            <div class="mb-3">
              <textarea id="commentText" class="form-control rounded-0 border-dark" rows="3" placeholder="Escribe tu opinión objetiva..." required></textarea>
            </div>
            <button type="submit" class="btn btn-win-primary">Publicar Comentario</button>
          </form>
        </div>
      </div>
    </div>
  </div>

  <div id="view-multimedia" class="screen-view">
    <div class="container my-5">
      <button class="btn btn-outline-dark btn-sm mb-4 fw-bold" onclick="navigateTo('view-home')">
        <i class="bi bi-arrow-left"></i> Regresar al Inicio
      </button>

      <h2 class="display-5 fw-bold border-bottom border-dark pb-3 mb-4" style="color: var(--color-azul-tinta);">
        Producto Multimedial Audiovisual
      </h2>

      <div class="multimedia-box">
        <div class="row align-items-center">
          <div class="col-md-6">
            <div class="ratio ratio-16x9 border border-dark">
              <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ" title="Video Reportaje Especial W.I.N" allowfullscreen></iframe>
            </div>
          </div>
          <div class="col-md-6 mt-3 mt-md-0">
            <span class="badge badge-maquilishuat">FORMATO: VIDEO REPORTAJE ESPECIAL</span>
            <h3 class="fw-bold mt-2">Reportaje: Transformación Financiera Digital</h3>
            <p><strong>Sección Vinculada:</strong> Economía (De Cero a Marca)</p>
            <p><strong>Justificación del formato y tema:</strong> Se seleccionó el formato de vídeo dinámico para llegar de forma ágil y atractiva a nuestra audiencia joven en smartphones, explicando visualmente el impacto del emprendimiento y los modelos financieros digitales en El Salvador.</p>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div id="view-auth" class="screen-view">
    <div class="container my-5">
      <button class="btn btn-outline-dark btn-sm mb-4 fw-bold" onclick="navigateTo('view-home')">
        <i class="bi bi-arrow-left"></i> Regresar al Inicio
      </button>

      <div class="row justify-content-center g-4">
        <div class="col-lg-6">
          <div class="p-4 p-md-5 bg-white border border-dark shadow-sm">
            <ul class="nav nav-pills nav-justified mb-4" id="authTabs" role="tablist">
              <li class="nav-item">
                <button class="nav-link active rounded-0 border border-dark fw-bold" id="tab-login" data-bs-toggle="pill" data-bs-target="#content-login" type="button">Iniciar Sesión</button>
              </li>
              <li class="nav-item">
                <button class="nav-link rounded-0 border border-dark fw-bold ms-2" id="tab-register" data-bs-toggle="pill" data-bs-target="#content-register" type="button">Crear Cuenta</button>
              </li>
            </ul>

            <div class="tab-content" id="authTabContent">
              <div class="tab-pane fade show active" id="content-login" role="tabpanel">
                <h4 class="fw-bold mb-3" style="color: var(--color-azul-tinta);"><i class="bi bi-box-arrow-in-right"></i> Acceso a Lectores</h4>
                <p class="small text-muted mb-4">Ingresa tu correo y contraseña registrados para acceder a tu sesión activa.</p>

                <form onsubmit="handleLogin(event)">
                  <div class="mb-3">
                    <label class="form-label fw-bold small">Correo Electrónico</label>
                    <input type="email" id="loginEmail" class="form-control rounded-0 border-dark" placeholder="correo@ejemplo.com" required>
                  </div>
                  <div class="mb-3">
                    <label class="form-label fw-bold small">Contraseña</label>
                    <input type="password" id="loginPass" class="form-control rounded-0 border-dark" placeholder="••••••••" required>
                  </div>
                  <button type="submit" class="btn btn-win-primary w-100 fw-bold"><i class="bi bi-unlock-fill"></i> Iniciar Sesión</button>
                </form>
              </div>

              <div class="tab-pane fade" id="content-register" role="tabpanel">
                <h4 class="fw-bold mb-3" style="color: var(--color-azul-tinta);"><i class="bi bi-person-plus-fill"></i> Crear Nueva Cuenta</h4>
                <p class="small text-muted mb-4">Únete a la red de lectores de W.I.N y guarda tu cuenta en nuestra base de datos activa.</p>

                <form id="userForm" onsubmit="handleRegister(event)">
                  <div class="mb-3">
                    <label class="form-label fw-bold small">Nombre Completo</label>
                    <input type="text" id="regName" class="form-control rounded-0 border-dark" required placeholder="Ej. Carlos Mendoza">
                  </div>
                  <div class="mb-3">
                    <label class="form-label fw-bold small">Correo Electrónico</label>
                    <input type="email" id="regEmail" class="form-control rounded-0 border-dark" required placeholder="correo@ejemplo.com">
                  </div>
                  <div class="mb-3">
                    <label class="form-label fw-bold small">Contraseña</label>
                    <input type="password" id="regPass" class="form-control rounded-0 border-dark" required placeholder="Crea tu contraseña">
                  </div>
                  <div class="mb-3">
                    <label class="form-label fw-bold small">Sección Preferida</label>
                    <select id="regInterest" class="form-select rounded-0 border-dark" required>
                      <option value="Deportes">Deportes (En Cancha)</option>
                      <option value="Economía">Economía (Plata y Números)</option>
                      <option value="Cultura">Cultura (Raíces)</option>
                      <option value="Entretenimiento">Entretenimiento (Pantalla y Play)</option>
                      <option value="Salud">Salud (Bienestar Real)</option>
                    </select>
                  </div>
                  <button type="submit" class="btn btn-win-primary w-100 fw-bold"><i class="bi bi-check-circle-fill"></i> Registrar e Iniciar Sesión</button>
                </form>
              </div>
            </div>

            <div id="activeSessionPanel" class="d-none mt-3 p-3 border border-dark bg-light text-center">
              <span class="badge bg-success mb-2"><i class="bi bi-check-circle"></i> Sesión Activa</span>
              <h5 class="fw-bold m-0" id="sessionUserName">Usuario</h5>
              <p class="small text-muted mb-2" id="sessionUserEmail">correo@ejemplo.com</p>
              <button class="btn btn-outline-danger btn-sm rounded-0 fw-bold mt-2" onclick="handleLogout()"><i class="bi bi-box-arrow-right"></i> Cerrar Sesión</button>
            </div>
          </div>
        </div>

        <div class="col-lg-6">
          <div class="p-4 bg-white border border-dark shadow-sm">
            <div class="d-flex justify-content-between align-items-center mb-3">
              <h4 class="fw-bold m-0" style="color: var(--color-azul-tinta);"><i class="bi bi-database"></i> Usuarios Registrados</h4>
              <span class="badge bg-success"><i class="bi bi-shield-lock"></i> BD Protegida</span>
            </div>
            <p class="small text-muted">Directorio de lectores almacenados activamente en el sistema:</p>

            <div class="table-responsive">
              <table class="table table-win table-hover align-middle">
                <thead>
                  <tr>
                    <th>ID</th>
                    <th>Nombre</th>
                    <th>Correo</th>
                    <th>Preferencia</th>
                  </tr>
                </thead>
                <tbody id="usersTableBody"></tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div id="view-about" class="screen-view">
    <div class="container my-5">
      <button class="btn btn-outline-dark btn-sm mb-4 fw-bold" onclick="navigateTo('view-home')">
        <i class="bi bi-arrow-left"></i> Regresar al Inicio
      </button>

      <div class="bg-white p-5 border border-dark shadow-sm">
        <h2 class="display-5 fw-bold mb-4 text-center" style="color: var(--color-azul-tinta);">Línea Editorial e Identidad</h2>
        
        <div class="p-4 border border-dark mb-4" style="background-color: var(--color-marfil);">
          <h3 class="fw-bold mb-3" style="color: var(--color-azul-tinta);"><i class="bi bi-info-circle-fill"></i> ¿Quiénes somos?</h3>
          <p class="lh-lg mb-0">
            <strong>W.I.N (World Information Network)</strong> es un periódico digital especializado comprometido con ofrecer información veraz, rigurosa y contextualizada en economía, deportes, cultura, entretenimiento y salud. Nacemos con la convicción de conectar a nuestros lectores con acontecimientos locales e internacionales desde una perspectiva ética, independiente y libre de sensacionalismo.
          </p>
        </div>

        <div class="row g-4 my-3">
          <div class="col-md-6">
            <div class="p-4 border border-dark h-100" style="background-color: var(--color-marfil);">
              <h4 class="fw-bold" style="color: var(--color-azul-tinta);">Misión</h4>
              <p>Informar con objetividad, veracidad y responsabilidad sobre los acontecimientos más relevantes en economía, deportes, cultura, entretenimiento y salud, ofreciendo contenido verificado y útil.</p>
            </div>
          </div>
          <div class="col-md-6">
            <div class="p-4 border border-dark h-100" style="background-color: var(--color-marfil);">
              <h4 class="fw-bold" style="color: var(--color-azul-tinta);">Visión</h4>
              <p>Ser el periódico digital de referencia por su credibilidad y excelencia periodística en El Salvador, conectando a la sociedad con una experiencia moderna, accesible y confiable.</p>
            </div>
          </div>
        </div>

        <h4 class="fw-bold mt-4 mb-3" style="color: var(--color-azul-tinta);">Integrantes del Equipo Periodístico</h4>
        <ul class="list-group list-group-flush border border-dark">
          <li class="list-group-item"><strong>Daniel Ernesto Pérez Torres</strong> (PT250916)</li>
          <li class="list-group-item"><strong>Alejandra Abigail Díaz Molina</strong> (DM251875)</li>
          <li class="list-group-item"><strong>Cristian Daniel Portillo Rivera</strong> (PR231615)</li>
          <li class="list-group-item"><strong>Karina Elizabeth Vela Pineda</strong> (VP202421)</li>
          <li class="list-group-item"><strong>José Raúl Landaverde Argueta</strong> (LA232970)</li>
          <li class="list-group-item"><strong>Cristian Edenilson Batres Santamaria</strong> (BS251953)</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="modal fade" id="authGifModal" tabindex="-1" aria-hidden="true" data-bs-backdrop="static">
    <div class="modal-dialog modal-dialog-centered text-center">
      <div class="modal-content border border-dark rounded-0 p-4" style="background-color: var(--color-marfil);">
        <h3 class="fw-bold mb-2" id="gifModalTitle" style="color: var(--color-azul-tinta);">¡Bienvenido a W.I.N!</h3>
        <p class="small text-muted mb-3" id="gifModalSub">Cargando tu sesión...</p>
        
        <div class="my-3">
          <img src="https://media1.tenor.com/m/LedML6uF2-4AAAAC/cat-scuba-scuba.gif" alt="Bienvenido GIF" class="img-fluid border border-dark shadow-sm" style="max-height: 220px; object-fit: cover;">
        </div>
      </div>
    </div>
  </div>

  <footer class="py-4 text-center">
    <div class="container">
      <p class="mb-1 fw-bold">W.I.N — World Information Network</p>
      <p class="small text-white-50 mb-0">Donde la tradición, informa al presente | Universidad Don Bosco 2026</p>
    </div>
  </footer>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>

  <script>
    const canvas = document.getElementById('lavaCanvas');
    const ctx = canvas.getContext('2d');

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    class LavaBlob {
      constructor() {
        this.reset();
      }
      reset() {
        this.x = Math.random() * canvas.width;
        this.y = canvas.height + Math.random() * 200;
        this.radius = Math.random() * 85 + 50;
        this.speed = Math.random() * 0.9 + 0.4;
        this.pulse = Math.random() * 0.05;
      }
      update() {
        this.y -= this.speed;
        this.x += Math.sin(this.y * 0.008) * 0.8;
        if (this.y < -this.radius * 2) {
          this.reset();
        }
      }
      draw() {
        ctx.beginPath();
        let grad = ctx.createRadialGradient(this.x, this.y, 0, this.x, this.y, this.radius);
        grad.addColorStop(0, 'rgba(255, 192, 203, 0.95)');
        grad.addColorStop(0.6, 'rgba(255, 182, 193, 0.55)');
        grad.addColorStop(1, 'rgba(255, 192, 203, 0)');
        ctx.fillStyle = grad;
        ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    const blobs = Array.from({ length: 18 }, () => new LavaBlob());

    function animateLava() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      blobs.forEach(blob => {
        blob.update();
        blob.draw();
      });
      requestAnimationFrame(animateLava);
    }
    animateLava();

    /* ========================================================
       BASE DE DATOS COMPLETA - TODAS LAS NOTAS > 200 PALABRAS
       ======================================================== */
    const articlesData = [
      // DEPORTES (En Cancha)
      {
        id: 1,
        category: "Deportes",
        subCategory: "Balón en Juego",
        title: "Brasil vence a Japón y avanza a los octavos de final del Mundial 2026",
        author: "Alejandra Abigail Díaz Molina",
        date: "Lunes 29 de junio de 2026",
        location: "Houston, Texas, 29 de junio de 2026",
        source: "FOX Sports (FOX 26), FIFA Match Center y Agence France-Presse (AFP).",
        mainImg: "https://media-cldnry.s-nbcnews.com/image/upload/c_fill,g_auto,w_2500,h_1726/rockcms/2026-06/260629-brazil-japan-world-cup-ew-312p-e1c4d8.jpg",
        summary: "La selección de Brasil venció 2-1 a Japón este lunes 29 de junio en el NRG Stadium de Houston, Estados Unidos, en un partido correspondiente a los dieciseisavos de final de la Copa Mundial de la FIFA 2026.",
        paragraphs: [
          "La selección de Brasil venció 2-1 a Japón este lunes 29 de junio en el NRG Stadium de Houston, Estados Unidos, en un encuentro crucial de los dieciseisavos de final de la Copa Mundial de la FIFA 2026. Con esta apretada victoria, el combinado sudamericano selló su boleto directo hacia los octavos de final, mientras que el ordenado equipo japonés culminó de forma digna su destacada participación dentro de la cita mundialista de Norteamérica.",
          "Durante la primera mitad, Japón sorprendió tácticamente al bloque defensivo brasileño gracias a la velocidad de sus transiciones ofensivas. Al minuto 29, el mediocampista Kaishu Sano aprovechó un balón dividido tras un desajuste en el área chica para batir al portero y poner en ventaja al cuadro asiático. A partir de la anotación, el conjunto japonés replegó sus líneas de manera sumamente disciplinada, bloqueando los callejones interiores y resistiendo con éxito los embates iniciales de Brasil hasta llegar al descanso.",
          "(imagen)",
          "En la etapa complementaria, la Canarinha modificó su planteamiento táctico incrementando la presión alta y abriendo el campo por las bandas. El esfuerzo rindió frutos al minuto 56, cuando Casemiro conectó un imponente testarazo al fondo de la red tras un tiro de esquina magistralmente ejecutado por Gabriel Magalhães. Con el marcador igualado 1-1, el cotejo ganó en dramatismo y desgaste físico para ambas plantillas.",
          "Ambos entrenadores realizaron modificaciones tácticas buscando refrescar sus líneas en el tramo final. Cuando la prórroga parecía inevitable, Gabriel Martinelli aprovechó una rápida asistencia de Bruno Guimarães al minuto 90+5 para firmar el 2-1 definitivo. La agónica anotación desató el delirio de la afición brasileña en el estadio, asegurando la continuidad del Pentacampeón en la máxima fiesta del balompié global.",
          "(imagen)",
          "El técnico brasileño destacó en la conferencia de prensa posterior la capacidad de reacción mental de sus dirigidos, reconociendo a su vez la enorme evolución táctica que demostró la selección japonesa a lo largo de los 90 minutos de juego."
        ],
        inlineImages: [
          "https://a.espncdn.com/photo/2026/0629/r1681551_1296x729_16-9.jpg",
          "https://cdn.conmebol.com/wp-content/uploads/2026/06/2283896102.jpg-1-1024x646.jpeg"
        ]
      },
      {
        id: 2,
        category: "Deportes",
        subCategory: "Bajo el Aro",
        title: "New York Knicks rompe sequía histórica y se corona campeón de la NBA 2026",
        author: "Cristian Daniel Portillo Rivera",
        date: "Lunes 15 de junio de 2026",
        location: "Nueva York, Estados Unidos, 15 de junio de 2026",
        source: "NBA Official Communications, ESPN Stats & Info y La Nación Deportes.",
        mainImg: "https://st1.uvnimg.com/23/31/243949864310a6dbeea61823a91e/ap26165151554560.jpg",
        summary: "Los New York Knicks conquistaron el título de la NBA al derrotar 4-1 a los San Antonio Spurs en las Finales 2026, volviendo a alzar el trofeo tras décadas de espera.",
        paragraphs: [
          "En una velada repleta de historia y emoción dentro del baloncesto profesional, los New York Knicks se consagraron campeones de la temporada 2025-2026 de la NBA tras superar 4-1 en la serie final a los San Antonio Spurs. La victoria decisiva obtenida en el abarrotado Madison Square Garden significó el fin de una prolongada sequía de 53 años sin alzar el emblemático trofeo Larry O'Brien.",
          "El encuentro definitivo estuvo marcado por un despliegue táctico excepcional de la franquicia neoyorquina, que combinó un juego defensivo asfixiante con una efectividad sobresaliente en los tiros perimetrales. Desde el primer cuarto, los Knicks impusieron un ritmo vertiginoso en las transiciones, capitalizando los descuidos defensivos de un equipo tejano que no logró descifrar el esquema de presión colectiva planteado en la duela.",
          "(imagen)",
          "Con un rendimiento colectivo brillante en el que destacaron tanto los titulares como la banca, el equipo de la Gran Manzana consolidó una diferencia irreversible en el marcador hacia el último cuarto. La actuación individual de su base estrella, quien lideró las estadísticas en puntos y asistencias, resultó clave para desarticular la estructura defensiva de San Antonio durante toda la eliminatoria.",
          "El pitazo final desató una emotiva celebración que se extendió desde el interior del recinto deportivo hasta las principales avenidas de Manhattan. Aficionados de múltiples generaciones celebraron un hito histórico que reinscribe a los Knicks en el mapa de las grandes dinastías del baloncesto norteamericano e internacional."
        ],
        inlineImages: [
          "https://www.bostonherald.com/wp-content/uploads/2026/06/FINALES-KNICKS_CAMPEONES_33374.jpg?w=1400"
        ]
      },
      {
        id: 3,
        category: "Deportes",
        subCategory: "A Fondo",
        title: "Lando Norris logra su primer Campeonato Mundial de Fórmula 1",
        author: "Daniel Ernesto Pérez Torres",
        date: "Lunes 8 de diciembre de 2025",
        location: "Abu Dhabi, Emiratos Árabes Unidos, 8 de diciembre de 2025",
        source: "FIA Formula 1 World Championship, Motorsport.com y BBC Sport.",
        mainImg: "https://www.lanacion.com.ar/resizer/v2/toda-la-emocion-de-lando-norris-en-el-podio-ya-es-73JOGWVGGJEKJKYI65DIXHVCBY.JPG?auth=46f7c65ca9614de0156c7263578e56ee80925fd3ab62f3648e78e901f9008f2c&width=1200&height=800&quality=70&smart=true",
        summary: "El piloto británico Lando Norris, al volante de McLaren, se proclamó campeón del mundo de Fórmula 1 tras una temporada brillante culminada en Abu Dhabi.",
        paragraphs: [
          "El trazado de Yas Marina en el Gran Premio de Abu Dhabi fue el escenario donde se resolvió una de las campañas más reñidas y espectaculares en la historia reciente de la Fórmula 1. Al cruzar la línea de meta en las posiciones de podio, el piloto británico Lando Norris aseguró matemáticamente los puntos necesarios para coronarse por primera vez como Campeón Mundial de Pilotos de la categoría reina del automovilismo.",
          "Al volante de un monoplaza McLaren de rendimiento sobresaliente, Norris ejecutó una carrera tácticamente impecable. A lo largo de las 58 vueltas del circuito, el corredor británico administró con madurez la degradación de los neumáticos, defendiendo su posición ante los constantes embates de sus rivales directos en la lucha por el certamen y evitando cualquier incidente en las zonas de frenada de alta velocidad.",
          "(imagen)",
          "Esta consagración representa el punto culminante de un proceso de desarrollo técnico iniciado por la escudería McLaren años atrás. El resultado no solo le otorga a Norris su primer trofeo orbital de pilotos, sino que consolida a la histórica escudería británica en la cima del Campeonato Mundial de Constructores frente a rivales de la talla de Red Bull y Ferrari.",
          "En el podio de premiación, el flamante campeón de 26 años dedicó el triunfo al equipo de ingenieros y mecánicos en Woking, subrayando que la consistencia, la resiliencia en los momentos difíciles de la temporada y el trabajo en equipo fueron las piezas fundamentales para alcanzar la cima del deporte a motor internacional."
        ],
        inlineImages: [
          "https://www.infobae.com/resizer/v2/VOH54QPYWFE2VNVJJEYFQHK2QI.JPG?auth=39017927c7023177fddaaad633c7e788d63fde3c9c1380d55a441b656c782bde"
        ]
      },
      {
        id: 4,
        category: "Deportes",
        subCategory: "Cinco Aros",
        title: "El Salvador afina detalles para la delegación nacional en Santo Domingo 2026",
        author: "Karina Elizabeth Vela Pineda",
        date: "Jueves 20 de agosto de 2026",
        location: "San Salvador, 20 de agosto de 2026",
        source: "Comité Olímpico de El Salvador (COES), INDES y Centro Caribe Sports.",
        mainImg: "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/07/juegos-centroamericanos-coes.jpg",
        summary: "El Comité Olímpico de El Salvador confirmó el plan de apoyo integral para los atletas que representarán al país en los XXV Juegos Centroamericanos y del Caribe Santo Domingo 2026.",
        paragraphs: [
          "El movimiento olímpico salvadoreño mantiene un ritmo acelerado e integral de preparación técnica, biomédica y logística de cara a su participación en los XXV Juegos Centroamericanos y del Caribe Santo Domingo 2026. Autoridades del Comité Olímpico de El Salvador (COES) expusieron los detalles del plan de apoyo que respaldará a más de doscientos atletas nacionales clasificados en diversas disciplinas deportivas.",
          "El programa multidisciplinario puesto en marcha contempla concentraciones en centros de alto rendimiento locales e internacionales, monitoreo nutricional personalizado y preparación psicológica especializada para afrontar la exigencia competitiva del certamen regional. Deportes como tiro con arco, surf, pesas, vela, karate y natación encabezan la nómina de disciplinas con elevadas expectativas de medalla.",
          "(imagen)",
          "Asimismo, los dirigentes deportivos subrayaron la importancia de dar continuidad a los procesos de desarrollo atlético iniciados en el ciclo olímpico anterior, garantizando fogueos internacionales de primer nivel que permitan elevar la marca técnica de los deportistas frente a las potencias de la zona del Caribe y Centroamérica.",
          "Con este esquema de preparación rigurosa, la delegación cuscatleca busca superar la cosecha histórica de preseas y reafirmar el posicionamiento del deporte salvadoreño en la esfera competitiva continental, fomentando a su vez el surgimiento de nuevas promesas en las categorías juveniles."
        ],
        inlineImages: [
          "https://lanoticiasv.com/wp-content/uploads/2026/07/santodomingo.jpg"
        ]
      },
      {
        id: 5,
        category: "Deportes",
        subCategory: "Modo Gamer",
        title: "San Salvador albergó la gran final de torneos de eSports regionales",
        author: "José Raúl Landaverde Argueta",
        date: "Lunes 27 de octubre de 2025",
        location: "San Salvador, 27 de octubre de 2025",
        source: "Liga Centroamericana de eSports, Visitesports.com y Diario El Mundo.",
        mainImg: "https://cdn-pro.elsalvador.com/wp-content/uploads/2025/09/539796980_1307626754095577_8931690389258325397_n-1-1024x768.jpg",
        summary: "Cientos de jóvenes compitieron en la capital salvadoreña durante el evento 'Legends 6', reuniendo a los mejores equipos de Valorant y League of Legends.",
        paragraphs: [
          "La capital salvadoreña se convirtió en el epicentro del entretenimiento digital y la tecnología con la exitosa realización del torneo regional 'Legends 6'. El evento congregó a cientos de entusiastas, creadores de contenido y ciberdeportistas provenientes de distintos países de la región centroamericana para competir en títulos icónicos como Valorant, League of Legends y Counter-Strike 2.",
          "Durante las intensas jornadas de competencia, la escenografía adaptada con pantallas LED de alta definición y conectividad de fibra óptica de última generación permitió a los asistentes vivir cada jugada con una inmersión total. Los equipos finalistas exhibieron refinadas estrategias de comunicación interna, reflejos mecánicos excepcionales y un nivel de coordinación colectiva comparable con ligas de alcance continental.",
          "(imagen)",
          "Además de repartir jugosos premios en efectivo y becas de especialización en áreas tecnológicas, la cita sirvió como vitrina institucional para consolidar la profesionalización de los eSports en El Salvador. Distintas marcas patrocinadoras y federaciones resaltaron la importancia de canalizar el talento joven hacia carreras vinculadas con la programación, el diseño de videojuegos y la gestión de eventos digitales.",
          "El cierre de la actividad estuvo marcado por aplaudidas exhibiciones de cosplay y espacios de encuentro entre comunidades de jugadores, reconfirmando a San Salvador como una sede altamente competitiva y atractiva para la realización de certámenes tecnológicos de gran magnitud en la región."
        ],
        inlineImages: [
          "https://www.telefonica.com/es/wp-content/uploads/sites/4/2024/02/pexels-photo-9072394.jpeg"
        ]
      },
      {
        id: 6,
        category: "Deportes",
        subCategory: "Cara a Cara",
        title: "Luisa Maida: 'Así como se entrena el cuerpo, también hay que entrenar la mente'",
        author: "Alejandra Abigail Díaz Molina",
        date: "Domingo 6 de septiembre de 2026",
        location: "San Salvador, 6 de septiembre de 2026",
        source: "ElSalvador.com, entrevista exclusiva realizada por el periodista Roberto J. Leiva.",
        mainImg: "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/09/luisa-maida-entrevista-psicologia-deportiva-experiencia-santo-domingo-2026-atletas-el-salvador-team-esa-robbie-ruud-02.jpg",
        summary: "La reconocida psicóloga deportiva y exatleta olímpica Luisa Maida comparte en exclusiva los aspectos clave para fortalecer la mentalidad de los deportistas de alto rendimiento.",
        paragraphs: [
          "En un diálogo ameno y revelador con el periódico digital W.I.N, la prestigiosa psicóloga deportiva y gloriosa exatleta olímpica salvadoreña Luisa Maida desglosó los pilares invisibles que sostienen el éxito en el deporte contemporáneo. Basándose en su amplia experiencia en las fosas de tiro de Pekín 2008 y su actual trabajo de campo con selecciones nacionales, Maida enfatizó que la preparación psicológica es igual de determinante que la preparación física o táctica.",
          "Durante la entrevista, la especialista analizó los mecanismos emocionales que experimenta un deportista sometido a altos niveles de presión mediática y competitiva. Explicó que condiciones como la ansiedad precompetitiva o el miedo al error deben ser abordadas mediante técnicas científicas de autorregulación, visualización guiada y control de la respiración diafragmática para evitar bloqueos en los momentos decisivos.",
          "(imagen)",
          "\"Una competencia internacional no debe ser percibida por el atleta como una amenaza latente a su valor personal, sino como una oportunidad extraordinaria para desplegar las herramientas trabajadas durante meses. En lugar de pensar 'ahí viene la presión', hay que instalar en la mente la premisa 'aquí vengo preparado'\", profundizó Maida al abordar su metodología de intervención con el Team ESA.",
          "Finalmente, la exatleta hizo un llamado riguroso a las federaciones y entrenadores para integrar de forma permanente la salud mental en las estructuras de formación base, asegurando que un deportista emocionalmente equilibrado no solo rinde mejor en la duela o la cancha, sino que consolida un proyecto de vida integral y saludable."
        ],
        inlineImages: [
          "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/09/luisa-maida-entrevista-psicologia-deportiva-experiencia-santo-domingo-2026-atletas-el-salvador-team-esa-robbie-ruud-01.jpg"
        ]
      },
      {
        id: 7,
        category: "Deportes",
        subCategory: "Números del Juego",
        title: "Árbitro salvadoreño Iván Barton comparte sus métricas e hitos profesionales en FESA",
        author: "Cristian Daniel Portillo Rivera",
        date: "Miércoles 23 de septiembre de 2026",
        location: "Santa Ana, 23 de septiembre de 2026",
        source: "ElSalvador.com, Fundación Educando a un Salvadoreño (FESA) y Concacaf Refereeing Department.",
        mainImg: "https://assets.laprensagrafica.com/__export/1781614551548/sites/prensagrafica/img/2026/06/16/barton.jpg_673822677.jpg",
        summary: "El réferi internacional Iván Barton repasó sus estadísticas de rendimiento arbitral y las decisiones estratégicas que lo llevaron desde Santa Ana hasta semifinales mundialistas.",
        paragraphs: [
          "El silbante internacional salvadoreño Iván Barton brindó una inspiradora conferencia magistral ante decenas de jóvenes becarios en las instalaciones de la Fundación Educando a un Salvadoreño (FESA). Durante la ponencia técnica, Barton desglosó con exactitud las métricas de rendimiento físico, análisis de video e interpretación del reglamento que le han permitido consolidarse como uno de los árbitros más calificados de la Concacaf y la FIFA.",

          "Barton detalló que en un encuentro de alta intensidad de nivel mundialista, un réferi central puede llegar a recorrer entre 10 y 13 kilómetros, realizando más de 50 esprints cortos y tomando alrededor de 200 decisiones en milisegundos. Destacó que el margen de error aceptado por las comisiones técnicas internacionales es inferior al 3%, lo que exige un acondicionamiento cardiovascular óptimo y una preparación teórica exhaustiva.",
          "(imagen)",
          "El profesional santaneco compartió anécdotas de su participación en la Copa Mundial de Catar y torneos de clubes continentales, enfatizando la trascendencia del temple psicológico al interactuar con jugadores de clase mundial y al utilizar la herramienta tecnológica del VAR (Árbitro de Asistente de Vídeo).",
          "Para cerrar el encuentro, el colegiado motivó a la juventud salvadoreña a perseguir sus metas mediante la disciplina inflexible y el estudio constante, reafirmando que el talento nacional posee todas las capacidades requeridas para destacar con excelencia en los escenarios más exigentes del deporte internacional."
        ],
        inlineImages: [
          "https://diarioelsalvador.media/2026/09/Ivan-Barton.jpg"
        ]
      },

      // ECONOMÍA (Plata y Números)
      {
        id: 8,
        category: "Economía",
        subCategory: "Casa Adentro",
        title: "Remesas hacia El Salvador mantendrían crecimiento, pero a menor ritmo",
        author: "Karina Elizabeth Vela Pineda",
        date: "Martes 22 de septiembre de 2026",
        location: "San Salvador, 22 de septiembre de 2026",
        source: "ElSalvador.com, Banco Central de Reserva (BCR) y reportes de la CEPAL.",
        mainImg: "https://images.unsplash.com/photo-1526304640581-d334cdbbf45e?auto=format&fit=crop&w=800&q=80",
        summary: "Las remesas familiares hacia El Salvador continuarían creciendo durante 2026, aunque a un ritmo menor que el registrado durante el año anterior.",
        paragraphs: [
          "Los ingresos por remesas familiares que ingresan a El Salvador mantendrán un comportamiento positivo al cierre del año 2026, si bien la tasa de variación interanual reflejará un ritmo de desaceleración gradual en comparación con los máximos históricos registrados en periodos anteriores. Según proyecciones analíticas del sector financiero citadas por ElSalvador.com y el Banco Central de Reserva (BCR), el monto acumulado proyectado se situaría cercano a los $10,458 millones.",
          "Esta cifra proyectada equivaldría a un crecimiento estimado del 4.8 % en comparación con el total contabilizado durante el año previo. Los analistas económicos explican que esta moderación en la velocidad de crecimiento responde a una serie de dinámicas estructurales en el mercado laboral estadounidense, principal país de origen de los envíos financieros de la diáspora salvadoreña.",
          "(imagen)",
          "Entre los factores determinantes se señalan el incremento en los costos de vida dentro de las ciudades receptoras en Norteamérica, una estabilización en los flujos migratorios y variaciones en las políticas de regulación del empleo informal en el extranjero. A pesar de la desaceleración porcentual, las remesas continúan constituyendo un pilar macroeconómico indispensable para el sustento de miles de hogares salvadoreños y para el impulso del consumo privado local.",
          "Expertos financieros sugieren continuar promoviendo mecanismos que permitan canalizar una mayor porción de estos flujos divisas hacia el ahorro formal, la inversión productiva en pequeños negocios y el acceso a seguros familiares, transformando el aporte de la diáspora en un motor de desarrollo económico sostenible en el territorio nacional."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1559526324-4b87b5e36e44?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 9,
        category: "Economía",
        subCategory: "Fuera de Fronteras",
        title: "Bancos centrales ajustan tasas de interés globales ante moderación de la inflación",
        author: "Daniel Ernesto Pérez Torres",
        date: "Jueves 18 de septiembre de 2026",
        location: "Washington D.C., Estados Unidos, 18 de septiembre de 2026",
        source: "Reserva Federal de EE. UU. (Fed), Banco Central Europeo (BCE) y Fondo Monetario Internacional (FMI).",
        mainImg: "https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?auto=format&fit=crop&w=800&q=80",
        summary: "Las principales instituciones financieras internacionales anunciaron nuevos recortes en las tasas de interés de referencia para estimular los mercados internacionales.",
        paragraphs: [
          "En una decisión coordinada que marca el rumbo de la política monetaria mundial, la Reserva Federal de los Estados Unidos y el Banco Central Europeo anunciaron sendas reducciones en sus respectivas tasas de interés de referencia. La medida responde a la contención progresiva de los índices de inflación en las economías desarrolladas y busca estimular la inversión productiva y el empleo sin generar presiones sobre los precios de los bienes de consumo.",
          "Los mercados bursátiles internacionales reaccionaron de manera optimista ante las decisiones de las autoridades monetarias, registrando alzas significativas en los principales indicadores financieros de Nueva York, Londres y Tokio. La flexibilización de las condiciones crediticias mundiales reduce los costos del endeudamiento externo tanto para corporaciones privadas como para gobiernos de economías emergentes en América Latina.",
          "(imagen)",
          "Especialistas del Fondo Monetario Internacional (FMI) señalaron que un entorno de menores tasas internacionales favorecerá el flujo de capitales hacia proyectos de infraestructura, energía renovable y tecnología en países en desarrollo. Sin embargo, advirtieron que la volatilidad en los precios de ciertas materias primas y las tensiones geopolíticas regionales aún representan riesgos latentes para la estabilidad financiera global.",
          "Para economías dolarizadas como la de El Salvador, este viraje en la política crediticia global ofrece un respiro en los costos del financiamiento bancario comercial y las emisiones de deuda soberana, facilitando la atracción de inversiones internacionales en sectores estratégicos durante el último trimestre del ejercicio fiscal."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1590283603385-17ffb3a7f29f?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 10,
        category: "Economía",
        subCategory: "De Cero a Marca",
        title: "Nuevos emprendimientos tecnológicos impulsan el ecosistema startup salvadoreño",
        author: "Cristian Daniel Portillo Rivera",
        date: "Lunes 21 de septiembre de 2026",
        location: "San Salvador, 21 de septiembre de 2026",
        source: "Ministerio de Economía (MINEC), Red de Emprendedores de El Salvador y Forbes Centroamérica.",
        mainImg: "https://static.accupass.com/eventbanner/2604140341281127001360.jpg",
        summary: "Más de cincuenta nuevas empresas emergentes en sectores fintech y comercio electrónico han logrado consolidar rondas de inversión inicial durante el año.",
        paragraphs: [
          "El panorama del emprendimiento de base tecnológica en El Salvador atraviesa por un periodo de ebullición sin precedentes, impulsado por una nueva generación de desarrolladores, creativos y financieros que están transformando conceptos innovadores en marcas comerciales altamente competitivas. Según datos del Ministerio de Economía (MINEC), más de cincuenta startups nacionales en sectores como la tecnología financiera (fintech), la logística de última milla y el comercio electrónico han logrado levantar capital semilla durante el presente año.",
          "El surgimiento de aceleradoras de negocios locales y alianzas estratégicas con fondos de inversión centroamericanos ha permitido que empresas emergentes diseñen plataformas digitales para automatizar pagos, optimizar inventarios en pequeñas empresas y facilitar transacciones transfronterizas. Este ecosistema dinámico está permitiendo que marcas nacidas en El Salvador escalen rápidamente sus servicios hacia mercados vecinos como Guatemala, Honduras y Costa Rica.",
          "(imagen)",
          "Uno de los factores determinantes en este crecimiento ha sido la capacitación especializada en desarrollo de software, análisis de datos y estrategias de posicionamiento de marca en entornos digitales. La adopción de tecnologías avanzadas ha reducido las barreras de entrada tradicionales, permitiendo a emprendimientos jóvenes competir cara a cara con actores consolidados en el sector de servicios.",
          "Líderes del sector coinciden en que la consolidación de marcas locales sólidas no solo atrae capital extranjero, sino que genera empleos de alto valor agregado para la juventud salvadoreña, posicionando al país como un hub regional emergente de innovación digital y emprendimiento tecnológico."
        ],
        inlineImages: [
          "https://centroamericaeconomia.net/wp-content/uploads/2026/08/WhatsApp-Image-2026-07-30-at-4.36.23-PM-1-copia.png"
        ]
      },
      {
        id: 11,
        category: "Economía",
        subCategory: "Jugadas de Negocio",
        title: "Aumenta $0.17 el precio de los combustibles en El Salvador",
        author: "José Raúl Landaverde Argueta",
        date: "Martes 15 de septiembre de 2026",
        location: "El Salvador, 15 de septiembre de 2026",
        source: "Dirección General de Energía, Hidrocarburos y Minas (DGEHM) y Agencia Internacional de Energía.",
        mainImg: "https://images.unsplash.com/photo-1527018601619-a508a2be00cd?auto=format&fit=crop&w=800&q=80",
        summary: "Los precios de referencia de los combustibles aumentaron nuevamente en El Salvador a partir del 15 de septiembre de 2026.",
        paragraphs: [
          "La Dirección General de Energía, Hidrocarburos y Minas (DGEHM) anunció un nuevo ajuste al alza en los precios de referencia de los combustibles en todo el territorio nacional, vigente a partir del 15 de septiembre. Las variaciones implican un incremento generalizado de $0.17 por galón en las gasolinas de tipo superior y regular, así como en el diésel, extendiéndose la quincena tarifaria hasta finales de mes.",
          "Con la actualización de precios, la gasolina superior pasó a cotizarse de la siguiente manera: $5.13 por galón en la zona central, $5.14 en el occidente del país y $5.17 en los departamentos orientales. Por su parte, la gasolina regular registró costos de $4.80 en el centro y $4.81 en las zonas occidental y oriental. El diésel alcanzó un precio de referencia uniforme de $4.86 por galón en la zona central y $4.87 en el resto del país.",
          "(imagen)",
          "Las autoridades gubernamentales explicaron que las fluctuaciones alcistas responden directamente a presiones internacionales en la cadena de distribución de petróleo. Entre los factores desencadenantes se citan los recortes de producción aplicados por la OPEP+, interrupciones logísticas en el transporte marítimo de hidrocarburos y la persistencia de tensiones geopolíticas en regiones estratégicas de Medio Oriente y Europa del Este.",
          "Representantes de gremiales del transporte de carga y comerciantes locales expresaron su monitoreo constante a las variaciones del mercado petrolero, haciendo un llamado al uso eficiente de los carburantes para mitigar el impacto operativo en la estructura de costos de flete de la canasta básica y productos de consumo masivo."
        ],
        inlineImages: [
          "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/09/combustibles-precios-1024x768.jpg"
        ]
      },
      {
        id: 12,
        category: "Economía",
        subCategory: "Sembrando Capital",
        title: "Fondo Verde aprueba financiamiento para proyectos agroforestales sostenibles",
        author: "Alejandra Abigail Díaz Molina",
        date: "Viernes 11 de septiembre de 2026",
        location: "San Salvador, 11 de septiembre de 2026",
        source: "Ministerio de Agricultura y Ganadería (MAG), Fondo de Inversión Ambiental de El Salvador (FIAES) y Fondo Verde para el Clima.",
        mainImg: "https://images.unsplash.com/photo-1500937386664-56d1dfef3854?auto=format&fit=crop&w=800&q=80",
        summary: "Nuevos fondos de cooperación internacional impulsarán la restauración de suelos y el cultivo sostenible de café y cacao en la cordillera Apaneca-Ilamatepec.",
        paragraphs: [
          "En una importante gestión para el fortalecimiento del sector rural y la sostenibilidad ecológica, el Fondo Verde para el Clima oficializó la aprobación de una partida de recursos de inversión no reembolsable destinada a proyectos agroforestales sostenibles en El Salvador. La iniciativa beneficiará directamente a miles de pequeños y medianos productores agrícolas asentados en las zonas altas de la cordillera Apaneca-Ilamatepec y la región septentrional del país.",
          "El programa multilateral enfoca su capital en la restauración de suelos degradados, la conservación de mantos acuíferos y la expansión de sistemas de cultivo bajo sombra de café y cacao fino de aroma. Estos modelos agrícolas no solo previenen la erosión de las laderas frente a eventos climáticos extremos, sino que capturan importantes toneladas de carbono atmosférico, posicionando la producción nacional en mercados de especialidad.",
          "(imagen)",
          "Además de la transferencia directa de insumos biológicos y sistemas de riego por goteo alimentados con energía solar, el financiamiento contempla programas de formación técnica en buenas prácticas agrícolas y certificación de comercio justo. Las cooperativas participantes tendrán acceso a garantías de crédito preferencial para modernizar sus plantas de beneficiado ecológico.",
          "Representantes del sector agropecuario manifestaron que sembrar capital ambiental y financiero en el campo salvadoreño es una estrategia integral para mitigar los efectos del cambio climático, revitalizar la economía local, generar oportunidades laborales dignas en comunidades rurales y asegurar la soberanía alimentaria con producción limpia y sostenible."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1464226184884-fa280b87c399?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 13,
        category: "Economía",
        subCategory: "El Tablero",
        title: "Economía salvadoreña crece 4.8 % durante el primer trimestre de 2026",
        author: "Cristian Daniel Portillo Rivera",
        date: "Miércoles 23 de septiembre de 2026",
        location: "San Salvador, 23 de septiembre de 2026",
        source: "ElSalvador.com, Banco Central de Reserva (BCR) y Ministerio de Economía.",
        mainImg: "https://diarioelsalvador.media/2026/06/WhatsApp-Image-2026-05-21-at-4.10.53-PM.jpeg",
        summary: "La economía salvadoreña registró un crecimiento del 4.8 % durante el primer trimestre de 2026, de acuerdo con los datos divulgados por el Banco Central de Reserva (BCR).",
        paragraphs: [
          "La actividad económica de El Salvador registró un dinamismo sobresaliente durante los primeros tres meses del año 2026, alcanzando una tasa de crecimiento interanual del 4.8 % en su Producto Interno Bruto (PIB). Así lo confirmó el Banco Central de Reserva (BCR) al presentar la actualización periódica de las cuentas nacionales, cifra que supera las expectativas promedio proyectadas por organismos financieros multilaterales.",
          "El informe macroeconómico destaca que el valor nominal de la producción nacional de bienes y servicios durante el periodo analizado ascendió a $9,261.8 millones. Entre las actividades económicas que mostraron mayor tracción e impulso en la medición destaca el sector de la construcción con un alza del 13.5 %, impulsado tanto por la inversión pública en infraestructura vial y centros hospitalarios como por proyectos privados residenciales y comerciales.",
          "(imagen)",
          "Otros rubros con desempeño positivo en el tablero económico fueron los servicios de transporte y almacenamiento, la industria turística, restaurantes y hoteles, así como el volumen de exportaciones de bienes no tradicionales. El consumo final de los hogares mantuvo una tendencia ascendente, respaldado por la estabilidad en los niveles de empleo y el flujo constante de divisas familiares.",
          "Autoridades del gabinete económico señalaron que estos indicadores reflejan la consolidación de la confianza del inversionista nacional y extranjero. Asimismo, reiteraron su compromiso de continuar facilitando trámites corporativos y promocionando al país en eventos internacionales de atracción de inversiones productivas."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1590283603385-17ffb3a7f29f?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 14,
        category: "Economía",
        subCategory: "Chamba Hoy",
        title: "Reconstrucción de mercados de Santa Ana y San Miguel contempla más de 3,700 locales",
        author: "Daniel Ernesto Pérez Torres",
        date: "Miércoles 23 de septiembre de 2026",
        location: "San Salvador, 23 de septiembre de 2026",
        source: "ElSalvador.com, Ministerio de Obras Públicas (MOP) y Asamblea Legislativa de El Salvador.",
        mainImg: "https://cdn-pro.elsalvador.com/wp-content/uploads/2025/10/noticias-construccion-mercados-santa-ana-san-miguel.jpg",
        summary: "La Asamblea Legislativa aprobó una modificación al presupuesto que incorpora $11.2 millones al Ministerio de Obras Públicas para avanzar en la reconstrucción de los mercados.",
        paragraphs: [
          "Con la meta de reactivar el comercio local e impulsar la creación de puestos de trabajo dignos en la zona occidental y oriental del país, la Asamblea Legislativa aprobó una modificación presupuestaria que destina $11.2 millones al Ministerio de Obras Públicas (MOP). Los fondos estarán focalizados en acelerar los trabajos de reconstrucción y modernización de los mercados municipales de Santa Ana y San Miguel.",
          "El financiamiento proviene de un convenio de crédito suscrito con el Banco Internacional de Reconstrucción y Fomento (BIRF). Del total asignado, cerca de $10.7 millones financiarán directamente las obras físicas de edificación estructural. El diseño arquitectónico proyectado para el nuevo mercado de Santa Ana contempla dos niveles con capacidad operativa para albergar a 2,387 locales comerciales bien equipados.",
          "(imagen)",
          "Por su parte, la moderna infraestructura presupuestada para el municipio de San Miguel constará de un edificio de tres pisos con espacio para 1,367 vendedores. Ambas edificaciones contarán con sistemas contra incendios de última generación, áreas de carga y descarga ordenadas, guarderías infantiles, oficinas administrativas y rampas de acceso inclusivo para personas con discapacidad.",
          "Se estima que la fase de construcción masiva generará más de tres mil empleos directos e indirectos en la industria de la edificación y servicios. Una vez concluidos, los nuevos mercados devolverán espacios seguros, limpios y modernos a comerciantes que resultaron afectados por siniestros anteriores, dinamizando la 'chamba' comercial en ambas cabeceras departamentales."
        ],
        inlineImages: [
          "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/02/dinero-y-negocios-mercados-santa-ana-san-miguel_4-1024x768.jpg"
        ]
      },

      // CULTURA (Raíces)
      {
        id: 15,
        category: "Cultura",
        subCategory: "Trazo Libre",
        title: "Exposición artística destaca el lenguaje visual y la formación de nuevas generaciones",
        author: "Karina Elizabeth Vela Pineda",
        date: "Viernes 18 de septiembre de 2026",
        location: "El Salvador, 18 de septiembre de 2026",
        source: "Ministerio de Cultura de El Salvador, Galería Nacional de Arte y catálogo oficial de la exposición.",
        mainImg: "https://www.euskonews.eus/0454zbk/argazkiak/kosmo45401_03.jpg",
        summary: "El reconocido pintor, dibujante y profesor de artes plásticas, maestro Arrieta, presentó una selección de obras realizadas a lo largo de su trayectoria artística.",
        paragraphs: [
          "En el marco de una vibrante iniciativa orientada a promover el aprecio por las artes plásticas y abrir los espacios culturales a la ciudadanía, la Galería Nacional alojó la inauguración de la muestra pictórica del maestro Arrieta. La colección reúne docenas de piezas creadas a lo largo de su fecunda carrera como pintor, dibujante y docente de generaciones de artistas locales.",
          "A través de una atenta guía explicativa, el maestro Arrieta detalló ante alumnos de escuelas públicas y universitarios cómo sus lienzos articulan un complejo lenguaje visual cargado de símbolos, texturas y contrastes cromáticos. Su propuesta formal aborda temas vinculados con la identidad centroamericana, la naturaleza tropical y la cotidianidad urbana con un estilo figurativo de gran lirismo.",
          "(imagen)",
          "Además de las pinturas al óleo y acrílico terminadas, la exhibición cuenta con un espacio didáctico donde se muestran los bocetos preparatorios en grafito y conté. Esta inclusión permite a los visitantes comprender el riguroso proceso de investigación visual, perspectiva y composición previa que exige la creación de una obra de arte plástico de alto nivel.",
          "El maestro Arrieta reafirmó su compromiso con la enseñanza del arte en las comunidades, destacando que el trazo libre y la creación artística son herramientas pacíficas fundamentales para cultivar la sensibilidad humana, el pensamiento crítico y la memoria colectiva en las nuevas generaciones salvadoreñas."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 16,
        category: "Cultura",
        subCategory: "Entre Líneas",
        title: "Feria Nacional del Libro reúne a autores independientes y editoriales centroamericanas",
        author: "José Raúl Landaverde Argueta",
        date: "Sábado 12 de septiembre de 2026",
        location: "San Salvador, 12 de septiembre de 2026",
        source: "Ministerio de Cultura de El Salvador, Cámara Salvadoreña del Libro y Red de Bibliotecas Públicas.",
        mainImg: "https://images.unsplash.com/photo-1457369804613-52c61a468e7d?auto=format&fit=crop&w=800&q=80",
        summary: "El Palacio Nacional de la Cultura acogió recitales de poesía, presentaciones de novelas contemporáneas y talleres de escritura creativa.",
        paragraphs: [
          "Las históricas instalaciones del Palacio Nacional de la Cultura sirvieron de escenario para la inauguración de la Feria Nacional del Libro 2026. El encuentro literario reunió a más de cuarenta casas editoriales independientes, distribuidores internacionales, ilustradores y decenas de escritores provenientes de toda la región centroamericana.",
          "Durante las jornadas culturales programadas, la ciudadanía disfrutó de recitales poéticos, conversatorios sobre la narrativa contemporánea y firmas de libros. Destacados novelistas locales compartieron mesa con jóvenes autores independientes, debatiendo sobre el impacto de las tecnologías digitales en la difusión de las letras salvadoreñas y los retos de la edición independiente.",
          "(imagen)",
          "El programa prestó especial atención a la infancia y la juventud, habilitando salas interactivas de lectura animada, talleres de poesía y representaciones de cuentacuentos enfocados en el rescate de mitos y leyendas tradicionales de la tradición oral cuscatleca. Asimismo, se presentaron nuevas colecciones de libros en formato Braille y audiofórmulas inclusivas.",
          "Organizadores y académicos calificaron la feria como un rotundo éxito de asistencia, subrayando que promover la lectura crítica entre líneas constituye un pilar esencial para la construcción de una sociedad más educada, empática y consciente de su rico patrimonio literario e histórico."
        ],
        inlineImages: [
          "https://www.prensalibre.com/wp-content/uploads/2026/04/Feria-del-Libro-en-Guatemala-reune-editoriales-y-promueve-lectura-en-el-Centro-Historico-este-domingo-1.jpeg"
        ]
      },
      {
        id: 17,
        category: "Cultura",
        subCategory: "Memoria Viva",
        title: "Investigación científica analiza formación rocosa relacionada con la historia del Arca de Noé",
        author: "Karina Elizabeth Vela Pineda",
        date: "Miércoles 23 de septiembre de 2026",
        location: "San Salvador, 23 de septiembre de 2026",
        source: "ElSalvador.com, Agencia Anadolu (AA) y Turkish National Geographic Council.",
        mainImg: "https://images.ecestaticos.com/RdCOqVgD392jcfzgtKKjUczWJCs=/0x0:0x0/1200x675/filters:fill(white):format(jpg)/f.elconfidencial.com%2Foriginal%2F430%2F39d%2Fdb7%2F43039ddb7b858fa7658077aba351a772.jpg",
        summary: "Un equipo internacional de científicos realiza investigaciones en una formación rocosa ubicada en Turquía que durante décadas ha sido relacionada popularmente con la historia del Arca de Noé.",
        paragraphs: [
          "Un equipo multidisciplinario integrado por geólogos, arqueólogos y geofísicos de universidades internacionales continúa ejecutando avanzados análisis científicos en la famosa formación geológica de Durupınar, ubicada en las cercanías del monte Ararat en Turquía. Este sitio ha capturado la fascinación mundial desde mediados del siglo XX debido a la particular silueta de la roca, la cual guarda un sorprendente parecido geométrico con la forma de un buque o embarcación de grandes dimensiones.",
          "Las labores de campo recientes han incluido la recolección de muestras de sedimentos mediante perforaciones a diferentes profundidades y el uso de radares de penetración terrestre para mapear la estructura interna de la formación sin alterar el entorno natural. Los científicos buscan determinar con precisión la edad radiométrica de las capas rocosas y analizar la presencia de materia orgánica fósil en el subsuelo.",
          "(imagen)",
          "Los investigadores han remarcado en sus informes preliminares que la meta del estudio es de carácter estrictamente geológico y paleoclimático, buscando explicar la evolución litológica de la región sin pretender validar de forma apresurada mitos o narrativas religiosas. No obstante, reconocen que los resultados de laboratorio aportarán valiosa información sobre la actividad tectónica e hidrológica de la zona durante el Holoceno.",
          "El estudio mantiene expectantes tanto a miembros de la comunidad científica internacional como a historiadores y antropólogos de la religión, quienes consideran el sitio de Durupınar un testimonio fascinante de cómo la memoria viva de la humanidad y la ciencia se entrelazan al estudiar los misterios de la historia antigua."
        ],
        inlineImages: [
          "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcREHu2IoX2XvU00eTWeIISqzBQ6vBj0tIYMzJPkktHXCcMDq5FlgsZANT42&s=10"
        ]
      },
      {
        id: 18,
        category: "Cultura",
        subCategory: "Sonido Propio",
        title: "Orquesta Sinfónica de San Salvador prepara concierto gratuito para cerrar el Mes Cívico",
        author: "Cristian Daniel Portillo Rivera",
        date: "Miércoles 23 de septiembre de 2026",
        location: "San Salvador, 23 de septiembre de 2026",
        source: "ElSalvador.com, Secretaría de Cultura de la Alcaldía de San Salvador Centro y Dirección del Coro Nacional.",
        mainImg: "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/05/orquesta-sinfonica-san-salvador-centro.jpg",
        summary: "La Orquesta Sinfónica de San Salvador ofrecerá una presentación musical el próximo sábado 26 de septiembre como parte de las actividades del Mes Cívico.",
        paragraphs: [
          "Con el firme propósito de cerrar con broche de oro las conmemoraciones patrias del Mes Cívico y llevar la música académica a espacios abiertos de convivencia ciudadana, la Orquesta Sinfónica de San Salvador ofrecerá un magno concierto gratuito. La velada cultural se llevará a cabo el sábado 26 de septiembre, a partir de las 6:00 de la tarde, sobre la 7.ª avenida Sur, frente a las remodeladas plazas del Mercado Central.",
          "El ensamble instrumental, compuesto por más de sesenta músicos profesionales salvadoreños, interpretará un repertorio versátil diseñado para cautivar a asistentes de todas las edades. El programa musical combinará majestuosas oberturas del repertorio clásico universal con arreglos sinfónicos de canciones folclóricas autóctonas como \"Dios Unión Libertad\", \"Las Cortadoras\" y \"El Torito Pinto\".",
          "(imagen)",
          "Autoridades de la Secretaría de Cultura municipal informaron que la actividad contará con un despliegue de seguridad, áreas de asientos accesibles para adultos mayores y pantallas gigantes para que el público disfrute de cada detalle de la ejecución instrumental. Además, se sumará como invitado especial el Coro Juvenil de la capital.",
          "Los organizadores destacaron que democratizar el acceso a la música académica fortalece la identidad cultural en la ciudadanía, brindando espacios de sana recreación familiar donde el 'sonido propio' de nuestra patria resuene con orgullo en el corazón del centro histórico."
        ],
        inlineImages: [
          "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/05/orquesta-sinfonica-san-salvador-centro-1-1024x768.jpg"
        ]
      },
      {
        id: 19,
        category: "Cultura",
        subCategory: "A la Mesa",
        title: "Pueblos vivos celebran feria gastronómica rescatando la cocina ancestral",
        author: "Alejandra Abigail Díaz Molina",
        date: "Jueves 17 de septiembre de 2026",
        location: "Sonsonate, 17 de septiembre de 2026",
        source: "Red de Cultura Gastronómica de El Salvador, Ministerio de Turismo (MITUR) y Alcaldía de Sonsonate.",
        mainImg: "https://scontent.fsal11-1.fna.fbcdn.net/v/t39.99422-6/727519292_1328582795460701_9018018992109558505_n.png?stp=dst-jpg_tt6&cstp=mx2048x1536&ctp=s2048x1536&_nc_cat=111&ccb=1-7&_nc_sid=127cfc&_nc_ohc=Jpe2S7CqnNQQ7kNvwFtfd6a&_nc_oc=AdpGQTWNu4h7XOmZ1aN6kA_vlGT0u9x0enBbw7UZ9KZVC95cwz61MstL1w8IA2CzOxo&_nc_zt=14&_nc_ht=scontent.fsal11-1.fna&_nc_gid=UfwCR_qRtKqwwJFQLk99iw&_nc_ss=7b289&oh=00_AQIeHAVwO5g_a1eA6EF4_A5M9kG8k0ZM61QiKnejqgvXHQ&oe=6ABA74E9",
        summary: "Cocineras e historiadores se dieron cita para elaborar platillos típicos basados en maíz, hierbas autóctonas y métodos tradicionales de cocción en barro.",
        paragraphs: [
          "El riquísimo legado culinario de las comunidades autóctonas de El Salvador fue el protagonista de la Gran Feria Gastronómica de los Pueblos Vivos, celebrada en la plaza central de Sonsonate. El evento reunió a matronas tradicionales, historiadores de la cocina y chefs contemporáneos dedicados a la investigación y preservación de las recetas ancestrales compartidas por generaciones.",
          "Durante la jornada, los visitantes deleitaron sus paladares con platillos elaborados mediante métodos autóctonos de cocción en comales de barro y fuego de leña de conacaste. Entre los preparados más populares destacaron diversas variedades de tamales envueltos en hoja de huerta, sopas sazonadas con chipilín y chaya, atoles de maíz pilado y el tradicional riguua bañado con crema fresca de la zona.",
          "(imagen)",
          "El festival contó con talleres interactivos sobre la molienda artesanal en piedra de curar y el uso medicinal e investigativo de especias nativas como el achiote y el alcapate. Asimismo, historiadores ofrecieron conferencias sobre la evolución de la dieta mesoamericana y la importancia del maíz en las festividades rituales precolombinas.",
          "Representantes del turismo local enfatizaron que sentarse 'a la mesa' para compartir las preparaciones de nuestros antepasados refuerza la identidad colectiva, promueve el consumo de ingredientes locales y dinamiza la economía de las pequeñas productoras agrícolas de las zonas rurales."
        ],
        inlineImages: [
          "https://scontent.fsal11-1.fna.fbcdn.net/v/t39.99422-6/726016421_3091176987739119_1154055678884499366_n.png?stp=dst-jpg_tt6&cstp=mx2048x1536&ctp=s2048x1536&_nc_cat=108&ccb=1-7&_nc_sid=127cfc&_nc_ohc=WOCfPgYpDwcQ7kNvwGy-Hoa&_nc_oc=AdqYiYKsHjyDKliCtEJLcy_tg8xBtp0WNVEi6N8wNrpyFLZWgOLR5sxIbRXzmTnUjgE&_nc_zt=14&_nc_ht=scontent.fsal11-1.fna&_nc_gid=X3OAteTZFmwT8yt5xnhWsQ&_nc_ss=7b289&oh=00_AQJyk9qQiyZ7cr89XjJt_LGH3jyPy5QjyCQvPCvlLbOCDg&oe=6ABA79A1"
        ]
      },
      {
        id: 20,
        category: "Cultura",
        subCategory: "En Vitrina",
        title: "Festival Ícaro continúa con una jornada dedicada al cine salvadoreño",
        author: "Daniel Ernesto Pérez Torres",
        date: "Miércoles 23 de septiembre de 2026",
        location: "San Salvador, 23 de septiembre de 2026",
        source: "ElSalvador.com, Centro Cultural de España en El Salvador (CCEES) y Casa del Arte Salvador.",
        mainImg: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRZ0tp6wNdCFNUeAe-PqZfxqqf85n-XgTuoi-inNCjnnalT24CH0Wj-DKQ&s=10",
        summary: "El Centro Cultural de España en El Salvador continúa con la programación del Festival Ícaro 2026, un ciclo cinematográfico dedicado al cine nacional.",
        paragraphs: [
          "La sala de proyecciones del Centro Cultural de España en El Salvador (CCEES) lució a su máxima capacidad para recibir una nueva sesión del prestigioso Festival Ícaro de Cine Centroamericano. La jornada estuvo dedicada íntegramente a visibilizar y galardonar el talento de cineastas salvadoreños que han desarrollado proyectos audiovisuales durante el último quinquenio.",
          "El programa de exhibición incluyó una variada selección de siete cortometrajes que abarcaron géneros como la animación en stop-motion, el documental social, la ficción dramática y el cine experimental. Obras destacadas como \"Prudencia Ayala, presidenta\", \"La última ave cantora\" y \"Memoria viva: Febe Elizabeth Velásquez\" capturaron el interés del público y la crítica por su impecable factura técnica y narrativa.",
          "(imagen)",
          "Tras las proyecciones, se realizó un conversatorio entre los realizadores, productores y estudiantes de comunicación audiovisual. Durante el espacio de preguntas, los cineastas discutieron sobre los desafíos de la financiación independiente en la región, la búsqueda de un lenguaje estético propio y la importancia de abrir nuevos circuitos de distribución internacional.",
          "Directores del festival resaltaron que poner 'en vitrina' las producciones locales demuestra la madurez del sector cineasta nacional, invitando a la población a respaldar con su asistencia el crecimiento del cine centroamericano."
        ],
        inlineImages: [
          "https://assets.laprensagrafica.com/__export/1788222970698/sites/prensagrafica/img/2026/08/31/xcaro_2.jpeg_20896918.jpeg"
        ]
      },
      {
        id: 21,
        category: "Cultura",
        subCategory: "De Generación en Generación",
        title: "Semana Santa en Chalatenango mantiene vivas las tradiciones religiosas y culturales",
        author: "José Raúl Landaverde Argueta",
        date: "Sábado 19 de septiembre de 2026",
        location: "Chalatenango, 19 de septiembre de 2026",
        source: "Comité de Festejos Tradicionales de Chalatenango, Casa de la Cultura de la Zona Norte e investigaciones de la UDB.",
        mainImg: "https://scontent.fsal2-2.fna.fbcdn.net/v/t39.30808-6/660609836_1607083501423178_576055218210826593_n.jpg?stp=dst-jpg_tt6&cstp=mx2048x1153&ctp=s2048x1153&_nc_cat=104&ccb=1-7&_nc_sid=f727a1&_nc_ohc=oMe-xD9ZyCEQ7kNvwHcfTQe&_nc_oc=Adr9IK7QQ5Y5z2Al8xdWau9mcghwNyia0RIjQ4WWhTiGCtsLB7ktMiB6LT0Mihb5fow&_nc_zt=23&_nc_ht=scontent.fsal2-2.fna&_nc_gid=_UaFNOc-S5z81zBRVcGobg&_nc_ss=7b289&oh=00_AQI1cm5PQrc-79klKQKiXPP2bHCcNkHKRKbGw2G-WLMSfg&oe=6ABA83C8",
        summary: "En Chalatenango, las comunidades participan en actividades como procesiones, Vía Crucis y elaboración de alfombras tradicionales.",
        paragraphs: [
          "Las comunidades del departamento de Chalatenango continúan reafirmando su profunda vocación comunitaria y fe popular mediante la preservación de las solemnes manifestaciones de la Semana Santa. Esta festividad histórico-religiosa constituye uno de los tesoros intangibles más valiosos de la región, uniendo a niños, jóvenes y adultos mayores en torno a actividades tradicionales que han perdurado a lo largo de los siglos.",
          "Durante las jornadas del Jueves y Viernes Santo, las principales arterias de los municipios Chalatecos se convierten en verdaderos lienzos de arte efímero. Decenas de familias trabajan coordinadamente desde la madrugada en la confección de elaboradas alfombras procesionales, utilizando toneladas de aserrín teñido, sal marina, flores silvestres y moldes de madera para plasmar motivos sacros y mensajes de paz social.",
          "(imagen)",
          "La elaboración de las alfombras y el acompañamiento en las procesiones del Vía Crucis y del Santo Entierro son actividades en las que los abuelos transmiten con paciencia a sus nietos las técnicas artesanales de teñido y el significado espiritual de cada rito. Esta dinámica intergeneracional garantiza la continuidad del patrimonio intangible en las zonas rurales.",
          "Líderes comunales y cronistas locales coinciden en que la preservación de estas costumbres fortalece la cohesión vecinal, promueve el turismo cultural consciente y asegura que el legado de nuestros antepasados continúe vivo 'de generación en generación'."
        ],
        inlineImages: [
          "https://scontent.fsal2-2.fna.fbcdn.net/v/t39.30808-6/662876124_1607083311423197_6817667871201854675_n.jpg?stp=dst-jpg_tt6&cstp=mx2048x1153&ctp=s2048x1153&_nc_cat=104&ccb=1-7&_nc_sid=f727a1&_nc_ohc=MElibRks65wQ7kNvwHLNr2q&_nc_oc=AdpS2rPdgROf0uYM7hKgkeMZekbC6guJMQY7zL9L1kYUjycDmwqnb1n_KMu_apcdCSM&_nc_zt=23&_nc_ht=scontent.fsal2-2.fna&_nc_gid=-33ZI4a-STEOLZYw__fx1w&_nc_ss=7b289&oh=00_AQLl4FeDwuAlO2na5-4wR4zjUQvCiQpPNXtOQp-sXZBorw&oe=6ABA7F1B"
        ]
      },

      // ENTRETENIMIENTO (Pantalla y Play)
      {
        id: 22,
        category: "Entretenimiento",
        subCategory: "Luces, Cámara",
        title: "Festival de Cine Internacional estrena las producciones más galardonadas del año",
        author: "Alejandra Abigail Díaz Molina",
        date: "Martes 15 de septiembre de 2026",
        location: "San Salvador, 15 de septiembre de 2026",
        source: "Red de Cineastas Centroamericanos, Teatro Presidente y Festival de Cine de Venecia.",
        mainImg: "https://imgs.elpais.com.uy/dims4/default/7491361/2147483647/strip/true/crop/3999x2499+0+0/resize/1200x750!/format/webp/quality/90/?url=https%3A%2F%2Fel-pais-uruguay-production-web.s3.us-east-1.amazonaws.com%2Fbrightspot%2Ff9%2Fea%2Fa11ce3b448398d1aed195dd805ea%2Fel-festival-de-veneci-20279028.jpg",
        summary: "Salas del país proyectan los largometrajes galardonados en festivales internacionales como Cannes y Venecia durante una semana dedicada al séptimo arte.",
        paragraphs: [
          "La cinefilia salvadoreña celebra por lo alto la llegada del Festival Internacional de Cine 'Luces, Cámara', un evento de proyección continental que proyecta en salas locales las producciones cinematográficas más aclamadas de la temporada. La cartelera del certamen incluye largometrajes y cortometrajes premiados en festivales de primer orden como Cannes, Venecia, San Sebastián y Sundance.",
          "Entre las cintas más esperadas por la audiencia destacan dramas de época, thrillers de autor y documentales sobre conservación planetaria procedentes de Europa, Asia y Latinoamérica. Las proyecciones cuentan con formatos de proyección digital en ultra alta definición y sistemas de audio envolvente para garantizar una experiencia cinematográfica de máxima calidad.",
          "(imagen)",
          "El festival ha habilitado además foros de discusión técnica donde críticos de cine e invitados internacionales analizan la evolución de la narrativa audiovisual, el uso de la iluminación natural en el rodaje y la dirección de actores en producciones de presupuesto independiente. Cientos de estudiantes universitarios han participado activamente en estas clases magistrales.",
          "Organizadores manifestaron su entusiasmo por la respuesta del público, subrayando que consolidar festivales de cine internacional en la capital enriquece la oferta de ocio cultural y motiva a las nuevas generaciones de realizadores locales a seguir creando historias con estándares internacionales."
        ],
        inlineImages: [
          "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRKYtlR_3tTFzKa4kzmCIjIqFv6kQmycKXq_LQkMTfD8f7gLhZ2V7vW0S7_&s=10"
        ]
      },
      {
        id: 23,
        category: "Entretenimiento",
        subCategory: "Play Directo",
        title: "“Yo Me Llamo All Stars” reúne nuevamente a figuras destacadas de la televisión salvadoreña",
        author: "José Raúl Landaverde Argueta",
        date: "Domingo 20 de septiembre de 2026",
        location: "San Salvador, 20 de septiembre de 2026",
        source: "Telecorporación Salvadoreña (TCS), Canal 2 y plataforma TCS GO.",
        mainImg: "https://d21tucfpen3j82.cloudfront.net/wp-content/uploads/2026/07/20100831/Yo-me-llamo-All-Stars-muy-pronto-por-Canal-2.webp",
        summary: "El programa “Yo Me Llamo All Stars” llegó a la televisión salvadoreña con una edición especial que reúne a los mejores imitadores de temporadas anteriores.",
        paragraphs: [
          "El formato de entretenimiento más popular de la televisión nacional regresó con una deslumbrante propuesta de producción: \"Yo Me Llamo All Stars\". La gala de estreno, emitida en horario estelar por las pantallas de Canal 2 y la plataforma streaming TCS GO, reunió en un mismo escenario a los imitadores más sobresalientes de las cuatro temporadas anteriores del exitoso certamen de caracterización musical.",
          "La nómina de quince participantes incluye a los ganadores históricos que encarnaron a figuras como Enrique Bunbury, Valentín Elizalde, Chayanne y Eduin Caz, quienes vuelven a someterse a la rigurosa evaluación de la mesa de jueces. El jurado evaluará la evolución en el registro vocal, la caracterización estética y el dominio escénico de cada concursante.",
          "(imagen)",
          "La conducción estelar del programa está a cargo de las reconocidas presentadoras Luciana Sandoval y Larissa Graniello, acompañadas en la zona de camerinos por Henry Urbina. La puesta en escena destaca por un impresionante despliegue de iluminación robótica, escenografía interactiva y un equipo profesional de caracterización, vestuario y maquillaje prostético.",
          "Las interacciones en redes sociales colocaron al programa en las tendencias principales de la noche. \"Yo Me Llamo All Stars\" se consolidó como la opción preferida del público familiar salvadoreño para sus noches de domingo, prometiendo galas repletas de emoción y talento de primer nivel."
        ],
        inlineImages: [
          "https://d21tucfpen3j82.cloudfront.net/wp-content/uploads/2026/09/03162340/El-escenario-vuelve-a-encenderse-con-Yo-Me-Llamo-All-Stars-696x396.webp"
        ]
      },
      {
        id: 24,
        category: "Entretenimiento",
        subCategory: "En Repeat",
        title: "Plataformas digitales registran récord de reproducciones para producciones musicales latinas",
        author: "Cristian Daniel Portillo Rivera",
        date: "Viernes 18 de septiembre de 2026",
        location: "San Salvador, 18 de septiembre de 2026",
        source: "Spotify Charts El Salvador, Apple Music Latin & Billboard Magazine.",
        mainImg: "https://assets.laprensagrafica.com/__export/1787881547820/sites/prensagrafica/img/2026/08/27/inflo_panacover.jpeg_1902800913.jpeg",
        summary: "El consumo de música en streaming en El Salvador muestra una fuerte preferencia por fusiones urbanas, pop tropical e indies emergentes.",
        paragraphs: [
          "Los reportes trimestrales de audiencia emitidos por las principales aplicaciones de streaming de audio reflejan un pico histórico en el consumo de producciones musicales latinas en El Salvador. Según métricas de Spotify Charts y Apple Music, las reproducciones de álbumes de artistas iberoamericanos se incrementaron un 32% en comparación con el mismo periodo del año anterior.",
          "Entre las preferencias del público local destacan las composiciones que fusionan ritmos urbanos con pop tropical, sonidos indies emergentes y elementos tradicionales de la cumbia centroamericana. Los sencillos lanzados recientemente por artistas consagrados y emergentes han logrado posicionarse rápidamente en las listas de reproducción denominadas 'En Repeat', acumulando millones de escuchas en dispositivos móviles.",
          "(imagen)",
          "Analistas de la industria musical señalan que la democratización en la distribución digital ha permitido a grupos independientes salvadoreños y regionales colocar sus producciones en los mismos escaparates globales que las grandes figuras comerciales. Esto ha propiciado un ecosistema musical sumamente dinámico y diverso.",
          "El hábito de escuchar música mediante plataformas digitales se ha consolidado como la principal forma de entretenimiento sonoro entre la juventud salvadoreña, que comparte y viraliza constantemente sus canciones preferidas en redes sociales, impulsando el crecimiento de la industria musical contemporánea."
        ],
        inlineImages: [
          "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcShPAMT1xUqBR-uarEVrs6fcZ3QWe9FXU1WTQSy1rb1UrINNoYprZ6gNk3t&s=10"
        ]
      },
      {
        id: 25,
        category: "Entretenimiento",
        subCategory: "Bajo los Reflectores",
        title: "Luis Miguel anuncia nueva gira para 2027 y crece la expectativa entre sus seguidores",
        author: "Karina Elizabeth Vela Pineda",
        date: "Martes 22 de septiembre de 2026",
        location: "San Salvador, 22 de septiembre de 2026",
        source: "ElSalvador.com, Cárdenas Marketing Network (CMN) y agencia de prensa del artista.",
        mainImg: "https://lapagina.com.sv/wp-content/uploads/2026/09/IMG_3048.jpeg",
        summary: "El cantante mexicano Luis Miguel anunció una nueva gira internacional para 2027, generando expectativa entre sus seguidores salvadoreños.",
        paragraphs: [
          "El legendario intérprete mexicano Luis Miguel volvió a acaparar los reflectores de la prensa internacional al oficializar mediante sus canales oficiales el lanzamiento de su próxima gira de conciertos pautada para el año 2027. La noticia desató una ola de entusiasmo entre su multitudinaria fanaticada en El Salvador, donde el 'Sol de México' mantiene un arraigo musical histórico.",
          "Aun cuando la productora del artista no ha publicado la distribución exacta de las fechas y recintos para la fase centroamericana, expertos del sector de espectáculos prevén que San Salvador sea incluida nuevamente dentro del itinerario continental, dado el rotundo éxito de taquilla alcanzado en sus presentaciones anteriores en el Estadio Cuscatlán.",
          "(imagen)",
          "Luis Miguel ofreció su último espectáculo en suelo cuscatleco en enero de 2024, oportunidad en la que reunió a más de treinta mil espectadores en un show imponente respaldado por mariachi y una nutrida banda de viento. Aquella velada reafirmó el idilio entre la estrella mexicana y el público salvadoreño que ha coreado sus éxitos a lo largo de cuatro décadas.",
          "Representantes de clubes de fans locales manifestaron estar listos para el inicio de las preventas de boletos una vez que la producción revele el calendario definitivo, aguardando con ansias el retorno de una de las voces más portentosas de la música en español."
        ],
        inlineImages: [
          "https://i0.wp.com/mayacomunicacion.com.mx/wp-content/uploads/2026/09/LuisMiguelTour2027-09222026.webp?fit=1200%2C751&ssl=1&w=640"
        ]
      },
      {
        id: 26,
        category: "Entretenimiento",
        subCategory: "Nivel Up",
        title: "Industria global del videojuego presenta avances tecnológicos de nueva generación",
        author: "Daniel Ernesto Pérez Torres",
        date: "Sábado 19 de septiembre de 2026",
        location: "Tokio, Japón, 19 de septiembre de 2026",
        source: "Tokyo Game Show (TGS 2026) Official Press Release, IGN & Eurogamer.",
        mainImg: "https://guslok.com/wp-content/uploads/2026/09/tokyo-game-show-2026-cancela-ultima-jornada-tifon.jpg",
        summary: "Motores gráficos avanzados e integración de renderizado foveal prometen transformar los videojuegos de consola y PC durante el próximo año.",
        paragraphs: [
          "Las firmas líderes de la industria del entretenimiento interactivo se dieron cita en el marco del Tokyo Game Show 2026 para revelar los avances tecnológicos que definirán el futuro inmediato de los videojuegos en consolas de sobremesa y computadoras de alto rendimiento. Las demostraciones técnicas exhibidas impresionaron a los asistentes por su hiperfidelidad gráfica y tiempos de carga imperceptibles.",
          "Entre las innovaciones más comentadas destaca la integración de motores gráficos de nueva generación habilitados con inteligencia artificial para la generación de física de fluidos, iluminación global en tiempo real y expresiones faciales fotorrealistas. Asimismo, la tecnología de renderizado foveal combinado con visores de realidad virtual promete una inmersión sensorial inédita para los jugadores.",
          "(imagen)",
          "Desarrolladores independientes también mostraron propuestas sorprendentes que aprovechan la arquitectura de las consolas híbridas para ofrecer experiencias multijugador fluidas y complejas. Títulos de rol, estrategia y simulación fueron los más galardonados por la prensa especializada durante la convención internacional.",
          "Comunidades de jugadores en El Salvador siguieron las transmisiones en directo del evento, celebrando la optimización de los nuevos motores gráficos que permitirán disfrutar de videojuegos cada vez más complejos, inmersivos y accesibles desde distintas plataformas digitales."
        ],
        inlineImages: [
          "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQvwE8owys2J5ZtcbynxyDT9pfzrGqrcsULcBxbStZpGuhPon1mWmNFSa8_&s=10"
        ]
      },
      {
        id: 27,
        category: "Entretenimiento",
        subCategory: "En Vivo",
        title: "Pablo Alborán regresará a El Salvador con su Global Tour KM0",
        author: "Cristian Daniel Portillo Rivera",
        date: "Miércoles 23 de septiembre de 2026",
        location: "San Salvador, 23 de septiembre de 2026",
        source: "ElSalvador.com, Producciones Salamanca y Warner Music Spain.",
        mainImg: "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/09/pablo-alboran-entradas-el-salvador-2.jpg",
        summary: "El cantante español Pablo Alborán regresará a El Salvador el próximo 29 de septiembre como parte de su gira internacional Global Tour KM0.",
        paragraphs: [
          "El afamado cantautor español Pablo Alborán confirmó su esperado regreso a tierras salvadoreñas como parte de la etapa latinoamericana de su victoriosa gira internacional \"Global Tour KM0\". El espectáculo en vivo está programado para realizarse el próximo martes 29 de septiembre, a las 8:00 de la noche, en el moderno complejo de Salamanca Eventos en San Salvador.",
          "La gira conmemora quince años de trayectoria artística del músico malagueño, quien ha preparado una producción escénica de gran formato que combina acústica de alta fidelidad, un imponente diseño de iluminación y pantallas envolventes. Durante el concierto, Alborán interpretará sus más célebres baladas románticas como \"Solamente Tú\", \"Saturno\", \"Dónde Está el Amor\" y \"Quién\", junto a nuevos temas de su producción discográfica reciente.",
          "(imagen)",
          "Representantes de la empresa productora informaron que el aforo habilitado para el recinto será de aproximadamente dos mil localidades, garantizando una atmósfera íntima y cercana entre el artista y su público. Las entradas puestas a disposición en los sectores Super Fan, Diamante y General registraron una elevada demanda desde las primeras horas de venta.",
          "El concierto de Pablo Alborán se suma a la nutrida agenda de espectáculos internacionales que durante el presente año ha consolidado a San Salvador como una parada indispensable para los grandes exponentes de la música hispana en vivo."
        ],
        inlineImages: [
          "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTO2JEwc-0uHS2n1QczJWWlGKjVkd8nAAb3aCEjuKiWrVISFDQwbWxJppY&s=10"
        ]
      },
      {
        id: 28,
        category: "Entretenimiento",
        subCategory: "Lo Que se Viene",
        title: "Anuncian estrenos cinematográficos y espectáculos masivos programados para 2027",
        author: "Alejandra Abigail Díaz Molina",
        date: "Domingo 20 de septiembre de 2026",
        location: "Los Ángeles, Estados Unidos, 20 de septiembre de 2026",
        source: "The Hollywood Reporter, Variety Magazine y Agencia EFE.",
        mainImg: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS68cATq-5zBb7FWd4RCdyTSSFU89ArvkXDZd7aMTSqzz-V7x_YMCIvS1fN&s=10",
        summary: "Estudios cinematográficos y productoras de eventos revelaron sus calendarios oficiales para el próximo año, prometiendo secuelas esperadas y giras mundiales.",
        paragraphs: [
          "Las principales corporaciones del entretenimiento cinematográfico y productoras de espectáculos masivos revelaron sus calendarios estratégicos de estrenos y giras globales programados para el año 2027. El anuncio generó gran revuelo entre los fanáticos de las superproducciones de Hollywood y la música en vivo, quienes ya anticipan un año repleto de grandes eventos culturales.",
          "En el ámbito del séptimo arte, los estudios confirmaron las fechas de lanzamiento de esperadas secuelas de franquicias de ciencia ficción, superhéroes y sagas animadas. Además, cineastas galardonados presentarán proyectos originales que prometen revolucionar el uso de los efectos visuales y el formato de sonido inmersivo en las salas de cine de todo el mundo.",
          "(imagen)",
          "Por su parte, la industria de la música en vivo anunció el montaje de ambiciosas giras mundiales que recorrerán estadios en América, Europa y Asia. Productoras centroamericanas han iniciado gestiones logísticas para incluir recintos salvadoreños dentro del itinerario regional de destacados artistas pop y agrupaciones de rock.",
          "El panorama de 'lo que se viene' presagia un año de gran dinamismo económico y recreativo para el sector del entretenimiento, invitando al público a mantenerse atento a los anuncios oficiales y al inicio de preventas de los eventos más esperados de la temporada."
        ],
        inlineImages: [
          "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYPDXvRhwDjSX6Eo79Ost3YpE-4MQiD96PA-nXdiYtbIMJbhFU9sdmvE6g&s=10"
        ]
      },

      // SALUD (Bienestar Real)
      {
        id: 29,
        category: "Salud",
        subCategory: "Diagnóstico Claro",
        title: "Especialistas resaltan la importancia de los chequeos preventivos de laboratorio",
        author: "Karina Elizabeth Vela Pineda",
        date: "Lunes 14 de septiembre de 2026",
        location: "San Salvador, 14 de septiembre de 2026",
        source: "Ministerio de Salud de El Salvador (MINSAL), Colegio Médico y Organización Panamericana de la Salud (OPS).",
        mainImg: "https://images.unsplash.com/photo-1579154204601-01588f351e67?auto=format&fit=crop&w=800&q=80",
        summary: "Medir periódicamente niveles de glucosa, perfil lipídico y presión arterial permite detectar de forma temprana patologías crónicas no transmisibles.",
        paragraphs: [
          "En el marco de las acciones de concienciación en salud pública, médicos internistas y patólogos hicieron un llamado enérgico a la población salvadoreña para adoptar la costumbre de realizarse chequeos clínicos y análisis de laboratorio de forma preventiva al menos una vez al año. La indicación busca identificar de manera oportuna alteraciones metabólicas que no suelen presentar síntomas visibles en sus etapas iniciales.",
          "Pruebas de laboratorio fundamentales como el perfil lipídico completo, la medición de glucosa en ayunas, exámenes de función renal y monitoreos de la presión arterial son herramientas diagnósticas clave para detectar a tiempo padecimientos como la diabetes mellitus, la hipertensión arterial y las dislipidemias, enfermedades que constituyen las principales causas de morbilidad en el país.",
          "(imagen)",
          "Contar con un 'diagnóstico claro' en etapas tempranas permite a los profesionales de la salud prescribir intervenciones preventivas orientadas a corregir hábitos de alimentación, incorporar rutinas de ejercicio físico o indicar tratamientos farmacológicos de baja complejidad, reduciendo drásticamente el riesgo de complicaciones cardiovasculares graves a futuro.",
          "Tanto la red del sistema público de salud como laboratorios privados han puesto a disposición de la ciudadanía jornadas de tamizaje preventivo con costos accesibles, reafirmando que la medicina preventiva es la inversión más efectiva para garantizar una vida plena y saludable."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1584515979956-d9f6e5d09982?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 30,
        category: "Salud",
        subCategory: "Buena Vibra",
        title: "Práctica regular del ejercicio al aire libre fortalece la salud cardiovascular y anímica",
        author: "José Raúl Landaverde Argueta",
        date: "Sábado 19 de septiembre de 2026",
        location: "San Salvador, 19 de septiembre de 2026",
        source: "Organización Panamericana de la Salud (OPS), Instituto Nacional de los Deportes (INDES) y Sociedad Salvadoreña de Cardiología.",
        mainImg: "https://images.unsplash.com/photo-1506126613408-eca07ce68773?auto=format&fit=crop&w=800&q=80",
        summary: "Caminar 30 minutos al día en espacios naturales contribuye a regular la presión arterial y estimula la liberación de endorfinas.",
        paragraphs: [
          "Especialistas en medicina deportiva y psicología del bienestar coincidieron en destacar los profundos beneficios biológicos y emocionales que reporta la práctica habitual de actividad física en espacios abiertos. Incorporar al menos treinta minutos diarios de caminata a paso ligero, atletismo recreativo o ciclismo en parques y zonas verdes contribuye significativamente al fortalecimiento del sistema cardiovascular.",
          "A nivel fisiológico, el ejercicio al aire libre ayuda a regular los niveles de presión arterial, mejora la sensibilidad a la insulina y favorece la síntesis natural de vitamina D gracias a la exposición solar moderada. Asimismo, la oxigenación óptima estimula la liberación de endorfinas y serotonina, neurotransmisores fundamentales para combatir el estrés urbano y la fatiga mental.",
          "(imagen)",
          "En San Salvador, espacios públicos como el Parque Saburo Hirao, el Bulevar Monseñor Romero y el Parque Cuscatlán registran una asistencia constante de familias que adoptan este estilo de vida saludable. Grupos comunitarios organizan sesiones gratuitas de yoga, aeróbicos y entrenamiento funcional al aire libre.",
          "Médicos cardiólogos enfatizaron que cultivar una 'buena vibra' a través del movimiento corporal constante es la medicina preventiva más accesible para reducir el sedentarismo, mejorar la calidad del sueño y promover una longevidad plena en todas las etapas de la vida."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1517838277536-f5f99be501cd?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 31,
        category: "Salud",
        subCategory: "Mente en Paz",
        title: "Especialistas promueven la salud mental mediante hábitos de descanso e higiene del sueño",
        author: "Daniel Ernesto Pérez Torres",
        date: "Jueves 17 de septiembre de 2026",
        location: "San Salvador, 17 de septiembre de 2026",
        source: "Asociación Salvadoreña de Psiquiatría, Organización Mundial de la Salud (OMS) y Unidad de Salud Mental del MINSAL.",
        mainImg: "https://images.unsplash.com/photo-1544367567-0f2fcb009e0b?auto=format&fit=crop&w=800&q=80",
        summary: "Mantener rutinas estables de sueño y reducir el uso prolongado de pantallas antes de dormir reduce el estrés y fortalece la resiliencia emocional.",
        paragraphs: [
          "En un entorno social caracterizado por la inmediatez y la hiperconexión digital, profesionales de la salud mental instaron a la ciudadanía a priorizar la higiene del sueño como un hábito indispensable para preservar el equilibrio emocional. Dormir entre siete y ocho horas diarias de forma continua permite la restauración celular, la consolidación de la memoria y la regulación del estado de ánimo.",
          "Psiquiatras y psicólogos advirtieron sobre los efectos nocivos del uso prolongado de dispositivos electrónicos durante las horas previas al descanso. La luz azul emitida por teléfonos inteligentes y pantallas inhibe la producción natural de melatonina, la hormona responsable de conciliar el sueño, provocando insomnio crónico, cuadros de ansiedad e irritabilidad en adultos y adolescentes.",
          "(imagen)",
          "Entre las recomendaciones clave para cultivar una 'mente en paz' se aconseja establecer horarios fijos para ir a la cama, acondicionar la habitación con un ambiente oscuro y silencioso, y practicar ejercicios sencillos de respiración o meditación guiada antes de dormir. Asimismo, se desaconseja el consumo de bebidas estimulantes como el café o energizantes durante la noche.",
          "Instituciones de salud pública continúan impartiendo talleres de salud mental en empresas y centros educativos, recordando a la población que buscar acompañamiento psicológico profesional ante situaciones de angustia o estrés es un acto de valentía y autocuidado fundamental."
        ],
        inlineImages: [
          "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQyAhYItEjFLe27eQpkkrjz5qBhRnWOJGosyXgMTE5EjgooDOJjZO6-_94&s=10"
        ]
      },
      {
        id: 32,
        category: "Salud",
        subCategory: "Plato Consciente",
        title: "Especialistas recomiendan incrementar el consumo de alimentos frescos y de temporada",
        author: "Alejandra Abigail Díaz Molina",
        date: "Martes 8 de septiembre de 2026",
        location: "San Salvador, 8 de septiembre de 2026",
        source: "Instituto de Nutrición de Centro América y Panamá (INCAP), FAO y Asociación Salvadoreña de Nutricionistas.",
        mainImg: "https://images.unsplash.com/photo-1498837167922-ddd27525d352?auto=format&fit=crop&w=800&q=80",
        summary: "Una alimentación variada basada en frutas, verduras y cereales integrales aporta fibra, vitaminas esenciales y antioxidantes para el organismo.",
        paragraphs: [
          "Nutricionistas y dietistas hicieron un enérgico llamado a la población para adoptar la filosofía del 'Plato Consciente', un modelo de alimentación enfocado en seleccionar ingredientes naturales frescos y reducir drásticamente la ingesta de productos altamente ultraprocesados, azúcares refinados y grasas saturadas.",
          "Especialistas del INCAP explicaron que estructurar las comidas diarias incluyendo una mitad de verduras frescas de colores variados, una cuarta parte de proteínas magras y otra cuarta parte de carbohidratos complejos o cereales integrales proporciona los micronutrientes, fibra alimentaria y antioxidantes que el organismo necesita para prevenir enfermedades metabólicas.",
          "(imagen)",
          "Aprovechar la disponibilidad de frutas y hortalizas de temporada cosechadas en los campos salvadoreños no solo garantiza una mayor densidad nutricional en la dieta, sino que favorece la economía doméstica y apoya de forma directa a las familias de pequeños agricultores locales.",
          "Programas comunitarios de nutrición promueven talleres interactivos donde se enseña a preparar menús saludables, económicos y deliciosos, demostrando que comer de forma consciente es una decisión cotidiana que transforma positivamente la salud integral de toda la familia."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1490645935967-10de6ba17061?auto=format&fit=crop&w=800&q=80"
        ]
      },
      {
        id: 33,
        category: "Salud",
        subCategory: "Antes que Después",
        title: "Kilómetros Rosa prepara nueva edición para promover la prevención del cáncer",
        author: "Karina Elizabeth Vela Pineda",
        date: "Martes 22 de septiembre de 2026",
        location: "San Salvador, 22 de septiembre de 2026",
        source: "ElSalvador.com, Fundación Actuar es Vivir (Fundactuar) y Banco Promerica.",
        mainImg: "https://sostenibilidad.sv/wp-content/uploads/2026/09/Banco-Promerica-KM-Rosa-2-1024x576.jpeg",
        summary: "La cuarta edición de Kilómetros Rosa se realizará el próximo domingo 4 de octubre para promover la prevención y detección temprana del cáncer.",
        paragraphs: [
          "Bajo el lema de concienciar a la sociedad salvadoreña sobre la trascendencia de la prevención y el diagnóstico precoz, la Fundación Actuar es Vivir (Fundactuar) y Banco Promerica presentaron oficialmente la cuarta edición de la carrera atlética 'Kilómetros Rosa'. El evento benéfico se llevará a cabo el próximo domingo 4 de octubre, teniendo como punto de salida y meta el centro comercial La Gran Vía.",
          "La convocatoria deportiva invita a participar en circuitos de 1K, 3K, 5K y 10K, ofreciendo alternativas adaptadas para corredores profesionales, aficionados, familias e incluso mascotas. Las inscripciones puestas a disposición del público incluyen un kit deportivo conmemorativo y la oportunidad de contribuir directamente a una causa humanitaria de gran impacto social.",
          "(imagen)",
          "El 100% de los fondos recaudados durante la jornada será destinado a financiar el programa 'Chequeo Rosa', una iniciativa médica integral que otorga mamografías, citologías y consultas ginecológicas gratuitas a miles de mujeres de escasos recursos económicos en comunidades vulnerables del país.",
          "Organizadores recordaron que detectar a tiempo afecciones como el cáncer de mama o cérvix salva vidas, enfatizando que educar e intervenir 'antes que después' es la clave para reducir los índices de mortalidad y brindar esperanza a las familias salvadoreñas."
        ],
        inlineImages: [
          "https://cdn-pro.elsalvador.com/wp-content/uploads/2026/09/Kilometros-Rosa-elsalvador.com-1-1024x768.jpg"
        ]
      },
      {
        id: 34,
        category: "Salud",
        subCategory: "La Salud del Futuro",
        title: "El Salvador podrá adquirir nueva PrEP inyectable para prevenir el VIH",
        author: "Cristian Daniel Portillo Rivera",
        date: "Miércoles 23 de septiembre de 2026",
        location: "San Salvador, 23 de septiembre de 2026",
        source: "ElSalvador.com, Organización Panamericana de la Salud (OPS), OMS y FDA.",
        mainImg: "https://images.unsplash.com/photo-1576091160399-112ba8d25d1d?auto=format&fit=crop&w=800&q=80",
        summary: "El Salvador fue incluido entre los países de América Latina y el Caribe que podrán adquirir lenacapavir, un medicamento inyectable preventivo de aplicación semestral.",
        paragraphs: [
          "En un hito sin precedentes para la salud pública y la prevención epidemiológica en la región, El Salvador fue confirmado en la lista de países beneficiados que podrán adquirir el innovador medicamento lenacapavir a precios preferenciales. La gestión fue concretada gracias a un acuerdo de acceso estratégico liderado por la Organización Panamericana de la Salud (OPS) a través de sus Fondos Rotatorios Regionales.",
          "El lenacapavir representa un salto cualitativo en la profilaxis preexposición (PrEP) contra el Virus de Inmunodeficiencia Humana (VIH). A diferencia de los esquemas de prevención oral que requieren la ingesta diaria de comprimidos, este antirretroviral de acción prolongada se administra mediante una inyección subcutánea únicamente dos veces al año (cada seis meses), garantizando una adherencia terapéutica óptima.",
          "(imagen)",
          "Ensayos clínicos internacionales rigurosos supervisados por la FDA y la OMS demostraron una eficacia superior al 99% en la prevención de la transmisión del virus en poblaciones de alto riesgo. Profesionales de la salud explicaron que el fármaco actúa bloqueando la cápside del virus en múltiples etapas de su ciclo de replicación, impidiendo que infecte las células del sistema inmunitario.",
          "Autoridades sanitarias del país evalúan los protocolos normativos para incorporar gradualmente esta tecnología médica de última generación dentro de los programas nacionales de salud sexual, posicionando a El Salvador a la vanguardia de 'la salud del futuro' en la lucha global por erradicar el VIH."
        ],
        inlineImages: [
          "https://images.unsplash.com/photo-1584308666744-24d5c474f2ae?auto=format&fit=crop&w=800&q=80"
        ]
      }
    ];

    let previousScreen = 'view-home';

    const heroWrapper = document.getElementById('heroParallax');
    const layerContainer = document.getElementById('layerContainer');

    if (heroWrapper && layerContainer) {
      heroWrapper.addEventListener('mousemove', (e) => {
        const rect = heroWrapper.getBoundingClientRect();
        const x = e.clientX - rect.left - (rect.width / 2);
        const y = e.clientY - rect.top - (rect.height / 2);

        const rotateX = (-y / rect.height) * 16;
        const rotateY = (x / rect.width) * 16;

        layerContainer.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
      });

      heroWrapper.addEventListener('mouseleave', () => {
        layerContainer.style.transform = `rotateX(0deg) rotateY(0deg)`;
      });
    }

    function navigateTo(screenId, navElement = null) {
      const currentActive = document.querySelector('.screen-view.active');
      if (currentActive) {
        previousScreen = currentActive.id;
      }

      document.querySelectorAll('.screen-view').forEach(view => view.classList.remove('active'));
      
      const target = document.getElementById(screenId);
      if (target) {
        target.classList.add('active');
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }

      if (navElement) {
        document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
        navElement.classList.add('active');
      }
    }

    function filterBySub(subName) {
      document.getElementById('sectionTitle').innerText = "Subsección: " + subName;
      const filtered = articlesData.filter(a => a.subCategory.toLowerCase() === subName.toLowerCase());
      renderNewsGrid(filtered, 'sectionNewsGrid');
      navigateTo('view-section');
    }

    function navigateToDetail(articleId) {
      const article = articlesData.find(a => a.id === articleId);
      if (!article) return;

      document.getElementById('artCategory').innerText = article.category;
      document.getElementById('artSubCategory').innerText = article.subCategory;
      document.getElementById('artTitle').innerText = article.title;
      document.getElementById('artAuthor').innerText = article.author;
      document.getElementById('artDate').innerText = article.date;
      document.getElementById('artLocation').innerText = article.location;
      document.getElementById('artSource').innerText = article.source;

      const contentBox = document.getElementById('artContent');
      contentBox.innerHTML = '';

      if (article.mainImg) {
        const mainImgEl = document.createElement('img');
        mainImgEl.src = article.mainImg;
        mainImgEl.alt = article.title;
        mainImgEl.className = 'article-img shadow-sm';
        contentBox.appendChild(mainImgEl);
      }

      let imgIdx = 0;
      article.paragraphs.forEach(p => {
        if (p.toLowerCase() === "(imagen)") {
          if (article.inlineImages && article.inlineImages[imgIdx]) {
            const inlineImgEl = document.createElement('img');
            inlineImgEl.src = article.inlineImages[imgIdx];
            inlineImgEl.alt = "Imagen de la noticia";
            inlineImgEl.className = 'article-img shadow-sm my-3';
            contentBox.appendChild(inlineImgEl);
            imgIdx++;
          }
        } else {
          const para = document.createElement('p');
          para.innerText = p;
          contentBox.appendChild(para);
        }
      });

      renderComments(articleId);
      document.getElementById('commentForm').dataset.articleId = articleId;

      navigateTo('view-article');
    }

    function goBackToPrevious() {
      navigateTo(previousScreen || 'view-home');
    }

    function renderNewsGrid(articles, targetContainerId) {
      const container = document.getElementById(targetContainerId);
      if (!container) return;

      if (articles.length === 0) {
        container.innerHTML = `
          <div class="col-12 text-center py-5">
            <div class="alert alert-light border border-dark p-4">
              <i class="bi bi-newspaper fs-1 text-muted"></i>
              <h4 class="mt-3 fw-bold">Sin noticias disponibles</h4>
              <p class="text-muted m-0">Actualmente no existen notas publicadas dentro de esta categoría.</p>
            </div>
          </div>
        `;
        return;
      }

      container.innerHTML = articles.map(art => `
        <div class="col-md-6 col-lg-4">
          <div class="card card-win h-100">
            <div class="card-img-wrapper">
              <img src="${art.mainImg}" alt="${art.title}">
            </div>
            <div class="card-body d-flex flex-column p-4">
              <div class="d-flex gap-1 mb-2 flex-wrap">
                <span class="badge badge-maquilishuat mb-1">${art.category}</span>
                <span class="badge bg-dark text-white mb-1">${art.subCategory}</span>
              </div>
              <h5 class="card-title fw-bold" style="color: var(--color-azul-tinta);">${art.title}</h5>
              <p class="card-text text-muted flex-grow-1 small">${art.summary}</p>
              <div class="border-top pt-2 mt-2 mb-3 text-muted" style="font-size: 0.78rem;">
                <div><i class="bi bi-person"></i> ${art.author}</div>
                <div><i class="bi bi-calendar3"></i> ${art.date}</div>
              </div>
              <button class="btn btn-win-primary align-self-start w-100 text-center" onclick="navigateToDetail(${art.id})">
                Leer Noticia Completa <i class="bi bi-arrow-right"></i>
              </button>
            </div>
          </div>
        </div>
      `).join('');

      const badgeCount = document.getElementById('artCountBadge');
      if (badgeCount && targetContainerId === 'newsGrid') {
        badgeCount.innerText = `${articles.length} Artículos Publicados`;
      }
    }

    function getUsersFromDB() {
      const users = localStorage.getItem('win_users_db_secure');
      return users ? JSON.parse(users) : [
        { id: 67, name: "Daniel Pérez", email: "daniel@win.sv", pass: "1234", interest: "Deportes (En Cancha)" },
        { id: 102, name: "Alejandra Díaz", email: "alejandra@win.sv", pass: "1234", interest: "Cultura (Raíces)" },
        { id: 103, name: "Cristian Portillo", email: "cristian@win.sv", pass: "1234", interest: "Entretenimiento (Pantalla y Play)" },
        { id: 104, name: "Karina Vela", email: "karina@win.sv", pass: "1234", interest: "Salud (Bienestar Real)" },
        { id: 105, name: "Raúl Landaverde", email: "raul@win.sv", pass: "1234", interest: "Economía (Plata y Números)" },
        { id: 106, name: "Edenilson Batres", email: "edenilson@win.sv", pass: "1234", interest: "Cultura (Raíces)" }
      ];
    }

    function saveUsersToDB(usersArray) {
      localStorage.setItem('win_users_db_secure', JSON.stringify(usersArray));
      renderUsersTable();
    }

    function showAuthGifModal(title, subtext, callback) {
      document.getElementById('gifModalTitle').innerText = title;
      document.getElementById('gifModalSub').innerText = subtext;
      
      const modalEl = document.getElementById('authGifModal');
      const bsModal = new bootstrap.Modal(modalEl);
      bsModal.show();

      setTimeout(() => {
        bsModal.hide();
        if (callback) callback();
      }, 3000);
    }

    function handleRegister(e) {
      e.preventDefault();
      const name = document.getElementById('regName').value;
      const email = document.getElementById('regEmail').value;
      const pass = document.getElementById('regPass').value;
      const interest = document.getElementById('regInterest').value;

      const users = getUsersFromDB();
      const existing = users.find(u => u.email.toLowerCase() === email.toLowerCase());

      if (existing) {
        alert('El correo ya está registrado en la base de datos. Por favor inicia sesión.');
        return;
      }

      const newUser = {
        id: Date.now().toString().slice(-4),
        name,
        email,
        pass,
        interest
      };

      users.push(newUser);
      saveUsersToDB(users);

      showAuthGifModal(`¡Bienvenido(a), ${newUser.name}!`, 'Creando tu perfil en W.I.N...', () => {
        setSession(newUser);
        document.getElementById('userForm').reset();
      });
    }

    function handleLogin(e) {
      e.preventDefault();
      const email = document.getElementById('loginEmail').value;
      const pass = document.getElementById('loginPass').value;

      const users = getUsersFromDB();
      const user = users.find(u => u.email.toLowerCase() === email.toLowerCase() && u.pass === pass);

      if (user) {
        showAuthGifModal(`¡Hola de nuevo, ${user.name}!`, 'Iniciando sesión en tu cuenta...', () => {
          setSession(user);
        });
      } else {
        alert('Credenciales incorrectas. Revisa tu correo o contraseña.');
      }
    }

    function setSession(user) {
      localStorage.setItem('win_active_session', JSON.stringify(user));
      updateSessionUI();
    }

    function handleLogout() {
      localStorage.removeItem('win_active_session');
      updateSessionUI();
      alert('Sesión cerrada correctamente.');
    }

    function updateSessionUI() {
      const activeSession = localStorage.getItem('win_active_session');
      const authTabs = document.getElementById('authTabs');
      const authTabContent = document.getElementById('authTabContent');
      const sessionPanel = document.getElementById('activeSessionPanel');
      const navBtn = document.getElementById('navAuthBtn');

      if (activeSession) {
        const user = JSON.parse(activeSession);
        authTabs.classList.add('d-none');
        authTabContent.classList.add('d-none');
        sessionPanel.classList.remove('d-none');

        document.getElementById('sessionUserName').innerText = user.name;
        document.getElementById('sessionUserEmail').innerText = `${user.email} | Interés: ${user.interest}`;
        navBtn.innerHTML = `<i class="bi bi-person-check-fill"></i> ${user.name.split(' ')[0]}`;
      } else {
        authTabs.classList.remove('d-none');
        authTabContent.classList.remove('d-none');
        sessionPanel.classList.add('d-none');
        navBtn.innerHTML = `<i class="bi bi-person-circle"></i> Iniciar Sesión`;
      }
    }

    function renderUsersTable() {
      const tbody = document.getElementById('usersTableBody');
      const users = getUsersFromDB();

      if (!tbody) return;

      tbody.innerHTML = users.map(u => `
        <tr>
          <td><strong>#${u.id}</strong></td>
          <td>${u.name}</td>
          <td>${u.email}</td>
          <td><span class="badge badge-maquilishuat">${u.interest}</span></td>
        </tr>
      `).join('');
    }

    function getCommentsFromDB() {
      const comments = localStorage.getItem('win_comments_db');
      return comments ? JSON.parse(comments) : {};
    }

    function renderComments(articleId) {
      const allComments = getCommentsFromDB();
      const list = document.getElementById('commentsList');
      const articleComments = allComments[articleId] || [];

      if (articleComments.length === 0) {
        list.innerHTML = `<p class="text-muted small">No hay comentarios aún. ¡Sé el primero en opinar!</p>`;
        return;
      }

      list.innerHTML = articleComments.map(c => `
        <div class="p-3 mb-2 border border-dark bg-white">
          <strong style="color: var(--color-azul-tinta);"><i class="bi bi-person-circle"></i> ${c.user}</strong>
          <p class="mb-0 mt-1 small">${c.text}</p>
        </div>
      `).join('');
    }

    function saveComment(e) {
      e.preventDefault();
      const articleId = document.getElementById('commentForm').dataset.articleId;
      const user = document.getElementById('commentUser').value;
      const text = document.getElementById('commentText').value;

      const allComments = getCommentsFromDB();
      if (!allComments[articleId]) {
        allComments[articleId] = [];
      }

      allComments[articleId].push({ user, text });
      localStorage.setItem('win_comments_db', JSON.stringify(allComments));

      document.getElementById('commentUser').value = '';
      document.getElementById('commentText').value = '';
      renderComments(articleId);
    }

    window.addEventListener('DOMContentLoaded', () => {
      renderNewsGrid(articlesData, 'newsGrid');
      renderUsersTable();
      updateSessionUI();
    });
  </script>
</body>
</html>
