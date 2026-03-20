<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CannaCiencia — Conocimiento libre sobre Cannabis</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{--gold:#c9a84c;--gold-light:#e8c87a;--green-bright:#52b788;--dark:#0a0c0a;--dark2:#111310;--dark3:#181c17;--text:#e8e0d0;--text-muted:#8a8070}
body{background:var(--dark);color:var(--text);font-family:'Space Mono',monospace;min-height:100vh;overflow-x:hidden}
nav{display:flex;justify-content:space-between;align-items:center;padding:1.5rem 3rem;border-bottom:1px solid rgba(201,168,76,.15);position:sticky;top:0;background:var(--dark);z-index:100}
.logo{font-family:'Cormorant Garamond',serif;font-size:1.6rem;font-weight:300;letter-spacing:.15em;color:var(--gold)}
.logo span{color:var(--green-bright)}
nav ul{display:flex;gap:2rem;list-style:none}
nav a{color:var(--text-muted);text-decoration:none;font-size:.7rem;letter-spacing:.2em;text-transform:uppercase;transition:color .3s}
nav a:hover{color:var(--gold)}
.hero{position:relative;padding:7rem 3rem 5rem;text-align:center;overflow:hidden}
.hero::before{content:'';position:absolute;top:-100px;left:50%;transform:translateX(-50%);width:700px;height:700px;background:radial-gradient(ellipse,rgba(82,183,136,.07) 0%,transparent 70%);pointer-events:none}
.hero>*{position:relative;z-index:1}
.hero-tag{font-size:.65rem;letter-spacing:.35em;color:var(--green-bright);text-transform:uppercase;margin-bottom:1.5rem;display:block}
h1{font-family:'Cormorant Garamond',serif;font-size:clamp(3rem,6vw,5.5rem);font-weight:300;line-height:1.05;margin-bottom:1.5rem}
h1 em{color:var(--gold);font-style:italic}
.hero-sub{font-size:.75rem;color:var(--text-muted);max-width:480px;margin:0 auto 3rem;line-height:2}
.cta-row{display:flex;gap:1rem;justify-content:center;flex-wrap:wrap}
.btn-p{background:var(--gold);color:var(--dark);font-family:'Space Mono',monospace;font-size:.7rem;letter-spacing:.2em;text-transform:uppercase;padding:.9rem 2.2rem;border:none;text-decoration:none;display:inline-block;transition:background .3s}
.btn-p:hover{background:var(--gold-light)}
.btn-o{background:transparent;color:var(--gold);border:1px solid rgba(201,168,76,.4);font-family:'Space Mono',monospace;font-size:.7rem;letter-spacing:.2em;text-transform:uppercase;padding:.9rem 2.2rem;text-decoration:none;display:inline-block;transition:all .3s}
.btn-o:hover{background:rgba(201,168,76,.05);border-color:var(--gold)}
.stats{display:grid;grid-template-columns:repeat(4,1fr);border-top:1px solid rgba(201,168,76,.1);border-bottom:1px solid rgba(201,168,76,.1)}
.stat{padding:2rem;text-align:center;border-right:1px solid rgba(201,168,76,.1)}
.stat:last-child{border-right:none}
.stat-num{font-family:'Cormorant Garamond',serif;font-size:2.8rem;font-weight:300;color:var(--gold);display:block}
.stat-lbl{font-size:.6rem;letter-spacing:.25em;color:var(--text-muted);text-transform:uppercase;margin-top:.3rem;display:block}
.sec{padding:5rem 3rem}
.sec-hdr{display:flex;align-items:baseline;gap:1.5rem;margin-bottom:3rem}
.sec-num{font-size:.65rem;color:var(--green-bright);letter-spacing:.3em}
h2{font-family:'Cormorant Garamond',serif;font-size:2.2rem;font-weight:300}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:1px;background:rgba(201,168,76,.08)}
.card{background:var(--dark2);padding:2rem;position:relative;overflow:hidden;transition:background .3s;cursor:pointer}
.card::after{content:'';position:absolute;bottom:0;left:0;width:100%;height:2px;background:var(--gold);transform:scaleX(0);transform-origin:left;transition:transform .3s}
.card:hover{background:var(--dark3)}
.card:hover::after{transform:scaleX(1)}
.card-num{font-size:.6rem;letter-spacing:.3em;color:var(--green-bright);text-transform:uppercase;margin-bottom:.8rem;display:block}
.card-title{font-family:'Cormorant Garamond',serif;font-size:1.45rem;margin-bottom:.8rem;line-height:1.2}
.card-desc{font-size:.65rem;color:var(--text-muted);line-height:1.9;margin-bottom:1.5rem}
.card-meta{display:flex;gap:.8rem;align-items:center;flex-wrap:wrap}
.badge{font-size:.55rem;letter-spacing:.2em;padding:.3rem .75rem;border:1px solid rgba(82,183,136,.3);color:var(--green-bright);text-transform:uppercase}
.badge-muted{border-color:rgba(138,128,112,.3);color:var(--text-muted)}
.badge-gold{border-color:rgba(201,168,76,.3);color:var(--gold)}
.arrow{margin-left:auto;color:var(--gold);transition:transform .3s}
.card:hover .arrow{transform:translateX(5px)}
.card-featured{background:var(--dark3);border:1px solid rgba(201,168,76,.2);grid-column:1/-1}
.card-featured .card-title{font-size:1.8rem}
/* Parts accordion */
.parts-grid{display:grid;grid-template-columns:1fr;margin-top:1.5rem;border:1px solid rgba(201,168,76,.1)}
.part-item{background:var(--dark2);padding:1rem 1.2rem;display:flex;justify-content:space-between;align-items:center;cursor:pointer;border-bottom:1px solid rgba(201,168,76,.08);transition:background .3s}
.part-item:last-child{border-bottom:none}
.part-item:hover,.part-item.open{background:#1c2119}
.part-left{display:flex;flex-direction:column;gap:.3rem}
.part-num{font-size:.55rem;color:var(--text-muted);letter-spacing:.2em;text-transform:uppercase}
.part-name{font-size:.7rem;color:var(--text)}
.part-right{display:flex;align-items:center;gap:1.2rem;flex-shrink:0}
.dl-badge{font-size:.55rem;letter-spacing:.15em;color:var(--gold);border:1px solid rgba(201,168,76,.3);padding:.25rem .6rem}
.toggle-icon{color:var(--gold);font-size:1.1rem;transition:transform .3s;line-height:1}
.part-item.open .toggle-icon{transform:rotate(180deg)}
/* Full content panel */
.part-content{display:none;background:#0d110c;border-bottom:1px solid rgba(201,168,76,.08)}
.part-content.open{display:block}
.part-body{padding:2rem 2.5rem;max-height:600px;overflow-y:auto;scrollbar-width:thin;scrollbar-color:rgba(201,168,76,.3) transparent}
.part-body::-webkit-scrollbar{width:4px}
.part-body::-webkit-scrollbar-thumb{background:rgba(201,168,76,.3);border-radius:2px}
.part-body h3{font-family:'Cormorant Garamond',serif;font-size:1.3rem;font-weight:400;color:var(--gold);margin:1.5rem 0 .8rem;line-height:1.3}
.part-body h3:first-child{margin-top:0}
.part-body h4{font-size:.72rem;color:var(--green-bright);letter-spacing:.15em;text-transform:uppercase;margin:1.2rem 0 .5rem}
.part-body p{font-size:.72rem;color:var(--text-muted);line-height:2;margin-bottom:1rem}
.part-body ul{margin:.5rem 0 1rem 1.2rem}
.part-body li{font-size:.7rem;color:var(--text-muted);line-height:1.9;margin-bottom:.3rem}
.part-body li strong,.part-body p strong{color:var(--text);font-weight:500}
.part-body .nota{background:rgba(82,183,136,.06);border-left:2px solid var(--green-bright);padding:1rem 1.2rem;margin:1rem 0;font-size:.7rem;color:var(--text-muted);line-height:1.9}
.part-body .nota strong{color:var(--green-bright)}
.part-body table{width:100%;border-collapse:collapse;margin:1rem 0;font-size:.65rem}
.part-body th{background:rgba(201,168,76,.08);color:var(--gold);padding:.5rem .8rem;text-align:left;border:1px solid rgba(201,168,76,.12);font-weight:500;letter-spacing:.1em}
.part-body td{padding:.5rem .8rem;border:1px solid rgba(201,168,76,.08);color:var(--text-muted);vertical-align:top}
.part-body .seccion-fin{text-align:center;font-size:.65rem;color:var(--text-muted);letter-spacing:.3em;padding:1.5rem 0 .5rem;border-top:1px solid rgba(201,168,76,.1);margin-top:2rem}
/* Resources */
.resources{display:grid;gap:1px;background:rgba(201,168,76,.08)}
.res-row{background:var(--dark2);display:grid;grid-template-columns:3rem 1fr auto auto;gap:1.5rem;align-items:center;padding:1.3rem 1.5rem;transition:background .3s}
.res-row:hover{background:var(--dark3)}
.res-i{font-size:.6rem;color:var(--text-muted)}
.res-n{font-size:.75rem}
.res-t{font-size:.55rem;letter-spacing:.2em;color:var(--green-bright);text-transform:uppercase}
.res-s{font-size:.6rem;color:var(--text-muted)}
.community{background:var(--dark3);padding:6rem 3rem;text-align:center;border-top:1px solid rgba(201,168,76,.1)}
.community h2{font-size:3.2rem;margin-bottom:1.2rem}
.community p{font-size:.72rem;color:var(--text-muted);max-width:420px;margin:0 auto 2.5rem;line-height:2}
.email-row{display:flex;max-width:420px;margin:0 auto}
.email-row input{flex:1;background:rgba(255,255,255,.05);border:1px solid rgba(201,168,76,.2);border-right:none;padding:.9rem 1rem;color:var(--text);font-family:'Space Mono',monospace;font-size:.7rem;outline:none}
.email-row input::placeholder{color:var(--text-muted)}
.email-row button{background:var(--gold);color:var(--dark);border:none;padding:.9rem 1.5rem;font-family:'Space Mono',monospace;font-size:.7rem;cursor:pointer;transition:background .3s}
.email-row button:hover{background:var(--gold-light)}
footer{padding:2rem 3rem;border-top:1px solid rgba(201,168,76,.1);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:1rem}
.footer-logo{font-family:'Cormorant Garamond',serif;font-size:1.1rem;color:var(--gold)}
.footer-copy{font-size:.6rem;color:var(--text-muted)}
.ig{color:var(--green-bright);text-decoration:none;font-size:.6rem;letter-spacing:.15em}
.ig:hover{color:var(--gold)}
@media(max-width:900px){.stats{grid-template-columns:repeat(2,1fr)}.stat:nth-child(2){border-right:none}.stat:nth-child(3){border-top:1px solid rgba(201,168,76,.1)}}
@media(max-width:700px){nav{padding:1rem 1.5rem}nav ul{display:none}.hero,.sec,.community{padding:3.5rem 1.5rem}h1{font-size:2.8rem}.res-row{grid-template-columns:1fr auto}.res-i,.res-s{display:none}footer{flex-direction:column;text-align:center}.card-featured{grid-column:auto}.part-body{padding:1.5rem}}
</style>
</head>
<body>
 
<nav>
  <div class="logo">Canna<span>Ciencia</span></div>
  <ul>
    <li><a href="#modulos">M&oacute;dulos</a></li>
    <li><a href="#biblioteca">Biblioteca</a></li>
    <li><a href="#herramientas">Herramientas</a></li>
    <li><a href="#comunidad">Comunidad</a></li>
    <li><a href="reel-creator.html" style="color:var(--gold);border:1px solid rgba(201,168,76,.3);padding:.3rem .8rem;border-radius:3px">&#127916; TRAILER</a></li>
  </ul>
</nav>
 
<section class="hero">
  <span class="hero-tag">Conocimiento libre &middot; Cannabis Sativa</span>
  <h1>La ciencia detr&aacute;s<br>de la <em>planta</em></h1>
  <p class="hero-sub">Tratados completos de bot&aacute;nica, taxonom&iacute;a, fisiolog&iacute;a y cultivo del cannabis. Contenido riguroso, abierto a la comunidad.</p>
  <div class="cta-row">
    <a href="#modulos" class="btn-p">Explorar m&oacute;dulos</a>
    <a href="#comunidad" class="btn-o">Unirse a la comunidad</a>
  </div>
</section>
 
<div class="stats">
  <div class="stat"><span class="stat-num">11</span><span class="stat-lbl">M&oacute;dulos</span></div>
  <div class="stat"><span class="stat-num">300+</span><span class="stat-lbl">P&aacute;ginas</span></div>
  <div class="stat"><span class="stat-num">100K+</span><span class="stat-lbl">Palabras</span></div>
  <div class="stat"><span class="stat-num">&infin;</span><span class="stat-lbl">Acceso libre</span></div>
</div>
 
<section class="sec" id="modulos">
  <div class="sec-hdr"><span class="sec-num">01 &mdash;</span><h2>M&oacute;dulos disponibles</h2></div>
  <div class="grid">
 
    <div class="card card-featured">
      <span class="card-num">M&oacute;dulo 01 &mdash; Completo &middot; 8 partes</span>
      <div class="card-title">Bot&aacute;nica y Taxonom&iacute;a de Cannabis Sativa</div>
      <p class="card-desc">Tratado completo de biolog&iacute;a vegetal con rigor universitario. Taxonom&iacute;a, morfolog&iacute;a, anatom&iacute;a, fisiolog&iacute;a y ciclo de vida. ~100,000 palabras. Haz clic en cada parte para leer el contenido completo.</p>
      <div class="card-meta">
        <span class="badge">Disponible</span>
        <span class="badge badge-gold">~100k palabras</span>
        <span class="badge badge-gold">8 partes</span>
      </div>
 
      <div class="parts-grid">
 
        <!-- PARTE 1 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 01</span><span class="part-name">Taxonom&iacute;a &middot; Reino Plantae</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>M&oacute;dulo 1 &mdash; Bot&aacute;nica y Taxonom&iacute;a de Cannabis Sativa</h3>
            <p>Tratado Completo de Biolog&iacute;a Vegetal. <em>Taxonom&iacute;a &bull; Morfolog&iacute;a &bull; Anatom&iacute;a &bull; Fisiolog&iacute;a &bull; Citolog&iacute;a</em></p>
            <h4>Introducci&oacute;n al M&oacute;dulo 1</h4>
            <p>La bot&aacute;nica del cannabis representa mucho m&aacute;s que el simple estudio descriptivo de una planta. Es el fundamento cient&iacute;fico sobre el cual se construyen todas las aplicaciones pr&aacute;cticas: cultivo optimizado, mejoramiento gen&eacute;tico, extracci&oacute;n de compuestos, desarrollo de f&aacute;rmacos, e incluso comprensi&oacute;n de efectos psicoactivos. Sin dominar la biolog&iacute;a fundamental de Cannabis sativa, cualquier conocimiento posterior carece de base s&oacute;lida.</p>
            <p>Este m&oacute;dulo adopta un enfoque riguroso y sistem&aacute;tico, comenzando con la posici&oacute;n del cannabis en el &aacute;rbol de la vida (taxonom&iacute;a y filogenia), progresando a trav&eacute;s de su arquitectura estructural (morfolog&iacute;a y anatom&iacute;a), y culminando en el funcionamiento din&aacute;mico de la planta viva (fisiolog&iacute;a y ciclos de vida).</p>
            <h4>Organizaci&oacute;n del M&oacute;dulo</h4>
            <ul>
              <li><strong>Secci&oacute;n 1.1:</strong> Clasificaci&oacute;n taxon&oacute;mica completa, desde Reino hasta variaci&oacute;n intraespec&iacute;fica</li>
              <li><strong>Secci&oacute;n 1.2:</strong> Morfolog&iacute;a externa &mdash; ra&iacute;ces, tallos, hojas, flores, semillas con detalles anat&oacute;micos</li>
              <li><strong>Secci&oacute;n 1.3:</strong> Anatom&iacute;a microsc&oacute;pica &mdash; tejidos, c&eacute;lulas especializadas, tricomas</li>
              <li><strong>Secci&oacute;n 1.4:</strong> Fisiolog&iacute;a vegetal &mdash; fotos&iacute;ntesis, respiraci&oacute;n, transporte, hormonas</li>
              <li><strong>Secci&oacute;n 1.5:</strong> Ciclo de vida completo &mdash; desde germinaci&oacute;n hasta senescencia</li>
            </ul>
            <div class="nota"><strong>&#128161; Nota sobre profundidad:</strong> Este m&oacute;dulo contiene aproximadamente 100,000 palabras distribuidas en ~300 p&aacute;ginas. Cada concepto se explica con rigor universitario/posgrado, incluyendo datos cuantitativos, referencias a literatura cient&iacute;fica, y conexiones interdisciplinarias.</div>
            <h3>1.1 Taxonom&iacute;a y Sistem&aacute;tica Filogen&eacute;tica</h3>
            <p>La taxonom&iacute;a es la ciencia de nombrar, describir y clasificar organismos. La sistem&aacute;tica moderna combina morfolog&iacute;a cl&aacute;sica con datos moleculares (secuencias de DNA/RNA) para inferir relaciones evolutivas (filogenia). Para Cannabis sativa, la clasificaci&oacute;n taxon&oacute;mica ha sido hist&oacute;ricamente controvertida debido a alta variabilidad fenot&iacute;pica, hibridaci&oacute;n frecuente, y nomenclatura confusa perpetuada por d&eacute;cadas de prohibici&oacute;n que limit&oacute; investigaci&oacute;n acad&eacute;mica seria.</p>
            <h3>1.1.1 Reino Plantae: Fundamentos de Biolog&iacute;a Vegetal</h3>
            <p>Cannabis sativa es inequ&iacute;vocamente una planta &mdash; miembro del Reino Plantae (o Archaeplastida en esquemas taxon&oacute;micos que incorporan an&aacute;lisis gen&oacute;micos extensivos). Comprender qu&eacute; significa &lsquo;ser una planta&rsquo; requiere examinar caracter&iacute;sticas celulares, bioqu&iacute;micas y evolutivas que definen este reino.</p>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 1 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
        <!-- PARTE 2 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 02</span><span class="part-name">Divisi&oacute;n Magnoliophyta hasta Familia</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>1.1.2 Divisi&oacute;n Magnoliophyta: Las Angiospermas</h3>
            <p>Las angiospermas (Magnoliophyta o Anthophyta) constituyen el grupo m&aacute;s diverso y evolutivamente exitoso de plantas terrestres, con aproximadamente 300,000&ndash;400,000 especies descritas, representando ~90% de todas las plantas vasculares. Cannabis sativa pertenece a este grupo dominante, cuyo &eacute;xito evolutivo se atribuye a innovaciones clave en reproducci&oacute;n, transporte vascular y diversidad ecol&oacute;gica.</p>
            <h4>A. Flores Verdaderas: &Oacute;rganos Reproductivos Complejos</h4>
            <p>Las flores son brotes modificados especializados para reproducci&oacute;n sexual. Cannabis, aunque con flores relativamente simples, mantiene todas las caracter&iacute;sticas angiospermas fundamentales.</p>
            <ul>
              <li><strong>Perianto:</strong> Flores masculinas con 5 s&eacute;palos verd&oacute;sos, sin p&eacute;talos. Flores femeninas con br&aacute;cteas modificadas y c&aacute;liz reducido.</li>
              <li><strong>Androceo:</strong> 5 estambres por flor. Filamentos delgados de 2&ndash;4 mm. Anteras bilobuladas con 4 microsporangios totales.</li>
              <li><strong>Gineceo:</strong> Carpelo &uacute;nico. Ovario s&uacute;pero con un &oacute;vulo. Estigmas largos (10&ndash;30 mm) blancos que tornan naranjas al madurar.</li>
            </ul>
            <h4>B. Doble Fertilizaci&oacute;n: Innovaci&oacute;n Exclusiva de Angiospermas</h4>
            <p>La doble fertilizaci&oacute;n es el proceso reproductivo m&aacute;s diagn&oacute;stico y exclusivo de angiospermas. Involucra fusi&oacute;n de ambos gametos masculinos con n&uacute;cleos en el saco embrionario femenino, resultando en embrion diploide y endospermo triploide.</p>
            <h4>Proceso en Cannabis sativa</h4>
            <ul>
              <li><strong>Fase 1 &mdash; Gametofito masculino:</strong> Microsporog&eacute;nesis en anteras &rarr; meiosis &rarr; 4 microsporas haploides. Grano de polen maduro triporado, 20&ndash;25 &micro;m, con exina de esporopolenina.</li>
              <li><strong>Fase 2 &mdash; Gametofito femenino:</strong> Megasporog&eacute;nesis &rarr; saco embrionario de 8 n&uacute;cleos tipo Polygonum. O&oacute;sfera, sin&eacute;rgidas, ant&iacute;podas y 2 n&uacute;cleos polares.</li>
              <li><strong>Fase 3 &mdash; Polinizaci&oacute;n:</strong> Anem&oacute;fila. 500,000&ndash;5,000,000 granos por planta. Tubo pol&iacute;nico crece 1&ndash;2 mm/hora, alcanza &oacute;vulo en 12&ndash;24 horas.</li>
            </ul>
            <div class="nota"><strong>&#128161; Curiosidad celular:</strong> El tubo pol&iacute;nico representa una de las c&eacute;lulas m&aacute;s extraordinarias en biolog&iacute;a vegetal. Puede crecer varios cent&iacute;metros con un di&aacute;metro de ~10 &micro;m, depositando m&aacute;s de 100 ves&iacute;culas secretoras por segundo en la punta.</div>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 2 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
        <!-- PARTE 3 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 03</span><span class="part-name">G&eacute;nero Cannabis &middot; Debate Taxon&oacute;mico</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>1.1.6 G&eacute;nero Cannabis: Historia y Nomenclatura</h3>
            <p>El g&eacute;nero Cannabis ha sido objeto de uno de los debates taxon&oacute;micos m&aacute;s prolongados y complejos en bot&aacute;nica. La controversia central: &iquest;Cannabis constituye un solo g&eacute;nero con una especie altamente variable (monot&iacute;pico), o m&uacute;ltiples especies distintas (polit&iacute;pico)?</p>
            <h4>Descripci&oacute;n Original de Linneo (1753)</h4>
            <p>Carl Linnaeus describi&oacute; Cannabis sativa en Species Plantarum (1753). Nombre del griego &kappa;&alpha;&nu;&nu;&alpha;&beta;&iota;&sigma; (k&aacute;nnabis). &lsquo;Sativa&rsquo; del lat&iacute;n &lsquo;cultivada&rsquo;. Especímenes tipo conservados en el Herbario Linneano (LINN) en Londres.</p>
            <h4>Cannabis indica &mdash; Lamarck (1785)</h4>
            <table>
              <tr><th>Caracter&iacute;stica</th><th>C. sativa (Lamarck)</th><th>C. indica (Lamarck)</th></tr>
              <tr><td>Altura</td><td>Alta (2&ndash;5 m)</td><td>Baja a media (1&ndash;2 m)</td></tr>
              <tr><td>Ramificaci&oacute;n</td><td>Escasa</td><td>Densa, muy ramificada</td></tr>
              <tr><td>Hojas</td><td>Foliolos estrechos</td><td>Foliolos anchos</td></tr>
              <tr><td>Entrenudos</td><td>Largos</td><td>Cortos</td></tr>
              <tr><td>Uso principal</td><td>Fibra, semillas</td><td>Medicina, psicoactivo</td></tr>
            </table>
            <h4>Cannabis ruderalis &mdash; Janischewsky (1924)</h4>
            <ul>
              <li><strong>Tama&ntilde;o:</strong> 30&ndash;80 cm. Tallos delgados, 3&ndash;5 foliolos.</li>
              <li><strong>Autofloraci&oacute;n:</strong> Caracter&iacute;stica m&aacute;s distintiva. Florece por edad (20&ndash;30 d&iacute;as), independiente del fotoper&iacute;odo.</li>
              <li><strong>THC:</strong> Generalmente bajo (&lt;0.5%). Distribuci&oacute;n: Rusia, Siberia, Asia Central.</li>
              <li><strong>Importancia moderna:</strong> Gen(es) de autofloraci&oacute;n introducidos en variedades fotoperi&oacute;dicas creando los populares &lsquo;auto-flowers&rsquo;.</li>
            </ul>
            <h4>Hip&oacute;tesis Monot&iacute;pica de Small y Cronquist (1976)</h4>
            <p>Propusieron unificar todo Cannabis bajo Cannabis sativa L. Argumentos: continuidad morfol&oacute;gica, interfertilidad completa, plasticidad fenot&iacute;pica, y domesticaci&oacute;n reciente (&lt;10,000 a&ntilde;os).</p>
            <div class="nota"><strong>&#128161; Base gen&eacute;tica de la autofloraci&oacute;n:</strong> Estudios moleculares (Toth et al., 2022) identificaron mutaciones en genes ort&oacute;logos a FLOWERING LOCUS T (FT) de Arabidopsis. Variantes en CsFT causan transici&oacute;n floral acelerada independiente del fotoper&iacute;odo.</div>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 3 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
        <!-- PARTE 4 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 04</span><span class="part-name">Morfolog&iacute;a I &middot; Ra&iacute;ces, Tallos, Hojas</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>1.2 Morfolog&iacute;a Externa</h3>
            <p>La morfolog&iacute;a externa estudia la forma, estructura y organizaci&oacute;n visible de la planta completa. Para Cannabis sativa, comprender la morfolog&iacute;a es esencial para identificaci&oacute;n bot&aacute;nica, optimizaci&oacute;n de cultivo, diagn&oacute;stico de problemas de salud vegetal, y reconocimiento de estados fenol&oacute;gicos.</p>
            <h3>1.2.1 Sistema Radicular: Fundamento Subterr&aacute;neo</h3>
            <p>Las ra&iacute;ces de Cannabis sativa constituyen un sistema complejo responsable de anclaje mec&aacute;nico, absorci&oacute;n de agua y nutrientes, almacenamiento de reservas, y s&iacute;ntesis de compuestos se&ntilde;alizadores (citoquininas, giberelinas). El sistema radicular es <strong>pivotante (taproot system)</strong>.</p>
            <h4>Anatom&iacute;a de la Ra&iacute;z Primaria</h4>
            <table>
              <tr><th>Zona de la Ra&iacute;z</th><th>Longitud</th><th>Funci&oacute;n Principal</th></tr>
              <tr><td>Cofia radicular</td><td>0.5&ndash;1 mm</td><td>Protecci&oacute;n del meristemo</td></tr>
              <tr><td>Meristemo apical</td><td>1&ndash;2 mm</td><td>Crecimiento en longitud</td></tr>
              <tr><td>Zona de elongaci&oacute;n</td><td>2&ndash;5 mm</td><td>Extensi&oacute;n de ra&iacute;z</td></tr>
              <tr><td>Zona de maduraci&oacute;n</td><td>5&ndash;20 mm</td><td>Absorci&oacute;n agua/nutrientes</td></tr>
              <tr><td>Zona de ra&iacute;ces laterales</td><td>Variable</td><td>Ramificaci&oacute;n del sistema</td></tr>
            </table>
            <div class="nota"><strong>&#128161; Profundidad m&aacute;xima:</strong> En estudios de campo con c&aacute;&ntilde;amo cultivado en suelos profundos, ra&iacute;ces pivotantes alcanzaron profundidades de 2.5&ndash;3 metros despu&eacute;s de 120 d&iacute;as. En contenedores, la ra&iacute;z queda restringida a 20&ndash;40 cm t&iacute;picamente.</div>
            <h3>1.2.2 Tallos: Arquitectura A&eacute;rea y Soporte</h3>
            <p>El tallo principal cumple funciones estructurales (soporte mec&aacute;nico), de transporte (xilema ascendente, floema descendente), y almacenamiento. La morfolog&iacute;a exhibe variaci&oacute;n notable entre genotipos: formas &lsquo;sativa&rsquo; alargadas vs &lsquo;indica&rsquo; compactas.</p>
            <h4>Ra&iacute;ces Laterales: Red de Absorci&oacute;n</h4>
            <ul>
              <li><strong>Iniciaci&oacute;n:</strong> C&eacute;lulas del periciclo adyacentes a polos de xilema se reprogram para dividirse, formando primordio de ra&iacute;z lateral. Proceso controlado por auxinas.</li>
              <li><strong>Patr&oacute;n de distribuci&oacute;n:</strong> Ra&iacute;ces laterales emergen cada 2&ndash;10 mm dependiendo de condiciones y disponibilidad de nutrientes.</li>
              <li><strong>Arquitectura:</strong> Forman red densa en primeros 30&ndash;60 cm de suelo para m&aacute;xima exploraci&oacute;n de recursos.</li>
            </ul>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 4 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
        <!-- PARTE 5 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 05</span><span class="part-name">Morfolog&iacute;a II &middot; Flores, Tricomas, Semillas</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>1.2.3 Flores y Tricomas</h3>
            <p>Las flores de Cannabis sativa representan las estructuras reproductivas m&aacute;s complejas y econ&oacute;micamente valiosas de la planta.</p>
            <h4>1.2.3.1 Flores Masculinas</h4>
            <table>
              <tr><th>Estructura</th><th>Dimensiones</th><th>Funci&oacute;n</th></tr>
              <tr><td><strong>Perianto (c&aacute;liz)</strong></td><td>3&ndash;5 mm</td><td>5 s&eacute;palos protectores</td></tr>
              <tr><td><strong>Estambres</strong></td><td>5 por flor</td><td>Producci&oacute;n de polen</td></tr>
              <tr><td><strong>Antera</strong></td><td>1&ndash;2 mm</td><td>4 sacos pol&iacute;nicos</td></tr>
              <tr><td><strong>Polen</strong></td><td>20&ndash;25 &micro;m</td><td>Gameto masculino</td></tr>
            </table>
            <h4>1.2.3.2 Flores Femeninas</h4>
            <table>
              <tr><th>Estructura</th><th>Caracter&iacute;sticas</th><th>Importancia</th></tr>
              <tr><td><strong>Br&aacute;ctea</strong></td><td>Hoja modificada resinosa</td><td>M&aacute;xima densidad de tricomas</td></tr>
              <tr><td><strong>Ovario</strong></td><td>Contiene 1 &oacute;vulo</td><td>Desarrollo de semilla</td></tr>
              <tr><td><strong>Estigmas</strong></td><td>10&ndash;30 mm blancos&rarr;naranjas</td><td>Receptivos al polen</td></tr>
              <tr><td><strong>Tricomas</strong></td><td>50&ndash;100 &micro;m</td><td>Producci&oacute;n de cannabinoides</td></tr>
            </table>
            <h4>1.2.3.3 Tricomas Glandulares</h4>
            <div class="nota"><strong>Tricomas capitados con tallo:</strong> Los tricomas capitados con tallo (50&ndash;100 &micro;m) son las f&aacute;bricas qu&iacute;micas principales del cannabis. Cada tricoma contiene c&eacute;lulas secretoras con ret&iacute;culo endoplasm&aacute;tico e aparato de Golgi hiperdesarrollados para bios&iacute;ntesis de cannabinoides y terpenos. La resina se acumula en espacio subcuticular.</div>
            <table>
              <tr><th>Tipo de Tricoma</th><th>Tama&ntilde;o</th><th>Funci&oacute;n Principal</th></tr>
              <tr><td>Bulbosos</td><td>10&ndash;15 &micro;m</td><td>Protecci&oacute;n m&iacute;nima</td></tr>
              <tr><td>Capitados s&eacute;siles</td><td>20&ndash;30 &micro;m</td><td>Cannabinoides moderados</td></tr>
              <tr><td>Capitados con tallo</td><td>50&ndash;100 &micro;m</td><td>M&aacute;xima producci&oacute;n</td></tr>
              <tr><td>Cistol&iacute;ticos</td><td>100&ndash;200 &micro;m</td><td>Protecci&oacute;n f&iacute;sica</td></tr>
            </table>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 5 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
        <!-- PARTE 6 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 06</span><span class="part-name">Anatom&iacute;a Microsc&oacute;pica &middot; Tejidos</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>1.3 Anatom&iacute;a Microsc&oacute;pica</h3>
            <p>La anatom&iacute;a microsc&oacute;pica examina la organizaci&oacute;n interna de los tejidos vegetales a nivel celular. En Cannabis sativa, esta organizaci&oacute;n determina directamente la capacidad de la planta para producir, almacenar y transportar compuestos de inter&eacute;s.</p>
            <h4>Tejidos Vegetales Especializados</h4>
            <ul>
              <li><strong>Tejidos meristem&aacute;ticos:</strong> C&eacute;lulas indiferenciadas con alta capacidad de divisi&oacute;n. Meristemos apicales (crecimiento en longitud) y laterales (crecimiento en grosor).</li>
              <li><strong>Tejidos fundamentales:</strong> Par&eacute;nquima (fotós&iacute;ntesis, reserva), col&eacute;nquima (soporte flexible), escler&eacute;nquima (soporte r&iacute;gido).</li>
              <li><strong>Tejidos vasculares:</strong> Xilema (transporte ascendente de agua y minerales) y floema (transporte de fotoasimilados).</li>
              <li><strong>Tejidos de revestimiento:</strong> Epidermis con c&eacute;lulas especializadas incluyendo estomas y tricomas.</li>
            </ul>
            <h4>C&eacute;lulas Secretoras</h4>
            <p>Las c&eacute;lulas secretoras de los tricomas glandulares poseen ret&iacute;culo endoplasm&aacute;tico liso hiperdesarrollado y abundantes dictiosomas (aparato de Golgi) &mdash; adaptaciones para la intensa bios&iacute;ntesis terpenoide y cannabinoide. La resina se acumula en el espacio subcuticular formando la t&iacute;pica &lsquo;cabeza&rsquo; del tricoma capitado.</p>
            <h4>Estomas y Regulaci&oacute;n H&iacute;drica</h4>
            <p>Cannabis sativa posee estomas principalmente en la cara abaxial (inferior) de las hojas. La densidad estom&aacute;tica var&iacute;a entre 100&ndash;400 estomas/mm&sup2; dependiendo del genotipo y condiciones ambientales. Las c&eacute;lulas guarda regulan la apertura mediadas por ABA (cido absc&iacute;sico) en respuesta a estres h&iacute;drico.</p>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 6 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
        <!-- PARTE 7 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 07</span><span class="part-name">Fisiolog&iacute;a Vegetal &middot; Fotos&iacute;ntesis</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>1.4 Fisiolog&iacute;a Vegetal</h3>
            <p>La fisiolog&iacute;a vegetal estudia los procesos din&aacute;micos que mantienen viva a la planta: captaci&oacute;n de energ&iacute;a, transporte de recursos, regulaci&oacute;n hormonal y respuestas al ambiente.</p>
            <h3>1.4.1 Fotos&iacute;ntesis en Cannabis sativa</h3>
            <p>Cannabis sativa es una planta C3. La fotos&iacute;ntesis ocurre principalmente en c&eacute;lulas del mes&oacute;filo foliar ricas en cloroplastos.</p>
            <h4>Fase Luminosa (Reacciones de Hill)</h4>
            <ul>
              <li><strong>Fotosistema II (PSII):</strong> Absorci&oacute;n de luz a 680 nm. Oxidaci&oacute;n del agua (fotol&iacute;sis): 2H&sub2;O &rarr; 4H&sup+ + 4e&sup- + O&sub2;</li>
              <li><strong>Cadena de transporte electr&oacute;nico:</strong> Generaci&oacute;n de gradiente de protones &rarr; s&iacute;ntesis de ATP v&iacute;a ATP sintasa.</li>
              <li><strong>Fotosistema I (PSI):</strong> Absorci&oacute;n a 700 nm. Producci&oacute;n de NADPH.</li>
            </ul>
            <h4>Fase Oscura (Ciclo de Calvin)</h4>
            <ul>
              <li><strong>Carboxilaci&oacute;n:</strong> RuBisCO cataliza fijaci&oacute;n de CO&sub2; en ribulosa-1,5-bisfosfato (RuBP) &rarr; 2 mol&eacute;culas de 3-fosfoglicerato (3-PGA).</li>
              <li><strong>Reducci&oacute;n:</strong> 3-PGA &rarr; gliceraldeh&iacute;do-3-fosfato (G3P) usando ATP y NADPH.</li>
              <li><strong>Regeneraci&oacute;n:</strong> G3P &rarr; RuBP para continuar el ciclo.</li>
            </ul>
            <h4>Sistema Hormonal</h4>
            <ul>
              <li><strong>Auxinas (AIA):</strong> Elongaci&oacute;n celular, dominancia apical, fototropismo, gravitropismo.</li>
              <li><strong>Giberelinas:</strong> Elongaci&oacute;n del tallo, germinaci&oacute;n, inducci&oacute;n floral en algunas especies.</li>
              <li><strong>Citoquininas:</strong> Divisi&oacute;n celular, retraso de senescencia, promoci&oacute;n de brotaci&oacute;n lateral.</li>
              <li><strong>Etileno:</strong> Maduraci&oacute;n de frutos, abscisi&oacute;n foliar, respuesta a estr&eacute;s mec&aacute;nico.</li>
              <li><strong>&Aacute;cido absc&iacute;sico (ABA):</strong> Cierre estom&aacute;tico, dormancia de semillas, respuesta a estr&eacute;s h&iacute;drico.</li>
            </ul>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 7 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
        <!-- PARTE 8 -->
        <div class="part-item" onclick="togglePart(this)">
          <div class="part-left"><span class="part-num">Parte 08</span><span class="part-name">Ciclo de Vida &middot; Germinaci&oacute;n a Senescencia</span></div>
          <div class="part-right"><span class="dl-badge">DOCX</span><span class="toggle-icon">&#8964;</span></div>
        </div>
        <div class="part-content">
          <div class="part-body">
            <h3>1.5 Ciclo de Vida Completo</h3>
            <p>Cannabis sativa es una planta anual que completa su ciclo de vida en una sola estaci&oacute;n de crecimiento. El ciclo comprende etapas bien definidas con caracter&iacute;sticas fisiológicas y morfológicas distintivas.</p>
            <h4>Etapa 1 &mdash; Germinaci&oacute;n (D&iacute;as 1&ndash;7)</h4>
            <ul>
              <li><strong>Imbibici&oacute;n:</strong> Absorci&oacute;n de agua activa enzimas hidriol&iacute;ticas. Temperatura &oacute;ptima: 22&ndash;25&deg;C.</li>
              <li><strong>Emergencia de rad&iacute;cula:</strong> Primera estructura en emerger, exhibe geotropismo positivo.</li>
              <li><strong>Apertura cotiledonar:</strong> Cotiledones se expanden y comienzan fotos&iacute;ntesis. La pl&aacute;ntula pasa de heterotrofa a aut&oacute;trofa.</li>
            </ul>
            <h4>Etapa 2 &mdash; Fase Vegetativa (Semanas 2&ndash;8+)</h4>
            <ul>
              <li><strong>Crecimiento activo:</strong> Expansi&oacute;n r&aacute;pida de tallos, hojas y sistema radicular.</li>
              <li><strong>Fotoper&iacute;odo:</strong> Requiere m&aacute;s de 18 horas de luz para mantenerse en fase vegetativa.</li>
              <li><strong>Producci&oacute;n de biomasa:</strong> Desarrollo de patr&oacute;n de ramificaci&oacute;n caracter&iacute;stico del genotipo.</li>
            </ul>
            <h4>Etapa 3 &mdash; Floraci&oacute;n (Semanas 8&ndash;20)</h4>
            <ul>
              <li><strong>Iniciaci&oacute;n floral:</strong> Inducida por noches largas (&gt;12 horas oscuridad continua). Mediada por fitocromos.</li>
              <li><strong>Diferenciaci&oacute;n sexual:</strong> Aparici&oacute;n de pre-flores que revelan sexo. Plantas masculinas florecen 1&ndash;2 semanas antes.</li>
              <li><strong>Desarrollo de cogollos:</strong> Acumulaci&oacute;n progresiva de tricomas y cannabinoides en br&aacute;cteas femeninas.</li>
              <li><strong>Madurez:</strong> Estigmas tornan naranjas/marrones. Tricomas capitados: transparentes &rarr; l&eacute;chosos &rarr; &aacute;mbar.</li>
            </ul>
            <h4>Etapa 4 &mdash; Senescencia</h4>
            <p>Tras la polinizaci&oacute;n (o en plantas sinsemilla al final de floraci&oacute;n), la planta entra en senescencia. Degradaci&oacute;n de clorofila, movilizaci&oacute;n de nutrientes hacia semillas, muerte programada de tejidos. Marcador de cosecha &oacute;ptima: 70&ndash;90% de tricomas &aacute;mbar seg&uacute;n preferencia de efecto.</p>
            <div class="nota"><strong>&#128161; Dato clave:</strong> En latitudes medias (40&ndash;50&deg;N), el d&iacute;a natural alcanza 12 horas de oscuridad continua alrededor del equinoccio de oto&ntilde;o (septiembre). Las variedades outdoor han sido seleccionadas para adaptarse a estos ciclos naturales locales.</div>
            <div class="seccion-fin">&#9135;&#9135;&#9135; FIN DE PARTE 8 &#9135;&#9135;&#9135;</div>
          </div>
        </div>
 
      </div><!-- /parts-grid -->
    </div><!-- /card-featured -->
 
    <div class="card"><span class="card-num">M&oacute;dulo 02</span><div class="card-title">Gen&eacute;tica y Cepas</div><p class="card-desc">Fundamentos de gen&eacute;tica vegetal, diferenciaci&oacute;n entre variedades, hibridaci&oacute;n y mejoramiento gen&eacute;tico aplicado.</p><div class="card-meta"><span class="badge badge-muted">Pr&oacute;ximamente</span><span class="arrow">&rarr;</span></div></div>
    <div class="card"><span class="card-num">M&oacute;dulo 03</span><div class="card-title">Cannabinoides y Terpenos</div><p class="card-desc">Qu&iacute;mica de los compuestos activos, rutas de bios&iacute;ntesis, efectos farmacol&oacute;gicos y aplicaciones terap&eacute;uticas.</p><div class="card-meta"><span class="badge badge-muted">Pr&oacute;ximamente</span><span class="arrow">&rarr;</span></div></div>
    <div class="card"><span class="card-num">M&oacute;dulo 04</span><div class="card-title">Cultivo y Agronom&iacute;a</div><p class="card-desc">T&eacute;cnicas de cultivo, gesti&oacute;n de sustratos, nutrici&oacute;n, iluminaci&oacute;n y control de entorno para producci&oacute;n &oacute;ptima.</p><div class="card-meta"><span class="badge badge-muted">Pr&oacute;ximamente</span><span class="arrow">&rarr;</span></div></div>
    <div class="card"><span class="card-num">M&oacute;dulos 05 &mdash; 11</span><div class="card-title">Contenido Avanzado</div><p class="card-desc">Extracci&oacute;n, farmacolog&iacute;a, legislaci&oacute;n, aplicaciones m&eacute;dicas e industria del c&aacute;&ntilde;amo. En desarrollo activo.</p><div class="card-meta"><span class="badge badge-muted">Pr&oacute;ximamente</span><span class="arrow">&rarr;</span></div></div>
  </div>
</section>
 
<section class="sec" id="biblioteca" style="padding-top:0">
  <div class="sec-hdr"><span class="sec-num">02 &mdash;</span><h2>Biblioteca de recursos</h2></div>
  <div class="resources">
    <div class="res-row"><span class="res-i">01</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 1: Taxonom&iacute;a y Reino Plantae</span><span class="res-t">DOCX</span><span class="res-s">~40k palabras</span></div>
    <div class="res-row"><span class="res-i">02</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 2: Divisi&oacute;n Magnoliophyta hasta Familia</span><span class="res-t">DOCX</span><span class="res-s">Disponible</span></div>
    <div class="res-row"><span class="res-i">03</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 3: G&eacute;nero Cannabis &middot; Debate Taxon&oacute;mico</span><span class="res-t">DOCX</span><span class="res-s">Disponible</span></div>
    <div class="res-row"><span class="res-i">04</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 4: Morfolog&iacute;a I &middot; Ra&iacute;ces, Tallos y Hojas</span><span class="res-t">DOCX</span><span class="res-s">Disponible</span></div>
    <div class="res-row"><span class="res-i">05</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 5: Morfolog&iacute;a II &middot; Flores, Tricomas y Semillas</span><span class="res-t">DOCX</span><span class="res-s">Disponible</span></div>
    <div class="res-row"><span class="res-i">06</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 6: Anatom&iacute;a Microsc&oacute;pica y Tejidos</span><span class="res-t">DOCX</span><span class="res-s">Disponible</span></div>
    <div class="res-row"><span class="res-i">07</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 7: Fisiolog&iacute;a Vegetal &middot; Fotos&iacute;ntesis y Hormonas</span><span class="res-t">DOCX</span><span class="res-s">Disponible</span></div>
    <div class="res-row"><span class="res-i">08</span><span class="res-n">M&oacute;dulo 1 &mdash; Parte 8: Ciclo de Vida Completo</span><span class="res-t">DOCX</span><span class="res-s">Disponible</span></div>
  </div>
</section>
 
<section class="sec" id="herramientas" style="padding-top:0">
  <div class="sec-hdr"><span class="sec-num">03 &mdash;</span><h2>Herramientas</h2></div>
  <div class="grid">
 
    <div class="card" onclick="window.location.href='reel-creator.html'" style="border:1px solid rgba(201,168,76,.15)">
      <span class="card-num" style="color:var(--gold)">Trailer Maker</span>
      <div class="card-title">Crea tu Reel Cinem&aacute;tico</div>
      <p class="card-desc">Sube tus fotos y v&iacute;deos, elige tu canci&oacute;n favorita y genera autom&aacute;ticamente un reel al estilo tr&aacute;iler de pel&iacute;cula. Detecci&oacute;n de beats, efectos cinem&aacute;ticos y exportaci&oacute;n incluidos.</p>
      <div class="card-meta">
        <span class="badge badge-gold">Nuevo</span>
        <span class="badge" style="border-color:rgba(201,168,76,.3);color:var(--gold)">Gratuito</span>
        <span class="arrow" style="color:var(--gold)">&rarr;</span>
      </div>
    </div>
 
    <div class="card" style="opacity:.55;cursor:default">
      <span class="card-num">Calendario Lunar</span>
      <div class="card-title">Cultivo por Fases Lunares</div>
      <p class="card-desc">Planifica tus ciclos de cultivo sincronizados con el calendario lunar. Siembra, poda y cosecha en el momento &oacute;ptimo seg&uacute;n la biolog&iacute;a de la planta.</p>
      <div class="card-meta"><span class="badge badge-muted">Pr&oacute;ximamente</span><span class="arrow">&rarr;</span></div>
    </div>
 
    <div class="card" style="opacity:.55;cursor:default">
      <span class="card-num">Identificador</span>
      <div class="card-title">Diagn&oacute;stico Visual de Plantas</div>
      <p class="card-desc">Sube una foto de tu planta y recibe un diagn&oacute;stico autom&aacute;tico de deficiencias, enfermedades o plagas con recomendaciones de correcci&oacute;n.</p>
      <div class="card-meta"><span class="badge badge-muted">Pr&oacute;ximamente</span><span class="arrow">&rarr;</span></div>
    </div>
 
  </div>
</section>
 
 
  <h2>&Uacute;nete a la <em style="color:var(--gold);font-family:'Cormorant Garamond',serif;font-style:italic">comunidad</em></h2>
  <p>Recibe cada nuevo m&oacute;dulo, recurso y publicaci&oacute;n directamente en tu correo. Sin spam. Solo ciencia.</p>
  <div class="email-row">
    <input type="email" placeholder="tu@email.com">
    <button onclick="alert('Gracias! Te avisaremos con cada nuevo modulo.')">Suscribirse</button>
  </div>
</section>
 
<footer>
  <div class="footer-logo">CannaCiencia</div>
  <div style="display:flex;gap:1.5rem;align-items:center;flex-wrap:wrap;justify-content:center">
    <a href="#modulos" class="ig">M&oacute;dulos</a>
    <a href="#biblioteca" class="ig">Biblioteca</a>
    <a href="#herramientas" class="ig">Herramientas</a>
    <a href="reel-creator.html" class="ig" style="color:var(--gold)">&#127916; Trailer Maker</a>
    <a href="https://instagram.com/verde.sin.filtro" class="ig">@verde.sin.filtro</a>
  </div>
  <div class="footer-copy">&copy; 2026 &middot; Conocimiento libre para la comunidad</div>
</footer>
 
<script>
function togglePart(el) {
  var isOpen = el.classList.contains('open');
  // Close all open parts[index.html](https://github.com/user-attachments/files/26140895/index.html)[reel-creator.html](https://github.com/user-attachments/files/26140897/reel-creator.html)

  document.querySelectorAll('.part-item.open').forEach(function(item) {
    item.classList.remove('open');
    item.nextElementSibling.classList.remove('open');
  });
  // If it wasn't open, open it
  if (!isOpen) {
    el.classList.add('open');
    el.nextElementSibling.classList.add('open');
  }
}
</script>
</body>
</html>
 
 
