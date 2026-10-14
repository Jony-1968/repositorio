# repositorio
criar repositorio
O tema e o objetivo, na frase que você escreveu no começo;
R: Quero aprender sobre Unicloud  da Unitronics  básico de uma forma simples e clara. Para quem nunca teve contato com Unicloud.
As fontes que entraram, e por que você confia nelas;
https://www.youtube.com/watch?v=3DItWqcJjbE
https://www.youtube.com/watch?v=4TiwbjwDLr4
https://www.youtube.com/watch?v=pjFt5vP31nw
https://www.youtube.com/watch?v=pjFt5vP31nw

A diretriz de comportamento que você deu ao notebook;
R: Quero aprender sobre Unicloud  da Unitronics  básico de uma forma simples e clara. Para quem nunca teve contato com Unicloud.
As perguntas que você fez, o que ele respondeu e de quais fontes;
Quero aprender sobre Unicloud  da Unitronics  básico de uma forma simples e clara. Para quem nunca teve contato com Unicloud.
O UniCloud da Unitronics é uma plataforma de nuvem e IIoT (Internet das Coisas Industrial) do tipo no-code (sem necessidade de programação web ou conhecimento prévio em nuvem), desenvolvida para fabricantes de máquinas e integradores industriais
. Ela permite coletar dados de PLCs, monitorar operações em tempo real, criar painéis visuais interativos e realizar acesso remoto seguro
.
1. Conceitos Fundamentais
Para entender o UniCloud do zero, é importante conhecer quatro termos básicos:
Organização (Organization): É a conta da empresa na nuvem que gerencia todo o sistema, incluindo os usuários, permissões de acesso, canais e dispositivos conectados
.
Tipo de Ativo (Asset Type): É o "molde" ou modelo da aplicação. Nele você define a estrutura de dados, ou seja, quais variáveis (tags) e alarmes do PLC serão transmitidos para a nuvem
.
Ativo (Asset): É a máquina física ou o PLC real instalado em campo rodando determinado Asset Type, identificado e validado pelo seu número de série individual
.
Dashboards (Painéis): São as telas visuais personalizadas construídas com elementos do tipo arrastar-e-soltar (widgets como medidores, gráficos, tabelas e mapas) para acompanhar o desempenho da máquina em tempo real
.
2. Como os Controladores se Conectam
A forma de conexão varia conforme a família do controlador Unitronics:
Linha UniStream: Possui suporte nativo ao protocolo MQTT e conecta-se diretamente à nuvem via Ethernet, Wi-Fi ou rede celular, precisando apenas de conexão com a internet e configuração de servidor DNS (sem necessidade de roteador externo)
.
Linhas Vision, Samba e Jazz / Dispositivos Modbus de Terceiros: Como não possuem suporte nativo ao protocolo MQTT, necessitam de um roteador Unitronics (UCR) intermediário para atuar como gateway de comunicação com a nuvem
.
3. Principais Recursos e Vantagens
Plataforma No-Code: Não exige escrita de códigos HTML ou JavaScript para construir painéis visuais e relatórios de telemetria
.
Acesso Remoto Seguro: Permite realizar manutenção remota, atualização de firmware, modificação de programa e controle de tela via VNC, Web Server ou túnel VPN
.
Segurança Robusta: A comunicação entre o PLC e a nuvem utiliza o protocolo seguro MQTT protegido por certificados digitais
.
Sincronização Automática de Tags: Após a configuração inicial, se você adicionar ou alterar tags do Asset Type, o UniCloud sincroniza os dados automaticamente em segundo plano, sem necessidade de refazer o download do programa no PLC
.
4. Fluxo Básico de Configuração (Passo a Passo)
O processo de colocação em funcionamento envolve três etapas principais
:
No Software de Programação (ex: UniLogic):
Configure as definições de rede no projeto (IP e servidor DNS)
.
Habilite a integração com o UniCloud e faça login na sua Organização
.
Crie o Asset Type, selecione as tags e alarmes que deseja enviar e sincronize com a nuvem (Sync Asset Type)
.
Descarregue o programa no PLC
.
No Painel do PLC (UniApps / IHM):
Ative o UniCloud no painel e carregue o certificado de segurança para autenticar o controlador
.
No Portal Web do UniCloud ([link suspeito removido]):
Cadastre a máquina criando um Asset e validando o número de série do PLC
.
Abra o editor de Dashboards, adicione os widgets desejados (gráficos, medidores, tabelas) e publique seu painel
.
O link do notebook compartilhado.
fonte 1
Webinar: Getting Started with UniCloud: the Basics using VisiLogic
fonte 2
Getting Started with UniCloud
fonte 7
Connecting UniStream to UniCloud

2 pergunta:
Como faço para configurar o Unistream no Unicloud?
A configuração do UniStream no UniCloud é realizada em quatro etapas principais, integrando o software de desenvolvimento (UniLogic), o portal web do UniCloud e o painel do controlador (UniApps)
.
1. Configuração Inicial e de Rede no UniLogic
Definição de IP e DNS: No menu do projeto, navegue até PLC Communications > Physical > Panel Ethernet
. Atribua um endereço IP ao painel e configure obrigatoriamente um servidor DNS (como o DNS público do Google: [link suspeito removido]) para permitir o acesso à internet
.
Ativação do VNC (para Acesso Remoto): Vá até VNC Server Management e selecione o modo de operação habilitado (Enabled with password) definindo uma senha segura
.
2. Habilitação da Integração e Definição do Asset Type
Habilitar o UniCloud: Na árvore do Solution Explorer, clique em UniCloud e selecione a opção para habilitar a integração
.
Autenticação: Faça login com suas credenciais da plataforma ou clique em Create Organization para cadastrar sua empresa
.
Criar o Asset Type: Clique em Create Asset Type e dê um nome ao modelo da aplicação
.
Mapeamento de Telemetria (Tags e Alarmes):
Tags: Acesse Asset Type > Tags e adicione as variáveis ou estruturas (structs) que deseja transmitir, definindo se o acesso será de apenas leitura (Read Only) ou leitura/escrita (Read/Write)
.
Alarmes: Na guia Alarms, habilite a integração e marque os alarmes do PLC que serão monitorados na nuvem
.
Acesso Remoto: Na aba Remote Access, marque a caixa Remote Access Control Enabled
.
Intervalo de Envio e Assinatura: Ajuste o campo Tags timer interval para definir a frequência de atualização dos dados
. O UniLogic calculará automaticamente a estimativa de envios mensais e indicará o plano de assinatura adequado
.
Sincronização e Download: Clique em Sync Asset Type no menu superior para enviar o modelo à nuvem e, em seguida, faça o Download completo do projeto para o PLC
.
3. Registro do Equipamento no Portal Web
Acesse o portal do UniCloud ([[link suspeito removido]](https://www.[link suspeito removido])) e vá em Device Management > Assets Management
.
Clique em Add, selecione o Asset Type criado no UniLogic e insira o Número de Série do PLC (PLC Serial) impresso no equipamento, clicando em Validate
.
Atribua um nome para a máquina (Asset Name) e salve
.
4. Ativação no Painel do Controlador (UniApps)
Acessar o UniApps: Na tela física da IHM (ou via VNC), toque e mantenha pressionado o canto superior direito do painel até abrir o menu do UniApps
.
Navegar até o UniCloud: Selecione a guia Network, avance para a página seguinte e clique no ícone UniCloud
.
Ativar o Serviço: Pressione Activate UniCloud
.
Carregar Certificado de Segurança:
Via Nuvem (Mais rápido): Selecione Load Certificate from UniCloud, insira seu e-mail e senha cadastrados no UniCloud e confirme
.
Via USB: Faça o download do arquivo de certificado (.cert) pelo portal web, salve-o em um pendrive e selecione Load Certificate from USB
.
Iniciar Transmissão: Acesse a aba Asset e clique em Start sending data
. O status de comunicação mudará para Connected, indicando que a telemetria está ativa e pronta para uso em dashboards
.
📊 Quer que eu ajude você a mapear as tags de um projeto específico ou criar um roteiro para a montagem do seu primeiro Dashboard no UniCloud?

fonte 1
Architectural Framework and Operational Value of Unitronics UniCloud in Industrial IoT Deployment
fonte 7
Webinar: Getting Started with UniCloud: the Basics with UniStream Controllers
fonte 9
Webinar: Getting Started with UniCloud: the Basics using VisiLogic


LInk:https://notebook.google.com/notebook/c07c680c-b17b-4e70-81a8-1c4fd97ec2ef
