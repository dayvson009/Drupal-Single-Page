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


## Multlingue o scroll nao desce? 

R = Faça as alterações seguintes:
`sites\all\modules\single_page_website\single_page_website.module` na linha ::111 
```php
Original:
  $anchor = "spw-" . str_replace("/", "-", drupal_get_path_alias($href));
  
Modificado:
  
  $lang = $GLOBALS['language']->prefix ;

  $anchor = "spw-" . $lang .'-'. str_replace("/", "-", drupal_get_path_alias($href));
  

```


## Minha "VIEWS" está mostrando todos os conteúdos Mutilingue na mesma pagina, como faço pra separar?


FILTER CRITERIA
Content: Published (Yes)
Node translation: Child translation

R = Primeiramente escolha a linguagem em padrãro no meu caso é o português.
 Agora em `estrutura\views\sua_view`.

 Em `FILTER CRITERIA` clique em `adicionar`. Em "Buscar" escreva em 'language', marque-o e aplique,
 na caixa `Configure filter criterion: Conteúdo: Idioma` selecione a opção `Current user's language`
 , aplique, salve. vualá hehehe...


