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
