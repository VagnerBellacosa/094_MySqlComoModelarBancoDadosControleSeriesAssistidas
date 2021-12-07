# Yarn: saiba tudo sobre esse gerenciador de pacotes Javascript!

- por[Cairo Noleto](https://blog.betrybe.com/author/cairo-noleto/) - 16 de outubro de 2020 - 11 minutos de leitura

Os gerenciadores de pacotes são ferramentas que auxiliam a criação de aplicações web por meio da instalação de pacotes de forma automática. Existem diferentes alternativas disponíveis no mercado que desenvolvem essa tarefa, uma delas é o **Yarn**.

Basicamente, ele é um poderoso gerenciador de pacotes para [JavaScript ](https://blog.betrybe.com/javascript/)desenvolvido pelo Facebook com a ajuda das empresas Exponent, [Google](https://blog.betrybe.com/tecnologia/truques-e-codigos-do-google/) e Tilde, e disponibilizado em [código aberto](https://blog.betrybe.com/tecnologia/codigo-aberto/) desde 2016. O Yarn foi criado para suprir a necessidade de oferecer mais velocidade, estabilidade e segurança na construção de aplicações web.

Um dos dilemas das pessoas que desenvolvem aplicações é a dúvida sobre qual ferramenta de gerenciamento de pacotes deve utilizar, já que existem diferentes e boas opções gratuitas, como o NPM do Node.js. Afinal, **Yarn vs NPM** não deixam de ser grandes concorrentes. Entretanto, é preciso conhecer as características dessas ferramentas para escolher a alternativa que ofereça melhores recursos.

Para ajudar você a conhecer um pouco mais sobre o Yarn package, fizemos este conteúdo que conta com os seguintes tópicos:

- [O que é e para que serve o Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#1)
- [Como é a arquitetura do Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#2)
- [Quais as diferenças entre Yarn e NPM?](https://blog.betrybe.com/desenvolvimento-web/yarn/#3)
- [Preciso parar de usar NPM para usar o Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#4)
- [Migrando de NPM para Yarn? Conheça os principais comandos Yarn e seus equivalentes em NPM](https://blog.betrybe.com/desenvolvimento-web/yarn/#5)
- [Quais as vantagens de usar o Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#6)
- [Quais as desvantagens do Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#7)
- [Como instalar o Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#8)
- [Quais as principais funcionalidades do Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#9)
- [Como utilizar o Yarn na prática?](https://blog.betrybe.com/desenvolvimento-web/yarn/#10)
- [Como desinstalar o Yarn?](https://blog.betrybe.com/desenvolvimento-web/yarn/#11)

Boa leitura!

## O que é e para que serve o Yarn?

Em uma [aplicação web](https://blog.betrybe.com/desenvolvimento-web/aplicacoes-web/) é comum adicionarmos diferentes ferramentas e [frameworks](https://blog.betrybe.com/framework-de-programacao/o-que-e-framework/) no projeto para atribuir funcionalidades e evitar o desenvolvimento de recursos que já existem e que podem ser reaproveitados, como o Bootstrap, [React](https://blog.betrybe.com/desenvolvimento-web/react/), [Angular](https://blog.betrybe.com/framework-de-programacao/angular/) e muitos outros. Invariavelmente, quando uma aplicação utiliza recursos externos significa que ela contém dependências que precisam ser referenciadas na aplicação.

Existem diferentes formas de adicionar esses recursos, uma delas é fazer o download e a instalação manual dos códigos. Essa forma, entretanto, além de mais trabalhosa pode gerar [falhas no funcionamento da aplicação](https://blog.betrybe.com/tecnologia/o-que-e-bug/) e dificuldade de manutenção.

Basicamente, a função dos gerenciadores de pacotes, como o **Yarn**, é **permitir a instalação desses recursos no projeto de forma rápida e segura**. Isso é feito por meio de instruções em linha de comando.

Assim, sempre que um recurso é adicionado, ele baixa os códigos necessários de um repositório e os adiciona ao projeto, além de adicionar as referências necessárias, caso o pacote precise de outras bibliotecas como dependência para funcionar corretamente.

O Yarn, portanto, é um **gerenciador de pacotes que faz a instalação, alteração e exclusão de recursos em aplicações web**. Trata-se de uma ferramenta de código aberto, que surgiu para suprir algumas necessidades que o seu principal concorrente, o NPM apresenta, entre elas a lentidão e a impossibilidade de instalar pacotes de forma offline.

## Como é a arquitetura do Yarn?

Em gerenciadores de pacotes como o Node, as dependências de um projeto são adicionadas em uma pasta chamada node_modules e relacionadas em um arquivo no formato [JSON](https://blog.betrybe.com/tecnologia/json/), chamado package.json. Assim, sempre que um novo pacote precisar ser instalado, atualizado ou removido, esses elementos são atualizados.

O **Yarn** também executa essas ações, embora na versão 2.x, os pacotes sejam instalados na pasta .yarn e não na node_modules como na versão 1.x. Além disso, ele contém um arquivo chamado yarn.lock, que armazena a versão de cada pacote utilizado na aplicação.

É essa característica que confere a ele a informação necessária para que a aplicação seja sempre a mesma, seja qual for o local em que ela estiver instalada. Outra particularidade de sua arquitetura é a forma de instalação dos pacotes, que é feita em três etapas distintas:

- **resolução**: em que o Yarn executa buscas nos registros para verificar as dependências existentes;
- **pesquisa no cache**: o Yarn procura pelas dependências necessárias no cache para verificar se elas já foram baixadas. Caso não existam, elas são baixadas primeiramente para o cache;
- **instalação**: por fim, as dependências são instaladas na pasta node_modules ou .yarn, de acordo com versão, e atualizadas nos arquivos de controle do Yarn.

## Quais as diferenças entre Yarn e NPM?

O comando NPM surgiu em meados de 2009 e foi criado com o intuito de **simplificar a troca de código JavaScript**. Assim como o comando YARN, ele tem a função de **gerenciar pacotes padrão da** **Node.js**. Além disso, o NPM também utiliza o pacote de configuração **package.json**. E aí você deve estar se perguntando, afinal, qual a diferença?

O comando YARN faz brilhar os olhos de um desenvolvedor ou desenvolvedora em relação à velocidade e segurança, pois o npm apresenta alguns problemas em relação a isso. 

Com o npm, a pessoa desenvolvedora pode enfrentar problemas, como a **divergência de versão de dependências**. Nesse problema, há a criação de um projeto que é colocado em um repositório remoto, como o gitHub ou gitLab. Quando outra pessoa clona o projeto e digita “npm install “para trazer as dependências do projeto, as versões ficam incompatíveis. Além disso, outra diferença é que o yarn gera o **yarn.lock**

## Preciso parar de usar NPM para usar o Yarn?

Aqui vai uma notícia boa: não, você não precisa banir totalmente um comando da sua vida para fazer uso de outro.

Você pode **utilizar ambos os comandos de acordo com a necessidade que você encontra em cada projeto**, afinal, é você quem determina qual se encaixa melhor de acordo com um framework, projeto ou o que o seu time está mais habituado a utilizar.

## Migrando de NPM para Yarn? Conheça os principais comandos Yarn e seus equivalentes em NPM

Como dito acima, o yarn e o npm são bem parecidos e seu uso não difere tanto. **Na maioria das vezes, o que você modificará é o começo do comando**, que, ao invés de ser npm, será yarn. Aqui separamos alguns exemplos dos principais comandos para mostrar a você:

| **NPM**         | **YARN**                 |
| --------------- | ------------------------ |
| npm install     | yarn                     |
| npm run         | yarn run                 |
| npm init        | yarn init                |
| npm cache clean | yarn cache clean         |
| npm shrinkwrap  | yarn generate-lock-entry |

Agora, vamos entender brevemente qual a função de cada comando yarn posto na tabela acima:

### YARN:

O comando yarn **serve para atualizar as dependências do projeto**. Vamos supor que você clonou o projeto de um repositório no gitHub. Para conseguir rodar o projeto, você precisará baixar as dependências, pois geralmente quando o desenvolvedor ou desenvolvedora sobe seu código para o repositório remoto, ele ignora a node_modules, e, para baixá-la em sua máquina, basta usar o *comando yarn*.

### Yarn run:

Depois de clonar o projeto e baixar as dependências, você pode utilizar o comando **yarn run para iniciar o projeto** e ver ele “funcionando” localmente.

### Yarn init:

É utilizado para criar o arquivo package.json.

### Yarn cache clean:

O comando yarn cache clean é utilizado para limpar o cache da aplicação.

### Yarn generate-lock-entry

É utilizado para criar o arquivo yarn.lock.

Newsletter da Trybe

Junte-se a mais de 100.000 pessoas da nossa tribo que recebem conteúdos gratuitos e exclusivos em nossa newsletter semanal!

## Quais as vantagens de usar o Yarn?

Existem muitos benefícios em utilizar o Yarn como gerenciador de pacotes. Confira, a seguir, as principais características dessa ferramenta.

### Modo offline

**O gerenciador contém um recurso de cache**, ou seja, quando um pacote é baixado pela primeira vez, fica armazenado em cache. Isso permite que se houver a necessidade de reinstalar esse mesmo pacote, ele fará primeiro a avaliação nesse espaço para conferir se o pacote já existe. Caso ele seja encontrado, não é preciso realizar um novo download.

Vale ressaltar que o Yarn define um local de cache padrão de acordo com a pasta raiz do projeto. Entretanto, é uma opção configurável e pode ser alterada conforme a necessidade. Outra característica desse recurso é que ele pode ser desabilitado, limpo e, até mesmo, compartilhado.

### Gerenciador de pacotes determinísticos

Outro benefício do Yarn é ser um gerenciador de pacotes determinísticos. Na prática, sempre que um novo projeto é criado, ele **contém um arquivo de configuração que armazena todas as dependências do projeto com suas respectivas versões**.

Essa característica permite que uma mesma aplicação contenha todas as dependências em qualquer ambiente em que for instalada. Trata-se de uma funcionalidade que ajuda a evitar situações em que um projeto só funciona em uma máquina específica.

### Desempenho da rede

Existem projetos que utilizam muitas dependências. Portanto, ao fazer a solicitação ao repositório para a instalação ou a manutenção dessas dependências pode ocorrer uma certa lentidão para o descarregamento dos arquivos necessários. O Yarn faz o enfileiramento das solicitações de forma eficiente com o objetivo de **evitar a sobrecarga da** [**rede**](https://blog.betrybe.com/tecnologia/topologias-de-rede/).

### Resiliência da rede

Como mencionamos, existem aplicações que utilizam inúmeros pacotes de dependências. Entretanto, podem ocorrer falhas de comunicação durante a instalação desses arquivos, o que causaria problemas na aplicação.

Uma das funcionalidades do Yarn **é repetir a solicitação em caso de falha**. Vale dizer que essa repetição é feita apenas para os casos que não foram concluídos com sucesso, o que evita o processamento duplicado das requisições.

### Modo plano

Existem muitos pacotes que utilizam outras bibliotecas como dependência. Portanto, ao baixar recursos que utilizam a mesma dependência, alguns gerenciadores de pacotes normalmente criam versões duplicadas do mesmo conteúdo.

O Yarn oferece um recurso chamado flat mode que elimina essa duplicidade, pois **permite a instalação de todas as dependências com uma única versão para cada pacote**.

## Quais as desvantagens do Yarn?

Por ser uma versão melhorada do npm, as desvantagens de se utilizar o comando yarn **fica a critério de cada pessoa desenvolvedora**, pois há aqueles que preferem utilizar o comando npm por ter mais familiaridade com ele, e há os que buscam utilizar o yarn por sua facilidade.

## Como instalar o Yarn?

A instalação do Yarn pode ser feita de forma bem simples por meio de outro gerenciador de pacotes, como o NPM, Scoop, Chocolatey, entre outros. Além disso, o **Yarn download** pode ser feito no [site oficial](https://classic.yarnpkg.com/en/docs/install#windows-stable) da ferramenta. Para executar o **Yarn install** pelo NPM, por exemplo, basta escrever o comando a seguir:

```javascript
npm install -g yarn
﻿
```

Vale dizer que existem versões para diferentes plataformas, como Windows, macOS, além de diferentes distribuições do [Linux](https://blog.betrybe.com/tecnologia/comandos-linux/).

## Quais as principais funcionalidades do Yarn?

### Yarn.lock: bloqueando dependências instaladas

O arquivo yarn.lock **assegura que as versões instaladas originalmente no projeto serão as mesmas em todas as máquinas** que baixarem aquele projeto. 

Esse era um dos problemas do npm, que modifica a versão de dependências podendo gerar conflitos de versão dentro do projeto.

### Yarn clean: fazendo a limpeza de dependências

O Yarn Clean é bastante útil para **deixar o projeto o mais limpo possível**. Ele faz uma varredura em todo o projeto em busca de dependências que não estão sendo usadas no projeto e as elimina. Isso ajuda bastante a deixar o projeto mais leve, principalmente em ambiente de produção, o que é essencial para o usuário ou usuária.

###  Modo off line

O yarn **permite que pessoas desenvolvedoras baixem dependências mesmo não estando conectados a internet**, o que é muito útil, pois se houver uma queda de internet, existe a possibilidade de seguir com o desenvolvimento local e instalar as dependências necessárias no projeto para isso.

### Workspaces

O workspaces é uma função do yarn que lembra a estruturação de arquitetura. Com ele é possível **juntar e instalar múltiplas dependências**.

## Como utilizar o Yarn na prática?

**A utilização do Yarn é bem semelhante à de outros gerenciadores de pacotes**. Confira, a seguir, como executar as principais tarefas em um projeto.

### Inicializando o Yarn

Para utilizar o Yarn em um projeto é preciso fazer a sua inicialização. Para isso, acesse a pasta em que a aplicação será criada e digite o seguinte comando:

yarn init

Será exibido uma série de questões para a criação do projeto:

- name;
- version;     
- description;
- entry point (index.js);
- repository URL;
- author;
- license (MIT);
- private.

Ao final do processo será gerado o arquivo package.json com os dados informados nessas questões. Confira o [código](https://blog.betrybe.com/tecnologia/algoritmo/):

```javascript
{
  "name": "projetoYarn",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT"
}
﻿
```

É importante dizer que o Yarn instalado é referente a versão 1.x. Entretanto, ele já está na versão 2.x, chamada Berry, que tem o processo de instalação um pouco diferente, pois ela é feita por projeto. Portanto, para utilizar essa versão é preciso adicionar uma etapa com o seguinte código:

```javascript
yarn policies set-version berry 
yarn set version berry        
﻿
```

Para conferir se a versão foi atualizada, basta digitar o seguinte código no terminal.

```javascript
yarn --version 
﻿
```

### Adicionando dependências

Com o projeto criado é hora de adicionar as dependências, que são as bibliotecas e [frameworks](https://blog.betrybe.com/framework-de-programacao/o-que-e-framework/) que serão utilizados no projeto. O Yarn disponibiliza os mesmos pacotes que outros gerenciadores disponíveis no mercado, como o NPM. Para adicionar um recurso, basta informar uma das opções a seguir:

```javascript
yarn add [nome_do_pacote]
yarn add bootstrap //exemplo
﻿
```

Nesse caso, será adicionada a última versão do pacote.

```javascript
yarn add [nome_do_pacote]@[versão]
yarn add bootstrap@4.1.3 // exemplo
﻿
```

Nesse caso, será adicionada a versão indicada no comando.

```javascript
yarn add[nome_do_pacote]@[tag]
yarn add bootstrap@latest // exemplo
﻿
```

### Instalando dependências

O Yarn permite fazer a instalação das dependências a partir do arquivo package.json, isto é, ele verifica as dependências relacionadas e realiza a instalação se for preciso. Existem duas formas de fazer isso, que é com os seguintes comandos:

```javascript
yarn 
// ou
yarn install.
﻿
```

### Fazendo updates

Os pacotes adicionados também podem ser atualizados. É possível atualizar várias dependências ao mesmo tempo ou indicar um pacote específico. Confira a sintaxe, a seguir:

```javascript
yarn upgrade [nome_do_pacote] // versão 1.x
yarn up [nome_do_pacote] // versão 2.x
﻿
```

É importante dizer que na versão 2.x o comando upgrade foi substituído por apenas up. Assim como no comando para adicionar pacotes, o **Yarn update** também pode ser feito com a indicação de uma tag ou com a indicação da versão desejada.

```javascript
yarn upgrade [nome_do_pacote]@[versão] // versão 1.x
yarn up [nome_do_pacote]@[versão] // versão 2.x
yarn upgrade [nome_do_pacote]@[tag] // versão 1.x
yarn up [nome_do_pacote]@[tag] // versão 2.x
﻿
```

### Removendo dependências

Outra funcionalidade importante no Yarn é a remoção de dependências, caso determinado pacote não seja mais utilizado pela aplicação. Essa tarefa é feita por meio do comando **Yarn remove**, que além de excluir o pacote, fará a atualização nos arquivos de configuração package.json e yarn.lock. Veja qual é a sintaxe do comando:

```javascript
yarn remove [nome_do_pacote]
﻿
```

## Como desinstalar o Yarn?

A forma de desinstalar o yarn vai depender de como você o instalou. Aqui vão alguns modos:

- Se você instalou globalmente com o npm:

npm unistall -g yarn

- Ubuntu:

sudo apt-get remove yarn && sudo apt-get purge yarn

- Tarball

rm -rf “$HOME/.yarn”

Como você pôde acompanhar, **o Yarn é um poderoso gerenciador de pacotes,** criado para oferecer mais velocidade e segurança na manipulação de dependências em uma aplicação web. Ele conta com recursos essenciais, como o modo offline, além de outras funcionalidades que facilitam o controle de bibliotecas e frameworks de forma simples e eficiente.

Utilizar o yarn traz diversos benefícios para a pessoa desenvolvedora, como segurança, praticidade, velocidade e clareza. Por ter sido criado com o intuito de suprir um problema que havia com o NPM, ele agrada muito desenvolvedores e desenvolvedoras que o utilizam, então, se você está iniciando ou quer migrar para o yarn, pode ser que você se surpreenda com sua facilidade!

Gostou do nosso conteúdo sobre o que é Yarn? Então, confira este post sobre [IDE e saiba o que é um ambiente de desenvolvimento integrado](https://blog.betrybe.com/tecnologia/ide/)!