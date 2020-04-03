# Performance web: Front-end

- [Performance web: Front-end](#performance-web-front-end)
	- [Minificação](#minifica%c3%a7%c3%a3o)
	- [Habilitar GZIP](#habilitar-gzip)
	- [Imagens](#imagens)
		- [Redimensionar imagens](#redimensionar-imagens)
		- [Otimização de imagens](#otimiza%c3%a7%c3%a3o-de-imagens)

Performance: site rápido melhora UX, relação direta entre performance e conversão, economia de banda/recursos do servidor e do cliente.

A performance que o usuário sente é, geralmente, mais atribuída ao front-end do que do back-end.

## Minificação

- Tamanho do site afeta diretamente a performance
- Minificação: remove espaços, comentários, ...
- Separar código minificado do código original (que ainda será necessário para o desenvolvedor). Criar outro diretório, como `dist` para os arquivos minificados.
- Ferramenta web:
  - https://refresh-sf.com/ (minify HTML, CSS e JS)
- Automatização:
  - `uglyfyjs` para node
  - utilizando `gulp`

## Habilitar GZIP

- Habilitar compressão `gzip` nos recursos de texto é uma das práticas mais impactantes no tamanho final da página
- Servidor zipa arquivos e envia para o navegador que "deszipa"
- Configuração depende do servido - Para o `ngix`, por exemplo:

```
server {
  listen 3030;
  root /path/to/dist;

  gzip on;
  gzip_types text/css application/javascript image/svg+xml;
}
```

## Imagens

- Imagens representam em média 2/3 do peso total das páginas
- Formatos: - `jpeg`: melhor formato para fotos na web - `svg`: vetorial, ícones com desenhos gráficos - `png`: alternativa quando svg não é suficiente
- Observação: salvar arquivos originais antes de otimizar

### Redimensionar imagens

- Redimensionar a imagem no tamanho que será exibida (exemplo, se é exibido em 50x50px, não preciso de arquivos com mais do que isso)
- Ferramentas: - Photoshop ou outro editor de imagens - Linha de comando com [ImageMagick](https://imagemagick.org/) - `mogrify -resize 50x50 site/assets/img/aluno-*`

### Otimização de imagens

- Metadados das imagens geralmente são desnecessárias para a página
- Otimização _lossy_: otimização com perdas visuais. Bom verificar otimização lossy para ver se não houve muito prejuízo de design.
- Otimização _lossless_: otimização sem perdas visuais (remove somente metadados e informações não essenciais - mas imagem final é idêntica)
- Ferramentas online e desktop: - http://kraken.io (png e jpeg) - https://tinypng.com/ (png e jpeg) - https://www.jpegmini.com/ - https://jakearchibald.github.io/svgomg/ (otimiza svg) - https://riot-optimizer.com/ (para desktop)
- Automatizar com gulp imagemin (otimiza JPGs, PNGs e SVGs de forma automática)
- Automatizar manualmente na linha de comando: - jpegtran (para jpeg): `jpegtran -progressive -optimize site/assets/img/aluno-adriano.jpeg > dist/assets/img/aluno-adriano.jpeg` - pngcrush (para png): `pngcrush site/assets/img/icon-diferencial-1.png dist/assets/img/icon-diferencial-1.png` - svgo (para svg): `svgo site/assets/img/categoria-business.svg dist/assets/img/categoria-business.svg`
- [ZorroSVG](http://quasimondo.com/ZorroSVG/): permite criar "JPEGs com transparência". Muita gente usa foto em PNG por causa da transparência mas isso é péssimo pra performance. O zorro usa filtros SVG pra separar a layer de transparência em uma mask separada. Na prática, JPEG com transparência.

---

https://www.alura.com.br/curso-online-otimizacao-performance-web
