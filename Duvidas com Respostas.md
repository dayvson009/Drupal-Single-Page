## Como colocar título nas páginas? 

R = No modulo "Single Page Website" ele nao mostra os titulos, a única solução é alterando o arquivo
`sites\all\modules\single_page_website\single_page_website.module` na linha ::116 
```php
Original:
    $output .= '<a name="' . $anchor . '"></a><div id="' . $anchor . '" class="single_page_wrapper"><div class="single_page">';

Modificado:
    $output .= '<a name="' . $anchor . '"></a><div id="' . $anchor . '" class="single_page_wrapper"><div class="single_page"><h2 class="title-page-'. $href .' title-main">'.$item['#title'].'</h2>';

```
Eu apenas adicionei uma tag `<h2>`. Onde o conteúdo é o título da página igual o menu.
