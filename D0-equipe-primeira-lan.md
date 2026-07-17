🏥 Projeto de Conectividade — Hospital Regional Vale do Itapecuru

1. Identificação do Projeto

Nome do Projeto: Rede Médica Integrada — Hospital Regional Vale do Itapecuru (MedConnect)

Responsável Técnico: Equipe de Infraestrutura de TI & Engenharia Clínica

Data de Criação: 17 de Julho de 2026

Status: Planejamento

2. O Problema

📌 Contexto e Desafio Atual

O Hospital Regional Vale do Itapecuru possui três pavilhões principais isolados a uma distância de até $800 \text{ metros}$ entre si: Administração (CPD), Pronto-Socorro (Triagem) e Farmácia Central / Almoxarifado. Atualmente, apenas o pavilhão administrativo possui acesso ativo à internet e ao banco de dados do Sistema de Prontuário Eletrônico do Paciente (PEP).

As outras duas unidades operam de forma offline, gerando graves riscos à saúde e gargalos operacionais:

[!CAUTION]
Atraso Crítico no Pronto-Socorro: Pacientes graves triados na emergência não têm seu histórico médico ou de alergias consultados em tempo real, dependendo de fichas físicas que demoram para ser localizadas.

[!WARNING]
Desabastecimento e Erro de Estoque: A farmácia registra a entrega de medicamentos e insumos de forma manual no papel. A demora na sincronização ao final do dia gera furos de estoque e risco de falta de remédios controlados.

[!IMPORTANT]
Lentidão em Laudos de Imagem: Exames de Raio-X e Tomografia Computadorizada precisam ser salvos em mídias físicas (como pen-drives) e transportados a pé por enfermeiros para análise médica no Pronto-Socorro.

3. Atividades e Necessidades

Para resolver essa criticidade de vidas e o gargalo técnico, mapeamos as necessidades em tempo de tráfego de dados para cada setor:

Pavilhão Operacional

Atividade Principal

Requisito de Rede

Prioridade

Administração (CPD)

Gestão de contratos, prontuário centralizado e faturamento do SUS/Convênios.

Internet dedicada de alta velocidade e controle de segurança de rede interna.

Alta

Pronto-Socorro (Triagem)

Triagem rápida de emergência, consulta rápida ao PEP e visualização de exames PACS.

Latência baixíssima ($< 5 \text{ ms}$) e largura de banda Gigabit para imagens médicas pesadas.

Crítica

Farmácia Central

Baixa imediata de medicamentos controlados e requisição de reposição de estoque.

Acesso persistente e seguro ao banco de dados do Almoxarifado central.

Alta

4. Solução Proposta

⚡ Arquitetura de Conectividade Gigabit PtP

A solução consiste em estender a rede local (LAN) do CPD Administrativo utilizando links de rádio sem fio ponto-a-ponto de alta frequência de nova geração ($60 \text{ GHz}$ com antenas direcionais Ubiquiti GigaBeam).

[!TIP]
Por que links de $60 \text{ GHz}$?
Ao contrário do Wi-Fi convencional de $2.4 \text{ GHz}$ ou $5 \text{ GHz}$, a frequência de $60 \text{ GHz}$ oferece throughput Gigabit real sem interferências com outros equipamentos médicos do hospital, eliminando a necessidade de obras civis complexas para passar cabos subterrâneos entre os pátios pavimentados dos pavilhões.

       [ Pavilhão Admin (CPD) ] 
               (Switch)
                  │
        [ Antena Base (60GHz) ] 
           )       (  <- Enlace Gigabit (Sem Fio)
          )         (
 [ Antena Emergência ]     [ Antena Farmácia ]
           │                        │
    [ Switch Local ]         [ Switch Local ]
           │                        │
     (PEP & Triagem)          (PC Dispensação)


🛠️ Hardware Proposto para os Blocos Isolados

Antenas de Micro-ondas: 2 pares de antenas externas Gigabit de $60 \text{ GHz}$ para alcance de até $1 \text{ km}$ com alta tolerância a intempéries.

Switches PoE de Acesso: 2 Switches gerenciáveis de 8 portas Gigabit Ethernet compatíveis com PoE+ para alimentar as antenas e os telefones IP dos setores diretamente pelo cabo de rede.

Nobreaks Semi-Senoidais: Nobreaks dedicados para manter os racks de comunicações ativos por até 2 horas em caso de quedas de energia no gerador hospitalar.

5. Próximas Etapas

[ ] Realizar teste físico de visada direta (Site Survey) entre as coberturas dos três pavilhões.

[ ] Mapear as sub-redes dedicadas para os pacientes e para o tráfego restrito de dados médicos (VLANs).

[ ] Validar a segurança lógica e criptografia no tráfego das antenas ponto-a-ponto.

[ ] Simular a topologia no Cisco Packet Tracer para validação dos fluxos de pacotes antes das compras de hardware.

Documento elaborado pelo Time de Infraestrutura para a disciplina de Redes de Computadores do IFMA.