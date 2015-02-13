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


## Bilingue ou multlingue nao funciona no meu Single Page? 

R = Faça as alterações seguintes:
`sites\all\modules\single_page_website\single_page_website.module` na linha ::111 
```php
Original:
  $anchor = "spw-" . str_replace("/", "-", drupal_get_path_alias($href));
  
Modificado:
  
  $lang = $GLOBALS['language']->prefix ;

  $anchor = "spw-" . $lang .'-'. str_replace("/", "-", drupal_get_path_alias($href));
  

```



