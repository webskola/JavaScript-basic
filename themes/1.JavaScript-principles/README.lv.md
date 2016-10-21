# JavaScript pamati

## Vispārējā informācija



### Piemēri

 - [Modal window](http://codepen.io/shshaw/pen/gEiDt)
 - [Matrix text](http://codepen.io/locoalien/pen/blKdy)
 - [Navigation](http://codepen.io/arkev/pen/DzCKF)
 - [Calculator](http://codepen.io/giana/pen/GJMBEv)
 - [Game](http://browserquest.mozilla.org/)
 - [Fun](http://codepen.io/VincentGarreau/pen/pnlso)

## Kur rakstīt?

0. Iekš taga `<script>` jebkurā vietā HMTL dokumentā.

	*index.html:*
	```html
	<body>
		Wake up, Neo...
		<script>
			alert('The Matrix has you...');
		</script>
		Follow the white rabbit.
	</body>
	```

0. Atsevišķā failā, pieslēdzot to HTML dokumentā.

	*trinity.js:*
	```js
	alert('The Matrix has you...');
	```

	*index.html:*
	```html
	<body>
		Wake up, Neo...
		<script src="trinity.js"></script>
		Follow the white rabbit.
	</body>
	```

	Modernā tendence pieslēgt js failu dokumenta beigās, pirms `</body>`.

## Sintakse

```js
// single line
/* Multi
   line
   comments */
```

*Mainīgie:*
```js
var a = 1;

var fooBar = 2, foo_bar = "baz", // letters: [ascii, unicode]
	_fooBar1 = true, $foo = [ "baz", 0 ]; // start with: letters, _,  $

var a = 1, A = 2; // case-sensitive. a != A
```

Nonstrict:
```js
var a = 123; // local
a = 123; // global
```

*Key words:*	`break; case; catch; continue; default; delete; do; else; finally; for; function; if; in; instanceof; new; return; switch; this; throw; try; typeof; var; void; while; with.`

*Reserved words:*
 - Nonstrict: `class; const; enum; export; extends; import; super;`
 - `'use strict'`: `implements; interface; let; package; private; protected; public; static; yield;`

## Datu tipi

Pamata JS datu tipi: Number, String, Boolean, Undefined, Object, Null, Function.

Pārbaudīt vērtības datu tipu var ar operātoru `typeof`. Piem.: `typeof x`.

### Number [Primitive like]

Skaitlis. `typeof x == 'number'`.

- 0
- 1.2
- 045
- 0x56
- 0.314e2
- NaN — not a number.

```js
var a = 0;
typeof a // 'number'
```

Pārvērst par skaitli var jebkuru cita datu tipa vērtību izmantojot kontruktoru `Number()` vai funkcijas `parseInt()` un `parseFloat()`.

```js
var a = "b";
Number(a); // NaN
typeof Number(a); // number
```

`parseInt()` konvertē vērtību par veselo skaitli. `parseInt()` pieņem divus argumentus: mainīgo vai vērtību un skaitīšanas sistēmu, kurā ir dots mainīgais vai vērtība:
```js
var a = "20px";
typeof a // 'string'
var b = parseInt(a, 10); // 20
typeof b // 'number'
```

`parseFloat()` konvertē vērtību par decimāldaļskaitli:

```js
var a = "20.2px";
typeof a // 'string'
var b = parseInt(a); // 20
typeof b // 'number'
```

Gadījumā, ja vērtību nav iespējams pārvērst par skaitli augšminētās funkcijas atgriež `NaN` (not a number — nav skaitlis). Bet `NaN` datu tips jomprojām bus `number`.

```js
var a = "b";
var b = Number(a); // NaN
typeof b; // number
```

### String

Virkne. `typeof x == 'string'`.

*… turpinājums sekos …*

### Function

Funkcija. `typeof x == 'function'`. Kaut kāda darbība kuru var izsaukt un izpildīt.

Funkcija bez argumentiem:
```js
function myF(){ // funkcijas izveide
	console.log("foo");
}
myF(); // funkcijas izsaukšana un izpilde
```

Funkcija ar argumentiem:
```js
function sum(a, b){ // funkcijas izveide
	console.log(a + b); // 11
}
sum(5, 6); // funkcijas izsaukšana un izpilde
```

Īpašība `length` atgriež cik argumentu pieņem funkcija.
```js
console.log(sum.length); // 2
```

Funkcija var atgriezt rezultātu pēc izpildes. Rezultāts var saglabāt un apstrādāt.
```js
function sum(a, b){
	return a + b;
}
var z = sum(5, 6);
console.log(x); // 11
```
Svarīgi izsaucot funkciju sūtīt viņai tik daudz argumentu, cik tā pieņem. Gadījumā, ja argumentu skaits nesakrīt, būs kļūda.

Ja nav zināms cik argumentu tiek sūtīts funkcijai izsaucot to, tad var izmantot mainīgo `arguments`, kas ir massīvs ar visiem nosūtītiem funkcijai argumentiem.

```js
function sum(){
	var result = 0;
	for (var i = 0; i < arguments.length; i++){
		result += arguments[i];
	}
	return result;
}
console.log(sum(10, 45, 67, 28, 11, 38)); // 199
```

## Cikli

Cikls ir jēdziens, ar ko apzīmē vairākkārtīgu kādas instrukciju kopas izpildīšanu.

### for

Konstrukcija `for` sastāv no nosacījuma bloka un cikla ķermeņa. Nosacījuma blokā tiek noteiks nosacījums cik reizes ciklam ir jāatkārtojās. Cikla ķermeņa tiek noteikts viss kas tiks izpildīts katrā cikla iterācijā.
```js
for (var i = 0; i < 10; i++) {
	console.log("Hello world - " + i);
}
```
Šeit `i` — cikla skaitītājs:
- `var i = 0` — skaitītāja definēšana. Notiks tikai pirmajā iterācijā.
- `i < 10` — nosacījums. Ja nosacījums atgriež `true`, tad cikla ķermenis tiks izpildīts.
- `i++` — skaitītāja izmaiņa. Notiek katrā iterācijā pēc ķermeņa izpildes.

Ir arī iespēja paplašināt cikla nosacījumus un veikt darbības ar vairākajiem skaitītājiem.
```js
for (var i = 0, j = 10; i < 10 && j > 0; i++, j -= 2) {
	console.log("Hello world");
}
```
Piemērs ar masīviem:
```js
var arr = ["foo", "bar", "baz"];
for (var i = 0; i < arr.length; i++) {
	console.log(arr[i]);
}
```

### while un do…while

Līdzīgs for.

```js
var i = 0;
while (i < 10) {
	console.log("Hello world - " + i);
	i++;
}
```
un do…while:
```js
var i = 0;
do {
	console.log("Hello world - " + i);
	i++;
} while (i < 10);
```
`While` un `do…while` atšķirās ar to, ka while pārbauda nosacījumu pirms iterācijas izpildes, bet `do…while` — pēc. Sanāk ka `do…while` tiks izpildīts vismaz vienu reizi, piem. ja nosacījums no paša sākuma būs `false`.

### for…in (cikls objektiem)

```js
var obj = { name: "Vasilijs", surname: "Žukovs", job: "developer"};
for (i in obj) {
	console.log(i + ": " + obj[i] + "\n");
}
```
Izvadīs:
```
name: Vasilijs
surname: Žukovs
job: developer
```
