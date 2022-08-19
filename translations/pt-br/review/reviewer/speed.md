# Velocidade das Revisões de Código

## Por Que As Revisões De Código Devem Ser Rápidas? {#why}

**Na Google, nós otimizamos a velocidade em que cada time de desenvolvedores
podem produzir um produto juntos**, ao invés de otimizar a velocidade que cada
desenvolvedor escreve código. A velocidade do desenvolvimento individual é
importante, só não é _tão_ importante quanto a velocidade do time todo.

Quando revisões de código são lentas, diversas coisas acontecem:

- **A velocidade do time como um todo cai**. Sim, o indivíduo que não responde
  rapidamente às revisões faz outro trabalho. Entretanto, novas funcionalidades
  e correções de bugs para o restante do time são atrasadas por dias, semanas,
  ou meses a cada CL que espera por revisão ou re-revisão.

- **Desenvolvedores começam a reclamar do processo de revisão de código.** Se um
  revisor responde somente a cada alguns dias, mas solicita mudanças grandes na
  CL a cada vez, isso pode ser frustrante e difícil para desenvolvedores.
  Frequentemente, isso é expressado através de reclamações de quão "rigoroso" o
  revisor está sendo. Se o revisor pedir as mesmas mudanças substanciais
  (mudanças que realmente melhoram a saúde do código), mas responder rapidamente
  todas as vezes que o desenvolvedor faz uma atualização, essas reclamações
  tendem a desaparecer. **A maioria das reclamações sobre o processo de revisão
  de código são geralmente resolvidas fazendo o processo ficar mais rápido**.

- **A saúde do código pode ser impactada**. Quando as revisões são lentas,
  existe um aumento de pressão para permitir desenvolvedores enviar CLs que não
  são tão boas quanto poderiam ser. Revisões lentas também desencorajam
  limpezas, refatorações, e outras melhorias para a CL atual.

## Quão rápidas as revisões de código precisam ser? {#fast}

Se você não estiver focado no meio de uma tarefa, **você deve fazer uma revisão
de código assim que ela chega**.

**Um dia útil é o máximo de tempo que deve levar para responder** a uma revisão
de código (isto é, a primeira coisa a se fazer na próxima manhã).

Seguir essas instruções significa que uma CL típica deve ter múltiplas rodadas
de revisão (se necessário) durante um único dia.

## Velocidade vs. Interrupção {#interruption}

Existe apenas um caso que levar em consideração a velocidade pessoal supera a
velocidade do time. **Se você estiver no meio de uma tarefa que requer foco,
como escrevendo código, não interrompa a si mesmo para fazer revisão de
código.** Pesquisas mostram que demora um longo tempo para o desenvolvedor
voltar a um fluxo de desenvolvimento regular após ser interrompido. Então
interromper a si mesmo enquanto estiver codando é na verdade _mais_ caro ao time
do que fazer o outro desenvolvedor esperar um pouco por uma revisão de código.

Ao invés disso, espere por uma pausa no seu trabalho antes de responder a uma
requisição de revisão. Isso pode significar quando sua tarefa de código estiver
completa, depois do almoço, voltando de uma reunião, voltando do banheiro, etc.

## Respostas Rápidas {#responses}

Quando falamos da velocidade da revisão de código, é sobre o tempo de _resposta_
que estamos preocupados, ao invés de quanto tempo a CL leva durante todo o
processo de revisão e submissão. O processo todo também deve ser rápido,
idealmente, mas **é ainda mais importante que cada _resposta individual_ seja
rápida do que todo o processo aconteça rapidamente**.

Mesmo que algumas vezes leve um longo tempo para passar por todo o _processo_ de
revisão, ter respostas rápidas do revisor ao longo do processo alivia a
frustração que desenvolvedores têm com revisões "lentas".

Se você está muito ocupado para fazer uma revisão completa quando chega uma CL,
você ainda pode enviar uma resposta rápida para o desenvolvedor falando quando
você vai vê-la, ou sugerir outros revisores que podem estar disponíveis a
fazerem a revisão mais rapidamente, ou
[dar alguns comentários gerais iniciais](navigate.md). (Obs: nada disso
significa que você deve interromper a programação mesmo que seja para responder
dessa forma - envie a resposta em uma pausa do seu trabalho.)

**É importante que revisores gastem tempo o suficiente em uma revisão para que
eles estejam certos que seu "LGTM" significa "esse código segue
[nossos padrões](standard.md)."** Entretanto, respostas individuais idealmente
ainda precisam ser [rápidas](#fast).

## Revisões em fusos horários diferentes {#tz}

Quando lidando com diferenças de fusos horários, tente dar resposta ao autor
enquanto ele tem tempo de resolver antes do final do horário de trabalho dele.
Se ele já terminou o trabalho do dia, tente garantir que sua revisão esteja
pronta antes do início do trabalho dele do próximo dia.

## LGTM com comentários {#lgtm-with-comments}

Para acelerar as revisões, há certas situação que o revisor deve dar o
LGTM/Aprovação mesmo que ele está deixando comentários não resolvidos na CL.
Isso é feito quando:

- O revisor está confiante que o desenvolvedor vai resolver os comentários do
  revisor apropriadamente.
- As mudanças remanescentes são de pouca importância e _não têm_ que serem
  resolvidas pelo desenvolvedor.

O revisor deve especificar qual dessas opções ele quis dizer, se não ficou
claro.

LGTM com comentários deve ser especialmente considerado quando o desenvolvedor e
o revisor estão em diferentes fusos horários e o desenvolvedor ficaria esperando
por um dia inteiro só para conseguir um "LGTM, aprovado".

## CLs Grandes {#large}

Se alguém lhe enviar uma CL que é tão grande que você não tem certeza quando
terá tempo para revisá-la, sua resposta típica pode ser pedir ao desenvolvedor
para [dividir a CL em várias CLs menores](../developer/small-cls.md) que são
construídas sequencialmente, ao invés de uma CL gigante que precisa ser revisada
de uma vez. Isso geralmente é possível e ajuda os revisores, mesmo que dê
trabalho adicional ao desenvolvedor.

Se uma CL _não pode_ ser quebrada em CLs menores, e você não tem tempo para
revisar tudo rapidamente, pelo menos escreva alguns comentários sobre o design
geral da CL e envie para o desenvolvedor. Um dos objetivos como revisor é sempre
tentar destravar o desenvolvedor ou permitir que ele tome alguma atitude
rapidamente, sem sacrificar a qualidade do código para isso.

## Melhorias da Revisão de Código com o Tempo {#time}

Se você seguir essas orientações e você é exigente com suas revisões de código,
você provavelmente vai perceber que o processo inteiro de revisão de código
tende a ir cada vez mais rápido com o tempo. Desenvolvedores aprendem o que é
necessário para um código mais limpo, e enviam CLs que são ótimas desde o
início, necessitando menos tempo de revisão. Revisores aprendem a responder
rapidamente e não adicionar latência desnecessária no processo de revisão. Mas
**não comprometa os [padrões de revisão de código](standard.md) ou a qualidade
por uma melhoria da velocidade** - isso não vai fazer nada acontecer mais
rapidamente no longo prazo.

## Emergências

Também há [emergências](../emergencies.md) onde a CL deve passar por _todo_ o
processo de revisão muito rapidamente, e onde as exigências de qualidade podem
ser relaxadas. Porém, por favor veja
[O que é uma emergência?](../emergencies.md#what) para uma descrição de quais
situações se qualificam como emergências e quais não.

Próxima: [Como escrever comentários de Revisão de Código](comments.md)
