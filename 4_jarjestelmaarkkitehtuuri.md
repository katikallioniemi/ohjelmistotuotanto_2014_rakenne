##  Järjestelmäarkkitehtuuri

* Pyri kuvailemaan tässä luvussa järjestelmäarkkitehtuuri yleisellä tasolla
* Mitä komponentteja järjestelmään tarvitaan jotta se pystyy palvelemaan määritettyjä käyttötapauksia?

Järjestelmän pääkomponentteja ovat:

- Paikannusjärjestelmä
	- **Fyysinen paikannuslaite**, pitkän kantaman etäluettava RFID-tunniste
	- **Paikannusverkon tukiasemat**, jotka tekevät kutsuja kantamansa sisällä oleville tunnisteille
	- **Ohjelmistokerros**, jonka vastuulla on
		- Lähettää ajoitetut paikannuskyselypyynnöt tukiasemille
		- tukiasemilta saapuvan paikannusdatan käsittely (virhedatan siivoaminen, kelvollisen datan sovittaminen pohjapiirrosmalliin)
		
- **Tietokantajärjestelmä**
	- paikannusdatan tallennus
	- käyttäjätietojen tallennus
	- muiden tarvittavien tietojen tallennus
	
- **Sovelluslogiikan** sisältävä **ohjelmistokerros**
	- Ottaa vastaan käyttäjien hakukyselyt, logiikka-API
	- Tekee tietokannalle hakupyynnöt
	- Prosessoi saadusta datasta kulloisenkin hakupyynnön edellyttämän tulosteen
	- Välittää tulosteen käyttöliittymäkerrokselle

- **Käyttäjienhallintasovellus**
	- Käyttäjätietojen hallinta
	- Käyttöoikeuksien hallinta
	- Autentikointi- ja käyttäjätietojen tarjoaminen sovelluslogiikalle ja käyttöliittymälle
	
- **Käyttöliittymäkomponentti**, esim. web-sovellus
	- Sisältää mukautetut käyttöliittymät eri käyttäjäryhmille
		- Tavanomainen käyttäjä (kyselyiden teko)
		- Käyttäjäjien hallinnointi (käyttäjien lisääminen ja poistaminen)
		- Järjestelmän ylläpitäjät (käytön seuranta, järjestelmän seuranta)
		
		
##PAIKANNUSJÄRJESTELMÄ

Järjestelmän käytössä oletetaan, että jokaisella tiloissa oleskelevalla henkilöllä on mukanaan pieni laite, joka pystyy vastaamaan paikannustukiaseman lähettämiin kutsuihin. Paluudatana on minimissään Käytännössä tämänkaltainen laite voisi olla passiivinen RFID-tunniste, joka on luettavissa useiden metrien etäisyydeltä. Jos lukukantama jää tavoitetta lyhyemmäksi, voidaan paikannuspyyntöjen varmuutta parantaa sijoittamalla tukiasemia kulkuväylien pullonkauloihin, kuten huoneiden ja käytävien oviaukkojen luokse, kulunvalvontalaitteiden yhteyteen yms.

Tukiasemien vastuulla on suorittaa tunnisteiden etälukuja, ja välittää saadut tiedot takaisin paikannusohjelmistolle. Tukiasemat voisivat liittyä olemassaolevaan wlan-verkkoon tai muodostaa oman mesh-verkon.

Paikannusjärjestelmän ohjelmistokerros huolehtii tukiasemaverkolta kerätyn datan suodattamisessta ja valmistelusta tallennusta varten. Viimeistään tässä vaiheessa datasta karsitaan pois henkilöt yksilöivät tiedot. Saatu sijaintidata sovitetaan kiinteistön fyysiseen malliin (graafi huoneista ja kulkureiteistä), ja jokaiselle saadulle datapisteelle määritellään todennäköisin sijainti huonetasolla. Mikäli sama tunniste on usean eri tukiaseman kantaman sisäpuolella, todellisen sijainnin päätteleminen on tiedot kokoavan ohjelmistokerroksen vastuulla. Mikäli tukiasemilta saadaan paluutietona myös lukuvasteen voimakkuus, voidaan paikannuksen tarkkuutta parantaa.
Mikäli joihinkin tiloihin tarvitaan tarkempaa paikannusta, voidaan tilaan sijoittaa vähintään kolme lukijaa, ja vasteiden voimakkuuden perusteella päätellä tunnisteiden sijainti huoneessa.

Perustapauksissa tietokantaan tallennetaan jokaisesta paikannuskyselystä huonekohtaisesti huoneessa olijoiden määrä. Tarkemmassa tarkastelussa olevat tilat voidaan jakaa pienempiin alueisiin. Tällöin käyttäjämäärät tallennetaan aluekohtaisesti. (Esim. auditorion etu- ja takaosassa olevien lukumäärät erikseen).

Viimeistään tässä vaiheessa, ennen tietokantatallennusta, datasta siivotaan pois yksittäiset käyttäjät yksilöivä data: etätunnisteet yksilöiviä ID-tietoja ei tallenneta. Tällöin yksittäisten käyttäjien kulun valvonta järjestelmän avulla on mahdotonta.

##TIETOKANTA
Tietokantajärjestelmä on melko tavanomainen datan tallennukseen ja lukuun soveltuva järjestelmä. Paikkatietoihin liittyviä tietoja ovat huonekohtaiset käyttäjämäärätiedot (käyttäjämäärä ja paikannuksen aika), tiedot tukiaseman toiminnasta (normaali toiminta tai vikatilat).
Lisäksi tietokantaan on tarpeellista tallentaa järjestelmän käyttäjien profiileihin liittyviä tietoja, kuten henkilökohtaisesti tallennetut hakuvalinnat ja haut, jne.

##SOVELLUSLOGIIKKA
Paikannusdataa käsittelevä sovelluslogiikka on järjestelmän keskeisin sovelluskomponentti. Sovelluslogiikan täytyy kyetä muodostamaan kaikki käyttäjille relevantit tietokantahaut, käsittelemään paluudatasta kulloinkin tarvitut tulosteet ja toteuttamaan eri toimintojen oheistoiminnallisuudet.
Sovelluslogiikan tehtäviin voi liittyä myös tietojen yhdistelyä eri järjestelmien välillä, mikäli järjestelmän tietoja halutaan yhdistellä vaikkapa tilanvarausjärjestelmän tai lukkarikoneen tai sähköpostijärjestelmän kanssa. (Tilan varaaja haluaa varaukselleen sopivamman kokoisen tilan aiemmin toteutuneen todellisen käyttäjämäärän mukaan, lukkarikoneeseen tarvitsee päivittää varauksen muuttunut paikka, järjestelmän tulisi lähettää kuukausittainen raportti tilojen käytöstä tilapalvelulle.)

##KÄYTTÄJIENHALLINTA
Käyttäjienhallinnan keskeisin tehtävä on tarjota sovelluksen käyttöön käyttäjien autentikointi, ja suojata käyttäjätiedot muun sovelluksen ulkopuolelle. Käyttäjällä tulisi olla järjestelmän käyttöön ainoastaan sallitut valtuudet, ja käyttöliittymäkomponentin tulee tarjota kulloisenkin käyttäjäprofiilin mukaiset näkymät.

##KÄYTTÖLIITTYMÄ
