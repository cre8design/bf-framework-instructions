# Instructions

## Folder Structure

- assets
  - css
    - style.css
    - [..].css
  - img
    - [..].jpg
- index.html
- [..].html

## Css Variables

Css Variablen werden verwendet um Werte zu speichern, die in mehreren CSS Klassen verwendet werden. Dadurch können diese Werte an einer Stelle geändert werden und werden automatisch in allen Klassen aktualisiert.

Bitte Css Variablen verwenden für Sachen wie:
- Farben
- Schriftgrößen
- Schriftarten
- Abstände

Beispiel:
```css
:root {
	--color-primary-100: #f0f4ff;
}

.element {
	background-color: var(--color-primary-100);
}
```

[https://www.w3schools.com/css/css3_variables.asp](https://www.w3schools.com/css/css3_variables.asp)

## BEM Standard

BEM steht für Block Element Modifier und ist ein Standard für die Benennung von CSS Klassen. Dieser Standard wird verwendet um die CSS Klassen zu strukturieren und zu vereinheitlichen. Dadurch wird der Code lesbarer und einfacher zu warten.

[https://getbem.com/introduction/](https://getbem.com/introduction/)

## Normalization

Jeder Browser hat seine eigenen Standardeinstellungen für HTML Elemente. Um diese zu überschreiben und ein einheitliches Aussehen zu gewährleisten, wird ein CSS Normalizer verwendet. Dieser ist in der Datei `normalize.css` zu finden und muss in jede HTML Datei eingebunden werden oder in die `style.css` kopiert werden.

#### Images
Würde allen Bildern eine max-width von 100% geben und padding und margin zurücksetzen.

Beispiel:
```css
img {
	max-width: 100%;
	padding: 0;
	margin: 0;
}
```

#### Links
Links würde ich grundsätlich normalisieren und dann als teil von paragraphen und headlines neu definieren.

Beispiel:
```css
a {
	color: inherit;
	text-decoration: none;
}

p a,
.paragraph a {
	color: var(--color-primary-100);
	text-decoration: underline;
}
```

## Common Elements

#### Typo

Css Klasssen für die Textformatierung.

- h1, .headline-1
- h2, .headline-2
- h3, .headline-3
- h4, .headline-4
- p, .paragraph
- small, .small

Vieleicht noch einige extra Klassen für besonders grosse Headlines
- .display
- .display-l
- .display-xl

#### Spacer Helpers
Helfsklassen um margins, paddings und gaps zu definieren. Normal hat man in den Css Variablen die Werte für die Abstände definiert. Diese können dann in den Helfsklassen verwendet werden. Idealerweise hat man für jedes Attribute, jede Richtung und jeden Wert eine Klasse.

Beispiel:
```css
:root {
	--spacing-xs: 0.25rem;
	--spacing-s: 0.5rem;
	--spacing-m: 1rem;
	--spacing-l: 2rem;
	--spacing-xl: 4rem;
}

.p {
	padding: var(--spacing-m);
}

.p-l {
	padding-left: var(--spacing-m);
}
...

.py-xl {
	padding-top: var(--spacing-xl);
	padding-bottom: var(--spacing-xl);
}
...

.mt-xs {
	margin-top: var(--spacing-xs);
}
...

.gap {
	gap: var(--spacing-m);
}

```

#### Color Helpers
Helfsklassen für Farben. Jeweils für den Hintergrund und den Text für alle wichtigen Farben.

Beispiel:
```css

:root {
	--color-primary-100: #f0f4ff;
	...
}

.bg-primary-100 {
	background-color: var(--color-primary-100);
}
...

.text-primary-100 {
	color: var(--color-primary-100);
}
...
```

#### Other Helpers
Weitere Helfsklassen für Sachen wie:
- border-radius
- flex, align-items, justify-content

#### Grid & Layout
Grid und Layout Klassen für die Positionierung von Elementen.

- page__section
  - Container klasse für eine Sektion die den ganze breite des Bildschirms einnimmt.
- page__container
  - Container klasse die eine maximale Breite hat. 
- grid
	- Container klasse für ein Kolumen. Normalerweise hat man immer 12 Kolumen.
- grid__col-[1..12]
  - 12 Kolumnenklassen für die Breite der Kolumen. Die Zahl bestimmt wie viele Kolumen die Klasse einnimmt.

Beispiel mit Helferklassen für eine Sektion mit zwei Kolumen, einer Hintergrundfarbe und einem Abstand nach oben und unten:

```html
<!-- Sektion mit voller weite, padding nach oben und unten und einer Hintergrundfarbe -->
<section class="page__section py-xl bg-primary-100">
	
	<!-- Container mit max. Breite -->
	<div class="page__container">
		
		<!-- Grid mit 12 Kolumen, Abtand zwischen den Kolumnen und horizontal zentierten kolumnen -->
		<div class="grid gap align-items-center">
			<div class="grid__col-6">
				...
			</div>
			<div class="grid__col-6">
				...
			</div>
		</div>
	</div>
</section>
```

#### Buttons
Eine Standard Klasse für buttons die für ```<button>``` und ```<a>``` Elemente functioniert und modifier klassen:
- .btn
- .btn--primary (Primary Color)
- .btn--secondary (Secondary Color)
- .btn--sm (Small)
- .btn--lg (Large)
- .btn--fw (Full Width)
- .btn--disabled (Disabled)

Beispiel:
```html
<button class="btn btn--primary btn--lg">
	Large Primary Button
</button>
<a href="#" class="btn btn--secondary btn--fw">
	Full Width Secondary Button
</a>
```

#### Badges
Eine Standard Klasse für badges die für ```<span>``` und ```<a>``` Elemente funktioniert und modifier klassen. Im grunde das gleiche wie bei Buttons
- .badge
- .badge--primary (Primary Color)
- .badge--secondary (Secondary Color)
- .badge--sm (Small)
- .badge--lg (Large)

Beispiel:
```html
	<span class="badge badge--primary badge--lg">
		Large Primary Badge
	</span>
	<a href="#" class="badge badge--secondary badge--sm">
		Small Secondary Badge
	</a>
```

#### Toolbar
Im grunde ein Container mit einem Abstand zwischen den Elementen. Wird genutzt um buttons, badges oder andere Element nebeneinander anzuordnen.

Beispiel:
```html
<!-- Beispiel mit zwei Buttons nebeneinander -->
<div class="toolbar">
	<button class="btn btn--primary btn--lg">
		Large Primary Button
	</button>
	<button class="btn btn--secondary btn--lg">
		Large Secondary Button
	</button>
</div>
```

#### Breadcrumbs
Klassen für Breadcrumbs.

Beispiel:
```html
<nav class="breadcrumbs">
	<a class="breadcrumbs__item" href="#">Home</a>
	<a class="breadcrumbs__item" href="#">Unter Seite</a>
	<strong class="breadcrumbs__item breadcrumbs__item--current">Unter Unter Seite</strong>
</nav>
```

#### Cards
Klassen für Cards. Zum Beispiel Produkte.

Beispiel:
```html
<div class="card">
	<div class="card__media">
		<img class="card__image" src="..." alt="...">
	</div>
	<div class="card__content">
		<div class="card__title">
			Some Title
		</div>
	</div>
</div>
```

#### Input, Form, Label & Field (schwierig)
Klassen für Inputs, Forms, Labels und Fields.

Wichtige Typen:
- input text
- input number
- input password
- input checkbox
- input radio
- select
- textarea

Beispiel:
```html
<form class="form">
	<div class="field">
		<label class="label" for="input-1">Input 1</label>
		<input class="input" id="input-1" type="text">
	</div>
	...
</form>
```

#### Toasts
Toasts sind alerts, meistens in form von Popups um den User über ein Event zu informieren.

Beispiel:
```html
<aside class="toasts">
	<div class="toast toast--success">
		<div class="toast__title">
			Some Title
		</div>
		<div class="toast__message">
			Lorem ipsum dolor
		</div>
		<div class="toast__close">
			X
		</div>
	</div>
</aside>
```

### Responsive und Media Queries (schwierig)

Mit media queries kann man CSS Klassen für bestimmte Bildschirmgrössen definieren. Zum Beispiel für mobile, tablet und desktop.

Beispiel:
```css
:root {
	--breakpoint-mobile: 480px;
	--breakpoint-tablet: 768px;
	--breakpoint-desktop: 1024px;
}

.element {
	background:red;
	
	/* Ab der Tablet grösse wird die Hintergrundfarbe mit blau überschrieben */
	@media (min-width: var(--breakpoint-tablet)) {
		background:blue;
	}
}
```
[https://www.w3schools.com/css/css_rwd_mediaqueries.asp](https://www.w3schools.com/css/css_rwd_mediaqueries.asp)

Wir können auch dafür Helfsklassen definieren. Zum Beispiel für die Sichtbarkeit von Elementen.
```css
.visible-mobile {
	display: none;
	
	@media (max-width: var(--breakpoint-mobile)) {
		display: block;
	}
}

.visible-tablet {
	display: none;

	@media (min-width: var(--breakpoint-mobile)) {
		display: block;
	}
}
```

Oder für die Breite von Kolumnen.
```css
.grid__col-12 {
	grid-column: 1 / span 12;
}

.grid__col-desktop-6 {
	@media (min-width: var(--breakpoint-desktop)) {
		grid-column: 1 / span 6;
	}
}
```
Dann können wir die Kolumnen so verwenden um eine Kolumne auf dem Handy über die ganze Breite zu machen und auf dem Desktop in zwei Kolumnen aufzuteilen.

```html
<section class="page__section">
	<div class="page__container">
		<div class="grid">
			<div class="grid__col-12 grid__col-desktop-6">
				...
			</div>
			<div class="grid__col-12 grid__col-desktop-6">
				...
			</div>
		</div>
	</div>
</section>
```
