# Meterologisk årstid v 1.0 
 
Denna yaml-fil beräknar den Meterologiska årstiden enligt SMHIs defintion (nedan) baserat på temperaturen där du bor.
 
## Installation
1. Ladda ner och kopiera  (meteorological_season_se.yaml) till mappen /homeassistant/packages   (om du ej har mappen packages får du skapa den först).
2. Lägg in följande två rader configuration.yaml (eller uppdatera befintlig rad)

```yaml
homeassistant:
  packages: !include_dir_named packages

```

3.  Uppdatera följande rad "entity_id: sensor.genomsnittlig_utomhus_temp"  med din temperatursensor
4.  Spara och starta om Home Assistant.
5.  Nu kommer 
