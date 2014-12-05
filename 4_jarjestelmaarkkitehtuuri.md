##  Järjestelmäarkkitehtuuri

OLAF-järjestelmän pääkomponentteja ovat:

- **Paikannusjärjestelmä**
	- **Fyysinen paikannuslaite**, pitkän kantaman passiivinen etäluettava RFID-tunniste tai Bluetooth Smart -laite
	- **Paikannusverkon tukiasemat**, jotka tekevät kutsuja kantamansa sisällä oleville tunnisteille
	- **Ohjelmistokerros**, jonka vastuulla on
		- Ajoitettujen paikannuskyselypyyntöjen lähettäminen tukiasemille
		- Tukiasemilta saapuvan paikannusdatan käsittely (virhedatan siivoaminen, kelvollisen datan sovittaminen tilan pohjapiirrosmalliin)
		
- **Tietokantajärjestelmä**
	- paikannusdatan tallennus
	- käyttäjätietojen tallennus
	- muiden tarvittavien tietojen tallennus
	
- **Sovelluslogiikan** sisältävä ohjelmistokerros
	- Ottaa vastaan käyttöliittymäkomponentin välittämät käyttäjien hakukyselyt, logiikka-API
	- Tekee tietokannalle hakupyynnöt
	- Prosessoi tietokannalta saadusta datasta kulloisenkin hakupyynnön edellyttämän tulosteen
	- Välittää tulosteen käyttöliittymäkerrokselle

- **Käyttäjienhallintasovellus**
	- Käyttäjätietojen hallinta
	- Käyttöoikeuksien hallinta
	- Autentikointi- ja käyttäjätietojen tarjoaminen sovelluslogiikalle ja käyttöliittymälle, mikäli käytössä ei ole keskitettyä autentikointipalvelua
	
- **Käyttöliittymäkomponentti**, esim. web-sovellus
	- Sisältää mukautetut käyttöliittymät eri käyttäjäryhmille
		- Tavanomainen käyttäjä (kyselyiden teko ja tallentaminen)
		- "*Muurahaisten*" hallinnointi (tilojen käyttäjien tunnisteiden lisääminen ja poistaminen)
		- Järjestelmän ylläpitäjät (käytön seuranta, järjestelmän seuranta, paikannusjärjestelmän toiminnan valvonta ja hallinnointi)
		
		
##PAIKANNUSJÄRJESTELMÄ

Järjestelmän käytössä oletetaan, että jokaisella tiloissa oleskelevalla henkilöllä on mukanaan pieni laite, joka pystyy vastaamaan paikannustukiaseman lähettämiin kutsuihin. Paluudatana on minimissään tunnisteen ID sekä tieto luetun radiosignaalin voimakkuudesta. Käytännössä tämänkaltainen laite voisi olla passiivinen RFID-tunniste, joka on luettavissa useiden metrien etäisyydeltä, tai pienitehoinen Bluetooth Smart -laite.
Jos valitun tekniikan lukukantama jää tavoitetta lyhyemmäksi, voidaan paikannuspyyntöjen varmuutta parantaa sijoittamalla tukiasemia kulkuväylien pullonkauloihin, kuten huoneiden ja käytävien oviaukkojen luokse, oviin kulunvalvontalaitteiden yhteyteen yms. (Oletuksena etätunniste olisi niin pieni, että sen voisi kiinnittää esim. avainnippuun. Ongelmana tosin voi olla avainten aiheuttamat häiriöt radiosignaalien lukemisessa.)

Tukiasemien vastuulla on suorittaa tunnisteiden etälukuja, ja välittää saadut tiedot takaisin paikannusohjelmistolle. Tukiasemat voisivat liittyä olemassaolevaan ethernet- tai wlan-verkkoon, tai muodostaa oman koko kiinteistön kattavan mesh-verkon.

Paikannusjärjestelmän ohjelmistokerros huolehtii tukiasemaverkolta kerätyn datan suodattamisessta ja valmistelusta tallennusta varten. Viimeistään tässä vaiheessa datasta karsitaan pois henkilöt yksilöivät tiedot.

Saatu sijaintidata sovitetaan kiinteistön fyysiseen malliin (graafi huoneista ja kulkureiteistä), ja jokaiselle saadulle datapisteelle määritellään todennäköisin sijainti huonetasolla. Mikäli sama tunniste on usean eri tukiaseman kantaman sisäpuolella, todellisen sijainnin päätteleminen on tiedot kokoavan ohjelmistokerroksen vastuulla.
Mikäli joihinkin tiloihin tarvitaan tarkempaa paikannusta (esim. auditorio, ruokala tai tila jonka käytöstä halutaan tarkempaa tietoa), voidaan tilaan sijoittaa lisää lukijoita, ja vasteiden voimakkuuden perusteella päätellä tunnisteiden sijainti tilassa.

Samassa huoneessa olevien tukiasemien tiedot yhdistetään ja tietokantaan tallennetaan  jokaisesta paikannuskyselystä vain huoneessa olijoiden määrä. Tarkemmassa tarkastelussa olevat tilat voidaan jakaa pienempiin alueisiin, ja tällöin käyttäjämäärät tallennetaan aluekohtaisesti. (Esim. auditorion etu- ja takaosassa olevien lukumäärät erikseen, tai sohvilla ja työpöytien ääressä olevien määrät erikseen).

Viimeistään tässä vaiheessa, ennen tietokantatallennusta, datasta siivotaan pois yksittäiset käyttäjät yksilöivä data: etätunnisteet yksilöiviä ID-tietoja ei tallenneta. Tällöin yksittäisten käyttäjien kulun valvonta järjestelmän avulla on mahdotonta. Tiedoista kuitenkin nähdään, jos jossain huoneessa oleskelee vain yksi henkilö, mutta tietojen perusteella ei voida selvittää, minne henkilö huoneesta poistuttuaan meni. Kannattaa myös huomioida, että yksittäisten henkilöiden kulun seuraaminen on mahdollista myös ilman paikannusjärjestelmää, esimerkiksi valvontakameroiden avulla, tai väijymällä ihmisen kintereillä.

##TIETOKANTA
Tietokantajärjestelmä on melko tavanomainen datan tallennukseen ja lukuun soveltuva tietokantajärjestelmä, sisältäen ohjelmiston ja palvelinlaitteiston. Paikkatietoihin liittyviä tietoja ovat huonekohtaiset käyttäjämäärätiedot (käyttäjämäärä ja paikannuksen aika). Lisäksi voidaan tallentaa esim. tietoja tukiasemaverkon toiminnasta (normaali toiminta tai mahdolliset vikatilat, paikannuksen väliaikaiset epätarkkuudet).
Järjestelmän tietokantaan on tarpeellista tallentaa myös järjestelmän käyttäjien profiileihin liittyviä tietoja, kuten käyttäjien tallentamat omat hakuvalinnat ja haut, jne.

##SOVELLUSLOGIIKKA
Paikannusdataa käsittelevä sovelluslogiikka on järjestelmän keskeisin sovelluskomponentti. Sovelluslogiikan täytyy kyetä muodostamaan kaikki käyttäjille relevantit tietokantahaut, käsittelemään paluudatasta kulloinkin tarvitut tulosteet ja toteuttamaan eri toimintojen oheistoiminnallisuudet.
Sovelluslogiikan tehtäviin voi liittyä myös tietojen yhdistelyä eri järjestelmien välillä, mikäli järjestelmän tietoja halutaan yhdistellä vaikkapa tilanvarausjärjestelmän tai lukkarikoneen tai sähköpostijärjestelmän kanssa. (Tilan varaaja haluaa varaukselleen sopivamman kokoisen tilan aiemmin toteutuneen todellisen käyttäjämäärän mukaan, lukkarikoneeseen tarvitsee päivittää varauksen muuttunut paikka, järjestelmän tulisi lähettää kuukausittainen raportti tilojen käytöstä tilapalvelulle.)

##KÄYTTÄJIENHALLINTA
Käyttäjienhallinnan keskeisin tehtävä on tarjota sovelluksen käyttöön käyttäjien autentikointi, ja suojata käyttäjätiedot muun sovelluksen ulkopuolelle. Käyttäjällä tulisi olla järjestelmän käyttöön ainoastaan sallitut valtuudet, ja käyttöliittymäkomponentin tulee tarjota kulloisenkin käyttäjäprofiilin mukaiset näkymät.

##KÄYTTÖLIITTYMÄ
Järjestelmän pääkäyttäjärymä, "*kyylät*", sisältää useita erilaisia käyttäjäprofiileita, joilla kullakin ryhmällä on omat erityistarpeet tehtyjen hakujen esittämiseen. Olisi hankalaa toteuttaa yhtä, yhdenmukaista käyttöliittymää, joka täyttäisi optimaalisesti eri käyttäjäryhmien erilaiset tarpeet. Tästä syystä käyttöliittymä kannattaisi toteuttaa modulaarisena siten, että kullekin käyttäjäryhmälle voidaan tarjota sopiva valikoima perustyökaluja, ja että kukin käyttäjä voi edelleen muokata omaa hakunäkymäänsä yksilökohtaisten tarpeidensa mukaan, esim. lisäämällä työkalupalkkeihin omia pikavalintojaan.
Järjestelmätasolla tämä edellyttää sitä, että tietokantaan tallennetaan kunkin käyttäjän käyttöliittymään tekemät personoinnit käyttäjäkohtaisesti.
Toteutuksen täytyy olla kuitenkin sellainen, että käyttäjän ei ole mahdollista poistaa välttämättömiä elementtejä, kuten hakunappeja tai uloskirjautumisnappeja.

Käyttöliittymä on kuvattu tarkemmin omassa dokumentissaan.