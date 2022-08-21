# Lidando com objeções na Revisão de Código

De vez em quando o desenvolvedor vai contestar uma revisão de código. Ou ele vai
discordar com a sugestão ou ele vai reclamar que você está sendo exigente
demais.

## Quem está certo? {#who_is_right}

Quando um desenvolvedor discorda de alguma sugestão, primeiro dê um tempo para
considerar se ele está correto. Frequentemente, ele está mais próximo do código
do que você está, então ele pode realmente ter uma visão melhor sobre certos
aspectos. O argumento dele faz sentido? Faz sentido sobre a perspectiva de
qualidade do código? Se sim, deixe ele saber que está certo e deixe a questão
pra trás.

Entretanto, nem sempre os desenvolvedores estão certos. Nesse caso o revisor
deve explicar melhor porque ele acredita que sua sugestão está correta. Uma boa
explicação demonstra um bom entendimento da resposta do desenvolvedor, e dá
informação adicional sobre porque a mudança está sendo solicitada.

Especificamente quando o revisor acredita que sua sugestão vai melhor a
qualidade do código, ele deve continuar a defender a mudança, se ele acreditar
que a melhoria justifica o trabalho adicional. **Melhorar a qualidade do código
tende a acontecer em pequenos paços.**

Algumas vezes leva algumas rodadas de explicação da sugestão antes que ela
realmente pegue. Só garanta que você continue [educado](comments.md#courtesy) e
deixe o desenvolvedor saber que você _ouve_ o que ele está fazendo, você só não
_concorda_.

## Chateando Desenvolvedores {#upsetting_developers}

Revisores algumas vezes acreditam que podem chatear o desenvolvedor se ele
insistir numa melhoria. Às vezes o desenvolvedor realmente fica chateado, mas
isso geralmente é rápido e depois eles ficam agradecidos que você ajudou a
melhorar a qualidade do código. Usualmente, se você for
[educado](comments.md#courtesy) nos seus comentários, desenvolvedores não vão
ficar chateados, e a preocupação só está na mente do revisor. Chateações
geralmente são mais sobre
[o modo como comentários são escritos](comments.md#courtesy) do que a
insistência do revisor na qualidade do código.

## Limpando mais tarde {#later}

Uma fonte comum de objeções é que desenvolvedores (compreensivelmente) querem
fazer as coisas andarem. Eles não querem ter outra rodada de revisão para
concluir essa CL. Então eles falam que vão limpar algo em uma outra CL e você
pode dar LGTM _nessa_ CL agora. Alguns desenvolvedores são muito bons nisso, e
vão imediatamente escrever uma CL que ajusta o problema. Entretanto, a
experiência mostra que quanto mais tempo passa depois de escrever a CL original,
menos provável é de essa limpeza acontecer. Na verdade, a não ser que o
desenvolvedor faça a limpeza _imediatamente_ depois da CL atual, ela nunca vai
acontecer. Isso não é porque desenvolvedores são irresponsáveis, mas porque eles
tem muito trabalho a fazer e a limpeza se perde ou é esquecida na pressão de
outro trabalho. Portanto, geralmente é melhor insistir que o desenvolvedor limpe
a CL _agora_, antes que esteja no código base e "feito". Deixar as pessoas
"limparem depois" é um modo comum do código se degenerar.

Se uma CL introduz nova complexidade, ela deve ser limpa antes de concluída a
não ser que seja uma [emergência](../emergencies.md). Se a CL expõe problemas
circundantes que não podem ser resolvidos agora, o desenvolvedor deve reportar
um bug para a limpeza e atribuí-la a si mesmo para que não seja perdida.
Opcionalmente também pode escrever um comentário TODO no código que referencia o
bug reportado.

## Reclamações Gerais Sobre Rigor {#strictness}

Se você você fazia revisões de código mais relaxadas e depois muda para fazer
revisões mais rigorosas, alguns desenvolvedores vão reclamar muito alto.
Melhorar a [velocidade](speed.md) de sua revisão de código geralmente faz que
essas reclamações sumam.

Algumas vezes pode levar meses para que as reclamações sumam, mas eventualmente
os desenvolvedores tendem a ver o valor na rigorosidade da revisão de código
assim como o ótimo código que ela ajuda a gerar. Às vezes os que mais reclamam
viram seus maiores apoiadores quando algo faz que eles entendam o valor que você
está agregando ao ser rigoroso.

## Resolvendo Conflitos {#conflicts}

Se você está seguindo tudo acima mas ainda encontra conflitos entre você e o
desenvolvedor que não podem ser resolvidos, veja
[O Padrão de Revisão de Código](standard.md) para orientações e princípios que
ajudam a resolver os conflitos.
