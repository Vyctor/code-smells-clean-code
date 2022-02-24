# Odores e Heuristícas

Este repositório é um compilado de odores e heuristicas retidos do livro **Clean Code** de **_Robert C. Martin_**.

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

### G8

### G9

### G10

### G11

### G12

### G13

### G14

### G15

### G16

### G17

### G18

### G19

### G20

### G21

### G22

### G23

### G24

### G25

### G26

### G27

### G28

### G29

### G30

### G31

### G32

### G33

### G34

### G35

### G36
