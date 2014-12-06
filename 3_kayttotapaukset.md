##Käyttäjäryhmät
Järjestelmän käyttäjäryhmät ovat ***"muurahaiset"***, ***"kyylät"*** ja **ylläpitäjät**. 

**"Muurahaiset"** ovat kiinteistön tilojen käyttäjiä. He eivät suoraan vuorovaikuta sovelluksen kanssa, vaan ainoastaan tuottavat paikkatietodataa. Järjestelmän normaalissa toiminnassa on oletuksena, että jokaisella tilojen käyttäjällä, "muurahaisella", on mukanaan etäluettava tunniste, joka on luettavissa käyttäjän oleskellessa missä tahansa rakennuksen tiloissa.

**"Kyylät"** ovat OLAF-analyysisovelluksen pääkäyttäjäryhmä. Heillä on käyttöliittymäsovelluksen kautta pääsy järjestelmän tuottamaan analyysitietoon tilojen käytöstä. He hyödyntävät järjestelmän tuottamaa tietoa, esim. suunnitellessaan tilojen tehokkaampaa käyttöä.

**Ylläpitäjät** hallinnoivat järjestelmää. He pitävät huolen tilamallin ajantasaisuudesta, lisäävät käyttäjiä ja muokkaavat käyttäjien oikeuksia, lisäävät muurahaisten etätunnisteet paikannusjärjestelmään. Ylläpitäjät saavat ylläpitoraportteja paikannusjärjestelmän toiminnasta.

## Käyttötapaukset

![Käyttäjätapaukset](http://users.metropolia.fi/~katikal/files/OLAF-UseCaseDiagram.png)

#Käyttäjätarinoita

###Muurahaiset
* Muurahaisena haluan, että järjestelmä on omalta kannaltani huomaamaton, jotta siitä olisi minulle mahdollisimman vähän vaivaa. 
* Muurahaisena haluan tietää, mihin tietoja käytetään ja kenen toimesta, jotta minun on helpompi hyväksyä  yksityisyyteni mahdollinen vaarantaminen
* Muurahaisena haluan, että minun tallusteluani talossa ei pysty seuraamaan, koska olisi kammottava ajatus että joku kyttäisi minua. Haluan, että minua ei voi yksilöidä kerätystä datasta.

###Tiedon käyttäjät
* Tilojen käytön suunnittelijana haluan nähdä **taulukkomuotoisen datan** lisäksi **visualisoinnin** (time lapse&heat map-esitys?) siitä, missä päin rakennusta käyttäjät enimmäkseen ovat vuorokauden aikana, jotta tilankäyttöä voitaisiin tehostaa ja (opiskelijoiden) työskentelytiloja kehittää
* Lounasruokalan esimiehenä haluan hakea ruokalan käyttäjätiedot lounaan ruuhka-ajalta, jotta pöytien sijoittelua voidaan parantaa, ja jotta keittiö voi ennakoida ruuhkapiikkejä
* Tiedon käyttäjänä haluan tallentaa toimialani piirissä olevat tilat omaan näkymääni, jotta pääsen tilojeni tietoihin myöhemmin nopeasti käsiksi
* Tiedon käyttäjänä haluan hakea tiloja luokitellusta näkymästä (luokat, ryhmätyötilat, neuvotteluhuoneet, toimistot, wc:t ym.), jotta voin valita esimerkiksi kaikki neuvottelutilat kerralla
* Siivouksesta vastaavana kiinteistönhoitajana haluan tietää, missä wc-tiloissa on vuorokauden aikana eniten käyttäjiä, jotta siivouksen lisäresurssit voidaan kohdentaa hyödyllisemmin
* Tilojen käytön suunnittelijana haluan ladata hakutuloksien kuvat tiedostoina käytettäväksi muissa ohjelmissa.

###Ylläpitäjät
* Ylläpitäjänä haluan päivittää pohjapiirroksen ja huoneiden koordinaatit, jotta remontin jälkeen tulleet tilamuutokset (seinien purku / rakennus ym?) voidaan huomioida 
* Ylläpitäjänä haluan lisätä *tiedon käyttäjien* käyttäjäryhmään henkilön, jotta uusi työntekijä pääsee töihin
* Ylläpitäjänä haluan parantaa joidenkin tilojen paikannustarkkuutta asentamalla valittuihin tiloihin lisää tukiasemia.
* Ylläpitäjänä haluan korvata vikaantuneen paikannustukiaseman uudella, ja päivittää uuden tukiaseman asetukset helposti.


## Keskeiset käyttötapausskenaariot
***
#### Käyttötapaus: Ole tiloissa
- **käyttäjäryhmä:** "*Muurahainen*"
- **alkutila (initial state):** Henkilö saapuu kiinteistöön, mukanaan järjestelmään kuuluva toimiva etälukutunniste.
- **normaali kulku (normal flow):**
	1. Henkilö oleskelee tiloissa
- **lopputila (end state):**
	- Henkilö poistuu 
- **vaihtoehtoiset kulut (alternate flow):**
	- Käyttäjällä ei ole etälukutunnistetta mukanaan
	- Etälukutunnisteen lukeminen ei onnistu: tunniste on liian lähellä metalliesineitä, liian kaukana lukijasta, tunniste on vaurioitunut, paristo on lopussa, radiotaajuuksissa on häiriöitä, paikannusjärjestelmässä on toimintahäiriö...
	- Etälukutunnistetta ei ole kirjattu järjestelmään tai se on poistettu järjestelmästä
	- Paikannusjärjestelmässä on toimintahäiriö
	- Käyttäjä on paikannusjärjestelmän katvealueella
- **samanaikainen tapahtuma**
	- Muut käyttäjät oleskelevat samoissa tiloissa, paikannusjärjestelmä lukee etätunnisteita

Huomattavaa on, että missään kuluista (normaali tai vaihtoehtoinen) "muurahainen" eli tilojen käyttäjä ei saa palautetta virhetilanteista tai järjestelmän normaalista toiminnasta. Järjestelmä pystyy tuottamaan paikkatietodataa ja toimimaan normaalisti, kunhan riittävän suuri osa "*muurahaisten*" etätunnisteista on riittävän usein luettavissa. (Riittävän suuri onnistumisprosentti on tässä tapauksessa jätetty tarkemmin määrittelemättä.)

***
#### Käyttötapaus: hae tilan käyttöhistoria
- **käyttäjäryhmä**: "*Kyylät*"
- **alkutila:** Käyttäjä on kirjautunut järjestelmään
- **normaali kulku:**
    1. Valitse toimintovalikosta hakutoiminto
    2. Käyttäjälle esitetään hakusivu, osa käyttöliittymäkomponenteista päivittyy hakunäkymän mukaisiksi
    3. Rajaa hakuparametriksi haluttu tila tai ryhmä tiloja:
        1.  lisää tiloja valintaan aktivoimalla ne
	        1. pohjapiirroksesta
	        2. listalta
	        3. kirjoittamalla nimi (niin monta kertaa kuin tarpeen)
        2.  poista tiloja valinnasta kartalta / listalta (niin monta kertaa kuin tarpeen)
    4. Rajaa hakuparametriksi haluttu ajanjakso aikajanalta
	    1. liukusäätimillä
	    2. syöttämällä päivämäärätiedot kenttiin
	    3. rastittamalla haluttujen viikkojen valintaruudut
    5. Valitse visualisoinnin esitystapa mahdollisten joukosta
	    1. heat map
	    2. ortograafinen 3D
	    3. kuvaaja (käyttäjät/aika)
	    4. taulukko
	    5. raakadata
	    6. (muita?)
    6. Suorita hakutoiminto valitsemalla hakupainike.
    7. Tarkastele hakutuloksia käyttöliittymän näkymässä.
    8. Mahdollisesti tallenna hakutulos tai hakuparametrit pikavalinnaksi, tai tulosta hakutulos
- **lopputila:**
	- Järjestelmä hakee tietokannasta valitut tiedot ja generoi valitun esitystavan mukaisen visualisoinnin.
	- Mikäli käyttäjä halusi tallentaa hakutuloksen, esitetään käyttäjälle tallennuksen valintaikkuna.
	- Mikäli käyttäjä halusi tallentaa hakuparametrit, lisätään käyttäjän tallennettuihin hakuihin uusi pikavalinta.
	- Hakutulosten rajaukset säilyvät seuraavaa hakua varten
- **vaihtoehtoiset kulut:**
    3a. Valitse valintapalkista aiempi tallennettu hakupikavalinta
    3b. Valitse yksi oletuspikavalinnoista (esim. uusi puoli, vanha puoli, kaikki ATK-luokat, kaikki auditoriot, ruokala)
    4a. Käyttäjä jättää valitsematta mitään ajanjaksoja. Voidaan joko muistuttaa käyttäjää valinnoista, tai käyttää oletusaikajaksoa, esim. yhtä viikkoa.
    5a. Käyttäjä jättää valitsematta esitystavan. Käytetään oletusesitystapana heat mappia.
    7a. Tulosta käyttäjälle virheilmoitus epäonnistuneesta hausta. Ehdota ratkaisuja, jos virheen syy on tiedossa.
    7b. Jos esitystavaksi oli valittu taulukko, tarjoa mahdollisuuksia järjestää taulukon tietoja
    3-5b. Muokkaa aiemman haun valintoja ja tee uusi haku
***
#### Käyttötapaus: lisää järjestelmään uusi käyttäjä
- **käyttäjäryhmä**: Ylläpitäjät
- **alkutila:** Ylläpitäjä on kirjautunut järjestelmään, ja valinnut "käyttäjien hallinta" -ylläpitonäkymän.
- **normaali kulku:**
	1. valitse toiminto "lisää uusi käyttäjä".
	2. Syötä käyttäjän tiedot kenttiin (nimi, sähköpostiosoite, käyttäjäprofiili jne.)
	3. Valitse käyttöoikeuksien laajuus (tavallinen käyttäjä, ylläpitäjä)
	4. Vahvista uuden käyttäjän luonti valitsemalla painike "lisää käyttäjä".
- **lopputila:**
	- Järjestelmä lähettää uudelle käyttäjälle sähköposti-ilmoituksen.
	- Mikäli organisaation käytössä ei ole keskitettyä autentikointipalvelua, uudelle käyttäjälle luodaan kertakäyttöinen salasana, joka lähetetään sähköpostin mukana.
	- Uusi käyttäjä näkyy käyttäjälistauksessa.
- **vaihtoehtoiset kulut:**
	- Järjestelmässä on jo samalla nimellä/käyttäjätunnuksella toinen käyttäjä. Uutta käyttäjätunnusta ei voida luoda, ja palataan vaiheeseen 2. Kenttiin täytetyt tiedot eivät katoa.
	- Osa syötetyistä tiedoista on virheellisiä. Korostetaan virheelliset kentät, ja palataan vaiheeseen 2.