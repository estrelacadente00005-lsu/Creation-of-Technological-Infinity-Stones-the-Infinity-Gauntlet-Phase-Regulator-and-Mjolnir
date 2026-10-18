
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laboratório de Engenharia Métrico-Dimensional - Joias, Manopla & Mjolnir</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        cyber: {
                            bg: '#02050e',
                            panel: '#070f26',
                            border: '#00f3ff',
                            text: '#d0f2ff',
                            space: '#00f3ff',
                            time: '#00ff66',
                            power: '#ff0055',
                            mind: '#ffcc00',
                            soul: '#ff6600',
                            reality: '#bd00ff',
                        }
                    },
                    fontFamily: {
                        mono: ['Courier New', 'monospace'],
                    }
                }
            }
        }
    </script>
    <style>
        body {
            background-color: #02050e;
            color: #d0f2ff;
            font-family: 'Courier New', Courier, monospace;
            user-select: none;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 15% 15%, rgba(0, 243, 255, 0.08) 0%, transparent 45%),
                radial-gradient(circle at 85% 85%, rgba(189, 0, 255, 0.08) 0%, transparent 45%);
        }

        /* Custom Scrollbar for HUD aesthetics */
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #04091a;
        }
        ::-webkit-scrollbar-thumb {
            background: #00f3ff;
            border-radius: 3px;
        }

        .neon-glow-cyan {
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.3);
        }
        .neon-text-cyan {
            text-shadow: 0 0 10px rgba(0, 243, 255, 0.6);
        }
        .neon-text-gold {
            text-shadow: 0 0 10px rgba(255, 204, 0, 0.6);
        }

        /* Sci-Fi Sliders */
        input[type="range"] {
            -webkit-appearance: none;
            appearance: none;
            width: 100%;
            height: 6px;
            background: #0d1b3e;
            border-radius: 3px;
            outline: none;
            border: 1px solid rgba(0, 243, 255, 0.3);
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #00f3ff;
            cursor: pointer;
            box-shadow: 0 0 10px #00f3ff;
        }

        /* Tab Active States */
        .tab-btn {
            transition: all 0.3s ease;
        }
        .tab-btn.active {
            background: rgba(0, 243, 255, 0.15);
            border-color: #00f3ff;
            color: #00f3ff;
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.25);
        }

        /* Custom Canvas Cursor */
        canvas {
            cursor: crosshair;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col items-center justify-between p-3 lg:p-6">

    <!-- CABEÇALHO HUD PRINCIPAL -->
    <header class="w-full max-w-7xl mb-4 border-b border-cyber-border/40 pb-3 flex flex-col md:flex-row justify-between items-center gap-3">
        <div>
            <h1 class="text-xl md:text-2xl font-bold text-cyber-border tracking-wider neon-text-cyan flex items-center gap-2">
                <span>⚡ IMPRESSORA QUÂNTICA 6D</span>
                <span class="text-xs bg-cyber-border/20 text-cyber-border px-2 py-0.5 rounded border border-cyber-border/50">MÉTRICA 11D</span>
            </h1>
            <p class="text-xs text-blue-300/70 mt-1">Sistemas SAMS/SROS • Reator HD-MHD • Engenharia Métrico-Dimensional de Artefatos</p>
        </div>
        <div class="flex items-center gap-4 text-xs bg-cyber-panel/80 px-4 py-2 rounded-lg border border-cyber-border/30">
            <div>
                <span class="text-gray-400 block">SINGULARIDADE:</span>
                <span id="headerSingularity" class="text-cyber-space font-bold">100.0% COERENTE</span>
            </div>
            <div class="border-l border-gray-700 h-6"></div>
            <div>
                <span class="text-gray-400 block">FLUXO MHD:</span>
                <span id="headerMHD" class="text-cyber-power font-bold">98.4 Yotta-W</span>
            </div>
        </div>
    </header>

    <!-- CONTAINER PRINCIPAL DO APPS -->
    <main class="w-full max-w-7xl grid grid-cols-1 lg:grid-cols-12 gap-4 flex-grow">

        <!-- PAINEL ESQUERDO: CONTROLES E SELEÇÃO DE ARTEFATO -->
        <section class="lg:col-span-3 bg-cyber-panel/90 border border-cyber-border/30 rounded-xl p-4 flex flex-col justify-between gap-4 backdrop-blur-md">
            
            <div class="space-y-3">
                <div class="text-xs text-cyber-border font-bold uppercase tracking-wider border-b border-cyber-border/20 pb-2 flex justify-between">
                    <span>1. Artefato em Produção</span>
                    <span class="text-gray-400">[6D-PRINT]</span>
                </div>

                <!-- ABAS DE NAVEGAÇÃO -->
                <button id="tab1" onclick="switchModule('stones')" class="tab-btn active w-full text-left p-3 rounded-lg border border-gray-800 bg-gray-900/60 text-xs font-bold flex flex-col gap-1">
                    <div class="flex items-center justify-between">
                        <span class="text-cyber-space">💎 1. JOIAS DO INFINITO</span>
                        <span class="text-[10px] bg-cyan-950 text-cyan-400 px-1.5 py-0.5 rounded">6 SINGULARIDADES</span>
                    </div>
                    <span class="text-[11px] text-gray-400 font-normal">Confinamento Métrico de Garganta de Minhoca</span>
                </button>

                <button id="tab2" onclick="switchModule('gauntlet')" class="tab-btn w-full text-left p-3 rounded-lg border border-gray-800 bg-gray-900/60 text-xs font-bold flex flex-col gap-1">
                    <div class="flex items-center justify-between">
                        <span class="text-cyber-reality">🥊 2. MANOPLA REGULADORA</span>
                        <span class="text-[10px] bg-purple-950 text-purple-300 px-1.5 py-0.5 rounded">CHASSI SAMS</span>
                    </div>
                    <span class="text-[11px] text-gray-400 font-normal">Absorvedor Bio-SAMS e Lasers SROS</span>
                </button>

                <button id="tab3" onclick="switchModule('mjolnir')" class="tab-btn w-full text-left p-3 rounded-lg border border-gray-800 bg-gray-900/60 text-xs font-bold flex flex-col gap-1">
                    <div class="flex items-center justify-between">
                        <span class="text-cyber-mind">🔨 3. MJOLNIR (QUARK-GLUON)</span>
                        <span class="text-[10px] bg-yellow-950 text-yellow-300 px-1.5 py-0.5 rounded">IA BIOMÉTRICA</span>
                    </div>
                    <span class="text-[11px] text-gray-400 font-normal">Matéria Decaída e Algoritmo da Dignidade</span>
                </button>
            </div>

            <!-- CONTROLES MODULADORES SLIDERS -->
            <div class="space-y-4 border-t border-cyber-border/20 pt-3">
                <div class="text-xs text-cyber-border font-bold uppercase tracking-wider">
                    <span>Moduladores de Campo</span>
                </div>

                <div class="space-y-1">
                    <div class="flex justify-between text-xs">
                        <span class="text-gray-300" id="lblSlider1">Frequência de Dobra:</span>
                        <span class="text-cyber-border font-bold" id="valSlider1">142.8 GHz</span>
                    </div>
                    <input type="range" id="slider1" min="10" max="200" value="142" oninput="updateSliders()">
                </div>

                <div class="space-y-1">
                    <div class="flex justify-between text-xs">
                        <span class="text-gray-300" id="lblSlider2">Estabilização Bio-SAMS:</span>
                        <span class="text-cyber-border font-bold" id="valSlider2">95.0%</span>
                    </div>
                    <input type="range" id="slider2" min="1" max="100" value="95" oninput="updateSliders()">
                </div>

                <div class="space-y-1">
                    <div class="flex justify-between text-xs">
                        <span class="text-gray-300" id="lblSlider3">Massa Métrica Quark-Gluon:</span>
                        <span class="text-cyber-border font-bold" id="valSlider3">1.8e14 kg</span>
                    </div>
                    <input type="range" id="slider3" min="1" max="100" value="50" oninput="updateSliders()">
                </div>
            </div>

            <!-- BOTÕES DE INTERAÇÃO ESPECÍFICA -->
            <div class="space-y-2 border-t border-cyber-border/20 pt-3" id="actionPanel">
                <!-- Injetado dinamicamente via JS -->
            </div>
        </section>

        <!-- PAINEL CENTRAL: CANVA INTERATIVO DE SIMULAÇÃO 2D -->
        <section class="lg:col-span-6 bg-black/80 border border-cyber-border/40 rounded-xl relative flex flex-col items-center justify-center min-h-[420px] lg:min-h-[520px] overflow-hidden shadow-2xl">
            <!-- TAG HUD SOBREPOSTA NO CANVAS -->
            <div class="absolute top-3 left-3 bg-black/80 border border-cyber-border/30 px-3 py-1.5 rounded text-[11px] text-cyber-border font-bold tracking-wide z-10 flex items-center gap-2">
                <span class="w-2 h-2 rounded-full bg-cyber-space animate-ping"></span>
                <span id="canvasStatusTag">EXIBINDO: SANGUINÁRIAS DE SINGULARIDADE MÉTRICA</span>
            </div>

            <!-- CANVAS 2D -->
            <canvas id="simCanvas" class="w-full h-full block z-0"></canvas>

            <!-- RODAPÉ HUD SOBREPOSTO NO CANVAS -->
            <div class="absolute bottom-3 right-3 bg-black/90 border border-purple-500/30 p-2.5 rounded text-[11px] text-gray-300 z-10 text-right space-y-0.5 pointer-events-none">
                <div id="hudLine1" class="text-cyber-space font-bold">ESTADO DE CONFINAMENTO: ESTÁVEL</div>
                <div id="hudLine2" class="text-gray-400">Garganta de minhoca aprisionada em Brana 11D</div>
                <div id="hudLine3" class="text-cyber-power">Feedback Térmico: 24.3 MK</div>
            </div>
        </section>

        <!-- PAINEL DIREITO: MONITORIA DE TELEMETRIA E LOGS -->
        <section class="lg:col-span-3 bg-cyber-panel/90 border border-cyber-border/30 rounded-xl p-4 flex flex-col justify-between gap-4 backdrop-blur-md">
            
            <!-- ESPECIFICAÇÕES TÉCNICAS DO ARTEFATO ATIVO -->
            <div class="space-y-3">
                <div class="text-xs text-cyber-border font-bold uppercase tracking-wider border-b border-cyber-border/20 pb-2">
                    <span>Telemetria em Tempo Real</span>
                </div>

                <div class="bg-gray-950/80 border border-cyber-border/20 rounded-lg p-3 space-y-2 text-xs">
                    <div class="flex justify-between items-center">
                        <span class="text-gray-400">Coerência Brana:</span>
                        <span id="telemetryCoherence" class="text-cyber-space font-bold">99.98%</span>
                    </div>
                    <div class="flex justify-between items-center">
                        <span class="text-gray-400">Absorção Gravitacional:</span>
                        <span id="telemetryGravity" class="text-cyber-time font-bold">14.2 GPa</span>
                    </div>
                    <div class="flex justify-between items-center">
                        <span class="text-gray-400">Temperatura SAMS:</span>
                        <span id="telemetryTemp" class="text-cyber-power font-bold">310.2 K</span>
                    </div>
                    <div class="flex justify-between items-center">
                        <span class="text-gray-400">Matriz SROS Laser:</span>
                        <span id="telemetryLaser" class="text-cyber-mind font-bold">SINCRO FULL-DUPLEX</span>
                    </div>
                </div>

                <!-- CARD EXPLICATIVO DA TECNOLOGIA -->
                <div class="bg-cyan-950/20 border border-cyan-500/30 rounded-lg p-3 text-[11px] leading-relaxed text-blue-200">
                    <h4 id="techTitle" class="font-bold text-cyber-space mb-1">SINGULARIDADE CONFINADA</h4>
                    <p id="techDesc">
                        Cada joia é uma micro-garganta de buraco de minhoca capturada da fase inflacionária do vácuo quântico e mantida estável através de uma casca de Cristal de Memória de Brana.
                    </p>
                </div>
            </div>

            <!-- LOGS DO SISTEMA EM TEMPO REAL -->
            <div class="space-y-2 border-t border-cyber-border/20 pt-3 flex-grow flex flex-col justify-end">
                <div class="text-xs text-cyber-border font-bold uppercase tracking-wider flex justify-between">
                    <span>Terminal de Eventos</span>
                    <span class="text-gray-500 text-[10px]">LIVE LOGS</span>
                </div>

                <div id="terminalLog" class="bg-black/90 border border-gray-800 rounded-lg p-2.5 h-36 overflow-y-auto text-[10px] space-y-1 font-mono text-gray-300">
                    <div class="text-cyber-space">> Impressora 6D inicializada no modo Métrico-Dimensional.</div>
                    <div class="text-cyber-time">> Matriz de Cristais de Brana acoplada ao chassi.</div>
                </div>
            </div>
        </section>

    </main>

    <!-- RODAPÉ COMPACTO -->
    <footer class="w-full max-w-7xl mt-3 text-center text-[11px] text-gray-500 border-t border-gray-900 pt-2">
        Engenharia Métrico-Dimensional Avançada • Simulação de Campo Gravitacional e Fusão Atômico-Quântica
    </footer>

    <!-- SCRIPT DA APLICAÇÃO E ENGINE DO CANVAS -->
    <script>
        // ESTADO GLOBAL DA APLICAÇÃO
        const state = {
            activeModule: 'stones', // 'stones', 'gauntlet', 'mjolnir'
            selectedStoneIndex: 0,
            gauntletStonesInserted: [false, false, false, false, false, false],
            isGauntletActive: false,
            mjolnirDignity: true, // true: Digno (Antigravidade), false: Não Digno (Massa Infinita)
            isMjolnirHeld: false,
            mjolnirY: 0,
            sliders: {
                slider1: 142,
                slider2: 95,
                slider3: 50
            }
        };

        // DADOS DAS 6 JOIAS DO INFINITO TECNOLÓGICAS
        const infinityStones = [
            { name: "Espaço", color: "#00f3ff", tech: "Gerador de Micro-Dobra Alcubierre", desc: "Dobra a métrica do espaço local permitindo deslocamento superlumínico e teletransporte quântico sem deslocamento mecânico." },
            { name: "Tempo", color: "#00ff66", tech: "Dilatação Relativística em Rotação", desc: "Acelera ou reverte marcos temporais locais utilizando campos de rotação de curvatura métrica induzidos por naves A/B." },
            { name: "Poder", color: "#ff0055", tech: "Reator HD-MHD Vácuo Quântico", desc: "Canaliza densidade energética pura de plasma magnetohidrodinâmico comprimido na escala subatômica." },
            { name: "Mente", color: "#ffcc00", tech: "Matriz SROS Neuronal Multidimensional", desc: "Supercomputador de brana processando probabilidades quânticas e controlando padrões bioelétricos neurais." },
            { name: "Alma", color: "#ff6600", tech: "Campo de Coerência Bio-SAMS Vivo", desc: "Ressoa com o fluido citoplasmático e vetores de energia vital de organismos vivos na 6ª dimensão." },
            { name: "Realidade", color: "#bd00ff", tech: "Injetor Quântico de Matéria Decaída", desc: "Altera a tabela periódica local reconfigurando estados de quarks e gluons em tempo real." }
        ];

        // REFERÊNCIAS DO CANVAS
        const canvas = document.getElementById('simCanvas');
        const ctx = canvas.getContext('2d');

        // ELEMENTOS DO DOM PARA ATUALIZAÇÃO
        const canvasStatusTag = document.getElementById('canvasStatusTag');
        const hudLine1 = document.getElementById('hudLine1');
        const hudLine2 = document.getElementById('hudLine2');
        const hudLine3 = document.getElementById('hudLine3');
        const techTitle = document.getElementById('techTitle');
        const techDesc = document.getElementById('techDesc');
        const terminalLog = document.getElementById('terminalLog');
        const actionPanel = document.getElementById('actionPanel');

        // RESIZE AUTOMÁTICO DO CANVAS
        function resizeCanvas() {
            const rect = canvas.parentElement.getBoundingClientRect();
            canvas.width = rect.width;
            canvas.height = rect.height;
            state.mjolnirY = canvas.height * 0.45;
        }
        window.addEventListener('resize', resizeCanvas);

        // REGISTRO DE LOGS
        function log(msg, colorClass = "text-cyber-space") {
            const entry = document.createElement('div');
            entry.className = `${colorClass}`;
            const time = new Date().toLocaleTimeString();
            entry.textContent = `[${time}] ${msg}`;
            terminalLog.appendChild(entry);
            terminalLog.scrollTop = terminalLog.scrollHeight;
        }

        // TROCA DE MÓDULOS
        function switchModule(mod) {
            state.activeModule = mod;
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
            
            if (mod === 'stones') {
                document.getElementById('tab1').classList.add('active');
                canvasStatusTag.textContent = "EXIBINDO: DISPOSITIVOS DE CONFINAMENTO DE SINGULARIDADE";
                techTitle.textContent = "TECNOLOGIA DE SINGULARIDADE MÉTRICA";
                techDesc.textContent = "Cada joia é uma garganta de buraco de minhoca microscopicamente aprisionada em uma casca de Cristais de Memória de Brana (11D Calabi-Yau).";
                log("Módulo 1 selecionado: Análise de Singularidades Métricas Confinadas.");
            } else if (mod === 'gauntlet') {
                document.getElementById('tab2').classList.add('active');
                canvasStatusTag.textContent = "EXIBINDO: MANOPLA DO INFINITO (REGULADOR DE FASE SAMS/SROS)";
                techTitle.textContent = "REGULADOR DE FASE BIO-SAMS";
                techDesc.textContent = "Chassi integrador equipado com fluido magnetorreológico que endurece em milissegundos para absorver o feedback de ondas gravitacionais e térmicas.";
                log("Módulo 2 selecionado: Manopla Reguladora de Fase acoplada.", "text-cyber-reality");
            } else if (mod === 'mjolnir') {
                document.getElementById('tab3').classList.add('active');
                canvasStatusTag.textContent = "EXIBINDO: MJOLNIR (MATÉRIA QUARK-GLUON ESTABILIZADA)";
                techTitle.textContent = "ALGORITMO DA DIGNIDADE (IA + MHD)";
                techDesc.textContent = "O martelo é impresso em matéria de estrela de nêutrons. Se a IA biométrica do SROS não reconhecer o usuário, o reator MHD aumenta a massa atômica para infinito.";
                log("Módulo 3 selecionado: Matéria Quark-Gluon & Teste de Dignidade Biométrica.", "text-cyber-mind");
            }

            updateSlidersLabels();
            renderActionPanel();
        }

        // ATUALIZAÇÃO DOS RÓTULOS DOS SLIDERS COM BASE NO MÓDULO
        function updateSlidersLabels() {
            const l1 = document.getElementById('lblSlider1');
            const l2 = document.getElementById('lblSlider2');
            const l3 = document.getElementById('lblSlider3');

            if (state.activeModule === 'stones') {
                l1.textContent = "Frequência de Dobra Alcubierre:";
                l2.textContent = "Pressão do Cristal de Brana:";
                l3.textContent = "Fluxo do Reator HD-MHD:";
            } else if (state.activeModule === 'gauntlet') {
                l1.textContent = "Coerência dos Lasers SROS:";
                l2.textContent = "Amortecimento Bio-SAMS:";
                l3.textContent = "Supressão de Thermal Feedback:";
            } else if (state.activeModule === 'mjolnir') {
                l1.textContent = "Densidade da Matéria Decaída:";
                l2.textContent = "Atração Gravitacional MHD:";
                l3.textContent = "Vetor Micro-Antigravidade:";
            }
            updateSliders();
        }

        function updateSliders() {
            state.sliders.slider1 = document.getElementById('slider1').value;
            state.sliders.slider2 = document.getElementById('slider2').value;
            state.sliders.slider3 = document.getElementById('slider3').value;

            document.getElementById('valSlider1').textContent = state.sliders.slider1 + (state.activeModule === 'stones' ? ' GHz' : ' %');
            document.getElementById('valSlider2').textContent = state.sliders.slider2 + ' %';
            document.getElementById('valSlider3').textContent = (state.sliders.slider3 * 0.18).toFixed(2) + ' e14 kg';

            // Atualiza métricas na interface
            document.getElementById('telemetryCoherence').textContent = (90 + state.sliders.slider1 * 0.05).toFixed(2) + '%';
            document.getElementById('telemetryGravity').textContent = (10 + state.sliders.slider3 * 0.2).toFixed(1) + ' GPa';
        }

        // REDERIZAR BOTÕES DINÂMICOS NO PAINEL ESQUERDO
        function renderActionPanel() {
            actionPanel.innerHTML = '';

            if (state.activeModule === 'stones') {
                const title = document.createElement('div');
                title.className = "text-[11px] text-gray-400 font-bold mb-1";
                title.textContent = "SELECIONAR JOIA PARA ANÁLISE:";
                actionPanel.appendChild(title);

                const grid = document.createElement('div');
                grid.className = "grid grid-cols-3 gap-1.5";

                infinityStones.forEach((stone, idx) => {
                    const btn = document.createElement('button');
                    btn.className = `p-1.5 rounded text-[10px] font-bold border transition ${state.selectedStoneIndex === idx ? 'border-white text-white' : 'border-gray-800 text-gray-400'}`;
                    btn.style.backgroundColor = `${stone.color}22`;
                    btn.style.borderColor = stone.color;
                    btn.textContent = stone.name;
                    btn.onclick = () => {
                        state.selectedStoneIndex = idx;
                        log(`Joia do ${stone.name} isolada na câmara de contenção.`, "text-cyber-space");
                        renderActionPanel();
                    };
                    grid.appendChild(btn);
                });
                actionPanel.appendChild(grid);

            } else if (state.activeModule === 'gauntlet') {
                const btnFit = document.createElement('button');
                btnFit.className = "w-full py-2 bg-purple-900/40 hover:bg-purple-800/60 border border-purple-500 text-purple-200 text-xs font-bold rounded transition shadow-lg";
                btnFit.textContent = "⚡ ENCAIXAR TODAS AS JOIAS NO CHASSI";
                btnFit.onclick = () => {
                    state.gauntletStonesInserted = [true, true, true, true, true, true];
                    log("Todas as 6 Joias Tecnológicas acopladas no Chassi da Manopla!", "text-cyber-reality");
                };

                const btnSnap = document.createElement('button');
                btnSnap.className = "w-full py-2 bg-red-900/40 hover:bg-red-800/60 border border-red-500 text-red-200 text-xs font-bold rounded transition shadow-lg mt-2";
                btnSnap.textContent = "💥 ATIVAR PULSO TOTAL (REGULAÇÃO DE FASE)";
                btnSnap.onclick = () => {
                    state.isGauntletActive = true;
                    log("ALERTA: Pulso de Singularidade Quântica disparado! Chassi Bio-SAMS suportando a carga gravitacional.", "text-cyber-power");
                    setTimeout(() => { state.isGauntletActive = false; }, 2500);
                };

                actionPanel.appendChild(btnFit);
                actionPanel.appendChild(btnSnap);

            } else if (state.activeModule === 'mjolnir') {
                const btnToggleDignity = document.createElement('button');
                btnToggleDignity.className = `w-full py-2 rounded text-xs font-bold border transition ${state.mjolnirDignity ? 'bg-green-900/40 border-green-500 text-green-200' : 'bg-red-900/40 border-red-500 text-red-200'}`;
                btnToggleDignity.textContent = state.mjolnirDignity ? "USUÁRIO: DIGNO (SROS AUTORIZADO)" : "USUÁRIO: NÃO DIGNO (NÃO AUTORIZADO)";
                btnToggleDignity.onclick = () => {
                    state.mjolnirDignity = !state.mjolnirDignity;
                    if (state.mjolnirDignity) {
                        log("SROS: Assinatura biométrica RECONHECIDA. Micro-antigravidade ativada.", "text-cyber-time");
                    } else {
                        log("SROS ALERTA: Assinatura NÃO autorizada! Ativando atração gravitacional MHD ao centro da Terra.", "text-cyber-power");
                    }
                    renderActionPanel();
                };

                actionPanel.appendChild(btnToggleDignity);
            }
        }

        // LISTENERS DE MOUSE PARA O CANVA (INTERAÇÃO MJOLNIR)
        canvas.addEventListener('mousedown', (e) => {
            if (state.activeModule === 'mjolnir') {
                state.isMjolnirHeld = true;
            }
        });
        canvas.addEventListener('mouseup', () => { state.isMjolnirHeld = false; });
        canvas.addEventListener('mouseleave', () => { state.isMjolnirHeld = false; });

        // ==========================================
        // ANIMATION LOOP & RENDERIZADORES DO CANVAS
        // ==========================================

        let animTime = 0;

        function animate() {
            animTime += 0.03;
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // DESENHA GRADE SCI-FI DE FUNDO NO CANVAS
            drawSciFiGrid();

            if (state.activeModule === 'stones') {
                renderStonesScene();
            } else if (state.activeModule === 'gauntlet') {
                renderGauntletScene();
            } else if (state.activeModule === 'mjolnir') {
                renderMjolnirScene();
            }

            requestAnimationFrame(animate);
        }

        // DESENHAR GRADE SCI-FI
        function drawSciFiGrid() {
            ctx.strokeStyle = "rgba(0, 243, 255, 0.04)";
            ctx.lineWidth = 1;
            const gridSize = 40;

            for (let x = 0; x < canvas.width; x += gridSize) {
                ctx.beginPath();
                ctx.moveTo(x, 0);
                ctx.lineTo(x, canvas.height);
                ctx.stroke();
            }
            for (let y = 0; y < canvas.height; y += gridSize) {
                ctx.beginPath();
                ctx.moveTo(0, y);
                ctx.lineTo(canvas.width, y);
                ctx.stroke();
            }
        }

        // ------------------------------------------
        // 1. RENDERIZADOR: JOIAS DO INFINITO
        // ------------------------------------------
        function renderStonesScene() {
            const stone = infinityStones[state.selectedStoneIndex];
            const cx = canvas.width / 2;
            const cy = canvas.height / 2;

            // Anéis de Confinamento de Brana (11D)
            ctx.save();
            ctx.translate(cx, cy);

            for (let i = 0; i < 3; i++) {
                ctx.rotate(animTime * (i % 2 === 0 ? 0.5 : -0.5));
                ctx.strokeStyle = stone.color;
                ctx.lineWidth = 1.5;
                ctx.globalAlpha = 0.4;
                ctx.beginPath();
                ctx.ellipse(0, 0, 110 + i * 20, 45 + i * 15, i * Math.PI / 4, 0, Math.PI * 2);
                ctx.stroke();
            }
            ctx.restore();

            // Garganta do Buraco de Minhoca / Singularidade Central
            ctx.shadowColor = stone.color;
            ctx.shadowBlur = 35;
            ctx.fillStyle = "#ffffff";
            ctx.beginPath();
            ctx.arc(cx, cy, 25 + Math.sin(animTime * 3) * 3, 0, Math.PI * 2);
            ctx.fill();

            // Casca de Cristal de Memória de Brana (Geometria Cobre)
            ctx.strokeStyle = stone.color;
            ctx.lineWidth = 3;
            ctx.shadowBlur = 15;
            ctx.beginPath();
            const sides = 6;
            const radius = 55;
            for (let i = 0; i < sides; i++) {
                const angle = (i * Math.PI * 2 / sides) + animTime * 0.2;
                const x = cx + Math.cos(angle) * radius;
                const y = cy + Math.sin(angle) * radius;
                if (i === 0) ctx.moveTo(x, y);
                else ctx.lineTo(x, y);
            }
            ctx.closePath();
            ctx.stroke();
            ctx.shadowBlur = 0;

            // Pulsações de Ondas Quânticas
            ctx.strokeStyle = stone.color;
            ctx.globalAlpha = 0.2;
            ctx.lineWidth = 2;
            const pulseR = (animTime * 60) % 180;
            ctx.beginPath();
            ctx.arc(cx, cy, pulseR, 0, Math.PI * 2);
            ctx.stroke();
            ctx.globalAlpha = 1.0;

            // HUD
            hudLine1.textContent = `SINGULARIDADE: ${stone.name.toUpperCase()}`;
            hudLine1.style.color = stone.color;
            hudLine2.textContent = stone.tech;
            hudLine3.textContent = `Frequência de Dobra: ${state.sliders.slider1} GHz`;

            techTitle.textContent = `JOIA DO ${stone.name.toUpperCase()}`;
            techDesc.textContent = stone.desc;
        }

        // ------------------------------------------
        // 2. RENDERIZADOR: MANOPLA DO INFINITO
        // ------------------------------------------
        function renderGauntletScene() {
            const cx = canvas.width / 2;
            const cy = canvas.height / 2 + 20;

            // Desenho do Braço / Chassi SAMS
            ctx.fillStyle = "#0c152e";
            ctx.strokeStyle = state.isGauntletActive ? "#ff0055" : "#00f3ff";
            ctx.lineWidth = 3;
            ctx.shadowColor = ctx.strokeStyle;
            ctx.shadowBlur = state.isGauntletActive ? 30 : 10;

            // Chassi do Antebraço
            ctx.beginPath();
            ctx.moveTo(cx - 70, cy + 180);
            ctx.lineTo(cx - 50, cy);
            ctx.lineTo(cx + 50, cy);
            ctx.lineTo(cx + 70, cy + 180);
            ctx.closePath();
            ctx.fill();
            ctx.stroke();

            // Palma e Articulações Bio-SAMS (Fluido Magnetorreológico)
            ctx.fillStyle = "#16254d";
            ctx.beginPath();
            ctx.arc(cx, cy - 30, 50, 0, Math.PI * 2);
            ctx.fill();
            ctx.stroke();

            // Posicionamento das 6 Joias no Chassi
            const stonePositions = [
                { x: cx - 35, y: cy - 20 }, // Espaço
                { x: cx - 15, y: cy - 35 }, // Tempo
                { x: cx + 15, y: cy - 35 }, // Poder
                { x: cx + 35, y: cy - 20 }, // Mente
                { x: cx, y: cy - 10 },      // Alma (Centro)
                { x: cx, y: cy + 50 }       // Realidade (Punho)
            ];

            stonePositions.forEach((pos, idx) => {
                const stone = infinityStones[idx];
                const isInserted = state.gauntletStonesInserted[idx];

                ctx.beginPath();
                ctx.arc(pos.x, pos.y, 10, 0, Math.PI * 2);
                
                if (isInserted) {
                    ctx.fillStyle = stone.color;
                    ctx.shadowColor = stone.color;
                    ctx.shadowBlur = 20;
                    ctx.fill();

                    // Lasers SROS de Conectividade Full Duplex
                    ctx.strokeStyle = stone.color;
                    ctx.lineWidth = 1.5;
                    ctx.beginPath();
                    ctx.moveTo(pos.x, pos.y);
                    ctx.lineTo(cx, cy - 30); // Conecta ao reator central da palma
                    ctx.stroke();
                } else {
                    ctx.fillStyle = "#040914";
                    ctx.strokeStyle = "#1a2c5b";
                    ctx.lineWidth = 2;
                    ctx.fill();
                    ctx.stroke();
                }
            });

            // Efeito Visual de Absorção Térmica Bio-SAMS quando ativo
            if (state.isGauntletActive) {
                ctx.strokeStyle = "#ff0055";
                ctx.lineWidth = 4;
                ctx.shadowColor = "#ff0055";
                ctx.shadowBlur = 25;

                for (let i = 0; i < 8; i++) {
                    const angle = animTime * 4 + i * (Math.PI / 4);
                    const rx = cx + Math.cos(angle) * 90;
                    const ry = cy + Math.sin(angle) * 90;
                    ctx.beginPath();
                    ctx.moveTo(cx, cy - 20);
                    ctx.lineTo(rx, ry);
                    ctx.stroke();
                }
            }

            // HUD
            hudLine1.textContent = "CHASSI: REGULADOR DE FASE SAMS/SROS";
            hudLine1.style.color = state.isGauntletActive ? "#ff0055" : "#00f3ff";
            hudLine2.textContent = `Absorção Térmica Bio-SAMS: ${state.sliders.slider2}%`;
            hudLine3.textContent = state.isGauntletActive ? "ALERTA: PULSO GRAVITACIONAL EM ABSORÇÃO!" : "Estável • Pronto para Pulso";
        }

        // ------------------------------------------
        // 3. RENDERIZADOR: MJOLNIR (QUARK-GLUON)
        // ------------------------------------------
        function renderMjolnirScene() {
            const cx = canvas.width / 2;

            // Mecânica do Algoritmo da Dignidade
            if (!state.mjolnirDignity) {
                // Não Digno: O martelo afunda na malha devido à massa infinita
                if (state.mjolnirY < canvas.height - 100) {
                    state.mjolnirY += 4;
                }
            } else {
                // Digno: Micro-antigravidade levita o martelo suavemente
                const targetY = canvas.height * 0.45 + Math.sin(animTime * 2) * 12;
                state.mjolnirY += (targetY - state.mjolnirY) * 0.1;
            }

            const cy = state.mjolnirY;

            // Desenhar Malha do Espaço-Tempo Deformada (Lensing Gravitacional)
            ctx.strokeStyle = state.mjolnirDignity ? "rgba(0, 243, 255, 0.15)" : "rgba(255, 0, 85, 0.4)";
            ctx.lineWidth = 1;
            const gridSpacing = 30;

            for (let x = 50; x < canvas.width - 50; x += gridSpacing) {
                ctx.beginPath();
                ctx.moveTo(x, canvas.height - 30);
                
                // Distorção métrica quanto mais perto do martelo
                const dist = Math.abs(x - cx);
                const warp = Math.max(0, (200 - dist) * (!state.mjolnirDignity ? 0.8 : 0.15));
                ctx.lineTo(x, canvas.height - 30 + warp);
                ctx.stroke();
            }

            // Desenho do Martelo Mjolnir (Matéria Quark-Gluon)
            ctx.save();
            ctx.translate(cx, cy);

            // Cabo do Martelo
            ctx.fillStyle = "#1f1912";
            ctx.strokeStyle = "#00f3ff";
            ctx.lineWidth = 1.5;
            ctx.fillRect(-6, 30, 12, 110);
            ctx.strokeRect(-6, 30, 12, 110);

            // Cabeça do Martelo (Matéria Decaída Hiperdensa)
            ctx.fillStyle = "#0c101d";
            ctx.strokeStyle = state.mjolnirDignity ? "#00f3ff" : "#ff0055";
            ctx.lineWidth = 3;
            ctx.shadowColor = ctx.strokeStyle;
            ctx.shadowBlur = state.mjolnirDignity ? 20 : 35;

            ctx.beginPath();
            ctx.moveTo(-60, -35);
            ctx.lineTo(60, -35);
            ctx.lineTo(75, -15);
            ctx.lineTo(75, 25);
            ctx.lineTo(60, 40);
            ctx.lineTo(-60, 40);
            ctx.lineTo(-75, 25);
            ctx.lineTo(-75, -15);
            ctx.closePath();
            ctx.fill();
            ctx.stroke();

            // Runas da IA Biométrica / SROS na superfície
            ctx.strokeStyle = state.mjolnirDignity ? "#ffcc00" : "#ff0055";
            ctx.lineWidth = 1;
            ctx.beginPath();
            ctx.arc(0, 2, 12, 0, Math.PI * 2);
            ctx.stroke();

            // Faíscas de Eletromagnetismo de Plasma se Digno
            if (state.mjolnirDignity) {
                ctx.strokeStyle = "#00f3ff";
                ctx.lineWidth = 2;
                for (let i = 0; i < 4; i++) {
                    if (Math.random() > 0.4) {
                        ctx.beginPath();
                        ctx.moveTo((Math.random() - 0.5) * 100, (Math.random() - 0.5) * 50);
                        ctx.lineTo((Math.random() - 0.5) * 140, (Math.random() - 0.5) * 80);
                        ctx.stroke();
                    }
                }
            }

            ctx.restore();

            // HUD
            hudLine1.textContent = state.mjolnirDignity ? "SROS: USUÁRIO DIGNO (ANTIGRAVIDADE ATIVA)" : "SROS: USUÁRIO NÃO AUTORIZADO (MASSA INFINITA)";
            hudLine1.style.color = state.mjolnirDignity ? "#00ff66" : "#ff0055";
            hudLine2.textContent = `Densidade Quark-Gluon: ${(state.sliders.slider3 * 0.18).toFixed(2)} e14 kg`;
            hudLine3.textContent = state.mjolnirDignity ? "Campo de Antigravidade: -9.8 m/s² (Leve)" : "Atração Gravitacional: ∞ N (Inamovível)";
        }

        // INICIALIZAÇÃO DA ENGINE
        window.onload = () => {
            resizeCanvas();
            updateSlidersLabels();
            renderActionPanel();
            animate();
            log("Laboratório Quântico pronto. Todos os parâmetros métricos sincronizados.");
        };
    </script>
</body>
</html>
