 Trilha Guiada — Entrega D0: Projeto Inicial de Rede Local (LanSphere)

Identificação do Projeto

Campo

Resposta da Equipe

Nome da equipe

Equipe 01 - Infraestrutura de Redes

Integrantes

Beatriz Campelo, Elizana de Sousa, Fernando Brandão

Turma

Técnico em Informática (Subsequente / Integrado)

Nome do projeto

LanSphere - Infraestrutura de Rede Local Isolada com Servidor de Serviços Local

Data

16/07/2026

1. Missão

Nesta entrega, a Equipe 01 consolidou a primeira hipótese documentada da rede física e lógica, resolvendo o problema de instabilidade de acesso prático no laboratório e provando o fluxo fim-a-fim de dados em um ambiente local isolado e estável.

2. Papéis e Organização do Grupo

Papel

Responsabilidade

Integrante

Facilitador

Controla o tempo e mantém a equipe focada nas etapas técnicas.

Fernando Brandão

Relator

Registra as respostas de rede e configurações lógicas.

Beatriz Campelo

Diagramador

Desenha a topologia lógica e física no simulador/documento.

Elizana de Sousa

Revisor Técnico

Confere a coerência de endereçamento IP e máscaras de sub-rede.

Elizana de Sousa

Parte A — Compreensão do Problema

5. O Problema

No contexto do Laboratório de Informática do IFMA Campus Itapecuru-Mirim, os estudantes do técnico em informática precisam de acesso rápido e estável a recursos didáticos de desenvolvimento Web e simulações cliente-servidor, mas a falta de uma infraestrutura física estruturada e de um plano lógico de sub-rede centralizado gerava isolamento das máquinas e lentidão nas dinâmicas de ensino, o que prejudicava a execução das aulas práticas de redes, gerando atraso nas entregas e limitação do aprendizado experimental.

6. Identificação dos Usuários

Grupo de usuários

Quantidade estimada

O que precisa fazer na rede

Prioridade

Estudantes Técnicos

$30$ por turma

Realizar testes de conectividade, simular envio de pacotes e navegar em páginas acadêmicas locais.

Alta

Professores / Docentes

$2$ por turma

Disponibilizar arquivos de páginas Web de aula e auditar o tráfego dos alunos.

Alta

Administrador de TI

$1$ profissional

Configurar portas do switch, monitorar integridade física do cabeamento e gerenciar IPs estáticos.

Média

Quem administrará ou manterá a rede?

A rede será administrada pela equipe técnica de TI do laboratório do IFMA em parceria didática com os próprios estudantes sob supervisão direta do professor orientador.

7. Identificação dos Setores ou Ambientes

Setor ou ambiente

Usuários atendidos

Dispositivos previstos

Needs principais

Área das Estações (Lab)

Estudantes Técnicos

$3$ PCs de simulação

Resolução rápida de nomes, baixa latência física e sem conflitos de IP na placa de rede.

Armário Rack (CPD Local)

Administrador de TI

$1$ Switch Catalyst 2960

Comutação de quadros na velocidade Gigabit/FastEthernet, organização visual dos cabos e prevenção de loops.

Área do Servidor

Estudantes e Professores

$1$ Servidor Web físico

Disponibilidade ininterrupta de serviços HTTP na porta $80$ para as estações clientes.

8. Necessidades e Serviços

Usuário ou setor

Necessidade

Serviço relacionado

Importância

Como saberemos que funciona?

Estudante / PC

Testar se as placas de rede estão se comunicando logicamente.

Diagnóstico ICMP (Ping)

Alta

Ao rodar o comando ping e receber $4$ respostas de volta com $0\%$ de perda de pacotes.

Estudante / PC

Acessar a aplicação de estudos no servidor remoto local.

Serviço Web HTTP (Porta $80$)

Alta

Renderização instantânea do código index_customizado.html no navegador do cliente.

Administrador / Rede

Interconectar os dispositivos sem colisões físicas e elétricas.

Comutação de Camada 2 (Switching)

Alta

Ao observar os link lights verdes no simulador e a tabela ARP contendo as associações MAC corretas.

Parte B — Da Necessidade à Proposta

9. Seleção de Recursos e Justificativa

Recurso

Quantidade inicial

Necessidade atendida

Justificativa

Dúvida ou premissa

Switch Cisco 2960

$1$ un.

Interconexão geral

Equipamento inteligente de Camada 2 que previne colisões na LAN.

Não necessita de IP ativo nas portas para comutar quadros locais.

Servidor Web (Server0)

$1$ un.

Hospedagem HTTP

Armazena o portal escolar e simula solicitações cliente-servidor de forma direta.

IP estático fixado em $192.168.10.100$ por convenção técnica.

Computadores (PCs)

$3$ un.

Estações do usuário

Permitem aos alunos disparar pings e navegar no browser da simulação.

Configuradas estaticamente na mesma sub-rede lógica /24.

Cabos de Cobre Diretos

$4$ un.

Enlace físico de cobre

Transportam os dados brutos em conexões FastEthernet de até $100 \text{ Mbps}$.

Distância curta, limitando-se ao laboratório físico (menos de $100 \text{ m}$).

Conferência de Capacidade

Quantas conexões cabeadas são necessárias inicialmente?
$4$ conexões físicas necessárias ($3$ PCs clientes + $1$ Servidor).

Quantas portas deverão ficar livres para expansão?
Como o switch Catalyst 2960 possui $24$ portas FastEthernet, teremos $20$ portas livres para novos computadores.

A quantidade de portas dos switches propostos é suficiente?
Sim, é amplamente suficiente. A conta matemática prova que:


$$4 \text{ portas em uso} < 24 \text{ portas disponíveis}$$

Quais usuários necessitam de Wi-Fi?
Para esta etapa inicial de infraestrutura isolada (D0), a conectividade sem fio (Wi-Fi) foi deixada fora de escopo para priorizar a estabilidade do cabeamento.

10. Registro de Premissas e Perguntas em Aberto

Tipo

Premissa ou pergunta

Por que importa?

Como será confirmada?

Premissa

O Gateway Padrão deve permanecer vazio ou $0.0.0.0$.

Prova que hosts na mesma sub-rede lógica se comunicam sem roteador usando ARP na Camada 2.

Disparando ping de $192.168.10.10$ para $192.168.10.100$ com sucesso.

Pergunta

Vamos implantar serviço DHCP na próxima entrega (D1)?

Evita configurações manuais de IP caso o laboratório ganhe mais computadores.

Validação com o professor orientador no início da próxima aula técnica.

Pergunta

Faremos uso de servidor DNS para resolução de nomes?

Permitirá digitar http://lansphere.ifma/ no navegador ao invés de memorizar o IP de destino.

Análise das expansões bônus do cronograma da disciplina.

Parte C — Topologia Inicial

11. Topologia da Rede (LanSphere)

A rede física está desenhada em uma topologia em estrela centralizada, onde todas as estações de usuários e o servidor terminam suas conexões físicas nas interfaces de acesso do switch central de comutação.

flowchart TD
    subgraph LAN_Isolada_LanSphere [Sub-rede Lógica: 192.168.10.0/24]
        SW["Switch Cisco Catalyst 2960"]
        
        PC0["PC0 Estação de Usuário<br>IP: 192.168.10.10"]
        PC1["PC1 Estação de Usuário<br>IP: 192.168.10.11"]
        PC2["PC2 Estação de Usuário<br>IP: 192.168.10.12"]
        SRV0["Servidor0 HTTP Web<br>IP: 192.168.10.100"]
        
        SW ---|FastEthernet 0/1| PC0
        SW ---|FastEthernet 0/2| PC1
        SW ---|FastEthernet 0/3| PC2
        SW ---|FastEthernet 0/24| SRV0
    end


Leitura da Topologia

Por onde o tráfego entra e sai da rede?
Como é uma rede local puramente isolada de simulação acadêmica, o tráfego não sai da LAN. Todo tráfego entra e sai estritamente através das placas de rede FastEthernet dos próprios computadores locais.

Qual é o ponto central das conexões cabeadas?
O Switch Cisco Catalyst 2960.

Onde o servidor está conectado?
O servidor está conectado diretamente à porta dedicada FastEthernet 0/24 do switch central.

Como os dispositivos sem fio entram na LAN?
Para a rede isolada LanSphere atual, não existem dispositivos sem fio conectados. Todo acesso é feito por meio de cabeamento estruturado direto de cobre.

12. Checklist Técnico da Topologia

[x] Todo equipamento listado aparece no desenho e na lista de recursos.

[x] Os cabos estão conectados diretamente de ponto a ponto sem "flutuar".

[x] O switch atua como o concentrador físico central da topologia em estrela.

[x] O servidor está conectado diretamente ao switch de comutação.

[x] Não foram configurados gateways padrões, uma vez que a sub-rede $192.168.10.0/24$ é local e isolada.

Parte E — Revisão e Entrega

18. Registro de Uso de Inteligência Artificial

A equipe utilizou ferramentas de IA de forma ética e assistida exclusivamente para auditar o comportamento teórico de barreira lógica do gateway $0.0.0.0$ e na estruturação visual das tabelas técnicas de requisitos.

Campo

Resposta

Ferramenta utilizada

Gemini 1.5 Pro & ChatGPT-4o

Prompt utilizado

"Atue como um especialista de redes Cisco. Revise as conexões físicas para uma topologia com 3 PCs, 1 Switch 2960 e 1 Servidor HTTP. O que acontece se deixarmos o Default Gateway em branco em uma rede isolada? Há perda de ping local?"

Sugestões aceitas

Validação conceitual de que o switch não precisa de IP configurado na placa de gerenciamento para que os quadros naveguem na mesma rede.

Sugestões rejeitadas

Instalação e uso de DHCP/DNS de forma precoce, optando-se por manter a rede estática e previsível na entrega D0.

Como verificamos

Através de discussões técnicas internas no grupo e comparando as respostas lógicas dadas com os slides teóricos das aulas do IFMA.

19. Justificativa da Proposta

A proposta apresentada pela Equipe 01 atende de forma cirúrgica ao problema de acesso local do laboratório de informática do IFMA Campus Itapecuru-Mirim. Ao projetarmos uma topologia em estrela baseada no Switch Catalyst 2960, eliminamos completamente o risco de colisões na transmissão de dados.

A escolha do plano estático de IPs $192.168.10.0/24$ garante que todas as máquinas permaneçam na mesma vizinhança lógica, de modo que a comunicação seja direta utilizando o protocolo ARP na Camada 2, sem depender de roteamento ou gateways.

Por fim, a hospedagem da nossa página institucional index_customizado.html na porta $80$ do Servidor0 simula com realismo e de maneira segura uma aplicação cliente-servidor real. Essa arquitetura serve de alicerce para futuros estudos que envolvam segmentação lógica de VLANs, roteamento estático/dinâmico e segurança com Firewalls nas próximas aulas práticas de Redes de Computadores.

Declaração de Autoria do Grupo

Declaramos que esta entrega técnica D0 reflete o aprendizado da Equipe 01 durante as aulas práticas de laboratório, com configurações executadas manualmente no simulador de redes e arquivos versionados no repositório GitHub.

Integrantes:

Beatriz Campelo

Elizana de Sousa

Fernando Brandão

IFMA Campus Itapecuru-Mirim, 17 de Julho de 2026.