# O Padrão de Revisão de Código

O principal propósito da revisão de código é garantir que a qualidade geral da
base de código da Google está melhorando com o tempo. Todas as ferramentas e
processos de revisão de código são desenvolvidas com esse fim.

Para alcançar isso, uma série de contrapartidas precisam ser balanceadas.

Primeiro, desenvolvedores precisam ser capazes de _progredir_ em suas tarefas.
Se você não enviar uma melhoria para o código base, então o código base nunca
vai ser melhorado. Também, se o revisor dificultar para que _qualquer_ alteração
entre, então os desenvolvedores são desincentivados a fazer melhorias no futuro.

Por outro lado, é dever do revisor garantir que cada CL é de tal qualidade que a
saúde geral do código base não está caindo com o tempo. Isso pode ser
complicado, porque geralmente bases de código se degradam por pequenas
alterações na qualidade do código através do tempo, especialmente quando um time
está sobre restrições de tempo significantes e eles sentem que precisam pegar
atalhos para cumprir suas metas.

Também, um revisor tem propriedade e responsabilidade sobre o código que está
revisando. Eles querem que o código base se mantenha consistente, manutenível, e
todas as outras coisas mencionadas no
[O que buscar em uma revisão de código.](looking-for.md)

Assim, nós temos as seguintes regras como padrão esperado em revisões de código:

**Em geral, revisores devem preferencialmente aprovar uma CL assim que ela
esteja em um estado que definitivamente melhora a qualidade geral do código do
sistema que está sendo trabalhado, mesmo que a CL não esteja perfeita.**

Esse é _o_ maior princípio entre todas as orientações de revisão de código.

Há limitações para isso, é claro. Por exemplo, se uma CL adiciona
funcionalidades que um revisor não quer no seu sistema, então o revisor
certamente pode recusar a aprovação mesmo que o código esteja bem feito.

Um ponto chave é que não existe um código "perfeito" &mdash; há apenas código
_melhor_. Revisores não devem solicitar ao autor refinar cada pequeno pedaço de
uma CL antes de aprová-la. Preferencialmente, o revisor deve balancear a
necessidade de avançar comparada com a importância da mudança que ele está
sugerindo. Ao invés de buscar perfeição, o que um revisor deve buscar é
_melhoria contínua_. Uma CL que, como um todo, melhora a manutenção, leitura e
entendimento do sistema não deve ser atrasada por dias ou semanas porque não
está "perfeita".

Revisores devem _sempre_ sentirem-se livres para deixar comentários expressando
que algo poderia ser melhor, mas se não for muito importante, coloque um prefixo
como "Nit: " para o autor saber que é só um ponto de refinamento que ele pode
escolher ignorar.

Nota: Nada nesse documento justifica liberar CLs que definitivamente _pioram_ a
qualidade geral do código do sistema. O único momento que você pode fazer isso é
em uma [emergência](../emergencies.md).

## Mentoria

Revisões de código podem ter uma função importante de ensinar desenvolvedores
algo novo sobre a linguagem, framework, ou princípios gerais de desenvolvimento
de software. É sempre bom deixar comentários que ajudam um desenvolvedor
aprender algo novo. Compartilhar conhecimento é parte da melhoria da saúde do
código ao longo do tempo. Apenas tenha em mente que se o seu comentário for
puramente educacional, mas não crítico para atender os padrões descritos nesse
documento, coloque um prefixo "Nit: " ou então explicite que ele não é
obrigatório que o autor resolva nessa CL.

## Princípios {#principles}

- Fatos técnicos e dados prevalecem sobre opinições e preferências pessoais.

- No que tange a estilo, o [guia de estilo](http://google.github.io/styleguide/)
  é autoridade absoluta. Qualquer ponto de estilo (espaço, etc.) que não esteja
  no guia de estilo é uma preferência pessoal. O estilo deve estar consistente
  com o que está no código. Se não existe estilo anterior, aceite o do autor.

- **Aspectos de desenvolvimento de software quase nunca são puramente problemas
  de estilo ou apenas preferência pessoal.** Eles são baseados em princípios
  fundamentais e precisam ser balanceados de acordo, não apenas por opinião
  pessoal. Algumas vezes existem algumas opções válidas. Se o autor puder
  demonstrar (seja por dados ou baseado em princípios da engenharia de software)
  que os caminhos são igualmente válidos, então o revisor deve aceitar a
  preferência do autor. Ou então a escolha deve ser guiada por princípios do
  desenvolvimento de software.

- Se nenhuma outra regra se aplica, então o revisor pode solicitar ao autor que
  seja consistente com a base de código atual, desde que não piore a qualidade
  do código do sistema.

## Resolvendo Conflitos {#conflicts}

Em qualquer conflito numa revisão de código, o primeiro passo é sempre o
desenvolvedor e o revisor tentarem chegar a um consenso, baseados nos conteúdos
desse e de outros documentos em [O Guia Do Autor da CL](../developer/index.md) e
[Como Fazer Uma Revisão de Código](./reviewer/index.md).

Quando entrar em consenso se tornar difícil, pode ajudar ter uma reunião
cara-a-cara ou por vídeo conferência entre o revisor e o autor, ao invés de
tentar resolver o conflito por comentários na revisão de código. (Se você fizer
isso, no entanto, garanta que grave os resultado da discussão em um comentário
na CL, para futuros leitores.)

Se isso não resolver a situação, então o jeito mais fácil seria escalar.
Geralmente o caminho da escalada é para discussões entre o time, tendo um Líder
Técnico para ajudar, pedindo uma decisão do mantenedor do código, ou pedindo
ajuda a um gerente. **Não deixe uma CL parada por causa de um autor e um revisor
que não entram em acordo.**

Próximo: [O que buscar em uma revisão de código](looking-for.md)
