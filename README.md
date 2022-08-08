# Regex Notes

Expressões Regulares (Regex)

`.` (meta-char) pode ser qualquer coisa

`.` o "ponto" que significa qualquer char
`*` o asterisco que serve para definir uma quantidade de chars, zero ou mais vezes
{e } as chaves que servem para definir uma quantidade de caracteres específicas que é desejado encontrar

Por exemplo:

`a{3}`

`\d*`
    

Lembrando também, se quisermos procurar pelo `*` ou `.` literalmente (sem significado especial), devemos utilizar o caractere `\`

CPF: 123.123.123-00
`\d\d\d\.\d\d\d\.\d\d\d-\d\dP`

Quantifier

`\d{3}\.\d{3}\.\d{3}\-\d{2}`


IPs de PC

- 126.1.112.34
- 128.126.12.244
- 192.168.0.34

`\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}`

- Telefone: `\(\d{2}\) \d{4}-\d{4}`
- CEP: `\d{5}-\d{3}`
- CNPj: `\d{2}\.\d{3}\.\d{3}\/\d{4}\-\d{2}`



Regex, ou expressões regulares, é uma linguagem para encontrar padrões de texto. Sendo uma linguagem independente, existem interpretadores para a maioria das plataformas de desenvolvimento, como JavaScript, C#, Python ou Ruby. 
Uma classe de caracteres predefinida é `\d`, que significa qualquer dígito. Existem vários meta-char, como `.` ou `*`. Existem quantifiers que definem quantas vezes um caractere deve aparecer:
 - `{1}` é um quantifier que significa uma vez.
 - `*` é um quantifier que significa zero, uma ou mais vezes
 - `.` é um meta-char que significa qualquer char.
 - Com `\` podemos escapar meta-chars, por exemplo `\..`

No caso do CPF sem pontos e somente números
`\d{3}\.{0,1}\d{3}\.?\d{3}\-?\d{2}`

`?` demonstra que o ponto pode ser opcional. Também pode ser usado com o quantifier `.{0,1}`

quando não tiver "-" e sim um "."

podemos definir uma classe de caracteres que podem aparecer nessa posição usando `[ ]`

`\d{3}\.?\d{3}\.?\d{3}[-.]?\d{2}`

não sendo usar o `\` para definir o meta-char `.` (ponto) pois ele tem significado literal dentro de uma classe

`\d` é igual à `[0-9]`
Qual é a classe correta para definir os números entre 1 e 3 E 6 e 9?

`[1-36-9]`
