# O que é Yarn e como funciona seu gerenciamento de pacotes

O Yarn é um gerenciador de pacotes que trouxe mais funcionalidades e vantagens para programadores. Com uma estrutura já conhecida e utilizada por ferramentas renomadas, como o NPM, essa aplicação tem se destacado por sua simplicidade e segurança.

[Ivan de Souza](https://rockcontent.com/br/blog/author/ivan/)



29 out, 20 | Leitura: 7min

![yarn](https://rockcontent.com/br/wp-content/uploads/sites/2/2020/10/yarn-1024x538.jpg)

Gerenciadores de pacotes são um recurso de extrema funcionalidade e praticidade para desenvolvedores que precisam de soluções prontas para agilizar a rotina. Entre os mais relevantes disponíveis no momento, **o Yarn se destaca para desenvolver desde softwares até infraestruturas de** [**hospedagens**](https://rockcontent.com/br/blog/hospedagem/) para sites de todos os tipos.

Desenvolver aplicações, principalmente para a web, é um trabalho que requer esforços minuciosos, com linhas extensas de códigos para descrever e ativar funções e recursos. Por vezes, há ainda chances de erros, devido ao alto volume de informações. No entanto, com o suporte de um gerenciador de pacotes qualificado, caso do Yarn, esse trabalho pode ser mais eficiente e ágil.

Neste post detalharemos mais sobre a ferramenta, como ela funciona e de que maneira pode ser útil no dia a dia de desenvolvedores. O conteúdo vai abordar os seguintes tópicos:

- [O que é Yarn?](https://rockcontent.com/br/blog/yarn/#1)
- [Como instalá-lo?](https://rockcontent.com/br/blog/yarn/#2)
- [Como funciona seu gerenciamento de pacotes?](https://rockcontent.com/br/blog/yarn/#3)
- [Quais as funcionalidades oferecidas?](https://rockcontent.com/br/blog/yarn/#4)
- [Quais as vantagens do Yarn?](https://rockcontent.com/br/blog/yarn/#4)

[Continue a leitura e confira!](https://rockcontent.com/br/blog/yarn/#4)

## O que é Yarn?

O Yarn é um **gerenciador de pacotes para aplicar comandos prontos ao código de uma aplicação**. 

Por ser uma ferramenta de código aberto, há uma comunidade de colaboradores experientes e qualificados que, continuamente, contribuem com novas adições de códigos, gerando pacotes variados. Assim, é possível utilizá-los nas mais diversas possibilidades.

Considerado um sucessor mais eficaz e seguro do que o [NPM](https://rockcontent.com/br/blog/npm/), o Yarn tem conquistado muitos adeptos. 

O que reforça essa ideia é o fato de a ferramenta utilizar também os [bancos de dados](https://rockcontent.com/br/blog/banco-de-dados/) tanto do NPM quanto do Bower, outro importante e conhecido gerenciador de pacotes de códigos. Essa integração é de grande utilidade, trazendo praticidade à rotina do programador.

### O surgimento

A ferramenta é recente, o que traz ainda mais perspectivas de evolução, o que é ótimo para os profissionais do setor. 

Surgida em 2016, anunciada como um novo pacote de [JavaScript](https://rockcontent.com/br/blog/javascript/) para o Facebook, ela é, na prática, fruto de colaborações entre grandes empresas, incluindo o Google, para dar suporte à comunidade de programadores. 

Dessa forma, é possível estimular uma padronização de códigos que favorece todo o cenário tecnológico, seja de empresas, seja de profissionais.

### Para que serve

O Yarn é tem a proposta de levar pacotes prontos que sejam capazes de adicionar diretamente funções diversas às aplicações. 

Como é fruto de um trabalho de colaboração, programadores contribuem com pacotes prontos, tornando esse gerenciador **cada vez mais enriquecido** em variedade de recursos já com códigos devidamente concluídos.

Ao trabalhar para instalar uma dependência em uma aplicação, ou até mesmo um recurso simples, o profissional precisa desenvolver as linhas de códigos referentes a elas. 

Algumas, por serem mais básicas e se repetirem em vários softwares, não precisam exatamente serem criadas a partir do zero. Esse é um dos casos em que utilizar um pacote de códigos do Yarn pode ser muito útil.

Cada um desses pacotes compartilhados no Yarn traz arquivos package.json, que são extremamente relevantes, já que descrevem o conteúdo desse módulo. 

Por isso, é fundamental que, ao contribuir com um pacote, o programador em questão não deixe de garantir essa padronização, o que vai ajudar muito os profissionais que vão fazer o uso.



## Como instalá-lo?

O processo de instalação do Yarn é realmente bem simples, especialmente se você já é um usuário do NPM. Nesse caso, a única alteração será do workflow, já que a base de dados utilizada não muda. Nesse cenário, para instalar, **basta executar o seguinte comando no próprio NPM**:

npm install -g yarnpkg

Não se esqueça de também executar as dependências do projeto que, nesse caso, estarão no arquivo package.json. Execute o comando:

yarn

Caso você ainda não utilize nenhum gerenciador, como o NPM, você precisará simplesmente baixar o Yarn no [site](https://yarnpkg.com/en/docs/install) da ferramenta.



## Como funciona seu gerenciamento de pacotes?

O processo de gerenciamento de pacotes, da criação de uma dependência até a sua remoção, é muito prático. 

São comandos simples, que você executa sempre com poucas linhas. Confira alguns dos principais que serão úteis na rotina de trabalho.

### Para começar um projeto

Esse é o ponto de partida para muitos profissionais. Para começar, execute:

yarn init

### Para adicionar uma dependência

Para instalar uma dependência do seu arquivo package.json basta executar:

yarn add [pacote]

yarn add [pacote]@[versão]

yarn add [pacote]@[tag]

Substitua os termos “**pacote**, “**versão**” e “**tag**” pelas informações do pacote que você deseja instalar.

### Para atualizar uma dependência

Substituindo os termos, como explicado, execute:

yarn upgrade [pacote]

yarn upgrade [pacote]@[versão]

yarn upgrade [pacote]@[tag]

### Para remover uma dependência

yarn remove [pacote]

Lembre-se de que no espaço em que está “pacote” você deve substituir informando qual pacote em questão quer remover.

### Para instalar todas as dependências de um projeto

Simplesmente execute o seguinte comando:

yarn install



## Quais as funcionalidades oferecidas?

O Yarn se destaca pelo seu **uso muito mais dinâmico e facilitado**, o que é fundamental em rotinas de desenvolvimento de aplicações variadas, como [sites](https://rockcontent.com/br/blog/site/) e blogs, em plataformas [CMS](https://rockcontent.com/br/blog/cms/) — como o [WordPress](https://rockcontent.com/br/blog/wordpress/) —, [plugins](https://rockcontent.com/br/blog/plugins/) e[ templates](https://rockcontent.com/br/blog/template/). 

No entanto, algumas funcionalidades específicas e exclusivas ajudam a colocar o Yarn em destaque. Confira as principais e mais diferenciadas.

### Lock file

Uma das funcionalidades introduzidas pelo Yarn é o arquivo **yarn.lock**, que tem a proposta de bloquear qualquer dependência instalada para assegurar instalações em ambientes diferentes. 

Assim, ele é capaz de manter toda a infraestrutura original, sem mudar nada nos arquivos e garantindo o funcionamento adequado.

### Limpeza de dependências

O comando de limpeza serve para executar uma busca em todas as dependências e encontrar o que não está em uso. Isso gera uma exportação para o arquivo chamado .yarnclean. 

Esse processo garante maior otimização no funcionamento da plataforma, trazendo **produtividade no trabalho**. Para executar a limpeza, basta utilizar o seguinte comando:

yarn clean

### Workspaces

O recurso workspace foi oferecido para estruturar arquiteturas de pacotes em subpastas no Yarn. A funcionalidade ajuda de diversas formas, entre as mais importantes:

- vincular dependências umas às outras;
- instalar dependências juntas, otimizando o trabalho do Yarn;
- ao usar o lock file, o Yarn não precisará usar um arquivo para cada projeto, já que estarão juntos o mesmo workspace.

### Modo offline

Esse recurso tem como objetivo permitir que pacotes sejam instalados sem precisar estar conectado à internet. Por isso, se você já instalou determinado pacote antes, **ele estará disponível novamente**, ainda que você esteja offline.



## Quais as vantagens do Yarn?

O Yarn é uma ferramenta que trouxe diversas vantagens quando foi apresentada, e esse foi o diferencial principal para os profissionais programadores. 

Por mais que o NPM funcionasse até mesmo de forma confiável e eficaz, **o Yarn foi capaz de ressignificar as qualidades de um gerenciador de pacotes**, mas sem precisar descartar completamente o NPM.

A seguir, entenda quais são esses diferenciais e vantagens que fazem o Yarn valer a pena.

### Rede com maior estabilidade

Uma rede resiliente é capaz de manter uma estabilidade mínima para garantir que tarefas importantes sejam concluídas com qualidade. Diante disso, o Yarn garante que pequenas falha de requisição não impactem em instalações. 

Isso significa que uma instabilidade não vai arruinar todo o trabalho que estava sendo feito, já que as requisições são repetidas.

### Maior organização de requisições

Mesmo que você trabalhe com um alto volume de requisições, o Yarn vai garantir que todas elas sejam cumpridas. 

Isso depende diretamente de organização e, para entregá-la, o gerenciador elenca todas e garante que, em um sistema de fileira, todas sejam atendidas a tempo e de maneira fluída. Assim, a rede pode ter seu desempenho explorado, sem gerar dificuldades.

### Agilidade que se destaca

A agilidade do Yarn é realmente surpreendente e é a principal característica destacada por usuários e especialistas. 

Para garantir isso, os pacotes baixados geram caches que guardam suas informações, sem precisar repetir o processo. As instalações são ágeis porque as operações também são processadas paralelamente.

### Praticidade na operação

Como você conferiu ao longo deste conteúdo, qualquer comando e ação comuns à operação são executados com simples linhas, tudo muito econômico e descomplicado. Em rotinas complexas e repletas de demandas, uma ferramenta tão fácil pode auxiliar bastante na produtividade.

### Seguro

Todo pacote, antes de ser instalado, passa por uma verificação minuciosa da ferramenta. Na prática, isso vai evitar que algum arquivo corrompido seja instalado, gerando problemas técnicos e perda de tempo na operação. Para fazer isso, o Yarn usa um sistema de checksums.

### Consistência e padronização

Manter a padronização na instalação dos pacotes não precisa ser uma preocupação, graças ao caráter determinístico que o Yarn adota. 

As dependências, quando instaladas, estarão disponíveis da mesma forma, ou seja, padronizadas, independentemente de como essa instalação é feita.

Indiscutivelmente, um gerenciador de pacotes pode ser muito útil para o trabalho de programadores.

Ter **códigos livres de erros e já padronizados**, independentemente se serão personalizados, minimiza problemas e ainda traz muito dinamismo e produtividade. O Yarn é capaz de oferecer isso tudo, com o adicional de ser extremamente funcional.

Já que estamos falando de operações com o JavaScript, aproveite e [entenda mais sobre o Node.js](https://rockcontent.com/br/blog/node-js/), um ambiente de execução amplamente utilizado!