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
        - `<thead>`: Fejléc, ide kerülnek a címkék
        - `<tbody>`: Ide generál a JavaScript dinamikusan sorokat (pl. adat beolvasás után)
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

<br>

### Könyvtárak (Libraries) és különbségük a keretrendszerekkel szemben

- **Könyvtár (lib, library):** Előre megírt, újrahasznosítható kódrészletek, függvények vagy modulok gyűjteménye.
    - Példa: Egy képfeldolgozó vagy grafikai library, amit egyszerűen behívhatsz a projektedbe.
    - Ezek nem adnak meg projekt struktúrát és fejlesztési mintákat – csak bizonyos feladatok megoldásához nyújtanak funkciókat.
    - Példakód:

        ```js
        // Pl. Lodash egy gyakori JS könyvtár
        import _ from 'lodash';
        const arr = [1, 2, 3, 4];
        const first = _.first(arr);
        ```

- **Keretrendszer (framework):**
    - Egy komplett, összefüggő megoldásrendszer, sok előre gyártott eszközzel: routing, state management, komponensstruktúra, stb.
    - Tipikus „best practice” megoldásokat használ, nem kell mindent nulláról írni.
    - Példa:
        - Routing: Angularban, React Routerben, Vue Routerben mind adott.
        - Auth/login: Keretrendszerekben legtöbbször van előre kidolgozott megoldás vagy integráció.
- **Fő különbség**:
    - Könyvtárat (lib) te használsz, azt hívod meg ott, ahol akarod.
    - Keretrendszer (framework) diktálja, hogyan épül fel az alkalmazás – a te kódod „illeszkedik” bele a framework által definiált struktúrába.
	


### A helyes tanulási sorrend

- Először tanuld meg nulláról, hogyan lehet felépíteni egy megoldást (például SPA-t), aztán térj át a keretrendszerekre és használd a best practice-ket.



### Kell-e keretrendszer?

- **Nem mindig szükséges!**
    - Kis, egyszerűbb projekthez, gyors prototípushoz elég egy-egy library vagy magad által írt JS.
    - Nagy, összetett, bővíthető és karbantartható alkalmazásokhoz (pl. vállalati rendszerek) viszont megéri keretrendszert használni.
---
<br><br><br>

### SPA – Single Page Application

- Ezeket gyakran modern keretrendszerekkel készítik.
- **SPA**: Az egész alkalmazás egyetlen oldalon fut (tipikusan index.html), és az adatokat AJAX/Fetch/HTTP-kérésekkel/hívásokkal dinamikusan tölti be, oldalfrissítés nélkül.

	![spaLifecycle](https://github.com/user-attachments/assets/2d1f06b8-f8fd-4ea3-afab-7cd1945036f9)



### AJAX – Az SPA-k őse

- **AJAX** = Asynchronous JavaScript And XML
- Lehetővé tette, hogy a weboldal frissítése nélkül dinamikus adatokat kérjünk le a szervertől (például JSON formátumban) és mutassunk meg a felhasználónak.
- Nincs teljes oldalfrissítés, csak az adatok frissülnek.

	![spa](https://github.com/user-attachments/assets/f674d62f-7041-46e6-9a68-cda60599b0d9)



### AJAX és XHR részletek

- **AJAX** nem önálló technológia, hanem **meglévő eszközök kombinációja**:
    - `XMLHttpRequest` (XHR) objektum a kérések kezelésére.
		- Mai napig velünk van
    - Adatformátumok (XML/JSON).
    - Aszinkron JavaScript logika.
- **XHR kérések** ma is használatosak (rövidítés: **XHR**).
A böngésző fejlesztői eszközein (DevTools) a **Network** fülön a **Fetch/XHR** szekcióban láthatók ezek a kérések.

	_Interjú tipp:_ Sok helyen kérdeznek XHR-ről, ne feledd, hogy ez a klasszikus AJAX megvalósítás módja!

	![AJAX](https://github.com/user-attachments/assets/a02a6ea4-03d4-4fd4-ac4e-3b888e2964d4)



### jQuery és szerepe

- **jQuery** egy JavaScript könyvtár *`(lib)`*, nem keretrendszer, ami régebben nagy népszerűségnek örvendett.
    - _Előnyei_ anno:
        - Egységesítette a böngészők közötti különbségeket (pl. event kezelés).
        - Egyszerű DOM manipuláció (pl. `$('#elem').slideToggle()`).
        - Szintaxis rövidség (pl. `$('.class')` helyett `document.querySelectorAll`).
    - _Hanyatlás oka_: A modern JavaScript (ES6+) és CSS3 megoldások kivetkőztették a szükségességét.
    - _Fejlesztő_: John Resig (korábbi Microsoft mérnök).
	- [JQuery Selector](https://www.w3schools.com/jquery/trysel.asp)

<br><br>




## Angular	
	
![angular](https://github.com/user-attachments/assets/148cfedd-b31f-4b87-9705-88875369ddd6)

### Projekt létrehozás és CLI

[Setup Angular Cli](https://angular.dev/tools/cli/setup-local)

- **CLI** -> *command line interface*
- **Angular CLI** → *The Angular CLI is a command-line interface tool which allows you to scaffold, develop, test, deploy, and maintain Angular applications directly from a command shell.*



**Angular CLI** telepítése:

```bash
npm install -g @angular/cli
```

**Új projekt** indítása:

```bash
ng new demo-app --standalone=false
```

**Kérdések** a generálásnál:
- _CSS preprocesszor_: Válaszd pl a `SASS`-t 
- _SSR (Server-Side Rendering)_: Írjuk be hogy `N`, tehát nemmel válaszoljunk.
- Ezután: `l` majd `cd demo app`



`src mappa` → `index.html` → `<app-root></app-root>` = Minden amit a komponensekbe írunk az `app-root`-ba, vagyis ennek helyére fog kerülni
 


### Mappaszerkezet táblázatban

| Mappa/fájl | Leírás |
| :-- | :-- |
| `src/` | Forráskódok fő mappája. |
| `src/app/` | Az alkalmazás fő modulja és komponensei. |
| `src/app/app.component.ts` | Alapértelmezett komponens TypeScript fájlja. |
| `src/app/app.compnent.spec.ts` | Tesztelésre van (Órán kitöröltük)
| `src/app/app.component.html` | A komponens HTML sablonja. |
| `src/app/app.component.scss` | A komponens stíluslapja (SCSS). |
| `src/assets/` | Statikus fájlok (pl. képek, betűtípusok). |
| `src/environments/` | Környezeti változók (pl. dev/prod API URL-ek). |
| `angular.json` | Projektkonfiguráció (build, serve, teszt beállítások). |


### Komponens szerkezet
Keretrendszerek fontos része a *komponens alapúság*

Minden komponens 3 fájlból áll:

1. **HTML** - Sablon (pl. `app.component.html`).
2. **TypeScript** - Logika (pl. `app.component.ts`).
3. **SCSS** - Stílusok (pl. `app.component.scss`).

Minden komponensnek van **SAJÁT** html, css és js fájlja
	 
	
### Futtatás és szerver

A futtatás nem liveserverrel hanem beépített terminállal törtétnik

**Szerver indítása**:

```bash
ng serve 
```
Ezután:
``` bash
N
```


- A parancs buildeli az alkalmazást és elindít egy lokális szervert (általában `http://localhost:4200`).

- Ez folyamatus buildelést és watch-olást csinál, tehát a terminált le is csukkhatjuk


### Adatkötés és eseménykezelés

- **Interpoláció** (template-ezés): TS változók megjelenítése HTML-ben:

    ```html
    <h1>{{ cim }}</h1>
    ```

A `cim` változó értéke dinamikusan frissül a komponensben.

<br>

- **Eseménykötés**:

    ```html
    <button (click)="valamiFuggveny()">Kattints</button>
    ```

A `(click)` esemény hozzárendelődik a TS fájlban lévő `valamiFuggveny` függvényhez.

<br>


## `ngModel` és FormsModule használata Angularban

### Kétirányú adatkötés input mezőnél – `ngModel`

**Keretrendszerek egyik legfontosabb része a kétirányú adatkötés**

- Az **`ngModel`** direktíva segítségével kétirányú (two-way) adatkapcsolatot létesíthetsz egy input mező és a komponensben (TS fájlban) lévő változó között.
- Például:

    ```html
    <input type="number" [(ngModel)]="myNumber">
    ```

- Itt a `myNumber` változó értéke mindig tükrözi az input mező aktuális értékét és fordítva.


**_ZH-ban:_** Kétirányú adatkötés (two way data dinding) ábra:

![twowadatabinding](https://github.com/user-attachments/assets/04ffc64e-f844-4f49-b875-223b6f724649)



### FormsModule importálása

- Ahhoz, hogy az **`ngModel`** használható legyen, tehát hogy működjön a binding, az adott Angular modulban (pl. `AppModule`) **be kell importálni a `FormsModule`-t**!
- Amikor a projekt `standalone: false` módban lett létrehozva (klasszikus modul-rendszer), az import így néz ki:

1. Nyisd meg a `src/app/app.module.ts` fájlt.
2. Egészítsd ki az importokat:

    ```typescript
    import { FormsModule } from '@angular/forms';
    ```

3. Tedd be a `imports` tömbbe, majd `ENTER` hogy beimportálja:

    ```typescript
    @NgModule({
    declarations: [
        AppComponent,
        // egyéb komponensek
    ],
    imports: [
        BrowserModule,
        FormsModule,        //<<-- itt!
    ],
    providers: [],
    bootstrap: [AppComponent]
    })
    export class AppModule { }
    ```

- Ezután már működni fog az `ngModel` a template-ben bármilyen input elemen.


### Standalone komponensek esetén

- Ha standalone Angular komponenseket használnál (**standalone: true** esetén), akkor nem a modulba, hanem közvetlenül a komponenshez kellene importálni a `FormsModule`-t vagy az adott form vezérlőt.
- Most viszont a klasszikus modul struktúra szerint dolgozol, ezért a fenti lépéseket kövesd!



---
## For ciklus HTML-ben – *ngFor használata Angularban

Az Angular **strukturális direktívákat** kínál a sablonban (HTML-ben) történő ciklikus megjelenítéshez. A leggyakoribb példa a **`*ngFor`**:

### Példa használat:

```html
<p *ngFor="let item of increments">{{ item }}</p>
```

- **Mit jelent ez?**
    - Az `increments` egy tömb a komponens TypeScript fájljában.
    - A sor minden egyes eleméhez (item) létrejön egy `<p>`, amelyben a sablonban az adott elem értéke jelenik meg.


### Részletesebb példa:

#### TypeScript fájl (app.component.ts):

```typescript
export class AppComponent {
  increments = [1, 2, 3, 4, 5];
}
```


#### HTML (app.component.html):

```html
<p *ngFor="let item of increments">{{ item }}</p>
```


#### Eredmény:

```html
1
2
3
4
5
```


### Fontosabb tudnivalók az *ngFor-ról

- Mindig **`*ngFor`** (csillaggal), mert strukturális direktíva!
- A sablonban az **`let item of lista`** szintaxist használjuk, ahol `item` az aktuális elem, `lista` pedig a bejárni kívánt tömb.
- További index kezelésére is van lehetőség:

    ```html
    <li>
    #{{ i }}: {{ elem }}
    </li>
    ```

*Fetch elemeken is ngfor-ral fogunk végig menni*

---


## Konstruktor szerepe komponensben

- Az Angular komponens TypeScript osztályának **konstruktorában** (constructor) inicializálhatod az adatokat, például alapértékeket adhatsz egy tömbhöz:

    ```typescript
    export class AppComponent {
    increments: number[] = [];

    constructor() {
        this.increments.push(1, 2, 3, 4, 5);
    }
    }
    ```

- A konstruktor **fő szerepe**: a komponens létrejöttekor (példányosításakor) egyszer fut le, így alkalmas kezdőértékek beállítására, szolgáltatások (service-ek) injektálására stb.

---

## `*ngIf` – Feltételes / Kondícionális megjelenítés  Angularban

- Az **`*ngIf`** strukturális direktíva feltételhez köti egy HTML elem megjelenítését.


### Alapszintaxisa:

```html
<p>Ez akkor látszik, ha a 'visible' igaz!</p>
```

- Csak akkor jelenik meg a `<p>`, ha a komponensben a **`visible`** változó értéke true.

### Példa logika a komponensben:

```typescript
export class AppComponent {
  visible = true;
}
```


### Ágak kezelése (`else`):

- *ngIf-else* eset:

    ```html
    </p><div>
    Hiba történt!
    </div>
    <ng-template #mindenOk>
    Minden rendben.
    </ng-template>
    ```

- Az `<ng-template>` blokk az else ág.

---

ngClass -> 

lehet 


## `ngClass` – Dinamikus osztály (class) kezelés Angularban

Lehet adatkötni osztályt is<br>
*"Keretrendszerekkel lehet mindent adatkötni"*<br>
Például a disable állapotot is lehet adatkötni és még nagyon sok mindent

Az **`[ngClass]`** direktíva lehetővé teszi, hogy egy elemhez dinamikusan adj többféle CSS osztályt (class-t) Angularban, feltételek alapján.


### Alapszintaxisa:

```html
<div>
  Dinamikus class-váltás példa
</div>
```

- **`bigger`** osztály akkor lesz ráadva, ha az `isBig` változó true.
- **`smaller`** osztály akkor, ha az `isBig` false.


### Példakód teljesen:

#### app.component.ts

```typescript
export class AppComponent {
  isBig = true;
}
```


#### app.component.html

```html
<div>
  Ez a szöveg vagy nagyobb, vagy kisebb stílust kap!
</div>
&lt;button (click)="isBig = !isBig"&gt;Vált&lt;/button&gt;
```


#### app.component.scss

```scss
.bigger {
  font-size: 2rem;
  color: green;
}
.smaller {
  font-size: 1rem;
  color: red;
}
```


### További lehetőségek

- Több osztály adásához is használhatsz tömböt:

    ```html
    <div></div>
    ```

- Egyedi logika alapján object vagy függvény is visszaadhatja az osztályokat.

---

### Röviden:

- **[ngClass]** – Egy elem CSS osztályainak dinamikus, feltételes beállítása Angular komponens változói/logikája alapján.

---



