# Odores e Heuristícas

Este repositório é um compilado de odores e heuristicas retidos do livro **Clean Code** de **_Robert C. Martin_**.

- [Odores e Heuristícas](#odores-e-heuristícas)
  - [Comentários](#comentários)
    - [C1: Informações inapropriadas](#c1-informações-inapropriadas)
    - [C2: Comentário obsoleto](#c2-comentário-obsoleto)
    - [C3: Comentários redundantes](#c3-comentários-redundantes)
    - [C4: Comentário mal escrito](#c4-comentário-mal-escrito)
    - [C5: Código como comentário](#c5-código-como-comentário)
  - [Ambiente](#ambiente)
    - [A1: Construir requer mais de uma etapa](#a1-construir-requer-mais-de-uma-etapa)
    - [A2: Testes requerem mais de uma etapa](#a2-testes-requerem-mais-de-uma-etapa)
  - [Funções](#funções)
    - [F1: Parâmetros em excesso](#f1-parâmetros-em-excesso)
    - [F2: Parâmetros de saída](#f2-parâmetros-de-saída)
    - [F3: Parâmetros lógicos](#f3-parâmetros-lógicos)
    - [F4: Função morta](#f4-função-morta)
  - [Geral](#geral)
    - [G1: Múltiplas linguagens em um arquivo fonte](#g1-múltiplas-linguagens-em-um-arquivo-fonte)
    - [G2: Comportamento óbvio não implementado](#g2-comportamento-óbvio-não-implementado)
    - [G3: Comportamento incorreto nos limites](#g3-comportamento-incorreto-nos-limites)
    - [G4: Seguranças anuladas](#g4-seguranças-anuladas)
    - [G5: Duplicação](#g5-duplicação)
    - [G6: Códigos no nível errado de abstração](#g6-códigos-no-nível-errado-de-abstração)
    - [G7: As classes base dependem de suas derivadas](#g7-as-classes-base-dependem-de-suas-derivadas)
    - [G8: Informações excessivas](#g8-informações-excessivas)
    - [G9: Código morto](#g9-código-morto)
    - [G10: Separação vertical](#g10-separação-vertical)
    - [G11: Inconsistência](#g11-inconsistência)
    - [G12: Entulho](#g12-entulho)
    - [G13: Acoplamento Artificial](#g13-acoplamento-artificial)
    - [G14: Feature Envy](#g14-feature-envy)
    - [G15: Parâmetros seletores](#g15-parâmetros-seletores)
    - [G16: Propósito obscuro](#g16-propósito-obscuro)
    - [G17: Responsabilidade mal posicionada](#g17-responsabilidade-mal-posicionada)
    - [G18: Modo estático inadequado](#g18-modo-estático-inadequado)
    - [G19: Use variáveis descritivas](#g19-use-variáveis-descritivas)
    - [G20: Funções devem dizer o que elas fazem](#g20-funções-devem-dizer-o-que-elas-fazem)
    - [G21: Entenda o Algoritmo](#g21-entenda-o-algoritmo)
    - [G22: Torne dependências lógicas em físicas](#g22-torne-dependências-lógicas-em-físicas)
    - [G23: Prefira polimorfismoa if/else ou switch/case](#g23-prefira-polimorfismoa-ifelse-ou-switchcase)
    - [G24: Siga as convenções padrões](#g24-siga-as-convenções-padrões)
    - [G25: Substitua os números mágicos por constantes com nome](#g25-substitua-os-números-mágicos-por-constantes-com-nome)
    - [G26: Seja preciso](#g26-seja-preciso)
    - [G27: Estrutura acima da convenção](#g27-estrutura-acima-da-convenção)
    - [G28: Encapsule as condicionais](#g28-encapsule-as-condicionais)
    - [G29: Evite condicionais negativas](#g29-evite-condicionais-negativas)
    - [G30: Funções devem fazer uma coisa só](#g30-funções-devem-fazer-uma-coisa-só)
    - [G31: Acoplamentos temporais ocultos](#g31-acoplamentos-temporais-ocultos)
    - [G32: Não seja arbitrário](#g32-não-seja-arbitrário)
    - [G33: Encapsule as condições de limite](#g33-encapsule-as-condições-de-limite)
    - [G34: Funções devem descer apenas um nível de abstração](#g34-funções-devem-descer-apenas-um-nível-de-abstração)
    - [G35: Mantenha os dados configuráveis em níveis altos](#g35-mantenha-os-dados-configuráveis-em-níveis-altos)
    - [G36: Evite a navegação transitiva](#g36-evite-a-navegação-transitiva)

## Comentários

### C1: Informações inapropriadas

Um comentário não deve conter informações que deveriam estar em outras sistemas diferentes do que se está trabalhando. Estes devem conter apenas dados técnico sobre o código e o projeto.

### C2: Comentário obsoleto

Um comentário que ficou velho, irrelevante e incorreto é obsoleto. Caso você encontre algum é melhor atualizá-lo ou removê-lo do código, pois estes tendem a se desviar do código que descreviam, gerando confusão e más interpretações.

### C3: Comentários redundantes

Um comentário redundante é aquele que descreve um código autodescritivo. Ao olhar o código já é intuitivo verificar a sua motivação.

Exemplos:

```ts
function() {
  let i = 0; // declara a variável i e inicializa com o valor 0
}
```

```ts
/**
 * @param email
 * @return Result
 *
**/
public sendMessageTo(email: string): Promise<Result> {
}
```

**Os comentários devem informar o que o código não consegue por sí só.**

### C4: Comentário mal escrito

Um comentário que valhe ser escrito **deve** ser bem escrito. Se for criar um, não tenha pressa e certifique-se que seja o melhor comentário que você já escreveu. Selecione bem suas palavras. Use corretamente a gramática e a pontuação. Não erre. Não diga o óbvio. Seja breve.

### C5: Código como comentário

Não comente código e deixe-o lá como se fosse precisar dele futuramente. Esse código com o passar do tempo fica cada vez mais irrelevante e essa informação é facilmente mantida pelo sistema de controle de versões.

Manter códigos comentados é uma **abominação**. Quando você ver, exclua-o, não deixe que código comentados existam.

Exemplo:

```ts
// Commented by a mysterious unknown reason
// const iWishToDoSomeMathOperation = function(numbers: number[]): number {
//   return something...
// };

const newIWishtToDoSomaMathOperation = function (numbers: number[]): number {
  return something...
};
```

## Ambiente

### A1: Construir requer mais de uma etapa

Construir um projeto deve ser uma operação simples e única.

Você não deve:

- Verificar muitos pedacinhos do controle de código fonte
- Precisar de uma sequência de comandos arcaicos ou scripts dependentes de contexto de modo a construir elementos individuais
- Ter de buscar perto e longe várias dependências extras, arquivos XML, e outros componentes que o sistema precise.

Você deve ser capaz de verificar o sistema com um único comando e então dar outro comando simples para construí-lo.

### A2: Testes requerem mais de uma etapa

Você deve ser capaz de rodar todos os testes de unidade com apenas um comando. No melhor dos casos, você pode executar todos ao clicar em um botão em sua IDE. No pior, você deve ser capaz de dar um único comando simples em um único prompt. Poder rodas os testes é tão essencial e importante que deve ser rápido, fácil e óbvio de se fazer.

## Funções

### F1: Parâmetros em excesso

As funções devem ter um número pequeno de parâmetros. Ter nenhum é **melhor**. Depois vem **um**, **dois** e **três**. Mais do que isso é questionável e deve-se evitar.

### F2: Parâmetros de saída

Os parâmetros de saída são inesperados. Espera-se que parâmetros sejam de entradas e não de saída. Se sua função for alterar o estado de algo, faça-a mudar o do objeto no qual ela é chamada.

### F3: Parâmetros lógicos

Parâmetros booleanos explicitamente declaram que a função faz mais de uma coisa. Eles são confusos e devem ser eliminados.

```ts
export function processData(isInternational: boolean): Something {
  if (isInternacional) {
    // do something...
  } else {
    // do other thing
  }
}
```

Refatorando:

```ts
export function processNationalData(): Something {
  // Do something...
}

export function processInternationalData(): Something {
  // Do something...
}
```

### F4: Função morta

Deve-se descartar os métodos que nunca são chamados. Manter pedaços de código morto é devastador. Não tenha receio de excluir a função, seu sistema de controle de código ainda se lembrará dela.

## Geral

### G1: Múltiplas linguagens em um arquivo fonte

O ideal para um arquivo fonte é ter apena uma linguagem, mas na vida real provavelmente em algum momento seremos força-dos a ignorar essa regra. De toda forma devemos minimizar a quantidade como o uso de linguagens extras em nossos códigos fontes.

### G2: Comportamento óbvio não implementado

Qualquer função ou classe deve implementar os comportamentos que outro programador possivelmente esperaria.
Quando um comportamento esperado não é implementado os leitores e usuários do código não podem mais depender de suas intuições sobre o que indica o nome das funções. Aquelas pessoas perdem a confiança no autor original e devem voltar a ler todos os detalhes do código.

### G3: Comportamento incorreto nos limites

Desenvolvedores geralmente criam funções as quais eles acham que funcionarão, e, então, confiam em suas intuições em vez de se esforçar para provar que o código realmente funciona em todos os lugares e limites.

Não existe substituição para uma dedicação minuciosa. Cada condição de limite, cada canto do código, ajuste e excessão representa algo que pode estragar um algoritmo elegante e intuitivo. Não depende de sua intuição. Cuide de cada condição de limite e teste sua aplicação.

### G4: Seguranças anuladas

É arriscado anular as seguranças. Desabilitar certos avisos, testes de falhas, podem ser de extremo risco para a aplicação.

### G5: Duplicação

Sempre que você encontrar duplicação no código significa que você perdeu uma chance para abstração. Aquela duplicação provavelmente poderia se tornar uma sub-rotina ou talvez outra classe completa. Ao transformar a duplicação em tal, você aumenta o vocabulário da linguagem de seu projeto. Outros programadores podem usar os recursos de abstração que você criar, e a codificação se torna mais rápida e menos propensa a erros devido a você ter elevado o nível de abstração.

A forma mais óbvia de duplicação é quando você possui blocos de código idênticos, como se alguns programadores tivessem saído copiando e colando estruturas aninhadas que aparecem repetidas diversas vezes, em diversos módulos, sempre testando as mesmas condições. Nesse caso deve-se **substituir pelo polimorfismo**.

Formas ainda mais sutis seriam os módulos que possuem algoritmos parecidos, mas que não possuem as mesmas linhas de código. Isso ainda é duplicação e deve-se resolver através dos padrões **Method** ou **Strategy**.

**Elimine a duplicação sempre que puder**.

### G6: Códigos no nível errado de abstração

É importante gerar abstrações que separem conceitos gerais de níveis mais altos dos conceitos detalhados de níveis mais baixos.

As vezes fazemos isso criando classes abstratas que contenham os conceitos de níveis mais altos e gerando derivadas que possuam os conceitos de níveis mais baixos. Com isso garantimos uma divisão completa.

Queremos que toos os conceitos de níveis mais altos fiquem na classe base e que todos os de níveis mais baixos fiquem em suas derivadas.

Por exemplo, constantes, variáveis ou funções que posuam apenas a implementação detalhada devem ficar na classe base. Essa não deve saber nada sobre o resto.

Essa regra também se aplica aos arquivos fonte, componentes e módulos. Um bom projeto de software exige que separemos os conceitos em níveis diferentes e que os coloquemos em contâineres distintos. De vez em quando, esses contâineres são classes base ou derivadas, e, às vezes, arquivos fontes, módulos ou componentes. Seja qual for o caso, a separação deve ser total. Não queremos que os conceitos de baixo e alto níveis se misturem.

### G7: As classes base dependem de suas derivadas

A razão mais comum para separar os conceitos em classes base e derivadas é para que os conceitos de níveis mais altos das classes base possam ficar independentes dos conceitos de níveis mais baixos das classes derivadas. Portanto, quando virmos classes base mencionando os nomes de suas derivadas, suspeitaremos de um problema.

De modo geral, **as classes base não devem enxergar nada de suas derivadas**.

Essa regra possui excessões. De vez em quando o número de derivadas é fixado, e a classe base tem códigos que consultamsuas derivadas. Vemos isso em muitas implementações de máquinas com configuração finita. Porém, neste caso, as classes base e derivadas estão fortemente acopladas e são sempre implementadas juntas no mesmo arquivo jar. De modo geral, queremos poder implementar as classes base e derivadas em arquivos jar direfentes.

### G8: Informações excessivas

Módulos bem definidos possuem interfaces pequenas que lhe permite fazer muito com pouco. Já os mal definidos possuem interfaces grandes e longas que lhe obriga a usar muitas formas diferentes para efetuar coisas simples. Um interface bem definida não depende de muitas funções, portanto, há baixo acoplamento. E uma interface mal definida depende de diversas funções que devem ser chamadas, gerando alto acoplamento.

Quanto menos tiver uma classe, melhor.
Quanto menos variáveis uma função usar, melhor.
Quanto menos variáveis tiver uma classe, melhor.
Esconda seus dados, funções utilitárias, constantes e variáveis temporárias.
Não crie muitas variáveis e funções protegidas para suas subclasses.
Concentre-se em manter as interfaces curtas e muito pequenas.
Limite as informações para ajudar a manter um baixo acoplamento.

### G9: Código morto

Um código morto é aquele que nunca é executado. Seu problema é que após um tempo ele começa a se tornar desatualizado, não seguindo regras ou convenções, se tornando obsoleto entre código atualizado. Quando encontrar código morto exclua-o do sistema.

### G10: Separação vertical

Devem-se declarar as variáveis e funções próximas de onde são utilizadas.
Deve-se declarar as variáveis locais imediatamente acima do seu primeiro uso, e o escopo deve ser vertical.
Não queremos que variáveis locais sejam declaradas centenas de linhas afastadas de onde são utilizadas.

Devem-se declarar as funções privadas imediatamente abaixo de seu primeiro uso. Elas pertencem ao escolpo de toda a classe. Mesmo assim, ainda desejamos limitar a distância vertical entre as chamadas e as declarações. Encontrar uma função privadadeve ser uma questão de buscar para baixo a partir de seu primeiro uso.

### G11: Inconsistência

Se você fizer algo de uma maneira, faça da mesma forma todas as outras coisas similares. Atenção ao escolher suas convenções, uma vez escolhidas, siga-as.

### G12: Entulho

De que serve um construtor sem implementação alguma? Para entulhar o código com pedaços inúteis. Variáveis que não são usadas, funções que não são chamadas, comentários que não acrescentam informações e assim por diante, são todos entulhos e devem ser removidos.

### G13: Acoplamento Artificial

Coisas que não dependem uma da outro não devem ser acopladas artificialmente. Por exemplo, enuns genéricos não devem ficar dentro de classes mais específicas, pois isso obriga todo o aplicativo a enxergar mais essas classes. O mesmo vale para funções static de proposito geral, declaradas em classes específicas.

De modo geral, um acoplamento artificial é um acoplamento entre dois módulos que não possuem um propósito direto. Isso ocorre quando se coloca uma variável, uma constante ou uma funções em um local temporariamente conveniente, porém inapropriado. Isso é descuido e preguiça.

Tome seu tempo para descobrir onde devem ser declaradas as funções, as constantes e as variáveis. Não as jogue no local mais conveniente e fácil e as deixe lá.

### G14: Feature Envy

Os métodos de uma classe devem ficar interessados nas variáveis e funções da classe a qual eles pertencem, e não de outras classes. Quando um método usa métodos de acesso e de alteração de algum outro objeto para manipular dados dentro deste objeto, o método inveja o escopo da classe daquele outro objeto. Ele queria estar dentro daquela outra classe de modo que pudesse ter acesso direto às variáveis que está manipulando.

### G15: Parâmetros seletores

São parâmetros que definem certo comportamento que uma função deva adotar. De forma geral é uma forma preguiçosa de não ter que dividir uma função grande em outras menores.

Exemplo:

```ts
export function calculatePayment(employee: Employee) {
  if (employee.department === "IT") {
    // do IT payment calcs
  } else if (employee.department === "SomeDepartment") {
    // do other payment cals
  }
}
```

Refatorando:

```ts
export function calculateITPayment(employee: Employee) {
  // do IT payment calcs
}

export function calculateSomeOtherDepartmentPayment(
  someOtherDepartmentEmployee: Employe
) {
  // do some other department calcs
}
```

### G16: Propósito obscuro

Queremos que o código seja o mais específico possível. Expressões contínuas, notação Húngara e números mágicos são elementos que obscurescem a intenção do autor.

Example:

```ts
export function calculateShopcartPrice(shopcart: Shopcart): number {
  const itensPrice = shopcart
    .map((item) => {
      return {
        value: item.value * item.quantity,
      };
    })
    .reduce((acc, value) => acc + value, 0);

  return itensPrice + 25.0;
}
```

Refactoring:

```ts
export function calculateShopcartPrice(shopcart: Shopcart): number {
  const deliveryPrice = 25.0;
  const itensPrice = shopcart
    .map((item) => {
      return {
        value: item.value * item.quantity,
      };
    })
    .reduce((acc, value) => acc + value, 0);

  return itensPrice + deliveryPrice;
}
```

### G17: Responsabilidade mal posicionada

Onde colocar o código é uma das decisões mais importantes que um desenvolvedor de software deve fazer.

Deve-se substituir o código onde um leitor geralmente espera. A constante PI deve ficar onde estão declaradas as funções de trigonometria, a constante OVERTIME_RATE deve ser declarada na classe HourlyPayCalculator e assim por diante.

Um exercício para sabermos onde colocar determinado trecho de código é analisar o que este trecho faz e o nome do local que estamos colocando-o.

### G18: Modo estático inadequado

Em geral deve-se dar preferência a métodos não estáticos. Na dúvida, torne a função não estática. Se precisar de uma função estática verifique se não há a necessidade de futuramente precisar que ela se comporte de maneira polimórfica.

### G19: Use variáveis descritivas

Variáveis explicativas são melhores do que variáveis não explicativas. É impressionante como um módulo pode se tornar transparente simplesmente ao separar os cálculos em valores intermediários e bem nomeados.

### G20: Funções devem dizer o que elas fazem

Se você tiver de olhar a assinatura, ou documentação, de uma função para saber o que ela faz, é melhor selecionar um nome melhor ou reorganizar a funcionalidade de modo que esta possa ser colocada em funções com nomes melhores.

O que esse código faz?

```ts
const date = new DateHandler();
date.add(5);
```

Refatorando:

```ts
const date = new DateHandler();
date.addDays(5);
```

### G21: Entenda o Algoritmo

Antes de achar que já terminou uma função, certifique-se de que você entenda como ela funciona. Ter passado em todos os testes não basta. Você deve compreender que a solução está correta.

Geralmente a melhor forma de obter esse conhecimento e entendimento é refatorar a função em algo que seja tão limpo e expressivo que fique óbvio que ela funcione.

### G22: Torne dependências lógicas em físicas

Se um módulo depende de outro, essa dependência deve ser física, e não apenas lógica. O módulo dependente não deve fazer suposições sobre o módulo no qual ele depende. Ao invés disso devemos explicitamente àquele módulo todas as informações das quais ele depende.

### G23: Prefira polimorfismoa if/else ou switch/case

Podem existir mais de uma estrutura switch para um dado tipo de seleção. Os casos nos quais o switch deve criar objetos polimórficos que substituam outras estruturas switch no resto do sistema.

### G24: Siga as convenções padrões

Cada equipe deve seguir um padrão de programação baseando-se nas normas comuns do mercado. A equipe não deve precisar de um documento que descreve essas convenções porque seus códigos fornecem os exemplos necessários.

Cada membro da equipe deve seguir essas convençõe, isso significa que cada um deve ser maduro o suficiente para entender que não importa onde você coloque suas chaves contanto que todos concordem onde colocá-las.

### G25: Substitua os números mágicos por constantes com nome

Substitua nomes de variáveis que contenham valores sem contexto para nomes que indiquem o que tal valor significa.

O que é esse valor 86400?

```ts
export function isBiggerThanADay(seconds: number): boolean {
  if (seconds > 86400) {
    return true;
  }
}
```

Refatorando:

```ts
export function isBiggerThanADay(seconds: number): boolean {
  const oneDayInSeconds = 86400;
  if (seconds > oneDayInSeconds) {
    return true;
  }
}
```

### G26: Seja preciso

quando você toma uma decisão em seu código, certifique-se de fazê-la precisamente. Saiba por que a tomou e como lidará com quaisquer excessões. Não seja desleixado com a precisão de suas decisões.

Ambiguidades e imprecisão em código são resltado de desacordos e desleixos. Seja qual for o caso, elas devem ser eliminadas.

### G27: Estrutura acima da convenção

Insista para que as decisões do projeto sejam baseadas em estrutura acima da convenção. Convenções de nomenclatura são boas, mas inferiores as estruturas que forçam um certo cumprimento. Por exemplo, switch/cases com enumerações bem nomeadas são inferiores a classes base com métodos abstratos. Ninguém é obrigado a implementar a estrutura switch/case da mesma forma o tempo todo, mas as classes base obrigam a implementação de todos os métodos abstratos das classes concretas.

### G28: Encapsule as condicionais

A lógica booleana já é difícil o bastante de entender sem precisar vê-la no contexto de um if ou um while. Extraia funções que expliquem o propósito da estrutura condicional.

Exemplo:

```ts
export function generateReceipt({ payd, date }: Purchase): Receipt {
  if (!payd || date.greaterThan(30, "days")) {
    throw new Error("Cannont generate Receipt");
  }
}
```

Refatorando

```ts
export function generateReceipt({ payd, date }: Purchase): Receipt {
  const canGenerateReceipt = payd && date.lessThan(30, "days");

  if (canGenerateReceipt)) {
    // do the job
  } else {
    throw new Error("Cannont generate Receipt");
  }
```

### G29: Evite condicionais negativas

É um pouco mais complicado entender condicionais negativas do que afirmativas. Opte sempre por utilizar condicionais afirmativas.

### G30: Funções devem fazer uma coisa só

Funções que executam mais de uma tarefa devem ser refatoradas em funções menores, cada um com uma única responsabilidade.

### G31: Acoplamentos temporais ocultos

Acoplamentos temporais costumam ser necessários, mas você não deve ocultar o acoplamento. Organize os parâmetros de suas funções de modo que a ordem na qual são chamadas fique óbvia.

Exemplo:

```ts
class MoogDiver {
  private gradient: Gradient;
  private splines: Splines[];

  public void dive(reason: string): void {
    this.gradient = saturateGradient();
    this.splintes = reticulateSplines(this.gradient);
    diveForMoog(splines, reason);
  }
}
```

Isso expõe o acoplamento temporário, ao ser necessário passar o valor anterior como parâmetro para o próximo passo.

### G32: Não seja arbitrário

Tenha um motivo para que você estruture seu código e certifique-se de que tal motivo seja infomado na estrutura. Se esta parece arbitrária, as outras pessoas se sentirão no direito de alterá-la. Mas se parece consistente por todo o sistema, as outras pessoas irão usá-la e preservar a convenção utilizada.

### G33: Encapsule as condições de limite

Condições de limite são difíceis de acompanhar. Coloque o processamento para elas em um único lugar. Não as deixe expalhadas pelo código.
Não queremos um enxame de +1s e -1s aparecendo aqui e acolá.

Exemplo:

```ts
if (level + 1 < tags.length) {
  return 0;
}
```

Refatorando:

```ts
const nextLevel = level + 1;

if (nextLevel < tags.length) {
  return 0;
}
```

### G34: Funções devem descer apenas um nível de abstração

As instruções de uma função devem ficar todas no mesmo nível de abstração, o qual deve ser um nível abaixo da operação descrita pelo nome da função. Isso pode ser o mais difícil dessas heurísticas para se interpretar e seguir, embora a idéia seja bastante simples.

### G35: Mantenha os dados configuráveis em níveis altos

Se você tiver uma constante, como um valor padrão ou de configuração, que seja conhecida e esperada em um nível alto de abstração, não a coloque numa função de nível baixo. Exponha a constrante como parâmetro para tal função, que será chamada por outra de nível mais alto.

### G36: Evite a navegação transitiva

De modo geral não queremos que um único módulo saiba muito sobre seus colaboradores. Mais especificamente, se A colabora com B e B colabora com C então não queremos que A colabore com C.
Isso às vezes se chama lei Demeter. Os programadores pragmáticos chamam de **Criar um código tímido**. Em ambos os casos, resume-se a garantir que os módulos saibam sobre seus colaboradores apenas e não sobre o mapa de navegação de todo o sistema.
