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
