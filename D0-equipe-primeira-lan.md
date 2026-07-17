* {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        background: var(--bg-gradient);
        background-size: 400% 400%;
        animation: gradientBG 15s ease infinite;
        color: #f1f5f9;
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 20px;
        overflow-x: hidden;
    }

    @keyframes gradientBG {
        0% { background-position: 0% 50%; }
        50% { background-position: 100% 50%; }
        100% { background-position: 0% 50%; }
    }

    .container {
        max-width: 900px;
        width: 100%;
        background: rgba(15, 23, 42, 0.65);
        backdrop-filter: blur(12px);
        -webkit-backdrop-filter: blur(12px);
        border: 1px solid var(--card-border);
        border-radius: 24px;
        padding: 40px;
        box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4), 
                    0 0 40px rgba(168, 85, 247, 0.1);
        text-align: center;
        position: relative;
    }

    .container::before {
        content: '';
        position: absolute;
        top: -2px;
        left: -2px;
        right: -2px;
        bottom: -2px;
        background: linear-gradient(45deg, var(--accent-cyan), var(--accent-purple), var(--accent-pink));
        border-radius: 26px;
        z-index: -1;
        opacity: 0.3;
        filter: blur(5px);
    }

    header h1 {
        font-size: 2.8rem;
        font-weight: 800;
        background: linear-gradient(to right, var(--accent-cyan), var(--accent-purple), var(--accent-pink));
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 5px;
        letter-spacing: -1px;
        filter: drop-shadow(0 2px 10px rgba(6, 182, 212, 0.2));
    }

    header h3 {
        font-size: 1.1rem;
        color: #94a3b8;
        text-transform: uppercase;
        letter-spacing: 2px;
        margin-bottom: 25px;
    }

    .badge-status {
        display: inline-flex;
        align-items: center;
        background: rgba(34, 197, 94, 0.1);
        border: 1px solid rgba(34, 197, 94, 0.3);
        color: var(--accent-green);
        padding: 6px 16px;
        border-radius: 50px;
        font-size: 0.85rem;
        font-weight: 600;
        margin-bottom: 30px;
        box-shadow: 0 0 15px rgba(34, 197, 94, 0.15);
    }

    .badge-status::before {
        content: '';
        display: inline-block;
        width: 8px;
        height: 8px;
        background-color: var(--accent-green);
        border-radius: 50%;
        margin-right: 8px;
        box-shadow: 0 0 8px var(--accent-green);
        animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
        0% { transform: scale(1); opacity: 1; }
        50% { transform: scale(1.3); opacity: 0.5; }
        100% { transform: scale(1); opacity: 1; }
    }

    /* Seção do Simulador Interativo */
    .simulator-section {
        background: rgba(0, 0, 0, 0.2);
        border: 1px solid var(--card-border);
        border-radius: 16px;
        padding: 25px;
        margin: 30px 0;
        position: relative;
    }

    .sim-title {
        font-size: 0.95rem;
        color: var(--accent-cyan);
        text-transform: uppercase;
        letter-spacing: 1.5px;
        margin-bottom: 20px;
        font-weight: bold;
    }

    .network-grid {
        display: flex;
        justify-content: space-between;
        align-items: center;
        position: relative;
        height: 200px;
        padding: 0 40px;
    }

    /* Linhas de conexão */
    .cable {
        position: absolute;
        height: 2px;
        background: rgba(255, 255, 255, 0.1);
        z-index: 1;
        transition: background 0.3s;
    }

    .cable-pc0 { width: 35%; left: 10%; top: 25%; transform: rotate(20deg); transform-origin: left; }
    .cable-pc1 { width: 32%; left: 10%; top: 50%; }
    .cable-pc2 { width: 35%; left: 10%; top: 75%; transform: rotate(-20deg); transform-origin: left; }
    .cable-srv { width: 38%; right: 10%; top: 50%; }

    /* Animação do Pacote de Rede */
    .packet {
        position: absolute;
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: var(--accent-cyan);
        box-shadow: 0 0 10px var(--accent-cyan);
        z-index: 5;
        display: none;
    }

    .device {
        display: flex;
        flex-direction: column;
        align-items: center;
        z-index: 2;
        cursor: pointer;
        transition: transform 0.2s;
    }

    .device:hover {
        transform: scale(1.1);
    }

    .device-icon {
        width: 50px;
        height: 50px;
        border-radius: 12px;
        background: rgba(255, 255, 255, 0.05);
        border: 1px solid var(--card-border);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.5rem;
        margin-bottom: 8px;
        transition: all 0.3s;
    }

    .device:hover .device-icon {
        box-shadow: 0 0 15px rgba(255, 255, 255, 0.1);
        background: rgba(255, 255, 255, 0.1);
    }

    .clients-stack {
        display: flex;
        flex-direction: column;
        gap: 25px;
    }

    /* Estilizações específicas dos equipamentos */
    .switch-device .device-icon {
        width: 65px;
        height: 45px;
        background: rgba(15, 23, 42, 0.8);
        border-color: var(--accent-purple);
        color: var(--accent-purple);
    }

    .switch-device:hover .device-icon {
        box-shadow: 0 0 20px rgba(168, 85, 247, 0.3);
        background: rgba(168, 85, 247, 0.1);
    }

    .server-device .device-icon {
        width: 55px;
        height: 65px;
        background: rgba(2, 132, 199, 0.1);
        border-color: var(--accent-cyan);
        color: var(--accent-cyan);
    }

    .server-device:hover .device-icon {
        box-shadow: 0 0 20px rgba(6, 182, 212, 0.4);
        background: rgba(6, 182, 212, 0.15);
    }

    .device-label {
        font-size: 0.75rem;
        font-weight: bold;
        color: #cbd5e1;
    }

    .device-ip {
        font-size: 0.65rem;
        color: #64748b;
    }

    /* Terminal de logs */
    .terminal-console {
        background: #020617;
        border: 1px solid rgba(255, 255, 255, 0.05);
        border-radius: 12px;
        padding: 15px;
        font-family: 'Courier New', Courier, monospace;
        font-size: 0.8rem;
        text-align: left;
        color: #38bdf8;
        max-height: 120px;
        overflow-y: auto;
        margin-top: 15px;
        box-shadow: inset 0 2px 8px rgba(0,0,0,0.8);
    }

    .terminal-line {
        margin-bottom: 4px;
        line-height: 1.4;
    }

    .terminal-line.success { color: #4ade80; }
    .terminal-line.info { color: #a78bfa; }

    /* Grid dos Integrantes */
    .team-section {
        margin-top: 35px;
    }

    .team-title {
        font-size: 1.1rem;
        font-weight: 700;
        color: #e2e8f0;
        margin-bottom: 15px;
        letter-spacing: 0.5px;
    }

    .team-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 15px;
    }

    .member-card {
        background: var(--card-bg);
        border: 1px solid var(--card-border);
        border-radius: 14px;
        padding: 15px;
        transition: all 0.3s ease;
    }

    .member-card:hover {
        transform: translateY(-4px);
        background: rgba(255, 255, 255, 0.05);
        border-color: var(--accent-purple);
        box-shadow: 0 10px 20px rgba(168, 85, 247, 0.1);
    }

    .member-role {
        font-size: 0.75rem;
        text-transform: uppercase;
        letter-spacing: 1px;
        color: var(--accent-pink);
        margin-bottom: 4px;
        font-weight: bold;
    }

    .member-name {
        font-size: 0.95rem;
        font-weight: 600;
        color: #f8fafc;
    }

    footer {
        margin-top: 30px;
        font-size: 0.75rem;
        color: #475569;
        border-top: 1px solid rgba(255, 255, 255, 0.05);
        padding-top: 20px;
    }

    @media (max-width: 600px) {
        .team-grid {
            grid-template-columns: 1fr;
        }
        .network-grid {
            padding: 0 10px;
        }
        .cable {
            display: none; /* Esconde linhas em telas muito pequenas */
        }
    }
</style>


<div class="container">
    <header>
        <h1>🌐 LanSphere</h1>
        <h3>IFMA — Campus Itapecuru-Mirim</h3>
        <div class="badge-status">Serviço HTTP Ativo na Porta 80</div>
    </header>

    <!-- Seção do simulador interativo -->
    <div class="simulator-section">
        <div class="sim-title">⚡ Simulador de Conectividade Local</div>
        
        <div class="network-grid">
            <!-- Cabos Virtuais -->
            <div class="cable cable-pc0" id="cable-pc0"></div>
            <div class="cable cable-pc1" id="cable-pc1"></div>
            <div class="cable cable-pc2" id="cable-pc2"></div>
            <div class="cable cable-srv" id="cable-srv"></div>

            <!-- Pacote físico animado -->
            <div class="packet" id="packet"></div>

            <!-- Clientes -->
            <div class="clients-stack">
                <div class="device" onclick="triggerPing('PC0', '192.168.10.10', 0)">
                    <div class="device-icon">💻</div>
                    <span class="device-label">PC0</span>
                    <span class="device-ip">192.168.10.10</span>
                </div>
                <div class="device" onclick="triggerPing('PC1', '192.168.10.11', 1)">
                    <div class="device-icon">💻</div>
                    <span class="device-label">PC1</span>
                    <span class="device-ip">192.168.10.11</span>
                </div>
                <div class="device" onclick="triggerPing('PC2', '192.168.10.12', 2)">
                    <div class="device-icon">💻</div>
                    <span class="device-label">PC2</span>
                    <span class="device-ip">192.168.10.12</span>
                </div>
            </div>

            <!-- Switch Central -->
            <div class="device switch-device">
                <div class="device-icon" id="switch-icon">🎛️</div>
                <span class="device-label">Catalyst 2960</span>
                <span class="device-ip">Camada 2 (MAC)</span>
            </div>

            <!-- Servidor -->
            <div class="device server-device" onclick="triggerServerClick()">
                <div class="device-icon" id="server-icon">🖥️</div>
                <span class="device-label">Servidor0</span>
                <span class="device-ip">192.168.10.100</span>
            </div>
        </div>

        <!-- Terminal Console -->
        <div class="terminal-console" id="console">
            <div class="terminal-line info">Consoles de Diagnósticos prontos. Clique em um PC para disparar um 'ping'.</div>
        </div>
    </div>

    <!-- Seção dos Integrantes -->
    <div class="team-section">
        <h4 class="team-title">👥 Equipe Acadêmica 01</h4>
        <div class="team-grid">
            <div class="member-card">
                <div class="member-role">Facilitador</div>
                <div class="member-name">Fernando Brandão</div>
            </div>
            <div class="member-card">
                <div class="member-role">Relatora & Git</div>
                <div class="member-name">Beatriz Campelo</div>
            </div>
            <div class="member-card">
                <div class="member-role">Revisora Técnica</div>
                <div class="member-name">Elizana de Sousa</div>
            </div>
        </div>
    </div>

    <footer>
        Infraestrutura de Rede Local Isolada — Trabalho Prático de Engenharia de Redes (D0)
    </footer>
</div>

<script>
    const consoleEl = document.getElementById('console');
    const packet = document.getElementById('packet');
    const switchIcon = document.getElementById('switch-icon');
    const serverIcon = document.getElementById('server-icon');

    function addLog(text, type = '') {
        const line = document.createElement('div');
        line.className = `terminal-line ${type}`;
        line.innerText = `> ${text}`;
        consoleEl.appendChild(line);
        consoleEl.scrollTop = consoleEl.scrollHeight;
    }

    let isAnimating = false;

    function triggerPing(pcName, pcIp, pcIndex) {
        if (isAnimating) return;
        isAnimating = true;

        // Limpa o console
        consoleEl.innerHTML = '';
        addLog(`Iniciando fluxo de diagnóstico partindo do host ${pcName}...`, 'info');
        addLog(`Verificando algoritmo do Host local: destino '192.168.10.100' está na mesma sub-rede /24.`, 'info');
        addLog(`Procurando cache ARP... MAC do Servidor0 não encontrado. Enviando ARP Request em Broadcast!`);

        // Coordenadas para a simulação física do pacote
        const grid = document.querySelector('.network-grid').getBoundingClientRect();
        const devices = document.querySelectorAll('.device');
        const pcRect = devices[pcIndex].getBoundingClientRect();
        const swRect = document.querySelector('.switch-device').getBoundingClientRect();
        const srvRect = document.querySelector('.server-device').getBoundingClientRect();

        // Posições relativas
        const startX = pcRect.left - grid.left + pcRect.width/2;
        const startY = pcRect.top - grid.top + pcRect.height/2;
        const swX = swRect.left - grid.left + swRect.width/2;
        const swY = swRect.top - grid.top + swRect.height/2;
        const srvX = srvRect.left - grid.left + srvRect.width/2;
        const srvY = srvRect.top - grid.top + srvRect.height/2;

        // Configuração física do pacote
        packet.style.left = `${startX}px`;
        packet.style.top = `${startY}px`;
        packet.style.display = 'block';

        // Etapa 1: PC -> Switch (ARP Request / Broadcast)
        setTimeout(() => {
            packet.style.transition = 'all 0.6s cubic-bezier(0.25, 1, 0.5, 1)';
            packet.style.left = `${swX}px`;
            packet.style.top = `${swY}px`;
            
            // Ativa iluminação do cabo correspondente
            document.getElementById(`cable-pc${pcIndex}`).style.background = 'var(--accent-purple)';
        }, 100);

        // Etapa 2: No Switch (Comutação inteligente e envio para o servidor)
        setTimeout(() => {
            addLog(`Switch Catalyst 2960 recebeu Broadcast. Aprendendo porta Fa0/${pcIndex+1} associada ao PC.`);
            addLog(`Switch replica o pacote ARP Request para o Servidor0 na porta dedicada Fa0/24.`, 'info');
            
            packet.style.left = `${srvX}px`;
            packet.style.top = `${srvY}px`;
            document.getElementById('cable-srv').style.background = 'var(--accent-cyan)';
        }, 800);

        // Etapa 3: No Servidor (Resposta ARP Reply e Processamento HTTP)
        setTimeout(() => {
            serverIcon.style.textShadow = '0 0 20px var(--accent-cyan)';
            addLog(`Servidor0 recebeu ARP Request e salvou o endereço IP do ${pcName} em sua tabela ARP.`, 'success');
            addLog(`Servidor0 responde com ARP Reply em UNICAST contendo o endereço físico MAC: 0060.2F3A.0701.`);
            
            // Retorna o pacote para o switch
            packet.style.left = `${swX}px`;
            packet.style.top = `${swY}px`;
        }, 1600);

        // Etapa 4: Switch direciona Unicast de volta para o PC de origem
        setTimeout(() => {
            addLog(`Switch consulta tabela CAM, localiza o PC correspondente e envia o quadro diretamente para a porta Fa0/${pcIndex+1}.`, 'info');
            packet.style.left = `${startX}px`;
            packet.style.top = `${startY}px`;
        }, 2300);

        // Etapa 5: Canal estabelecido. Enviando Mensagem de Aplicação (HTTP GET)
        setTimeout(() => {
            addLog(`Sucesso ARP! O Host local obteve o MAC de destino. Disparando pacotes HTTP GET na porta 80!`, 'success');
            addLog(`[Resposta Web de Boas-Vindas obtida do Servidor0!]`, 'success');
            addLog(`Exibindo dados: index_customizado.html renderizado com sucesso no PC! 🎉`, 'success');
            
            // Desliga cabos e limpa animação
            document.getElementById(`cable-pc${pcIndex}`).style.background = '';
            document.getElementById('cable-srv').style.background = '';
            packet.style.display = 'none';
            isAnimating = false;
        }, 3000);
    }

    function triggerServerClick() {
        consoleEl.innerHTML = '';
        addLog(`Aba de Serviços do Servidor0 aberta.`, 'info');
        addLog(`HTTP Daemon rodando ativamente na porta tcp/80.`, 'success');
        addLog(`Portas HTTPS (tcp/443) escutando requisições com TLS ativado.`, 'success');
        addLog(`Hospedado localmente: index_customizado.html (Versão final de Engenharia D0 da Equipe 1)`);
    }
</script>
