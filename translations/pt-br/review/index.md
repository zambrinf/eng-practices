# Guia de Revisão De Código Para Desenvolvedores

## Introdução {#intro}

Revisão de código é o processo que alguém além do(s) autor(es) de um pedaço de
código examina aquele código.

Na Google, nós usamos a revisão de código para manter a qualidade do nosso
código e produtos.

Essa documentação é a descrição canônica dos processos e políticas de revisão de
código da Google.

Essa página é um resumo do nosso processo de revisão de código. Existem outros
dois grandes documentos que são parte desse guia:

- **[Como Fazer Uma Revisão de Código](./reviewer/index.md)**: Um guia detalhado
  para o revisor de código.
- **[O Guia Do Autor da CL](./developer/index.md)**: Um guia detalhado para os
  desenvolvedores cujas CLs estão passando por revisão.

## O Que Revisores De Código Buscam? {#look_for}

Revisores de código devem buscar:

- **Design**: O código foi bem desenvolvido e é apropriado para o seu sistema?
- **Funcionalidade**: O código se comporta como a intenção do autor? O código se
  comporta bem para os seus usuários?
- **Complexidade**: O código pode ser mais simples? Outro desenvolvedor vai ser
  capaz de entender e usar facilmente esse código no futuro?
- **Testes**: O código tem testes automatizados corretos e bem desenvolvidos?
- **Nomenclatura**: O desenvolvedor escolheu nomes claros para variáveis,
  classes, métodos, etc.?
- **Comentários**: Os comentários são claros e úteis?
- **Estilo**: O código segue nossas
  [diretrizes de estilo](http://google.github.io/styleguide/)?
- **Documentação**: O desenvolvedor também atualizou as documentações
  relevantes?

Veja **[Como Fazer Uma Revisão de Código](./reviewer/index.md)** para mais
informações.

### Escolhendo Os Melhores Revisores {#best_reviewers}

Em geral, você vai querer achar os _melhores_ revisores que puder que serão
capazes de responder à sua revisão dentro de um período razoável de tempo.

O melhor revisor é aquele que poderá revisar de maneira minuciosa e correta o
pedaço de código que você está escrevendo. Isso geralmente significa o(s)
dono(s) do código, que podem ou não ser as pessoas do arquivo de donos. Algumas
vezes isso significa pedir para diferentes pessoas revisarem diferentes partes
da CL.

Se uma pessoa ideal não estiver disponível, você pode pelo menos colocá-la em
cópia na sua alteração.

### Revisão Presencial (e Pair Programming) {#in_person}

Se você fez pair-programming em um pedaço de código com uma pessoa que é
qualificada para fazer uma boa revisão de código nele, então aquele pedaço de
código é considerado revisado.

Você também pode fazer revisão de código presencialmente onde o revisor faz
perguntas e o desenvolvedor da alteração apenas fala quando é solicitado.

## Veja Também {#seealso}

- [Como Fazer Uma Revisão de Código](./reviewer/index.md): Um guia detalhado
  para o revisor de código.
- [O Guia Do Autor da CL](./developer/index.md): Um guia detalhado para os
  desenvolvedores cujas CLs estão passando por revisão.
