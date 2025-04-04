Meterologisk årstid v 1.0 
 
Denna yaml-fil beräknar den Meterologiska årstiden enligt SMHIs defintion (nedan) baserat på temperaturen där du bor.
 
Installation
1. Ladda ner och kopiera denna yaml fil  (meteorological_season_se.yaml) till mappen /homeassistant/packages   (om du ej har mappen packages får du skapa den först)
2.  Lägg in följande två rader configuration.yaml (eller uppdatera befintlig rad)

homeassistant:
 packages: !include_dir_named packages

3. Spara och starta om Home Assistant
