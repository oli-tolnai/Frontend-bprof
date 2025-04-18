
### Mappaszerkezet táblázatban

| Mappa/fájl | Leírás |
| :-- | :-- |
| `src/` | Forráskódok fő mappája. |
| `src/app/` | Az alkalmazás fő modulja és komponensei. |
| `src/app/app.component.ts` | Alapértelmezett komponens TypeScript fájlja. |
| `src/app/app.component.html` | A komponens HTML sablonja. |
| `src/app/app.component.scss` | A komponens stíluslapja (SCSS). |
| `src/assets/` | Statikus fájlok (pl. képek, betűtípusok). |
| `src/environments/` | Környezeti változók (pl. dev/prod API URL-ek). |
| `angular.json` | Projektkonfiguráció (build, serve, teszt beállítások). |

### Komponens szerkezet

Minden komponens 3 fájlból áll:

1. **HTML** - Sablon (pl. `app.component.html`).
2. **TypeScript** - Logika (pl. `app.component.ts`).
3. **SCSS** - Stílusok (pl. `app.component.scss`).

### Futtatás és szerver

- **Szerver indítása**:

```bash
ng serve
```

    - A parancs buildeli az alkalmazást és elindít egy lokális szervert (általában `http://localhost:4200`).


### Adatkötés és eseménykezelés

- **Interpoláció**: TS változók megjelenítése HTML-ben:

```html
<h1>{{ cim }}</h1>
```

A `cim` változó értéke dinamikusan frissül a komponensben.
- **Eseménykötés**:

```html
&lt;button (click)="valamiFuggveny()"&gt;Kattints!&lt;/button&gt;
```

A `(click)` esemény hozzárendelődik a TS fájlban lévő `valamiFuggveny` függvényhez.
- **Two-way data binding**:
Kétirányú adatkötéshez (pl. űrlapmezőknél) használd az `[(ngModel)]` direktívát:

```html
&lt;input [(ngModel)]="felhasznaloNeve"&gt;
```

A `felhasznaloNeve` változó szinkronban marad az input mezővel.

![image](https://github.com/user-attachments/assets/7497915b-4e56-47c3-a375-fcc10f6c6a6b)

## `ngModel` és FormsModule használata Angularban

### Kétirányú adatkötés input mezőnél – `ngModel`

- Az **`ngModel`** direktíva segítségével kétirányú (two-way) adatkapcsolatot létesíthetsz egy input mező és a komponensben (TS fájlban) lévő változó között.
- Például:

```html
&lt;input type="number" [(ngModel)]="myNumber"&gt;
```

Itt a `myNumber` változó értéke mindig tükrözi az input mező aktuális értékét és fordítva.


### FormsModule importálása

- Ahhoz, hogy az **`ngModel`** használható legyen, az adott Angular modulban (pl. `AppModule`) **be kell importálni a `FormsModule`-t**!
- Amikor a projekt `standalone: false` módban lett létrehozva (klasszikus modul-rendszer), az import így néz ki:

1. Nyisd meg a `src/app/app.module.ts` fájlt.
2. Egészítsd ki az importokat:

```typescript
import { FormsModule } from '@angular/forms';
```

3. Tedd be a `imports` tömbbe:

```typescript
@NgModule({
  declarations: [
    AppComponent,
    // egyéb komponensek
  ],
  imports: [
    BrowserModule,
    FormsModule,        // &lt;&lt;-- itt!
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
<p>{{ item }}</p>
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
</p><p>{{ item }}</p>
```


#### Eredmény:

```
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

## `*ngIf` – Feltételes megjelenítés Angularban

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
&lt;ng-template #mindenOk&gt;
  Minden rendben.
&lt;/ng-template&gt;
```

- Az `&lt;ng-template&gt;` blokk az else ág.

---

## `ngClass` – Dinamikus osztály (class) kezelés Angularban

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


