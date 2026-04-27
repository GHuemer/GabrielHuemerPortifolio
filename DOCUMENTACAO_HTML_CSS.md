# Documentação: HTML, CSS e Análise do Template de Portfólio

## 1. Diferença entre HTML e CSS

Depois de estudar o template do portfólio e analisar o código, consegui entender melhor a diferença entre essas duas tecnologias.

**HTML (HyperText Markup Language)** é basicamente o "esqueleto" da página web. Ele define a estrutura e o conteúdo. Quando eu abro o arquivo `index.html` deste portfólio, vejo que o HTML está responsável por:

- Definir o cabeçalho da página com as informações de navegação (`<header>`)
- Organizar as seções como "Sobre Mim", "Habilidades", "Projetos" e "Contato" usando `<section>`
- Colocar conteúdo como textos, imagens e links nos lugares certos
- Estruturar a hierarquia das informações (títulos, parágrafos, listas)

Por exemplo, no código vemos:
```html
<h1>Gabriel <span class="accent-text">Huemer</span></h1>
<h2>Desenvolvedor Full Stack & Mobile</h2>
<p class="lead">Especialista em...</p>
```

O HTML simplesmente diz "aqui tem um título grande, aqui tem um subtítulo, aqui tem um parágrafo".

**CSS (Cascading Style Sheets)** é o "pintor" da página. Ele pega essa estrutura que o HTML criou e deixa bonita. O CSS é responsável por:

- Definir cores, fontes e tamanhos de texto
- Posicionar os elementos na página (layouts)
- Adicionar espaçamento (margins e padding)
- Criar efeitos visuais como sombras, transições e animações
- Fazer a página ficar responsiva em diferentes tamanhos de tela

Então, **como eles trabalham juntos?** HTML é o conteúdo bruto, e CSS o apresenta de forma visual atrativa. Sem HTML não há conteúdo para exibir, e sem CSS a página seria um muro de texto sem graça. No nosso portfólio, o HTML define a estrutura das seções e o CSS (no arquivo `assets/css/main.css`) faz com que pareça um site moderno e profissional.

---

## 2. Exemplos de CSS e suas Propriedades

Escolhi três propriedades CSS que fazem diferença visível no portfólio:

### 2.1 - Propriedade `color`

**O que faz:** Define a cor do texto.

**Como afeta:** Muda a aparência do conteúdo textual. Cores diferentes podem trazer ênfase ou criar hierarquia visual.

**Exemplo de código encontrado no template:**
```css
.accent-text {
  color: #a06cd5;  /* Cor roxa/lilás */
}

h1 {
  color: #ffffff;  /* Texto branco no cabeçalho */
}
```

No `index.html`, vemos isso sendo usado:
```html
<h1>Gabriel <span class="accent-text">Huemer</span></h1>
```

A palavra "Huemer" fica em uma cor diferente, criando destaque visual.

### 2.2 - Propriedade `background-color`

**O que faz:** Define a cor de fundo de um elemento.

**Como afeta:** Separa visualmente os conteúdos e cria "caixas" que organizam a página.

**Exemplo do template:**
```css
.hero {
  background-color: #1a1a1a;  /* Fundo escuro */
}

.light-background {
  background-color: #f8f9fa;  /* Fundo claro */
}
```

Na seção "Habilidades Técnicas" (`#skills`), a página usa `light-background` para criar contraste com as outras seções escuras.

### 2.3 - Propriedade `margin` e `padding`

**O que fazem:** 
- `margin`: espaçamento externo (entre o elemento e outros)
- `padding`: espaçamento interno (entre o conteúdo e a borda)

**Como afetam:** Controlam quanto espaço há ao redor do conteúdo, deixando a página mais "respirada" e legível.

**Exemplo do template:**
```css
.section-title {
  margin-bottom: 50px;  /* Espaço abaixo do título */
}

.project-card {
  padding: 20px;  /* Espaço interno da caixa do projeto */
  margin: 15px;   /* Espaço ao redor da caixa */
}
```

Isso faz com que as caixas de projetos não fiquem coladas umas às outras e pareçam mais profissionais.

### 2.4 - Propriedade `font-size`

**O que faz:** Define o tamanho do texto.

**Como afeta:** Cria hierarquia de importância. Textos maiores parecem mais importantes.

**Exemplo:**
```css
h1 {
  font-size: 48px;      /* Título grande */
}

p {
  font-size: 16px;      /* Texto normal */
}

small {
  font-size: 12px;      /* Texto pequeno */
}
```

---

## 3. As Três Formas de Aplicar CSS

### 3.1 - CSS Inline

**Como funciona:** Você coloca o CSS diretamente na tag HTML usando o atributo `style`.

**Exemplo de código:**
```html
<p style="color: blue; font-size: 18px;">Este texto é azul e maior</p>

<div style="background-color: #f0f0f0; padding: 20px;">
  Caixa com fundo cinza e espaçamento interno
</div>
```

**Vantagens:**
- Rápido de aplicar quando precisa fazer uma mudança específica
- Não precisa de arquivo extra

**Desvantagens:**
- Muito difícil de manter em projetos grandes (fica bagunçado)
- Não reutiliza estilos (precisa repetir o CSS em cada elemento)
- Mistura HTML com CSS, deixando o código confuso
- Difícil mudar o estilo de vários elementos ao mesmo tempo

No portfólio do Gabriel, **quase não há CSS inline**, o que é uma boa prática.

---

### 3.2 - CSS Interno (ou Embedded)

**Como funciona:** Você coloca as regras CSS dentro de uma tag `<style>` no `<head>` da página HTML.

**Exemplo de código:**
```html
<!DOCTYPE html>
<html>
<head>
  <title>Meu Portfólio</title>
  <style>
    body {
      background-color: #f0f0f0;
      font-family: Arial, sans-serif;
    }
    
    h1 {
      color: #333;
      font-size: 32px;
    }
    
    .section {
      margin: 20px;
      padding: 15px;
    }
  </style>
</head>
<body>
  <h1>Gabriel Huemer</h1>
  <p class="section">Desenvolvedor Full Stack</p>
</body>
</html>
```

**Vantagens:**
- Melhor que inline porque pelo menos organiza o CSS em um só lugar
- Funciona em uma única página sem precisar de arquivo externo
- É considerado relativamente limpo para pequenos projetos

**Desvantagens:**
- O arquivo HTML fica muito grande e pesado
- Não dá pra reutilizar os estilos em outras páginas do site
- Dificulta a manutenção quando o site cresce
- Mistura apresentação com estrutura

O template do portfólio do Gabriel usa CSS interno de forma mínima (basicamente para imports).

---

### 3.3 - CSS Externo

**Como funciona:** Você cria um arquivo `.css` separado e linka ele no HTML usando a tag `<link>`.

**Exemplo de código:**

Arquivo `index.html`:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Meu Portfólio</title>
  <link href="assets/css/main.css" rel="stylesheet">
</head>
<body>
  <h1>Gabriel Huemer</h1>
  <p class="section">Desenvolvedor Full Stack</p>
</body>
</html>
```

Arquivo `assets/css/main.css`:
```css
body {
  background-color: #f0f0f0;
  font-family: 'Roboto', sans-serif;
  margin: 0;
  padding: 0;
}

h1 {
  color: #333;
  font-size: 32px;
  margin-bottom: 10px;
}

.section {
  margin: 20px;
  padding: 15px;
  background-color: white;
  border-radius: 8px;
}
```

**Vantagens:**
- O arquivo HTML fica limpo e focado no conteúdo
- Reutiliza estilos em múltiplas páginas (um arquivo CSS serve para o site todo)
- Fácil manter e atualizar estilos (muda uma vez e reflete em tudo)
- O arquivo CSS é carregado uma vez e cacheado pelo navegador (mais rápido)
- Separação clara entre estrutura (HTML) e apresentação (CSS)

**Desvantagens:**
- Requer um arquivo extra (mais um arquivo para gerenciar)
- Para sites muito simples pode ser "overkill"

**O template do portfólio usa CSS externo, que é a abordagem mais profissional.** Vemos no `index.html`:
```html
<link href="assets/css/main.css" rel="stylesheet">
<link href="assets/vendor/bootstrap/css/bootstrap.min.css" rel="stylesheet">
```

---

## 4. Análise do Template de Portfólio - Tipo de CSS Utilizado

O template escolhido foi **GHuemer/GabrielHuemerPortifolio** que está hospedado aqui mesmo no repositório.

### Tipos de CSS encontrados:

**1. CSS Externo (principal):**
- `<link href="assets/css/main.css" rel="stylesheet">` - Arquivo CSS customizado
- `<link href="assets/vendor/bootstrap/css/bootstrap.min.css" rel="stylesheet">` - Bootstrap framework
- `<link href="assets/vendor/bootstrap-icons/bootstrap-icons.css" rel="stylesheet">` - Ícones Bootstrap
- `<link href="assets/vendor/aos/aos.css" rel="stylesheet">` - Efeitos de animação
- Outros arquivos CSS de vendors

**2. CSS Interno:**
Praticamente não há. O template é bem estruturado.

**3. CSS Inline:**
Também não há uso significativo de inline styles.

**Conclusão sobre o uso:** O template segue a **melhor prática**, usando CSS externo como principal método de estilização.

---

## 5. Identificação dos Diferentes Seletores CSS

Analisando o código do `index.html` e o padrão de um template Bootstrap bem estruturado, identifiquei os seguintes tipos de seletores:

### 5.1 - Seletores Simples

**O que são:** Selecionam elementos baseado em seu nome, classe, ID ou seletor universal.

**Exemplos encontrados no template:**

```html
<!-- Elemento por tag (Universal) -->
<p>Texto em parágrafo</p>

<!-- Classe -->
<h2 class="section-header">Sobre Mim</h2>

<!-- ID -->
<section id="hero">...</section>

<!-- Tag simples -->
<header>...</header>
```

**Possível CSS correspondente:**
```css
/* Seletor de tag simples */
p {
  font-size: 16px;
  line-height: 1.6;
}

/* Seletor de classe */
.section-header {
  font-size: 32px;
  font-weight: bold;
}

/* Seletor de ID */
#hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
}

/* Seletor universal */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

### 5.2 - Seletores Pseudo-classes

**O que são:** Selecionam elementos com base em um estado (como hover, focus, visited, etc).

**Exemplos do template:**

```html
<!-- Links que podem ter diferentes estados -->
<a href="#portfolio" class="btn btn-primary">Ver Projetos</a>
<a href="https://github.com/GHuemer" class="github"><i class="bi bi-github"></i></a>
```

**CSS correspondente que provavelmente existe:**
```css
/* Quando o mouse passa sobre um link */
a:hover {
  color: #a06cd5;
  text-decoration: underline;
}

/* Links já visitados */
a:visited {
  color: #888;
}

/* Quando um elemento recebe foco (teclado ou click) */
button:focus {
  outline: 2px solid #a06cd5;
}

/* Primeiro elemento filho */
li:first-child {
  margin-top: 0;
}

/* Último elemento filho */
li:last-child {
  margin-bottom: 0;
}
```

Especificamente no portfólio vemos elementos como:
```html
<div class="skill-item">
  <h4>Python</h4>
  <div class="progress">
    <div class="progress-bar" role="progressbar" aria-valuenow="90"></div>
  </div>
</div>
```

Que provavelmente tem CSS como:
```css
.skill-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 15px rgba(0,0,0,0.1);
}
```

### 5.3 - Seletores Combinadores

**O que são:** Combinam múltiplos seletores para selecionar elementos baseado em relacionamento.

**Exemplos do template:**

```html
<section id="skills">
  <div class="container">
    <div class="row">
      <div class="col-lg-6">
        <div class="skills-category">
          <h3>Linguagens de Programação</h3>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Possível CSS com combinadores:**
```css
/* Combinador descendente (espaço) - seleciona h3 dentro de skills-category */
.skills-category h3 {
  font-size: 24px;
  margin-bottom: 20px;
}

/* Combinador filho (>) - seleciona div que é filho direto de row */
.row > div {
  margin-bottom: 30px;
}

/* Combinador irmão adjacente (+) - seleciona h3 que vem logo após h2 */
h2 + h3 {
  margin-top: 10px;
}

/* Combinador irmão geral (~) - seleciona qualquer p que vem após h2 */
h2 ~ p {
  color: #666;
}
```

No template vemos:
```html
<nav id="navmenu" class="navmenu">
  <ul>
    <li><a href="#hero">Home</a></li>
    <li><a href="#about">Sobre Mim</a></li>
  </ul>
</nav>
```

Que provavelmente tem:
```css
/* Irmão adjacente */
.navmenu ul li + li {
  border-left: 1px solid #ccc;
}

/* Descendente */
.navmenu a {
  color: white;
  text-decoration: none;
}
```

### 5.4 - Seletores Pseudo-elementos

**O que são:** Selecionam e estilizam uma parte específica de um elemento.

**Exemplos do template:**

```html
<h1>Gabriel <span class="accent-text">Huemer</span></h1>
<p class="description">Estudante de Sistemas de Informação...</p>
```

**CSS com pseudo-elementos:**
```css
/* ::before - adiciona conteúdo antes do elemento */
.accent-text::before {
  content: "✦ ";
  color: #a06cd5;
}

/* ::after - adiciona conteúdo depois do elemento */
.section-header::after {
  content: "";
  display: block;
  width: 60px;
  height: 4px;
  background-color: #a06cd5;
  margin: 10px auto 0;
}

/* ::first-line - estiliza primeira linha de texto */
.description::first-line {
  font-weight: bold;
}

/* ::first-letter - estiliza primeira letra */
.description::first-letter {
  font-size: 24px;
  font-weight: bold;
  color: #a06cd5;
}

/* ::selection - estiliza texto selecionado */
p::selection {
  background-color: #a06cd5;
  color: white;
}
```

Também vemos no portfólio elementos como:
```html
<div class="contact-item">
  <div class="icon-box">
    <i class="bi bi-envelope"></i>
  </div>
  <div class="content">
    <h4>Email</h4>
  </div>
</div>
```

Que podem usar:
```css
.contact-item::before {
  content: "";
  position: absolute;
  left: 0;
  width: 4px;
  height: 100%;
  background: #a06cd5;
}
```

### 5.5 - Seletores de Atributos

**O que são:** Selecionam elementos baseado em atributos HTML ou valores de atributos.

**Exemplos do template:**

```html
<img src="assets/img/profile/profile-2.webp" alt="Gabriel Huemer" class="profile-image">
<a href="https://github.com/GHuemer" class="github">...</a>
<div data-aos="fade-right" data-aos-delay="100">...</div>
<input type="email" name="email" required>
```

**CSS com seletores de atributos:**
```css
/* Seleciona elementos com atributo alt */
img[alt] {
  border-radius: 8px;
}

/* Seleciona links que terminam em .github */
a[href$=".github"] {
  color: #333;
}

/* Seleciona elementos com href que contém "github" */
a[href*="github"] {
  color: #0366d6;
}

/* Seleciona elementos com href que começa com "http" */
a[href^="http"] {
  color: blue;
}

/* Seleciona inputs com type email */
input[type="email"] {
  border: 1px solid #ccc;
  padding: 8px;
}

/* Seleciona elementos com atributo data-aos */
[data-aos] {
  animation-duration: 0.8s;
}

/* Seleciona elementos com atributo required */
[required] {
  border-color: #ff6b6b;
}
```

No código específico do portfólio:
```html
<div class="col-lg-6" data-aos="fade-right" data-aos-delay="100">
```

Há CSS como:
```css
[data-aos="fade-right"] {
  opacity: 0;
  transform: translateX(-30px);
}

[data-aos-delay="100"] {
  animation-delay: 0.1s;
}
```

---

## Conclusão

Analisando este template de portfólio profissional, fica claro que:

1. **HTML e CSS trabalham juntos:** HTML estrutura o conteúdo e CSS o torna visualmente atrativo
2. **CSS externo é a melhor prática** para projetos maiores
3. **Seletores CSS são ferramentas poderosas** que permitem estilização precisa e eficiente
4. **Bootstrap é um framework que abstrai muito do CSS**, mas é bom conhecer os seletores por baixo

O template do Gabriel é um excelente exemplo de boas práticas web, utilizando estrutura HTML semântica, CSS externo bem organizado, e frameworks como Bootstrap para acelerar o desenvolvimento mantendo qualidade visual profissional.

