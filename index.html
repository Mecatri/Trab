<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>P&ID Instrument Inspector & Document Correlator - TG1</title>
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
  <!-- PDF.js for rendering PDF documents inside Canvas -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
  
  <script>
    pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            mono: ['JetBrains Mono', 'monospace'],
          },
          colors: {
            brand: {
              50: '#f0f7ff',
              100: '#e0effe',
              500: '#0284c7',
              600: '#0369a1',
              700: '#075985',
              800: '#0c4a6e',
              900: '#0f172a',
            }
          }
        }
      }
    }
  </script>
  <style>
    body { font-family: 'Inter', sans-serif; }
    .mono { font-family: 'JetBrains Mono', monospace; }
    /* Custom Scrollbar */
    ::-webkit-scrollbar { width: 6px; height: 6px; }
    ::-webkit-scrollbar-track { background: #1e293b; }
    ::-webkit-scrollbar-thumb { background: #475569; border-radius: 3px; }
    ::-webkit-scrollbar-thumb:hover { background: #64748b; }
    
    /* Interactive Hotspot Animation */
    @keyframes pulse-ring {
      0% { transform: scale(0.95); opacity: 0.8; }
      50% { transform: scale(1.15); opacity: 0.4; }
      100% { transform: scale(0.95); opacity: 0.8; }
    }
    .tag-pulse {
      animation: pulse-ring 2.5s infinite ease-in-out;
    }
    .diagram-container {
      cursor: grab;
      user-select: none;
    }
    .diagram-container:active {
      cursor: grabbing;
    }
  </style>
</head>
<body class="bg-slate-950 text-slate-100 h-screen flex flex-col overflow-hidden">

  <!-- TOP HEADER -->
  <header class="bg-slate-900 border-b border-slate-800 px-4 py-3 flex items-center justify-between shrink-0 z-20">
    <div class="flex items-center space-x-3">
      <div class="bg-sky-600 text-white p-2 rounded-lg font-bold flex items-center justify-center shadow-lg shadow-sky-900/40">
        <i class="fa-solid fa-microchip text-xl"></i>
      </div>
      <div>
        <h1 class="font-bold text-lg text-white flex items-center gap-2">
          P&ID Inspector TG1 
          <span class="text-xs bg-sky-950 text-sky-400 border border-sky-800 px-2 py-0.5 rounded-full font-mono">Siemens Sucuriú</span>
        </h1>
        <p class="text-xs text-slate-400">Correlação entre P&ID de Vapor Geral e Lista de Funções de Automação</p>
      </div>
    </div>

    <!-- Navigation Tabs -->
    <div class="flex items-center bg-slate-950 p-1 rounded-xl border border-slate-800 text-sm font-medium">
      <button id="btn-view-diagram" onclick="switchView('diagram')" class="px-4 py-1.5 rounded-lg text-sky-400 bg-slate-800 shadow-sm flex items-center gap-2 transition-all">
        <i class="fa-solid fa-diagram-project"></i> Diagrama Interativo
      </button>
      <button id="btn-view-correlator" onclick="switchView('correlator')" class="px-4 py-1.5 rounded-lg text-slate-400 hover:text-slate-200 flex items-center gap-2 transition-all">
        <i class="fa-solid fa-list-check"></i> Correlação de Documentos
        <span id="badge-missing-count" class="bg-amber-500/20 text-amber-400 text-xs px-1.5 py-0.5 rounded-full font-mono border border-amber-500/30">21 Fora</span>
      </button>
      <button id="btn-view-all" onclick="switchView('all-tags')" class="px-4 py-1.5 rounded-lg text-slate-400 hover:text-slate-200 flex items-center gap-2 transition-all">
        <i class="fa-solid fa-table-list"></i> Todos os Instrumentos
      </button>
    </div>

    <!-- Actions -->
    <div class="flex items-center space-x-2">
      <!-- Upload PDF/Image Button -->
      <label class="bg-sky-600 hover:bg-sky-500 text-white px-3 py-1.5 rounded-lg text-xs font-semibold cursor-pointer flex items-center gap-1.5 transition shadow-md shadow-sky-900/40">
        <i class="fa-solid fa-file-arrow-up"></i> Carregar PDF/Imagem
        <input type="file" id="file-uploader" accept="application/pdf,image/*" onchange="handleFileUpload(event)" class="hidden">
      </label>

      <button onclick="toggleDrawMode()" id="btn-draw-mode" class="bg-slate-800 hover:bg-slate-700 text-slate-300 border border-slate-700 px-3 py-1.5 rounded-lg text-xs font-medium flex items-center gap-1.5 transition">
        <i class="fa-solid fa-vector-square text-sky-400"></i> <span id="draw-mode-label">Desenhar Marcador</span>
      </button>

      <button onclick="openAddInstrumentModal()" class="bg-slate-800 hover:bg-slate-700 text-sky-400 border border-slate-700 px-3 py-1.5 rounded-lg text-xs font-medium flex items-center gap-1.5 transition">
        <i class="fa-solid fa-plus"></i> Novo TAG
      </button>
      <button onclick="exportUserData()" class="bg-slate-800 hover:bg-slate-700 text-slate-300 border border-slate-700 p-2 rounded-lg text-xs transition" title="Exportar Dados">
        <i class="fa-solid fa-download"></i>
      </button>
    </div>
  </header>

  <!-- MAIN CONTENT AREA -->
  <div class="flex-1 flex overflow-hidden relative">

    <!-- VIEW 1: DIAGRAM VIEWER -->
    <div id="view-diagram" class="flex-1 flex overflow-hidden relative">
      
      <!-- Left Sidebar: Filter / Search -->
      <aside class="w-80 bg-slate-900 border-r border-slate-800 flex flex-col shrink-0 z-10">
        <div class="p-3 border-b border-slate-800 space-y-2">
          <div class="relative">
            <i class="fa-solid fa-magnifying-glass absolute left-3 top-2.5 text-slate-500 text-xs"></i>
            <input type="text" id="search-tag" onkeyup="filterSidebarTags()" placeholder="Buscar TAG, KKS ou Descrição..." class="w-full bg-slate-950 border border-slate-800 rounded-lg pl-8 pr-3 py-1.5 text-xs text-slate-200 focus:outline-none focus:border-sky-500">
          </div>
          <div class="flex gap-1 text-[11px]">
            <select id="filter-system" onchange="filterSidebarTags()" class="w-full bg-slate-950 border border-slate-800 rounded-lg px-2 py-1 text-slate-300 focus:outline-none focus:border-sky-500">
              <option value="ALL">Todos os Sistemas</option>
              <option value="MS">Vapor Principal (MS)</option>
              <option value="E1">Extrações & Drenos (E1/LP)</option>
              <option value="TURB">Turbina & Mancais</option>
              <option value="OIL">Óleo Lubrificante & Controle</option>
              <option value="GEN">Gerador</option>
            </select>
            <select id="filter-pid-status" onchange="filterSidebarTags()" class="w-full bg-slate-950 border border-slate-800 rounded-lg px-2 py-1 text-slate-300 focus:outline-none focus:border-sky-500">
              <option value="ALL">Todos P&IDs</option>
              <option value="IN_PID">No P&ID Geral</option>
              <option value="OUT_PID">Em Auxiliares (Fora)</option>
            </select>
          </div>
        </div>

        <div id="sidebar-tag-list" class="flex-1 overflow-y-auto p-2 space-y-1">
          <!-- Dynamically filled -->
        </div>

        <div class="p-2 border-t border-slate-800 text-[11px] text-slate-500 flex justify-between items-center bg-slate-950">
          <span id="sidebar-count">Showing 0 tags</span>
          <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-emerald-500"></span> P&ID Geral</span>
          <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-amber-500"></span> Auxiliares</span>
        </div>
      </aside>

      <!-- Center: Canvas / SVG Diagram -->
      <main class="flex-1 bg-slate-950 flex flex-col relative overflow-hidden">
        
        <!-- Canvas Toolbar -->
        <div class="absolute top-4 left-4 z-10 flex items-center bg-slate-900/90 backdrop-blur border border-slate-800 p-1.5 rounded-xl shadow-xl space-x-1">
          <button onclick="zoomDiagram(0.15)" class="p-2 hover:bg-slate-800 text-slate-300 rounded-lg transition" title="Zoom In"><i class="fa-solid fa-plus"></i></button>
          <button onclick="zoomDiagram(-0.15)" class="p-2 hover:bg-slate-800 text-slate-300 rounded-lg transition" title="Zoom Out"><i class="fa-solid fa-minus"></i></button>
          <button onclick="resetDiagramZoom()" class="p-2 hover:bg-slate-800 text-slate-300 rounded-lg transition text-xs font-mono" title="Reset Zoom">100%</button>
          <div class="h-4 w-px bg-slate-800 my-auto"></div>
          <button onclick="toggleHotspotHighlight()" id="btn-highlight-hotspots" class="px-2 py-1 hover:bg-slate-800 text-sky-400 text-xs font-medium rounded-lg flex items-center gap-1 transition">
            <i class="fa-solid fa-bullseye"></i> Destaques
          </button>

          <!-- PDF Page Selector (Visible when PDF is loaded) -->
          <div id="pdf-page-controls" class="hidden flex items-center space-x-1 pl-2 border-l border-slate-800 text-xs font-mono">
            <button onclick="changePDFPage(-1)" class="p-1 text-slate-400 hover:text-white"><i class="fa-solid fa-chevron-left"></i></button>
            <span id="pdf-page-num" class="text-sky-400 font-bold">1</span>/<span id="pdf-page-count" class="text-slate-400">1</span>
            <button onclick="changePDFPage(1)" class="p-1 text-slate-400 hover:text-white"><i class="fa-solid fa-chevron-right"></i></button>
          </div>
        </div>

        <div class="absolute top-4 right-4 z-10 bg-slate-900/90 backdrop-blur border border-slate-800 px-3 py-1.5 rounded-xl shadow-xl text-xs text-slate-400 flex items-center gap-3">
          <div class="flex items-center gap-1.5">
            <div class="w-3 h-3 rounded bg-sky-500/30 border border-sky-400"></div> No P&ID de Vapor
          </div>
          <div class="flex items-center gap-1.5">
            <div class="w-3 h-3 rounded bg-amber-500/30 border border-amber-400"></div> Em Sistemas Auxiliares
          </div>
        </div>

        <!-- HOVER FLOATING TOOLTIP CARD -->
        <div id="hover-tooltip" class="absolute pointer-events-none z-30 bg-slate-900/95 border border-sky-500/80 shadow-2xl rounded-xl p-3 w-72 backdrop-blur-md hidden transition-all duration-150 transform -translate-x-1/2 -translate-y-full mb-3">
          <div class="flex justify-between items-start border-b border-slate-800 pb-2">
            <div>
              <span id="tooltip-tag" class="font-mono font-bold text-sm text-sky-400">10LBA10CP010</span>
              <p id="tooltip-kks" class="text-[10px] font-mono text-slate-400">11-5051-PI-2002</p>
            </div>
            <span id="tooltip-status" class="px-1.5 py-0.5 text-[9px] font-bold rounded bg-emerald-500/20 text-emerald-400 border border-emerald-500/30">P&ID</span>
          </div>
          <p id="tooltip-desc" class="text-xs text-slate-200 font-medium my-2">MAIN STEAM GATE VALVE INLET PRESSURE</p>
          <div class="space-y-1 text-[11px] font-mono bg-slate-950 p-2 rounded-lg border border-slate-800">
            <div class="flex justify-between"><span class="text-slate-400">Range:</span><span id="tooltip-range" class="text-slate-200 font-bold">0 ... 150 bar</span></div>
            <div class="flex justify-between"><span class="text-slate-400">Sistema:</span><span id="tooltip-system" class="text-sky-300">Vapor Principal</span></div>
          </div>
          <p id="tooltip-note" class="text-[10px] text-amber-300/90 italic mt-2 line-clamp-2">Clique para ver e editar detalhes completos.</p>
        </div>

        <!-- Diagram Viewport / Canvas Container -->
        <div id="diagram-viewport" class="diagram-container flex-1 w-full h-full overflow-hidden flex items-center justify-center relative bg-slate-950">
          <div id="diagram-wrapper" class="transform origin-center transition-transform duration-75 relative">
            
            <!-- Canvas layer for rendering PDF / Uploaded Images -->
            <canvas id="pdf-canvas" class="rounded-2xl shadow-2xl hidden"></canvas>

            <!-- Default Process Flow Diagram SVG -->
            <svg id="pid-svg" width="1200" height="750" viewBox="0 0 1200 750" xmlns="http://www.w3.org/2000/svg" class="bg-slate-900 border border-slate-800 rounded-2xl shadow-2xl">
              <!-- Grid Background -->
              <defs>
                <pattern id="grid" width="30" height="30" patternUnits="userSpaceOnUse">
                  <path d="M 30 0 L 0 0 0 30" fill="none" stroke="#1e293b" stroke-width="0.5"/>
                </pattern>
                <marker id="arrow" viewBox="0 0 10 10" refX="5" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
                  <path d="M 0 0 L 10 5 L 0 10 z" fill="#38bdf8"/>
                </marker>
              </defs>
              <rect width="100%" height="100%" fill="url(#grid)" />

              <!-- TITLE BLOCK / HEADER IN SVG -->
              <rect x="20" y="20" width="380" height="45" rx="8" fill="#0f172a" stroke="#334155" stroke-width="1"/>
              <text x="35" y="42" fill="#38bdf8" font-size="13" font-weight="bold" font-family="Inter">DIAGRAMA DE FLUXO - VAPOR GERAL & TURBO-GERADOR TG1</text>
              <text x="35" y="58" fill="#94a3b8" font-size="10" font-family="Inter">Planta de Sucuriú - Siemens Energy / Arauco</text>

              <!-- EQUIPMENT DRAWINGS -->
              <rect x="50" y="250" width="80" height="180" rx="10" fill="#1e293b" stroke="#0284c7" stroke-width="2"/>
              <text x="90" y="335" fill="#e2e8f0" font-size="12" font-weight="bold" text-anchor="middle">CALDEIRA</text>
              <text x="90" y="350" fill="#38bdf8" font-size="9" text-anchor="middle">Vapor Superaquecido</text>

              <path d="M 130 290 L 250 290 L 250 290 L 400 290" fill="none" stroke="#38bdf8" stroke-width="4" marker-end="url(#arrow)"/>
              <text x="200" y="280" fill="#7dd3fc" font-size="10" font-weight="bold">Vapor Principal (Main Steam)</text>

              <rect x="400" y="240" width="110" height="100" rx="8" fill="#0f172a" stroke="#38bdf8" stroke-width="2" stroke-dasharray="4,2"/>
              <text x="455" y="260" fill="#38bdf8" font-size="10" font-weight="bold" text-anchor="middle">BLOCO ESV / CV</text>
              <polygon points="430,280 450,290 430,300" fill="#ef4444"/>
              <polygon points="470,280 450,290 470,300" fill="#ef4444"/>

              <polygon points="510,240 660,260 660,380 510,400" fill="#1e293b" stroke="#e2e8f0" stroke-width="2"/>
              <text x="585" y="315" fill="#ffffff" font-size="14" font-weight="bold" text-anchor="middle">TURBINA HP</text>
              <text x="585" y="335" fill="#94a3b8" font-size="10" text-anchor="middle">Alta Pressão</text>

              <polygon points="690,250 820,230 820,410 690,390" fill="#1e293b" stroke="#e2e8f0" stroke-width="2"/>
              <text x="755" y="315" fill="#ffffff" font-size="14" font-weight="bold" text-anchor="middle">TURBINA LP</text>
              <text x="755" y="335" fill="#94a3b8" font-size="10" text-anchor="middle">Baixa Pressão</text>

              <rect x="580" y="315" width="370" height="10" fill="#64748b"/>

              <rect x="950" y="260" width="140" height="120" rx="12" fill="#1e293b" stroke="#10b981" stroke-width="2"/>
              <circle cx="1020" cy="320" r="35" fill="#0f172a" stroke="#10b981" stroke-width="2"/>
              <text x="1020" y="325" fill="#10b981" font-size="18" font-weight="bold" text-anchor="middle">G</text>
              <text x="1020" y="395" fill="#a7f3d0" font-size="11" font-weight="bold" text-anchor="middle">GERADOR</text>

              <path d="M 610 373 L 610 520 L 780 520" fill="none" stroke="#f59e0b" stroke-width="3" marker-end="url(#arrow)"/>
              <text x="620" y="470" fill="#fbbf24" font-size="10" font-weight="bold">Extração E1 / LP Header</text>

              <rect x="700" y="580" width="160" height="100" rx="10" fill="#0f172a" stroke="#06b6d4" stroke-width="2"/>
              <path d="M 755 410 L 755 580" fill="none" stroke="#06b6d4" stroke-width="3"/>
              <text x="780" y="625" fill="#38bdf8" font-size="12" font-weight="bold" text-anchor="middle">KONDENSATOR</text>
              <text x="780" y="640" fill="#94a3b8" font-size="10" text-anchor="middle">Condensador Principal</text>

              <rect x="50" y="550" width="360" height="150" rx="12" fill="#0f172a" stroke="#f59e0b" stroke-width="1.5" stroke-dasharray="6,3"/>
              <text x="230" y="575" fill="#f59e0b" font-size="11" font-weight="bold" text-anchor="middle">SISTEMAS AUXILIARES (Lube Oil & Control Oil)</text>
              
              <rect x="70" y="600" width="80" height="70" rx="6" fill="#1e293b" stroke="#f59e0b" stroke-width="1"/>
              <text x="110" y="635" fill="#e2e8f0" font-size="9" text-anchor="middle">Tanque de Óleo</text>

              <rect x="180" y="600" width="80" height="70" rx="6" fill="#1e293b" stroke="#f59e0b" stroke-width="1"/>
              <text x="220" y="635" fill="#e2e8f0" font-size="9" text-anchor="middle">Filtros & Resfriador</text>

              <rect x="290" y="600" width="100" height="70" rx="6" fill="#1e293b" stroke="#ef4444" stroke-width="1"/>
              <text x="340" y="635" fill="#e2e8f0" font-size="9" text-anchor="middle">Bloco Trip Hydraulic</text>

              <!-- HOTSPOTS (OVERLAY INSTRUMENT TAGS) -->
              <g id="hotspots-group">
                <!-- Dynamically generated or static placed SVG groups -->
              </g>

            </svg>
          </div>
        </div>

      </main>

      <!-- Right Drawer: Instrument Details & Interactive Editor Panel -->
      <aside id="detail-drawer" class="w-96 bg-slate-900 border-l border-slate-800 flex flex-col shrink-0 z-20 transition-all duration-300 transform translate-x-0">
        
        <!-- Drawer Header -->
        <div class="p-4 border-b border-slate-800 flex items-center justify-between bg-slate-900">
          <div class="flex items-center gap-2">
            <span id="drawer-status-badge" class="px-2 py-0.5 text-xs font-semibold rounded-md bg-emerald-500/20 text-emerald-400 border border-emerald-500/30">
              No P&ID Geral
            </span>
            <span id="drawer-kks" class="font-mono text-xs text-slate-400">11-5051-PI-2002</span>
          </div>
          <button onclick="deleteCurrentInstrument()" class="text-rose-400 hover:text-rose-300 p-1 rounded-lg hover:bg-slate-800 transition mr-1" title="Excluir TAG">
            <i class="fa-solid fa-trash-can"></i>
          </button>
        </div>

        <!-- Instrument Title -->
        <div class="p-4 border-b border-slate-800 bg-slate-950/60">
          <div class="flex items-center justify-between">
            <h2 id="drawer-tag" class="text-xl font-mono font-bold text-sky-400">10LBA10CP010</h2>
            <span id="drawer-type-icon" class="w-8 h-8 rounded-lg bg-sky-950 border border-sky-800 flex items-center justify-center text-sky-400">
              <i class="fa-solid fa-gauge-high"></i>
            </span>
          </div>
          <p id="drawer-desc" class="text-sm font-medium text-slate-200 mt-1">MAIN STEAM GATE VALVE INLET PRESSURE</p>
        </div>

        <!-- Detail Sub-Tabs -->
        <div class="flex border-b border-slate-800 bg-slate-900 text-xs font-medium">
          <button id="tab-btn-specs" onclick="switchDetailTab('specs')" class="flex-1 py-2.5 text-sky-400 border-b-2 border-sky-500 font-semibold transition">
            Especificações & Alarmes
          </button>
          <button id="tab-btn-edit" onclick="switchDetailTab('edit')" class="flex-1 py-2.5 text-slate-400 hover:text-slate-200 transition flex items-center justify-center gap-1.5">
            <i class="fa-solid fa-pen-to-square"></i> Editar Dados
          </button>
          <button id="tab-btn-comments" onclick="switchDetailTab('comments')" class="flex-1 py-2.5 text-slate-400 hover:text-slate-200 transition flex items-center justify-center gap-1.5">
            Comentários <span id="drawer-comment-badge" class="w-2 h-2 rounded-full bg-sky-500 hidden"></span>
          </button>
        </div>

        <!-- Drawer Content Body -->
        <div class="flex-1 overflow-y-auto p-4 space-y-4">
          
          <!-- TAB 1: SPECS & ALARMS -->
          <div id="tab-content-specs" class="space-y-4">
            
            <div class="bg-slate-950 rounded-xl p-3 border border-slate-800 space-y-2">
              <div class="flex justify-between items-center text-xs">
                <span class="text-slate-400">Faixa de Medição (Range):</span>
                <span id="drawer-range" class="font-mono font-bold text-slate-200">0 ... 150 bar (g)</span>
              </div>
              <div class="flex justify-between items-center text-xs">
                <span class="text-slate-400">Sistema:</span>
                <span id="drawer-system-name" class="font-mono text-sky-300">Vapor Principal</span>
              </div>
              <div class="flex justify-between items-center text-xs">
                <span class="text-slate-400">Documento de Origem:</span>
                <span id="drawer-doc-origin" class="text-slate-300">Pág. 6 - Lista de Funções</span>
              </div>
            </div>

            <!-- Alarm & Trip Threshold Table -->
            <div>
              <h3 class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                <i class="fa-solid fa-triangle-exclamation text-amber-400"></i> Setpoints, Alarmes & Trips
              </h3>
              <div class="bg-slate-950 rounded-xl border border-slate-800 overflow-hidden text-xs">
                <table class="w-full text-left">
                  <thead class="bg-slate-900/80 text-slate-400 border-b border-slate-800 font-mono text-[11px]">
                    <tr>
                      <th class="p-2">Nível</th>
                      <th class="p-2">Valor</th>
                      <th class="p-2">Ação/Trip</th>
                      <th class="p-2">Intertrava</th>
                    </tr>
                  </thead>
                  <tbody id="drawer-alarms-body" class="divide-y divide-slate-800/60 font-mono">
                    <!-- Dynamic -->
                  </tbody>
                </table>
              </div>
            </div>

            <!-- Functional Remarks / Siemens Notes -->
            <div>
              <h3 class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                <i class="fa-solid fa-circle-info text-sky-400"></i> Notas de Automação
              </h3>
              <div id="drawer-siemens-remarks" class="bg-slate-950 p-3 rounded-xl border border-slate-800 text-xs text-slate-300 leading-relaxed font-mono">
                -
              </div>
            </div>

          </div>

          <!-- TAB 2: COMPLETE INSTRUMENT EDITOR -->
          <div id="tab-content-edit" class="space-y-3 text-xs hidden">
            <div class="bg-slate-950 p-3 rounded-xl border border-slate-800 space-y-2">
              <div>
                <label class="block text-slate-400 mb-1 font-medium">TAG Primário:</label>
                <input type="text" id="edit-tag-id" class="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 font-mono text-sky-400 font-bold focus:border-sky-500">
              </div>
              <div>
                <label class="block text-slate-400 mb-1 font-medium">KKS Secundário:</label>
                <input type="text" id="edit-kks" class="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 font-mono text-slate-200 focus:border-sky-500">
              </div>
              <div>
                <label class="block text-slate-400 mb-1 font-medium">Descrição Técnica:</label>
                <input type="text" id="edit-desc" class="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 text-slate-200 focus:border-sky-500">
              </div>
              <div class="grid grid-cols-2 gap-2">
                <div>
                  <label class="block text-slate-400 mb-1 font-medium">Range / Faixa:</label>
                  <input type="text" id="edit-range" class="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 font-mono text-slate-200 focus:border-sky-500">
                </div>
                <div>
                  <label class="block text-slate-400 mb-1 font-medium">Sistema:</label>
                  <select id="edit-system" class="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 text-slate-200 focus:border-sky-500">
                    <option value="MS">Vapor Principal (MS)</option>
                    <option value="E1">Extração E1 & LP</option>
                    <option value="TURB">Turbina & Mancais</option>
                    <option value="OIL">Óleo Lub/Controle</option>
                    <option value="GEN">Gerador Elétrico</option>
                  </select>
                </div>
              </div>
              <div class="pt-2">
                <label class="flex items-center gap-2 cursor-pointer">
                  <input type="checkbox" id="edit-pid-status" class="rounded bg-slate-900 border-slate-800 text-sky-500 focus:ring-0">
                  <span class="text-slate-300">Consta no P&ID de Vapor Geral</span>
                </label>
              </div>
            </div>

            <div>
              <label class="block text-slate-300 font-semibold mb-1">Notas do Fabricante / Automação:</label>
              <textarea id="edit-notes" rows="3" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-2 text-slate-200 font-mono text-xs focus:border-sky-500"></textarea>
            </div>

            <button onclick="saveInstrumentEdits()" class="w-full py-2 bg-sky-600 hover:bg-sky-500 text-white font-semibold rounded-lg transition shadow-md shadow-sky-900/40">
              <i class="fa-solid fa-floppy-disk mr-1"></i> Salvar Alterações
            </button>
          </div>

          <!-- TAB 3: EDITABLE COMMENTS & LOGIC NOTES -->
          <div id="tab-content-comments" class="space-y-4 hidden">
            <div class="bg-slate-950 p-3 rounded-xl border border-slate-800 text-xs text-slate-400">
              <p><i class="fa-solid fa-pen-to-square text-sky-400 mr-1"></i> Observações de campo e comissionamento.</p>
            </div>

            <div>
              <label class="block text-xs font-semibold text-slate-300 mb-1">Status de Verificação:</label>
              <select id="user-status-select" onchange="saveUserComments()" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-2 text-xs text-slate-200 focus:outline-none focus:border-sky-500">
                <option value="NORMAL">✅ Normal / Verificado</option>
                <option value="PENDING">⚠️ Pendente de Calibração</option>
                <option value="MISSING_PID">❓ Não Encontrado no P&ID Físico</option>
                <option value="REVIEW">🔍 Requer Revisão da Automação</option>
              </select>
            </div>

            <div>
              <label class="block text-xs font-semibold text-slate-300 mb-1">Notas Personalizadas:</label>
              <textarea id="user-notes-text" rows="8" oninput="saveUserComments()" placeholder="Digite aqui suas observações sobre a malha, cartão DCS/TCS, calibração..." class="w-full bg-slate-950 border border-slate-800 rounded-xl p-3 text-xs text-slate-200 focus:outline-none focus:border-sky-500 font-mono"></textarea>
            </div>

            <div class="flex justify-between items-center text-[11px] text-slate-500 pt-2 border-t border-slate-800">
              <span id="save-indicator"><i class="fa-solid fa-floppy-disk"></i> Salvo automaticamente</span>
              <button onclick="clearUserComment()" class="text-rose-400 hover:text-rose-300">Limpar Nota</button>
            </div>
          </div>

        </div>

        <!-- Drawer Footer -->
        <div class="p-3 border-t border-slate-800 bg-slate-950 text-xs flex justify-between items-center">
          <button onclick="focusTagOnDiagram(currentSelectedTagId)" class="px-3 py-1.5 bg-sky-600 hover:bg-sky-500 text-white rounded-lg font-medium transition flex items-center gap-1">
            <i class="fa-solid fa-crosshairs"></i> Centralizar no P&ID
          </button>
          <button onclick="closeDrawer()" class="px-3 py-1.5 bg-slate-800 hover:bg-slate-700 text-slate-300 rounded-lg transition">
            Fechar
          </button>
        </div>

      </aside>

    </div>

    <!-- VIEW 2 & VIEW 3 remain available... -->
            <tbody id="correlation-table-body" class="divide-y divide-slate-800/60 font-mono">
              <!-- Dynamic -->
            </tbody>
          </table>
        </div>
      </div>

    </div>

    <!-- VIEW 3: ALL TAGS GRID/LIST VIEW -->
    <div id="view-all-tags" class="flex-1 flex flex-col bg-slate-950 overflow-hidden hidden">
      <div class="p-4 bg-slate-900 border-b border-slate-800 flex items-center justify-between">
        <h2 class="text-base font-bold text-white flex items-center gap-2">
          <i class="fa-solid fa-table-list text-sky-400"></i> Catálogo Completo de Instrumentos TG1
        </h2>
        <span class="text-xs text-slate-400">Exibindo todos os instrumentos cadastrados no banco funcional</span>
      </div>

      <div class="flex-1 overflow-y-auto p-4 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-3" id="all-tags-grid">
        <!-- Dynamic Cards -->
      </div>
    </div>

  </div>

  <!-- ADD CUSTOM INSTRUMENT MODAL -->
  <div id="modal-add-instrument" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm flex items-center justify-center z-50 hidden">
    <div class="bg-slate-900 border border-slate-800 rounded-2xl w-full max-w-lg p-5 shadow-2xl space-y-4">
      <div class="flex justify-between items-center border-b border-slate-800 pb-3">
        <h3 class="text-base font-bold text-white flex items-center gap-2">
          <i class="fa-solid fa-circle-plus text-sky-400"></i> Cadastrar Novo Instrumento
        </h3>
        <button onclick="closeAddInstrumentModal()" class="text-slate-400 hover:text-slate-200">
          <i class="fa-solid fa-xmark text-lg"></i>
        </button>
      </div>

      <form id="form-add-instrument" onsubmit="handleAddInstrument(event)" class="space-y-3 text-xs">
        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block text-slate-300 font-medium mb-1">TAG / KKS Primário *</label>
            <input type="text" id="add-tag" required placeholder="Ex: 10LBA10CP030" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-2 text-slate-200 font-mono focus:border-sky-500">
          </div>
          <div>
            <label class="block text-slate-300 font-medium mb-1">KKS Secundário</label>
            <input type="text" id="add-kks" placeholder="Ex: 11-5051-PI-2003" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-2 text-slate-200 font-mono focus:border-sky-500">
          </div>
        </div>

        <div>
          <label class="block text-slate-300 font-medium mb-1">Descrição Técnico *</label>
          <input type="text" id="add-desc" required placeholder="Ex: HIGH PRESSURE TURBINE INLET TEMP" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-2 text-slate-200 focus:border-sky-500">
        </div>

        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block text-slate-300 font-medium mb-1">Sistema *</label>
            <select id="add-system" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-2 text-slate-200 focus:border-sky-500">
              <option value="MS">Vapor Principal (MS)</option>
              <option value="E1">Extração E1 / LP Header</option>
              <option value="TURB">Turbina HP/LP</option>
              <option value="OIL">Óleo Lubrificante (MAV/MAX)</option>
              <option value="GEN">Gerador Elétrico (MKA/MKD)</option>
            </select>
          </div>
          <div>
            <label class="block text-slate-300 font-medium mb-1">Faixa de Medição (Range)</label>
            <input type="text" id="add-range" placeholder="Ex: 0 ... 100 bar (g)" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-2 text-slate-200 font-mono focus:border-sky-500">
          </div>
        </div>

        <div>
          <label class="block text-slate-300 font-medium mb-1">Consta no P&ID de Vapor Geral?</label>
          <div class="flex gap-4 items-center">
            <label class="flex items-center gap-1.5 cursor-pointer">
              <input type="radio" name="add-pid-status" value="true" checked class="text-sky-500 focus:ring-0">
              <span class="text-slate-300">Sim (No P&ID Geral)</span>
            </label>
            <label class="flex items-center gap-1.5 cursor-pointer">
              <input type="radio" name="add-pid-status" value="false" class="text-sky-500 focus:ring-0">
              <span class="text-slate-300">Não (Sistemas Auxiliares)</span>
            </label>
          </div>
        </div>

        <div class="pt-3 border-t border-slate-800 flex justify-end gap-2">
          <button type="button" onclick="closeAddInstrumentModal()" class="px-4 py-2 bg-slate-800 text-slate-300 rounded-lg hover:bg-slate-700">Cancelar</button>
          <button type="submit" class="px-4 py-2 bg-sky-600 text-white rounded-lg hover:bg-sky-500 font-medium">Cadastrar Instrumento</button>
        </div>
      </form>
    </div>
  </div>

  <!-- JAVASCRIPT LOGIC -->
  <script>
    // INITIAL INSTRUMENT DATABASE (Based on Siemens TG1 Function List & Vapor Geral P&ID)
    const initialInstruments = [
      {
        id: "10LBA10CP010",
        kks: "11-5051-PI-2002",
        desc: "MAIN STEAM GATE VALVE INLET PRESSURE",
        system: "MS",
        systemName: "Vapor Principal (Main Steam)",
        range: "0 ... 150 bar (g)",
        inVaporPID: true,
        page: "Pág. 6",
        x: 200, y: 260, // SVG coordinates on diagram
        alarms: [
          { level: "L1", val: "89 bar", action: "W / S", remark: "Transição SGC Turbina" },
          { level: "H1", val: "106.1 bar", action: "W", remark: "Alerta Pressão Alta" },
          { level: "H2", val: "120 bar", action: "A", remark: "Alarm Max Pressão" }
        ],
        siemensNotes: "Usado para os critérios de vapor principal X4a (10LBA10FT030) e proteção de superaquecimento."
      },
      {
        id: "10LBA10CT010",
        kks: "11-5051-TI-2003",
        desc: "MAIN STEAM GATE VALVE INLET TEMPERATURE",
        system: "MS",
        systemName: "Vapor Principal (Main Steam)",
        range: "0 ... 600 °C",
        inVaporPID: true,
        page: "Pág. 6",
        x: 290, y: 260,
        alarms: [
          { level: "L1", val: "f6", action: "W / S", remark: "Superaquecimento Mínimo" },
          { level: "H1", val: "519 °C", action: "W", remark: "Alerta Temp Alta (TD 3s)" }
        ],
        siemensNotes: "Critério de liberação de abertura da válvula principal X1a e X4a."
      },
      {
        id: "10LBA10CP020",
        kks: "11-5051-PI-2005",
        desc: "EMERGENCY STOP VALVE INLET PRESSURE",
        system: "MS",
        systemName: "Vapor Principal (Main Steam)",
        range: "0 ... 150 bar (g)",
        inVaporPID: true,
        page: "Pág. 6",
        x: 370, y: 260,
        alarms: [
          { level: "L1", val: "89 bar", action: "LIM / S", remark: "Atua na redução do fluxo de vapor" },
          { level: "H1", val: "102 bar", action: "LIM / S", remark: "Atua na abertura de válvulas de sobrecarga" }
        ],
        siemensNotes: "Pressão a montante das válvulas de controle e parada de emergência."
      },
      {
        id: "10LBD10CP930",
        kks: "11-5051-PT-2042",
        desc: "LP HEADER PRESSURE (Coletor de Baixa)",
        system: "E1",
        systemName: "Extração E1 & Coletor LP",
        range: "0 ... 10 bar (g)",
        inVaporPID: true,
        page: "Pág. 7",
        x: 700, y: 500,
        alarms: [
          { level: "C", val: "3.7 - 5.4 bar", action: "C", remark: "Malha de Controle de Pressão LP" },
          { level: "H1", val: "6.0 bar", action: "A / ZHW", remark: "Trip via BRAUN Voter 5" }
        ],
        siemensNotes: "Votação 2oo3 dos transmissores 11-5051-PT-2042-A/B/C."
      },
      {
        id: "10MAC19CT910",
        kks: "11-5051-TT-2030",
        desc: "LP TURBINE EXHAUST STEAM TEMPERATURE",
        system: "TURB",
        systemName: "Turbina LP & Condensador",
        range: "0 ... 200 °C",
        inVaporPID: true,
        page: "Pág. 17",
        x: 780, y: 440,
        alarms: [
          { level: "L1", val: "70 °C", action: "S", remark: "Desliga injeção de condensado na exaustão" },
          { level: "H1", val: "90 °C", action: "S", remark: "Liga injeção de condensado na exaustão" },
          { level: "H3", val: "120 °C", action: "A / ZF", remark: "TRIP Automático da Turbina" }
        ],
        siemensNotes: "Proteção contra superaquecimento da palhetada de exaustão do corpo de baixa pressão."
      },
      {
        id: "10MAV40CP910",
        kks: "11-5051-PI-2627",
        desc: "LUBE OIL PRESSURE (Pressão Geral de Óleo)",
        system: "OIL",
        systemName: "Sistema de Óleo Lubrificante",
        range: "0 ... 10 bar (g)",
        inVaporPID: false, // Fora do P&ID Geral de Vapor
        page: "Pág. 31",
        x: 100, y: 640,
        alarms: [
          { level: "L1", val: "2.2 bar", action: "W / S", remark: "Liga 2ª bomba principal de óleo" },
          { level: "L3", val: "2.0 bar", action: "A / Z", remark: "TRIP da Turbina por baixa pressão de óleo" },
          { level: "L4", val: "1.9 bar", action: "A / S", remark: "Partida de emergência da bomba CC" }
        ],
        siemensNotes: "AUSENTE no P&ID de Vapor Geral. Pertence ao P&ID do Skid de Óleo Lubrificante (11-501-PRC-0011)."
      },
      {
        id: "10MAX41CP910",
        kks: "11-5051-PI-3202",
        desc: "TRIP OIL PRESSURE (Pressão do Óleo de Disparo)",
        system: "OIL",
        systemName: "Óleo de Controle e Disparo",
        range: "0 ... 250 bar (g)",
        inVaporPID: false,
        page: "Pág. 36",
        x: 340, y: 640,
        alarms: [
          { level: "L1", val: "125 bar", action: "W", remark: "Alerta de Pressão Baixa de Óleo de Trip" },
          { level: "L2", val: "90 bar", action: "A / Z", remark: "TRIP de Emergência por Perda de Óleo de Proteção" }
        ],
        siemensNotes: "AUSENTE no P&ID de Vapor Geral. Pertence ao sistema hidráulico do gabinete de proteção local."
      },
      {
        id: "10MKA10CT910",
        kks: "11-5051-TE-2652",
        desc: "GENERATOR STATOR WINDING PHASE U TEMP",
        system: "GEN",
        systemName: "Gerador Elétrico",
        range: "0 ... 200 °C",
        inVaporPID: false,
        page: "Pág. 38",
        x: 1020, y: 320,
        alarms: [
          { level: "H1", val: "126 °C", action: "W", remark: "Alerta Temperatura Alta do Estator" },
          { level: "H2", val: "131 °C", action: "A / Z", remark: "TRIP Elétrico / Abrir Disjuntor" }
        ],
        siemensNotes: "AUSENTE no P&ID de Vapor Geral. Medição interna do estator do gerador."
      },
      {
        id: "10MAD10CS910",
        kks: "11-5051-SI-2601",
        desc: "TURBINE SPEED (Medição de Rotação)",
        system: "TURB",
        systemName: "Turbina & Mancais",
        range: "0 ... 5000 RPM",
        inVaporPID: false,
        page: "Pág. 18",
        x: 520, y: 330,
        alarms: [
          { level: "H1", val: "3960 RPM", action: "A / ZF / ZHW", remark: "Trip por Sobrevelocidade Eletrônica (Braun)" }
        ],
        siemensNotes: "Pickups magnéticos sobre roda dentada do eixo dianteiro."
      },
      {
        id: "10LBD10CG010",
        kks: "11-5051-ZI-2048",
        desc: "EXTRACTION E1 NON-RETN-VLV POSITION",
        system: "E1",
        systemName: "Extração E1 & Coletor LP",
        range: "0 ... 100 %",
        inVaporPID: false,
        page: "Pág. 8",
        x: 610, y: 500,
        alarms: [
          { level: "L1", val: "3.8 %", action: "S", remark: "Ativação do sistema de proteção de contra-fluxo" }
        ],
        siemensNotes: "AUSENTE no P&ID de Vapor Geral. Chave de posição da válvula de retenção de extração."
      }
    ];

    // APPLICATION STATE
    let instruments = [];
    let currentSelectedTagId = "10LBA10CP010";
    let userComments = {}; // Stores localStorage notes
    let zoomLevel = 1;
    let panX = 0, panY = 0;
    let isDragging = false, dragStartX = 0, dragStartY = 0;
    let correlationFilter = 'ALL';

    // INITIALIZATION
    window.onload = function() {
      loadInstruments();
      loadUserComments();
      renderSidebarTags();
      renderHotspotsOnSVG();
      renderCorrelationTable();
      renderAllTagsGrid();
      selectTag("10LBA10CP010");
      setupDiagramPanZoom();
    };

    function loadInstruments() {
      const stored = localStorage.getItem('pid_instruments_db');
      if (stored) {
        instruments = JSON.parse(stored);
      } else {
        instruments = [...initialInstruments];
        saveInstruments();
      }
    }

    function saveInstruments() {
      localStorage.setItem('pid_instruments_db', JSON.stringify(instruments));
    }

    function loadUserComments() {
      const stored = localStorage.getItem('pid_user_comments');
      if (stored) {
        userComments = JSON.parse(stored);
      }
    }

    function saveUserComments() {
      const text = document.getElementById('user-notes-text').value;
      const status = document.getElementById('user-status-select').value;
      
      userComments[currentSelectedTagId] = {
        notes: text,
        status: status,
        updatedAt: new Date().toISOString()
      };
      
      localStorage.setItem('pid_user_comments', JSON.stringify(userComments));
      
      // Update badge indicator
      const badge = document.getElementById('drawer-comment-badge');
      if (text.trim().length > 0) {
        badge.classList.remove('hidden');
      } else {
        badge.classList.add('hidden');
      }

      // Re-render components to reflect status icons
      renderSidebarTags();
      renderCorrelationTable();
    }

    function clearUserComment() {
      document.getElementById('user-notes-text').value = '';
      document.getElementById('user-status-select').value = 'NORMAL';
      saveUserComments();
    }

    // VIEW SWITCHING
    function switchView(viewName) {
      document.getElementById('view-diagram').classList.add('hidden');
      document.getElementById('view-correlator').classList.add('hidden');
      document.getElementById('view-all-tags').classList.add('hidden');

      document.getElementById('btn-view-diagram').className = "px-4 py-1.5 rounded-lg text-slate-400 hover:text-slate-200 transition flex items-center gap-2";
      document.getElementById('btn-view-correlator').className = "px-4 py-1.5 rounded-lg text-slate-400 hover:text-slate-200 transition flex items-center gap-2";
      document.getElementById('btn-view-all').className = "px-4 py-1.5 rounded-lg text-slate-400 hover:text-slate-200 transition flex items-center gap-2";

      if (viewName === 'diagram') {
        document.getElementById('view-diagram').classList.remove('hidden');
        document.getElementById('btn-view-diagram').className = "px-4 py-1.5 rounded-lg text-sky-400 bg-slate-800 shadow-sm flex items-center gap-2 transition-all font-semibold";
      } else if (viewName === 'correlator') {
        document.getElementById('view-correlator').classList.remove('hidden');
        document.getElementById('btn-view-correlator').className = "px-4 py-1.5 rounded-lg text-sky-400 bg-slate-800 shadow-sm flex items-center gap-2 transition-all font-semibold";
        renderCorrelationTable();
      } else if (viewName === 'all-tags') {
        document.getElementById('view-all-tags').classList.remove('hidden');
        document.getElementById('btn-view-all').className = "px-4 py-1.5 rounded-lg text-sky-400 bg-slate-800 shadow-sm flex items-center gap-2 transition-all font-semibold";
        renderAllTagsGrid();
      }
    }

    // SIDEBAR RENDERING & FILTERING
    function renderSidebarTags() {
      const container = document.getElementById('sidebar-tag-list');
      const search = document.getElementById('search-tag').value.toLowerCase();
      const systemFilter = document.getElementById('filter-system').value;
      const pidFilter = document.getElementById('filter-pid-status').value;

      const filtered = instruments.filter(inst => {
        const matchesSearch = inst.id.toLowerCase().includes(search) || 
                              inst.kks.toLowerCase().includes(search) || 
                              inst.desc.toLowerCase().includes(search);
        const matchesSys = systemFilter === 'ALL' || inst.system === systemFilter;
        const matchesPID = pidFilter === 'ALL' || 
                           (pidFilter === 'IN_PID' && inst.inVaporPID) || 
                           (pidFilter === 'OUT_PID' && !inst.inVaporPID);
        return matchesSearch && matchesSys && matchesPID;
      });

      document.getElementById('sidebar-count').innerText = `${filtered.length} de ${instruments.length} TAGs`;

      container.innerHTML = filtered.map(inst => {
        const isSelected = inst.id === currentSelectedTagId;
        const hasNote = userComments[inst.id] && userComments[inst.id].notes.trim().length > 0;
        
        return `
          <div onclick="selectTag('${inst.id}')" class="p-2.5 rounded-xl border transition cursor-pointer flex items-center justify-between ${
            isSelected 
              ? 'bg-sky-950/80 border-sky-500 shadow-lg shadow-sky-950/50' 
              : 'bg-slate-950/60 border-slate-800/80 hover:bg-slate-800/50'
          }">
            <div class="space-y-0.5">
              <div class="flex items-center gap-2">
                <span class="font-mono text-xs font-bold ${isSelected ? 'text-sky-300' : 'text-slate-200'}">${inst.id}</span>
                ${inst.inVaporPID 
                  ? '<span class="w-2 h-2 rounded-full bg-emerald-500" title="Presente no P&ID de Vapor Geral"></span>'
                  : '<span class="w-2 h-2 rounded-full bg-amber-500" title="Em Sistemas Auxiliares"></span>'
                }
              </div>
              <p class="text-[11px] text-slate-400 truncate max-w-[190px]">${inst.desc}</p>
            </div>
            <div class="flex flex-col items-end gap-1">
              <span class="text-[10px] font-mono px-1.5 py-0.5 rounded bg-slate-900 border border-slate-800 text-slate-400">${inst.system}</span>
              ${hasNote ? '<i class="fa-solid fa-comment-dots text-sky-400 text-xs"></i>' : ''}
            </div>
          </div>
        `;
      }).join('');
    }

    function filterSidebarTags() {
      renderSidebarTags();
    }

    // HOTSPOTS ON SVG DIAGRAM
    function renderHotspotsOnSVG() {
      const group = document.getElementById('hotspots-group');
      
      group.innerHTML = instruments.map(inst => {
        if (!inst.x || !inst.y) return ''; // Skip instruments without coordinates

        const isSelected = inst.id === currentSelectedTagId;
        const colorClass = inst.inVaporPID ? '#0284c7' : '#f59e0b'; // Sky for Vapor PID, Amber for Aux

        return `
          <g transform="translate(${inst.x}, ${inst.y})" onclick="selectTag('${inst.id}')" class="cursor-pointer group">
            <!-- Pulsing outer ring -->
            <circle cx="0" cy="0" r="${isSelected ? 18 : 12}" fill="${colorClass}" opacity="0.2" class="tag-pulse"/>
            <!-- Main Badge -->
            <circle cx="0" cy="0" r="${isSelected ? 12 : 9}" fill="${isSelected ? '#38bdf8' : colorClass}" stroke="#ffffff" stroke-width="1.5"/>
            <!-- Icon -->
            <text x="0" y="3" fill="#ffffff" font-size="8" font-weight="bold" text-anchor="middle" font-family="Inter">
              ${inst.id.includes('CP') ? 'P' : inst.id.includes('CT') ? 'T' : 'I'}
            </text>
            <!-- Label Tag -->
            <rect x="-35" y="-28" width="70" height="15" rx="3" fill="#0f172a" stroke="${isSelected ? '#38bdf8' : '#334155'}" stroke-width="1"/>
            <text x="0" y="-18" fill="${isSelected ? '#38bdf8' : '#e2e8f0'}" font-size="8" font-weight="bold" font-family="JetBrains Mono" text-anchor="middle">
              ${inst.id}
            </text>
          </g>
        `;
      }).join('');
    }

    // SELECT TAG & UPDATE DRAWER
    function selectTag(tagId) {
      currentSelectedTagId = tagId;
      const inst = instruments.find(i => i.id === tagId);
      if (!inst) return;

      // Update Drawer Header & Status
      document.getElementById('drawer-tag').innerText = inst.id;
      document.getElementById('drawer-kks').innerText = inst.kks;
      document.getElementById('drawer-desc').innerText = inst.desc;
      document.getElementById('drawer-system-name').innerText = inst.systemName;
      document.getElementById('drawer-range').innerText = inst.range;
      document.getElementById('drawer-doc-origin').innerText = inst.page + " - Lista de Funções";

      const badge = document.getElementById('drawer-status-badge');
      if (inst.inVaporPID) {
        badge.className = "px-2 py-0.5 text-xs font-semibold rounded-md bg-emerald-500/20 text-emerald-400 border border-emerald-500/30";
        badge.innerText = "No P&ID de Vapor Geral";
      } else {
        badge.className = "px-2 py-0.5 text-xs font-semibold rounded-md bg-amber-500/20 text-amber-400 border border-amber-500/30";
        badge.innerText = "Em Sistemas Auxiliares";
      }

      // Render Alarms Table
      const alarmsBody = document.getElementById('drawer-alarms-body');
      if (inst.alarms && inst.alarms.length > 0) {
        alarmsBody.innerHTML = inst.alarms.map(a => `
          <tr class="hover:bg-slate-900/50">
            <td class="p-2 font-bold ${a.level.startsWith('H') ? 'text-amber-400' : 'text-sky-400'}">${a.level}</td>
            <td class="p-2 text-slate-200">${a.val}</td>
            <td class="p-2 text-rose-400 font-bold">${a.action}</td>
            <td class="p-2 text-slate-400 font-sans text-[11px]">${a.remark}</td>
          </tr>
        `).join('');
      } else {
        alarmsBody.innerHTML = `<tr><td colspan="4" class="p-2 text-slate-500 text-center font-sans">Sem setpoints de alarme cadastrados</td></tr>`;
      }

      // Render Siemens Notes
      document.getElementById('drawer-siemens-remarks').innerText = inst.siemensNotes || "Sem observações adicionais.";

      // Load Saved User Comment
      const userComm = userComments[tagId] || { notes: '', status: 'NORMAL' };
      document.getElementById('user-notes-text').value = userComm.notes || '';
      document.getElementById('user-status-select').value = userComm.status || 'NORMAL';

      // Update Comment Indicator Badge
      const commBadge = document.getElementById('drawer-comment-badge');
      if (userComm.notes && userComm.notes.trim().length > 0) {
        commBadge.classList.remove('hidden');
      } else {
        commBadge.classList.add('hidden');
      }

      // Re-render sidebar highlights & SVGs
      renderSidebarTags();
      renderHotspotsOnSVG();
    }

    function switchDetailTab(tabName) {
      const specsBtn = document.getElementById('tab-btn-specs');
      const commentsBtn = document.getElementById('tab-btn-comments');
      const specsContent = document.getElementById('tab-content-specs');
      const commentsContent = document.getElementById('tab-content-comments');

      if (tabName === 'specs') {
        specsBtn.className = "flex-1 py-2.5 text-sky-400 border-b-2 border-sky-500 font-semibold transition";
        commentsBtn.className = "flex-1 py-2.5 text-slate-400 hover:text-slate-200 transition flex items-center justify-center gap-1.5";
        specsContent.classList.remove('hidden');
        commentsContent.classList.add('hidden');
      } else {
        commentsBtn.className = "flex-1 py-2.5 text-sky-400 border-b-2 border-sky-500 font-semibold transition flex items-center justify-center gap-1.5";
        specsBtn.className = "flex-1 py-2.5 text-slate-400 hover:text-slate-200 transition";
        commentsContent.classList.remove('hidden');
        specsContent.classList.add('hidden');
      }
    }

    function closeDrawer() {
      // Logic for mobile or hiding drawer if needed
    }

    // DIAGRAM PAN & ZOOM LOGIC
    function setupDiagramPanZoom() {
      const container = document.getElementById('diagram-viewport');
      const wrapper = document.getElementById('diagram-wrapper');

      container.addEventListener('mousedown', (e) => {
        isDragging = true;
        dragStartX = e.clientX - panX;
        dragStartY = e.clientY - panY;
      });

      window.addEventListener('mousemove', (e) => {
        if (!isDragging) return;
        panX = e.clientX - dragStartX;
        panY = e.clientY - dragStartY;
        updateTransform();
      });

      window.addEventListener('mouseup', () => {
        isDragging = false;
      });

      container.addEventListener('wheel', (e) => {
        e.preventDefault();
        const delta = e.deltaY > 0 ? -0.1 : 0.1;
        zoomDiagram(delta);
      });
    }

    function zoomDiagram(delta) {
      zoomLevel = Math.min(Math.max(0.5, zoomLevel + delta), 2.5);
      updateTransform();
    }

    function resetDiagramZoom() {
      zoomLevel = 1;
      panX = 0;
      panY = 0;
      updateTransform();
    }

    function updateTransform() {
      const wrapper = document.getElementById('diagram-wrapper');
      wrapper.style.transform = `translate(${panX}px, ${panY}px) scale(${zoomLevel})`;
    }

    function focusTagOnDiagram(tagId) {
      switchView('diagram');
      const inst = instruments.find(i => i.id === tagId);
      if (inst && inst.x && inst.y) {
        // Center pan on coordinates
        zoomLevel = 1.3;
        panX = (600 - inst.x) * zoomLevel;
        panY = (375 - inst.y) * zoomLevel;
        updateTransform();
      }
    }

    // CORRELATION TABLE TOOL
    function renderCorrelationTable() {
      const tbody = document.getElementById('correlation-table-body');
      const search = document.getElementById('corr-search-input').value.toLowerCase();

      const totalCount = instruments.length;
      const inCount = instruments.filter(i => i.inVaporPID).length;
      const outCount = instruments.filter(i => !i.inVaporPID).length;

      document.getElementById('corr-total-count').innerText = totalCount;
      document.getElementById('corr-in-count').innerText = inCount;
      document.getElementById('corr-out-count').innerText = outCount;
      document.getElementById('badge-missing-count').innerText = `${outCount} Fora`;

      const filtered = instruments.filter(inst => {
        const matchesFilter = correlationFilter === 'ALL' || 
                              (correlationFilter === 'IN_PID' && inst.inVaporPID) || 
                              (correlationFilter === 'OUT_PID' && !inst.inVaporPID);
        const matchesSearch = inst.id.toLowerCase().includes(search) || 
                              inst.kks.toLowerCase().includes(search) || 
                              inst.desc.toLowerCase().includes(search);
        return matchesFilter && matchesSearch;
      });

      tbody.innerHTML = filtered.map(inst => `
        <tr class="hover:bg-slate-800/40 transition">
          <td class="p-3 font-bold text-sky-400">${inst.id}</td>
          <td class="p-3 text-slate-400">${inst.kks}</td>
          <td class="p-3 font-sans font-medium text-slate-200">${inst.desc}</td>
          <td class="p-3"><span class="px-2 py-0.5 rounded bg-slate-800 text-slate-300 text-[10px]">${inst.systemName}</span></td>
          <td class="p-3">
            ${inst.inVaporPID 
              ? '<span class="px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-400 border border-emerald-500/30 text-[10px] font-sans font-semibold">✅ No P&ID Vapor</span>'
              : '<span class="px-2 py-0.5 rounded-full bg-amber-500/20 text-amber-400 border border-amber-500/30 text-[10px] font-sans font-semibold">⚠️ Ausente do P&ID Geral</span>'
            }
          </td>
          <td class="p-3 font-sans text-slate-400 text-[11px]">
            ${inst.inVaporPID ? 'Vapor geral TG-1.pdf' : 'Skid de Auxiliares (Óleo/Gerador)'}
          </td>
          <td class="p-3 text-right">
            <button onclick="selectTag('${inst.id}'); switchView('diagram'); focusTagOnDiagram('${inst.id}')" class="px-2 py-1 bg-slate-800 hover:bg-sky-600 text-slate-300 hover:text-white rounded transition text-[11px]">
              <i class="fa-solid fa-eye"></i> Ver
            </button>
          </td>
        </tr>
      `).join('');
    }

    function filterCorrelationTable(type) {
      correlationFilter = type;
      document.getElementById('corr-filter-all').className = type === 'ALL' ? "px-3 py-1 rounded-lg bg-sky-600 text-white font-medium" : "px-3 py-1 rounded-lg bg-slate-800 text-slate-300 hover:bg-slate-700";
      document.getElementById('corr-filter-out').className = type === 'OUT_PID' ? "px-3 py-1 rounded-lg bg-sky-600 text-white font-medium" : "px-3 py-1 rounded-lg bg-slate-800 text-slate-300 hover:bg-slate-700";
      document.getElementById('corr-filter-in').className = type === 'IN_PID' ? "px-3 py-1 rounded-lg bg-sky-600 text-white font-medium" : "px-3 py-1 rounded-lg bg-slate-800 text-slate-300 hover:bg-slate-700";
      renderCorrelationTable();
    }

    // ALL TAGS GRID VIEW
    function renderAllTagsGrid() {
      const container = document.getElementById('all-tags-grid');
      container.innerHTML = instruments.map(inst => `
        <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 space-y-3 shadow-lg flex flex-col justify-between">
          <div>
            <div class="flex justify-between items-start">
              <span class="font-mono text-base font-bold text-sky-400">${inst.id}</span>
              ${inst.inVaporPID 
                ? '<span class="text-[10px] px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-400 border border-emerald-500/30">P&ID Vapor</span>'
                : '<span class="text-[10px] px-2 py-0.5 rounded-full bg-amber-500/20 text-amber-400 border border-amber-500/30">Auxiliares</span>'
              }
            </div>
            <p class="text-xs text-slate-400 font-mono mt-0.5">${inst.kks}</p>
            <h4 class="text-sm font-semibold text-slate-100 mt-2">${inst.desc}</h4>
            <p class="text-xs text-slate-400 mt-1"><i class="fa-solid fa-sitemap mr-1"></i> ${inst.systemName}</p>
          </div>

          <div class="pt-3 border-t border-slate-800 flex justify-between items-center text-xs">
            <span class="font-mono text-slate-300">${inst.range}</span>
            <button onclick="selectTag('${inst.id}'); switchView('diagram')" class="px-3 py-1 bg-sky-600 hover:bg-sky-500 text-white rounded-lg font-medium transition flex items-center gap-1">
              Detalhes <i class="fa-solid fa-arrow-right"></i>
            </button>
          </div>
        </div>
      `).join('');
    }

    // ADD INSTRUMENT MODAL LOGIC
    function openAddInstrumentModal() {
      document.getElementById('modal-add-instrument').classList.remove('hidden');
    }

    function closeAddInstrumentModal() {
      document.getElementById('modal-add-instrument').classList.add('hidden');
    }

    function handleAddInstrument(e) {
      e.preventDefault();
      const tag = document.getElementById('add-tag').value.toUpperCase();
      const kks = document.getElementById('add-kks').value || tag;
      const desc = document.getElementById('add-desc').value;
      const system = document.getElementById('add-system').value;
      const range = document.getElementById('add-range').value || '0 ... 100%';
      const inVaporPID = document.querySelector('input[name="add-pid-status"]:checked').value === 'true';

      const newInst = {
        id: tag,
        kks: kks,
        desc: desc,
        system: system,
        systemName: system === 'MS' ? 'Vapor Principal' : 'Sistemas Auxiliares',
        range: range,
        inVaporPID: inVaporPID,
        page: 'Personalizado',
        x: 400, y: 400, // Default coordinates
        alarms: [],
        siemensNotes: "Instrumento adicionado manualmente pelo usuário."
      };

      instruments.push(newInst);
      saveInstruments();
      closeAddInstrumentModal();

      renderSidebarTags();
      renderHotspotsOnSVG();
      renderCorrelationTable();
      renderAllTagsGrid();
      selectTag(tag);
      switchView('diagram');
    }

    // EXPORT USER DATA / NOTES
    function exportUserData() {
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify({
        instruments: instruments,
        comments: userComments
      }, null, 2));
      const downloadAnchor = document.createElement('a');
      downloadAnchor.setAttribute("href", dataStr);
      downloadAnchor.setAttribute("download", "PID_Instrument_Comments_TG1.json");
      document.body.appendChild(downloadAnchor);
      downloadAnchor.click();
      downloadAnchor.remove();
    }
  </script>
</body>
</html>
    // PDF & FILE UPLOADER STATE
    let pdfDoc = null;
    let pageNum = 1;
    let isDrawMode = false;
    let isDrawingShape = false;
    let drawStartX = 0, drawStartY = 0;

    // FILE UPLOAD HANDLER (PDF or Image)
    function handleFileUpload(event) {
      const file = event.target.files[0];
      if (!file) return;

      if (file.type === 'application/pdf') {
        const fileReader = new FileReader();
        fileReader.onload = function() {
          const typedarray = new Uint8Array(this.result);
          pdfjsLib.getDocument(typedarray).promise.then(pdf => {
            pdfDoc = pdf;
            pageNum = 1;
            document.getElementById('pdf-page-count').innerText = pdf.numPages;
            document.getElementById('pdf-page-controls').classList.remove('hidden');
            renderPDFPage(pageNum);
          });
        };
        fileReader.readAsArrayBuffer(file);
      } else if (file.type.startsWith('image/')) {
        const reader = new FileReader();
        reader.onload = function(e) {
          const img = new Image();
          img.onload = function() {
            const canvas = document.getElementById('pdf-canvas');
            canvas.width = img.width;
            canvas.height = img.height;
            const ctx = canvas.getContext('2d');
            ctx.drawImage(img, 0, 0);

            canvas.classList.remove('hidden');
            document.getElementById('pid-svg').classList.add('hidden');
            document.getElementById('pdf-page-controls').classList.add('hidden');
          };
          img.src = e.target.result;
        };
        reader.readAsDataURL(file);
      }
    }

    function renderPDFPage(num) {
      if (!pdfDoc) return;
      pdfDoc.getPage(num).then(page => {
        const viewport = page.getViewport({ scale: 1.5 });
        const canvas = document.getElementById('pdf-canvas');
        const ctx = canvas.getContext('2d');
        canvas.height = viewport.height;
        canvas.width = viewport.width;

        const renderContext = {
          canvasContext: ctx,
          viewport: viewport
        };
        page.render(renderContext).promise.then(() => {
          canvas.classList.remove('hidden');
          document.getElementById('pid-svg').classList.add('hidden');
          document.getElementById('pdf-page-num').innerText = num;
        });
      });
    }

    function changePDFPage(delta) {
      if (!pdfDoc) return;
      if (pageNum + delta >= 1 && pageNum + delta <= pdfDoc.numPages) {
        pageNum += delta;
        renderPDFPage(pageNum);
      }
    }

    // DRAWING / MARKER TOOL ON CANVAS
    function toggleDrawMode() {
      isDrawMode = !isDrawMode;
      const btn = document.getElementById('btn-draw-mode');
      const label = document.getElementById('draw-mode-label');

      if (isDrawMode) {
        btn.className = "bg-sky-600 text-white border border-sky-400 px-3 py-1.5 rounded-lg text-xs font-semibold flex items-center gap-1.5 transition shadow-lg shadow-sky-900/50";
        label.innerText = "Clique para Marcar";
        document.getElementById('diagram-viewport').style.cursor = 'crosshair';
      } else {
        btn.className = "bg-slate-800 hover:bg-slate-700 text-slate-300 border border-slate-700 px-3 py-1.5 rounded-lg text-xs font-medium flex items-center gap-1.5 transition";
        label.innerText = "Desenhar Marcador";
        document.getElementById('diagram-viewport').style.cursor = 'grab';
      }
    }

    // SVG HOTSPOTS WITH HOVER TOOLTIP & CLICK TO EDIT
    function renderHotspotsOnSVG() {
      const group = document.getElementById('hotspots-group');
      
      group.innerHTML = instruments.map(inst => {
        if (!inst.x || !inst.y) return '';

        const isSelected = inst.id === currentSelectedTagId;
        const colorClass = inst.inVaporPID ? '#0284c7' : '#f59e0b';

        return `
          <g transform="translate(${inst.x}, ${inst.y})" 
             onclick="selectTag('${inst.id}')" 
             onmouseenter="showTooltip(event, '${inst.id}')" 
             onmouseleave="hideTooltip()"
             class="cursor-pointer group">
            <circle cx="0" cy="0" r="${isSelected ? 18 : 12}" fill="${colorClass}" opacity="0.2" class="tag-pulse"/>
            <circle cx="0" cy="0" r="${isSelected ? 12 : 9}" fill="${isSelected ? '#38bdf8' : colorClass}" stroke="#ffffff" stroke-width="1.5"/>
            <text x="0" y="3" fill="#ffffff" font-size="8" font-weight="bold" text-anchor="middle" font-family="Inter">
              ${inst.id.includes('CP') ? 'P' : inst.id.includes('CT') ? 'T' : 'I'}
            </text>
            <rect x="-35" y="-28" width="70" height="15" rx="3" fill="#0f172a" stroke="${isSelected ? '#38bdf8' : '#334155'}" stroke-width="1"/>
            <text x="0" y="-18" fill="${isSelected ? '#38bdf8' : '#e2e8f0'}" font-size="8" font-weight="bold" font-family="JetBrains Mono" text-anchor="middle">
              ${inst.id}
            </text>
          </g>
        `;
      }).join('');
    }

    // HOVER TOOLTIP DISPLAY
    function showTooltip(event, tagId) {
      if (isDrawMode) return;
      const inst = instruments.find(i => i.id === tagId);
      if (!inst) return;

      const tooltip = document.getElementById('hover-tooltip');
      document.getElementById('tooltip-tag').innerText = inst.id;
      document.getElementById('tooltip-kks').innerText = inst.kks;
      document.getElementById('tooltip-desc').innerText = inst.desc;
      document.getElementById('tooltip-range').innerText = inst.range;
      document.getElementById('tooltip-system').innerText = inst.systemName;

      const statusEl = document.getElementById('tooltip-status');
      if (inst.inVaporPID) {
        statusEl.className = "px-1.5 py-0.5 text-[9px] font-bold rounded bg-emerald-500/20 text-emerald-400 border border-emerald-500/30";
        statusEl.innerText = "No P&ID";
      } else {
        statusEl.className = "px-1.5 py-0.5 text-[9px] font-bold rounded bg-amber-500/20 text-amber-400 border border-amber-500/30";
        statusEl.innerText = "Auxiliares";
      }

      // Position Tooltip
      const rect = event.target.getBoundingClientRect();
      tooltip.style.left = `${rect.left + rect.width / 2}px`;
      tooltip.style.top = `${rect.top - 10}px`;
      tooltip.classList.remove('hidden');
    }

    function hideTooltip() {
      document.getElementById('hover-tooltip').classList.add('hidden');
    }

    // EDIT INSTRUMENT DATA
    function selectTag(tagId) {
      currentSelectedTagId = tagId;
      const inst = instruments.find(i => i.id === tagId);
      if (!inst) return;

      // Populate Read-only View
      document.getElementById('drawer-tag').innerText = inst.id;
      document.getElementById('drawer-kks').innerText = inst.kks;
      document.getElementById('drawer-desc').innerText = inst.desc;
      document.getElementById('drawer-system-name').innerText = inst.systemName;
      document.getElementById('drawer-range').innerText = inst.range;

      // Populate Edit Form
      document.getElementById('edit-tag-id').value = inst.id;
      document.getElementById('edit-kks').value = inst.kks;
      document.getElementById('edit-desc').value = inst.desc;
      document.getElementById('edit-range').value = inst.range;
      document.getElementById('edit-system').value = inst.system;
      document.getElementById('edit-pid-status').checked = inst.inVaporPID;
      document.getElementById('edit-notes').value = inst.siemensNotes || '';

      const badge = document.getElementById('drawer-status-badge');
      if (inst.inVaporPID) {
        badge.className = "px-2 py-0.5 text-xs font-semibold rounded-md bg-emerald-500/20 text-emerald-400 border border-emerald-500/30";
        badge.innerText = "No P&ID de Vapor Geral";
      } else {
        badge.className = "px-2 py-0.5 text-xs font-semibold rounded-md bg-amber-500/20 text-amber-400 border border-amber-500/30";
        badge.innerText = "Em Sistemas Auxiliares";
      }

      // Render Alarms Table
      const alarmsBody = document.getElementById('drawer-alarms-body');
      if (inst.alarms && inst.alarms.length > 0) {
        alarmsBody.innerHTML = inst.alarms.map(a => `
          <tr class="hover:bg-slate-900/50">
            <td class="p-2 font-bold ${a.level.startsWith('H') ? 'text-amber-400' : 'text-sky-400'}">${a.level}</td>
            <td class="p-2 text-slate-200">${a.val}</td>
            <td class="p-2 text-rose-400 font-bold">${a.action}</td>
            <td class="p-2 text-slate-400 font-sans text-[11px]">${a.remark}</td>
          </tr>
        `).join('');
      } else {
        alarmsBody.innerHTML = `<tr><td colspan="4" class="p-2 text-slate-500 text-center font-sans">Sem setpoints cadastrados</td></tr>`;
      }

      document.getElementById('drawer-siemens-remarks').innerText = inst.siemensNotes || "Sem observações adicionais.";

      const userComm = userComments[tagId] || { notes: '', status: 'NORMAL' };
      document.getElementById('user-notes-text').value = userComm.notes || '';
      document.getElementById('user-status-select').value = userComm.status || 'NORMAL';

      renderSidebarTags();
      renderHotspotsOnSVG();
    }

    function saveInstrumentEdits() {
      const inst = instruments.find(i => i.id === currentSelectedTagId);
      if (!inst) return;

      inst.id = document.getElementById('edit-tag-id').value.toUpperCase();
      inst.kks = document.getElementById('edit-kks').value;
      inst.desc = document.getElementById('edit-desc').value;
      inst.range = document.getElementById('edit-range').value;
      inst.system = document.getElementById('edit-system').value;
      inst.inVaporPID = document.getElementById('edit-pid-status').checked;
      inst.siemensNotes = document.getElementById('edit-notes').value;

      saveInstruments();
      selectTag(inst.id);
      renderSidebarTags();
      renderCorrelationTable();
      renderAllTagsGrid();
      alert('Instrumento atualizado com sucesso!');
    }

    function deleteCurrentInstrument() {
      if (confirm(`Tem certeza que deseja excluir o TAG ${currentSelectedTagId}?`)) {
        instruments = instruments.filter(i => i.id !== currentSelectedTagId);
        saveInstruments();
        if (instruments.length > 0) {
          selectTag(instruments[0].id);
        }
        renderSidebarTags();
        renderCorrelationTable();
        renderAllTagsGrid();
      }
    }

    // CANVAS CLICK FOR CREATING NEW MARKERS VISUALLY
    document.getElementById('pid-svg').addEventListener('click', function(e) {
      if (!isDrawMode) return;
      const rect = this.getBoundingClientRect();
      const clickX = Math.round((e.clientX - rect.left) / zoomLevel);
      const clickY = Math.round((e.clientY - rect.top) / zoomLevel);

      const tag = prompt("Digite o TAG/KKS do novo instrumento marcado neste ponto:", "10LBA10CP" + Math.floor(Math.random() * 900 + 100));
      if (!tag) return;

      const newInst = {
        id: tag.toUpperCase(),
        kks: tag,
        desc: "Novo Instrumento Marcado no Diagrama",
        system: "MS",
        systemName: "Vapor Principal",
        range: "0 ... 100 bar (g)",
        inVaporPID: true,
        page: "Criado Manualmente",
        x: clickX,
        y: clickY,
        alarms: [],
        siemensNotes: "Marcador posicionado visualmente pelo usuário."
      };

      instruments.push(newInst);
      saveInstruments();
      toggleDrawMode();
      selectTag(newInst.id);
      switchDetailTab('edit');
    });

    function switchDetailTab(tabName) {
      const specsBtn = document.getElementById('tab-btn-specs');
      const editBtn = document.getElementById('tab-btn-edit');
      const commentsBtn = document.getElementById('tab-btn-comments');

      const specsContent = document.getElementById('tab-content-specs');
      const editContent = document.getElementById('tab-content-edit');
      const commentsContent = document.getElementById('tab-content-comments');

      specsContent.classList.add('hidden');
      editContent.classList.add('hidden');
      commentsContent.classList.add('hidden');

      specsBtn.className = "flex-1 py-2.5 text-slate-400 hover:text-slate-200 transition";
      editBtn.className = "flex-1 py-2.5 text-slate-400 hover:text-slate-200 transition flex items-center justify-center gap-1.5";
      commentsBtn.className = "flex-1 py-2.5 text-slate-400 hover:text-slate-200 transition flex items-center justify-center gap-1.5";

      if (tabName === 'specs') {
        specsBtn.className = "flex-1 py-2.5 text-sky-400 border-b-2 border-sky-500 font-semibold transition";
        specsContent.classList.remove('hidden');
      } else if (tabName === 'edit') {
        editBtn.className = "flex-1 py-2.5 text-sky-400 border-b-2 border-sky-500 font-semibold transition flex items-center justify-center gap-1.5";
        editContent.classList.remove('hidden');
      } else {
        commentsBtn.className = "flex-1 py-2.5 text-sky-400 border-b-2 border-sky-500 font-semibold transition flex items-center justify-center gap-1.5";
        commentsContent.classList.remove('hidden');
      }
    }
  </script>
</body>
</html>
