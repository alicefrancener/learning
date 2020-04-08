# Performance web: Front-end

- [Performance web: Front-end](#performance-web-front-end)
  - [Minificação](#minifica%c3%a7%c3%a3o)
  - [Habilitar GZIP](#habilitar-gzip)
  - [Imagens](#imagens)
    - [Redimensionar imagens](#redimensionar-imagens)
    - [Otimização de imagens](#otimiza%c3%a7%c3%a3o-de-imagens)
  - [Economizando requests](#economizando-requests)
    - [Diminuir dependências](#diminuir-depend%c3%aancias)
    - [Concatenar CSS e JS](#concatenar-css-e-js)
    - [Recursos inline](#recursos-inline)
    - [Sprites em PNG](#sprites-em-png)
    - [Sprites em SVG](#sprites-em-svg)
  - [Paralelizar requests](#paralelizar-requests)
  - [Ferramentas](#ferramentas)
    - [Chrome DevTools](#chrome-devtools)
    - [Sites de análise de performance](#sites-de-an%c3%a1lise-de-performance)

Performance: site rápido melhora UX, relação direta entre performance e conversão, economia de banda/recursos do servidor e do cliente.

A performance que o usuário sente é, geralmente, mais atribuída ao front-end do que do back-end.

## Minificação

- Tamanho do site afeta diretamente a performance
- Minificação: remove espaços, comentários, ...
- Separar código minificado do código original (que ainda será necessário para o desenvolvedor). Criar outro diretório, como `dist` para os arquivos minificados.
- Ferramenta web:
  - https://refresh-sf.com/ (minify HTML, CSS e JS)
- Automatização: utilizando `uglyfyjs`, `cssnano`,`htmlmin` no `gulp`

## Habilitar GZIP

- Habilitar compressão `gzip` nos recursos de texto é uma das práticas mais impactantes no tamanho final da página
- Servidor zipa arquivos e envia para o navegador que "deszipa"
- Configuração depende do servido 
- Para o `ngix`, por exemplo:

```
server {
  listen 3030;
  root /path/to/dist;

  gzip on;
  gzip_types text/css application/javascript image/svg+xml;
}
```

Para checar se o `gzip` está habilitado, checar no header do response o campo `content-encoding: gzip`.

## Imagens

- Imagens representam em média 2/3 do peso total das páginas
- Formatos: 
  - `jpeg`: melhor formato para fotos na web 
  - `svg`: vetorial, ícones com desenhos gráficos 
  - `png`: alternativa quando svg não é suficiente
- Observação: salvar arquivos originais antes de otimizar

### Redimensionar imagens

- Redimensionar a imagem no tamanho que será exibida (exemplo, se é exibido em 50x50px, não preciso de arquivos com mais do que isso)
- Ferramentas: 
  - Photoshop ou outro editor de imagens 
  - Linha de comando com [ImageMagick](https://imagemagick.org/) 
  - `mogrify -resize 50x50 site/assets/img/aluno-*`

### Otimização de imagens

- Metadados das imagens geralmente são desnecessárias para a página
- Otimização:
  - _lossy_: otimização com perdas visuais. Bom verificar otimização lossy para ver se não houve muito prejuízo de design.
  - _lossless_: otimização sem perdas visuais (remove somente metadados e informações não essenciais - mas imagem final é idêntica)

- Ferramentas online e desktop: 
  - http://kraken.io (png e jpeg) 
  - https://tinypng.com/ (png e jpeg)
  - https://www.jpegmini.com/ 
  - https://jakearchibald.github.io/svgomg/ (otimiza svg) 
  - https://riot-optimizer.com/ (para desktop)
- Automatizar com gulp `imagemin` (otimiza JPGs, PNGs e SVGs de forma automática)
- Automatizar manualmente na linha de comando: 
  - jpegtran (para jpeg): `jpegtran -progressive -optimize site/assets/img/aluno-adriano.jpeg > dist/assets/img/aluno-adriano.jpeg` 
  - pngcrush (para png): `pngcrush site/assets/img/icon-diferencial-1.png dist/assets/img/icon-diferencial-1.png` 
  - svgo (para svg): `svgo site/assets/img/categoria-business.svg dist/assets/img/categoria-business.svg`
- [ZorroSVG](http://quasimondo.com/ZorroSVG/): permite criar "JPEGs com transparência". Muita gente usa foto em PNG por causa da transparência mas isso é péssimo pra performance. O zorro usa filtros SVG pra separar a layer de transparência em uma mask separada. Na prática, JPEG com transparência.

---

https://www.alura.com.br/curso-online-otimizacao-performance-web


## Economizando requests

### Diminuir dependências

- Muitas vezes gastamos requests e bytes com frameworks pesados e desnecessários
- Avaliar bem se o uso deles é se realmente necessário ou podem ser substituídos por JavaScript puro

### Concatenar CSS e JS

- Concatenar arquivos `css` diminuem número de requests. Diminuir o número de requests faz com que os downloads sejam mais rápidos no HTTP 1. Temos menos concorrência nas 6 conexões disponíveis, logo, recursos precisam aguardar menos para serem baixados. De bônus, o GZIP funciona muito bem em recursos texto concatenados com bastante repetição, como CSS.
- Utilizar `useref` no `gulp` para isso, na **build**, por exemplo
- Trade-off: 
	- quando colocamos tudo em um arquivo só, do ponto de vista da produção, estamos perdendo a capacidade de cachear os arquivos individualmente, se mexermos uma linha de um arquivo, terá que baixar tudo de novo. Se mexêssemos uma linha de um arquivo em outro cenário ele iria baixar apenas aquele arquivo que foi alterado.
	- talvez não seja necesário carregar todos js e css na página home, por exemplo, se ele não usar todos componentes

### Recursos inline

- Para diminuir requests também pode ser recuros inline. Ou seja, ao invés de fazer uma requisição para um recurso css, posso incluir esse estilo dentro do meu arquivo html.
- Posso fazer inline de scripts JS, estilos, svgs...
- Obs: se fizer isso com determinado arquivo, remover ele da concatenação que possa ter feito
- Vale a pena para recursos pequenos
- Avaliar pensando em cache. Se colocar inline em uma página e for usar o mesmo recurso em outra página, não estará cacheado, então terei que fazer nova requisição
- Ideal é que HTML seja < 14 Kb porque é o tamanho aproximado de 10 segmentos TCP que é o padrão da janela inicial de novas conexões
- Automatizar: usar `inline-source` no `gulp`
	- incluir o atributo `inline` na minha tag: `<script inline src="assets/js/home.js"></script>`
	- esse arquivo será embutino diretamente no html após rodar a tarefa no `gulp`

### Sprites em PNG

- Manualmente (pode ser mais "seguro" e não é difícil):
	- 1. Gerar sprite
		- Utilizar o progama ImageMagick com o comando: `convert site/assets/img/*.png -append site/assets/img/diferenciais.png`
	- 2. Editar css para usar o novo arquivo: adicionar sprite gerada no `background-image` e definir posição do ícone a ser usado com `background-position`
- Automação: utiliar `spritesmith` ou `sprity` no `gulp` ou na linha de comando. Dessa forma, pode produzeir o sprite e o css modificado com as posições corretas dos ícones.

### Sprites em SVG

- Usando [`svg-sprite`](https://github.com/jkphl/svg-sprite)
- Cada arquivo será um `<symbol>` dentro de `<svg>` 
- No html usar `<svg><use xlink:href="assets/img/categorias.svg#mobile"/></svg>` que ele usará o `<symbol>` do arquivo svg com id="mobile"

## Paralelizar requests

- Como temos um limite de ~6 conexões por hostname, uma técnica para paralelizar os requests é usar mais de um hostname
- Para isso, precisamos de um segundo domínio/subdomínio
- Usando hostnames distintos cada um poderá ter 6 conexões simultâneas
- Basta alterar no HTML os requests que queremos jogar pra o endereço paralelo, ma boa ideia é jogar as imagens para carregarem por outro hostname
- De dois a três hostnames é o ideal, uma vez que muitos hostnames paralelos podem causar congestionamento na rede e atrasar o browser

## Ferramentas

### Chrome DevTools

- o Chrome DevTools nos permite analisar muitas coisas da performance do site
- Utilizando a aba Network podemos analisar:
  - O waterfall dos requests, mostrando a sequência de requisições, o tempo de espera de cada um, o tempo de resposta do servidor, o tempo de download de cada recurso
  - O número de conexões simultâneas, que limita a quantidade de requests em paralelo (no Chrome são 6 requisições em paralelo)
  - O número total de requests embaixo e o tamanho final da página.

- É possível simular uma conexção real (ao invés de localhost) usando o recurso de *throttling* do DevTools (ex. simula 3G, 4G, ...)
- Bom desabilitar cache (*disable cache*) no DevTools

### Sites de análise de performance

- https://developers.google.com/speed/pagespeed/insights/
- https://www.webpagetest.org/