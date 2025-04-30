# Frontend 11 szerda 04-30
# TANANYAG: Angular, Komponensek

angular mappa: spa vs mpa and ajax.png

## spa vs mpa and ajax
![spaVmpa&ajax](https://github.com/user-attachments/assets/c9ca3eef-bddf-44f7-8b4d-24ca01c7b760)
[practice mappa](oli-tolnai/Frontend-bprof/félévMásodikFele/04-30_Frontend_11_szerda/practice): gyakorlófeladatok zh-hoz, exam-02.md zh leírás, sorrend ahhoz, hogyan csináljuk meg a feladatokat




Angular előnye a komponensek.

az app mappa is  egy komponens. Alap komponens volt (előző órán) Három része van: html, css, js

A Komponenseket többféleképpen is fel lehet használni.

Kódból nagyon jól lehet generáltatni dolgokat. 


alkalmazás legenerálása megszakítás nélkül:
`ng new devcrud --standalone=false --skip-tests --style=sass --ssr=false`

skip-tests: tesztek skippelése: ez egy kapcsoló
kapcsolók dokumnteációja: https://angular.dev/cli/generate/application

`cd devcrud`

kód generálás angularral: 
`ng generate class developer --skip-tests`

álalában rövidíthetőek:
`ng g class developer --skip-tests`
component = c
generate = g


különálló komponenesek
C - create komponens
R - list komponens
U - edit komponens
D - ehhez nem csinálunk külön komponenst

`ng generate component create --skip-tests`
`ng generate component list --skip-tests`
`ng generate component edit --skip-tests`

terminálból több command lefuttatása:
és jelekkel történik:
`ng g class developer --skip-tests` && `ng g c create --skip-tests` && `ng g c list --skip-tests` && `ng g c edit --skip-tests` && code .

code . megnyitja

readme fájlba beleírta a kódót a siposm


app.component.html-ből kitöröltünk mindent

`ng serve` - Szerver indítása

mai feladat:
*1.ábra
az api hívásokat ki tudjuk szervezni servicek-be ezt fogjuk a kövi órán megcsinálni


`ng g c footer --skip-tests`

`ng g c nav --skip-tests` - navigációs elemek


Kiszervetett kis komponens (pl list komponens) így felhasználható másik html fájlban
app.component.html-ben: <app-list></app-list>

nav.component.html-ben megcsináljuk a navigációs komponeneseket
majd app.componenent.html-ben felhasználhaató a <app-nav></app-nav>


*a framework struktúrálja rendszerezi a kódunkat.

komponeneses elrendezés nagy extrálja, hogy minden komponenesnek külön css-se van és ha egyikben beállítjuk pl az összes p tag-re hogy piros legyen, akkor csak az adott komponenensen belül lévő html-ben lévő p tag-ek lesznek pirosak


`href` egy oldalújratöltés csinál, de nekünk angularban ez nem jó, meg lehet oldani akár `href`-vel is: `preventDefault()` alapvetű működést abortálni lehet és saját metúdussal megírhatjuk hogy mi történjen 
VISZONT mi `routerLink`-et használunk
`routerLink="/list"`
`routerLink="/edit"`
ez még nem fog működni ezért ezt megg kell tennünk:

`app-routing.module.ts`
routes-on belül kell megadnuunk a routs-okat.
{ path: "", redirectTo: "list", patchMatch: "full"}, - ha nincs beírva semmi, akkor ezt tölti be
{ path: "list", componenent: ListComponent },
{ path: "list", componenent: EditComponent },
{ path: "**", redirectTo: "list", patchMatch: "full"}, - ha bármi más van beírva, akkor ezt tölti be
fontos entereznünk hogy beimporálja

ez sem fog még működni ugyanis a  <router-outlet></router-outlet> kell még az app.componenent.html-be

*2.ábra

**lépések:
1. routerLink
2. routing beállítása
3. <router-outlet>


Ebbe még belerakjuk a bootrsappat.
EZT A NAGY FŐ INDEX.HTML-be rakjuk bele

leállítjuk az egészet majd `ng serve` újraindítjuk, ugyanis a fő index.html-ben lévő változtatásokat nem kezeli az angular automatikusan

rákeresünk: bootstrap footer, ha nem lehet kimásolni a kódokat, akkor jobbklikk inspect, megkeressük a footer-t majd copy element és bemásoljuk a sajátunkba
https://getbootstrap.com/docs/5.3/examples/footers/

nav bar: lehet kell hozzá a bootstrap js script is

*a bootstrap href-eket használ ezt van hogy át kell rakni routerLink-re, ha link-ekete akarunk kezelni pl navbar-nál 


siposm containerek helyett mx-5 my-5 (marginok) használ, ha zoomolás miatt összekuszálódik a kinézet, mert így nagyjából jobban megtartja



kövi lépés: ListComponent:
load() methoddal betöltüj majd a localstorage-ból a dolgokat, kövi órán ezt lecseréjük az api hívásokra
developer.ts-ben megcsináljuk a tulajdonásokat
seed() -> ebben hozzuk létre elemeket amike majd elmentünk a localstorage-ba

save()-> ezzel mentjük meg a localstorage-ba az elemeket.
*inspect -> Application -> Local storage
Ez a saját localstorage-om az adott böngészőben. Az itt eltárolt elemek megmaradnak ha kikapcsoljuk a gépet és újra megnyitjuk (perzisztens adattárolás)
construkrba bármikor ha meghívjuk egymás után a seed-et és a seed-et akkor lényegében resetelni tudjuk

ehelyett mi most a load-ot fogjuk belerakni a construktorba. ami azt csinálja, hogy a localstorage-ból kiszedjuk az elemeket
aminél fontos hogy ne egy sima objektumként jelenjenek meg hanem még egy fontos lépés hogy típusos ojbektumként jelenjenek meg. (Ezt csinájuk az Object.Assign-val





#Házi megcsinálni azt, hogy a Salary úgy jelenejen meg 250,000 HUF ahelyett hogy 250000 HUF, figyelni kell hogy van aki milliókat keres 
1. megközelítése. list componens-be csinálni egy formatSalary()-t
2. developer osztályban formatSalary()-t és akkor úgy meghívni a table-ben hogy {{ developer.formatSalary() }}

default érték miatt az age és a salary placehodlere nem működik mert alapértelmezett értéke 0. Ezért megadhatjuk azt pl hogy age: number | null = null ahelyett hogy age: number = 0
így vagy szám vagy null lehet az értéke
az input type-nak is number kell hogy legyen a típusa

ha frontenden kell id-t generálni akkor
npm Guid Typescript-re rákeresünk
fontos nekünk ez kell: guid-typescript
import { Guid } from "guid-typescript"
id: string = Guid.Create().toString()

akár erre is rákereshetünk:
javascript guid function w3schools
de a másik érdekesebb


amikor a felhasználót szeretnék átiírányítani valami után egy másik oldalra, akkor create.components.ts.-ben ezt meg tudjuk nézni
dependecy injection *3.ábra
kontruktoron szokás megcsinálni
(van method injection is amúgy)


törölni lehet slice splice meg filterrel is. 
filterrel rákeresünk azokra amikkel nem egyezik meg az adott ID így visszaadja az üsszes többit  (list.componenent.ts)


kiszedni a linkből az id-t (edit.componenent.ts)
constructor(private route: ActivatedRoute){
route.params.subscribe(param => {idejön a kód: load, filter, `param["id"]`})}


#Házi2:  létrehozni egy 
- delete komponens-t
- input mező ->id
- gomb -> bemásolt id alapján töröljük az elemet
---- ha ez megvan akkor
- textarea ->több id törlése egyszerre

- akár megprobálhatjuk legördülős listával (dropdown list)

#Házi3: Create felületen
Create gomb csak akkor aktív hogyha a name != ""; email-ben van @ jel és .pont karakter ; salary > 1000
 
