# Frontend 11 szerda 04-30
# TANANYAG: SPA, MPA és AJAX ábra + zh gyakorlás ismertető

angular mappa: spa vs mpa and ajax.png

## spa vs mpa and ajax
![spaVmpa&ajax](https://github.com/user-attachments/assets/c9ca3eef-bddf-44f7-8b4d-24ca01c7b760)

---

[practice: ](https://github.com/oli-tolnai/Frontend-bprof/tree/main/f%C3%A9l%C3%A9vM%C3%A1sodikFele/04-30_Frontend_11_szerda/practice) gyakorlófeladatok zh-hoz

[exam-02.md: ](https://github.com/oli-tolnai/Frontend-bprof/blob/main/f%C3%A9l%C3%A9vM%C3%A1sodikFele/04-30_Frontend_11_szerda/exam-02.md) zh leírás + sorrend ahhoz, hogyan csináljuk meg a gyakorlófeladatokat


<br><br>

# TANANYAG: Angular, Komponensek

*Angular előnye a komponensek.*

- Az `app` mappa is  egy komponens. Ez lényegében egy alap komponens (ezt használtuk előző órán)
- Három része van: 
    - html
    - css
    - js

A Komponenseket többféleképpen is fel lehet használni.

Kódból nagyon jól lehet generáltatni dolgokat.

### Például: 
Alkalmazás legenerálása megszakítás nélkül:

```bash
ng new devcrud --standalone=false --skip-tests --style=sass --ssr=false
```    

- A kódban lehet használni [kapcsolókat](https://angular.dev/cli/generate/application)
- Előző órán a teszt fájlt kitöröltük. Ennek létrehozását meg lehet előzni a `--skip-tests` kapcsolóval. 

Ezután belépünk a létrehozott alkalmazás mappájába: 
    
```bash
cd devcrud
```

**Tudunk kódokat is generálni angularral**<br>
Például egy developer osztályt így hozunk létre:

```bash
ng generate class developer --skip-tests
```


A kódban általában tudunk rövidíteni is:

```bash
ng g class developer --skip-tests
```

Class-t nem rövidítjük c-re, mert az a componens rövidítése ugyanis osztályt ritkán generálunk kódból

component = c

generate = g


### Az CRUD alkalmazásunkhoz különálló komponeneseket hozunk létre:

- C - create komponens
- R - list komponens
- U - edit komponens
- D - ehhez nem csinálunk külön komponenst (lejjebb kifejtjük miért)

A három komponenst ezekkel a kódokkal hozhatjuk létre:<br>
`ng generate component create --skip-tests`<br>
`ng generate component list --skip-tests`<br>
`ng generate component edit --skip-tests`

**Terminálból akár több command-ot is lefuttathatunk egyszerre, ezeke az `&` karakterrel választjuk el egymástól:**<br>

Miden egybe így néz ki: 
```bash
ng new devcrud --standalone=false --skip-tests --style=sass --ssr=false && 
cd devcrud &&
ng g class developer --skip-tests && 
ng g c create --skip-tests && 
ng g c list --skip-tests && 
ng g c edit --skip-tests && 
code .
```
A `code .` egyből meg is nyitja 


*app.component.html-ből kitöröltünk mindent*<br>
Szerver indítása:
```bash
ng serve
```


### Mai feladat az hogy egy crud-os webalkalmazást létrehozzunk
 - Egyenlőre localStorage-t használunk fetch api hívások helyett, és majd az api hívásokat is ki fogjuk tudni szervezni service-ekbe a kövi órán vesszük)

![1.ábra](https://github.com/user-attachments/assets/7eb05ac2-366b-4d51-9e0d-9c92d27216b9)

az api hívásokat ki tudjuk szervezni servicek-be ezt fogjuk a kövi órán megcsinálni

1. Csináltunk egy footer komponenst

    ```bash
    ng g c footer --skip-tests
    ```

2. És csináltunk egy navigációs komponenst (amiben a navigációs elemek lesznek)

    ```bash
    ng g c nav --skip-tests
    ```

    ***Ezek a komponensek mind az app komponens mappáján belül találhatóak meg külön almappákban***

### A kiszervezett kis komponenseket fel tudunk használni másik html fájlokban.
Például: 
 - van nekünk olyan komponensünk hogy `nav` és a<br>
 `nav.component.html`-ben megcsináljuk a navigációs komponeneseket<br>
- Ezt fel tudjuk használni például az `app.component.html`-ben

    ```bash
    <app-nav></app-nav>
    ```
- De ugyanígy a footer-t is

    ```bash
    <app-footer></app-footer>
    ```


 <br>*a framework struktúrálja, rendszerezi a kódunkat*<br>



*komponeneses elrendezés nagy extrája, hogy minden komponenesnek külön css-se van és ha egyikben beállítjuk pl az összes `p` tag-re hogy piros legyen, akkor csak az adott komponenensen belül lévő html-ben lévő `p` tag-ek lesznek pirosak*

A navigációs rész elkészítésénél azt akarjuk megoldani, hogy ne egy új oldal nyíljon meg amikor létrehozni akarunk új developert. Ezért azt az oldalt nem `href` segítségével fogjuk hozzáadni.<br>
Ugyanis a `href` mindig egy oldalújratöltés csinál, de nekünk angularban ez most nem jó. Meg lehetne oldani akár `href`-vel is: `preventDefault()` alapvetű működést abortálni lehet és saját metúdussal megírhatjuk hogy mi történjen 

Viszont mi `routerLink`-et fogunk használunk így nem lesz oldalújratöltés és egy spa-t tudunk csinálni
`nav.component.html`-en belül tehát a `href="/list"` helyett most egy ilyen linket csinálunk:

```js
routerLink="/list"
routerLink="/edit"
```

Azonban ez egyelőre még nem fog működni ezért két lépést még meg kell tennünk:

Az `app-routing.module.ts`-ben megírjuk az alábbi részt:
routes-on belül kell megadnuunk a routs-okat.
```js
const routes: Routes = [
  { path: "", redirectTo: "list", pathMatch: "full" }, // ha nincs beírva semmi, akkor ezt (jelent esetben `list`) tölti be
  { path: "list", component: ListComponent },
  { path: "create", component: CreateComponent },
  { path: "edit/:id", component: EditComponent },
  { path: "**", redirectTo: "list", pathMatch: "full" }, // ha a felsoroltak közül egyikkel sem egyezik meg ami be van írva akkor szintén a `list` lesz betöltve
];
```

Fontos az enter leütése a component-ek beírásakor meg csak akkor imporálja be azokat:
```ts
import { ListComponent } from './list/list.component';
import { EditComponent } from './edit/edit.component';
import { CreateComponent } from './create/create.component';
```

### Routes magyarázata táblázatban
| path | redirectTo / component |
| :-- | :-- |
| `http://localhost:4200/` | `list` |
| `http://localhost:4200/create` | `create` |
| `http://localhost:4200/edit:id` | `edit` (emellett átadjuk majd az id-t is, de ezt majd később) |
| `http://localhost:4200/asdBÁRMITÍRHATSZIDEasd` | `list` |



**Azonban ez sem fog még működni**<br>
Az `app.component.html`-be be kell illeszteni az alábbi sort:
```js
<router-outlet></router-outlet>
``` 


### Tehát a lépések az alábbiak_
1. routerLink
2. routing beállítása
3. `<router-outlet>`


### Ha Bootstrap-et is használunk akkor **FONTOS** hogy azt a fő `INDEX.HTML`-be rakjuk bele

Az `index.html`-ben lévő változtatásokat nem kezeli az angular automatikusan ezért leállítjuk az egészet majd `ng serve`-vel újraindítjuk


Ha rákeresünk: [bootstrap footer](https://getbootstrap.com/docs/5.3/components/navbar/#external-content), akkor találunk olyan példákat ahol nincs példakód ami ki lehetne másolni.
- Ezért inspect -> megkeressük a footer-t -> jobbklikk -> copy element -> bemásoljuk a sajátunkba


[nav bar](https://getbootstrap.com/docs/5.3/components/navbar/) esetén ha ilyen dropdown fajtát rakunk bele akkor lehet kell hozzá a bootstrap js script is


[Gombok](https://getbootstrap.com/docs/5.0/components/buttons/#button-tags) esetén a bootstrap `href`-eket használ ezért ezt át kell rakni routerLink-re

Containerek helyett lehet használni ezeket: `mx-5 my-5` (marginok), így pl zoomolásnál jobban megtartja a kinézetet és kesébé csúsznak el az elemek.



### Kövi lépés a ListComponent elkészítése:


Elsőnek legeneráltunk egy developer osztályt majd a 
`developer.ts` -ben megcsináljuk a tulajdonásokat

`list.component.ts`<br>
`load()` metódussal betöltjül majd a localstorage-ból a dolgokat **(kövi órán ezt lecseréjük az api hívásokra)**<br>
`seed()` -> ebben hozzuk létre elemeket amiket majd elmentünk a localstorage-ba<br>
`save()` -> ezzel mentjük meg a localstorage-ba az elemeket.

***inspect -> Application -> Local storage***<br>
Ez a saját `localStorage`-om az adott böngészőben. Az itt eltárolt elemek megmaradnak például akkor is ha kikapcsoljuk a gépet és újra megnyitjuk (perzisztens adattárolás).

Ha a construkrba bármikor ha meghívjuk egymás után a `seed()`-et és a `save()`-et akkor lényegében resetelni tudjuk a localStorage-ot

Ehelyett mi most a load-ot fogjuk belerakni a construktorba. Ez azt csinálja, hogy a localstorage-ból kiszedji az elemeket. 
Ennél fontos hogy ne egy sima objektumként jelenjenek meg az elemek, hanem típusos ojbektumként  Ezt az `Object.Assign`-val csináljuk meg

```ts
let data = JSON.parse(localStorage.getItem("bprof_devs") ?? "[]")
Object.values(data).map(x => this.developers.push(Object.assign(new Developer(), x)))
```





## Házi1
### Megcsinálni azt, hogy a Salary úgy jelenejen meg hogy: 250,000 HUF ahelyett hogy 250000 HUF<br>figyelni kell hogy van aki milliókat keres vagy kevessebet és azoknál is jól nézzen ez ki, tehát dinamikusan működjön

**Két féle megközelítéssel csinálhatjuk ezt meg:**
1. list componens-be csinálni egy `formatSalary()`-t
2. developer osztályban készítünk egy `formatSalary()`-t és akkor úgy meghívni a `table`-ben hogy `{{ developer.formatSalary() }}`


-----


*Probléma:* A számot váró input mezőknél a placeholder helyett 0 van.<br>
*Megoldás:* 
Default érték miatt az `age` és a `salary` `placeholder`-re nem működik mert alapértelmezett értéke 0. Ezért megadhatjuk azt pl hogy `age: number | null = null` ahelyett hogy `age: number = 0`
Ebben az esetben vagy szám vagy null lehet az értéke, és a default értéke 0 lesz.
Az input type-nak is number kell hogy legyen a típusa és akkor már jól fog működni.


----


Ha frontenden kell id-t generálni akkor erre kell rákeresnünk: `npm Guid Typescript`-re rákeresünk
és az alábbi kell neünk: <br>[`guid-typescript`](https://www.npmjs.com/package/guid-typescript)
```js 
import { Guid } from "guid-typescript"
id: string = Guid.Create().toString()
```



Amikor a felhasználót szeretnék átirányítani egy művelet után egy másik oldalra<br>
például a új developer létrehozásakor a `Create` gombra nyomva egyből töltődjön be a `List` (Read) nézet, akkor jelen esetben a `create.components.ts`-ben ezt meg tudjuk tenni

```ts
  constructor(private router: Router) { }

  create(): void {
    this.loadAndSave()
    this.router.navigate(["list"])
  }
```

dependecy injection miatt a konstruktoron keresztül kapja meg a `router`-t 
![di](https://github.com/user-attachments/assets/b921553d-0918-4fab-b674-a7957649c8e3)


----


törölni lehet `slice`-val és `splice`-val meg `filter`-rel is. <br>
`Filter`-rel rákeresünk azokra amikkel nem egyezik meg az adott ID így visszaadja az összes többit  
```ts
this.developers = this.developers.filter(x => x.id != developer.id)
```

---


Kiszedni a link/path-ből az id-t konstruktoron keresztül lehet:<br>
`edit.components.ts`<br>
```ts
  constructor(private route: ActivatedRoute, private router: Router) {
    route.params.subscribe(param => {
      // load
      let developers: Developer[] = Array<Developer>()
      let data = JSON.parse(localStorage.getItem("bprof_devs") ?? "[]")
      Object.values(data).map(x => developers.push(Object.assign(new Developer(), x)))

      // filter
      this.developer = developers.filter(x => x.id == param["id"])[0]
    })
  }
```
Ebben a példában meg is keresi azt a developer-t amelyikhez tartozik az id.


----
## Házi2:  
létrehozni egy 
- delete komponens-t
- input mező -> id
- gomb -> bemásolt id alapján töröljük az elemet
    <hr>ha ez megvan akkor: <hr>

- textarea ->több id törlése egyszerre
- akár megprobálhatjuk legördülős listával (dropdown list)

## Házi3: Create felületen a Create gomb csak akkor aktív hogyha a name != "" és az email-ben van @ jel és .pont karakter és a salary > 1000

 
