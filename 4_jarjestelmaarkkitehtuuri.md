##  Järjestelmäarkkitehtuuri

* Pyri kuvailemaan tässä luvussa järjestelmäarkkitehtuuri yleisellä tasolla
* Mitä komponentteja järjestelmään tarvitaan jotta se pystyy palvelemaan määritettyjä käyttötapauksia?

Järjestelmän pääkomponentteja ovat:

- Paikannusjärjestelmä
	- Fyysinen paikannuslaite
	- Paikannuslaitetta kutsuvat paikannusverkon tukiasemat
	- Ohjelmistokerros, jonka vastuulla on
		- Paikannusdatan kyselypyynnöt käyttäjien laitteille
		- Saapuvan paikannusdatan käsittely (virhedatan siivoaminen, kelvollisen datan sovittaminen pohjapiirrosmalliin)