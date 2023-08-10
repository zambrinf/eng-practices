# Navegando uma CL em Revisão

## Resumo

Agora que você sabe [O que buscar em uma revisão de código](looking-for.md),
qual é o modo mais eficiente de organizar uma revisão que está espalhada por
diversos arquivos?

1. A mudança faz sentido? Ela tem uma boa
   [descrição](../developer/cl-descriptions.md)?
2. Olhe a parte mais importante da alteração primeiro. Ela foi bem desenvolvida
   no geral?
3. Olhe o restante da CL em uma sequência apropriada.

## Passo um: Dê uma olhada ampla na alteração {#step_one}

Olhe a [descrição da CL](../developer/cl-descriptions.md) e o que ela faz no
geral. A mudança faz sentido? Se essa mudança não deveria ter acontecido em
primeiro lugar, responsa imediatamente com uma explicação do motivo dessa
alteração não acontecer. Quando você rejeita uma mudança como essa, também é uma
boa ideia sugerir ao desenvolvedor o que ele deveria ter feito.

Por exemplo, você pode dizer "Parece que isso deu um bom trabalho, obrigado!
Entretanto, nós estamos indo numa direção de remover o sistema FooWidget que
você está modificando aqui, então não quremos fazer nenhuma nova modificação
agora. Que tal ao invés disso você refatorar nossa nova classe BarWidget?"

Observe que não só o o revisor rejeitou a atual CL e sugeriu uma alternativa,
como ele fez isso com _cortesia_. Esse tipo de cortesia é importante porque nós
queremos mostrar respeito como desenvolvedores mesmo quando nós discordamos.

Se você pegar mais do que algumas CLs que representam mudanças que você não quer
fazer, considere retrabalhar o processo de desenvolvimento do seu time ou o
processo para contribuidores externo para que exista mais comunicação antes das
CLs serem escritas. É melhor falar "não" às pessoas antes que elas façam um
trabalho gigantesco que agora precisa ser jogado fora ou drasticamente refeito.

## Passo dois: Examine as principais partes da CL {#step_two}

Busca o arquivo ou os arquivos que são a parte principal da CL. Frequentemente,
tem um arquivo que tem maior número de alterações lógicas, e é a maior parte da
CL. Olhe essa principal parte primeiro. Isso ajuda a dar um contexto para todas
as pequenas partes da CL, e em geral acelera a revisão de código. Se a CL for
grande demais para você encontrar a parte principal, pergunte ao desenvolvedor o
que olhar primeiro, ou peça a ele para
[dividir a CL em múltiplas CLs](../developer/small-cls.md).

Se você ver grandes problemas de design nessa parte da CL, você deve enviar
comentários imediatamente, mesmo se você não tiver tempo de revisar o restante
da CL no momento. De fato, revisar o restante da CL poderia ser uma perda de
tempo, porque se os problemas de design forem significantes, grande parte do
código em revisão pode desaparecer e não interessar mais.

Existem duas grandes razões para ser importante enviar esses comentários
imediatamente:

- Desenvolvedores geralmente enviam a CL por email e então imediatamente começam
  um novo trabalho baseado na CL enquanto estão esperando a revisão. Se existem
  grandes problemas de design na CL que você está revisando, então também terá
  retrabalho na próxima CL. Você vai querer pegá-los antes de eles terem feito
  muito trabalho baseado nesse design problemático.
- Grandes mudanças de design precisam de mais tempo do que pequenas mudanças.
  Quase todos desenvolvedores tem prazos; para cumprir esses prazos e ainda ter
  qualidade no código, o desenvolvedor precisa começar qualquer grande
  retrabalho na CL o quanto antes.

## Passo três: Olhe o restante da CL em uma sequência apropriada {#step_three}

Uma vez que você confirmou que não há grandes problemas de design na CL como um
todo, tente imaginar uma sequência lógica para olhar pelos arquivos enquanto
garanta que você não vai perder nenhum arquivo a ser revisado. Usualmente depois
de ver os principais arquivos, é mais simples apenas olhar cada arquivo na ordem
que a ferramente de revisão de código apresenta para você. Algumas vezes também
é útil ler os testes antes de ler o código principal, porque você tem uma ideia
do que a mudança se propõe a fazer.

Próxima: [Velocidade das Revisões de Código](speed.md)
