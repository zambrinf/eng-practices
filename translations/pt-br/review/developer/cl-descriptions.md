# Escrevendo boas descrições de CL

A descrição da CL é um registro público de **qual** alteração está sendo feita e
**porquê** foi feita. Ela vai se tornar parte permanente do nosso histórico de
controle de versão, e vai possivelmente ser lida por centenas de pessoas além de
seus revisores durante os anos.

Futuros Desenvolvedores vão buscar por sua CL baseados em sua descrição. Alguém
no futuro pode estar buscando por sua alteração por uma leve memória da sua
relevância mas sem ter os detalhes à mão. Se toda informação importante está no
código e não na descrição, vai ser muito mais difícil para eles localizarem sua
CL.

## Primeira Linha {#firstline}

- Pequeno resumo do que está sendo feito.
- Sentença completa, escrita como se fosse uma ordem.
- Seguida por uma linha vazia.

A **primeira linha** de uma descrição de CL deve ser um pequeno resumo de **o
que** _especificamente está sendo feito pela CL_, seguido por uma linha em
branco. Isso é o que aparecerá no histórico dos resumos do controle de versão,
então deve ser informativa o suficiente para que futuras pessoas que buscarem o
código não precisem ler a CL ou toda a sua descrição para entender o que a CL
realmente _fez_ ou o que a diferencia de outras CLs. Isto é, a primeira linha
deve ser independente, permitindo leitores passar pelo histórico muito mais
rápido.

Tente manter sua primeira linha pequena, focada, e direto ao ponto. A clareza e
utilidade ao leitor deve ser a principal preocupação.

Por tradição, a primeira linha da CL é uma sentença completa, escrita como se
fosse uma ordem (uma sentença imperativa). Por exemplo, diga \"**Excluir** o RPC
FizzBuzz e **substituir** com o novo sistema." No entendo, você não precisa
escrever o restante da descrição como uma sentença imperativa.

## O corpo é informativo {#informative}

A [primeira linha](#firstline) deve ser um pequeno e focado resumo, enquanto o
restante da descrição deve preencher os detalhes e incluir qualquer informação
adicional que um leitor necessita para entender a alteração holisticamente. Deve
incluir uma breve descrição do problema que está sendo resolvido, e porquê essa
foi a melhor abordagem. Se existe alguma deficiência nessa abordagem, elas devem
ser mencionadas. Se relevante, inclua informações básicas como números de bugs,
resultados de benchmark, e links para documentos de design.

Se você incluir links para recursos externos considera que eles podem não ser
visíveis para futuros leitores por restrições de acesso ou políticas de
retenção. Onde possível inclua contexto o suficiente para revisores e futuros
leitores entenderem a CL.

Mesmo pequenas CL merecem uma pequena atenção aos detalhes. Coloque a CL no
contexto.

## Descrições ruims de CL {#bad}

"Ajustar bug" é uma descrição inadequada de CL. Qual bug? O que você fez para
arrumar? Outras descrições ruins incluem:

- "Ajustar build."
- "Adiciona patch."
- "Movendo código de A para B."
- "Fase 1."
- "Adicionar funções convenientes."
- "Removendo URLs estranhas."

Algumas dessas são descrições reais de CLs. Embora pequenas, elas não dão
informação útil o suficiente.

## Boas descrições de CL {#good}

Aqui estão algumas descrições boas:

### Alteração de funcionalidade

Exemplo:

> rpc: remover o limite de tamanho da lista de mensagens no servidor RPC
>
> Servidores como FizzBuzz tem grandes mensagens que podem se beneficiar de
> reúso. Fazer a lista maior, e adicionar uma goroutine que vagorasamente limpa
> as entradas da lista através do tempo, assim servidores parados eventualmente
> liberam toda a sua lista de entradas

As primeira palavras descrevem o que a CL realmente faz. O restante da descrição
fala sobre o problema sendo resolvido, porque essa é uma boa solução, e um pouco
mais de informação específica sobre a implementação.

### Refatorando

Exemplo:

> Construir uma Task com um TimeKeeper que usa seus métodos TimeStr e Now.
>
> Adicionar um método Now em Task, assim o método getter borglet() pode ser
> removido (que somente era usado pelo OOMCandidate para chamar o método Now do
> borglet). Isso substitui os métodos em Borglet e delega para um TimeKeeper.
>
> Permitindo que Tasks suportem Now é um passo para eliminar a dependência do
> Borglet. Enventualmente, colaboradores que dependam de pegar o Now da Task
> devem alterar para usar o TimeKeeper diretamente, mas isso é uma refatoração
> em pequenos passos.
>
> Continuando a meta de longo prazo de refatoração da Hierarquia Borglet.

A primeira linha descreve o que a CL faz e como isso foi alterado. O restante da
descrição fala sobre a implementação específica, o contexto da CL, que a solução
não é ideal, e possíveis futuras direções. Também explica _porquê_ a mudança
está sendo feita.

### CL pequena que precisa de contexto

Exemplo:

> Criar uma regra de build de Python3 para status.py
>
> Isso permite que os usuários que já estão usando o Python3 possam depender de
> uma regra próxima à regra de build original do status, em vez de em algum
> lugar em sua própria árvore. Isso incentiva novos usuários a utilizarem o
> Python3, se possível, em vez do Python2, e simplifica significativamente
> algumas ferramentas automatizadas de refatoração de arquivos de build que
> estão sendo desenvolvidas atualmente.

A primeira frase descreve o que está sendo feito de fato. O restante da
descrição explica o _motivo_ da mudança e fornece ao revisor um contexto
detalhado.

## Descrições de CL geradas automaticamente

Alguns CLs são gerados por ferramentas. Sempre que possível, suas descrições
também devem seguir os conselhos apresentados aqui. Ou seja, a primeira linha
deve ser curta, focada e independente, e o corpo da descrição do CL deve incluir
detalhes informativos que ajudem os revisores e futuros pesquisadores de código
a entender o efeito de cada CL.

## Revisar a descrição antes de enviar o CL

Os CLs podem passar por mudanças significativas durante a revisão. Vale a pena
revisar a descrição de um CL antes de enviá-lo, para garantir que ela ainda
reflita o que o CL faz.

Próximo: [CLs pequenos](small-cls.md)
