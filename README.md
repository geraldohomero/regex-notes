# Regex Notes

- [Regex CPF](https://github.com/geraldohomero/regex-notes/blob/main/regexCPF.md)
- [Regex Tester](https://github.com/geraldohomero/regex)

## Expressões Regulares (Regex)

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


IPs de PC podem ter números variados:

- 126.1.112.34
- 128.126.12.244
- 192.168.0.34

    - `\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}`

- Telefone: `\(\d{2}\) \d{4}-\d{4}`
- CEP: `\d{5}-\d{3}`
- CNPj: `\d{2}\.\d{3}\.\d{3}\/\d{4}\-\d{2}`



Regex, ou expressões regulares, é uma linguagem para encontrar padrões de texto. Sendo uma linguagem independente, existem interpretadores para a maioria das plataformas de desenvolvimento, como JavaScript, C#, Python ou Ruby. 
Uma classe de caracteres predefinida é `\d`, que significa qualquer dígito. Existem vários meta-char, como `.` ou `*`. Existem quantifiers que definem quantas vezes um caractere deve aparecer:
 - `{1}` é um quantifier que significa uma vez.
 - `*` é um quantifier que significa zero, uma ou mais vezes
 - `.` é um meta-char que significa qualquer caracter.
 - Com `\` podemos escapar meta-chars, por exemplo `\..`

No caso do CPF sem pontos e somente números (12312312300)

`\d{3}\.{0,1}\d{3}\.?\d{3}\-?\d{2}`

`?` demonstra que o ponto pode ser opcional. Também pode ser usado com o quantifier `.{0,1}`

quando não tiver "-" e sim um "."

podemos definir uma classe de caracteres que podem aparecer nessa posição usando `[ ]`

`\d{3}\.?\d{3}\.?\d{3}[-.]?\d{2}`

não sendo usar o `\` para definir o meta-char `.` (ponto) pois ele tem significado literal dentro de uma classe

`\d` é igual à `[0-9]`
Qual é a classe correta para definir os números entre 1 e 3 E 6 e 9?

`[1-36-9]`


- `?` - zero ou uma vez.
- `*` - zero ou mais vezes.
- `+` - uma ou mais vezes.
- `{n}` - exatamente n vezes.
- `{n,}` - no mínimo n vezes.
- `{n,m}` - no mínimo n vezes, no máximo m vezes.

### Trabalhando com espaços

- O primeiro caractere é um espaço branco.
- `\t` é um tab.
- `\r` é carriage return.
- `\n` é newline.
- `\f` é form feed.
- `\s`é um white space
    - `\s+` igual à uma ou mais vezes

### Letras

- `[A-Z]` significa de A até Z, sempre maiúscula.
- `[A-Zç]`para caracteres especiais.
- `[a-z]` significa de a até z, sempre minúscula,
- `[A-Za-z]` significa A-Z ou a-z.
- `[abc]` significa a, b ou c.

### Recapitulando

- Podemos definir facilmente a classe de qualquer caractere com o `[A-Z]`.

- Conhecemos todos os quantifiers como `?`, `+`, `*` e `{n}`.

- `\s` significa whitespace e é um atalho para `[ \t\r\n\f]`.

 - `\w` significa word char e é uma atalho para `[A-Za-z0-9_]`.
 
 ### Âncora
 
 Uma forma de encontrar uma posição. Existem âncoras predefinidas que selecionam uma posição dentro do alvo
 
 - `\b`- word boundary (limite de palavras) - Não pega word-char
 - `\b` no início e no final
 - `^` - "no início do target (alvo)"
 - `$`- "no final do target (alvo)"
 
 
### Grupos

- `()`
- `(?:)` retirar do resultado da execução do regex (non-capturing group)
    - `([0123]?\d)\s+(?:de\s+)?([A-Z][a-zç]{1,8})\s+(?:de\s+)?([12]\d{3})` - Data formato: 00 de Mês de 19(20)xx

### Greed

Quantifier `+` + `?` torna-o preguiçoso

### Backreferences

- `/1`
`/` seguido do número do grupo de referência


### JavaScript

- Exemplo com Regex fixa:

`var regex = /(\d\d)(\w)/g;` //2 dígitos e 1 word char, dois grupos

`var resultado = regex.exec('11a22b33c ');`

- Exemplo com Regex não-fixa

`var exp = new RegExp("(\\d\\d)(\\w)", "g");`

### Validação senha HTML5

#### Exemplo:

- `"pattern"= ^(?=.*[a-z](?=.*[A-Z](?=.*[0-9](?!=.*[ !@#$%^&*_-=-+]).{6,12}$`

Descrição para o formato esperado `"title"=descrição`
