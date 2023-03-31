# Como escrever comentários de Revisão de Código

## Resumo

- Seja gentil.
- Explique seu raciocínio.
- Equilibre dar soluções explícitas com apenas apontar problemas e deixar o
  desenvolvedor decidir.
- Encoraje o desenvolvedor a simplificar o código e adicionar comentários ao
  invés de apenas explicar a complexidade a você.

## Cortesia

Em geral, é importante ser
[cortês e respeitoso](https://chromium.googlesource.com/chromium/src/+/master/docs/cr_respect.md)
enquanto também está sendo bem claro e útil para o desenvolvedor cujo código
está sendo revisado. Um jeito é garantir que sempre está fazendo comentários
sobre o _código_ e nunca fazendo comentários sobre o _desenvolvedor_. Nem sempre
você precisa seguir essa prática, mas você definitivamente deve usá-la quando
falando algo que pode soar ríspido ou controverso. Por exemplo:

Ruim: "Por que **você** usa threads aqui quando obviamente não há benefícios
para serem conseguidos com concorrência?"

Bom: "O modelo de concorrência aqui está adicionando complexidade ao sistema sem
nenhum benefício real de performance que eu consiga ver. Como não há benefícios
de performance, é melhor que o código seja single-threaded ao invés de usar
múltiplas threads."

## Explique porquê {#why}

Uma coisa que você vai perceber sobre o exemplo "bom" acima é que ele ajuda o
desenvolvedor entender _porquê_ você está fazendo esse comentário. Você nem
sempre precisa incluir essa informação nos seus comentários de revisão, mas
algumas vezes é apropriado dar um pouco mais de explicação sobre sua intenção, a
melhor prática que você está seguindo, ou como a sugestão melhora a qualidade do
código.

## Dando orientação {#guidance}

**Em geral é responsabilidade do desenvolvedor ajustar a CL, não do revisor.**
Você não precisar fazer um design detalhado de uma solução ou escrever o código
para o desenvolvedor.

Isso não quer dizer que o revisor não deve ser prestativo, no entanto. Em geral
você deve ter um equilíbrio apropriado entre apontar problemas e dar orientações
diretas. Apontar problemas e deixar o desenvolvedor decidir geralmente ajuda o
desenvolvedor aprender, e faz revisões de código serem mais fáceis. Isso também
pode resultar numa solução melhor, pois o desenvolvedor está mais familiarizado
com o código do que o revisor está.

Entretanto, às vezes instruções diretas, sugestões, ou mesmo código é mais útil.
O objetivo principal da revisão de código é ter a melhor CL possível. Um
objetivo secundário é melhorar as habilidades do desenvolvedor para que ele
necessite cada vez menos de revisão.

Lembre que pessoas aprendem por reforço do que eles estão fazendo bem e não só o
que eles podem melhorar. Se você ver coisas que goste em uma CL, comente isso
também! Exemplos: desenvolvedor limpou um algoritmo bagunçado, fez uma cobertura
de testes exemplar, ou você como revisor aprendeu algo com a CL. Assim como
qualquer comentário, inclua [porquê](#why) você gostou de algo, encorajando o
desenvolvedor a continuar boas práticas.

## Aceitando Explicações {#explanations}

Se você pedir para um desenvolvedor explicar um pedaço de código que você não
entende, isso geralmente resulta em ele **reescrever o código mais claramente**.
Ocasionalmente, adicionar comentários no código também é uma resposta
apropriada, desde que isso não está apenas explicando um código complexo demais.

**Explicações escritas apenas em uma ferramenta de revisão de código não são
úteis para futuros leitores do código.** Elas são aceitas apenas em poucas
circunstâncias, como quando você está revisando uma área que você não tem muita
familiaridade e o desenvolvedor explica algo que leitores comuns do código
geralmente já saberiam.

Próximo: [Lidando com objeções na Revisão de Código](pushback.md)
