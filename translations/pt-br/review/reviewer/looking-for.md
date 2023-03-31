# O que buscar em uma revisão de código

Obs: Garanta que sempre levará em consideração
[O Padrão de Revisão de Código](standard.md) quando observar cada um desses
pontos.

## Design

O mais importante para verificar em uma revisão é o design geral da CL. As
interações entre as várias partes do código da CL fazem sentido? Isso pertence à
sua base de código, ou a uma biblioteca? É bem integrada com o restante do
sistema? Agora é uma boa hora para adicionar essa funcionalidade?

## Funcionalidade

A CL faz o que o desenvolvedor pretende? O que o desenvolvedor pretende é bom
para os usuários desse código? Os "usuários" são geralmente tanto os usuários
finais (quando eles são afetados pela mudança) e os desenvolvedores (que
precisarão "usar" esse código no futuro).

Geralmente, esperamos que os desenvolvedores testem as CLs bem o suficiente tal
que no momento da revisão de código tudo esteja funcionando corretamente.
Entretanto, enquanto revisor você deve pensar em casos mais amplos, procurar
problemas de concorrência, tentar pensar como um usuário, e garantir que não há
bugs que você veja somente lendo o código.

Você _pode_ validar uma CL se você quiser - o momento mais importante para um
revisor testar o comportamento da CL é quando ela tem impacto visual ao usuário,
como **mudanças na UI**. É difícil pensar em como as mudanças vão impactar o
usuário somente lendo o código. Para mudanças assim, você pode pedir para o
desenvolvedor demonstrar a funcionalidade se for muito incoveniente entrar na CL
e testar por conta própria.

Outra momento que é importante pensar sobre a funcionalidade durante uma revisão
de código é quando existe algum tipo de **programação paralela** acontecendo na
CL que teoricamente poderia causar deadlocks e condições de corrida. Esses tipos
de problemas são muito difíceis de detectar ao simplesmente rodar o código, e
geralmente necessita que alguém (tanto o desenvolvedor como o revisor) pense
nelas com cuidado para garantir que não existem problemas sendo introduzidos.
(Observe que iso é uma boa razão para não usar modelos de concorrência onde
condições de corrida ou deadlocks são possíveis - pode ser muito complexo para
revisar ou entender o código)

## Complexidade

A CL é mais complexa do que deveria ser? Verifique isso em todos os níveis da
CL - existem linhas individuais muito complexas? Existem funções muito
complexas? Existem classes muito complexas? "Muito complexas" geralmente
significa **"não pode ser entendida rapidamente por leitores do código".**
Também pode significar **"desenvolvedores provavelmente vão introduzir bugs
quando tentarem chamar ou modificar esse código"**.

Um tipo particular de complexidade é o **over-engineering**, onde
desenvolvedores fizeram o código mais genérico do que era necessário, ou
adicionaram funcionalidades que não são necessárias atualmente pelo sistema.
Revisores devem estar especialmente vigilantes para over-engineering. Encoraje
desenvolvedores a resolver problemas que eles sabem que precisam ser resolvidos
_agora_, não problemas que o desenvolvedor especula que _podem_ precisar serem
resolvidos no futuro. O problema futuro deve ser resolvido quando você puder ver
sua real forma e seus requisitos.

## Testes

Peça por testes unitários, de integração, ou end-to-end conforme for apropriado
para a alteração. Em geral, testes devem ser adicionados na mesma CL que o
código de produção a não ser que a CL esteja resolvendo uma
[emergência](../emergencies.md).

Garanta que os testes na CL estão corretos, sensatos e úteis. Testes não testam
eles mesmos, e raramente escrevemos testes para nossos testes - um humano deve
garantir que os testes são válidos.

O teste vai realmente falhar quando o código quebrar? Se o código sofrer
alteração, eles podem produzir falsos positivos? Cada teste faz uma simples e
útil verificação? Os testes são separados apropriadamente entre diferentes
métodos de teste?

Lembre que testes também são código e precisam de manutenção. Não aceite
complexidade em testes só porque eles não fazem parte do código principal.

## Nomenclatura

O desenvolvedor escolheu bons nomes para tudo? Um bom nome é bom o suficiente
para comunicar o que o item é ou faz, sem ser tão longo que fica difícil de ler.

## Comentários

O desenvolvedor escreveu comentários claros em Português compreensível? Todos os
comentários são realmente necessários? Geralmente comentários são úteis quando
explicam **porquê** um código existe, e não _o que_ o código está fazendo. Se o
código não está claro o suficiente para explicar a si mesmo, então o código deve
ser simplificado. Há algumas exceções (expressões regulares e algoritmos
complexos geralmente se beneficiam de comentários que explicam o que eles fazem,
por exemplo), mas a maioria dos comentários devem ser para informações que o
código por si não contém, como a razão por trás de uma decisão.

Também é bom olhar comentários que estavam lá antes da CL. Talvez exista um
comentário TODO que pode ser removido agora, um comentário aconselhando a não
fazer essa alteração, etc.

Observe que comentários são diferentes de _documentação_ de classes, módulos, ou
funções, essa deve expressar o motivo de um pedaço de código, como deve ser
usado, e como se comporta quando usado.

## Estilo

Nós temos [guias de estilo](http://google.github.io/styleguide/) na Google para
todas nossas principais linguagens, e até para as menos importantes. Garanta que
a CL siga o guia de estilo apropriado.

Se você quer melhorar um ponto de estilo que não está no guia de estilo, coloque
um prefixo "Nit: " no seu comentário para o desenvolvedor saber que é uma
observação detalhista (nitpick) que você acha que pode melhorar o código mas não
é obrigatório. Não bloqueie CLs de serem enviadas baseadas somente em
preferências pessoais de estilo.

O autor da CL não deve incluir mudanças grandes de estilo combinadas com outras
mudanças. Isso torna difícil de ver o que está sendo alterado na CL, faz merges
e rollbacks ficarem mais complexos, e causam outros problemas. Por exemplo, se
um autor quer reformatar um arquivo inteiro, faça-o enviar outra CL apenas com
as alterações funcionais após isso.

## Consistência

E se o código for inconsistente com o guia de estilo? Pelos nossos
[princípios de revisão de código](standard.md#principles), o guia de estilo é
autoridade absoluta: se alguma coisa é um requisito do guia de estilo, a CL deve
seguir as orientações.

Em alguns casos, o guia de estilo faz recomendações ao invés de declarar
requisitos. Nesses casos, utilize o bom senso se o novo código deve seguir as
recomendações ou o código ao redor dele. Tenda a seguir o guia de estilo a não
ser que cause uma inconsistência local e fique muito confusa.

Se nenhuma outra regra se aplica, o autor deve manter a consistência com o
código que já existe.

De qualquer forma, encoraje o autor a documentar um bug e adicionar um TODO para
limpar o código existente.

## Documentação

Se uma CL muda como um usuário builda, testa, interage, ou libera código,
verifique se ela também atualiza a documentação associada, incluindo LEIAMEs,
páginas g3doc, e qualquer documentação de referência gerada. Se a CL exclui ou
deprecia código, considere se a documentação também deve ser deletada. Se a
documentação está faltando, solicite-a.

## Todas linhas {#every-line}

Em geral, olhe _todas_ linhas de código que você foi designado a revisar.
Algumas coisas como arquivos de dados, código gerado, ou grandes estruturas de
dados você pode olhar por cima algumas vezes, mas não olhe por cima de classe,
função ou bloco de código escrito por um humano e assuma o que tem dentro está
certo. Obviamente alguns códigos merecem um exame mais minucioso do que outros -
é uma escolha que você precisa fazer - mas você deve pelo menos _entender_ o que
o código todo está fazendo.

Se você perceber que está difícil demais para ler o código e isso está deixando
a revisão lenta, então você deve avisar o desenvolvedor sobre isso e esperar que
ele esclareça o código antes de você tentar revisá-lo. Na Google, nós
contratamos ótimos engenheiros de software, e você é um deles. Se você não
consegue entender o código, é muito provável que outros desenvolvedores também
não. Portanto você também está ajudando futuros desenvolvedores a entender esse
código quando você pede ao desenvolvedor para esclarecê-lo.

Se você entende o código mas não se sente qualificado para fazer alguma parte da
revisão, [garanta que exista um revisor](#every-line-exceptions) na CL que é
qualificado, particularmente para casos complexos como privacidade, segurança,
concorrência, acessibilidade, intercionalização, etc.

### Exceções {#every-line-exceptions}

E se não fizer sentido para você revisar todas as linhas? Por exemplo, você é um
de múltiplos revisores numa CL e pode ser solicitado:

- Revisar somente alguns arquivos que são parte de uma alteração maior.
- Revisar somente certos aspectos da CL, como o design de alto nível,
  privacidade ou implicações de segurança, etc.

Nesses casos, anote em um comentário quais partes você revisou. Prefira dar um
[LGTM com comentários](speed.md#lgtm-with-comments).

Se ao invés você preferir dar o LGTM depois de confirmar que outros revisores
revisaram outras partes da CL, anote isso explicitamente em um comentário para
definir expectativas. Tente [responder rapidamente](speed.md#responses) assim
que a CL alcançou o estado desejado.

## Contexto

Geralmente é útil olhar a CL em um contexto mais amplo. As ferramentas de
revisão de código na maioria das vezes vão lhe mostrar somente algumas linhas de
código ao redor das partes que foram alteradas. Às vezes você precisa olhar o
arquivo todo para garantir que a mudança faz sentido. Por exemplo, você pode ver
que apenas quatro novas linhas foram adicionadas, mas quando você olha o arquivo
todo, você vê que as quatro linhas estão em um método de 50 linhas que agora
precisa ser quebrado em métodos menores.

Também é útil pensar a CL no contexto do sistema como um todo. A CL está
melhorando a saúde do código do sistema ou está deixando o sistema todo mais
complexo, menos testado, etc? **Não aceite CLs que pioram a saúde do código do
sistema.** A maioria dos sistemas ficam complexos através de pequenas mudanças
que se somam, então é importante prevenir até mesmo essas pequenas complexidades
em novas alterações.

## Coisas Boas {#good-things}

Se você ver algo legal em uma CL, fale ao desenvolvedor, especialmente quando
eles resolveram um dos seus comentários de maneira ótima. Revisões de código
geralmente só focam em erros, mas elas podem oferecer apreço e encorajar boas
práticas também. Às vezes é até mais valioso, em termos de mentoria, falar a um
desenvolvedor o que ele fez certo do que o que ele fez errado.

## Resumo

Em uma revisão de código, você deve garantir que:

- O código tem um bom design.
- A funcionalidade é boa para os usuários do código.
- Qualquer mudança na UI é sansata e parece bonita.
- Qualquer programação paralela é feita com segurança.
- O código não é mais complexo do que o necessário.
- O desenvolvedor não está implementando coisas que ele _pode_ precisar no
  futuro mas ele sabe que não vai precisar agora.
- O código tem testes unitários apropriados.
- Os testes são bem desenvolvidos.
- O desenvolvedor usou nomes claros para tudo.
- Comentários são claros e úteis, e em geral explicam _porquê_ ao invés de _o
  que_.
- O código é apropriadamente documentado (geralmente em g3doc).
- O código segue os guias de estilo.

Garanta revisar **toda linha** de código que você foi solicitado a revisar, olhe
o **contexto**, garanta que você está **melhorando a saúde do código**, e elogie
desenvolvedor nas **coisas boas** que ele faz.

Próxima: [Navegando uma CL em Revisão](navigate.md)
