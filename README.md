# Trabalhando com Imagens SVG

## Indice

1. [Conceituação Geral](#conceituação-geral)

2. [Extensão dos Arquivos](#extensão-dos-arquivos)

3. [O Básico do Sistema de Coordenadas](#o-básico-do-sistema-de-coordenadas)

## Conceituação Geral

A imagens SVG (Scalable Vector Graphics) são os gráficos geradas pelo uso do conceito de vetorização, que consiste em  usar um conjunto de funções geômetricos para descrever uma entidade gráfica. Essas funções são indicadas através de códigos específicos, com sintaxe de alto nível, que são os responsáveis por indicar ao navegador/leitor de imagens como e onde os gráficos devem ser desenhados na tela.

Elas são formuladas a partir de código puro e sua sintaxe é baseada no padrão XML (Extensible Markup Language) da W3C, que é aberto para todos. Por este mesmo motivo podem ser aninhadas diretamente dentro de códigos XHMTL e HTML5 de forma nativa, tem uma interface DOM para scripting (JS e outras linguagens de scripting), animação e podem ser comprimidas sem problemas. Além disso, devido ao seu funcionamento, podem ser redimensionados sem NENHUM tipo de perda na qualidade da imagem.

Elas são especialmente interessantes pois é possível trabalhar a partir de qualquer editor de código de sua preferência e visualizar o resultado diretamente no navegador. Para trabalhos mais complexos é recomendado utilizar editores de imagens mais completos e com suporte nativo ao formato SVG, como o **[Inkscape](https://inkscape.org/ "Inkscape's Homepage")**.

## Extensão dos Arquivos

Imagens SVG possuem como extensão de arquivo nativa o '.svg' (tudo minúsculo). Ela é suportada pela maioria dos browsers modernos e programas de edição de imagens que trabalham com vetorização.

O código que descreve imagens SVG pode se tornar complexo rapidamente e isso traz consigo o aumento do tamanho do arquivo. Então, também  existe a extensão '.svgz' (tudo minúsculo), ela foi criada pela Adobe para definir imagens SVG comprimidas. Apesar dessa extensão não ser tão comum, devido a inconsistencias de renderização, ela pode ser encontrada em determinados contextos.

## O Básico do Sistema de Coordenadas

As imagens SVG trabalham com a definição de uma 'tela de pintura', que limitará a área onde os elementos serão desenhados. Essa tela sempre será definida a partir do elemento raiz `<svg></svg>` [(sobre)](#o-elemento-raiz-svg), portanto, ele será o responsável por conter os gráficos e por definir a orientação do sistema de coordenadas para seus elementos filhos.

Com isso em mente, é possível dizer que o sistema de coordenadas utilizado em SVG é semelhante ao cartesiano. Ele contém um deslocamento ***x***, referente a horizontal, e um ***y***, referente a vertical, mas no caso do SVG a **ORIGEM** padrão do sistema de coordenadas fica localizada no canto superior esquerdo da tela. Isto é, o ponto que seria referente ao (0,0) estára sempre no topo do lado esquerdo, nisso ela se assemelha a forma como elementos HTML são renderizados em uma página.

É possível contornar essa situação e tornar o sistema de coordenadas mais palatável a nossa lógica. Apesar do sistema considerar o topo esquerdo da tela de pintura como origem do sistema de coordenadas, é possível delegar coordenadas negativas **(exemplo: -100)** a ele. Isso pode ser utilizado para posicionar os pontos ***x = 0*** e ***y = 0*** **(0,0)** no centro da tela de pintura, tornando a orientação dos elementos um trabalho mais fácil. Isso poderá ser visto com detalhes nos exemplos.

## A Ordem dos Elementos Importa

---

Conforme visto acima os elementos elementos do código possuem uma ordem segundo a qual são desenhados na tela. Essa ordem obedece estritamente a posição em que eles são declarados dentro do código e cria um sistema de camadas. Isso pode ser melhor visto a seguir:

```
<svg>
    <rect /> <!-- O retângulo será desenhado na terceira camada, portanto a mais baixa -->
    
    <circle /> <!-- O circulo será desenhado na segunda camada, portanto acima da terceira e abaixo da primeira -->

    <line /> <!-- A linha será desenhada na primeira camada, portanto acima de todas as outras --> 
</svg>
```

Assim é criado um sistema de camadas na imagem, semelhante ao que ja é visto em editores de imagens. Isso influência, principalmente, na forma como os elementos são visualizados na tela e como são trabalhados no código. Seguindo o exemplo acima a linha irá sobrepor os outros dois elementos, o circulo irá sobrepor o retângulo e, por fim, o retângulo terá sua área visível limitada pelos elementos que estão acima dele.

Isso permite que cada camada seja trabalhada de forma individual e a sobreposição permite criar imagens mais complexas. É possível tornar esse sistema de camadas ainda mais poderoso e flexível com o uso do elemento de agrupamento `<g></g>` [(sobre)](#o-elemento-de-agrupamento), entraremos em detalhes posteriormente.

## Aninhamento do SVG na Web

---

As imagens SVG não são para uso exclusivo na web, mas é nela que mais brilham devido a sua flexibilidade. Existem algumas formas diferentes de se aninhar elas em uma página, cada uma tem suas próprias vantagens e limitações. As mais conhecidas são:

1. Diretamente no Documento HTML5/XHTML

   Nos navegadores modernos é possível inserir o código SVG diretamente estrutura da página, pois eles são capazes de distinguir o código e desenhar a imagem da forma correta. Fazendo isso o código respeitará a hierarquia do DOM e pode ser manipulado através de CSS e scripting.

   <body>
    <svg
      version="1.1"
      width="300"
      height="200"
      xmlns="http://www.w3.org/2000/svg"
    >
      <rect width="100%" height="100%" fill="red" />

      <circle cx="150" cy="100" r="80" fill="green" />

      <text x="150" y="125" font-size="60" text-anchor="middle" fill="white">
        SVG
      </text>
    </svg>
  </body>

   Em

## Os Principais Elementos SVG

- O Elemento Raiz (svg)
- O Elemento de Agrupamento (g)
- O Elemento de Texto (text)
- O Elemento Retângulo (rect)
- O Elemento Círculo (cicle)
- O Elemento Elipse (ellipse)
- O Elemento Linha (line)
- O Elemento Polilinha (svg)
- O Elemento Polígono (svg)
- O Elemento Caminho (path)

### Utilizando CSS com SVG


### Trabalhando com Inkscape


### Referências

- MDN - SVG Tutorial

- W3Schools - SVG Tutorial

- W3C - SVG Especifications

- XML - Especifications

- Inkscape How To

- Exemplos
