# Emergências

Algumas vezes existem CLs emergenciais que precisam passar pelo processo de
revisão de código o mais rápido possivel.

## O Que É Uma Emergência? {#what}

Uma CL emergencial pode ser uma **pequena** alteração que: permite um grande
lançamento continuar ao invés de ser revertido, conserta um bug que está
afetando significativamente os usuários em produção, lida com uma questão legal
urgente, fecha uma grande brecha de segurança, etc.

Em emergências nós realmente nos preocupamos com a velocidade de todo o processo
de revisão de código, não somente a
[velocidade de resposta](./reviewer/speed.md). _Somente_ neste caso, o revisor
deve se preocupar mais com a velocidade da revisão e a corretude do código (isso
realmente resolve a emergência?) do que qualquer outra coisa. Além disso
(provavelmente obviamente) essas revisões devem ter prioridade sobre outras
revisões de código, quando elas chegarem.

Entretanto, após a emergência ser resolvida você deve olhar novamente as CLs
emergenciais e [revisá-las minuciosamente](./reviewer/looking-for.md).

## O Que NÃO É Uma Emergência? {#not}

Para deixar claro, os seguintes casos _não_ são emergências:

- Querer lançar essa semana ao invés da semana seguinte (a não ser que haja um
  [prazo rígido](#deadlines))
- O desenvolvedor trabalhou em uma funcionalidade por um longo período e ele
  quer muito essa CL para dentro.
- Os revisores são todos de outro fuso horário onde neste momento é noite ou
  eles estão ausentes fora do local.
- É final do dia numa sexta-feira e seria ótimo essa CL pra dentro antes de o
  desenvolvedor sair para o fim-de-semana.
- Um gerente diz que a revisão precisar estar completa e a CL dentro ainda hoje
  por causa de um [prazo flexível (não rígido)](#deadlines)
- Reverter uma CL que está causando falhas nos testes ou quebrando a build.

E assim por diante.

## O que é um prazo rígido? {#deadlines}

Um prazo rígido é quando **algo desastroso pode acontecer** se você perdê-lo.
Por exemplo:

- Enviar sua CL até uma determinada data é necessário por obrigação contratual.
- Seu produto vai falhar completamente se não for liberado até certa data.
- Alguns fabricantes de hardware enviam novos hardwares apenas uma vez por ano.
  Se você perder o prazo para enviar o código a eles, pode ser desastroso,
  dependendo do tipo de código que você está tentando enviar.

Atrasar uma release por uma semana não é desastroso. Perder uma reunião
importante pode ser desastroso, mas geralmente não é.

A maioria dos prazos são flexíveis, não rígidos. Eles representam um desejo para
a funcionalidade estar pronta até certa data. Eles são importantes, mas você não
deve sacrificar a saúde do código para mantê-los.

Se você tem longos ciclos de release (várias semanas) pode ser tentador
sacrificar a qualidade da revisão de código para uma funcionalidade estar no
próximo ciclo. Entretanto, esse padrão, se repetido, é uma forma comum de
projetos apresentarem dívida técnica muito pesada. Se os desenvolvedores
rotineiramente estão enviando CLs perto do fim do ciclo elas "devem entrar" com
revisões superficiais, então o time pode midificar o processo para que grandes
mudanças aconteçam cedo no ciclo e tenham tempo suficiente para uma boa revisão.
