# Meterologisk årstid v 1.1
 
Denna yaml-fil beräknar den Meterologiska årstiden enligt SMHIs defintion (nedan) baserat på temperaturen där du bor.

<img src="https://github.com/droidgren/home_assistant/blob/main/meteorological_season/brick-card.png">
<img src="https://github.com/droidgren/home_assistant/blob/main/meteorological_season/entitiy.png">


## Installation
1. Ladda ner och kopiera  (meteorological_season_se.yaml) till mappen /homeassistant/packages   (om du ej har mappen packages får du skapa den först).
2. Se till configuration.yaml har denna konfiguration för att kunna läsa in filen , om "homeassistant:" redan finns lägger du till packages-raden

```yaml
homeassistant:
  packages: !include_dir_named packages

```

3.  Uppdatera följande rad "entity_id: sensor.genomsnittlig_utomhus_temp"  med din temperatursensor
4.  Spara och starta om Home Assistant.
5.  Nu kommer ett antal räknare och datum entiteter att skapas samt en sensor och automation
6.  Sensorn "Meterologisk årstid" kommer nu att ange aktuell årstid och datum när detta inträffade.  Observera att det tar 5-7 dagar (beroende på årstid) innan detta kan fastställas.

###  Uppdatera datum årstid i efterhand
1. Om det tex är vår, kolla vilket datum detta inträffade på följande sida: https://www.smhi.se/vader/observationer/ankomstkarta/
2. Ange datumet i entiten input_datetime.mst_**XXXX**_arrival_date (tex 2025-02-21 ) XXXX = Spring, Summer, Autumn, Winter
3. Slå på entiteten input_boolean.mst_**XXXX**_date_set
4. Övriga årstidsdatum visas som attribut till entiteten Meterologisk årstid ( Se bild nedan). Om datum för dessa ej är angivna kommer de visa det datum som skripet startade på första gången. Om du ej vet vilket datum årstiden inträffade på kan du sätta datummet till 1970-01-01, då kommer datumet inte visas tills det får ett korrekt datum. 


### Övrigt
- Observera att sensorn endast uppdateras en gång per dygn
- Som attribut till Meterologisk årstid finns även förra dagens genomsnittstemp, samt historik för tidgare datum då årstider inträffade. 
<img src="https://github.com/droidgren/home_assistant/blob/main/meteorological_season/attribut.png">
## Defintioner (från SMHI) 
### Vinter
Vintern anländer om det råder vintertemperatur fem dygn i följd. 
Vintertemperatur är det då dygnsmedeltemperaturen är 0,0°C eller lägre, men ännu inte fem dygn i följd. 
Vinterns ankomstdatum avser det första dygnet av fem med vintertemperaturer.

### Vår
Våren anländer om det råder vårtemperatur sju dygn i följd. 
Vårtemperatur är det då dygnsmedeltemperaturen är över 0,0°C, men ännu inte sju dygn i följd. Vårens ankomstdatum avser det första dygnet av sju med vårtemperaturer. 
Den 15 februari har satts som det tidigaste tillåtna datumet för vårens ankomst. 
Senast möjliga datum för vårens ankomst är den 31 juli.

### Sommar
Sommaren anländer om det råder sommartemperatur fem dygn i följd. 
Sommartemperatur är det då dygnsmedeltemperaturen är 10,0°C eller högre, men ännu inte fem dygn i följd. 
Sommarens ankomstdatum avser det första dygnet av fem med sommartemperaturer.

### Höst
Hösten anländer om det råder hösttemperatur fem dygn i följd. 
Hösttemperatur är det då dygnsmedeltemperaturen är under 10,0°C, men ännu inte fem dygn i följd. Höstens ankomstdatum avser det första dygnet av fem med hösttemperaturer. 
Den 1 augusti har satts som det tidigaste tillåtna datumet för höstens ankomst. 
Senast möjliga datum för höstens ankomst är den 14 februari.
