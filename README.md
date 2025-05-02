# Módulo 15 - Introdução ao SASS

## Menu
[Aula 1 - Node JS](#aula-1---node-js)  
[Aula 2 - Sintaxe SASS e SCSS](#aula-2---sintaxe-sass-e-scss)  
[Aula 3 - Variáveis e estrutura no sass(SASS) ](#aula-3---variáveis-e-estrutura-no-sass-sass)  
[Aula 4 - Reutilize CSS com Mixins](#aula-4--reutilizando-código-com-mixins-sass)  
[Aula 5 - Funções e operadores](#aula-5--funções-e-operadores-no-sass)  

## Aula 1 - Node JS

### Introdução ao Node.js e ao Sass (SASS)

O Sass é um **pré-processador para CSS**, ou seja, uma ferramenta que estende as funcionalidades do CSS tradicional. Com ele, podemos usar **variáveis**, **funções** e **dividir o código em diferentes arquivos**, o que facilita muito a organização e manutenção dos estilos.

Neste curso, vamos utilizar o Sass através do **Node.js**.

### O que é Node.js?

De acordo com a explicação do professor, o **Node.js não é uma linguagem de programação**, mas sim uma **ferramenta que permite executar código JavaScript fora do navegador**, em ambientes como o terminal do sistema operacional.

### Como instalar o Node.js?

1. Acesse o site oficial: [https://nodejs.org](https://nodejs.org)  
2. Na seção de download, a versão **LTS (Long Term Support)** já estará selecionada por padrão.
3. Role um pouco a página e selecione o instalador para o seu sistema operacional (por exemplo, Windows).
4. Após a instalação, abra o terminal e digite o comando:

```bash
node -v
```

Esse comando mostra a **versão instalada do Node.js**, confirmando que a instalação foi concluída com sucesso.

### Instalando o Sass com NPM

Depois que o Node.js estiver instalado, o próximo passo é instalar o Sass globalmente com o seguinte comando no terminal:

```bash
npm install -g sass
```

### Organização de pastas e navegação

Após a instalação, o professor navegou até a pasta onde ele guarda seus códigos — no caso dele, chamada `BackCodes`.

No meu caso, minha estrutura de pastas é diferente:
- Eu tenho uma pasta chamada `EBAQ` dentro dos **Meus Documentos**.
- Dentro da `EBAQ`, há duas subpastas: `FRONT` e `BACK`.
- Na pasta `FRONT`, mantenho uma pasta chamada `FEITA`, onde organizo todos os módulos e projetos já finalizados.
- Fora da pasta `FEITA`, costumo deixar o módulo em que estou trabalhando atualmente.

Confesso que não lembrava exatamente como fazer a navegação pelo terminal, pois faz um tempo que não pratico esse tipo de comando. Por isso, abri o terminal diretamente pela interface do Windows, clicando com o botão direito na pasta onde vou trabalhar com Sass e selecionando a opção **"Abrir no terminal"**.

## Aula 2 - Sintaxe SASS e SCSS

### Introdução ao Node.js e ao Sass (SASS)

Na primeira aula, o professor havia feito todo o processo pelo terminal, mas agora estamos utilizando o **VS Code**.

O nome do arquivo que vamos construir nesta aula será **`main.sass`**.

#### Duas Sintaxes do Sass

O professor explica que o Sass possui duas sintaxes:
- **`.sass`**: diferente do CSS, **não utiliza chaves nem ponto e vírgula**.
- **`.scss`**: mais parecida com a escrita tradicional do CSS.

##### Exemplo Comparativo

No **CSS**, escreveríamos:

```css
body {
  background-color: red;
}
```

Já no **`.sass`**, faríamos:

```
body
  background-color: red
```

Ou seja, apenas com indentação e sem o uso de `{}`, `;`.

#### Extensão para VS Code

A extensão utilizada para realce de sintaxe é **Sass**, desenvolvida por **Syler Seely**.

Ela colore os elementos do código:
- O seletor (ex: `body`) em **amarelo**
- A propriedade (ex: `background-color`) em **azul**
- O valor (ex: `red`) com **fundo da cor correspondente**

#### Preferência pela Sintaxe `.scss`

O professor afirma que a sintaxe `.scss` será a mais utilizada no curso.  
Apesar da introdução ao `.sass`, vamos focar no **`main.scss`** daqui em diante.

Pessoalmente, não achei o `.sass` muito prático, pois exige digitação manual de seletores, propriedades e valores, sem autocomplete. Isso torna o processo mais trabalhoso do que o necessário.

#### Sass como Pré-processador

O **Sass é um pré-processador**, ou seja, ele **transforma arquivos `.sass` ou `.scss` em CSS puro**.

Para isso, utilizamos o **Node.js**, e começamos o processo com:

```bash
npm init
```

Esse comando inicializa o projeto Node e faz perguntas como:

- Nome do pacote (`package name`) – usei “sass” para manter simples
- Versão – Enter para manter `1.0.0`
- Descrição – deixei em branco
- Entry point – `index.js` (padrão)
- Test, Git repo, Keywords, Author, License – todos deixei padrão (Enter)
- Confirmação final – digitei `yes`

#### Repositório Git

Uma diferença que percebi é que, enquanto o professor não criou repositório Git, eu já havia criado o meu. Isso fez com que o projeto já estivesse integrado com versionamento online.

Na etapa de **autor**, preenchi com meu nome: **Matheus**.

#### Arquivos Criados pelo Node

Ao finalizar o `npm init`, são criados:
- `package.json`: informações e dependências do projeto
- `package-lock.json`: controle de versões exatas dos pacotes
- `node_modules/`: pasta com todos os pacotes instalados

**Importante**: essa pasta é muito grande e não deve ir para o repositório Git.  
Para isso, criamos um arquivo chamado `.gitignore` e adicionamos:

```
node_modules
```

#### Diferença entre `package.json` e `package-lock.json`

- `package.json`: guarda **as dependências declaradas**
- `package-lock.json`: controla **as versões reais instaladas**  
Isso garante que outros desenvolvedores terão o mesmo ambiente ao instalar o projeto.

#### Instalando o Sass localmente

Instalamos o Sass no ambiente local com:

```bash
npm i --save-dev sass
```

O `--save-dev` indica que o Sass será usado apenas no desenvolvimento.

#### Editando o `package.json`

No `package.json`, editamos a seção de `scripts`:

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "sass": "sass"
}
```

Adicionamos a vírgula para separar os scripts corretamente.

#### Executando o Sass

Para rodar o Sass, usamos:

```bash
npm run sass
```

No entanto, isso gerará erro se não definirmos **arquivo de entrada e saída**.

##### Forma correta:

```bash
npm run sass main.scss main.css
```

- `main.scss`: arquivo de entrada
- `main.css`: arquivo de saída gerado

Esse comando cria dois arquivos:
- `main.css`: o CSS final
- `main.css.map`: mapeia as alterações do SCSS

#### Utilidade do `main.css.map`

Esse arquivo permite que o **DevTools do navegador** aponte as alterações diretamente no `main.scss`, e não no `main.css`.

Isso facilita a depuração e edição, pois sabemos exatamente onde o estilo foi definido no código fonte.

#### Visualizando no navegador

Criamos um arquivo `index.html` com:

```html
<link rel="stylesheet" href="main.css">
```

Abrimos no navegador com **Live Server**.

No DevTools, ao inspecionar os elementos, vemos que:
- As estilizações aparecem como se tivessem sido feitas no `main.scss`
- Isso acontece graças ao arquivo `main.css.map`, que faz a ligação entre SCSS e CSS

## Aula 3 - Variáveis e Estrutura no Sass (SASS)

Nesta aula, aprendemos a **declarar variáveis no Sass**, organizar os arquivos do projeto e aplicar estruturas como **aninhamento de seletores**, **pseudo-classes** e **condicionais com classes**.

### Estrutura Inicial

Começamos a aula **excluindo os arquivos** `main.css`, `main.css.map` e `main.scss`, pois o professor reorganizou a estrutura do projeto.

No VS Code, criamos:
- Uma pasta chamada `source`, onde ficará o arquivo-fonte `.scss`.
- Dentro de `source`, uma pasta chamada `dist` (apesar de não ter sido usada diretamente nesta aula).
- Fora da `source`, uma pasta `build`, onde o Sass gerará o CSS final.

### Atualização do package.json

Alteramos o script do `package.json` para definir o arquivo de entrada e saída da compilação Sass:

```json
"scripts": {
  "sass": "sass source/main.scss build/main.css"
}
```

Esse script permite executar a compilação com:

```bash
npm run sass
```

Para automatizar esse processo e compilar sempre que houver alteração, criamos um segundo script com o `--watch`:

```json
"sass-watch": "sass source/main.scss build/main.css --watch"
```

E executamos com:

```bash
npm run sass-watch
```

Para parar o monitoramento, usamos `Ctrl + C` no terminal.

### Uso de Variáveis no Sass

No Sass, variáveis são declaradas com **cifrão ($)**, seguidas do nome (em camelCase, por convenção) e o valor:

```scss
$corPrincipal: #eee;
$corSecundaria: #111;
```

Essas variáveis podem ser utilizadas em qualquer parte do código Sass. Na compilação, o Sass substitui as variáveis pelos valores, gerando um CSS limpo e direto:

```scss
body {
  background-color: $corPrincipal;
}
```

Será compilado como:

```css
body {
  background-color: #eee;
}
```

### Diferença entre Sass e CSS puro

O CSS moderno também permite criar variáveis com `--nome-da-variavel`, mas essas são **dinâmicas** e dependem do escopo (como `:root` ou um seletor). Já o Sass usa **variáveis estáticas**, substituídas no momento da compilação, com mais flexibilidade para reutilização e legibilidade.

### Aninhamento de seletores

No CSS tradicional:

```css
header h1 {
  color: #111;
}
```

No Sass:

```scss
header {
  background-color: $corPrincipal;

  h1 {
    color: $corSecundaria;
  }
}
```

O Sass entende que `h1` está dentro de `header` e compila corretamente para o CSS esperado.

### Pseudo-classes com `&`

No CSS:

```css
button:hover {
  background-color: red;
}
```

No Sass:

```scss
button {
  &:hover {
    background-color: red;
  }
}
```

O `&` representa o seletor pai (`button`). Isso torna o código mais limpo e evita repetições.

### Condicional com classes

No Sass, também podemos usar `&.classe`:

```scss
button {
  &.sucesso {
    background-color: green;

    &:hover {
      background-color: $corSecundaria;
    }
  }
}
```

Isso se traduz no CSS como:

```css
button.sucesso {
  background-color: green;
}

button.sucesso:hover {
  background-color: #111;
}
```

### Código Final `main.scss`

```scss
$corPrincipal: #eee; 
$corSecundaria: #111;

body {
    background-color: $corPrincipal;
}

header {
    background-color: $corPrincipal;

    h1 {
        color: $corSecundaria;
    }
}

button {
    padding: 16px;
    background-color: $corSecundaria;
    color: $corPrincipal;

    &:hover {
        background-color: red;
    }

    &.sucesso {
        background-color: green;

        &:hover {
            background-color: $corSecundaria;
        }
    }
}
```

### Código Final `index.html`

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="build/main.css">
</head>
<body>
    <header>
        <div class="container">
            <h1>Nome do site</h1>
        </div>
    </header>
    <button class="sucesso" type="button">Clique aqui</button>
</body>
</html>
```

Essa aula mostrou como o Sass permite organizar o código CSS de forma mais **modular, reutilizável e limpa**, otimizando o desenvolvimento e a manutenção dos estilos.

## Aula 4 – Reutilizando código com Mixins (SASS)

Nesta aula, o foco principal foi aprender a **reutilizar código com mixins** em SASS. Os objetivos foram:

* Criar mixins personalizados;
* Definir mixins com parâmetros;
* Aplicar mixins em seletores específicos;
* Compreender como utilizar mixins em diferentes partes do CSS.

---

### Estrutura inicial do projeto

Começamos removendo arquivos antigos (`produto.scss`, `reset.scss` e `cores.scss`) e mantivemos apenas o `main.scss` na pasta `source`. O arquivo HTML também foi limpo, mantendo apenas a estrutura básica com o link para o `main.css` (gerado via build do SASS).

---

### Configuração e variáveis globais

Foram criados dois arquivos SCSS:

* `reset.scss`: aplicando um reset global com `box-sizing`, `margin` e `padding`;
* `variáveis.scss`: com a variável `$fonte-principal: 'Roboto, sans-serif';`

A fonte Roboto foi adicionada ao projeto via Google Fonts e aplicada no `reset.scss` com:

```scss
font-family: $fonte-principal;
```

Esses dois arquivos foram movidos para a pasta `config`, e o `reset.scss` foi importado em `main.scss` com:

```scss
@use 'config/reset';
```

---

### Estrutura HTML

A página foi composta por duas áreas principais:

1. `<header>` com um `<div class="container">` e um `<h1>` com o texto *Projeto SASS*.
2. `.form-container` com:

   * Um `<h2>` de chamada: *Se inscreva na newsletter para receber dicas sobre CSS*;
   * Um `<form>` com os campos:

```html
<label for="nome-completo">Nome completo</label>
<input type="text" id="nome-completo" required>

<label for="email">Seu melhor e-mail</label>
<input type="email" id="email" required>

<button type="submit">Cadastrar</button>
```

---

### Estilização e layout

A estrutura começou a ser estilizada no `main.scss`:

#### Corpo e container

```scss
body {
    background-color: #eee;
}

.container {
    max-width: 1024px;
    width: 100%;
    margin: 0 auto;

    h1 {
        text-align: center;
    }
}
```

#### Header

```scss
header {
    padding: 16px 0;
    background-color: greenyellow;
}
```

#### Formulário

A `.form-container` foi ajustada com uso de `calc()`:

```scss
.form-container {
    height: calc(100vh - 70px);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
```

> **Nota:** ao usar `flex-direction: column`, os eixos se invertem:
>
> * `justify-content` alinha verticalmente,
> * `align-items` alinha horizontalmente.

O formulário foi centralizado com:

```scss
form {
    width: 100%;
    max-width: 480px;
    margin-top: 40px;
}
```

---

### Introdução aos Mixins

Um **mixin** foi criado para centralizar estilos reutilizáveis:

```scss
@mixin elementoForm() {
    padding: 8px;
    display: block;
    width: 100%;
    margin-bottom: 16px;
}
```

Esse mixin foi aplicado em `input` e `button`:

```scss
input {
    @include elementoForm();
    background-color: transparent;
    border: none;
    border-bottom: 1px solid #000;
}

button {
    @include elementoForm();
}
```

Inicialmente, os estilos estavam agrupados diretamente nos seletores, mas isso causou problemas visuais, pois algumas propriedades não se aplicavam bem ao botão. A solução foi usar o mixin para compartilhar apenas as propriedades comuns.

---

### Mixins com parâmetros

Mixins também podem aceitar **parâmetros personalizados**, como:

```scss
@mixin elementoForm($margem) {
    margin-bottom: $margem;
}
```

E sua chamada:

```scss
@include elementoForm(80px);
```

> Sim, é possível passar **múltiplos parâmetros**, como:

```scss
@mixin estiloPersonalizado($bg, $corTexto, $padding) {
  background-color: $bg;
  color: $corTexto;
  padding: $padding;
}
```

Esse recurso torna o CSS mais dinâmico, reutilizável e adaptável a diferentes situações visuais no projeto.

## Aula 5 – Funções e Operadores no SASS

Esta é a última aula do módulo introdutório de SASS. A aula anterior, considerada como aula 4, tratava da reutilização de código com mixins. A primeira aula foi apenas introdutória e não continha conteúdo técnico relevante.

Nesta aula, o foco é o uso de **funções** e **operadores** no SASS. Os objetivos são:

* Entender como operadores matemáticos podem ser aplicados no SASS;
* Criar **funções personalizadas**;
* Explorar o uso de **funções nativas** da linguagem.

---

### Paleta de cores personalizada

O professor decidiu atualizar o esquema de cores do site utilizando a [Flat UI Colors](https://flatuicolors.com/). As cores escolhidas foram:

* **Cor de fundo:** Light Blue Ballerina `#C8D6E5`
* **Cor principal:** Aqua Velvet `#01A3A4`
* **Cor secundária:** Jade Dust `#00D2D3`

Essas cores foram adicionadas ao arquivo `variaveis.scss` com as seguintes variáveis:

```scss
// Fontes
$fontePrincipal: "Roboto", sans-serif;

// Esquema de cores
$corDeFundo: #c8d6e5;
$corPrincipal: #01a3a4;
$corSecundaria: #00d2d3;
```

---

### Estilizações com as novas variáveis

As variáveis foram importadas em `main.scss`:

```scss
@use 'config/variaveis';
```

#### Header:

* `background-color: variaveis.$corPrincipal;`
* `h1` dentro do header com `color: #fff;`

#### .form-container:

* `max-width: 760px;`
* `h2` com `font-size: pixelParaEm(40px);` e `text-align: center;`

#### Label:

```scss
label {
  font-weight: bold;
  cursor: pointer;
}
```

#### Botão:

```scss
button {
  background-color: variaveis.$corSecundaria;
  border: none;
  cursor: pointer;
  font-size: 18px;
  font-weight: bold;
  color: #fff;

  &:hover {
    background-color: lighten(variaveis.$corSecundaria, 10%);
  }
}
```

---

### Responsividade e uso de unidades dinâmicas

O professor destacou a importância de evitar valores fixos em `px` e preferir unidades relativas como `em`, principalmente para responsividade.

#### Criação da função personalizada `pixelParaEm`:

```scss
@use 'sass:math';

@function pixelParaEm($alvoEmPixel, $contextoEmPixel: 16px) {
  @return math.div($alvoEmPixel, $contextoEmPixel) + em;
}
```

Essa função evita a necessidade de fazer cálculos manuais e garante que o valor retornado seja acompanhado da unidade `em`.

#### Breakpoints definidos:

```scss
// Breakpoints
$mobile: 767px;
$tablet: 1023px;
```

#### Uso da media query:

```scss
@media screen and (max-width: variaveis.$mobile) {
  .container {
    max-width: 80%;
  }
}
```

---

### Funções nativas do SASS

O professor apresentou duas funções nativas para manipulação de cores:

* **`darken(cor, percentual)`**: escurece uma cor.
* **`lighten(cor, percentual)`**: clareia uma cor.

Exemplo de uso no `hover` do botão:

```scss
background-color: lighten(variaveis.$corSecundaria, 10%);
```

Essas funções são úteis para gerar variações visuais coerentes a partir das cores já definidas no projeto.

---

Com essas abordagens, a aula encerra o módulo introdutório de SASS com conceitos fundamentais de **reutilização de código**, **responsividade**, **funções** e **operações dinâmicas** no estilo da aplicação.

