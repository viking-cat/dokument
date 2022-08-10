---
parent: "Blender"
layout: page
title: "Skulptering"
---

Blender har ett skulpterings läge som påminner mycket om ZBrush. Blender är dock lite anorlunda, framförallt pga att ZBrush specialiserar på en sak medan Blender är en sweichisk armé kniv. Förut var inte skulpteringsverktygen så stabila men Blender utvecklarna har tagit konkuransen på allvar och många stora uppdateringar har därför de senaste åren varit fokuserade på att förbättra detta läge...

# Förberedelser

## Tillägg

<span style="float:right; text-align:right; display:inline-block; width:400px;">
  <img src="/dokument/assets/blender-sculpting-preferences-add_ons.JPG" alt="Preference Window" style="width:400px;">
</span>

* Gå till ***Edit -> Preferences*** i menyn
* Välj sedan Add-ons i sido menyn till fönstret som öppnas.
* Sök efter "***extra***"
* Välj följande plugins:
  * Add Curve: Extra Options
  * Add Mesh: Extra Options
* Välj slutligen ***Save Preferences***

<div style="clear:right;"></div>

## Radera Scene Objekt

<div style="float:right; text-align:right;width:400px; object-fit:contain;">
  <img src="/dokument/assets/blender-sculpting-delete_sceen_contents.JPG" alt="Preference Window" style="width:400px;">
</div>

* Go to the top right menu area with the scene contents.
* Select one or more items, right-click and select delete.
* Repeat if necessary until everything has been removed.

<div style="clear:both;"></div>

## Skapa Referens Bilder

Försäkra dig om att du är i ***Object Mode*** läget:
* Tryck *****ctrl + tab***** för att öppna läges-cirkel-menyn.
* Välj "***object mode***"

Lägg nu till en rundad kub:
* Tryck *****shift + a***** för att öppna "Add" menyn
* Välj "***Image -> Background***" så öppnas en dialog för att välja bild 
  * ***Det finns ett alternativ för referensbild men denna krånglar ibland***
  * ***Bilden kan komma att läggas till i en udda vinkel men det rätar vi strax till***
  * Du behöver en bild för varje vinkel, vanligast är att man utgår från en fram, bak och sidobild.
    * Repetera detta för varje bild som du har
    * Alternativ, gör följande för att duplicera bilden
      * Gå till ***Scene Objects*** i översta högra hörnet.
      * Välj markera bilden som du vill duplicera
      * Tryck ******ctrl + x***** för att kopiera den
      * Tryck ******ctrl + v***** för varje kopia som du vill skapa
* Bilderna kan ligga i en underlig position för tillfället så gör följande:
  * Tryck *****n***** för att öppna "Transform" menyn på höger sida
    * Försäkra dig om att du är på "Item" tabben. Du bör se X,Y,Z för Locaiton, Rotation och Scale.
      * Location och Scale skall alltid vara:
        * Location: 0, 0, 0
        * Scale: 1, 1, 1
      * Rotationen måste ändras individuellt:
      * Framsidans rotation: 90, 0, 0
      * Baksidans rotation: 90, 0, 180
      * Sidans rotation: 90, 0, 90
*  Just nu överlappar alla bilder och kommer vara i vägen, därför bör du gå till ***Object Data Properties*** tabben i menyn under listna med "Scenobjekten".
  * Alla bilder ska ha följande inställningar
    *  Depth: Back
    *  Showin in:
      *  Ortographic
      *  Only Axis Aligned
      *  ***Perspective avmarkerar du***
    *  Opacity: 0.5
  * Sedan gör du följande per bild:
    *  Framsidan
      * Side: Front
    *  Baksidan
      * Side: Back
    *  Sidobilden
      * Side: Both

## Skapa Rund Kub

<span style="float:right; text-align:right; display:inline-block; object-fit:contain; width:400px;">
  <img src="/dokument/assets/blender-sculpting-add_rounded_cube.JPG" alt="Preference Window" style="width:400px;"><br/>
  <img src="/dokument/assets/blender-sculpting-add_rounded_cube-options.JPG" alt="Preference Window" style="width:400px;">
</span>

Försäkra dig om att du är i ***Object Mode*** läget:
* Tryck *****ctrl + tab***** för att öppna läges-cirkel-menyn.
* Välj "***object mode***"

Lägg nu till en rundad kub:
* Tryck *****shift + a***** för att öppna "Add" menyn
* Välj "***mesh -> round cube***" för att lägga till en rundad kub
* Längst ner till vänster finns en öppen eller stängd meny, se till att följande värden är satta:
  * Radius: 1.00
  * Arc: 16

<div style="clear:both;"></div>

# Vektyg
...

# Referencer
* [Blender 2.9 Tutorial - Stylized Character Modeling - Part 1 of 9: Head Blockout & Rough Sculpt](https://youtu.be/UKI8_PAFFz4)
