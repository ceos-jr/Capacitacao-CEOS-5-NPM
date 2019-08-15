# Gerenciador de versões do NODE.js

Explicamos o necessário para esse módulo sobre o NODE.js e agora vamos aprender a instalar e utilizar essa ferramenta

**Observação**: É extremamente recomendado que você utilize a instalação utilizando o NVM. A título de curiosidade, deixamos como realizar a instalação comum. Caso você seja usuário windows, recomendo que pare. Brincadeira a parte, utilize a instalação comum.

## Instalação comum

Antes de começarmos, saiba que essa talvez não seja a melhor e a unica maneira de se instalar essa ferramenta. Mais abaixo você conhecerá o NVM que irá tornar sua vida mais fácil em questão de gerenciamento de versões do NODE.js. Por que isso é importante? Versões mais novas do NODE.js tem suporte para features javascript lançadas recentemente, mas algumas aplicações são construídas em cima de versões mais antigas e assim, caso seja necessário, precisamo voltar versões.

Acessando o site do [node.js](https://nodejs.org/pt-br/), você tem um botão de download. Para Windows esse botão servirá muito bem para o que queremos. Para Linux, vamos utilizar esse [link](https://nodejs.org/pt-br/download/package-manager/). Basta você escolher a Distro que utiliza e seguir o passo a passo.

Caso você seja usuário de ubuntu, use a seção *Como instalar utilizando PPA* desse [link](https://www.digitalocean.com/community/tutorials/como-instalar-o-node-js-no-ubuntu-16-04-pt).

## Instalação utilizando o NVM

Primeiro, é necessário a instalação do NVM. Para fazer isso, baixe o script com

```shellscript
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

ou 

```shellscript
$ wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

Reinicie o seu terminal e teste se o NVM foi corretamente instalado digitando `nvm`.

Agora, para realizar a instalação do node.js, basta digitar:
```shellscript
$ nvm install node
```

Para realizar a instalação de uma versão específica, utilize:
```shellscript
$ nvm install <número da versão>
```

Ex.:
```shellscript
$ nvm install 6.0.0
```

Para listar as versões, utilize:
```shellscript
$ nvm ls-remote
```

Para usar uma versão, utilize:
```shellscript
$ nvm use 6.0.0
```

## Usando Node.js

Agora que temos tudo instalado, estamos pronto para utilizar o Node.js. Abra seu terminal e digite `node`.
Você verá que o terminal agora apresenta um simbolo de `>`. Você pode digitar agora qualquer código javascript válido que o node executará. Teste um pouco seus conhecimentos de javascript utilizando essa interface do terminal.

Escrever projetos dessa forma é algo inviável. Logo existe outra forma de executar seu código javascript com o node.js. Crie um arquivo com extensão `.js`. Por exemplo, `index.js`. Depois escreva algum código como mostra abaixo:

```js
console.log("Hello, world!");
```

Feito isso, digite em seu terminal `node index.js`. E catchau, você vai visualizar a mensagem `Hello, world!`.


