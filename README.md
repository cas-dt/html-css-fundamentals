# HTML-CSS Einführung, Teil 2

## Attribute

Ein HTML-Tag kann eines oder mehrere *Attribute* haben. Attribute haben immer die Form `foo="bar"`: `foo` ist die «Eigenschaft», `bar` ein Wert: ein Wort oder eine Zahl.

### Beispiele

- `href="https://zhdk.ch"` Ziel eines Links (`<a>` Tag)
- `src="img/cat.jpg"` Pfad eines Bildes in einem `<img>` Tag
- `width="400" height="300"` Gr

Solche Attribute erweitern HTML-Tags um bestimmte Informationen, z.B. eine Link-Adresse.

**Attribute sind notwendig für Bilder und für Links.**

## Bilder

HTML-Dokumente enthalten nur Text. Damit eine Website trotzdem Bilder haben kann, gibt es den Tag `<img>`, der Bezug zu einer Bilddatei herstellt und angibt, an welcher Stelle des Dokuments es eingefügt werden soll.

Damit das Bild gefunden wird, braucht es einen Pfad zur Datei. Dieser wird mit dem Attribut `src` (‘source’) angegeben.

Für Benutzer\*innen, die auf eine Screen-Reader Software angewiesen sind und für Suchmaschinen braucht es einen beschreibenden Text zum Bild. Dieser wird mit dem `alt` Attribut (‘alternate text’) angegeben.

```
<img width="800" height="600" src="/img/mein-bild.jpg" alt="Bild einer Zimmerpflanze">
```

Die *Attribute* in diesem Beispiel bedeuten der Reihe nach:

- Das Bild wird mit einer Breite von 800 Pixeln gerendert.
- Das Bild wird mit einer Höhe von 600 Pixeln gerendert.
- Die Bilddatei liegt im Ordner `img` und hat den Namen `mein.bild.jpg`
- Der Text «Bild einer Zimmerpflanze" wird vorgelesen, wenn eine *Screen Reader Software* verwendet wird, und er wird von Suchmaschinen erfasst. Er wird auch angezeigt, wenn die Datei nicht gefunden wurde oder beschädigt ist.

Alle Attribute ausser `src` sind optional. Das `alt` Attribut ist relevant für *SEO* (Search Enginge Optimization) und für *Accessibility*. `width` und `height` sorgen dafür, dass auch wenn das Bild das Bild noch nicht fertig gerendert ist, Platz im Text dafür ausgespart wird. So lassen sich sprunghafte Verschiebungen beim Laden grösserer Bilder vermeiden.

## Bildformate

Browser können folgende Bildformate rendern:

- `jpg/jpeg` ein komprimiertes Bitmap-Format
- `png` ein komprimiertes Bitmap-Format mit Transparenz
- `gif` ein komprimiertes Bitmap-Format mit Transparenz, und mehreren Ebenen, die wie ein Daumenkino abgespielt werden können.
- `webp` (relativ neu) ein noch stärker komprimiertes Bitmap-Format. Ca. ein Drittel kleiner als jpg und png.
- `svg` ein Vektor-Format.

### Begriffe

Ein *Bitmap-Bild* ist aus Punkten unterschiedlicher Farbe aufgebaut. Wenn es zu klein abgebildet wird, ist es unscharf, wenn es zu gross abgebildet wird, erscheint es verpixelt. Als «Auflösung» wird die Dichte bezeichnet, mit der ein Bitmap-Bild gedruckt wird. Im Zusammenhang mit Screens ist die Auflösung eines Bildes ziemlich irrelevant: Ein 375 Pixel breites Bild wird im Browser so gerendert, dass es 375 Pixel breit ist. Beispiele: gif, tiff

**Ausnahme:** Es gibt Bildschirme mit sehr hoher Pixeldichte – bei Apple heisst das z.B. «Retina». Würden Websites (und andere GUI-Software) an solchen Screens normal skaliert, so wären die Dimensionen viel zu klein: Texte würden winzig erscheinen. Darum werden Pixel an solchen Bildschirmen vom Betriebssystem umgerechnet/skaliert. Im Web Design wird dann von CSS-Pixeln (umgerechnete Grösse) und Device-Pixeln (physisch vorhandene Pixel) gesprochen: An einem Bildschirm mit doppelter Pixeldichte enthält ein CSS-Pixel tatsächlich vier Device-Pixel, bei dreifacher Pixeldichte sogar neun Device-Pixel. In solchen Fällen wirken Bilder schärfer, wenn sie doppelt oder dreifach so gross sind, wie sie vom Browser gerendert werden. In der Praxis ist dieser Anwendungsfall aber eher selten, weil aufwendig.

Ein *Vektor-Bild* enthält Koordinaten von Punkten, Linien und Flächen, die zusammen ein Bild ergeben. Solche Bilder können ohne Qualitätsverlust vergrössert und verkleinert (Fachbegriff: *skaliert*) werden. Beispiele: EPS, SVG.

Durch *Komprimierung* wird eine Datei verkleinert. Im JPEG-Format werden z.B. Pixel, die nahe beieinanderliegen und ähnliche Farbewerte haben, zu Rechtecken zusammengefasst. Durch die Komprimierung findet in der Regel ein Qualitätsverlust statt.

## Links

Ein Link kann auf ein anderes HTML-Dokument führen, auf eine Datei anderen Formats (dann ist es ein Download-Link) oder auf eine «Sprungmarke» im gleichen Dokument (dann ist es ein Textanker).

- In jedem dieser drei Fälle wird der `<a>` Tag verwendet.
- Das Ziel des Links wird mit einem *Attribut* angegeben: `href="anderes-dokument.html"`
- Der Text zwischen <a> und </a> wird als *Ankertext* bezeichnet.

### Link auf ein anderes HTML-Dokument

`<a href="/about/">`

### Link auf eine anderes Website

`<a href="https://en.wikipedia.org/wiki/Foobar" target="_blank">`

Das Attribut `target="_blank"` sorgt dafür, dass das Ziel des Links in einem neuen Fenster / einem neuen Tab geöffnet wird.

### Link auf eine Sprungmarke

`<a href="#foo-bar>`

Sprungmarken werden in langen Dokumenten verwendet. Als Ziel fungiert ein HTML-Tag mit einem Attribut `id`, in der Regel eine Überschrift: `<h2 id="foo-bar">Foo Bar</h2>.

### Spezial-Links (für Expert\*innen)

Es gibt auch Links auf Stylesheets und JavaScript-Dateien. Diese werden **nicht** mit dem `<a>` Tag geschrieben.

Ein Beispiel für einen Link auf ein Stylesheet: `<link rel="stylesheet" href="style.css">`. Dieser Tag steht im `<head>` eines HTML-Dokuments.

Link auf eine JavaScript Datei: `<script  src="my-script.js"></script>`. Diese Tags stehen fast am Ende eines HTML-Dokuments: Nach dem schliessenden `</body>` Tag und vor dem schliessenden `</html>` Tag

## Masseinheiten in  CSS

### em und rem

Die Masseinheiten `em` und `rem` stehen für das Schriftgeviert und werden ausgehend von einer Basisgrösse errechnet. Bei `rem` ist es die Schriftgrösse des Selektors [`:root`](https://developer.mozilla.org/en-US/docs/Web/CSS/:root), bei `em` die des nächsten übergeordneten Elements, das eine definierte Schriftgrösse hat (fehleranfällig).

TL;DR – Verwende `rem`, nicht `em`!

    :root {
        font-size: 100%; /* Browser default */
        line-height: 1.3;
    }

    h1 { font-size: 1.75rem; }  /* 28px */

    h2 { font-size: 1.375rem; } /* 22px */

    p  { font-size: 0.875rem; } /* 14px */

    @media (min-width: 700px) { /* Breakpoint, siehe unten */
        :root { font-size: 150%; }
    }

Mit diesen Masseinheiten kannst du aufeinander abgestimmte Schriftgrössen definieren. Um das ganze System an verschiedene Ausgabegeräte oder Screen-Grössen anzupassen, reicht es, einen einzigen Grundwert anzupassen und alle Schriftgrössen werden proportional skaliert.

Im Beispiel oben ist der letzte Abschnit eine ‘Media Query’ (siehe unten): Das sind Regeln, die nur unter bestimmten Bediungungen gelten, hier z.B. für Bildschirme, die breiter als 700 Pixel sind.

### Punkt

Die Einheit Punkt `pt` gibt es auch in CSS. Sie ist ca. ein Viertel grösser als ein Pixel und entspricht dem typographischen Punkt (1/72 Zoll). Ob ein Screen entsprechend geeicht ist, ist nicht gewährleistet. Darum solltest du Einheiten wie Punkt und Millimeter nur für [Print-Stylesheets](https://alistapart.com/article/goingtoprint) einsetzen.

Verwirrenderweise sprechen auch iOS-App Developer von Punkt, meinen damit aber eine Einheit, die gleich gross wie ein CSS-Pixel ist 🤯. Damit soll eine Verwechselung mit den eigentlich im Gerät eingebauten *Device-Pixeln* vermieden werden, deren Anzahl bei gleicher Breite je nach Gerät stark variieren kann. So sind die Bildschirme von iPhone 6 bis iPhone X 375 CSS-Pixel breit, enthalten aber auf der Horizontalen in Wirklichkeit zwischen 750 und 1242 «Gerätepixel».

Fun Fact: Unter [Andoid Devs heisst die Einheit wiederum `dp`](https://developer.android.com/guide/topics/resources/more-resources.html#Dimension).
