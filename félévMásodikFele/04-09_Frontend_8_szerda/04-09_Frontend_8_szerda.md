# 8. TANANYAG CSS preprocesszorok 2025.04.09

többször előforduló értékek esetén pl ugyanaz a radius, color, akkor arra szoktunk törekedni, hogy ezeket az ismétlődő értékeket kiszervezzük változókba.

A sima css is támogat már változó kezelést.
Úgy néz ki, hogy a preprocesszorok css-t állítanak elő. 

css-ben van olyan hogy `calc(...)`
a változók is már elérhető a natív css-ben

A css preprocesszoroknak az a célja, hogy van egy forráskódunk
*** Rajz ***

eddig mi natív css-t írtunk. most megnézzük a preprocesszorokat amik natív css-t állítanak elő forráskód alapján

preprocesszor: előfeldolgozás

* CSS Preprocesszorok:
1) Sass / Scss 
2) Less
Ezeknek a lényege hogy a fejlesztők munkáját menkönnyítse
---------- 
Nem css prerocesszorok:
a) TailWind CSS
b) PureCSS
c) Lightning CSS -> **menő glowing effektek**


1. Sass 
https://sass-lang.com/install/

ehhez kell ezis: https://nodejs.org/en/download
Node.js a szervezoldali JavaScript
Ezt a verziót használjuk: v20.19.0 (LTS)
telepítés után teszteljük:
    `node -v`
    `npm --version`
Ezután sass telepítés:
    `npm install -g sass`

<link rel="stylesheet" href="main.sass">
Ez így nem működik
Ez is mutatja hogy egy weboldal HTML+CSS+JS-ből áll 
"A Sass kicsit ilyen pythonos"
Nem kell {} hanem a behúzások fontosak.

ezzel az utasítással lehet lefordítani a sass-t:
    sass source/stylesheets/index.scss build/stylesheets/index.css

Terminal -> belápünk a megfelelő mappába
lefuttatjuk: `sass main.sass output.css`
ezután meg ezt is beírhatjuk:  <link rel="stylesheet" href="output.css">

Sass fájlt írunk és az állítja elő a css-t.
Sass-ban a pontosvesszők is elhagyhatók
Minden változtatás után újra le kell futtatni.

** változó:
$text-color: #fafa

`sass --watch main.sass output.css`
állandóan figyelni fogja a változásokat. és nem kell folyamatosan manuálisan futtatni

* A less is nagyon hanonlóan működik *

## Refactoring példa 02-refactoring mappa


## 03-sass mappa -> 01-sass-basics

// Define mixins -> lényegében "függvények"
=rounded-corners($radius: 5px)
    border-radius: $radius

=border-color($color: red)
    border: 5px solid $color
	

mixin meghívása:
.container
    width: 80%
    margin: 0 auto
    margin-bottom: $margin-size-lg
    margin-top: $margin-size-lg
    padding: 20px
    +rounded-corners
    +border-color(white)

## 02-sass-advanced mappa
külön szokás kezelni:
main.sass
mixins.sass
variables.sass

Lehetséges feltételeket is készíteni:

@mixin text-color($param: dark)
    @if $param == light
        color: #fff
    @else if $param == dark
        color: #1f1c1c
    @else if $param == danger
        color: #c53c3c
		
		
main.sass-ban:
@import mixins.sass	
Manapság már jobban preferálják inkább a @use-t
ez csak akkor fogja hasznáni, ha ténylegesen kell

## 04-less mappa
** Az scss ugyanaz mint a Sass kivéve hogy ki van rakva a kapcsos zárójelek: {} és a pontosvesszők
pár apró változás még van
less-ben nincs --watch mint a sass-ban, hanem ezt külön package-ekkel lehet valahogy megoldani


*elsősorban css fejlesztők használják ezeket
Mi Bootstrap-et használunk
Az Angular pedig komponens alapú

--------------------


# TANANYAG: TypeScript

JavaScript
	- volt 
	- pár 
	- tulajdonsága pl:
	- dinamikusan típusos -> function(param) itt nem derlül ki hogy a param az mi? number? object? string?
	- gyengén típusos    -'

ehhez egy kis segítség volt:
/**jdoc/ -> de ez csak nekünk volt egy jelzés

NYLEVI PROBLÉMÁK -megoldás-> TypeScript
"Type" -> a típusos problémákat akarja megoldani legfőképp

a html-ben TypeScript fájlt nem tudunk megadni, csakis JS-t

lesz egy TypeScript forrásállomány ami átmegy egy compiler-en/fordítón és lesz belőle egy natív JavaScript
		
* https://www.typescriptlang.org/ *

telepítés:
`npm install typescript --save-dev`

.gitignore fájl létrehozása és beleírjuk hogy node_modules. Akkor a node_modules mappa nem lesz verziókövetve

futtatás:
`tsc app.ts` -> létrehoz egy app.js-t	
`tsc app.ts -watch`

	
(_super olyan mint c#-ban a base. tehát az őskontruktor meghívása)


## Snake játék
rétegzést fogunk használni

 	


