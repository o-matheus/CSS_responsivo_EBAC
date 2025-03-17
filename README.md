# CSS Responsivo
## Menu
[Aula 1 - Utilizando o Viewport](#aula-1---utilizando-o-viewport)  
[Aula 2 - Trabalhando com unidades de medidas flexíveis](#aula-2---trabalhando-com-unidades-de-medida-flexíveis)  
[Aula 3 - breakpoints e media queries](#aula-3---breakpoints-e-media-queries)  
[Aula 4 - Trabalhando com imagens responsivas](#aula-4---trabalhando-com-imagens-responsivas)  
[Aula 5 - Menu Dropdown](#aula-5---menu-dropdown)  
[Aula 6 - CSS Grid](#aula-6---display-grid)  
[Aula 7 - Layout responsivo](#aula-7---layout-responsivo)  

## Aula 1 - Utilizando o Viewport
O **viewport** é a área visível de um site dentro da janela do navegador. Podemos ajustar seus parâmetros para melhorar a experiência do usuário.

### Configurações do Viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
- **`initial-scale`** → Define o zoom padrão da página.
- **`maximum-scale`** → Controla o valor máximo de zoom.
- **`user-scalable`** → Permite ou impede que o usuário altere o zoom.

### Medidas Relacionadas
- **px** → Pixels fixos.
- **vw** → Largura relativa ao viewport (100vw = toda a largura da tela).
- **vh** → Altura relativa ao viewport (100vh = toda a altura da tela).

Lembrando que se um container tiver um tamanho definido, ele ocupará apenas esse espaço, e não toda a tela.

---
## Aula 2 - Trabalhando com Unidades de Medida Flexíveis
### Unidades Fixas:
- **px** → Pixels.
- **pt** → Pontos (usado em impressão).

### Unidades Flexíveis:
- **vw** → Largura relativa ao viewport.
- **vh** → Altura relativa ao viewport.
- **em** → Baseado no tamanho da fonte do elemento pai.
- **rem** → Baseado no tamanho da fonte do elemento raiz (`html`).
- **%** → Baseia-se no tamanho do elemento pai.

Essas unidades flexíveis são essenciais para criar layouts responsivos e adaptáveis a diferentes tamanhos de tela.

---
## Aula 3 - Breakpoints e Media Queries
As **media queries** permitem aplicar estilos CSS condicionalmente, baseando-se no tamanho da tela ou outras características do dispositivo.

### Exemplo de Media Query
```css
@media screen and (max-width: 768px) {
    body {
        background-color: lightgray;
    }
}
```
Aqui, o fundo do `body` muda para cinza claro em telas menores que 768px.

### Conceitos-Chave
- **Mobile First** → Criar o site responsivo primeiro para dispositivos menores e depois adaptar para telas maiores.
- **Principais Breakpoints**:
    - **Celular** → Até 768px.
    - **Tablet** → 768px - 1024px.
    - **Notebook** → 1024px - 1440px.
    - **Desktop** → Acima de 1440px.

### Operadores em Media Queries
| Operador | Significado | Exemplo |
| --- | --- | --- |
| **`and`** | Ambas as condições precisam ser verdadeiras | `(min-width: 600px) and (max-width: 1200px)` |
| **`,`** (OU) | Se qualquer condição for verdadeira, aplica-se o estilo | `(max-width: 600px), (orientation: portrait)` |
| **`not`** | Inverte a condição | `not (min-width: 600px)` |
| **`only`** | Aplica apenas em navegadores modernos | `only screen and (min-width: 800px)` |

### Tipos de Mídia
| Tipo | Uso |
| --- | --- |
| **`screen`** | Para telas de dispositivos. |
| **`print`** | Para impressão de documentos. |
| **`speech`** | Para leitores de tela (acessibilidade). |
| **`all`** | Para qualquer tipo de mídia. |

---
## Aula 4 - Trabalhando com Imagens Responsivas
A tag `<picture>` permite exibir imagens diferentes dependendo das condições do viewport.

### Exemplo de Uso
```html
<picture>
    <source media="(max-width: 600px)" srcset="imagem-pequena.jpg">
    <img src="imagem-padrao.jpg" alt="Imagem responsiva">
</picture>
```
Caso a tela tenha até 600px de largura, a imagem `imagem-pequena.jpg` será carregada. Caso contrário, `imagem-padrao.jpg` será exibida.

### Imagens no CSS
Embora seja possível adicionar imagens no CSS, isso pode afetar a acessibilidade, pois leitores de tela não interpretam corretamente essas imagens.

```css
div {
    background-image: url('imagem.jpg');
    height: 300px;
    width: 300px;
    background-repeat: no-repeat;
    background-size: cover; /* Ocupa todo o espaço disponível */
}
```
### Valores de `background-size`:
- **contain** → Mantém a proporção, mas pode não preencher todo o espaço.
- **cover** → Ajusta a imagem para cobrir todo o espaço, podendo cortar partes da imagem.

Utilizar corretamente as imagens responsivas melhora o desempenho e a experiência do usuário em diferentes dispositivos.


## Aula 5 - Menu dropdown 
### HTML 5
`<input type="search" placeholder="Busque no site">`  
Aprendi sobre esse tipo de input, que é utilizado como um campo de pesquisa.

```html
<li>
    Esporte
    <ul>
        <li><a href="#">Futebol</a></li>
        <li><a href="#">Economia</a></li>
        <li><a href="#">Fórmula 1</a></li>
    </ul>
</li>
```
Dentro da tag `li`, podemos adicionar submenus com outra `ul` e outras `li`.

### CSS
```css
.menu li {
    float: left;
    list-style: none;
}

.submenu {
    display: none;
    list-style: none;
    background-color: red;
    position: absolute;
    left: 0;
    width: 300px; /* Para que o elemento não fique quebrado e as palavras fiquem lado a lado */
    top: 100%; /* Faz com que o elemento filho comece logo após o elemento pai */
}

.menu > li {
    float: left;
    list-style: none;
    padding: 16px;
    border-top: 4px solid transparent;
    position: relative;
}

.menu li:hover {
    border-color: red; 
}

.clear-left {
    clear: left;
}
```
Aqui estamos utilizando `float`, mas acredito que seja apenas para compreendermos seu funcionamento. Atualmente, ele caiu em desuso devido ao `display: flex;` e `display: grid;`. Embora funcionasse com adaptações, `float` não foi projetado para trabalhar com layouts. Pesquisando sobre o assunto, percebi que ele é útil em CSS legado ou quando queremos que o texto de um elemento flutue ao redor de uma imagem, como em um artigo ou legenda.

`list-style: none;`  
Remove os marcadores das listas não ordenadas.

`position: relative;`  
Garante que o elemento filho não ultrapasse os limites do elemento pai.

`position: absolute;`  
No menu retrátil, é importante definir `position: absolute;` para que, ao expandir, o menu não altere o layout adicionando espaçamentos desnecessários. Sem `position: relative;` no pai, o menu pode invadir outros elementos, pois ele considera o elemento pai maior, ao qual pertence. Quando o pai possui `position: relative;`, a relação entre os elementos fica mais controlada.

`left: 0;`  
Faz com que o submenu comece o mais à esquerda possível dentro do menu.

`border-top: 4px solid transparent;` `border-color: red;`  
Inicialmente, me perguntei por que usar essas duas propriedades em vez de definir a cor diretamente no `.menu li:hover`. Depois, percebi que, sem a borda transparente antes, haveria um deslocamento do elemento ao passar o mouse por cima, modificando o design de forma indesejada.

## Aula 6 - Display Grid

### HTML 6
```html
<div class="conteudo">
    <main>
        <section class="destaque">
            <h2>Em destaque</h2>
            <article class="noticia">
                <a href="#">
                    <img src="https://placehold.co/320x320" alt="placeholder 320x320">
                    <h3>Lorem ipsum dolor sit amet consectetur adipisicing elit. At quibusdam ea vero eos soluta tenetur.</h3>
                </a>
            </article>
        </section>
    </main>
    <aside>
    </aside>
</div>
```
Estamos construindo aqui a seção de conteúdo do nosso site.

- **`<main>`** → Representa o conteúdo principal do site (centralizado).
- **`<aside>`** → Representa o conteúdo secundário (nas bordas).
- **`lorem10`** → Define o tamanho do texto gerado pelo **Lorem Ipsum**. O número define a quantidade de palavras.
- **`<img src="https://placehold.co/320x320" alt="placeholder 320x320">`** → Neste `src`, estamos usando uma imagem placeholder. Ela tem a dimensão da imagem que será utilizada no design final, permitindo visualizar a disposição dos elementos corretamente. No site `placehold.co`, qualquer tamanho especificado após `/` será o tamanho da imagem retornada.

---

### CSS 6
```css
.submenu {
    background-color: #fff;
}

.conteudo {
    display: grid;
    grid-template-columns: 70% 30%;
}

.noticias {
    display: grid;
    grid-template-columns: repeat(3, 32.6%);
    column-gap: 1%;
    row-gap: 5%;
}
```

### Explicação do Código CSS:

- **`background-color: #fff;`** → Define uma cor de fundo branca para melhor legibilidade.
- **`display: flex;`** → Ideal para layouts **unidimensionais** (linha ou coluna).
- **`display: grid;`** → Melhor para trabalhar com **duas dimensões** (linhas e colunas).
- **`grid-template-columns:`** → Define o número e o tamanho das colunas, podendo ser valores fixos ou flexíveis.
- **`grid-template-rows:`** → Define o número e o tamanho das linhas, podendo ser valores fixos ou flexíveis.
- **`fr`** → Unidade de medida do Grid, ajusta o tamanho conforme o espaço disponível do container, sem depender do tamanho da fonte ou do elemento pai.
- **`grid-template-columns: 70% 30%;`** → No exemplo, os elementos do conteúdo "Em destaque" ocupam **70%** do container, enquanto "Novidades" ocupa os **30%** restantes, criando um bom contraste entre o conteúdo principal e o secundário.
- **`grid-template-columns: repeat(3, 32.6%);`** → `repeat(qtd_colunas, espaço ocupado)` evita repetição manual de valores, tornando o código mais limpo.
- **`column-gap: 1%;`** → Define o espaçamento entre as colunas.
- **`row-gap: 5%;`** → Define o espaçamento entre as linhas.

## Aula 7 - Layout Responsivo

Para construir o layout responsivo, começamos a trabalhar com **media queries**, que são regras CSS aplicadas apenas quando determinadas condições são atendidas. No caso da aula, as media queries foram acionadas quando a tela alcançava um valor mínimo ou máximo de largura.

### CSS 7
```CSS
@media screen and (min-width: 768px) and (max-width: 1023px) {

}

@media screen and (max-width: 767px) {

}
```

A partir disso, criamos regras específicas para que, dependendo do dispositivo, o conteúdo ficasse melhor disposto.

### 📌 Propriedades mais comuns para celulares:
🔹 **display: block;** (Elementos em linha passam a ocupar toda a largura)  
🔹 **display: flex; flex-direction: column;** (Alinha elementos em coluna no mobile)  
🔹 **max-width: 100%; height: auto;** (Para imagens responsivas)  
🔹 **font-size: rem;** (Texto que se ajusta automaticamente)  
🔹 **@media (max-width: 768px) {}** (Para estilos específicos de celular)  
🔹 **overflow-x: hidden;** (Evita rolagem horizontal)  
🔹 **background-size: cover;** (Imagens de fundo responsivas)  

### 📌 Propriedades mais comuns para tablets:
🔹 **Use @media (max-width: 1024px)** para definir estilos para tablets.  
🔹 **Ajuste width: 90% e max-width: 100%** para manter elementos proporcionais.  
🔹 **Use display: flex e grid-template-columns** para reorganizar layouts.  
🔹 **Reduza fontes com font-size: 1.2rem;** para melhor legibilidade.  
🔹 **Ajuste imagens com object-fit: cover;** para evitar distorções.  
🔹 **Aumente a área de clique dos botões** para melhorar a usabilidade.  