# CLs Pequenos

## Por que Escrever CLs Pequenos? {#why}

CLs pequenos e simples são:

- **Revisados mais rapidamente**. É mais fácil para um revisor encontrar cinco
  minutos várias vezes para revisar CLs pequenos do que reservar 30 minutos para
  revisar uma CL grande.
- **Revisados de forma mais completa**. Com mudanças grandes, revisores e
  autores tendem a ficar frustrados com grandes volumes de comentários
  detalhados indo e vindo - às vezes a ponto de pontos importantes serem
  ignorados ou perdidos.
- **Menos propensos a introduzir bugs**. Como você está fazendo menos
  alterações, é mais fácil para você e seu revisor raciocinarem efetivamente
  sobre o impacto da CL e ver se um bug foi introduzido.
- **Menos trabalho desperdiçado se forem rejeitados**. Se você escrever uma CL
  enorme e o revisor disser que a direção geral está errada, você desperdiçou
  muito trabalho.
- **Mais fácil de mesclar**. Trabalhar em uma CL grande leva muito tempo, então
  você terá muitos conflitos quando mesclar e precisará mesclar frequentemente.
- **Mais fácil de projetar adequadamente**. É muito mais fácil aprimorar o
  design e a saúde do código em uma pequena alteração do que refinar todos os
  detalhes de uma alteração grande.
- **Menos bloqueio nas revisões**. Enviar partes autocontidas da sua alteração
  geral permite que você continue codificando enquanto aguarda a revisão da sua
  CL atual.
- **Mais simples de reverter.** Uma CL grande provavelmente afetará arquivos que
  são atualizados entre a submissão inicial da CL e uma CL de reversão,
  complicando a reversão (as CLs intermediárias também provavelmente precisarão
  ser revertidas).

Observe que **os revisores têm a discrição de rejeitar sua alteração totalmente
pelo simples motivo de ser muito grande**. Geralmente, eles vão agradecer pela
sua contribuição, mas solicitar que você a divida em uma série de alterações
menores. Pode dar muito trabalho dividir uma alteração depois de já tê-la
escrito, ou pode exigir muito tempo argumentar sobre por que o revisor deveria
aceitar sua grande alteração. É mais fácil escrever CLs pequenos desde o início.

## O que é Pequeno? {#what_is_small}

Em geral, o tamanho certo para uma CL é **uma alteração autocontida**. Isso
significa que:

- A CL faz uma alteração mínima que aborda **apenas uma coisa**. Geralmente é
  apenas uma parte de um recurso, em vez de todo o recurso de uma vez. Em geral,
  é melhor optar por escrever CLs que sejam pequenos demais do que CLs que sejam
  muito grandes. Trabalhe com o revisor para descobrir qual tamanho é aceitável.
- A CL deve [incluir código de teste relacionado](#test_code).
- Tudo o que o revisor precisa entender sobre a CL (exceto desenvolvimentos
  futuros) está na CL, na descrição da CL, na base de código existente ou em uma
  CL que eles já revisaram.
- O sistema continuará funcionando bem para seus usuários e desenvolvedores
  depois que a CL for enviada.
- A CL não é tão pequena a ponto de suas implicações serem difíceis de entender.
  Se você adicionar uma nova API, deve incluir o uso da API na mesma CL para que
  os revisores possam entender melhor como a API será utilizada. Isso também
  evita a inclusão de APIs não utilizadas.

Não há regras rígidas e rápidas sobre o tamanho "muito grande". 100 linhas
geralmente é um tamanho razoável para uma CL, e 1000 linhas geralmente é muito
grande, mas isso fica a critério do seu revisor. O número de arquivos que uma
alteração abrange também afeta seu "tamanho". Uma alteração de 200 linhas em um
arquivo pode ser aceitável, mas distribuída em 50 arquivos, geralmente será
muito grande.

Lembre-se de que, embora você esteja intimamente envolvido com seu código desde
o momento em que começou a escrevê-lo, o revisor geralmente não tem contexto. O
que parece uma CL de tamanho aceitável para você pode ser esmagador para o
revisor. Quando estiver em dúvida, escreva CLs menores do que você acredita ser
necessário. Revisores raramente reclamam de receber CLs que são muito pequenas.

## Quando as Grandes CLs São Aceitáveis? {#large_okay}

Existem algumas situações em que mudanças grandes não são tão ruins:

- Geralmente, a exclusão de um arquivo inteiro pode ser considerada como apenas
  uma linha de alteração, pois não leva muito tempo para o revisor revisar.
- Às vezes, uma CL grande foi gerada por uma ferramenta de refatoração
  automática na qual você confia completamente, e o trabalho do revisor é apenas
  verificar e confirmar que eles realmente desejam a alteração. Essas CLs podem
  ser maiores, embora algumas das ressalvas acima (como mesclagem e testes)
  ainda se apliquem.

### Divisão por Arquivos {#splitting-files}

Outra maneira de dividir uma CL é por grupos de arquivos que exigirão revisores
diferentes, mas que são alterações autocontidas.

Por exemplo: você envia uma CL para modificações em um protocolo de buffer e
outra CL para alterações no código que usa esse protótipo. Você precisa enviar a
CL do protótipo antes da CL do código, mas ambas podem ser revisadas
simultaneamente. Se você fizer isso, talvez queira informar a ambos os grupos de
revisores sobre a outra CL que você escreveu, para que eles tenham contexto para
suas alterações.

Outro exemplo: você envia uma CL para uma alteração de código e outra para a
configuração ou experimento que usa esse código; isso é mais fácil de reverter
também, se necessário, já que arquivos de configuração/experimento são às vezes
enviados para a produção mais rapidamente do que as alterações de código.

## Separe as Refatorações {#refactoring}

Geralmente, é melhor fazer refatorações em uma CL separada das alterações de
recursos ou correções de bugs. Por exemplo, mover e renomear uma classe deve
estar em uma CL diferente da correção de um bug nessa classe. É muito mais fácil
para os revisores entenderem as alterações introduzidas por cada CL quando elas
são separadas.

Pequenas limpezas, como corrigir o nome de uma variável local, podem ser
incluídas dentro de uma CL de recurso ou correção de bug. Isso fica a critério
dos desenvolvedores e revisores decidirem quando uma refatoração é tão grande
que dificultará a revisão se incluída na sua CL atual.

## Mantenha o Código de Teste Relacionado na Mesma CL {#test_code}

CLs devem incluir código de teste relacionado. Lembre-se de que
[pequenez](#what_is_small) aqui se refere à ideia conceitual de que a CL deve
ser focada e não é uma função simplista na contagem de linhas.

Uma CL que adiciona ou altera lógica deve ser acompanhada por testes novos ou
atualizados para o novo comportamento. CLs de refatoração pura (que não têm a
intenção de alterar o comportamento) também devem ser cobertas por testes;
idealmente, esses testes já existem, mas se não existirem, você deve
adicioná-los.

Modificações de teste independentes podem ser enviadas em CLs separados
primeiro, assim como as [diretrizes de refatoração](#refactoring). Isso inclui:

- Validar código já existente e enviado com novos testes.
- Garante que a lógica importante é coberta por testes.
- Aumenta a confiança em refatorações subsequentes no código afetado. Por
  exemplo, se você deseja refatorar um código que ainda não é coberto por
  testes, enviar CLs de teste antes de enviar CLs de refatoração pode validar
  que o comportamento testado não foi alterado antes e depois da refatoração.
- Refatorar o código de teste (por exemplo, introduzir funções auxiliares).
- Introduzir códigos de estrutura de teste maiores (por exemplo, um teste de
  integração).

## Não Quebre a Compilação {#break}

Se você tiver várias CLs que dependem umas das outras, precisará encontrar uma
maneira de garantir que o sistema inteiro continue funcionando após cada
submissão da CL. Caso contrário, você pode quebrar a compilação para todos os
seus colegas desenvolvedores por alguns minutos entre as submissões das suas CLs
(ou até mais tempo se algo der errado inesperadamente com suas submissões
posteriores da CL).

## Não é Possível Deixá-lo Pequeno o Suficiente? {#cant}

Às vezes, você se deparará com situações em que parece que sua CL precisa ser
grande. Isso é muito raro. Autores que praticam escrever CLs pequenos quase
sempre conseguem encontrar uma maneira de decompor a funcionalidade em uma série
de alterações pequenas.

Antes de escrever uma CL grande, considere se precedê-la com uma CL somente de
refatoração pode abrir caminho para uma implementação mais limpa. Fale com seus
colegas de equipe e veja se alguém tem ideias sobre como implementar a
funcionalidade em CLs menores.

Se todas essas opções falharem (o que deve ser extremamente raro), obtenha
consentimento de seus revisores antecipadamente para revisar uma CL grande, para
que eles sejam avisados sobre o que está por vir. Nessa situação, espere passar
muito tempo no processo de revisão, seja vigilante para não introduzir bugs e
seja extra diligente na escrita de testes.

Próximo: [Como Lidar com os Comentários do Revisor](handling-comments.md)
