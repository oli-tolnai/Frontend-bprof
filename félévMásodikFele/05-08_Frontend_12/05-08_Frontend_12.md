# 05-08_Frontend_12

# TANANYAG: Service, komponensek


A múltkor abbahagyott feladatot folytatjuk. 
Bele akarunk rakni plusz egy fületet, ahol statisztikák lesznek

Ehhez kell egy új komponens:

```ts
ng g c stats --skip-tests
```

app-rooting.module.ts -> path:stats-ot hozzáadni

nav.componentet bűvítjük: 
lista eleme routerLink: /stats


stats.component.ts:
itt vannak a metódusok amik statisztikákat készítenek
(ide pár példa method)

getAllSkills() -> ismétlődő elemek eltávolítása:
this.developers.map(x =>x.skills).flat()

map -> minden elemen végig megy és vissza adja a meghatározott értéket tehát  a skilleket
flat -> több dimenziós tömböt kisimítja *1ábra
sort -> sorrendbe állítja betűrendbe
new set -> ez kiszűri az ismétlődéseket, halmaz tulajdonság hogy nincs benne ismétlődő elelm. és a set egy új halmazt csinál
array.from csinál a setből(halmazból) egy listát

ez egy érdekes példa volt mert már volt egy kész alklmaazásunk és mi csak belefejlesztettnk egy új komponenst

ha a vásárló azt mondja hogy szerenté a List devs-nél látni a statisztikát akkor csak ennyit kell tennünk:
list.komponent:
<app-stats>

nem pedig a stats.ts kódját másolta át, hanem csak a komponens beillesztette egy másik komponensbe




mindegyik komponensben vannak ismétlődő részek pl. load() save() 
a rendszer lelke rétegzett kódfelépítés

Logic -> legfontosabb (üzleti logika)
angularban ennek neve a Service

developer service generálása:

```ts
ng g s developer
```

ide másoljuk be az ismétlődő metódusokat: load, remove, create udpdate, save, seed
dbString: string = "bprof_devs"
mindig érdemes kiszervezni ide a database egy külön változóba

ezután
list.component.ts refaktorálása:

remove -> irányítson át a service adott műveletéhez. ehhez el kell érnünk a service-t
ctor -> át kell venii a serviceket: (private service: DeveloperService) -> ez a dependency injection (-> singleton)
ezután a remove-nál: this.service.remove(developer)

tehát ha angularban servicek-ről beszélünk akkor dependency injection-ről is beszélünk 
Ez a szolgáltatás singleton formában jön létre. 


list.komponent.html
privát láthatósa-> ts kódon belül lehet elérni, ahhoz hogy elérjük a html-ben is tegyük publiccá a ts ctor-ban lévő service-t

és ezt megcsináljuk a többi komponensnél is: create -> ezt elég egyszerű volt refaktorálni
edit komoponensél: ts: ctor és save refaktorálása



ezután létrehozunk statistics service-t is
```ts
ng g s statistics
```

ide behelyezünk mident ami a stats-ban volt
és így  a stat component.ts-ben csak át kell adni a ctor-nak és ezután a html-ben úgy kell meghívni, hogy pl: service.averageSalary

a szolgáltatásoknak a lényegi része nagyjából ennyi volt

-----
https://angular.dev/api/common/CurrencyPipe
pipe szimbólum: |
statscomponent html-be belerakjuk a currencyt
app.module.ts be kell importolni:
import localeHu from '@angular/commmon/lovales/hu'
import {registerLocalData} from angular/common
registerLocaData(localeHu)

-----
következő probléma, hogy legszkillesebb ember törlésekor is ő marad a legszkillesebb, amíg nem frissítük az oldalt

a singletonság miatt hiába lépünk át a statistics fülre, mivel ugyanazt a példányt kapja meg mint ami be lett illestve a listdevs komponensbe így mivel ez spa és nincs oldalújratöltés ezért még ekkor sem fog frissülni

### DOM optimalizáció
- virtual DOM (react) https://miro.medium.com/v2/resize:fit:1400/0*_C52yYMRTDuMtdBA
van az eredeti dom és van ennek egy shadow copy virtual dom-a. és a react elsőkörben ezt vizsgálja, abban keres.
valami ütemezés szerint vizsgálja hogy a dom-ban mik azok a változások amik történtek és 
nem az eredeti dom-on dolgozok hanem egy virtuálisan amin könnyebb. pl virtual dom-on valamit háromszor módosítok akkor a felhasználónak elég csak a végső állapotot látni így az eredeti dom csak egyszer fog frissülni
- Change Detection (angular) -> ez lesz neünk most a megoldás
	_lifecycle_ -> ez is kapcsolódhat a tanulmányaikhoz



statistics.service.ts-ben:
this.load() nem kell. 
és minden számítás meg kell hogy kapjon egy developer tömböt amivel dolgozni tud

stat komponens ts-nél ctor-ba átvesszük a statService-t és a devService-t is
get-eken keresztül hívjuk meg a metódusokat. 
lényege hogy máshogy működik a háttérben mint ahogy azt mi látjuk
alma(...) != get alma(...)

stats component html-ben is refaktorálunk


-------szünet
## Feladat: localstorage lecserélése adatbázisra
developer.service.ts-en kell dolgoznunk.

ctor-ba private http: HttpClient
loadApi(): void függvény
appiBaseUrl-be berakjuk az alap api url-t
és a függvényeket is refaktoráljuk
NullInjector error az hogy app.module.ts-be be kell rakni az importsokba is a HttpClient-et


----
[tervezés]-> Macskák: name, id, ... -> JSON {id, name} ebből tudjuk milyen lesz az API és ebből lehet párhuzamosan elkezdeni fejelszteni az a Frontendet és a Backendet

[fejlesztés] -> B.E. + F.E. párhuzamosan


node_modules mappa sok helyet foglal ezért van benne a .gitignore fájlban

npmi -vel lelehet buildelni ezért nem kell a node_modules mappát másolgatni

megjegyzés a zh-nál beszéltekhez:
*event loop akkor szed ki elemet és akkor osztja ki amikor üres a callback

*learning curve 4.ábra


template engine / framework 
<p>{{alma}}</p>
talán feltölt erről ábárt a cliens oldalról (Anuglar) mi ennek a flow-ja
és van másik ábra hogy ez milyen a szerver oldalon (pl Twig) (egyszerűbb)


*félévben kimaradt dolgok, amiket kövi félévben veszünk:
bejelentkezési funkció, 
observable void helyett 
rxjs

ngIf-t inkkúább érdemes kiszervezni egy metódusba ha komplex a feltétel
ngif = alma.length > 0 & ...
					    |->(konkatenálasz)

*routeroutlet

fetchelésnél ami nem jött vissza a promise, addig lehet hogy üres oldalt fogunk látni ezért pl meglehet csinálni, hogy a listkomponent.html-ben a table-nél berakunk egy ngif-et ami nézi hogy nagyobb e mint 0 a lista, tehát megjött e már a promise, és ha nem akkor else ágban lehet valami loadingot berakni, mint pl a facebook-nál is van fading.

szoftech-en olyan dolgot fogunk mos venni, ami kövi félévben önálló munkáknál nagyon fontos lesz
