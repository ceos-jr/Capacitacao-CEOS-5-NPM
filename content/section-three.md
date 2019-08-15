# Configurando e Iniciando o NPM

## Iniciando

Para começar nossos projetos, vamos configurar o nosso NPM, automatizando algumas configurações que estão presentes em um arquivo chamado `package.json`.

Verifique se o NPM está instalado com `npm --version`. Se não estiver, volte para a próxima seção. Para iniciar o projeto, use `npm init`. Ele vai criar a `package.json` e definir os valores iniciais. Eles são o nome do criador do projeto, a versão do projeto, a descrição, a url do repositório, etc. Basicamente, com esse comando estamos dizendo "Ei npm, gerencia as minhas dependências e define as configurações de projeto ou pacote".

## Configurando

Podemos definir valores default para esses valores na `package.json`. Digite em seu terminal:

```shellscript
$ npm set init-author-name "Your name"
```

```shellscript
$ npm set init-author-email "Your e-mail"
```

```shellscript
$ npm set init-author-url "Your webpage"
```

```shellscript
$ npm set init-license "Some license(ISC, MIT, etc)"
```

Intuitivamente, sabemos que `init-author-name` é usado para configurar o nome do autor, `init-author-email` é usado para configurar o e-mail do autor, `init-author-url` é usado para configurar a página pessoal do autor e `init-license` para configurar a licença padrão quando projetos forem inicializados.

Beleza, você agora pode me fazer a seguinte pergunta: "Mas pq eu devo configurar esses valores?". Vamos la então. Quando você inicia um projeto com npm init, o npm lhe pede algumas informações. Algumas já tem valor padrão, outras não(Porque não faz sentido ou deve ser configurado por você). Assim, configurando logo esses valores, agilizamos o processo de inicialização de um projeto. Seria agora preciso apenas digitar `npm init -y` que a `package.json` seria gerada com os valores definidos ao configurar o npm.

Sobre a licença, particularmente eu utilizo por padrão a MIT, mas você pode entrar nessa [página](https://opensource.org/licenses) e ler mais sobre as licenças disponiveis para uso em projetos open source.

**Observação**: Você pode visualizar as configurações digitando `npm config ls -l`

## Instalando Pacotes de terceiros

A comunidade node tem milhões de bibliotecas disponiveis para facilitar o nosso trabalho de desenvolver projetos. Já sabemos como inicializar o nosso gerenciador de bibliotecas, mas como instalamos elas. O npm nos fornece uma command line bem intuitiva. Assim, com o simples comando de:

```shellscript
$ npm install -g <library>
```

Observe a flag `-g`. Ela instala a biblioteca globalmente. Logo, se ela tiver algum comando via CLI(Command Line Interface), podemos usar facilmente. Mas isso é algo totalmente positivo? A resposta é depende. Alguns casos é realmente necessário ter uma biblioteca instalada globalmente. Mas em geral é melhor ter elas como dependências locais pois assim fica regristrado em nosso `package.json` que temos essa biblioteca no nosso projeto junto com sua versão. Também facilita o trabalho em equipe, pois pessoas que estão trabalhando no mesmo projeto tem como instalar as dependências do projeto em diferentes máquinas com o projeto pronto para continuar sendo desenvolvido.

Certo, a flag `-g` instala globalmente a biblioteca. Mas como instalo ela localmente? Assim como temos uma flag para global, também temos flag para local. Porém agora temos dois tipos: normal e de desenvolvimento.

```shellscript
$ npm install --save <library>

# or

$ npm install -s <library>
```

```shellscript
$ npm install --save-dev <library>

# or

$ npm install -S <library>
```

Saiba bem qual tipo utilizar antes de instalar, pois isso influência diretamente o projeto em produção. Quanto mais dependência, mais pesado o projeto fica e isso influência diretamente na velocidade do site. Por exemplo, bibliotecas de teste, são dependências de desenvolvimento enquanto o react é uma dependência normal. Assim não é necessário a biblioteca de testes estar presente em produção.

Veja que ao instalar um pacote localmente, é criado uma pasta `node_modules`. Ali está as bibliotecas instaladas e seu código. Futuramente iremos aprender a criar nossa própria biblioteca.

**Observação 1**: Busque olhar o que está acontecendo com sua `package.json` ao instalar uma biblioteca.

**Observação 2**: Apesar de você intuitivamente traduzir `library` para livraria. A tradução correta nesse caso é biblioteca. POR FAVOR, não erre isso em sua vida profissional. 

## Problema de acesso negado

No mundo linux, normalmente você consegue realizar muitas atividades apenas utilizando o Terminal. Claro que isso não quer dizer que em outro SO você não possa fazer o mesmo. Algumas dessas ações via terminal exigem permissão do usuário. Por exemplo, se você tentar criar uma pasta via terminal nos diretórios anteriores a `home/<username>`, será necessário usar a palavra-chave `sudo` antes.

Mas porque toda essa explicação? Keep calm and lets know why. Normalmente o node é instalado em uma pasta em que você não tem permissão para editar sem usar `sudo`. Isso quer dizer que qualquer comando de escrita realizado pelo node ou npm vai causar um conflito. Ou seja, quando instalarmos uma biblioteca globalmente, teriamos um erro caso não seja usado a palavra-chave `sudo`.

Mas resolver isso é algo bem simples.

1. Primeiro, crie uma pasta em seu repositório raiz

```shellscript
$ mkdir ~/.npm-global
```

2. Configure o npm para considerar essa pasta o lugar onde fica as bibliotecas instaladas globalmente

```shellscript
$ npm config set prefix '~/.npm-global'
```

3. Abra o arquivo `~/.profile` e adicione no final uma linha de configuração

Abra com o nano ou qualquer outro editor de texto
```shellscript
$ nano ~/.profile
```

Adicione essa instrução no fim do arquivo
```shellscript
export PATH=~/.npm-global/bin:$PATH
```

4. Atualize o '~/.profile'

```shellscript
$ source ~/.profile
```

**Observação**: Caso você tenha instalado o node.js com o nvm, não é necessário realizar essa configuração.

## Removendo bibliotecas

Mais uma vez o npm salva nossas vidas quando a ideia é remover bibliotecas instaladas. Sejam elas globais ou locais.

```shellscript
$ npm uninstall -g <library>
```

```shellscript
$ npm uninstall --save <library>
```

```shellscript
$ npm uninstall --save-dev <library>
```

Pelas linhas de comando acima, veja que você so precisa saber como a biblioteca foi instalada. Ou seja, global, local normal ou local dependência de desenvolvedor.

## GIT IGNORE

NUNCA. NUNCA. NUNCA mesmo você deve mandar a pasta `node_modules` para o repositório do git. Por isso o git nos fornece uma forma de negar o versionamento de determinado arquivo ou pasta. Basta criar um arquivo `.gitignore` e adicionar os arquivos que devem ser ignorados. Existe um [repositório](https://github.com/github/gitignore) que fornece o `.gitignore` para cada tipo de linguagem. Assim, é garantido que você nunca vai enviar um arquivo especifico da linguagem que você esta trabalhando que não deve ser versionado para o github.

## Instalando bibliotecas de projetos

Quando você baixa em sua máquina um repositório, nele não deve vir as bibliotecas instaladas. Ou seja não deve existir uma node_modules. Mas uma das mágicas do NPM é analisar o seu `package.json`, buscar as dependências, criar uma pasta `node_modules` e colocar todas as dependências dentro dessa pasta. Logo vai estar tudo pronto para execução do projeto.

