**eleventy**
    = npm package
    = jednoduchý generátor statických stránek
    - spustíme ho pomocí npm run start
    - základem je main.njk - tento soubor se nemění a používá se všude kde je uveden nahoře
            - tento soubor se uloží do složky templates ve složce src
    - ostatní .html stránky vkládáme přímo do src
    - všechny .css soubory se vkládají do složky css v src
    - pomocí tzv. bundlů a bundlerů se dá spojit např. několik .css do jednoho
    - jelikož v bundlu jsou všechny .css najednou musím všechno dělit do sekcí
            - proto si musím obsah HTML zařadit do sekce (např: newpage.html -> veškerý obsah zařadíme do <section class={NAZEV_SEKCE}> -> potom v newpage.css se odkazujeme na celé HTML pomocí oné sekce) 
    - složka dist = všeno co mám ve složce src se překopíruje do dist a to dávám zákazníkovi a nasazuji na server
    - v rámci webu se používá relativní adresevání
    - musíme přidas složku s obrázky do konfigurace, aby se zkopírovala do dist (eleventyConfig.addPassthroughCopy("src/images");) -> pokud se odkazujeme na obrázek od jinud než z index.html tak musím odejít o složků výš ../images/image.png -> pokud chci obrázem přímo v index.html tak ty .. nepíšu a pokud něco blbne tak to **vypnu a zapnu** :D
            - toto použijeme jen ve chvíli že děláme malý web
- 

