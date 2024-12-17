**DOKUMENTACE 11TY(eleventy)**
https://www.11ty.dev/docs

**eleventy**
    = npm package
    = jednoduchý generátor statických stránek (engine pro web stránky)
    - spustíme ho pomocí **npm run start**
        npm = ovl. balíčkovacího systému
        run = spuštění příkazu
        start = příkaz (příkaz najdeme v package.json -> scripts)
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
- npm run build
- občas se může stát že to zamrzne jak widle - musíme restartovat :)))))

**NPM**
- npm run se vždy dívá do package.json v otevřené složce
- dev dependences = balíčky použíté ve vývoji, ale ve finále se nepoužívají
- balíčky po stažení (npm install) uloženy v node_modules složce
- když se nám stáhnou i další balíčky s tím co chceme tak se jedná o dependencies toho co checeme
- pokud chceme použít další demendenci tak ji musíme nainstalovat

*eleventy.config.js*

= sem zadáme jednotlivé složky které v projektu budeme používat
        - definujeme sem kdy jsou uloženy kódy, obrázky, atd.
        - definujeme složky jejichž obsah chceme nakopírovat do dist (fin. složky)
                - např.: eleventyConfig.addPassthroughCopy("src/images");

        - složka dist = to co bude ve finále uvedeno do provozu
        - musíme ji nastavit jako output:   eleventyConfig.setOutputDirectory("./dist");

*css-bundler.njk*

= spojujeme .css (stylesheety) do jednoho a potom už upravujeme nej pomocí sekcí
- díky spojování stylesheetů si můžeme dát ten pospojovaný do main.njk a už to nemusíme měnit jen si v jednotlive styly musíme rozlišit na sekce

*main.njk*

= hl. template do kterého nějak umisťujeme všechno ostatní
        - tzv. (kostra webu)
- kontent ostatních indexů se vkládá do {{content | safe}}
- title stránky ostatních indexů se vkládá do {{title}} v title

parametry ostatních indexů se píší do tzv. headmeter
---
layout: {NAZEV_TEMPLATE(vetsinou main.njk)}
title: {NAZEV_STRANKY}
tags: {TAGY}
---

parametr layout = určuje kde se bude renderovat daný index
parametr title = určuje titul stránky
parametr tags = nadefinujeme jednotlivé kolekce, odkaz na více zároveň, můžeme seskládat více sekcí dohromady


- můžeme mít více layoutů

**DOPSAT**
<section>
  <ul>
    {%- for post in collections.menu -%}
        <li>{{ post.data.title }}</li>
    {%- endfor -%}
  </ul>
</section>

!! - to co přes watchdog vidíme je ve skutečnosti složka dist
