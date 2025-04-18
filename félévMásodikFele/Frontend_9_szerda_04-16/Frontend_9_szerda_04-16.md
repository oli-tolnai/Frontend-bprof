munkahely: evosoft
# Frontend 9 szerda 04.16

## ZH

Ea kifejtős: 17/20

Ea teszt 10/10

Gyak: 6/10

82,5%


./ használjuk relatív megadás, mert tárhely feltöltés esetén e nélkül nem fog működni
pl.: `./bootstrap.css` *ábra1*
ha ez nincs ott akkor a root mappába fogja keresni

**Fontosak az ábrák jegyzetelésnél


*Csináljunk magunknak gyakorlófeladatokat



típus feladatok begyakorlása nem rendes tanulás



Mi az a callback: https://www.youtube.com/watch?v=_LsQy_oAAx4


mennyit kell készülni a tárgyra:
1 kredit = 25-30 munkaóra (kontakt +önálló)


# TANANYAG: typescript

typescript = superset of JS
superset = a js kiterjesztése *ábra2*

**Snake
a kígyó blokkok tömbje



# TANANYAG: angular

Az angular egy keretrendszer (framework)
	- sok eszköz együttes használata (a keretrendszerek komplexebbek)
	- az app kódja formálható és struktúrálható (js könyvtár ezt nem csinálja)
	- előre megírt `best-prectice` dolgok használata
						'-> "nem kell feltalálni a kereket"
	
	-*React -> facebook
	-*Vue	-> célja a react és angular akkori pozitív előnyös részeit összegzése 
	-*Angular -> google				
framework hell: js -> vue.js -> nuxt.js

feladattól függ hogy kell e keretrendszer


------------------------- angulart szembeállítjuk a föggvénykönyvtárakat
függvény könyvtárak libs()
	- előre megírt kód snippetek	
	- xyDtect(...) nem formálja és nem struktúrálja
	

-------------------------
**AJAX -> Asynchronous JavaScript and XML
https://systemoutofmemory.com/cdn/shop/articles/ajax_f4b39b0c-ffc9-47a4-bea0-e0c4a151d088_1024x1024.png?v=1533603180

keretrendszereket akár úgy is el tudjuk nevezni, hogy **SPA** -> Single Page Application
SPA-> nincs oldal újratöltés, az ajax hívások ilyenek voltak

spa lifecycle: https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTjmKBXRgu33o1BgGfc0MwgAaJh4vynbDG9rQ&s

Az AJAX nem egy darab technológia, hanem meglévőek összessége: async, XMLHttpRequest, XML/JSON

** XMLHttpRequest -> XHR 
ez még a mai napig is velünk van
kérdés:
hol tudjuk megnézni és mi az XHR?:
developer nézet -> network -> filter kereső alatt Fecth/XHR

Az oldal nem töltődik őjra csak a benne lévő tertalma *ábra3*


----------
** JQuery ** - régebben használták 
	- **lib!** (nem keretrendszer)
	https://www.w3schools.com/jquery/trysel.asp
	- John Resig
	
	
-------------
### Angular	
	
https://angular.dev/tools/cli/setup-local
npm install -g @angular/cli
CLI -> command line interface

`ng new demo-app --standalone=false` -> új projekt - ng - angular rövidítése

ezután `sass` kiválasztás
ezután: `N` 
`l`
`cd demo app`

src mappa:
index.html -> app-root - minden amit írunk ide vagyis ennek helyére fog kerülni

app mappa:
app.component.sepc.ts ts fáljok tesztelésére van (ki lehet törölni)

keretrendszerek fontos része a *komponens alapúság*

*ábra4*
app -html	
	 css (sass)
	 js (ts)
ez az app komponens
	
minden komponensnek VAN SAJÁT html, css, js fájla
	 
	
futtatás nem liveserver hanem beépített terminál

`ng serve`
`N`
elkezdi lebuildelni az egészet
	 
ez folyamatus buildelést és watch-olást csinál, tehát a terminált le is csukkhatjuk

ts változót html-ben élérni (template-ezés): {{title}}

app.component.html-ben amit beírunk az belekerül az index html-ben lévő app-root -ba


*keretrendszerek egyik legfontosabb része a kétirányú adatkötés*

ngModel-lel lehet bindingolni, adatkötést csinálni, html input-től a ts-be
app.Moduele.ts:

@NgModule imports:
`FormsModule` enterezni kell hogy beimporálja
	'-> kell hozzá hogy működjön a binding
	
zhban: két irányű adatkötés: https://miro.medium.com/v2/resize:fit:1024/0*M0UhDhQ-21achCiF.png  two way data binding


ngfor -> htmlben for ciklus amiben pl megadjuk egy a ts-ben lévő listáű

ngIf -> feltételes / kondícionális megjelenítés

angular Dicertives -> pl NgIf, ngfor...

ngClass -> lehet adatkötni osztályt is | ezt ki lehet helyben is fejteni, de akár ki lehet szervezni egy külön metódusba
keretrendszerekkel lehet mindent adatkötni

lehet pl a disable állapotot is adatkötni és még nagyon sok mindent


új osztályok:
export class User{}
tehát lehet bővíteni osztályokkal

házi
input mezőt cseréljük le text-re és usereket lehessen hozáadni nem stringként hanem user objectként


fetch elemeken is ngfor-ral fogunk végig menni

