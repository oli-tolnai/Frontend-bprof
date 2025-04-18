# <span style="font-variant:small-caps;">Frontend 9 szerda 04.16</span> 
<br>

# TANANYAG: Frontend gyakorlati és elméleti zh eredményértékelés


### Témakörök:

- **JavaScript (JS)**: Az egyik legfontosabb, dinamikus weboldalak készítésére alkalmas nyelv. Gyakorlati alkalmazásai közé tartozik például az űrlapellenőrzés, interaktív elemek létrehozása, aszinkron adatkérés (AJAX) stb.
- **CSS (Cascading Style Sheets)**: A weboldalak megjelenésének (dizájn, színek, elrendezés, animációk) kialakítására szolgál. A gyakorlatban kiemelt szerepet kap a reszponzív dizájn (különböző eszközökhöz való igazodás) készítésében.
- **Bootstrap**: Egy népszerű, nyílt forráskódú CSS-keretrendszer, amely előre elkészített komponenseket (gombok, űrlapok, rácsrendszer stb.) és reszponzív elrendezést biztosít a gyorsabb fejlesztéshez.
- **HTML (HyperText Markup Language)**: A weboldalak szerkezetének leírására szolgáló jelölőnyelv. Minden weboldal alapja, struktúrát ad a tartalomnak (pl. címsorok, bekezdések, listák, táblázatok).


### Ezek működésének gyakorlati alkalmazása:

- A frontend fejlesztés során a HTML-lel létrehozzuk a weboldal vázát.
- A CSS-sel formázzuk, stílusossá tesszük az elemeket.
- A Bootstrap segítségével gyorsan és könnyedén készítünk modern, mobilbarát felületeket sablonok vagy komponensek használatával.
- A JavaScript működést, interaktivitást és dinamikus tartalomkezelést ad az oldalaknak.


### Az óra témája:

A mai órán az elkészült dolgozatok értékelését végeztük el. Megbeszéltük a tipikus hibákat, sikeres megoldásokat, illetve áttekintettük a legfontosabb tanulságokat. Az értékelés során külön kitértünk a technológiák helyes alkalmazására, a kódban előforduló hibákra és a kreatív megoldásokra is.

## Gyakorlati hibák és tippek

- **Saját CSS használata**:
Ha a feladat külön kéri, mindig hozz létre saját CSS fájlt, és ne csak a Bootstrap alapértelmezett stílusaira hagyatkozz!
- **Helyes elérési út megadása**:
Ha a forrásfájl egy mappában található, a relatív elérési utat pontosan add meg:
`href="./bootstrap.css"`
Ne csak `href="bootstrap.css"` legyen, mert bár ez működik Live Server-rel, a deploy (élesítés) során könnyen eltörhetnek a hivatkozások. A forrásfájlok elérési útjának követése és helyes megadása nagyon fontos! Ha ez nincs ott akkor a root mappában fogja keresni
![relativUtvonal](https://github.com/user-attachments/assets/29776e7c-48d1-40e9-a3aa-0cf53946c999) 
- **Formázási problémák javítása**:
Ha elcsúszik a formázás vagy rendezetlen a kód, VS Code-ban az **Alt + Shift + F** billentyűparancsot használd a gyors formázáshoz.
- **Bootstrap táblázat (table) használata**:
    - Ismerd a Bootstrap `table` működését (osztályok, például `table`, `table-striped` stb.).
    - Tudnod kell, hogyan lehet JavaScript-ből hivatkozni a táblázat egyes elemeire.
    - A táblázat szerkezete:
        - `<thead&gt>`: Fejléc, ide kerülnek a címkék
        - `<tbodyy`: Ide generál a JavaScript dinamikusan sorokat (pl. adat beolvasás után)
    - Példa: A `<tbody>`-ba alapból nem írunk semmit, oda a JS tölti be az adatokat.
- **JSON beolvasása és megjelenítése JS-sel táblázatban**:
    - A `fetch()` vagy más adatlekérő módszerek segítségével tölts be JSON fájlt.
    - A JSON elemeit különböző JavaScript ciklusokkal (pl. `forEach`, `map`) jelenítsd meg táblázat soronként.
    - Fontos: Ha nem működik a fetch (például CORS vagy elérési gondok miatt), akkor közvetlenül JS tömbként másold be az adatokat a fájlba, így is meg tudod jeleníteni az információt.
- **Időmenedzsment**:
    - A vizsgán/rövid idő alatt összetett megoldást írni nagy kihívás. Prioritás: működő alapstruktúra, majd utána a részletek.
- **Problémamegoldás**:
    - Ha valami nem működik (pl. fetch), alkalmazz alternatív megoldást, ne akadjon el a fejlesztés!
- **HTML és JS szétválasztása**:
    - Törekedj arra, hogy a HTML szerkezet és a JavaScript logika jól elkülönüljön egymástól, így átláthatóbb és könnyebben karbantartható lesz a kód.
- **Szűrések, feldolgozások JavaScript-ben**:
    - A JSON feldolgozás után tudnod kell egyszerű szűréseket, például a legkevesebbet kereső dolgozó keresése, vagy társai.
    - Ezekhez olyan JS tömbműveleti függvényeket kell ismerni, mint: `filter`, `find`, `sort`, `reduce`.
- **Classok helyes megadása**:
    - Több class felsorolásakor NINCS vessző a class-ok között.

```html
<div></div>
```

- **Async/await ismerete**:
    - Az aszinkron adatkezelés modern JavaScript-ben alap. Ismerd az `async/await` használatát, működését, és tipikus hibáit!
- **Inline CSS**:
    - Kivételes esetben (egy-egy elemhez) használható, de inkább külön CSS fájlban vagy `<style>` blokkban add meg a stílusokat!
- **JS: createElement és innerText nem láncolható**:
    - Például hibás:

```js
document.createElement('div').innerText = 'szöveg';
```

    - Helyesen:

```js
const elem = document.createElement('div');
elem.innerText = 'szöveg';
```

    - Az utasításokat külön sorban, egymás után írd le, ne láncold össze őket.

---

## Elméleti részek kiegészítése

### Callback függvények

- **Callback függvényeket nem returnoljuk, hanem meghívjuk**:
Egy callback függvény lényege, hogy egy másik függvény hívja meg, amikor valamilyen esemény bekövetkezik vagy egy adott művelet befejeződik.
Példa:

```js
function doSomething(callback) {
  // valamilyen logika
  callback(); // Meghívás, nem return
}
```

Mi az a callback: https://www.youtube.com/watch?v=_LsQy_oAAx4

### Ábrák szerepe

- **Ábrák nagyon fontosak**:
Elméleti anyaghoz mindig jó, ha a magyarázatokat ábrákkal is támogatod. Ha nem tudsz ábrát rajzolni, keress netről szemléletes diagramokat (pl. Google Képek: "JavaScript event loop diagram").


### Szemléletes kódpéldák

- **Szemléletes kódpélda minden elméleti magyarázathoz**:
Egy jó kódpélda segít megérteni az elmélet gyakorlati alkalmazását.
- **Optimalizált szó jelentése**:
Az "optimalizált" azt jelenti, hogy egy megoldás már a lehetőségekhez képest a legjobb állapotban van. Nincs olyan, hogy "optimalizáltabb", mert az optimalizált abszolút: vagy elérted az optimumot, vagy nem.


### Tanulási módszerek

- **Probléma a csak ChatGPT-vel való tanulással**:
Ha csak AI-tól tanulsz, könnyen előfordulhat, hogy nem érted meg a mögöttes problémát, csak másolsz. A Google-nél céltudatos kereséssel jutsz el a lényegi válaszokhoz és közben magad kell kiválasztani, értelmezni, kipróbálni a megoldást.
- **Saját feladatok gyártása**:
Önállóan alkoss feladatokat és próbáld azokat megoldani! Ez segít a mélyebb megértésben és kreatív gondolkodásban.


### Szakmai kommunikáció és záróvizsga

- **Záróvizsgán szóban kell magyarázni**:
Ismerned kell a szakmai szókincset, tudnod kell magyarázni ábrákat, folyamatokat. Nem elég a leírás, gyakorold a szóbeli magyarázatot is!


### Kódolvasás és -értelmezés

- **Kód olvasása/értelmezése nem elég!**
    - Töltsd le a mintakódokat, futtasd le őket!
    - Módosítsd a kódot, egészítsd ki, cseréld ki részeket, hogy valóban megértsd a működését.
    - A kód aktív eszköz, nem csak olvasmány!


### `fetch` szintaxisa

- **Alaposan tanuld meg a `fetch` hívás pontos szintaxisát**:
Vizsgán nincs Google, tehát tudnod kell fejből!
Példa:

```js
fetch('adatok.json')
  .then(response =&gt; response.json())
  .then(data =&gt; console.log(data))
  .catch(error =&gt; console.error(error));
```

- **Kihívás**: Légy tisztában az aszinkron működéssel, hibakezeléssel (`catch`), és a JSON feldolgozásával.


### Szakszerű megfogalmazás

- **Pontos szakmai fogalmazás**
Legyél képes egyszerűen és pontosan leírni, hogy egy adott fogalom (pl. event loop, async/await) mit jelent, hogyan működik, miért fontos.

---

## Event Loop részletesen

### Mi az Event Loop?

Az **event loop (eseményciklus)** a JavaScript motor egyik alapvető része, amely lehetővé teszi a nem-blokkoló, aszinkron műveletek végrehajtását egyetlen szálon (single-threaded környezetben).

### Hogyan működik?

1. **Call Stack (Hívási verem)**:
Ide kerülnek a szinkron műveletek (függvényhívások, változók, stb.). Mindig csak egy függvény fut egyszerre.
2. **Web APIs / Background APIs**:
Az aszinkron kódokat (pl. setTimeout, fetch, event listener) a böngésző motor kezeli a háttérben.
3. **Callback Queue (Várakozó sor)**:
A háttérben lefutó aszinkron műveletek befejezése után azok callback-jait ide helyezi a rendszer.
4. **Event Loop**:
Az event loop folyamatosan figyeli, hogy a call stack üres-e. Ha igen, a callback queue első elemét átteszi a call stack-be, és az elindulhat.

### Ábra (keresd netről: “event loop diagram”):

[MDN Event Loop Ábra](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop#the_event_loop)


```
[ Call Stack ] <-- Event Loop <-- [ Callback Queue ]
        ^                                   |
        +------ Web APIs ---- fetch, setTimeout, stb. 
```


### Példakód:

```js
console.log('Első');

setTimeout(() => {
  console.log('Második (asynchronous)');
}, 0);

console.log('Harmadik');
```

**Várható kimenet:**

```
Első
Harmadik
Második (asynchronous)
```

**Magyarázat**:
A `setTimeout` callback-je a Web API-hoz kerül, majd a callback queue-ba helyezi az event loop, miután a call stack kiürült.

### Miért fontos?

- Lehetővé teszi, hogy felhasználói interakciók, szerverválaszok vagy egyéb aszinkron események ne állítsák meg a fő futási szálat.
- Ha nem érted, mi történik a háttérben, könnyen hibás aszinkron kódot írhatsz (pl. race condition, deadlock).
<hr><br><br><br>



# TANANYAG: TypeScript (TS)


**Mi az a TypeScript?**
- TypeScript = superset of JavaScript | *superset* = a js kiterjesztése

	![supersetOfJs](https://github.com/user-attachments/assets/ac9bdd50-eae7-4f6a-91b3-f24a78ab56e6)
- A TypeScript a JavaScript „supersetje”, vagyis a JavaScript kibővítése.
- Minden, ami JavaScript, az TypeScript-ben is érvényes – de a TypeScript ad hozzá típusosságot, OOP-tulajdonságokat (osztályok, interfészek), fejlettebb szerkesztés támogatást.
- Kód:

```ts
let age: number = 22;
```








<br><br><br>

# TANANYAG: Angular, Frameworkök és Könyvtárak

### Angular – Miért keretrendszer?

- **Angular** egy fejlett keretrendszer (framework), amit a Google fejleszt.
- A keretrendszerek (pl. Angular, React, Vue) a frontenden egységes szerkezetet, best practice-ket adnak ("nem kell feltalálni a kereket") , támogatnak routingot, állapotkezelést, űrlapkezelést, stb.
- A keretrendszer sok eszköz együttes használata, így ezek komplexebbek is mint például egy library
- Az app kódja formálható és struktúrálható (js könyvtár ezt nem csinálja)
- _Előny:_ Komplett megoldásokat kínálnak a fejlesztés szinte minden részére, emiatt támogatják a projekt struktúrálását, a moduláris kódbázist és az újrafelhasználhatóságot.

### Népszerű keretrendszerek
```
- React -> facebook
- Vue	-> Közösségi fejlesztés, célja a React és Angular előnyeinek ötvözése.
- Angular -> google
- (Továbbiak: Svelte, Ember.js, stb.)
```
*Feladattól függ hogy kell e keretrendszer*

### Framework Hell

- Folyamatosan újabb keretrendszerek jelennek meg, ráadásul egyes keretrendszerekre is készülnek új „framework-ök” (pl. js → Vue → Nuxt.js).
- Egyet megtanulva azonban könnyen tudsz boldogulni a többivel is, mert a szemléletük, architektúrájuk hasonló.




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

