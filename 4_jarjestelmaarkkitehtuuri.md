##  Järjestelmäarkkitehtuuri

* Pyri kuvailemaan tässä luvussa järjestelmäarkkitehtuuri yleisellä tasolla
* Mitä komponentteja järjestelmään tarvitaan jotta se pystyy palvelemaan määritettyjä käyttötapauksia?

Järjestelmän pääkomponentteja ovat:

- Paikannusjärjestelmä
	- Fyysinen paikannuslaite, pitkän kantaman etäluettava RFID-tunniste
	- Paikannusverkon tukiasemat, jotka tekevät kutsuja kantamansa sisällä oleville tunnisteille
	- Ohjelmistokerros, jonka vastuulla on
		- Lähettää ajoitetut paikannuskyselypyynnöt tukiasemille
		- tukiasemilta saapuvan paikannusdatan käsittely (virhedatan siivoaminen, kelvollisen datan sovittaminen pohjapiirrosmalliin)
		
- Tietokantajärjestelmä
	- paikannusdatan tallennus
	- käyttäjätietojen tallennus
	- muiden tarvittavien tietojen tallennus

- Sovelluslogiikan sisältävä ohjelmistokerros
	- Ottaa vastaan käyttäjien hakukyselyt, logiikka-API
	- Tekee tietokannalle hakupyynnöt
	- Prosessoi saadusta datasta kulloisenkin hakupyynnön edellyttämän tulosteen
	- Välittää tulosteen käyttöliittymäkerrokselle

- Käyttäjähallintasovellus
	- Käyttäjätietojen hallinta
	- Käyttöoikeuksien hallinta
	- Autentikointi- ja käyttäjätietojen tarjoaminen sovelluslogiikalle ja käyttöliittymälle
	
- Käyttöliittymäkerros, esim. web-sovellus
	- Sisältää mukautetut käyttöliittymät eri käyttäjäryhmille
		- Tavanomainen käyttäjä (kyselyiden teko)
		- Käyttäjäjien hallinnointi (käyttäjien lisääminen ja poistaminen
		- Järjestelmän ylläpitäjät (käytön seuranta, järjestelmän seuranta)
		
		
##PAIKANNUSJÄRJESTELMÄ

Järjestelmän käytössä oletetaan, että jokaisella tiloissa oleskelevalla henkilöllä on mukanaan pieni laite, joka pystyy vastaamaan paikannustukiaseman lähettämiin kutsuihin. Käytännössä tämänkaltainen laite voisi olla pieni, passiivinen RFID-tunniste, joka on luettavissa useiden metrien etäisyydeltä. Jos lukukantama jää tavoitetta lyhyemmäksi, voidaan paikannuspyyntöjen varmuutta parantaa sijoittamalla tukiasemia kulkuväylien pullonkauloihin, kuten huoneiden ja käytävien oviaukkojen luokse, kulunvalvontalaitteiden yhteyteen yms.