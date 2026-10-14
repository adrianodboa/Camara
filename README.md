<!DOCTYPE html>
<html lang="pt-BR" class="dark">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>OPERAÇÃO CÂMARA 240 | Analista Legislativo - Arquivologia</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://unpkg.com/lucide@latest"></script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;600;700&display=swap" rel="stylesheet">
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            mono: ['JetBrains Mono', 'monospace'],
          },
          colors: {
            slate: {
              850: '#151e2e',
              900: '#0f172a',
              950: '#080d1a',
            },
            emerald: {
              450: '#10b981',
            }
          }
        }
      }
    }
  </script>
  <style>
    body {
      background-color: #080d1a;
      color: #f1f5f9;
      font-family: 'Inter', sans-serif;
    }
    .custom-scrollbar::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    .custom-scrollbar::-webkit-scrollbar-track {
      background: #0f172a;
    }
    .custom-scrollbar::-webkit-scrollbar-thumb {
      background: #334155;
      border-radius: 9999px;
    }
    .custom-scrollbar::-webkit-scrollbar-thumb:hover {
      background: #475569;
    }
    .tier-s-glow {
      box-shadow: 0 0 20px -5px rgba(56, 189, 248, 0.35);
    }
    .tier-a-glow {
      box-shadow: 0 0 20px -5px rgba(250, 204, 21, 0.3);
    }
    @keyframes pulse-border {
      0%, 100% { border-color: rgba(16, 185, 129, 0.5); }
      50% { border-color: rgba(16, 185, 129, 1); }
    }
    .mission-active {
      animation: pulse-border 2s infinite;
    }
  </style>
</head>
<body class="min-h-screen flex flex-col selection:bg-cyan-500 selection:text-slate-950">

  <!-- TOP HUD BAR (GAMIFICATION & STATUS GLOBAL) -->
  <header class="sticky top-0 z-40 bg-slate-950/90 backdrop-blur-md border-b border-slate-800 px-4 lg:px-8 py-3">
    <div class="max-w-7xl mx-auto flex flex-wrap items-center justify-between gap-4">
      
      <!-- Brand & Rank -->
      <div class="flex items-center gap-3">
        <div class="w-11 h-11 rounded-xl bg-gradient-to-br from-cyan-500 via-blue-600 to-indigo-700 flex items-center justify-center shadow-lg shadow-cyan-500/20 border border-cyan-400/30">
          <i data-lucide="shield-check" class="w-6 h-6 text-white"></i>
        </div>
        <div>
          <div class="flex items-center gap-2">
            <span class="text-xs font-mono uppercase tracking-widest px-2 py-0.5 rounded bg-cyan-500/10 text-cyan-400 border border-cyan-500/30 font-bold">Cebraspe • 240 Pts</span>
            <span id="hud-phase-badge" class="text-xs font-mono uppercase tracking-wider px-2 py-0.5 rounded bg-amber-500/10 text-amber-400 border border-amber-500/30">Bloco 1: Volume</span>
          </div>
          <h1 class="text-base lg:text-lg font-extrabold tracking-tight text-white flex items-center gap-2">
            OPERAÇÃO CÂMARA 240 <span class="text-slate-500 font-normal text-xs hidden sm:inline">| Arquivologia Legislativa</span>
          </h1>
        </div>
      </div>

      <!-- Center HUD: Daily Meta 100Q + Streak + Countdown -->
      <div class="flex items-center gap-3 sm:gap-6 bg-slate-900/90 border border-slate-800 rounded-xl px-4 py-2">
        <!-- Meta Diária -->
        <div class="flex items-center gap-2.5">
          <div class="relative w-10 h-10 flex items-center justify-center">
            <svg class="w-10 h-10 -rotate-90" viewBox="0 0 36 36">
              <path class="text-slate-800" stroke-width="3.5" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831"/>
              <path id="hud-daily-ring" class="text-emerald-400 transition-all duration-500" stroke-dasharray="0, 100" stroke-width="3.5" stroke-linecap="round" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831"/>
            </svg>
            <span id="hud-daily-pct" class="absolute text-[10px] font-mono font-bold text-white">0%</span>
          </div>
          <div>
            <div class="text-[11px] text-slate-400 font-medium uppercase tracking-wider">Meta Hoje</div>
            <div class="text-sm font-mono font-bold text-white"><span id="hud-today-q" class="text-emerald-400">0</span>/<span id="hud-target-q">100</span> <span class="text-xs text-slate-400">itens</span></div>
          </div>
        </div>

        <div class="h-7 w-px bg-slate-800"></div>

        <!-- Saldo Líquido Global -->
        <div>
          <div class="text-[11px] text-slate-400 font-medium uppercase tracking-wider">Saldo Líquido</div>
          <div class="text-sm font-mono font-bold flex items-center gap-1">
            <span id="hud-net-score" class="text-cyan-400">+0</span>
            <span class="text-[11px] text-slate-500 font-normal">pts</span>
          </div>
        </div>

        <div class="h-7 w-px bg-slate-800 hidden sm:block"></div>

        <!-- Streak -->
        <div class="hidden sm:flex items-center gap-1.5">
          <i data-lucide="flame" class="w-5 h-5 text-orange-500 fill-orange-500"></i>
          <div>
            <div class="text-[11px] text-slate-400 font-medium uppercase tracking-wider">Ofensiva</div>
            <div class="text-sm font-mono font-bold text-orange-400"><span id="hud-streak">0</span> dias</div>
          </div>
        </div>

        <div class="h-7 w-px bg-slate-800 hidden md:block"></div>

        <!-- Contagem Regressiva -->
        <div class="hidden md:block">
          <div class="text-[11px] text-slate-400 font-medium uppercase tracking-wider">Prova: 17/01/27</div>
          <div class="text-sm font-mono font-bold text-rose-400"><span id="hud-countdown">95</span> dias</div>
        </div>
      </div>

      <!-- Player Level & XP + Backup -->
      <div class="flex items-center gap-3">
        <div class="text-right hidden xl:block">
          <div class="flex items-center justify-end gap-1.5">
            <span id="hud-rank-title" class="text-xs font-bold text-amber-400">Nível 1 • Técnico de Protocolo</span>
          </div>
          <div class="w-36 h-2 bg-slate-800 rounded-full overflow-hidden mt-1">
            <div id="hud-xp-bar" class="h-full bg-gradient-to-r from-amber-500 to-yellow-300 transition-all duration-500" style="width: 10%"></div>
          </div>
          <div class="text-[10px] font-mono text-slate-400 mt-0.5"><span id="hud-xp-val">0</span> XP acumulados</div>
        </div>

        <button onclick="openBackupModal()" title="Salvar / Restaurar Backup de Dados" class="p-2.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-slate-300 border border-slate-700/80 flex items-center gap-1.5 text-xs font-medium transition">
          <i data-lucide="database" class="w-4 h-4 text-cyan-400"></i>
          <span class="hidden sm:inline">Dados</span>
        </button>
      </div>

    </div>
  </header>

  <!-- NAVIGATION TABS -->
  <nav class="bg-slate-900/60 border-b border-slate-800/80 px-4 lg:px-8 overflow-x-auto custom-scrollbar">
    <div class="max-w-7xl mx-auto flex items-center gap-1 py-1.5">
      <button onclick="switchTab('dashboard')" id="tab-btn-dashboard" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap bg-cyan-500/15 text-cyan-300 border border-cyan-500/30">
        <i data-lucide="crosshair" class="w-4 h-4"></i>
        Comando Diário (100Q+)
      </button>
      <button onclick="switchTab('simulador')" id="tab-btn-simulador" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap text-slate-400 hover:text-white hover:bg-slate-800/60">
        <i data-lucide="cpu" class="w-4 h-4 text-emerald-400"></i>
        Simulador Cebraspe (<span id="nav-q-count">60</span>+ Itens)
      </button>
      <button onclick="switchTab('codice')" id="tab-btn-codice" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap text-slate-400 hover:text-white hover:bg-slate-800/60">
        <i data-lucide="book-open-check" class="w-4 h-4 text-amber-400"></i>
        Códice Pareto 80/20 (Teoria 15m)
      </button>
      <button onclick="switchTab('gaps')" id="tab-btn-gaps" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap text-slate-400 hover:text-white hover:bg-slate-800/60">
        <i data-lucide="zap" class="w-4 h-4 text-purple-400"></i>
        Caderno de Gaps (<span id="nav-gaps-count">0</span>)
      </button>
      <button onclick="switchTab('discursiva')" id="tab-btn-discursiva" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap text-slate-400 hover:text-white hover:bg-slate-800/60">
        <i data-lucide="pen-tool" class="w-4 h-4 text-rose-400"></i>
        Engenharia Discursiva (P3 • 60 Pts)
      </button>
      <button onclick="switchTab('cronograma')" id="tab-btn-cronograma" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap text-slate-400 hover:text-white hover:bg-slate-800/60">
        <i data-lucide="calendar-days" class="w-4 h-4 text-blue-400"></i>
        Mapa de 96 Dias & ROI
      </button>
    </div>
  </nav>

  <!-- MAIN CONTENT CONTAINER -->
  <main class="flex-1 max-w-7xl w-full mx-auto px-4 lg:px-8 py-6">

    <!-- ==========================================
         TAB 1: COMANDO DIÁRIO (META 100 QUESTÕES/DIA)
         ========================================== -->
    <section id="tab-dashboard" class="tab-content space-y-6">
      
      <!-- Top Banner: Alerta de Missão Diária & Seletor de Data -->
      <div class="bg-gradient-to-r from-slate-900 via-slate-900 to-cyan-950/40 border border-slate-800 rounded-2xl p-5 flex flex-col lg:flex-row items-start lg:items-center justify-between gap-4">
        <div class="space-y-1">
          <div class="flex items-center gap-2">
            <span class="px-2.5 py-0.5 rounded-full text-xs font-mono font-bold bg-emerald-500/20 text-emerald-300 border border-emerald-500/30 flex items-center gap-1">
              <span class="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span> MISSÃO ATIVA
            </span>
            <span class="text-xs text-slate-400 font-mono" id="dashboard-current-date-label">Quarta-feira, 14/10/2026</span>
          </div>
          <h2 class="text-xl sm:text-2xl font-black text-white tracking-tight">
            Meta Operacional: <span class="text-cyan-400">100+ Questões Cebraspe / Dia</span>
          </h2>
          <p class="text-xs sm:text-sm text-slate-300 max-w-3xl">
            Distribuição matemática calibrada pela <strong>Curva ABC de Pareto</strong>: 50 itens no <strong>Tier S (Diamante)</strong>, 30 itens no <strong>Tier A (Ouro)</strong> e 20 itens no <strong>Tier B (Prata)</strong>. Lembre-se da <em>Omissão Consciente</em>: deixar de 10% a 15% em branco protege seu saldo líquido!
          </p>
        </div>

        <!-- Date selector & Target adjuster -->
        <div class="flex flex-wrap items-center gap-3 self-stretch lg:self-center bg-slate-950/80 p-3 rounded-xl border border-slate-800">
          <div>
            <label class="block text-[10px] font-mono uppercase text-slate-400">Data do Registro</label>
            <input type="date" id="active-date-input" onchange="changeActiveDate(this.value)" class="bg-slate-900 text-white text-xs font-mono rounded-lg px-2.5 py-1.5 border border-slate-700 focus:outline-none focus:border-cyan-500"/>
          </div>
          <div>
            <label class="block text-[10px] font-mono uppercase text-slate-400">Meta Diária</label>
            <select id="daily-goal-select" onchange="updateDailyGoalTarget(this.value)" class="bg-slate-900 text-cyan-400 font-mono font-bold text-xs rounded-lg px-2.5 py-1.5 border border-slate-700 focus:outline-none">
              <option value="100">100 Q / dia (Padrão Hardcore)</option>
              <option value="120">120 Q / dia (Aceleração)</option>
              <option value="150">150 Q / dia (Modo Insano)</option>
              <option value="180">180 Q / dia (Simulado Completo P1+P2)</option>
            </select>
          </div>
        </div>
      </div>

      <!-- KPI Cards of the Selected Day -->
      <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
        <div class="bg-slate-900/90 border border-slate-800 rounded-xl p-4">
          <div class="flex items-center justify-between text-xs text-slate-400 mb-1">
            <span>QUESTÕES HOJE</span>
            <i data-lucide="check-circle-2" class="w-4 h-4 text-cyan-400"></i>
          </div>
          <div class="text-2xl font-mono font-black text-white"><span id="day-kpi-total">0</span> <span class="text-xs font-normal text-slate-500">/ <span id="day-kpi-target">100</span></span></div>
          <div class="text-[11px] text-slate-400 mt-1" id="day-kpi-status">Faltam 100 questões</div>
        </div>

        <div class="bg-slate-900/90 border border-slate-800 rounded-xl p-4">
          <div class="flex items-center justify-between text-xs text-slate-400 mb-1">
            <span>ACERTOS BRUTOS</span>
            <i data-lucide="trending-up" class="w-4 h-4 text-emerald-400"></i>
          </div>
          <div class="text-2xl font-mono font-black text-emerald-400" id="day-kpi-correct">0</div>
          <div class="text-[11px] text-slate-400 mt-1">Taxa bruta: <span id="day-kpi-acc" class="text-white font-mono">0%</span></div>
        </div>

        <div class="bg-slate-900/90 border border-slate-800 rounded-xl p-4">
          <div class="flex items-center justify-between text-xs text-slate-400 mb-1">
            <span>ERROS (-1 PT)</span>
            <i data-lucide="alert-Octagon" class="w-4 h-4 text-rose-400"></i>
          </div>
          <div class="text-2xl font-mono font-black text-rose-400" id="day-kpi-wrong">0</div>
          <div class="text-[11px] text-slate-400 mt-1">Penalidade Cebraspe</div>
        </div>

        <div class="bg-slate-900/90 border border-slate-800 rounded-xl p-4">
          <div class="flex items-center justify-between text-xs text-slate-400 mb-1">
            <span>EM BRANCO (TÁTICO)</span>
            <i data-lucide="shield" class="w-4 h-4 text-amber-400"></i>
          </div>
          <div class="text-2xl font-mono font-black text-amber-400" id="day-kpi-blank">0</div>
          <div class="text-[11px] text-slate-400 mt-1">Ideal: 10% a 15%</div>
        </div>

        <div class="col-span-2 md:col-span-1 bg-gradient-to-br from-cyan-950/60 to-slate-900 border border-cyan-500/40 rounded-xl p-4">
          <div class="flex items-center justify-between text-xs text-cyan-300 font-semibold mb-1">
            <span>SALDO LÍQUIDO DIA</span>
            <i data-lucide="award" class="w-4 h-4 text-cyan-400"></i>
          </div>
          <div class="text-2xl font-mono font-black text-white" id="day-kpi-net">+0</div>
          <div class="text-[11px] text-cyan-300/80 mt-1">% Líquido: <span id="day-kpi-net-pct" class="font-mono font-bold">0%</span> (Meta: ≥68%)</div>
        </div>
      </div>

      <!-- MATRIZ DE EXECUÇÃO DIÁRIA POR TIERS (100 QUESTÕES) -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        
        <!-- COLUNA 1 E 2: CHECKLIST DE BATERIAS POR TIER (PARETO 80/20) -->
        <div class="lg:col-span-2 space-y-5">
          
          <!-- TIER S: DIAMANTE (50% = 50 QUESTÕES/DIA) -->
          <div class="bg-slate-900/95 border border-cyan-500/40 rounded-2xl p-5 tier-s-glow">
            <div class="flex flex-wrap items-center justify-between gap-2 pb-3 mb-4 border-b border-slate-800">
              <div class="flex items-center gap-2.5">
                <span class="px-2.5 py-1 rounded-lg bg-cyan-500/20 text-cyan-300 font-mono font-black text-xs border border-cyan-400/40">TIER S • DIAMANTE (50%)</span>
                <h3 class="font-bold text-white text-sm sm:text-base">Incidência Tripla (P1 + P2 + P3)</h3>
              </div>
              <div class="text-xs font-mono">
                Progresso Tier S Hoje: <span id="tier-s-progress" class="font-bold text-cyan-400">0 / 50</span> itens
              </div>
            </div>

            <div class="space-y-3" id="tier-s-list">
              <!-- Populated dynamically by JS -->
            </div>
          </div>

          <!-- TIER A: OURO (30% = 30 QUESTÕES/DIA) -->
          <div class="bg-slate-900/95 border border-amber-500/40 rounded-2xl p-5 tier-a-glow">
            <div class="flex flex-wrap items-center justify-between gap-2 pb-3 mb-4 border-b border-slate-800">
              <div class="flex items-center gap-2.5">
                <span class="px-2.5 py-1 rounded-lg bg-amber-500/20 text-amber-300 font-mono font-black text-xs border border-amber-400/40">TIER A • OURO (30%)</span>
                <h3 class="font-bold text-white text-sm sm:text-base">Diferencial de Desempate e Fronteira</h3>
              </div>
              <div class="text-xs font-mono">
                Progresso Tier A Hoje: <span id="tier-a-progress" class="font-bold text-amber-400">0 / 30</span> itens
              </div>
            </div>

            <div class="space-y-3" id="tier-a-list">
              <!-- Populated dynamically by JS -->
            </div>
          </div>

          <!-- TIER B: PRATA (20% = 20 QUESTÕES/DIA) -->
          <div class="bg-slate-900/95 border border-slate-700 rounded-2xl p-5">
            <div class="flex flex-wrap items-center justify-between gap-2 pb-3 mb-4 border-b border-slate-800">
              <div class="flex items-center gap-2.5">
                <span class="px-2.5 py-1 rounded-lg bg-slate-700 text-slate-200 font-mono font-black text-xs border border-slate-600">TIER B • PRATA (20%)</span>
                <h3 class="font-bold text-white text-sm sm:text-base">Manutenção Rápida via Estudo Reverso</h3>
              </div>
              <div class="text-xs font-mono">
                Progresso Tier B Hoje: <span id="tier-b-progress" class="font-bold text-slate-300">0 / 20</span> itens
              </div>
            </div>

            <div class="space-y-3" id="tier-b-list">
              <!-- Populated dynamically by JS -->
            </div>
          </div>

        </div>

        <!-- COLUNA 3: LANÇADOR RÁPIDO DE BATERIA + RADAR DE PERFORMANCE -->
        <div class="space-y-5">
          
          <!-- Lançador Rápido de Questões (Baterias Externas ou Rápidas) -->
          <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5">
            <div class="flex items-center justify-between mb-3">
              <h3 class="font-bold text-white text-sm flex items-center gap-2">
                <i data-lucide="plus-circle" class="w-4 h-4 text-emerald-400"></i>
                Registrar Bateria de Questões
              </h3>
              <span class="text-[10px] font-mono uppercase px-2 py-0.5 rounded bg-emerald-500/10 text-emerald-400">+10 XP / questão</span>
            </div>
            <p class="text-xs text-slate-400 mb-4">
              Fez questões no TEC/QConcursos ou PDF? Lance a bateria aqui ou use o nosso <strong>Simulador Cebraspe</strong> na aba ao lado (que já grava automaticamente!).
            </p>

            <form onsubmit="logManualBattery(event)" class="space-y-3">
              <div>
                <label class="block text-xs text-slate-300 font-medium mb-1">Matéria / Eixo do Edital</label>
                <select id="log-subject" required class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-white focus:outline-none focus:border-cyan-500">
                  <!-- Populated by JS -->
                </select>
              </div>

              <div class="grid grid-cols-3 gap-2.5">
                <div>
                  <label class="block text-[11px] text-emerald-400 font-mono mb-1">Certas (+1)</label>
                  <input type="number" id="log-correct" min="0" max="200" value="16" required class="w-full bg-slate-950 border border-emerald-500/40 rounded-xl px-3 py-2 text-sm font-mono font-bold text-emerald-400 focus:outline-none"/>
                </div>
                <div>
                  <label class="block text-[11px] text-rose-400 font-mono mb-1">Erradas (-1)</label>
                  <input type="number" id="log-wrong" min="0" max="200" value="2" required class="w-full bg-slate-950 border border-rose-500/40 rounded-xl px-3 py-2 text-sm font-mono font-bold text-rose-400 focus:outline-none"/>
                </div>
                <div>
                  <label class="block text-[11px] text-amber-400 font-mono mb-1">Branco (0)</label>
                  <input type="number" id="log-blank" min="0" max="200" value="2" required class="w-full bg-slate-950 border border-amber-500/40 rounded-xl px-3 py-2 text-sm font-mono font-bold text-amber-400 focus:outline-none"/>
                </div>
              </div>

              <div>
                <label class="block text-xs text-slate-300 font-medium mb-1">Gap de 1 Linha (Opcional — Erro que virou aprendizado)</label>
                <input type="text" id="log-gap-note" placeholder="Ex: [OAIS] SIP não traz PREMIS; PREMIS é gerado na ingestão p/ AIP." class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-white focus:outline-none focus:border-purple-500"/>
              </div>

              <button type="submit" class="w-full py-2.5 px-4 rounded-xl bg-gradient-to-r from-emerald-500 to-cyan-500 hover:from-emerald-400 hover:to-cyan-400 text-slate-950 font-extrabold text-xs uppercase tracking-wider transition shadow-lg shadow-emerald-500/20 flex items-center justify-center gap-2">
                <i data-lucide="save" class="w-4 h-4"></i>
                Gravar Bateria & Computar Saldo Líquido
              </button>
            </form>
          </div>

          <!-- Termômetro da Omissão Consciente (Cebraspe) -->
          <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 space-y-3">
            <div class="flex items-center justify-between">
              <h3 class="font-bold text-white text-sm flex items-center gap-2">
                <i data-lucide="gauge" class="w-4 h-4 text-amber-400"></i>
                Calibrador de Omissão Consciente
              </h3>
              <span id="omission-badge" class="text-[10px] font-mono px-2 py-0.5 rounded bg-slate-800 text-slate-300">Aguardando dados</span>
            </div>
            <p class="text-xs text-slate-400">
              Para fazer <strong>122+ pontos líquidos</strong> nos 180 itens, você precisa deixar entre <strong>11% e 16% da prova em branco</strong> (20 a 30 itens) e manter ≥82% de acerto no que marcar.
            </p>
            <div class="bg-slate-950 rounded-xl p-3 border border-slate-800 space-y-2 text-xs font-mono">
              <div class="flex justify-between">
                <span class="text-slate-400">Total Resolvido (Acumulado):</span>
                <span id="global-stat-total" class="text-white font-bold">0 itens</span>
              </div>
              <div class="flex justify-between">
                <span class="text-slate-400">Taxa de Acerto nos Marcados:</span>
                <span id="global-stat-marked-acc" class="text-emerald-400 font-bold">0%</span>
              </div>
              <div class="flex justify-between">
                <span class="text-slate-400">Taxa de Omissão Tática:</span>
                <span id="global-stat-blank-rate" class="text-amber-400 font-bold">0%</span>
              </div>
              <div class="flex justify-between pt-2 border-t border-slate-800">
                <span class="text-cyan-300 font-bold">Projeção em Prova de 180 Itens:</span>
                <span id="global-stat-projection" class="text-cyan-400 font-black">0 pts líquidos</span>
              </div>
            </div>
          </div>

          <!-- Histórico de Logs de Hoje -->
          <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5">
            <div class="flex items-center justify-between mb-3">
              <h3 class="font-bold text-white text-sm flex items-center gap-2">
                <i data-lucide="history" class="w-4 h-4 text-cyan-400"></i>
                Baterias Gravadas no Dia
              </h3>
              <button onclick="clearTodayLogs()" class="text-[11px] text-rose-400 hover:underline">Zerar dia</button>
            </div>
            <div id="today-logs-container" class="space-y-2 max-h-60 overflow-y-auto custom-scrollbar">
              <!-- Populated by JS -->
            </div>
          </div>

        </div>
      </div>
    </section>

    <!-- ==========================================
         TAB 2: SIMULADOR CEBRASPE (BANCO INTERATIVO)
         ========================================== -->
    <section id="tab-simulador" class="tab-content hidden space-y-6">
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 flex flex-col lg:flex-row items-start lg:items-center justify-between gap-4">
        <div>
          <div class="flex items-center gap-2 mb-1">
            <span class="px-2 py-0.5 rounded text-[10px] font-mono font-bold bg-emerald-500/20 text-emerald-300 border border-emerald-500/30">AGENTE SIMULADOR CEBRASPE</span>
            <span class="text-xs text-slate-400 font-mono">1 Errada anula 1 Certa • Botão de Omissão Tática Incluso</span>
          </div>
          <h2 class="text-xl font-black text-white">Banco Hardcore de Questões Inéditas & Clássicas da Câmara</h2>
          <p class="text-xs text-slate-300">
            Cada questão respondida aqui <strong>já soma automaticamente na sua meta diária de 100 questões</strong> e permite enviar o comentário direto para o seu <strong>Caderno de Gaps de 1 Linha</strong>!
          </p>
        </div>

        <div class="flex flex-wrap items-center gap-2">
          <select id="sim-filter-tier" onchange="renderSimulatorQuestion()" class="bg-slate-950 text-xs font-mono text-white border border-slate-700 rounded-xl px-3 py-2">
            <option value="ALL">Todos os Tiers (S, A, B)</option>
            <option value="S">Apenas TIER S (Diamante - 50%)</option>
            <option value="A">Apenas TIER A (Ouro - 30%)</option>
            <option value="B">Apenas TIER B (Prata - 20%)</option>
          </select>

          <select id="sim-filter-subject" onchange="renderSimulatorQuestion()" class="bg-slate-950 text-xs font-mono text-white border border-slate-700 rounded-xl px-3 py-2">
            <option value="ALL">Todas as Matérias</option>
          </select>

          <button onclick="openNewQuestionModal()" class="px-3 py-2 rounded-xl bg-cyan-500/20 hover:bg-cyan-500/30 text-cyan-300 border border-cyan-500/30 text-xs font-bold flex items-center gap-1.5 transition">
            <i data-lucide="plus" class="w-4 h-4"></i> Criar Questão Inédita
          </button>
        </div>
      </div>

      <!-- Simulator Arena -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <div class="lg:col-span-2 space-y-4">
          <div id="sim-card" class="bg-slate-900 border border-slate-800 rounded-2xl p-6 space-y-6 relative overflow-hidden">
            <!-- Populated by JS -->
          </div>
        </div>

        <!-- Simulator Sidebar Stats & Question Navigator -->
        <div class="space-y-4">
          <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 space-y-3">
            <h3 class="font-bold text-white text-sm flex items-center gap-2">
              <i data-lucide="bar-chart-3" class="w-4 h-4 text-cyan-400"></i>
              Placar da Sessão no Simulador
            </h3>
            <div class="grid grid-cols-4 gap-2 text-center font-mono">
              <div class="bg-slate-950 p-2.5 rounded-xl border border-slate-800">
                <div class="text-[10px] text-slate-400">Certas</div>
                <div id="sim-stat-c" class="text-base font-bold text-emerald-400">0</div>
              </div>
              <div class="bg-slate-950 p-2.5 rounded-xl border border-slate-800">
                <div class="text-[10px] text-slate-400">Erradas</div>
                <div id="sim-stat-e" class="text-base font-bold text-rose-400">0</div>
              </div>
              <div class="bg-slate-950 p-2.5 rounded-xl border border-slate-800">
                <div class="text-[10px] text-slate-400">Branco</div>
                <div id="sim-stat-b" class="text-base font-bold text-amber-400">0</div>
              </div>
              <div class="bg-cyan-950/40 p-2.5 rounded-xl border border-cyan-500/40">
                <div class="text-[10px] text-cyan-300">Líquido</div>
                <div id="sim-stat-net" class="text-base font-black text-white">+0</div>
              </div>
            </div>
          </div>

          <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5">
            <div class="flex items-center justify-between mb-3">
              <h3 class="font-bold text-white text-sm">Mapa de Itens do Filtro</h3>
              <button onclick="resetSimulatorProgress()" class="text-[11px] text-slate-400 hover:text-white">Reiniciar marcações</button>
            </div>
            <div id="sim-question-grid" class="grid grid-cols-6 sm:grid-cols-8 gap-1.5 max-h-72 overflow-y-auto custom-scrollbar pr-1">
              <!-- Populated by JS -->
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ==========================================
         TAB 3: CÓDICE PARETO 80/20 (GUIAS DE 15 MIN)
         ========================================== -->
    <section id="tab-codice" class="tab-content hidden space-y-6">
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5">
        <span class="px-2.5 py-0.5 rounded text-[10px] font-mono font-bold bg-amber-500/20 text-amber-300 border border-amber-500/30">ESTRATÉGIA 1 • VELOCIDADE 2</span>
        <h2 class="text-xl font-black text-white mt-1">Códice de Inteligência & Guias Esquematizados de 15 Minutos</h2>
        <p class="text-xs sm:text-sm text-slate-300 mt-1">
          Resumos cirúrgicos de altíssimo ROI com todos os contrastes que o Cebraspe usa para derrubar candidatos na P1, P2 e P3. Clique em qualquer módulo para expandir e marcar como revisado (+30 XP).
        </p>
      </div>

      <div id="codice-modules-container" class="grid grid-cols-1 md:grid-cols-2 gap-5">
        <!-- Populated by JS with ultra-rich technical content -->
      </div>
    </section>

    <!-- ==========================================
         TAB 4: CADERNO DE GAPS DE UMA LINHA
         ========================================== -->
    <section id="tab-gaps" class="tab-content hidden space-y-6">
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 flex flex-col lg:flex-row items-start lg:items-center justify-between gap-4">
        <div>
          <span class="px-2.5 py-0.5 rounded text-[10px] font-mono font-bold bg-purple-500/20 text-purple-300 border border-purple-500/30">ESTRATÉGIA 4 • REVISÃO RELÂMPAGO</span>
          <h2 class="text-xl font-black text-white mt-1">Caderno de Gaps de Uma Linha</h2>
          <p class="text-xs sm:text-sm text-slate-300">
            Abandone resumos longos! Cada erro seu vira uma única frase de contraste cirúrgico. Na Reta Final (Dias 80 a 96), este caderno será sua leitura diária obrigatória.
          </p>
        </div>
        <div class="flex items-center gap-2">
          <button onclick="toggleFlashcardMode()" id="btn-flashcard-mode" class="px-4 py-2.5 rounded-xl bg-purple-500/20 hover:bg-purple-500/30 text-purple-300 border border-purple-500/40 text-xs font-bold flex items-center gap-2 transition">
            <i data-lucide="sparkles" class="w-4 h-4"></i> Modo Quiz / Flashcard
          </button>
        </div>
      </div>

      <!-- Add new 1-line Gap -->
      <form onsubmit="addOneLineGap(event)" class="bg-slate-900/90 border border-purple-500/30 rounded-2xl p-4 flex flex-col md:flex-row gap-3">
        <select id="gap-subject-select" required class="md:w-64 bg-slate-950 border border-slate-700 rounded-xl px-3 py-2.5 text-xs text-white font-medium">
          <!-- Populated by JS -->
        </select>
        <input type="text" id="gap-text-input" required placeholder="Digite a frase de contraste (Ex: [Ato 62/85] Transferência mantém vínculo de propriedade; Recolhimento extingue e passa ao domínio público.)" class="flex-1 bg-slate-950 border border-slate-700 rounded-xl px-4 py-2.5 text-xs sm:text-sm text-white focus:outline-none focus:border-purple-400"/>
        <button type="submit" class="px-5 py-2.5 rounded-xl bg-purple-600 hover:bg-purple-500 text-white font-bold text-xs uppercase tracking-wider transition whitespace-nowrap flex items-center justify-center gap-1.5">
          <i data-lucide="plus" class="w-4 h-4"></i> Inserir Gap (+15 XP)
        </button>
      </form>

      <!-- Filter & List of Gaps -->
      <div class="flex flex-wrap items-center justify-between gap-2">
        <div class="flex items-center gap-2">
          <span class="text-xs text-slate-400">Filtrar por matéria:</span>
          <select id="gap-filter-select" onchange="renderGapsList()" class="bg-slate-900 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-white">
            <option value="ALL">Todas as Matérias</option>
          </select>
        </div>
        <span class="text-xs font-mono text-slate-400">Total de Gaps Blindados: <strong id="gaps-total-badge" class="text-purple-400">0</strong></span>
      </div>

      <div id="gaps-list-container" class="grid grid-cols-1 gap-3">
        <!-- Populated by JS -->
      </div>
    </section>

    <!-- ==========================================
         TAB 5: ENGENHARIA DISCURSIVA (P3 - 60 PONTOS)
         ========================================== -->
    <section id="tab-discursiva" class="tab-content hidden space-y-6">
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5">
        <span class="px-2.5 py-0.5 rounded text-[10px] font-mono font-bold bg-rose-500/20 text-rose-300 border border-rose-500/30">ESTRATÉGIA 3 • PROVA P3 (25% DA NOTA GLOBAL)</span>
        <h2 class="text-xl font-black text-white mt-1">Laboratório de Engenharia Discursiva & Blindagem do Divisor TL</h2>
        <p class="text-xs sm:text-sm text-slate-300 mt-1">
          A Prova Discursiva vale <strong>60,00 pontos</strong> (1 Peça Técnica de 50 linhas = 30 pts + 2 Questões de 20 linhas = 30 pts). Use a calculadora oficial da fórmula Cebraspe e treine Esqueletos de 15 Minutos com Abertura Espelhada.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        
        <!-- Calculadora Oficial NPT = NC - 6 * (NE / TL) -->
        <div class="bg-slate-900 border border-rose-500/30 rounded-2xl p-5 space-y-4">
          <h3 class="font-bold text-white text-base flex items-center gap-2">
            <i data-lucide="calculator" class="w-5 h-5 text-rose-400"></i>
            Simulador da Fórmula Gramatical
          </h3>
          <div class="bg-slate-950 p-3 rounded-xl border border-slate-800 text-center font-mono text-xs text-rose-300">
            NPT = NC - 6 × (NE ÷ TL)
          </div>
          <p class="text-xs text-slate-400">
            Veja matematicamente por que escrever entre <strong>46 e 50 linhas</strong> na Peça Técnica reduz pela metade o impacto de qualquer erro gramatical:
          </p>

          <div class="space-y-3">
            <div>
              <div class="flex justify-between text-xs mb-1">
                <span class="text-slate-300">Nota de Conteúdo (NC - máx 30,00):</span>
                <span id="calc-nc-val" class="font-mono font-bold text-emerald-400">28.50 pts</span>
              </div>
              <input type="range" id="calc-nc" min="10" max="30" step="0.5" value="28.5" oninput="updateDiscursiveCalc()" class="w-full accent-emerald-500"/>
            </div>

            <div>
              <div class="flex justify-between text-xs mb-1">
                <span class="text-slate-300">Número de Erros Gramaticais (NE):</span>
                <span id="calc-ne-val" class="font-mono font-bold text-rose-400">8 erros</span>
              </div>
              <input type="range" id="calc-ne" min="0" max="25" step="1" value="8" oninput="updateDiscursiveCalc()" class="w-full accent-rose-500"/>
            </div>

            <div>
              <div class="flex justify-between text-xs mb-1">
                <span class="text-slate-300">Total de Linhas Efetivas (TL - máx 50):</span>
                <span id="calc-tl-val" class="font-mono font-bold text-cyan-400">49 linhas</span>
              </div>
              <input type="range" id="calc-tl" min="20" max="50" step="1" value="49" oninput="updateDiscursiveCalc()" class="w-full accent-cyan-500"/>
            </div>
          </div>

          <div class="bg-slate-950 rounded-xl p-4 border border-slate-800 space-y-2 font-mono text-xs">
            <div class="flex justify-between">
              <span class="text-slate-400">Desconto Gramatical:</span>
              <span id="calc-penalty" class="text-rose-400 font-bold">-0.98 pts</span>
            </div>
            <div class="flex justify-between">
              <span class="text-slate-400">Se escrevesse só 25 linhas:</span>
              <span id="calc-penalty-25" class="text-slate-500 line-through">-1.92 pts</span>
            </div>
            <div class="flex justify-between pt-2 border-t border-slate-800 text-sm">
              <span class="text-white font-bold">Nota Final da Peça (NPT):</span>
              <span id="calc-npt-final" class="text-emerald-400 font-black">27.52 / 30.00</span>
            </div>
          </div>
        </div>

        <!-- Gerador e Treinador de Esqueletos de 15 Minutos (P3) -->
        <div class="lg:col-span-2 bg-slate-900 border border-slate-800 rounded-2xl p-5 space-y-4">
          <div class="flex flex-wrap items-center justify-between gap-2">
            <h3 class="font-bold text-white text-base flex items-center gap-2">
              <i data-lucide="file-text" class="w-5 h-5 text-cyan-400"></i>
              Temas Quentes P3 & Construtor de Esqueleto em 15 Minutos
            </h3>
            <select id="discursive-theme-select" onchange="loadDiscursiveTheme()" class="bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-white font-mono">
              <!-- Populated by JS -->
            </select>
          </div>

          <div id="discursive-prompt-box" class="bg-slate-950 border border-slate-800 rounded-xl p-4 space-y-2 text-xs text-slate-300">
            <!-- Populated by JS -->
          </div>

          <div>
            <div class="flex items-center justify-between mb-1.5">
              <label class="text-xs font-bold text-slate-300">Seu Esqueleto Tático / Redação com Abertura Espelhada:</label>
              <span id="discursive-line-estimator" class="text-[11px] font-mono text-cyan-400">~0 linhas estimadas</span>
            </div>
            <textarea id="discursive-editor" rows="7" oninput="estimateDiscursiveLines()" placeholder="Treine aqui seu Esqueleto de 15 minutos ou redija o texto aplicando o Check Visual (repetindo literalmente os termos do comando na 1ª frase de cada parágrafo)..." class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-xs sm:text-sm text-white font-mono focus:outline-none focus:border-cyan-500"></textarea>
          </div>

          <div class="flex flex-wrap items-center justify-between gap-3">
            <button onclick="revealDiscursiveModel()" class="px-4 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-amber-300 text-xs font-bold flex items-center gap-1.5 transition">
              <i data-lucide="eye" class="w-4 h-4"></i> Ver Padrão de Resposta Nota 30/30
            </button>
            <button onclick="saveDiscursiveTraining()" class="px-5 py-2 rounded-xl bg-rose-600 hover:bg-rose-500 text-white text-xs font-bold uppercase tracking-wider flex items-center gap-1.5 transition">
              <i data-lucide="check-square" class="w-4 h-4"></i> Salvar Treino Discursivo (+50 XP)
            </button>
          </div>

          <div id="discursive-model-answer" class="hidden bg-emerald-950/30 border border-emerald-500/40 rounded-xl p-4 text-xs text-slate-200 space-y-2">
            <!-- Populated by JS -->
          </div>
        </div>

      </div>
    </section>

    <!-- ==========================================
         TAB 6: MAPA DE 96 DIAS & ARQUITETURA DE ROI
         ========================================== -->
    <section id="tab-cronograma" class="tab-content hidden space-y-6">
      
      <!-- Periodização em 3 Blocos -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div class="bg-slate-900 border border-cyan-500/40 rounded-2xl p-5 space-y-2">
          <div class="flex items-center justify-between">
            <span class="text-xs font-mono font-bold text-cyan-400 uppercase">BLOCO 1 • DIAS 1 A 48</span>
            <span class="text-[11px] font-mono text-slate-400">13/10 a 29/11/2026</span>
          </div>
          <h3 class="font-bold text-white text-base">Construção de Volume Brutal</h3>
          <p class="text-xs text-slate-300">
            100% da carga do edital prioritário (Tiers S, A e B) vencida com <strong>100+ questões/dia</strong> (4.800 questões no bloco) + leitura de 15 min dos guias de RiC, IA/RAG, OAIS e Normas da Câmara.
          </p>
        </div>

        <div class="bg-slate-900 border border-amber-500/40 rounded-2xl p-5 space-y-2">
          <div class="flex items-center justify-between">
            <span class="text-xs font-mono font-bold text-amber-400 uppercase">BLOCO 2 • DIAS 49 A 79</span>
            <span class="text-[11px] font-mono text-slate-400">30/11 a 30/12/2026</span>
          </div>
          <h3 class="font-bold text-white text-base">Aceleração & Cruzamento Normativo</h3>
          <p class="text-xs text-slate-300">
            Baterias mistas de 120 questões/dia, foco cirúrgico nas Normas Internas da Câmara (Portaria 182/20, Atos 62/85 e 206/90, Res. 29/93), cruzamento LAI × LGPD 2026 e Esqueletos Discursivos semanais.
          </p>
        </div>

        <div class="bg-slate-900 border border-rose-500/40 rounded-2xl p-5 space-y-2">
          <div class="flex items-center justify-between">
            <span class="text-xs font-mono font-bold text-rose-400 uppercase">BLOCO 3 • DIAS 80 A 96</span>
            <span class="text-[11px] font-mono text-slate-400">31/12/26 a 17/01/2027</span>
          </div>
          <h3 class="font-bold text-white text-base">Reta Finalíssima & Freio de Mão</h3>
          <p class="text-xs text-slate-300">
            Zero conteúdo novo! Leitura diária do Caderno de Gaps de Uma Linha, revisão dos quadros de prazos (5, 15, 25, 100 anos; 30-45 dias CONARQ 40) e calibragem da Omissão Consciente para cravar 122+ líquidos.
          </p>
        </div>
      </div>

      <!-- Grid dos 96 Dias (13/10/2026 a 17/01/2027) -->
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-2">
          <div>
            <h3 class="font-bold text-white text-base">Tabuleiro Tático dos 96 Dias (9.600+ Questões Até a Prova)</h3>
            <p class="text-xs text-slate-400">Clique em qualquer dia para carregar as estatísticas daquela data ou registrar sua meta retroativa.</p>
          </div>
          <div class="flex items-center gap-3 text-xs font-mono">
            <span class="flex items-center gap-1.5"><span class="w-3 h-3 rounded bg-emerald-500 inline-block"></span> Meta 100Q Batida</span>
            <span class="flex items-center gap-1.5"><span class="w-3 h-3 rounded bg-amber-500 inline-block"></span> Em Andamento</span>
            <span class="flex items-center gap-1.5"><span class="w-3 h-3 rounded bg-slate-800 border border-slate-700 inline-block"></span> Pendente</span>
          </div>
        </div>

        <div id="calendar-96-grid" class="grid grid-cols-4 sm:grid-cols-8 md:grid-cols-12 gap-2">
          <!-- Populated by JS -->
        </div>
      </div>
    </section>

  </main>

  <!-- MODAL: CRIAR QUESTÃO INÉDITA -->
  <div id="modal-new-q" class="fixed inset-0 z-50 hidden bg-slate-950/80 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-slate-900 border border-slate-700 rounded-2xl max-w-lg w-full p-6 space-y-4">
      <div class="flex items-center justify-between">
        <h3 class="font-bold text-white text-base">Adicionar Item Cebraspe ao Simulador</h3>
        <button onclick="closeNewQuestionModal()" class="text-slate-400 hover:text-white"><i data-lucide="x" class="w-5 h-5"></i></button>
      </div>
      <form onsubmit="saveCustomQuestion(event)" class="space-y-3">
        <div>
          <label class="block text-xs text-slate-300 mb-1">Matéria / Eixo</label>
          <select id="new-q-subject" required class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-white"></select>
        </div>
        <div>
          <label class="block text-xs text-slate-300 mb-1">Assertiva Padrão Cebraspe</label>
          <textarea id="new-q-stmt" required rows="3" placeholder="Digite a afirmação técnica para julgamento em CERTO ou ERRADO..." class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-xs text-white"></textarea>
        </div>
        <div>
          <label class="block text-xs text-slate-300 mb-1">Gabarito Oficial</label>
          <select id="new-q-ans" required class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-white font-mono">
            <option value="C">CERTO</option>
            <option value="E">ERRADO</option>
          </select>
        </div>
        <div>
          <label class="block text-xs text-slate-300 mb-1">Comentário / Frase de Contraste (1 Linha)</label>
          <input type="text" id="new-q-exp" required placeholder="Explicação direta do porquê está certo ou errado..." class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-white"/>
        </div>
        <button type="submit" class="w-full py-2.5 rounded-xl bg-cyan-500 hover:bg-cyan-400 text-slate-950 font-bold text-xs uppercase">Salvar no Banco de Questões</button>
      </form>
    </div>
  </div>

  <!-- MODAL: BACKUP / RESTAURAÇÃO JSON -->
  <div id="modal-backup" class="fixed inset-0 z-50 hidden bg-slate-950/80 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-slate-900 border border-slate-700 rounded-2xl max-w-lg w-full p-6 space-y-4">
      <div class="flex items-center justify-between">
        <h3 class="font-bold text-white text-base flex items-center gap-2">
          <i data-lucide="database" class="w-5 h-5 text-cyan-400"></i>
          Central de Persistência e Backup
        </h3>
        <button onclick="closeBackupModal()" class="text-slate-400 hover:text-white"><i data-lucide="x" class="w-5 h-5"></i></button>
      </div>
      <p class="text-xs text-slate-300">
        Seus dados já ficam salvos automaticamente no armazenamento local deste navegador (`localStorage`). Para garantir segurança total ou transferir seu progresso entre dispositivos, copie ou baixe o código abaixo:
      </p>
      <textarea id="backup-json-area" rows="5" class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-[11px] font-mono text-cyan-300"></textarea>
      <div class="flex flex-wrap gap-2">
        <button onclick="exportBackupFile()" class="flex-1 py-2 px-3 rounded-xl bg-cyan-500 hover:bg-cyan-400 text-slate-950 font-bold text-xs flex items-center justify-center gap-1.5">
          <i data-lucide="download" class="w-4 h-4"></i> Baixar Arquivo .JSON
        </button>
        <button onclick="importBackupFromText()" class="flex-1 py-2 px-3 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-bold text-xs flex items-center justify-center gap-1.5">
          <i data-lucide="upload" class="w-4 h-4"></i> Restaurar Dados Colados
        </button>
      </div>
    </div>
  </div>

  <!-- TOAST NOTIFICATION -->
  <div id="toast-box" class="fixed bottom-5 right-5 z-50 hidden bg-slate-900 border border-cyan-500/50 text-white px-4 py-3 rounded-xl shadow-2xl flex items-center gap-3 text-xs font-medium">
    <i data-lucide="check-circle" class="w-4 h-4 text-emerald-400"></i>
    <span id="toast-msg">Progresso gravado!</span>
  </div>

  <script>
    // =========================================================================
    // 1. ESTRUTURA DE DISCIPLINAS, PESOS, TIERS E METAS DIÁRIAS (100 Q/DIA)
    // =========================================================================
    const SUBJECTS = [
      {
        id: 'S_PRESERV',
        tier: 'S',
        name: 'Preservação Digital, Sistemas (e-ARQ/SIGAD/RDC-Arq) e OAIS/PREMIS',
        short: 'Preservação/OAIS/PREMIS',
        dailyQuota: 18,
        pointsPotential: '56 pts (P2 + Peça P3)',
        speed: 'Velocidade 2 (Guia 15m + Questões)',
        desc: 'SIGAD vs GED, Autenticidade vs Integridade, SIP->AIP->DIP, 4 entidades PREMIS, Archivematica vs AtoM, WARC.'
      },
      {
        id: 'S_GESTAO_CD',
        tier: 'S',
        name: 'Arquivologia Clássica, PCD/TTD e Normas Internas da Câmara',
        short: 'Gestão/PCD/Normas CD',
        dailyQuota: 14,
        pointsPotential: '40 pts (P2 + P3)',
        speed: 'Velocidade 1 & 2 (Portaria 182/20, Atos 62/85, 206/90)',
        desc: 'Lei 8.159, Res. CONARQ 40/41/43, Portaria DG 182/2020, Ato 62/85 (Transferência x Recolhimento), Ato 206/90 (CADAr), Res. 29/93 (CEDS).'
      },
      {
        id: 'S_LAI_LGPD',
        tier: 'S',
        name: 'LAI (12.527) + LGPD Atualizada (Lei 15.352/2026) + Dir. Adm',
        short: 'LAI + LGPD 2026',
        dailyQuota: 10,
        pointsPotential: '35 pts (P1 + P2 + P3)',
        speed: 'Velocidade 1 & 2 (Reforma ANPD 2026)',
        desc: 'Prazos 5/15/25/100 anos, Art. 16 LGPD, Anonimizado vs Pseudonimizado, ANPD Agência vinculada ao MJSP, DPO no Controlador e Operador.'
      },
      {
        id: 'S_PORT',
        tier: 'S',
        name: 'Língua Portuguesa Cebraspe (Interpretação, Coesão, Sintaxe e Reescrita)',
        short: 'Português Cebraspe',
        dailyQuota: 8,
        pointsPotential: '34 pts (28 P1 + 6 Blindagem P3)',
        speed: 'Velocidade 1 (Estudo Reverso Puro)',
        desc: 'Reescrita de períodos, coesão referencial, vírgula em orações adjetivas, partícula SE, crase e proteção do divisor TL na discursiva.'
      },
      {
        id: 'A_RIC_CI',
        tier: 'A',
        name: 'Ciência da Informação, Metadados e Records in Contexts (RiC vs NOBRADE)',
        short: 'RiC-CM/RiC-O vs NOBRADE',
        dailyQuota: 12,
        pointsPotential: '30 pts (P2 + Questão P3)',
        speed: 'Velocidade 2 (Grafo Policêntrico N:N)',
        desc: 'Árvore 1:N vs Grafo N:N, Record vs Instantiation, Mechanism (agentes robôs/softwares), Triplas RDF, Interoperabilidade Sintática vs Semântica.'
      },
      {
        id: 'A_IA_RAG',
        tier: 'A',
        name: 'Inteligência Artificial (LLMs, RAG, Alucinação, OCR/HTR) e BI',
        short: 'IA Generativa / RAG / OCR-HTR',
        dailyQuota: 10,
        pointsPotential: '32 pts (P1 + P2 + P3)',
        speed: 'Velocidade 2 (Arquitetura RAG em Acervos)',
        desc: 'RAG conectando LLM ao repositório confiável, OCR (impresso) vs HTR (manuscrito), Precisão (ruído) vs Revocação (silêncio), Human-in-the-Loop.'
      },
      {
        id: 'A_GOV_DADOS',
        tier: 'A',
        name: 'Governança de Dados (DAMA-DMBOK, Linhagem, Data Owner vs Steward)',
        short: 'Governança DAMA-DMBOK',
        dailyQuota: 8,
        pointsPotential: '20 pts (P1 + P2)',
        speed: 'Velocidade 2 (Papel do Arquivista)',
        desc: 'Data Owner (decisão executiva) vs Data Steward (curadoria técnica/arquivista), Linhagem de dados, Qualidade e Catálogo de Dados.'
      },
      {
        id: 'B_CONST_REG',
        tier: 'B',
        name: 'Direito Constitucional (Art. 5º e Arts. 44-58) + Artigos-Chave RICD',
        short: 'Constitucional Legislativo',
        dailyQuota: 8,
        pointsPotential: '14 pts (P1)',
        speed: 'Velocidade 1 (Art. 49 vs 51 vs 52 + CPIs)',
        desc: 'Competências exclusivas do CN (Art. 49) vs privativas da Câmara (Art. 51) e Senado (Art. 52); CPIs (Art. 58 §3º).'
      },
      {
        id: 'B_LIC_ADM',
        tier: 'B',
        name: 'Nova Lei de Licitações (14.133 - 4 Pilares), Lei 8.112 e Dec. 9.203',
        short: 'Licitações 14.133 + Dec. 9.203',
        dailyQuota: 6,
        pointsPotential: '14 pts (P1)',
        speed: 'Velocidade 1 (Inexigibilidade x Dispensa)',
        desc: 'Modalidades (Diálogo Competitivo; fim de tomada/convite), Inexigibilidade (Art. 74) vs Dispensa (Art. 75), Governança Dec. 9.203/17.'
      },
      {
        id: 'B_SQL_REGEX',
        tier: 'B',
        name: 'SQL Básico (5 Cláusulas), Expressões Regulares (Regex), APIs e Power BI',
        short: 'SQL + Regex + Power BI',
        dailyQuota: 6,
        pointsPotential: '12 pts (P1 + P2)',
        speed: 'Velocidade 1 & 2 (Leitura Visual)',
        desc: 'Cláusulas SELECT, FROM, WHERE, ORDER BY, JOIN; Metacaracteres Regex (\\d, {n}, +, *, ?); DAX básico e visualização.'
      }
    ];

    // =========================================================================
    // 2. BANCO DE QUESTÕES CEBRASPE (ALTA COMPLEXIDADE - PADRÃO CÂMARA)
    // =========================================================================
    const INITIAL_QUESTIONS = [
      // TIER S - PRESERVAÇÃO DIGITAL, OAIS, PREMIS, e-ARQ, RDC-ARQ
      {
        id: 'Q1', subject: 'S_PRESERV', tier: 'S',
        stmt: 'Segundo o modelo de referência OAIS (ISO 14721), os metadados de preservação no padrão PREMIS devem vir obrigatoriamente encapsulados dentro do Pacote de Submissão de Informação (SIP) enviado pelo produtor, cabendo ao repositório apenas validá-los na transferência para o AIP.',
        ans: 'E',
        exp: '[OAIS/PREMIS] O SIP enviado pelo produtor NÃO exige PREMIS completo; os metadados PREMIS (Object, Event, Agent, Rights) são gerados/registrados durante o processo de ingestão (ex: no Archivematica) para compor o AIP.'
      },
      {
        id: 'Q2', subject: 'S_PRESERV', tier: 'S',
        stmt: 'Na arquitetura integrada de preservação e acesso adotada em repositórios arquivísticos digitais confiáveis (RDC-Arq), o software Archivematica atua no processamento e geração do AIP (backend de preservação), enquanto o AtoM (Access to Memory) atua como plataforma de descrição e difusão dos pacotes DIP (frontend de acesso).',
        ans: 'C',
        exp: '[Archivematica x AtoM] Divisão clássica de RDC-Arq: Archivematica processa microsserviços de ingestão e guarda o AIP; AtoM consome o DIP para difusão e descrição multinível.'
      },
      {
        id: 'Q3', subject: 'S_PRESERV', tier: 'S',
        stmt: 'De acordo com o e-ARQ Brasil (versão revisada), um Sistema Informatizado de Gestão Arquivística de Documentos (SIGAD) distingue-se de um simples GED porque o SIGAD controla o ciclo de vida documental a partir do Plano de Classificação e da Tabela de Temporalidade e Destinação (TTD) desde a captura.',
        ans: 'C',
        exp: '[e-ARQ Brasil] SIGAD incorpora obrigatoriamente PCD e TTD para gerir o ciclo vital; o GED trata documentos de forma compartimentada sem controle arquivístico de temporalidade.'
      },
      {
        id: 'Q4', subject: 'S_PRESERV', tier: 'S',
        stmt: 'No dicionário de dados PREMIS 3.0, as quatro entidades fundamentais que estruturam os metadados de preservação digital são: Object (Objeto), Event (Evento), Agent (Agente) e Rights (Direitos), sendo a propriedade Intelectual (Intellectual Entity) tratada atualmente como uma subcategoria da entidade Object.',
        ans: 'C',
        exp: '[PREMIS 3.0] As 4 entidades do modelo PREMIS são Object, Event, Agent e Rights. Intellectual Entity passou a ser um nível de Object (junto com Representation, File e Bitstream).'
      },
      {
        id: 'Q5', subject: 'S_PRESERV', tier: 'S',
        stmt: 'A realização de migração de formato de um documento arquivístico digital (por exemplo, de DOCX para PDF/A-1b) durante a admissão no RDC-Arq preserva tanto a autenticidade quanto a integridade da cadeia de bits (bitstream) original do objeto.',
        ans: 'E',
        exp: '[Autenticidade x Integridade] A migração altera a cadeia de bits (quebra a integridade física do bitstream original), mas mantém a AUTENTICIDADE documental se devidamente registrada em metadados de evento PREMIS.'
      },
      {
        id: 'Q6', subject: 'S_PRESERV', tier: 'S',
        stmt: 'O formato WARC (Web ARChive, ISO 28500) é o padrão internacional recomendado para o arquivamento da web legislativa, pois permite encapsular não apenas o conteúdo HTML coletado, mas também os cabeçalhos HTTP de requisição e resposta, garantindo o contexto técnico da captura.',
        ans: 'C',
        exp: '[Formato WARC] O WARC armazena o recurso web junto com os cabeçalhos HTTP (request/response) e metadados de coleta (harvesting), sendo superior ao antigo ARC.'
      },

      // TIER S - NORMAS DA CÂMARA E GESTÃO DOCUMENTAL
      {
        id: 'Q7', subject: 'S_GESTAO_CD', tier: 'S',
        stmt: 'Conforme a Portaria DG da Câmara dos Deputados nº 182/2020, o conceito de "Arquivo Impresso" refere-se ao documento originalmente nascido físico em suporte papel que foi posteriormente submetido à digitalização com certificação digital ICP-Brasil.',
        ans: 'E',
        exp: '[Portaria CD 182/2020] Pegadinha clássica! Na Portaria 182/2020, "Arquivo Impresso" é a versão impressa (em papel) de um documento digital ou nato-digital, e não um documento nato-físico digitalizado.'
      },
      {
        id: 'Q8', subject: 'S_GESTAO_CD', tier: 'S',
        stmt: 'Nos termos do Ato da Mesa da Câmara dos Deputados nº 62/1985, a operação de transferência de documentos ao Arquivo mantém o vínculo de propriedade com a unidade administrativa produtora, ao passo que o recolhimento extingue esse vínculo e incorpora a documentação ao patrimônio público permanente.',
        ans: 'C',
        exp: '[Ato da Mesa 62/1985] Na Câmara, a Transferência (para o arquivo intermediário) mantém o vínculo de propriedade com o órgão produtor; o Recolhimento (permanente) cessa esse vínculo.'
      },
      {
        id: 'Q9', subject: 'S_GESTAO_CD', tier: 'S',
        stmt: 'De acordo com a Portaria DG nº 182/2020, a Coordenação de Arquivo (Coarq) detém a prerrogativa de requisitar compulsoriamente documentos arquivísticos de valor permanente que estejam retidos indevidamente nas unidades administrativas da Câmara dos Deputados.',
        ans: 'C',
        exp: '[Portaria CD 182/2020] A Coarq possui poder de requisição compulsória sobre acervos permanentes ou documentos não recolhidos no prazo pelas unidades da Casa.'
      },
      {
        id: 'Q10', subject: 'S_GESTAO_CD', tier: 'S',
        stmt: 'Segundo a Resolução CONARQ nº 40/2014, após a publicação do Edital de Ciência de Eliminação de Documentos no Diário Oficial, deve-se aguardar o prazo mínimo de 15 dias corridos para a efetiva fragmentação mecânica do acervo.',
        ans: 'E',
        exp: '[Resolução CONARQ 40/2014] O prazo do Edital de Ciência de Eliminação é de 30 a 45 dias (e não 15 dias) para que interessados possam requerer o desentranhamento ou cópias.'
      },
      {
        id: 'Q11', subject: 'S_GESTAO_CD', tier: 'S',
        stmt: 'O Ato da Mesa nº 206/1990 instituiu a Comissão de Avaliação de Documentos de Arquivo (CADAr) na Câmara dos Deputados, definindo seus membros natos para conduzir o processo de análise e validação das tabelas de temporalidade da Casa.',
        ans: 'C',
        exp: '[Ato da Mesa 206/1990] O Ato 206/90 rege a CADAr na Câmara dos Deputados, enquanto a Resolução CD nº 29/1993 trata da Comissão Especial de Documentos Sigilosos (CEDS).'
      },
      {
        id: 'Q12', subject: 'S_GESTAO_CD', tier: 'S',
        stmt: 'Pelo princípio arquivístico da territorialidade, documentos produzidos por uma comissão parlamentar da Câmara em diligência oficial no exterior pertencem aos arquivos públicos do país estrangeiro onde o ato foi praticado.',
        ans: 'E',
        exp: '[Territorialidade / Proveniência] Exceção clássica: representações diplomáticas, missões parlamentares ou militares no exterior vinculam-se ao fundo da instituição produtora (Câmara dos Deputados), não ao território estrangeiro.'
      },

      // TIER S - LAI + LGPD (ATUALIZADA PELA LEI 15.352/2026)
      {
        id: 'Q13', subject: 'S_LAI_LGPD', tier: 'S',
        stmt: 'Com a reforma promovida pela Lei nº 15.352/2026 na estrutura da proteção de dados no Brasil, a Autoridade Nacional de Proteção de Dados (ANPD) consolidou sua natureza jurídica como agência reguladora integrante da administração indireta, vinculada ao Ministério da Justiça e Segurança Pública (MJSP).',
        ans: 'C',
        exp: '[LGPD + Lei 15.352/2026] A ANPD possui natureza de autarquia especial / agência reguladora vinculada ao MJSP, e não mais órgão da Presidência da República.'
      },
      {
        id: 'Q14', subject: 'S_LAI_LGPD', tier: 'S',
        stmt: 'À luz da LGPD atualizada, o Encarregado pelo tratamento de dados pessoais (DPO) é classificado juridicamente como um terceiro agente de tratamento, respondendo solidariamente com o controlador e o operador pelos danos causados aos titulares.',
        ans: 'E',
        exp: '[LGPD 2026] Agentes de tratamento são APENAS o Controlador e o Operador. O Encarregado (DPO) é indicado pelo controlador e pelo operador, mas NÃO é agente de tratamento nem responde civilmente nessa qualidade.'
      },
      {
        id: 'Q15', subject: 'S_LAI_LGPD', tier: 'S',
        stmt: 'Nos termos do art. 16 da LGPD, os dados pessoais devem ser obrigatoriamente eliminados após o término de seu tratamento, sendo vedada sua conservação pelos arquivos públicos mesmo para fins de cumprimento de obrigação legal ou estudo por órgão de pesquisa.',
        ans: 'E',
        exp: '[Art. 16 LGPD x TTD] O art. 16 da LGPD AUTORIZA expressamente a conservação de dados pessoais após o término do tratamento para: I - cumprimento de obrigação legal/regulatória (TTD arquivística) e II - estudo por órgão de pesquisa.'
      },
      {
        id: 'Q16', subject: 'S_LAI_LGPD', tier: 'S',
        stmt: 'Na LGPD, o dado pseudonimizado deixa de ser considerado dado pessoal e fica fora do escopo de incidência da lei, independentemente de a informação adicional capaz de reidentificar o titular ser mantida separadamente pelo controlador.',
        ans: 'E',
        exp: '[Anonimizado x Pseudonimizado] Apenas o dado ANONIMIZADO (irreversível) fica fora da LGPD (art. 12). O dado PSEUDONIMIZADO (art. 13, §4º) permite reidentificação por chave separada e CONTINUA sujeito à LGPD!'
      },
      {
        id: 'Q17', subject: 'S_LAI_LGPD', tier: 'S',
        stmt: 'As hipóteses legais do legítimo interesse do controlador e da proteção do crédito NÃO podem ser invocadas para fundamentar o tratamento de dados pessoais sensíveis na LGPD.',
        ans: 'C',
        exp: '[Dados Sensíveis - Art. 11 LGPD] O art. 11 não contempla legítimo interesse nem proteção ao crédito! Essas duas bases valem apenas para dados pessoais comuns (art. 7º, IX e X).'
      },
      {
        id: 'Q18', subject: 'S_LAI_LGPD', tier: 'S',
        stmt: 'De acordo com a Lei de Acesso à Informação (Lei nº 12.527/2011), informações pessoais relativas à intimidade, vida privada, honra e imagem terão seu acesso restrito pelo prazo máximo de 100 anos a contar da sua data de produção, independentemente de classificação de sigilo.',
        ans: 'C',
        exp: '[Art. 31 LAI] Informações pessoais sensíveis/intimidade têm restrição de até 100 anos a partir da produção, INDEPENDENTEMENTE de classificação em reservado (5), secreto (15) ou ultrassecreto (25).'
      },

      // TIER S - PORTUGUÊS CEBRASPE
      {
        id: 'Q19', subject: 'S_PORT', tier: 'S',
        stmt: 'No período "Os documentos legislativos que possuem valor histórico permanente não podem ser eliminados", a inserção de vírgulas imediatamente após "legislativos" e após "permanente" manteria a correção gramatical do texto, mas alteraria seu sentido original.',
        ans: 'C',
        exp: '[Sintaxe / Pontuação Cebraspe] A oração adjetiva restritiva (sem vírgulas) passaria a ser explicativa (com vírgulas): a correção gramatical é mantida, mas o sentido muda (passaria a afirmar que TODOS os documentos legislativos possuem valor histórico).'
      },
      {
        id: 'Q20', subject: 'S_PORT', tier: 'S',
        stmt: 'Na frase "Procedeu-se à eliminação dos autos findos conforme o edital", a partícula "se" classifica-se como pronome apassivador, razão pela qual a locução "à eliminação" exerce a função de sujeito paciente.',
        ans: 'E',
        exp: '[Partícula SE + Regência] O verbo "proceder" no sentido de realizar é transitivo indireto (quem procede, procede A algo). Logo, o "se" é Índice de Indeterminação do Sujeito (IIS), e não pronome apassivador!'
      },
      {
        id: 'Q21', subject: 'S_PORT', tier: 'S',
        stmt: 'Em "A preservação digital, cujos requisitos técnicos constam no e-ARQ Brasil, exige investimento contínuo", a substituição de "cujos requisitos técnicos" por "a qual os requisitos técnicos" preservaria a correção gramatical do período.',
        ans: 'E',
        exp: '[Pronome Relativo CUJO] "Cujo" indica posse e jamais pode ser substituído por "o qual / a qual / que" sem preposição de posse.'
      },

      // TIER A - RECORDS IN CONTEXTS (RiC) & CIÊNCIA DA INFORMAÇÃO
      {
        id: 'Q22', subject: 'A_RIC_CI', tier: 'A',
        stmt: 'A norma Records in Contexts (RiC), desenvolvida pelo Conselho Internacional de Arquivos (ICA), promove uma mudança de paradigma em relação à ISAD(G) e à NOBRADE ao substituir a descrição hierárquica monocêntrica em árvore (1:N) por um modelo de grafo policêntrico e multidimensional (N:N).',
        ans: 'C',
        exp: '[RiC vs NOBRADE] A NOBRADE/ISAD(G) baseia-se numa árvore hierárquica rígida (Fundo > Seção > Série > Dossiê > Item). O RiC-CM e o RiC-O adotam uma rede/grafo multidimensional onde um documento pode conectar-se a múltiplos contextos e agentes.'
      },
      {
        id: 'Q23', subject: 'A_RIC_CI', tier: 'A',
        stmt: 'No Modelo Conceitual do Records in Contexts (RiC-CM), a entidade "Record" (Documento) confunde-se com o seu suporte físico ou arquivo digital, não havendo distinção entre o conteúdo intelectual e a sua representação material.',
        ans: 'E',
        exp: '[RiC-CM: Record vs Instantiation] O RiC separa rigorosamente o documento intelectual ("Record" / "Record Set") de sua materialização física ou digital ("Instantiation"). Um único Record pode ter múltiplas Instantiations (ex: original em pergaminho + matriz TIFF + derivada PDF/A).'
      },
      {
        id: 'Q24', subject: 'A_RIC_CI', tier: 'A',
        stmt: 'Na modelagem da entidade Agente (Agent) do Records in Contexts (RiC-CM), além de Pessoas, Famílias e Entidades Coletivas, inclui-se a subentidade "Mechanism" (Mecanismo), permitindo descrever softwares, algoritmos ou sensores automatizados que produzem ou gerenciam documentos.',
        ans: 'C',
        exp: '[RiC-CM: Mechanism] Grande inovação do RiC! A subentidade Mechanism reconhece sistemas informatizados, robôs e agentes de software como agentes no contexto de produção/gestão documental.'
      },
      {
        id: 'Q25', subject: 'A_RIC_CI', tier: 'A',
        stmt: 'A ontologia RiC-O (Records in Contexts - Ontology), expressa em OWL/RDF para a Web Semântica, estrutura o conhecimento arquivístico por meio de triplas semânticas no formato Sujeito → Predicado → Objeto.',
        ans: 'C',
        exp: '[RiC-O / RDF] O RiC-O utiliza o padrão RDF/OWL da W3C, representando relações em grafos de conhecimento por meio de triplas (Subject - Predicate - Object).'
      },
      {
        id: 'Q26', subject: 'A_RIC_CI', tier: 'A',
        stmt: 'Enquanto a interoperabilidade sintática preocupa-se com o formato estrutural de troca de dados (como XML e JSON), a interoperabilidade semântica garante que o significado preciso dos conceitos seja compartilhado entre sistemas heterogêneos por meio de tesauros, taxonomias e ontologias.',
        ans: 'C',
        exp: '[Interoperabilidade Sintática x Semântica] Sintática = estrutura/gramática de dados (XML, JSON, CSV). Semântica = significado inequívoco do domínio (SKOS, OWL, Tesauros, Ontologias).'
      },

      // TIER A - IA GENERATIVA, RAG, OCR/HTR, MÉTRICAS
      {
        id: 'Q27', subject: 'A_IA_RAG', tier: 'A',
        stmt: 'Na aplicação de Grandes Modelos de Linguagem (LLMs) a acervos legislativos, a arquitetura RAG (Retrieval-Augmented Generation) exige o retreinamento completo dos pesos neurais do modelo (fine-tuning) a cada novo projeto de lei protocolado na Câmara dos Deputados.',
        ans: 'E',
        exp: '[Arquitetura RAG] O RAG NÃO exige retreinamento (fine-tuning) dos pesos do LLM! Ele faz uma busca vetorial/semântica externa no repositório confiável da Câmara e injeta os trechos recuperados no prompt para ancorar a resposta e evitar alucinações.'
      },
      {
        id: 'Q28', subject: 'A_IA_RAG', tier: 'A',
        stmt: 'Para a conversão em texto pesquisável de atas parlamentares manuscritas do século XIX pertencentes ao Arquivo Histórico da Câmara, a tecnologia indicada é o HTR (Handwritten Text Recognition), que utiliza redes neurais profundas para reconhecer caligrafias cursivas históricas, superando as limitações do OCR tradicional.',
        ans: 'C',
        exp: '[OCR vs HTR] OCR (Optical Character Recognition) é voltado a textos impressos/tipográficos; HTR (Handwritten Text Recognition, ex: Transkribus) reconhece manuscritos históricos.'
      },
      {
        id: 'Q29', subject: 'A_IA_RAG', tier: 'A',
        stmt: 'Em sistemas de recuperação da informação arquivística, o aumento da métrica de Revocação (Recall) visa combater o "ruído" (documentos irrelevantes recuperados), enquanto a Precisão (Precision) visa combater o "silêncio" (documentos relevantes que deixaram de ser recuperados).',
        ans: 'E',
        exp: '[Precisão vs Revocação] O item inverteu os conceitos! PRECISÃO combate o RUÍDO (mede a pureza dos resultados retornados); REVOCAÇÃO (Recall) combate o SILÊNCIO (mede a capacidade de encontrar todos os documentos relevantes existentes no acervo).'
      },

      // TIER A - GOVERNANÇA DE DADOS (DAMA-DMBOK)
      {
        id: 'Q30', subject: 'A_GOV_DADOS', tier: 'A',
        stmt: 'Segundo o guia DAMA-DMBOK, o Data Steward (Custodiante/Curador de Dados) é o executivo de alto escalão que detém a propriedade política do ativo de dados, enquanto o Data Owner atua exclusivamente na configuração operacional de backups de banco de dados.',
        ans: 'E',
        exp: '[Data Owner x Data Steward] Invertido! O Data Owner é a autoridade executiva/negocial responsável pela decisão sobre o domínio de dados; o Data Steward (papel ideal do arquivista/cientista da informação) executa a curadoria técnica, qualidade, metadados e regras de negócio.'
      },
      {
        id: 'Q31', subject: 'A_GOV_DADOS', tier: 'A',
        stmt: 'A linhagem de dados (Data Lineage) permite rastrear a origem, a movimentação e todas as transformações sofridas por um conjunto de dados ao longo do seu ciclo de vida, aproximando-se conceitualmente da cadeia de custódia e proveniência arquivística.',
        ans: 'C',
        exp: '[Linhagem de Dados] Data Lineage documenta de onde o dado veio, por quais pipelines (ETL/ELT) passou e como foi transformado, garantindo auditabilidade e rastreabilidade.'
      },

      // TIER B - DIREITO CONSTITUCIONAL, LICITAÇÕES, SQL E REGEX
      {
        id: 'Q32', subject: 'B_CONST_REG', tier: 'B',
        stmt: 'Nos termos da Constituição Federal de 1988, compete privativamente à Câmara dos Deputados autorizar, por dois terços de seus membros, a instauração de processo contra o Presidente e o Vice-Presidente da República e os Ministros de Estado.',
        ans: 'C',
        exp: '[CF/88 Art. 51, I] Competência privativa da Câmara dos Deputados: autorizar por 2/3 a instauração de processo (juízo de admissibilidade). O julgamento nos crimes de responsabilidade cabe ao Senado (Art. 52, I).'
      },
      {
        id: 'Q33', subject: 'B_CONST_REG', tier: 'B',
        stmt: 'As Comissões Parlamentares de Inquérito (CPIs) possuem poderes de investigação próprios das autoridades judiciais, podendo decretar diretamente a quebra de sigilo bancário, fiscal e de dados telefônicos (registros de chamadas), bem como determinar a interceptação telefônica (escuta ambiental).',
        ans: 'E',
        exp: '[CPIs - Art. 58 §3º CF + STF] CPI pode quebrar sigilo bancário, fiscal e de DADOS telefônicos (extrato de ligações), mas NÃO pode determinar interceptação telefônica (grampo/escuta), que exige reserva de jurisdição (ordem judicial).'
      },
      {
        id: 'Q34', subject: 'B_LIC_ADM', tier: 'B',
        stmt: 'A Nova Lei de Licitações e Contratos (Lei nº 14.133/2021) extinguiu as modalidades Tomada de Preços, Convite e RDC, introduzindo a modalidade Diálogo Competitivo para contratações que envolvam inovação tecnológica ou técnica em que a Administração não possa definir as especificações com precisão suficiente.',
        ans: 'C',
        exp: '[Lei 14.133/2021 - Modalidades] As 5 modalidades atuais são: Pregão, Concorrência, Concurso, Leilão e Diálogo Competitivo. Tomada de preços e convite foram extintos.'
      },
      {
        id: 'Q35', subject: 'B_LIC_ADM', tier: 'B',
        stmt: 'Na Lei nº 14.133/2021, a contratação de profissional do setor artístico consagrado pela crítica ou de serviços técnicos especializados de natureza predominantemente intelectual com profissionais de notória especialização configura hipótese de dispensa de licitação.',
        ans: 'E',
        exp: '[Inexigibilidade x Dispensa] Inviabilidade de competição (fornecedor exclusivo, artista consagrado, serviço técnico intelectual com notória especialização e credenciamento) é INEXIGIBILIDADE (art. 74), e não dispensa (art. 75).'
      },
      {
        id: 'Q36', subject: 'B_SQL_REGEX', tier: 'B',
        stmt: 'Em uma expressão regular (Regex) aplicada à validação de metadados legislativos, o padrão ^\\d{5}-\\d{3}$ valida exatamente uma string composta por cinco dígitos numéricos, seguidos de hífen e três dígitos numéricos, como um código de CEP.',
        ans: 'C',
        exp: '[Regex] ^ indica início da linha, \\d{5} exige exatos 5 dígitos numéricos, - exige o hífen literal, \\d{3} exige 3 dígitos e $ indica fim da linha.'
      },
      {
        id: 'Q37', subject: 'B_SQL_REGEX', tier: 'B',
        stmt: 'Na linguagem SQL, a cláusula WHERE é utilizada para filtrar grupos de registros após a aplicação de funções de agregação na cláusula GROUP BY, enquanto a cláusula HAVING filtra linhas individuais antes do agrupamento.',
        ans: 'E',
        exp: '[SQL: WHERE vs HAVING] Invertido! WHERE filtra linhas individuais ANTES do GROUP BY; HAVING filtra os grupos resultantes DEPOIS do GROUP BY.'
      }
    ];

    // =========================================================================
    // 3. CÓDICE DE INTELIGÊNCIA (GUIAS ESQUEMATIZADOS DE 15 MINUTOS)
    // =========================================================================
    const CODICE_MODULES = [
      {
        id: 'MOD_1',
        tier: 'TIER S • DIAMANTE',
        title: '1. Arquitetura OAIS (ISO 14721), PREMIS 3.0, Archivematica & AtoM',
        points: 'Potencial: 56 Pontos (P2 + Peça Técnica P3)',
        content: `
          <div class="space-y-3 text-xs text-slate-300 leading-relaxed">
            <div class="p-3 bg-slate-950 rounded-xl border border-cyan-500/30">
              <strong class="text-cyan-400 block mb-1">Fluxo dos Pacotes no Modelo OAIS:</strong>
              <ul class="list-disc pl-4 space-y-1">
                <li><strong>SIP (Submission Information Package):</strong> Enviado pelo <em>Produtor</em> ao repositório na fase de Ingestão. Ainda NÃO contém toda a estrutura PREMIS de preservação.</li>
                <li><strong>AIP (Archival Information Package):</strong> Gerado na Ingestão (pelo <strong>Archivematica</strong>) e armazenado no <em>Armazenamento Arquivístico</em>. Contém o objeto digital + PDI (Preservation Description Information: Referência, Contexto, Proveniência, Fixidez [Hash/Checksum] e Direitos) + Metadados <strong>PREMIS</strong> encapsulados em <strong>METS</strong>.</li>
                <li><strong>DIP (Dissemination Information Package):</strong> Derivada gerada para o <em>Consumidor/Usuário</em> acessar na plataforma de difusão (<strong>AtoM</strong>).</li>
              </ul>
            </div>
            <div class="p-3 bg-slate-950 rounded-xl border border-slate-800">
              <strong class="text-emerald-400 block mb-1">As 4 Entidades do PREMIS 3.0:</strong>
              <p><strong>1. Object</strong> (Intellectual Entity, Representation, File, Bitstream) • <strong>2. Event</strong> (Ações de preservação: ingestão, migração, verificação de vírus/fixidez) • <strong>3. Agent</strong> (Pessoas, organizações ou softwares vinculados aos eventos) • <strong>4. Rights</strong> (Permissões e bases legais).</p>
            </div>
            <div class="p-3 bg-slate-950 rounded-xl border border-slate-800">
              <strong class="text-amber-400 block mb-1">Contraste Fatal Cebraspe (Autenticidade vs. Integridade):</strong>
              <p>Converter um arquivo de Word (.docx) para <strong>PDF/A</strong> durante a normalização no Archivematica <strong>altera a cadeia de bits (bitstream)</strong>, mas <strong>preserva a autenticidade</strong> porque o evento de migração fica documentado na trilha de auditoria PREMIS!</p>
            </div>
          </div>
        `
      },
      {
        id: 'MOD_2',
        tier: 'TIER S • DIAMANTE',
        title: '2. Normas Internas da Câmara dos Deputados & CONARQ',
        points: 'Potencial: 40 Pontos (P2 + Fundamentação Legal da P3)',
        content: `
          <div class="space-y-3 text-xs text-slate-300 leading-relaxed">
            <div class="p-3 bg-slate-950 rounded-xl border border-cyan-500/30">
              <strong class="text-cyan-400 block mb-1">Portaria DG nº 182/2020 (Gestão Documental na CD):</strong>
              <ul class="list-disc pl-4 space-y-1">
                <li><strong>Arquivo Impresso:</strong> É a cópia impressa em papel de um documento digital (não confunda com documento nato-físico digitalizado!).</li>
                <li><strong>Suporte vs. Formato:</strong> Suporte é a base física/material (papel, disco magnético); Formato é a estrutura lógica de codificação de bits (PDF/A, XML, TIFF).</li>
                <li><strong>Poder da Coarq:</strong> A Coordenação de Arquivo pode <strong>requisitar compulsoriamente</strong> documentos de valor permanente retidos nas unidades da Câmara.</li>
              </ul>
            </div>
            <div class="p-3 bg-slate-950 rounded-xl border border-slate-800">
              <strong class="text-emerald-400 block mb-1">Atos da Mesa e Resoluções da Câmara:</strong>
              <ul class="list-disc pl-4 space-y-1">
                <li><strong>Ato da Mesa nº 62/1985:</strong> Na <em>Transferência</em> (arquivo intermediário), o setor produtor <strong>mantém o vínculo de propriedade</strong>; no <em>Recolhimento</em> (arquivo permanente), <strong>extingue-se o vínculo</strong> e passa ao domínio público.</li>
                <li><strong>Ato da Mesa nº 206/1990:</strong> Estrutura e membros natos da <strong>CADAr</strong> (Comissão de Avaliação de Documentos de Arquivo).</li>
                <li><strong>Resolução CD nº 29/1993:</strong> Rege a <strong>CEDS</strong> (Comissão Especial de Documentos Sigilosos).</li>
                <li><strong>Resolução CONARQ nº 40/2014:</strong> Prazo de <strong>30 a 45 dias</strong> após publicação do Edital de Ciência de Eliminação antes da fragmentação.</li>
              </ul>
            </div>
          </div>
        `
      },
      {
        id: 'MOD_3',
        tier: 'TIER S • DIAMANTE',
        title: '3. LAI (Lei 12.527/11) + LGPD Atualizada (Lei 15.352/2026)',
        points: 'Potencial: 35 Pontos (Incidência Tripla P1 + P2 + P3)',
        content: `
          <div class="space-y-3 text-xs text-slate-300 leading-relaxed">
            <div class="p-3 bg-slate-950 rounded-xl border border-cyan-500/30">
              <strong class="text-cyan-400 block mb-1">Quadro de Prazos da LAI vs. LGPD:</strong>
              <ul class="list-disc pl-4 space-y-1">
                <li><strong>Reservado:</strong> 5 anos • <strong>Secreto:</strong> 15 anos • <strong>Ultrassecreto:</strong> 25 anos (prorrogável 1 vez pela CMRI).</li>
                <li><strong>Informação Pessoal (Intimidade/Honra/Imagem - Art. 31 LAI):</strong> Restrição máxima de <strong>100 anos</strong> a contar da data de produção, <em>independentemente de classificação de sigilo</em>.</li>
                <li><strong>Art. 16 da LGPD (Salvaguarda Arquivística):</strong> Permite conservar dados pessoais após o término do tratamento para <strong>cumprimento de obrigação legal/regulatória (TTD)</strong> e <strong>estudo por órgão de pesquisa</strong> (garantida, sempre que possível, a anonimização).</li>
              </ul>
            </div>
            <div class="p-3 bg-slate-950 rounded-xl border border-slate-800">
              <strong class="text-rose-400 block mb-1">Atualização da Lei nº 15.352/2026 & Pegadinhas:</strong>
              <ul class="list-disc pl-4 space-y-1">
                <li><strong>ANPD:</strong> Autarquia de natureza especial (Agência Reguladora) vinculada ao <strong>Ministério da Justiça e Segurança Pública (MJSP)</strong>.</li>
                <li><strong>Encarregado (DPO):</strong> Indicado pelo controlador E pelo operador, mas <strong>NÃO é agente de tratamento</strong>.</li>
                <li><strong>Anonimizado vs. Pseudonimizado:</strong> Anonimizado está FORA da LGPD; Pseudonimizado (chave separada) está DENTRO da LGPD.</li>
                <li><strong>Dados Sensíveis (Art. 11):</strong> Proibido usar <em>Legítimo Interesse</em> e <em>Proteção do Crédito</em>!</li>
              </ul>
            </div>
          </div>
        `
      },
      {
        id: 'MOD_4',
        tier: 'TIER A • OURO',
        title: '4. Records in Contexts (RiC-CM / RiC-O) vs. NOBRADE',
        points: 'Potencial: 30 Pontos (Favorito para Questão de 20 Linhas na P3)',
        content: `
          <div class="space-y-3 text-xs text-slate-300 leading-relaxed">
            <div class="p-3 bg-slate-950 rounded-xl border border-amber-500/30">
              <strong class="text-amber-400 block mb-1">O Confronto Direto NOBRADE vs. RiC (ICA):</strong>
              <ul class="list-disc pl-4 space-y-1">
                <li><strong>Topologia:</strong> NOBRADE usa árvore hierárquica monocêntrica (1:N); o <strong>RiC</strong> adota um <strong>grafo policêntrico multidimensional (N:N)</strong>.</li>
                <li><strong>Record vs. Instantiation:</strong> O RiC separa o documento intelectual (<em>Record</em>) de suas manifestações físicas ou digitais (<em>Instantiation</em>).</li>
                <li><strong>Agente Mechanism:</strong> O RiC inclui softwares, algoritmos e robôs como subentidade de Agente (<em>Mechanism</em>).</li>
                <li><strong>RiC-O (Ontologia OWL/RDF):</strong> Usa triplas semânticas (<code>Sujeito → Predicado → Objeto</code>) para conectar acervos na Web de Dados Conectados (Linked Open Data).</li>
              </ul>
            </div>
          </div>
        `
      },
      {
        id: 'MOD_5',
        tier: 'TIER A • OURO',
        title: '5. IA Generativa (RAG, Alucinação, OCR/HTR) & Governança DAMA',
        points: 'Potencial: 41 Pontos Combinados (P1 + P2 + P3)',
        content: `
          <div class="space-y-3 text-xs text-slate-300 leading-relaxed">
            <div class="p-3 bg-slate-950 rounded-xl border border-amber-500/30">
              <strong class="text-amber-400 block mb-1">Arquitetura RAG (Retrieval-Augmented Generation):</strong>
              <p>Conecta o LLM ao repositório arquivístico confiável da Câmara (RDC-Arq/AtoM) por meio de embeddings vetoriais. Antes de gerar a resposta, o sistema recupera os documentos autênticos e exige citação da fonte, mitigando <strong>alucinações</strong> sem precisar retreinar (fine-tuning) o modelo a cada nova lei.</p>
            </div>
            <div class="p-3 bg-slate-950 rounded-xl border border-slate-800">
              <strong class="text-cyan-400 block mb-1">Conceitos-Chave de Prova:</strong>
              <ul class="list-disc pl-4 space-y-1">
                <li><strong>OCR vs. HTR:</strong> OCR para impressos tipográficos; HTR (Handwritten Text Recognition) para manuscritos históricos cursivos.</li>
                <li><strong>Precisão vs. Revocação:</strong> Precisão evita o <em>ruído</em> (lixo nos resultados); Revocação evita o <em>silêncio</em> (perder documentos relevantes).</li>
                <li><strong>Data Owner vs. Data Steward:</strong> Owner decide politicamente; Steward (Arquivista) faz a curadoria de metadados e qualidade.</li>
              </ul>
            </div>
          </div>
        `
      },
      {
        id: 'MOD_6',
        tier: 'TIER B • PRATA',
        title: '6. Cheat Sheet: CF/88 Legislativo, Licitações (14.133), SQL & Regex',
        points: 'Potencial: 35 Pontos Rápidos em P1 e P2',
        content: `
          <div class="space-y-3 text-xs text-slate-300 leading-relaxed">
            <div class="p-3 bg-slate-950 rounded-xl border border-slate-700">
              <strong class="text-white block mb-1">CF/88 (Art. 49 vs. 51 vs. 52):</strong>
              <p><strong>Art. 49 (Exclusiva CN - Decreto Legislativo):</strong> sustar atos exorbitantes do Executivo, resolver sobre tratados, julgar contas do Presidente.<br>
              <strong>Art. 51 (Privativa Câmara):</strong> autorizar processo contra Presidente (2/3), proceder à tomada de contas se não apresentadas em 60 dias.<br>
              <strong>Art. 52 (Privativa Senado):</strong> processar e julgar Presidente nos crimes de responsabilidade, aprovar autoridades (sabatina).</p>
            </div>
            <div class="p-3 bg-slate-950 rounded-xl border border-slate-700">
              <strong class="text-emerald-400 block mb-1">SQL & Regex Visual:</strong>
              <p><strong>Ordem SQL:</strong> <code>SELECT ... FROM ... JOIN ... ON ... WHERE ... GROUP BY ... HAVING ... ORDER BY</code>.<br>
              <strong>Regex:</strong> <code>\\d</code> (dígito), <code>\\w</code> (alfanumérico), <code>+</code> (1 ou mais), <code>*</code> (0 ou mais), <code>?</code> (0 ou 1 / opcional), <code>{n,m}</code> (repetição exata).</p>
            </div>
          </div>
        `
      }
    ];

    // =========================================================================
    // 4. TEMAS DISCURSIVOS P3 (PEÇA TÉCNICA 50L + QUESTÕES 20L)
    // =========================================================================
    const DISCURSIVE_THEMES = [
      {
        id: 'P3_1',
        title: 'Tema 1 (Peça Técnica 50L - 30 pts): Parecer sobre RDC-Arq, OAIS/PREMIS e Portaria CD 182/2020',
        prompt: `<strong>Situação Hipotética:</strong> Uma comissão permanente da Câmara dos Deputados mantém em pastas de rede compartilhadas (sem controle de SIGAD) centenas de arquivos de áudio, vídeo e textos nato-digitais de audiências públicas históricas, além de pretender eliminar listagens com dados pessoais sem observar a TTD. Redija um <strong>Parecer Técnico (46 a 50 linhas)</strong> fundamentado na Portaria DG nº 182/2020, no e-ARQ Brasil, no modelo OAIS/PREMIS e na LGPD/LAI.<br>
        <strong>Quesitos Obrigatórios:</strong> 1) Prerrogativa da Coarq (Portaria 182/2020) e distinção entre SIGAD, GED e RDC-Arq [10,00 pts]; 2) Fluxo SIP → AIP → DIP (Archivematica/AtoM) e entidades PREMIS para garantir autenticidade [10,00 pts]; 3) Tratamento de dados pessoais em acervos permanentes segundo o art. 16 da LGPD e prazos da LAI [10,00 pts].`,
        model: `<strong>ESQUELETO PADRÃO 30/30 (ABERTURA ESPELHADA):</strong><br>
        • <strong>§1 (Quesito 1 - Linhas 1 a 16):</strong> "No que tange às prerrogativas da Coordenação de Arquivo (Coarq) e à arquitetura de sistemas documentais, cumpre destacar que a Portaria DG nº 182/2020 autoriza a requisição compulsória de acervos de valor permanente retidos nas unidades administrativas..." (Diferenciar GED de SIGAD e apontar a necessidade de recolhimento a um RDC-Arq).<br>
        • <strong>§2 (Quesito 2 - Linhas 17 a 33):</strong> "Quanto ao fluxo de preservação digital sob o modelo OAIS (ISO 14721) e ao padrão PREMIS, a admissão dos objetos exige a transformação do pacote SIP em AIP por meio do Archivematica..." (Citar as 4 entidades PREMIS: Object, Event, Agent e Rights, fixidez por hash e difusão do DIP via AtoM).<br>
        • <strong>§3 (Quesito 3 - Linhas 34 a 49):</strong> "Por fim, acerca da interseção entre a Tabela de Temporalidade e Destinação (TTD), a LAI e a LGPD, o art. 16, incisos I e II, da Lei nº 13.709/2018 autoriza expressamente a conservação de dados pessoais após o término do tratamento para cumprimento de obrigação legal e pesquisa histórica..." (Citar o prazo de até 100 anos do art. 31 da LAI e o Edital de Ciência de 30 a 45 dias da Res. CONARQ 40/2014).`
      },
      {
        id: 'P3_2',
        title: 'Tema 2 (Questão Técnica 20L - 15 pts): Transição da NOBRADE para o Records in Contexts (RiC-CM / RiC-O)',
        prompt: `<strong>Comando:</strong> Discorra, em até 20 linhas, sobre a mudança de paradigma entre a descrição multinível tradicional (ISAD(G)/NOBRADE) e o padrão <strong>Records in Contexts (RiC)</strong> do CIA, abordando: a) transição topológica (árvore vs. grafo); b) distinção entre <em>Record</em> e <em>Instantiation</em>; c) o papel da subentidade <em>Mechanism</em> e das triplas RDF no RiC-O.`,
        model: `<strong>ESQUELETO PADRÃO 15/15 (18 A 20 LINHAS):</strong><br>
        • <strong>§1 (Linhas 1 a 7):</strong> "A transição da NOBRADE para a norma Records in Contexts (RiC) substitui a descrição hierárquica monocêntrica em árvore (1:N) por um modelo de grafo policêntrico e multidimensional (N:N)..."<br>
        • <strong>§2 (Linhas 8 a 14):</strong> "Ademais, no que se refere à modelagem de entidades no RiC-CM, estabelece-se a separação rigorosa entre o documento intelectual (Record) e sua materialização física ou digital (Instantiation)..."<br>
        • <strong>§3 (Linhas 15 a 20):</strong> "Por fim, quanto aos agentes e à Web Semântica, o RiC inova ao incluir a subentidade Mechanism (softwares e algoritmos) e ao estruturar a ontologia RiC-O em triplas RDF (Sujeito → Predicado → Objeto)."`
      },
      {
        id: 'P3_3',
        title: 'Tema 3 (Questão Técnica 20L - 15 pts): Arquitetura RAG, LLMs e Governança de Dados no Acervo Legislativo',
        prompt: `<strong>Comando:</strong> Explique como a arquitetura <strong>RAG (Retrieval-Augmented Generation)</strong> viabiliza o uso seguro de Grandes Modelos de Linguagem (LLMs) na pesquisa em acervos legislativos da Câmara, diferenciando as métricas de Precisão e Revocação e destacando o papel do arquivista como <em>Data Steward</em> e <em>Human-in-the-Loop</em>.`,
        model: `<strong>ESQUELETO PADRÃO 15/15 (18 A 20 LINHAS):</strong><br>
        • <strong>§1 (Linhas 1 a 8):</strong> "A arquitetura RAG (Retrieval-Augmented Generation) viabiliza o uso seguro de LLMs no acervo legislativo ao acoplar um mecanismo de recuperação vetorial sobre o repositório confiável da Câmara antes da geração textual, mitigando alucinações..."<br>
        • <strong>§2 (Linhas 9 a 14):</strong> "No tocante às métricas de avaliação da recuperação, a Precisão atua na contenção do ruído (documentos irrelevantes), ao passo que a Revocação (Recall) combate o silêncio documental..."<br>
        • <strong>§3 (Linhas 15 a 20):</strong> "Nesse ecossistema de governança (DAMA-DMBOK), o arquivista atua como Data Steward e Human-in-the-Loop, assegurando a linhagem, a proveniência e a curadoria ética dos metadados que alimentam a IA."`
      }
    ];

    // =========================================================================
    // 5. GAPS INICIAIS DE UMA LINHA (PRÉ-CARREGADOS DA ANÁLISE)
    // =========================================================================
    const INITIAL_GAPS = [
      { id: 'G1', subject: 'S_LAI_LGPD', text: '[LGPD 2026 - Lei 15.352] Encarregado (DPO) é indicado pelo controlador E operador, mas NÃO é agente de tratamento; ANPD agora é Agência Reguladora vinculada ao MJSP.' },
      { id: 'G2', subject: 'S_PRESERV', text: '[OAIS / PREMIS] O pacote SIP não traz metadados PREMIS completos; o PREMIS (Object, Event, Agent, Rights) é gerado na ingestão (Archivematica) para compor o AIP.' },
      { id: 'G3', subject: 'S_GESTAO_CD', text: '[Ato da Mesa 62/1985] Transferência mantém o vínculo de propriedade com o setor produtor; Recolhimento extingue o vínculo e passa ao domínio público.' },
      { id: 'G4', subject: 'S_GESTAO_CD', text: '[Portaria CD 182/2020] "Arquivo Impresso" é a versão impressa de um documento digital (e não nato-físico digitalizado); Coarq tem poder de requisição compulsória.' },
      { id: 'G5', subject: 'S_LAI_LGPD', text: '[LGPD Art. 16 x TTD] A LGPD autoriza conservar dados pessoais após o fim do tratamento para cumprir obrigação legal (TTD) e pesquisa histórica.' },
      { id: 'G6', subject: 'A_RIC_CI', text: '[RiC vs NOBRADE] Transição da árvore monocêntrica (1:N) para o grafo policêntrico (N:N); Record (intelectual) separa-se de Instantiation (físico/digital); Mechanism inclui softwares como agentes.' },
      { id: 'G7', subject: 'A_IA_RAG', text: '[RAG & Métricas] RAG evita alucinação ancorando o LLM no repositório sem fine-tuning; Precisão evita RUÍDO e Revocação evita SILÊNCIO.' }
    ];

    // =========================================================================
    // 6. ESTADO GLOBAL E PERSISTÊNCIA (LOCALSTORAGE)
    // =========================================================================
    const STORAGE_KEY = 'CAMARA_240_ARQUIVOLOGIA_STATE_V1';

    let appState = {
      activeDate: '2026-10-14',
      dailyTarget: 100,
      xp: 150,
      dailyLogs: {
        // 'YYYY-MM-DD': [ { id, subject, c, e, b, time } ]
      },
      customQuestions: [],
      simProgress: {
        // questionId: 'C' | 'E' | 'B'
      },
      currentSimIndex: 0,
      gaps: [],
      completedCodice: [],
      discursiveDrafts: {}
    };

    function loadState() {
      try {
        const saved = localStorage.getItem(STORAGE_KEY);
        if (saved) {
          const parsed = JSON.parse(saved);
          appState = { ...appState, ...parsed };
        } else {
          appState.gaps = [...INITIAL_GAPS];
          saveState();
        }
      } catch (err) {
        console.error('Erro ao carregar localStorage:', err);
        appState.gaps = [...INITIAL_GAPS];
      }
      if (!appState.gaps || appState.gaps.length === 0) {
        appState.gaps = [...INITIAL_GAPS];
      }
    }

    function saveState() {
      try {
        localStorage.setItem(STORAGE_KEY, JSON.stringify(appState));
      } catch (err) {
        console.error('Erro ao gravar no localStorage:', err);
      }
      updateAllUI();
    }

    function showToast(msg) {
      const box = document.getElementById('toast-box');
      document.getElementById('toast-msg').textContent = msg;
      box.classList.remove('hidden');
      setTimeout(() => box.classList.add('hidden'), 3200);
    }

    // =========================================================================
    // 7. FUNÇÕES DE CÁLCULO E ATUALIZAÇÃO DE INTERFACE
    // =========================================================================
    function getAllQuestions() {
      return [...INITIAL_QUESTIONS, ...(appState.customQuestions || [])];
    }

    function getDayLogs(dateStr) {
      return appState.dailyLogs[dateStr] || [];
    }

    function getDayTotals(dateStr) {
      const logs = getDayLogs(dateStr);
      let c = 0, e = 0, b = 0;
      const bySubject = {};
      const byTier = { S: 0, A: 0, B: 0 };

      SUBJECTS.forEach(s => bySubject[s.id] = { c: 0, e: 0, b: 0, total: 0 });

      logs.forEach(l => {
        c += Number(l.c || 0);
        e += Number(l.e || 0);
        b += Number(l.b || 0);
        const tot = Number(l.c || 0) + Number(l.e || 0) + Number(l.b || 0);
        if (bySubject[l.subject]) {
          bySubject[l.subject].c += Number(l.c || 0);
          bySubject[l.subject].e += Number(l.e || 0);
          bySubject[l.subject].b += Number(l.b || 0);
          bySubject[l.subject].total += tot;
        }
        const subjObj = SUBJECTS.find(s => s.id === l.subject);
        if (subjObj && byTier[subjObj.tier] !== undefined) {
          byTier[subjObj.tier] += tot;
        }
      });

      const total = c + e + b;
      const net = c - e;
      return { c, e, b, total, net, bySubject, byTier };
    }

    function getGlobalTotals() {
      let c = 0, e = 0, b = 0, streak = 0;
      const dates = Object.keys(appState.dailyLogs).sort();
      dates.forEach(d => {
        const dt = getDayTotals(d);
        c += dt.c;
        e += dt.e;
        b += dt.b;
        if (dt.total >= 100) streak++;
      });
      const total = c + e + b;
      const net = c - e;
      return { c, e, b, total, net, streak };
    }

    function getRankInfo(xp) {
      const ranks = [
        { min: 0, title: 'Nível 1 • Estagiário de Protocolo' },
        { min: 500, title: 'Nível 2 • Técnico de Arquivo Corrente' },
        { min: 1500, title: 'Nível 3 • Especialista CONARQ / e-ARQ' },
        { min: 3500, title: 'Nível 4 • Engenheiro OAIS / PREMIS' },
        { min: 7000, title: 'Nível 5 • Arquiteto de Grafos RiC-O & RAG' },
        { min: 12000, title: 'Nível 6 • Guardião da Coarq (Câmara)' },
        { min: 20000, title: 'Nível 7 • Analista Legislativo Aprovado (240 Pts)' }
      ];
      let current = ranks[0];
      let nextMin = 500;
      for (let i = 0; i < ranks.length; i++) {
        if (xp >= ranks[i].min) {
          current = ranks[i];
          nextMin = ranks[i + 1] ? ranks[i + 1].min : ranks[i].min + 10000;
        }
      }
      const pct = Math.min(100, Math.round(((xp - current.min) / (nextMin - current.min)) * 100));
      return { title: current.title, pct };
    }

    function updateAllUI() {
      const todayStats = getDayTotals(appState.activeDate);
      const globalStats = getGlobalTotals();
      const target = Number(appState.dailyTarget || 100);

      // HUD Top Bar
      const pct = Math.min(100, Math.round((todayStats.total / target) * 100));
      document.getElementById('hud-daily-ring').setAttribute('stroke-dasharray', `${pct}, 100`);
      document.getElementById('hud-daily-pct').textContent = `${pct}%`;
      document.getElementById('hud-today-q').textContent = todayStats.total;
      document.getElementById('hud-target-q').textContent = target;
      document.getElementById('hud-net-score').textContent = (globalStats.net >= 0 ? '+' : '') + globalStats.net;
      document.getElementById('hud-streak').textContent = globalStats.streak;

      // Countdown to 2027-01-17
      const examDate = new Date('2027-01-17T08:00:00');
      const curDate = new Date(appState.activeDate + 'T08:00:00');
      const diffDays = Math.max(0, Math.ceil((examDate - curDate) / (1000 * 60 * 60 * 24)));
      document.getElementById('hud-countdown').textContent = diffDays;

      // Phase badge
      const startDate = new Date('2026-10-13T00:00:00');
      const dayNumber = Math.max(1, Math.min(96, Math.floor((curDate - startDate) / (1000 * 60 * 60 * 24)) + 1));
      const phaseBadge = document.getElementById('hud-phase-badge');
      if (dayNumber <= 48) {
        phaseBadge.textContent = `Dia ${dayNumber}/96 • Bloco 1: Volume`;
      } else if (dayNumber <= 79) {
        phaseBadge.textContent = `Dia ${dayNumber}/96 • Bloco 2: Aceleração`;
      } else {
        phaseBadge.textContent = `Dia ${dayNumber}/96 • Bloco 3: Reta Final`;
      }

      // Rank & XP
      const rk = getRankInfo(appState.xp);
      document.getElementById('hud-rank-title').textContent = rk.title;
      document.getElementById('hud-xp-bar').style.width = `${rk.pct}%`;
      document.getElementById('hud-xp-val').textContent = appState.xp;

      // Nav counts
      document.getElementById('nav-q-count').textContent = getAllQuestions().length;
      document.getElementById('nav-gaps-count').textContent = appState.gaps.length;

      // Dashboard Date & KPIs
      document.getElementById('active-date-input').value = appState.activeDate;
      document.getElementById('daily-goal-select').value = String(appState.dailyTarget);
      document.getElementById('dashboard-current-date-label').textContent = `Data Operacional Selecionada: ${appState.activeDate.split('-').reverse().join('/')} (Dia ${dayNumber} de 96)`;

      document.getElementById('day-kpi-total').textContent = todayStats.total;
      document.getElementById('day-kpi-target').textContent = target;
      const rem = Math.max(0, target - todayStats.total);
      document.getElementById('day-kpi-status').textContent = rem === 0 ? '🔥 META DIÁRIA BATIDA!' : `Faltam ${rem} questões hoje`;
      document.getElementById('day-kpi-correct').textContent = todayStats.c;
      document.getElementById('day-kpi-wrong').textContent = todayStats.e;
      document.getElementById('day-kpi-blank').textContent = todayStats.b;

      const markedToday = todayStats.c + todayStats.e;
      const accToday = markedToday > 0 ? Math.round((todayStats.c / markedToday) * 100) : 0;
      document.getElementById('day-kpi-acc').textContent = `${accToday}%`;

      document.getElementById('day-kpi-net').textContent = (todayStats.net >= 0 ? '+' : '') + todayStats.net;
      const netPctToday = todayStats.total > 0 ? Math.round((todayStats.net / todayStats.total) * 100) : 0;
      document.getElementById('day-kpi-net-pct').textContent = `${netPctToday}%`;

      // Global Omission Calibrator
      document.getElementById('global-stat-total').textContent = `${globalStats.total} itens`;
      const globalMarked = globalStats.c + globalStats.e;
      const globalMarkedAcc = globalMarked > 0 ? Math.round((globalStats.c / globalMarked) * 100) : 0;
      const globalBlankRate = globalStats.total > 0 ? Math.round((globalStats.b / globalStats.total) * 100) : 0;
      const projected180 = globalStats.total > 0 ? Math.round((globalStats.net / globalStats.total) * 180) : 0;

      document.getElementById('global-stat-marked-acc').textContent = `${globalMarkedAcc}%`;
      document.getElementById('global-stat-blank-rate').textContent = `${globalBlankRate}%`;
      document.getElementById('global-stat-projection').textContent = `${projected180 >= 0 ? '+' : ''}${projected180} pts líquidos`;

      const omBadge = document.getElementById('omission-badge');
      if (globalStats.total === 0) {
        omBadge.textContent = 'Sem dados ainda';
        omBadge.className = 'text-[10px] font-mono px-2 py-0.5 rounded bg-slate-800 text-slate-300';
      } else if (projected180 >= 120) {
        omBadge.textContent = '✅ TOPO DA CLASSIFICAÇÃO (120+)';
        omBadge.className = 'text-[10px] font-mono px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-300 border border-emerald-500/30';
      } else if (globalBlankRate < 8) {
        omBadge.textContent = '⚠️ AGRESSIVO DEMAIS (Treine deixar em branco!)';
        omBadge.className = 'text-[10px] font-mono px-2 py-0.5 rounded bg-rose-500/20 text-rose-300 border border-rose-500/30';
      } else {
        omBadge.textContent = '⚡ EM CALIBRAGEM TÁTICA';
        omBadge.className = 'text-[10px] font-mono px-2 py-0.5 rounded bg-amber-500/20 text-amber-300 border border-amber-500/30';
      }

      renderTierChecklists(todayStats, target);
      renderTodayLogsList();
      renderGapsList();
      render96DaysCalendar();
      lucide.createIcons();
    }

    // =========================================================================
    // 8. RENDERIZAÇÃO DAS METAS DIÁRIAS POR TIER (S, A, B)
    // =========================================================================
    function renderTierChecklists(todayStats, target) {
      const scale = target / 100;
      const sTarget = Math.round(50 * scale);
      const aTarget = Math.round(30 * scale);
      const bTarget = Math.round(20 * scale);

      document.getElementById('tier-s-progress').textContent = `${todayStats.byTier.S} / ${sTarget}`;
      document.getElementById('tier-a-progress').textContent = `${todayStats.byTier.A} / ${aTarget}`;
      document.getElementById('tier-b-progress').textContent = `${todayStats.byTier.B} / ${bTarget}`;

      const buildRow = (subj) => {
        const quota = Math.round(subj.dailyQuota * scale);
        const st = todayStats.bySubject[subj.id] || { c: 0, e: 0, b: 0, total: 0 };
        const pct = Math.min(100, Math.round((st.total / quota) * 100));
        const net = st.c - st.e;
        const done = st.total >= quota;

        return `
          <div class="bg-slate-950/90 border ${done ? 'border-emerald-500/50' : 'border-slate-800'} rounded-xl p-3.5 transition">
            <div class="flex flex-wrap items-center justify-between gap-2 mb-1.5">
              <div class="flex items-center gap-2">
                <span class="w-5 h-5 rounded-full flex items-center justify-center text-xs ${done ? 'bg-emerald-500 text-slate-950 font-bold' : 'bg-slate-800 text-slate-400'}">
                  ${done ? '✓' : '•'}
                </span>
                <span class="font-bold text-xs sm:text-sm text-white">${subj.name}</span>
              </div>
              <div class="flex items-center gap-2">
                <span class="text-[11px] font-mono px-2 py-0.5 rounded bg-slate-900 text-slate-300 border border-slate-800">${subj.pointsPotential}</span>
                <span class="text-xs font-mono font-bold ${done ? 'text-emerald-400' : 'text-cyan-400'}">${st.total} / ${quota} Q</span>
              </div>
            </div>
            <p class="text-[11px] text-slate-400 mb-2.5">${subj.desc}</p>
            <div class="w-full h-1.5 bg-slate-800 rounded-full overflow-hidden mb-2.5">
              <div class="h-full ${done ? 'bg-emerald-400' : 'bg-cyan-400'} transition-all duration-300" style="width: ${pct}%"></div>
            </div>
            <div class="flex flex-wrap items-center justify-between gap-2 text-[11px] font-mono">
              <div class="text-slate-400">
                Hoje: <span class="text-emerald-400">${st.c}C</span> • <span class="text-rose-400">${st.e}E</span> • <span class="text-amber-400">${st.b}B</span> | Líquido: <strong class="text-white">${net >= 0 ? '+' : ''}${net}</strong>
              </div>
              <div class="flex items-center gap-1.5">
                <button onclick="quickAddBattery('${subj.id}', ${quota})" class="px-2.5 py-1 rounded-lg bg-emerald-500/15 hover:bg-emerald-500/25 text-emerald-300 border border-emerald-500/30 font-sans font-semibold transition">
                  + Cravar Meta (${quota}Q)
                </button>
                <button onclick="openSimWithSubject('${subj.id}')" class="px-2.5 py-1 rounded-lg bg-cyan-500/15 hover:bg-cyan-500/25 text-cyan-300 border border-cyan-500/30 font-sans font-semibold transition">
                  Treinar no Simulador
                </button>
              </div>
            </div>
          </div>
        `;
      };

      document.getElementById('tier-s-list').innerHTML = SUBJECTS.filter(s => s.tier === 'S').map(buildRow).join('');
      document.getElementById('tier-a-list').innerHTML = SUBJECTS.filter(s => s.tier === 'A').map(buildRow).join('');
      document.getElementById('tier-b-list').innerHTML = SUBJECTS.filter(s => s.tier === 'B').map(buildRow).join('');
    }

    function quickAddBattery(subjectId, quota) {
      // Simula uma bateria calibrada padrão (ex: 80% certas, 10% erradas, 10% em branco)
      const b = Math.max(1, Math.round(quota * 0.12));
      const e = Math.max(1, Math.round(quota * 0.10));
      const c = Math.max(1, quota - b - e);

      addLogEntry(subjectId, c, e, b);
      showToast(`Meta de ${quota} questões gravada (${c}C, ${e}E, ${b}B = +${c - e} pts líquidos)!`);
    }

    function addLogEntry(subject, c, e, b, customNote = '') {
      if (!appState.dailyLogs[appState.activeDate]) {
        appState.dailyLogs[appState.activeDate] = [];
      }
      const totalQ = Number(c) + Number(e) + Number(b);
      appState.dailyLogs[appState.activeDate].unshift({
        id: 'L_' + Date.now() + '_' + Math.random().toString(36).slice(2, 6),
        subject,
        c: Number(c),
        e: Number(e),
        b: Number(b),
        time: new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' })
      });

      appState.xp += totalQ * 10;

      if (customNote && customNote.trim().length > 3) {
        appState.gaps.unshift({
          id: 'G_' + Date.now(),
          subject,
          text: customNote.trim()
        });
        appState.xp += 15;
      }

      saveState();
    }

    function logManualBattery(ev) {
      ev.preventDefault();
      const subject = document.getElementById('log-subject').value;
      const c = Number(document.getElementById('log-correct').value || 0);
      const e = Number(document.getElementById('log-wrong').value || 0);
      const b = Number(document.getElementById('log-blank').value || 0);
      const note = document.getElementById('log-gap-note').value;

      if (c + e + b <= 0) return;

      addLogEntry(subject, c, e, b, note);
      document.getElementById('log-gap-note').value = '';
      showToast(`Bateria registrada com sucesso (+${(c + e + b) * 10} XP)!`);
    }

    function renderTodayLogsList() {
      const container = document.getElementById('today-logs-container');
      const logs = getDayLogs(appState.activeDate);
      if (logs.length === 0) {
        container.innerHTML = `<div class="text-xs text-slate-500 text-center py-4">Nenhuma bateria gravada nesta data ainda.</div>`;
        return;
      }
      container.innerHTML = logs.map(l => {
        const subj = SUBJECTS.find(s => s.id === l.subject);
        const net = l.c - l.e;
        return `
          <div class="bg-slate-950 border border-slate-800 rounded-xl px-3 py-2 flex items-center justify-between text-xs">
            <div>
              <div class="font-bold text-slate-200">${subj ? subj.short : l.subject} <span class="text-[10px] text-slate-500 font-mono">(${l.time})</span></div>
              <div class="font-mono text-[11px] text-slate-400">
                <span class="text-emerald-400">${l.c}C</span> • <span class="text-rose-400">${l.e}E</span> • <span class="text-amber-400">${l.b}B</span>
              </div>
            </div>
            <div class="flex items-center gap-2">
              <span class="font-mono font-bold ${net >= 0 ? 'text-cyan-400' : 'text-rose-400'}">${net >= 0 ? '+' : ''}${net} pts</span>
              <button onclick="deleteLogItem('${l.id}')" class="text-slate-500 hover:text-rose-400">×</button>
            </div>
          </div>
        `;
      }).join('');
    }

    function deleteLogItem(id) {
      const logs = getDayLogs(appState.activeDate);
      appState.dailyLogs[appState.activeDate] = logs.filter(l => l.id !== id);
      saveState();
    }

    function clearTodayLogs() {
      appState.dailyLogs[appState.activeDate] = [];
      saveState();
      showToast('Registros do dia selecionado foram zerados.');
    }

    function changeActiveDate(val) {
      if (!val) return;
      appState.activeDate = val;
      saveState();
    }

    function updateDailyGoalTarget(val) {
      appState.dailyTarget = Number(val);
      saveState();
      showToast(`Meta diária ajustada para ${val} questões/dia!`);
    }

    // =========================================================================
    // 9. SIMULADOR CEBRASPE (BANCO INTERATIVO)
    // =========================================================================
    function getFilteredQuestions() {
      const tierFilter = document.getElementById('sim-filter-tier').value;
      const subjFilter = document.getElementById('sim-filter-subject').value;
      return getAllQuestions().filter(q => {
        if (tierFilter !== 'ALL' && q.tier !== tierFilter) return false;
        if (subjFilter !== 'ALL' && q.subject !== subjFilter) return false;
        return true;
      });
    }

    function openSimWithSubject(subjId) {
      document.getElementById('sim-filter-tier').value = 'ALL';
      document.getElementById('sim-filter-subject').value = subjId;
      appState.currentSimIndex = 0;
      switchTab('simulador');
      renderSimulatorQuestion();
    }

    function renderSimulatorQuestion() {
      const list = getFilteredQuestions();
      const card = document.getElementById('sim-card');
      const grid = document.getElementById('sim-question-grid');

      if (list.length === 0) {
        card.innerHTML = `<div class="text-center py-8 text-slate-400 text-sm">Nenhuma questão encontrada para este filtro.</div>`;
        grid.innerHTML = '';
        return;
      }

      if (appState.currentSimIndex >= list.length) {
        appState.currentSimIndex = 0;
      }

      const q = list[appState.currentSimIndex];
      const subj = SUBJECTS.find(s => s.id === q.subject);
      const userAns = appState.simProgress[q.id]; // 'C', 'E', 'B' or undefined

      let feedbackHtml = '';
      if (userAns) {
        const isCorrect = userAns === q.ans;
        const isBlank = userAns === 'B';
        const statusColor = isBlank
          ? 'border-amber-500/40 bg-amber-950/30 text-amber-200'
          : isCorrect
          ? 'border-emerald-500/40 bg-emerald-950/30 text-emerald-200'
          : 'border-rose-500/40 bg-rose-950/30 text-rose-200';

        const statusTitle = isBlank
          ? '🛡️ OMISSÃO TÁTICA (0 PONTO — SALDO PROTEGIDO)'
          : isCorrect
          ? '✅ ACERTO CIRÚRGICO (+1 PONTO LÍQUIDO)'
          : '❌ ERRO PENALIZADO (-1 PONTO LÍQUIDO)';

        feedbackHtml = `
          <div class="p-4 rounded-xl border ${statusColor} space-y-2 text-xs">
            <div class="flex items-center justify-between font-mono font-bold">
              <span>${statusTitle}</span>
              <span>Gabarito Oficial: ${q.ans === 'C' ? 'CERTO' : 'ERRADO'}</span>
            </div>
            <p class="text-slate-200 leading-relaxed">${q.exp}</p>
            <div class="pt-2 flex justify-end">
              <button onclick="sendQuestionExpToGaps('${q.id}')" class="px-3 py-1.5 rounded-lg bg-purple-500/20 hover:bg-purple-500/30 text-purple-300 border border-purple-500/40 font-semibold flex items-center gap-1.5">
                ⚡ Salvar esta regra no Caderno de Gaps (+15 XP)
              </button>
            </div>
          </div>
        `;
      }

      card.innerHTML = `
        <div class="flex flex-wrap items-center justify-between gap-2 pb-4 border-b border-slate-800">
          <div class="flex items-center gap-2">
            <span class="px-2.5 py-1 rounded-lg bg-cyan-500/20 text-cyan-300 font-mono font-bold text-xs border border-cyan-500/30">
              TIER ${q.tier}
            </span>
            <span class="text-xs font-bold text-slate-200">${subj ? subj.short : q.subject}</span>
          </div>
          <span class="text-xs font-mono text-slate-400">Item ${appState.currentSimIndex + 1} de ${list.length} (${q.id})</span>
        </div>

        <div class="py-2">
          <p class="text-sm sm:text-base text-white leading-relaxed font-medium">
            Julgue o item a seguir, a respeito de ${subj ? subj.name : 'conhecimentos legislativos'}:<br><br>
            <span class="text-cyan-100 font-normal">"${q.stmt}"</span>
          </p>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-3 gap-3">
          <button onclick="answerSimulatorQuestion('${q.id}', 'C')" ${userAns ? 'disabled' : ''} class="py-3 px-4 rounded-xl font-mono font-bold text-xs uppercase tracking-wider border transition flex items-center justify-center gap-2 ${userAns === 'C' ? 'bg-emerald-500 text-slate-950 border-emerald-400' : 'bg-slate-950 hover:bg-emerald-950/50 text-emerald-400 border-emerald-500/40'}">
            [ C ] CERTO
          </button>
          <button onclick="answerSimulatorQuestion('${q.id}', 'E')" ${userAns ? 'disabled' : ''} class="py-3 px-4 rounded-xl font-mono font-bold text-xs uppercase tracking-wider border transition flex items-center justify-center gap-2 ${userAns === 'E' ? 'bg-rose-500 text-white border-rose-400' : 'bg-slate-950 hover:bg-rose-950/50 text-rose-400 border-rose-500/40'}">
            [ E ] ERRADO
          </button>
          <button onclick="answerSimulatorQuestion('${q.id}', 'B')" ${userAns ? 'disabled' : ''} class="py-3 px-4 rounded-xl font-mono font-bold text-xs uppercase tracking-wider border transition flex items-center justify-center gap-2 ${userAns === 'B' ? 'bg-amber-500 text-slate-950 border-amber-400' : 'bg-slate-950 hover:bg-amber-950/50 text-amber-400 border-amber-500/40'}">
            [ B ] DEIXAR EM BRANCO
          </button>
        </div>

        ${feedbackHtml}

        <div class="flex items-center justify-between pt-3 border-t border-slate-800">
          <button onclick="moveSimQuestion(-1)" class="px-4 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-xs font-semibold text-slate-200">← Anterior</button>
          <button onclick="moveSimQuestion(1)" class="px-4 py-2 rounded-xl bg-cyan-500 hover:bg-cyan-400 text-xs font-bold text-slate-950">Próximo Item →</button>
        </div>
      `;

      // Update session stats
      let sc = 0, se = 0, sb = 0;
      list.forEach(item => {
        const ua = appState.simProgress[item.id];
        if (!ua) return;
        if (ua === 'B') sb++;
        else if (ua === item.ans) sc++;
        else se++;
      });

      document.getElementById('sim-stat-c').textContent = sc;
      document.getElementById('sim-stat-e').textContent = se;
      document.getElementById('sim-stat-b').textContent = sb;
      const snet = sc - se;
      document.getElementById('sim-stat-net').textContent = (snet >= 0 ? '+' : '') + snet;

      // Render grid buttons
      grid.innerHTML = list.map((item, idx) => {
        const ua = appState.simProgress[item.id];
        let btnClass = 'bg-slate-950 text-slate-400 border-slate-800';
        if (ua === 'B') btnClass = 'bg-amber-500/20 text-amber-300 border-amber-500/40';
        else if (ua && ua === item.ans) btnClass = 'bg-emerald-500/20 text-emerald-300 border-emerald-500/40';
        else if (ua && ua !== item.ans) btnClass = 'bg-rose-500/20 text-rose-300 border-rose-500/40';

        if (idx === appState.currentSimIndex) {
          btnClass += ' ring-2 ring-cyan-400';
        }
        return `<button onclick="jumpSimQuestion(${idx})" class="h-8 rounded-lg border font-mono text-xs font-bold ${btnClass}">${idx + 1}</button>`;
      }).join('');
    }

    function answerSimulatorQuestion(qId, choice) {
      const q = getAllQuestions().find(item => item.id === qId);
      if (!q) return;

      appState.simProgress[qId] = choice;

      // Also record in today's daily log automatically!
      const c = choice !== 'B' && choice === q.ans ? 1 : 0;
      const e = choice !== 'B' && choice !== q.ans ? 1 : 0;
      const b = choice === 'B' ? 1 : 0;

      addLogEntry(q.subject, c, e, b);
      renderSimulatorQuestion();
    }

    function moveSimQuestion(delta) {
      const list = getFilteredQuestions();
      if (list.length === 0) return;
      appState.currentSimIndex = (appState.currentSimIndex + delta + list.length) % list.length;
      renderSimulatorQuestion();
    }

    function jumpSimQuestion(idx) {
      appState.currentSimIndex = idx;
      renderSimulatorQuestion();
    }

    function resetSimulatorProgress() {
      appState.simProgress = {};
      saveState();
      renderSimulatorQuestion();
      showToast('Marcações do simulador reiniciadas.');
    }

    function sendQuestionExpToGaps(qId) {
      const q = getAllQuestions().find(item => item.id === qId);
      if (!q) return;
      appState.gaps.unshift({
        id: 'G_' + Date.now(),
        subject: q.subject,
        text: q.exp
      });
      appState.xp += 15;
      saveState();
      showToast('Regra adicionada ao Caderno de Gaps de Uma Linha (+15 XP)!');
    }

    function openNewQuestionModal() {
      document.getElementById('modal-new-q').classList.remove('hidden');
    }
    function closeNewQuestionModal() {
      document.getElementById('modal-new-q').classList.add('hidden');
    }
    function saveCustomQuestion(ev) {
      ev.preventDefault();
      const subjId = document.getElementById('new-q-subject').value;
      const subj = SUBJECTS.find(s => s.id === subjId);
      const stmt = document.getElementById('new-q-stmt').value.trim();
      const ans = document.getElementById('new-q-ans').value;
      const exp = document.getElementById('new-q-exp').value.trim();

      const newQ = {
        id: 'QC_' + (appState.customQuestions.length + 1),
        subject: subjId,
        tier: subj ? subj.tier : 'S',
        stmt,
        ans,
        exp
      };
      appState.customQuestions.push(newQ);
      appState.xp += 25;
      saveState();
      closeNewQuestionModal();
      renderSimulatorQuestion();
      showToast('Questão inédita adicionada ao banco (+25 XP)!');
    }

    // =========================================================================
    // 10. CÓDICE DE INTELIGÊNCIA (GUIAS DE 15 MINUTOS)
    // =========================================================================
    function renderCodiceModules() {
      const container = document.getElementById('codice-modules-container');
      container.innerHTML = CODICE_MODULES.map(mod => {
        const isDone = (appState.completedCodice || []).includes(mod.id);
        return `
          <div class="bg-slate-900 border ${isDone ? 'border-emerald-500/40' : 'border-slate-800'} rounded-2xl p-5 flex flex-col justify-between space-y-4">
            <div class="space-y-3">
              <div class="flex items-center justify-between">
                <span class="px-2 py-0.5 rounded text-[10px] font-mono font-bold bg-cyan-500/15 text-cyan-300 border border-cyan-500/30">${mod.tier}</span>
                <span class="text-[11px] font-mono text-amber-400 font-semibold">${mod.points}</span>
              </div>
              <h3 class="font-bold text-white text-base">${mod.title}</h3>
              ${mod.content}
            </div>
            <div class="pt-3 border-t border-slate-800 flex items-center justify-between">
              <span class="text-[11px] font-mono ${isDone ? 'text-emerald-400' : 'text-slate-500'}">
                ${isDone ? '✓ Guia de 15m Estudado' : 'Pendente de leitura rápida'}
              </span>
              <button onclick="markCodiceStudied('${mod.id}')" class="px-3 py-1.5 rounded-xl text-xs font-bold transition ${isDone ? 'bg-slate-800 text-slate-300' : 'bg-emerald-500 hover:bg-emerald-400 text-slate-950'}">
                ${isDone ? 'Revisar Novamente (+15 XP)' : 'Concluir Guia 15m (+30 XP)'}
              </button>
            </div>
          </div>
        `;
      }).join('');
    }

    function markCodiceStudied(modId) {
      if (!appState.completedCodice) appState.completedCodice = [];
      if (!appState.completedCodice.includes(modId)) {
        appState.completedCodice.push(modId);
        appState.xp += 30;
      } else {
        appState.xp += 15;
      }
      saveState();
      renderCodiceModules();
      showToast('Leitura técnica de 15 minutos registrada no sistema!');
    }

    // =========================================================================
    // 11. CADERNO DE GAPS DE UMA LINHA
    // =========================================================================
    let isFlashcardMode = false;

    function toggleFlashcardMode() {
      isFlashcardMode = !isFlashcardMode;
      const btn = document.getElementById('btn-flashcard-mode');
      btn.innerHTML = isFlashcardMode
        ? `<i data-lucide="list" class="w-4 h-4"></i> Voltar para Lista Visível`
        : `<i data-lucide="sparkles" class="w-4 h-4"></i> Modo Quiz / Flashcard`;
      renderGapsList();
      lucide.createIcons();
    }

    function addOneLineGap(ev) {
      ev.preventDefault();
      const subject = document.getElementById('gap-subject-select').value;
      const text = document.getElementById('gap-text-input').value.trim();
      if (!text) return;

      appState.gaps.unshift({
        id: 'G_' + Date.now(),
        subject,
        text
      });
      appState.xp += 15;
      document.getElementById('gap-text-input').value = '';
      saveState();
      showToast('Gap de 1 Linha blindado com sucesso (+15 XP)!');
    }

    function renderGapsList() {
      const filter = document.getElementById('gap-filter-select').value;
      const container = document.getElementById('gaps-list-container');
      const list = (appState.gaps || []).filter(g => filter === 'ALL' || g.subject === filter);

      document.getElementById('gaps-total-badge').textContent = list.length;

      if (list.length === 0) {
        container.innerHTML = `<div class="text-center py-8 text-slate-500 text-xs">Nenhum Gap registrado para este filtro.</div>`;
        return;
      }

      container.innerHTML = list.map((g, idx) => {
        const subj = SUBJECTS.find(s => s.id === g.subject);
        return `
          <div class="bg-slate-900 border border-slate-800 hover:border-purple-500/40 rounded-xl p-4 flex items-center justify-between gap-4 transition">
            <div class="space-y-1 flex-1">
              <div class="flex items-center gap-2">
                <span class="px-2 py-0.5 rounded text-[10px] font-mono font-bold bg-purple-500/15 text-purple-300 border border-purple-500/30">
                  #${idx + 1} • ${subj ? subj.short : g.subject}
                </span>
              </div>
              <p onclick="this.classList.toggle('blur-sm')" class="text-xs sm:text-sm text-white font-medium leading-relaxed cursor-pointer transition ${isFlashcardMode ? 'blur-sm select-none' : ''}" title="Clique para revelar/ocultar">
                ${g.text}
              </p>
            </div>
            <button onclick="deleteGap('${g.id}')" class="text-slate-500 hover:text-rose-400 p-1" title="Remover Gap">
              <i data-lucide="trash-2" class="w-4 h-4"></i>
            </button>
          </div>
        `;
      }).join('');
    }

    function deleteGap(id) {
      appState.gaps = appState.gaps.filter(g => g.id !== id);
      saveState();
    }

    // =========================================================================
    // 12. ENGENHARIA DISCURSIVA (P3 - 60 PONTOS & DIVISOR TL)
    // =========================================================================
    function updateDiscursiveCalc() {
      const nc = parseFloat(document.getElementById('calc-nc').value);
      const ne = parseInt(document.getElementById('calc-ne').value, 10);
      const tl = parseInt(document.getElementById('calc-tl').value, 10);

      document.getElementById('calc-nc-val').textContent = `${nc.toFixed(2)} pts`;
      document.getElementById('calc-ne-val').textContent = `${ne} erros`;
      document.getElementById('calc-tl-val').textContent = `${tl} linhas`;

      const penalty = 6 * (ne / tl);
      const penalty25 = 6 * (ne / 25);
      const finalNpt = Math.max(0, nc - penalty);

      document.getElementById('calc-penalty').textContent = `-${penalty.toFixed(2)} pts`;
      document.getElementById('calc-penalty-25').textContent = `-${penalty25.toFixed(2)} pts`;
      document.getElementById('calc-npt-final').textContent = `${finalNpt.toFixed(2)} / 30.00`;
    }

    function loadDiscursiveTheme() {
      const sel = document.getElementById('discursive-theme-select').value;
      const theme = DISCURSIVE_THEMES.find(t => t.id === sel) || DISCURSIVE_THEMES[0];

      document.getElementById('discursive-prompt-box').innerHTML = theme.prompt;
      document.getElementById('discursive-model-answer').innerHTML = theme.model;
      document.getElementById('discursive-model-answer').classList.add('hidden');
      document.getElementById('discursive-editor').value = (appState.discursiveDrafts && appState.discursiveDrafts[theme.id]) || '';
      estimateDiscursiveLines();
    }

    function estimateDiscursiveLines() {
      const txt = document.getElementById('discursive-editor').value;
      const lines = txt.trim() ? Math.ceil(txt.length / 65) : 0;
      document.getElementById('discursive-line-estimator').textContent = `~${lines} linhas estimadas no padrão Cebraspe`;
    }

    function revealDiscursiveModel() {
      document.getElementById('discursive-model-answer').classList.toggle('hidden');
    }

    function saveDiscursiveTraining() {
      const sel = document.getElementById('discursive-theme-select').value;
      const txt = document.getElementById('discursive-editor').value;
      if (!appState.discursiveDrafts) appState.discursiveDrafts = {};
      appState.discursiveDrafts[sel] = txt;
      appState.xp += 50;
      saveState();
      showToast('Esqueleto / Redação P3 salva com sucesso (+50 XP)!');
    }

    // =========================================================================
    // 13. CALENDÁRIO TÁTICO DOS 96 DIAS (13/10/2026 A 17/01/2027)
    // =========================================================================
    function render96DaysCalendar() {
      const grid = document.getElementById('calendar-96-grid');
      const start = new Date('2026-10-13T12:00:00');
      let html = '';

      for (let i = 0; i < 96; i++) {
        const d = new Date(start);
        d.setDate(start.getDate() + i);
        const iso = d.toISOString().slice(0, 10);
        const label = iso.slice(8, 10) + '/' + iso.slice(5, 7);
        const stats = getDayTotals(iso);
        const target = Number(appState.dailyTarget || 100);

        let bg = 'bg-slate-950 border-slate-800 text-slate-400 hover:border-slate-600';
        if (stats.total >= target) {
          bg = 'bg-emerald-500/20 border-emerald-500/50 text-emerald-300 font-bold';
        } else if (stats.total > 0) {
          bg = 'bg-amber-500/20 border-amber-500/50 text-amber-300';
        }

        if (iso === appState.activeDate) {
          bg += ' ring-2 ring-cyan-400';
        }

        html += `
          <button onclick="selectDayFromCalendar('${iso}')" class="p-2 rounded-xl border text-center transition flex flex-col items-center justify-center ${bg}">
            <span class="text-[10px] font-mono opacity-75">D${i + 1} • ${label}</span>
            <span class="text-xs font-mono font-bold mt-0.5">${stats.total}Q</span>
          </button>
        `;
      }
      grid.innerHTML = html;
    }

    function selectDayFromCalendar(iso) {
      appState.activeDate = iso;
      saveState();
      switchTab('dashboard');
      showToast(`Carregado Dia Operacional: ${iso.split('-').reverse().join('/')}`);
    }

    // =========================================================================
    // 14. NAVEGAÇÃO ENTRE ABAS & BACKUP MODAL
    // =========================================================================
    function switchTab(tabName) {
      document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
      document.getElementById(`tab-${tabName}`).classList.remove('hidden');

      document.querySelectorAll('.tab-btn').forEach(btn => {
        btn.className = 'tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap text-slate-400 hover:text-white hover:bg-slate-800/60';
      });
      const activeBtn = document.getElementById(`tab-btn-${tabName}`);
      if (activeBtn) {
        activeBtn.className = 'tab-btn flex items-center gap-2 px-4 py-2.5 rounded-lg text-xs sm:text-sm font-semibold transition whitespace-nowrap bg-cyan-500/15 text-cyan-300 border border-cyan-500/30';
      }

      if (tabName === 'simulador') renderSimulatorQuestion();
      if (tabName === 'codice') renderCodiceModules();
      if (tabName === 'discursiva') updateDiscursiveCalc();
      lucide.createIcons();
    }

    function openBackupModal() {
      document.getElementById('backup-json-area').value = JSON.stringify(appState, null, 2);
      document.getElementById('modal-backup').classList.remove('hidden');
    }
    function closeBackupModal() {
      document.getElementById('modal-backup').classList.add('hidden');
    }
    function exportBackupFile() {
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(appState, null, 2));
      const dlAnchor = document.createElement('a');
      dlAnchor.setAttribute("href", dataStr);
      dlAnchor.setAttribute("download", `backup_camara_240_${appState.activeDate}.json`);
      document.body.appendChild(dlAnchor);
      dlAnchor.click();
      dlAnchor.remove();
    }
    function importBackupFromText() {
      try {
        const raw = document.getElementById('backup-json-area').value;
        const parsed = JSON.parse(raw);
        appState = { ...appState, ...parsed };
        saveState();
        closeBackupModal();
        showToast('Backup restaurado com sucesso!');
      } catch (e) {
        alert('JSON inválido. Verifique o conteúdo colado.');
      }
    }

    // =========================================================================
    // 15. INICIALIZAÇÃO DO SISTEMA
    // =========================================================================
    function initSelectDropdowns() {
      const subjOptions = SUBJECTS.map(s => `<option value="${s.id}">[TIER ${s.tier}] ${s.short} (Meta: ${s.dailyQuota}Q)</option>`).join('');
      document.getElementById('log-subject').innerHTML = subjOptions;
      document.getElementById('new-q-subject').innerHTML = subjOptions;
      document.getElementById('gap-subject-select').innerHTML = subjOptions;

      document.getElementById('sim-filter-subject').innerHTML = `<option value="ALL">Todas as Matérias (${SUBJECTS.length})</option>` + SUBJECTS.map(s => `<option value="${s.id}">[Tier ${s.tier}] ${s.short}</option>`).join('');
      document.getElementById('gap-filter-select').innerHTML = `<option value="ALL">Todas as Matérias</option>` + SUBJECTS.map(s => `<option value="${s.id}">[Tier ${s.tier}] ${s.short}</option>`).join('');

      document.getElementById('discursive-theme-select').innerHTML = DISCURSIVE_THEMES.map(t => `<option value="${t.id}">${t.title}</option>`).join('');
    }

    window.addEventListener('DOMContentLoaded', () => {
      loadState();
      initSelectDropdowns();
      loadDiscursiveTheme();
      updateDiscursiveCalc();
      renderCodiceModules();
      updateAllUI();
    });
  </script>
</body>
</html>
