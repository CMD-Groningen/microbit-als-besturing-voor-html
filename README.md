# Micro:bit bewegingssensor voor besturing van animaties en audio in HTML pagina

Dit is een werkend voorbeeld inclusief instructies over hoe je een microbit als input kan gebruiken om apparaten buiten de micro:bit te bedienen. Door bijvoorbeeld in dit geval de microbit te schudden of ondersteboven te draaien, kun je videos, animaties of mp3 audio afspelen in de browser op je laptop of tablet. De micro:bit is dan de input en de laptop of tablet de output.

Door deze stappen te volgen, kun je de micro:bit gebruiken om interacties in bijvoorbeeld een webpagina te besturen, wat een leuke manier is om fysieke input en bediening te integreren met laptop of tablet en interface design. 

### Wat zit er in de download?

- **HTML en CSS** 
  - De HTML-pagina bevat een div (`#animate`) en een knop (`#connectButton`).
  - De CSS code bevat verschillende CSS classes (`grijs`, `groen`, `blauw`, `shake`) voor de div met bijbehorende animaties.
- **JavaScript** 
  - Controleert of de browser de Web Serial API ondersteunt.
  - Beheert de verbinding met de micro:bit via de seriële USB poort.
  - Leest data van de micro:bit en verwerkt deze om de CSS classes op de DIV te wijzigen, wat verschillende animaties activeert.
  - Laat de DIV "dansen" en speelt een geluid af bij de `Shake`-actie.
- **Micro:bit code**
  - Stuurt seriële USB data naar de computer gebaseerd op gedetecteerde gebaren input van de Micro:bit (`LogoUp`, `LogoDown`, `Shake`).

## Wat heb je nodig?

- Een computer met een moderne webbrowser die de Web Serial API ondersteunt (bijv. Google Chrome).
- Een micro:bit (versie 2 heeft de voorkeur, maar versie 1 kan ook) met USB-kabel.
- Een **HTML pagina** met code voor de browser 
- een **HEX bestand** met code voor de Micro:bit
- en een geluidsbestandje genaamd **disco.mp3**

De HTML pagina, de HEX file en het MP3 geluidsbestandje zijn alle drie meegeleverd als je dit Github project download naar je laptop! > klik hier

## Stappen

### Voorbereiding van de Micro:bit:

1. Open de Makecode editor op https://makecode.microbit.org/
2. Kopieer onderstaande microbit code naar de editor:

- Klik op `New Project`.

- Voeg de volgende code toe in de JavaScript of Blok modus  (je kunt bovenin de editor kiezen tussen Blocks of JavaScript invoer)

- Deze code zorgt ervoor dat input die je maakt op de micro:bit niet alleen naar het LED schermpje, maar ook via de USB kabel naar je laptop toegestuurd word (PS. dit is de microbit code ook in het HEX bestand zit)

  ```javascript
  serial.redirectToUSB()
  basic.forever(function () {
      if (input.isGesture(Gesture.LogoUp)) {
          basic.showString("L")
          serial.writeLine("L")
          basic.pause(1000)
          basic.clearScreen()
      }
      if (input.isGesture(Gesture.LogoDown)) {
          basic.showString("E")
          serial.writeLine("E")
          basic.pause(1000)
          basic.clearScreen()
      }
      if (input.isGesture(Gesture.Shake)) {
          basic.showString("S")
          serial.writeLine("S")
          basic.pause(1000)
          basic.clearScreen()
      }
  })
  ```

### Upload de code naar de micro:bit

- Sluit de micro:bit aan op je computer via de USB-kabel.
- Je kunt op de paarse "download" button helemaal links onderin de editor klikken om de code naar je micro:bit te kopiëren.
- Je kunt de code ook op een andere manier op je microbit opslaan, namelijk:
- download de `.hex` file naar je computer.
- Sleep de gedownloade `.hex` file naar de micro:bit drive die op je computer verschijnt.

### Voorbereiding van de HTML-pagina

1. Maak een HTML bestand aan op de volgende manier:

   - Maak een leeg mapje/folder aan en open deze in VsCode.
   - Maak een bestand aan genaamd **index.html** en kopieer de gegeven HTML-code in dit nieuw bestand.
   - Voeg het **geluidsbestand** (disco.mp3) toe in diezelfde folder. Dus zorg ervoor dat je een geluidsbestand genaamd `disco.mp3` hebt en plaats dit in dezelfde directory als de `index.html`.

### Uitvoeren in de browser

1. **Open de HTML-pagina in je browser**:
   - Dubbelklik op `index.html` om deze in je standaardwebbrowser te openen. Zorg ervoor dat je een browser gebruikt die de Web Serial API ondersteunt (zoals Google Chrome).
2. **Verbind de micro:bit met de browser**:
   - Klik op de button "Verbinden met micro:bit" op de geopende HTML-pagina.
   - Er verschijnt een pop-up waarin je de micro:bit kunt selecteren. Kies de micro:bit en klik op `Connect`.
   - Rechtsklik in de HTML pagina en kies in het dropdownmenu voor **inspect** om de Google Chrome code inspector te openen. In het tabblad van de **console** kun je precies zien wat er van moment tot moment gebeurt op de achtergrond terwijl de micro:bit met de browser communiceert!

### Interactie met de micro:bit en de HTML pagina

- Zodra de verbinding is gemaakt, kun je de micro:bit verschillende gebaren laten detecteren:
  - **Logo omhoog (Logo Up)**: De div verandert naar een groene achtergrond en wordt vergroot en verkleind.
  - **Logo omlaag (Logo Down)**: De div verandert naar een blauwe achtergrond en wordt vergroot en verkleind.
  - **Schudden (Shake)**: De div begint te schudden en het geluid `disco.mp3` wordt afgespeeld.

