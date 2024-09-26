# Media Queries

## O que são Media Queries?
Imagine que você está construindo um site e quer garantir que ele fique bonito e fácil de usar em qualquer dispositivo: um computador (desktop), um tablet ou um celular. O problema é que as telas desses dispositivos têm tamanhos e orientações diferentes, então o que fica bom em uma tela grande pode não funcionar tão bem em uma tela pequena.

**Media Queries** são como regras que você coloca no seu CSS (o código que controla o estilo do seu site) para dizer: "Se a tela for deste tamanho ou estiver nesta orientação, faça essas mudanças no design". Elas permitem que o site "responda" ao ambiente em que está sendo exibido, por isso dizemos que as media queries ajudam a criar designs responsivos.

## Como eles funcionam?
A lógica básica das media queries é bem simples. O CSS verifica a largura da tela, a orientação do dispositivo (vertical ou horizontal), ou até o tipo de mídia (como impressão ou visualização na tela) e então aplica os estilos definidos para aquela condição.

Aqui está um exemplo básico de uma media query que muda o fundo de uma página dependendo da largura da tela:

```
/* Estilo padrão */
body {
  background-color: white;
}

/* Se a largura da tela for menor que 600px (como em celulares) */
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}

```
No exemplo acima, a página terá um fundo branco por padrão. No entanto, se o dispositivo tiver uma largura de tela menor que 600 pixels (como a maioria dos celulares), o fundo mudará para azul claro. Isso permite que o site tenha uma aparência diferente dependendo do tamanho da tela.

## Exemplos práticos:
**Impressão (Print)** - Se você deseja criar uma página que fique bonita tanto na tela quanto no papel (se alguém quiser imprimir), você pode usar media queries para isso. No exemplo abaixo, escondemos elementos desnecessários como o menu, e ajustamos o conteúdo para que ele seja impresso de maneira adequada.

```
@media print {
  /* Ocultar menus e seções irrelevantes para impressão */
  nav, .header, .footer {
    display: none;
  }
  
  /* Ajustar a largura do conteúdo para caber na página impressa */
  .content {
    width: 100%;
    font-size: 12pt;
  }
  
  /* Estilizar links para aparecerem com o URL na impressão */
  a::after {
    content: " (" attr(href) ")";
  }
}

```
Estamos dizendo que, quando alguém for imprimir a página, os menus e o cabeçalho serão escondidos, e o conteúdo será redimensionado para caber na página impressa. Além disso, os links terão o URL visível para que a pessoa que imprimir saiba para onde o link levaria.

**Menu Responsivo** - Dependendo do dispositivo em que a página é visualizada, o menu pode ser exibido de diferentes formas. Em uma tela maior (como a de um desktop), o menu pode aparecer na horizontal. Mas em uma tela pequena (como a de um celular), pode ser mais prático que ele apareça na vertical.
```
/* Estilo base para desktop */
nav ul {
  display: flex;
  justify-content: space-around;
  list-style-type: none;
}

/* Para telas pequenas como smartphones */
@media (max-width: 600px) {
  nav ul {
    display: block;
    text-align: center;
  }
  
  nav ul li {
    padding: 10px 0;
  }
}

/* Para tablets */
@media (min-width: 601px) and (max-width: 1024px) {
  nav ul {
    display: flex;
    flex-direction: column;
    text-align: left;
  }
}

```
- **Desktop:** O menu aparece horizontalmente, com os itens dispostos lado a lado.
- **Celular (até 600px):** O menu muda para vertical, com os itens aparecendo um abaixo do outro.
- **Tablet (entre 601px e 1024px):** O menu continua sendo flexível, mas os itens são dispostos em uma coluna vertical, e alinhados à esquerda.

**Galeria de Imagens Responsiva** - 
Se você tem uma galeria de fotos em seu site, você pode usar media queries para ajustar o número de colunas de imagens dependendo do tamanho da tela:
```
/* Estilo base para desktop */
.gallery {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

/* Para telas menores como smartphones */
@media (max-width: 600px) {
  .gallery {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Para tablets */
@media (min-width: 601px) and (max-width: 1024px) {
  .gallery {
    grid-template-columns: repeat(3, 1fr);
  }
}
```
- **Desktop:** A galeria exibe 4 colunas de imagens.
- **Smartphones (até 600px)**: A galeria diminui para 2 colunas, para que as imagens fiquem maiores e mais fáceis de visualizar.
-**Tablets (entre 601px e 1024px):** A galeria mostra 3 colunas.
Isso garante que as imagens sejam exibidas de forma agradável e organizada em qualquer dispositivo.

**Layout de Texto em Colunas** - Outra aplicação prática das media queries é ajustar a quantidade de colunas de texto dependendo da orientação da tela. Em dispositivos que estão sendo usados na horizontal (landscape), podemos mostrar mais colunas de texto, enquanto em dispositivos na vertical (portrait) podemos exibir menos colunas para facilitar a leitura.

```
/* Para dispositivos em modo retrato (portrait) */
@media (orientation: portrait) {
  .content {
    column-count: 1;
  }
}

/* Para dispositivos em modo paisagem (landscape) */
@media (orientation: landscape) {
  .content {
    column-count: 2;
  }
}
```

- **Modo Retrato (portrait):** O conteúdo aparece em uma única coluna.
- **Modo Paisagem (landscape):** O conteúdo é exibido em duas colunas, para aproveitar melhor o espaço na tela.

## **Conclusão**
As media queries são uma ferramenta poderosa no CSS que permitem que você crie páginas da web que se adaptam a diferentes dispositivos e situações. Seja mudando a forma como o conteúdo é exibido em dispositivos móveis, ajustando o layout para impressão, ou adaptando o site a diferentes orientações de tela, as media queries ajudam a garantir que seu site fique sempre agradável e fácil de usar, independentemente do dispositivo que seu visitante estiver utilizando.


