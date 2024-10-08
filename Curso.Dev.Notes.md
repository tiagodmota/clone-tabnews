# Do curso.dev

## Git vs. GitHub

- Confundir **Git** com **GitHub** seria o mesmo que confundir um arquivo de vídeo (```.mp4```, p. ex.) com uma plataforma de vídeo (YouTube, p. ex.);

- O Git é um programa, o mais relevante **sistema de controle de versão** existente. Superficialmente falando, ele pode ser comparado a um **editor de vídeos** (ferramenta); e um **vídeo** a um **repositório Git** (produto feito com a ferramenta);

- Grosso modo, repositório Git é uma pasta com seu projeto e os arquivos de rastreio/salvamento de modificações do mesmo;

- Por outro lado, o GitHub é um "YouTube" de repositórios Git. Assim como uma plataforma de vídeos: **hospeda**, **distribui **e **agrega um ecossistema ao vídeo** (editor de vídeo simplificado e embutido, geração de legendas automáticas, comentários, curtidas, doações, etc., etc., etc.); o GitHub também disponibiliza recursos úteis e adicionais em volta de repositórios Git.

## Codespaces

- O codespaces é um ambiente de desenvolvimento remoto que disponibiliza uma série de ferramentas pré-instaladas e configuradas, dentre elas: Docker, NVM, NPM e Node.js;

## Noções sobre Node.js e NVM (node version manager)

### Comandos iniciais

- Listagem das versões do Node.js: `nvm ls` (ls = list);
- Instalação de uma versão do Node.js: `nvm install {versão}` (Ex.: `nvm install lts/hydrogen` ou `nvm install 18.12.0`);
- `nvm alias default {versão}` define qual versão do Node.js será usada como padrão pelo ambiente de programação atual. (Ex.: `nvm alias default lts/hydrogen` ou `nvm alias default 18.12.0`);

### Considerações

- Versões major de LTS são compatíveis com suas respectivas subversões (18.0.0 pode interoperar diretamente com o 18.20.4);

- Arquivos com o sufixo "rc" (run commands) seguem uma convenção de nomeação. Eles servem para guardar comandos de inicialização direcionados a determinado programa/utilitário;
  
  - Caso um arquivo `.nvmrc` seja criado no diretório em que o `nvm` é usado, ele detecta (porque é programado para identificar o nome padrão ".nvmrc") e executa o conteúdo;
  - A título de exemplo, colocar o nome/número da versão do Node.js dentro do arquivo permite a execução avulsa do `nvm install`, sem a necessidade de especificar o parâmetro manualmente.

## Next.js framework

- É um framework mais orquestrador do que opinativo, ao contrário do React;
- `npm` (node package manager) é um gerenciador de dependências que será usado no projeto.

## Arquivo manifesto

- Arquivos de manifesto são uma descrição de projetos e/ou módulos logicamente coesos e independentes de um projeto. Pode conter, principalmente: metadados, dependências e scripts.

- São criados a partir do comando `npm init` o arquivo `package.json` e `package-lock.json`, com todas as dependências primárias requeridas pelo projeto em questão;

- O arquivo `package-lock.json` rastreia e armazena, detalhadamente, dependências de dependências (será importante em algo chamado Continuous Integration);

- `NPM` (node packet manager) é o gerenciador de dependências para projetos Javascript que se utilizará.

## Comandos iniciais

- `npm init` -> cria os arquivos de manifesto;
- `npm install next@13.1.6` -> Instala o framework Next.js;
- `npm install react@18.2.0` -> As bibliotecas-base do React;
- `npm install react-dom@18.2.0` -> Renderizador HTML do React;
  - O `React Native` é o renderizador mobile (Android/iOS), `React Three Fiber` é o 3D, etc.

## Protocolos

- HTTP: Hypertext Transfer Protocol (arquivos que referenciam outros documentos sucessivamente);

- FTP: File Transfer Protocol (transferência de genérica de arquivos);

- SMTP: Simple Mail Transfer Protocol (transferência de mensagens de e-mail);

- Protocolo: regras que duas partes conhecem para estabelecer comunicação entre si (onde começa, onde termina, quais "espaços de preenchimento" existem, quais espaços são opcionais ou obrigatórios, etc.);

- São empilháveis;
  
  - HTTP usa regras para comunicar entre cliente e servidor;
    - Essas informações podem ser transitadas via TCP;
      - Que por sua vez usa o Internet Protocol (IP)

- Protocolos com mais verificação de perda de info como TCP geram custo;
  
  - Nem sempre compensa pagar esse custo (caso de vídeos zoom, com protocolo UDP)
  - Quem compensa a perda de frames geralmente são os humanos que estão na reunião zoom;

- No UDP, se há perda de movimento de um objeto na tela de posição A para posição B,
  ele preenche esse limbo com dataframes intermediários;
  
  - Isso não ocorre no TCP, o qual ao perceber a perda de um dado na transmissão
    negocia o re-envio dessa informação, ocasionando "travamentos" na fluidez do objeto;

## Roteamento com Nextjs

- Tudo que coloca na pasta pages do next vira rota pública;
- pages/index.js -> seusite.com/
- pages/produtos/index.js -> seusite.com/produtos

## Conceitos de Git

- Merge conflict: quando alterações de duas pessoas causam conflito na execução
  da versão de código de cada uma;
  
  - Algo como uma pessoa está codando contado que existe um bloco x de código e
    a outra pessoa deletou o bloco x
  - Aí abre-se um Merge conflict que só será resolvido por um humano;

- O Git tem o github como cópia de referencia e você tem vários clones que voce
  clonou em sua maquina

- O Git tira foto do estado dos arquivos, ou seja ,coloca identificador em
  cada um deles e guarda eles em pacotes chamado blobs (binary large object). Conjunto
  de blobs é uma foto;

- Depois, se dos arquivos que você guardou antes você só alterou alguns, o git
  vai tirar uma foto nova inteira apenas dos arquivos alterados (vai juntar apenas os
  blobs dos arquivos alterados numa nova foto)e o que ficou inalterado ele vai apontar
  para os blobs da foto anterior;

- Quando você precisa de ver as diferenças, o git joga um blob de arquivo numa versão
  x contra o blob de outro na versão y e calcula o que foi mudado sob demanda

## Estágios de arquivos no git

- Modified: uma arquivo que já tem commit e que foi modificado;

- Staged: um arquivo que você quer, só ele, que entre no palco para tirar a foto/commit
  e deixa o restante de fora (há casos assim onde você modifica vários para descobrir que resolveria o problema alterando apenas uma linha);

- git status
  
  - untracked: arquivos não rastreados que mal foram mexidos. Você alterou, ele vira modified;
  - ('modified'): não rastreado, mudanças que ainda não foram adicionadas com `git add .`
  - Staged: mudanças que aparecem como "Changes to be committed" após o `git add .`
  - commited: mudanças que aparecem como commit com hash após `git commit` e você digitar o texto do commit no arquivo do editor

- Basicamente:
  
  - **Untracked** --> qualquer alteração --> **modified** --> `git add` --> **staged** --> `git commit` --> **commited**

- Todos os arquivos acima são monitorados por git. Os que estão no .gitignore nem untracked chegam a ser;

- Build: arquivos nossos --> arquivos finais que serão consumidos pelo navegador (eles ficam na .next/)

## Git amend e git push

- `git log` --oneline
  
  - logs em uma linha, resumidos

- `git diff` calcula a diferença entre os arquivos salvos nos commits x o que você tem atualmente na sua área de trabalho

- Caracter `\n` basicamente indica o caracter newline, que basicamente
  é um caractere que indica FIM DA LINHA. Se não tem ele, para os computadores, meio que nem linha aquele trecho é.

- Por isso você consegue selecionar um pequeno espaço após cada linha
  de código. É o \n, invibilizado pelo editor para não atrapalhar sua leitura;

- `git commit --amend`: com isso você consegue pegar o arquivo staged e emendar a alteração dele com a do commit anterior;

## Sobre push e outros comandos para git online

- "On branch main
  Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)"
  
  - Isso significa que a sua branch main local está a frente da main origin (online) em 1 commit

- origin/main = na origin online, a branch main

- local/main = no rep. local, a branch main

- git push: local --> remoto/online (empurrar)

- git pull: local <-- remoto/online (puxar)

- packtage.json: metadados, scripts e dependencias;

- packtage-lock.json: toma nota das dependencias principais e dependencias das dependencias;
  
  - é exclusivamente sobre dependencias;

- Sobre o problema do git --amend:
  
  - se você faz um --amend, ele volta no tempo,
    pega a alteração do seu commit mais atual e
    mescla com o commit anterior, gerando uma NOVA
    foto, um NOVO commit;
  - com isso, o commit anterior que você tinha foi
    descartado e agora você tem um novo commit que
    não tá lá na origin/main;
  - isso gera inconsistência;
  - usando o git push --force você força o push
    e faz o origin aceitar as alterações. O mais recente
    commit do origin será substituido pelo commit mais
    recente do seu rep. local;

## Client x Server

- Cliente é quem requisita, servidor é quem supre um serviço;

- Um ator não é limitado apenas a ser só server ou só client, ele pode assumir papéis diferentes dependendo da relação;

- Comunicação é feita por protocolos;

- Deploy: depositar arquivos nos servidores que vão fornecer serviço;

- Hoje:
  
  - Máquina local --> C.I. (Continuous Integrator) --> Build --> Produção;
  - C.I. = contém testes automatizados;
  - Build = ocorre numa máquina que vai criar a versão final de código que rodará na internet;
  - Produção: ...produção!

## Mais deploys

- Minimal Privilege Principle: principio do menor priilégio;
  
  - Libera o básico de acessos e depoise xpanda conforme necessidade;

- Deploys na vercel sempre ficam com url identificando eles;
  
  - branchs tem url unica;
  - commits tem url unica;

- Isso permite você, em casos de problemas com atualizações, voltar para um deploy que deu certo e apontar o dominio oficial publico da vercel para esse deploy funcional;

## Muralhas

- Muralha de tecnologia x Muralha de negócio;

## Orgânico x Impressora 3D

- Over Engineering: complicar demais implementação de funcionalidade que poderia ter sido mais simples;
- Feature Creep: tanta feature que mais atrapalha do que ajuda na UX;

## Moral x Prática

- Não dá para mudar os resultados passados, mas escolha ser você quem determina a interpretação desses resultados e o que vai fazer no futuro;
  - Não aumente as dores da realidade; bola para frente.

## Como organizar tarefas

- Conceito relevante: `saldo positivo x saldo negativo`
  
  - Fazer mais com que menos;
  - Qualquer tarefa que abale esse senso natural de saldo na sua mente se torna cansativa;
  - Ex: cenário ruim do nível 4 (sobrecarregar programador com rotinas de gestão)

- Nível 1: anotação para apenas lembrar do que precisa ser feito. Custo de energia (para produzir essa anotação) e de aquecimento (rapidez de verificação) devem ser baixíssimos. Ex: folhas de papel A4 com as tarefas;

- Nível 2: `lembrar de todas as coisas a serem feitas com tempo de aquecimento baixo, mas em grupo`. Ótimo ter checkboxes para marcar de forma parcial e total. Ex: quadro na geladeira;

- Nível 3: expandir conhecimento. Utilizar ferramentas que tem tempo de produção maior (trello, github, etc) contendo mais informações e um tempo de aquecimento maior também (demora mais para visualizar pois precisa carregar as páginas, etc);

- Nível 4: gerar métricas sobre as pessoas que estão trabalhando. Isso é muitas vezes mais útil ao gestor do que ao programador que programa (participar de reuniões, arrastar um card de jira...);
  
  - Mensurar métricas é MEIO, e não um FIM em si mesmo; Não pese as pessoas do seu time!

## Como lidar com projetos de qualquer tamanho

- Nunca negocie com terroristas. Seu cérebro engata muitas situações de tudo ou nada e o certo a se fazer sempre é optar pelo terceiro caminho: fazer aos poucos, trabalhar pouco, ganhar pouco. Apesar do mal estar que essa frase provoca, é possível se livrar disso com o tempo e a persistência;
- Issue de inception: Issue é onde você mostra problemas do projeto. A issue do inception é como se fosse uma penseira onde você descarrrega toda a ideia bagunçada que você tem na cabeça de uma forma linear num texto, analisando a origem da ideia, alicerces e se ela para em pé mesmo;
- Isso vai gerar uma pedra enorme. Você tem que quebrar ela até conseguir definir tamanhos de pedras que você vai conseguir lidar;

## Criando milestones e issues do projeto

- Por padrão, quebre as pedras o máximo possível até ficar na pedrinha em que você considere viável para implementar;

- Mecânica de dopamina:
  
  - 1º estágio - Início: cérebro identifica oportunidade e libera pequenas doses de dopamina em regiões do cérebro para você gerar movimento e ir em direção ao objetivo;
  - 2º estágio - Progresso: cérebro libera novas doses maiores à medida que o caminho tomado pelo seu movimento começa a gerar resultado. estímulo para concluir o movimento;
  - 3º estágio - Final: caso o movimento produza um resultado que é "aprovado", uma dose final e maior de dopamina é liberada e o evento mexe com as estruturas do cérebro, modelando-o;

## Configurando formatadores

- editorconfig: editor enquanto você digita;

- prettier: ajusta inclusive códigos já existentes;

- comandos:
  
  - npm i prettier -D = instala como dependencia de desenvolvimento;
  - adicione {"lint:check": "prettier --check ."} no package.json;
  - Instale a extensão do prettier e insira ele como formatador padrão do vscode;
  - Habilite o formatar ao salvar;
  - Autosave: desabilite. Isso vai ajudar para quando fazer testes automatizados.

## Resoluções de DNS

- Seu computador contata o DNS server, pega o ip referente ao endereço que você pesquisou e depois o seu pc usa esse ip para se referir diretamente ao servidor que contem os serviços que você quer utilizar;

- Domain Name System;

- Converte nome em endereço IP ("resolver");

- É como uma tabelona que anota o nome e o endereço relativo;
  
  - Um ip pode mudar, mas aí o nome continua, não impacta no domínio;

- Você faz a requsiição primeiramente para um recursive server;
  
  - Esse recursive server vai pedir para um root server (um dos servidores dns poderosos lá) se ele sabe qual é o ip referente àquele domínio;

- tabnews.com.br.
  
  - "termina" com ponto. O root server vai ler de trás para frente;
  - "." indica o root server;
  - ".br" é o TLD, Top Level Domain. E o root server sabe qual é a lista dos servidores que são dos TLD. Os roots servers sabem quais os ips dos servidores dos TLD;
    - ccTLDs = country code tld domains - para países, .br, .pt, etc
    - gTLDs = generic TLDs como o .com, .org, .dev, .bradesco
  - Depois disso, então, o computador vai pergar a lista de nomes dos tlds devolvida pelo root server e perguntar onde está o dominio tabnews.com.br;
    - Esse TLD só retorna onde está o Authoritative Server,o que tem as informações, registros do seu domínio tabnews.com.br
    - Dentro desse pacotinho de informações está o ip do servidor da sua aplicação;
    - Ele devolve esse ip para seu computador usar na requisição para o servidor final;
  - Para agilizar as requisições futuras, pode ser utilizado cache em cada um desses servidores que foram consultados;

## Registrando um domínio próprio

- Para registrar um dominio você tem que ir atrás de um registor
  (registrador, como registro.br, uolhost, hostgator, locaweb...);
- É como se eles fossem vivo, claro, tim... e você pode migrar entre
  registradores também;
- NIC.br = Nucleo de Informação e Controle do .br - denominado "Registry" ou "Registro" no schema do Deschamps
  - Ele que tem todos os endereços .br possiveis disponiveis
  - Ele é consultado pelo registro.br na hora que você coloca o dominio que vc quer la
  - E retorna se tá disponivel ou não;
  - Se estiver disponivel, aí o seu registrador (hostgator, locaweb, registro.br)
    passa as info para o Registry e o Registry insere esse registro na lista de TLDs consultaveis apontando para o seu Authoritative Server
- A compra de um dominio passa pela escolha do dominio, cadastro simples, confirmação de usuário e pagamento.
- Uma vez que o domínio foi pago, você precisa de um servidor authoritativo, que vai transmitir isso para o Registor, que
  vai passar isso para o Registry (NIC.br) que vai atualizar o TLD com seu endereço e assim, os novos fluxos vindo do
  root server irão encontrar seu site
- O que faremos agora é
  - Ir no servidor dns da vercel
  - Colocar nosso domínio lá
  - E fazer com que o registro.br aponte para o nosso domínio no server autoritativo da vercel
  - Isso fará com que o Registry pegue essa informação e propague para o TLD, de forma que novas solicitações vindas
    do root server serão lançadas direto para nosso server autoritativo (o server dns da vercel que contem nosso dominio
    cooppplatform.com.br)
- Para fazer com que o server da vercel seja o nosso authoritativo, você vai em domain > add > insere o repo do projeto >
  insere o domínio comprado no registro.br > finaliza
- Inicialmente a vercel irá pensar que temos um server authoritativo externo e estamos tentando fazer com que ela aponte para esse server externo. Mas nós queremos que a vercel seja o authoritativo. Logo, basta ir na aba nameservers > add > aparece os dois endereços de server DNS:
  - ns1.vercel-dns.com
  - ns2.vercel-dns.com
- Esses serão os dois servers dns da vercel que vão responder pelo domínio;
- Vá no registro.br, entre no seu dominio clicando no nome dele > vá para dns > cole os dois endereços de server dns que apontei acima
- Lembrete: o server authoritativo não armazena o site, ele APONTA para o ip do server que armazena o site
- O Nome real do Authoritative Server é Authoritative Nameserver
- para instalar pacote com comando dig: `sudo apt install dnsutils`
- comando: `dig nomedoseudominio.com.br A`
  - Com isso você tá buscando o IP do server que guarda seu site
  - No caso, vai aparecer dois ips na mesma faixa, demonstrando os dois servidores da vercel mais proximos de você para entregarem os dados do site
- Os records são registros no server authoritativo;
  - `dig coopplatform.com.br TXT +trace`
    - Nesse exemplo buscamos o conteudo do record TXT e pedimos para mostrar todo o caminho tomado até chegar no server authoritativo

## MacDonald's Theory

- Sugira algo bizarro apenas para quebrar o gelo e subir sugestões do pessoal;
- E aos poucos será definido:
  - O que fazer => área para notícias e conteúdos agro para o público;
  - O que proteger => relevância de conteúdos para o público;
  - O que repetir para as novas pessoas que chegarem dentro do seu projeto => produza conteúdo relevante que você terá espaço para fazer propaganda do seu produto!!

## Não confie em 100% uptime

- Comprometimento de 99,9% de uptime;
- Equivale a 44min. por mês;
- Isso é combinado no SLA nos termos de serviço quando vc acessa a plataforma;
- Quanto mais complexo o serviço, mais difícil determinar o que é "ficar fora" ou "downtime";
- Status pages;
  - Pesquise `termo + status` no google;
  - aws status;
  - vercel status;
- Mas não confie nem no status da página de status;

## PoC x MVP

- Proof of Concept;
- Minimal Valuable Product;
- Primeiro você faz várias provas de conceito baratas (versões de página, por exemplo);
- Depois você vai fazer o MVP para fazer o produto completo mínimo bem feito de forma que o mínimo já seja a solução sem ruídos entre o cliente e sua aplicação;
- 
