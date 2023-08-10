# Como lidar com os comentários do revisor

Quando você envia um CL (Changelist) para revisão, é provável que o revisor
responda com vários comentários sobre o seu CL. Aqui estão algumas coisas úteis
para saber sobre como lidar com os comentários do revisor.

## Não leve para o lado pessoal {#personal}

O objetivo da revisão é manter a qualidade da nossa base de código e dos nossos
produtos. Quando um revisor faz uma crítica ao seu código, pense nisso como uma
tentativa de ajudar você, a base de código e o Google, em vez de um ataque
pessoal contra você ou suas habilidades.

Às vezes, os revisores podem ficar frustrados e expressar essa frustração em
seus comentários. Isso não é uma prática adequada para os revisores, mas como
desenvolvedor, você deve estar preparado para isso. Pergunte a si mesmo: "Qual é
a coisa construtiva que o revisor está tentando me comunicar?" e então aja como
se isso fosse o que eles realmente disseram.

**Nunca responda com raiva aos comentários da revisão de código.** Isso é uma
séria violação da etiqueta profissional e ficará registrado para sempre na
ferramenta de revisão de código. Se estiver muito irritado ou incomodado para
responder com gentileza, afaste-se do computador por um tempo ou trabalhe em
outra coisa até se sentir calmo o suficiente para responder de forma educada.

Em geral, se um revisor não está fornecendo feedback de maneira construtiva e
educada, explique isso a eles pessoalmente. Se não puder falar com eles
pessoalmente ou por chamada de vídeo, envie-lhes um e-mail privado. Explique de
maneira gentil o que você não gosta e o que gostaria que eles fizessem de
maneira diferente. Se eles também responderem de forma não construtiva a essa
discussão privada, ou se isso não tiver o efeito desejado, então recorra ao seu
gerente, conforme apropriado.

## Corrigir o Código {#code}

Se um revisor disser que não entende algo em seu código, sua primeira resposta
deve ser melhorar o próprio código. Se o código não puder ser melhorado,
adicione um comentário explicando por que o código está ali. Somente se um
comentário parecer sem sentido, sua resposta deve ser uma explicação na
ferramenta de revisão de código.

Se um revisor não entendeu alguma parte do seu código, é provável que outros
leitores futuros do código também não entenderão. Responder na ferramenta de
revisão de código não ajuda os futuros leitores de código, mas esclarecer o seu
código ou adicionar comentários ajuda.

## Pensar de forma colaborativa {#think}

Escrever um CL pode exigir muito trabalho. É muitas vezes muito satisfatório
enviar um CL para revisão, sentir que está concluído e ter certeza de que nenhum
trabalho adicional é necessário. Pode ser frustrante receber comentários pedindo
mudanças, especialmente se você não concorda com eles.

Nesses momentos, reserve um momento para refletir se o revisor está fornecendo
feedback valioso que ajudará a base de código e o Google. Sua primeira pergunta
para si mesmo deve ser sempre: "Eu entendi o que o revisor está pedindo?"

Se você não puder responder a essa pergunta, peça esclarecimentos ao revisor.

E então, se você entender os comentários, mas discordar deles, é importante
pensar de forma colaborativa, não combativa ou defensiva:

Ruim: "Não, não vou fazer isso."

Bom: "Eu escolhi a opção X por causa [desses prós/contras] com [essas
compensações]. Minha compreensão é que usar Y seria pior por causa [dessas
razões]. Você está sugerindo que Y atende melhor às compensações originais, que
devemos ponderar as compensações de forma diferente ou algo mais?"

Lembre-se, a
**[cortesia e o respeito](https://chromium.googlesource.com/chromium/src/+/master/docs/cr_respect.md)
devem ser sempre a primeira prioridade**. Se você discordar do revisor, encontre
maneiras de colaborar: peça esclarecimentos, discuta prós/contras e explique por
que seu método é melhor para a base de código, usuários e/ou Google.

Às vezes, você pode saber algo sobre os usuários, base de código ou CL que o
revisor desconhece. [Corrija o código](#code) quando apropriado e envolva o
revisor em uma discussão, fornecendo mais contexto a eles. Geralmente, é
possível chegar a um consenso entre você e o revisor com base em fatos técnicos

## Resolvendo Conflitos {#conflicts}

Seu primeiro passo para resolver conflitos deve ser sempre tentar chegar a um
consenso com o revisor. Se não conseguir alcançar um consenso, consulte
[O Padrão de Revisão de Código](../reviewer/standard.md), que apresenta
princípios a serem seguidos em tal situação.
