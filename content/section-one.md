# NODE.js

Provavelmene você ja deve ter ouvido falar dessa palavra desde a sua entrada na UFC. Nessa sessão vamos entender muito pouco sobre essa tecnologia, mas não deixe de fixar alguns termos dito aqui, pois facilita você entender o motivo de ser uma ferramenta muito utilizada.

Em um mundo com PHP, Java, Python e Ruby, temos uma paralisação de processamento quando realizamos uma operação de Entrada/Saída(Chamaremos normalmente esse termo de I/O). Isso nos custa muito em tempo de resposta para o usuário. Essa abordagem é conhecida como Blocking Thread. Vamos dar um exemplo. Suponha que você tenha um servidor. Para cada usuário que realiza uma requisição a esse servidor para pegar alguma informação do banco de dados, temos um processo. Agora suponha que vários usuários realizem uma requisição. Como estamos em uma arquitetura Blocking-Thread, uma requisição será respondida apenas quando a anterior tiver sido completamente processada.

Com NODE.js, temos outra abordagem chamada de Non-Blocking Thread. Para explicá-la, vamos de novo ver um exemplo. Suponha que temos um servidor. E diferentes usuário realizam uma requisição para coletar suas informações de um banco de dados. Sendo o servidor em NODE.js, a primeira vai iniciar, logo apos isso, a segunda requisição vai iniciar, não esperando o fim do processamento da primeira. Quando houver uma resposta o NODE se encarrega de dizer que esta pronto e enviar para o usuário. Observe a imagem abaixo para complementtar o entendimento da diferença entre essas duas arquiteturas.

![Blocking vs Non-Blocking arquitetura](../.github/part-one/blockingvsnonblocking.png)

A imagem acima foi retirada do seguinte [artigo](https://www.freecodecamp.org/news/what-exactly-is-node-js-ae36e97449f5/).

Aqui vemos uma clara vantagem de utilizar NODE.js. Com pouco recurso computacional, podemos criar aplicações poderosas que aceitam mais requisições de usuário. Mas o que realmente é node.js? Uma linguagem de programação? Na verdade, depois da explicação, você estra proibido de dizer que NODE.js é uma linguagem de programação. NODE é um runtime javascript que utiliza a engine V8. A mesma engine utilizada no navegador da google Chrome. Podemos dizer que é um interpretador javascript. De modo grosso e superficial, ele traduz um código javascript para um código back-end válido.

> A título de curiosidade. NODE.js foi escrito inicialmente em C++. Caso você queira ver o github do node.js, acesse esse [link](https://github.com/nodejs/node).

> NODE.js foi criado por Ryan Dahl e mais 14 colaboradores. Em 2009 ele apresentou a tecnologia na JSCONF Europeia. Recomendo muito que você assista essa [palestra](https://www.youtube.com/watch?v=ztspvPYybIY)

> Para quem acha que NODE.js é perfeito. Assista essa [palestra](https://www.youtube.com/watch?v=M3BM9TB-8yA) mostrando que existem pontos negativos também na tecnologia. (**Spoiler**). Ryan Dahl está criando outro sistema chamado [Deno](https://deno.land/) que corrige essas desvantagens.

**Observação talvez desnecessária**: Ryan Dahl é um gênio. Talvez você se ache incapaz de realizar um feito como o dele, mas se você observar na palestra, o perfil dele é de um cara introvertido. Não se diminua, estude e nunca ache que sabe de tudo. Esteja em constante aprendizado. Converse com pessoas para entender diferentes pontos de vista e assim você pode se tornar tão F**A quanto esse cara.