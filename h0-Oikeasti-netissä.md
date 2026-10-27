# h0 Oikeasti netissä

## x) 
Niemi 2025: H4 Tehtävät
Artikkeli: Teoriasta käytäntöön pilvipalvelimen avulla:
- Susanna Lehdon artikkelissa käsitellään virtuaalipalvelimen käyttöönottoa ja suojaamista palomuurilla.
- Palvelimen lokitiedoista nädään, jos ulkopuoliset ovat yrittäneet ottaa siihen yhteyttä. Artikkelissa selviää, että Kiinasta yritettiin ottaa yhteys.
- **Oma huomio:** Artikkeli osoittaa, että julkiseen verkkoon liitetty palvelin voi joutua tuntemattomien yhteydenottoyritysten kohteeksi. Siksi palvelimen suojaaminen on todella tärkeää heti käyttöönoton yhteydessä.

Artikkeli: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS:
- Artikkelissa käydään läpi lyhyesti, kuinka uusi virtuaalipalvelin configuroidaan
- Tulimuurin reiän teko komento: $ sudo ufw allow 22/tcp, $ sudo ufw enable
- Näytetään miten lisätään uusi käyttäjä sudo oikeuksilla.
- **Oma kysymys:** Miten palvelimen tietoturvaa voitaisiin parantaa vielä lisää palomuurin ja kättäjätilien asetusten lisäksi?

Partanen 2025: Harjoitus 5: Nimekäs: a) Nimi 
- Tehtävässä hankitaan julkinen verkkotunnus eli domain-nimi Namecheap-palveluntarjoajalta. Domain valinnassa otetaan nimi, joka on edulliseen hintaan.
- Domain-nimi yhdistetään virtuaalipalvelimeen Namecheapin DNS-asetusten avulla.
- Host kohdassa www tarkoittaa www.aleksipartanen.space osoitetta.
- @ host tarkoittaa pelkästään domain osoitetta eli aleksipartanen.space.
- **Oma huomio:** Opin, että verkkosivun julkaisemiseen tarvitaan palvelimen lisäksi domain-nimi. Sekä oikein määritetyt DNS-asetukset. Domain-nimi helpottaa sivustolle pääsyä/löytämistä, koska käyttäjän ei tarvitse muistaa palvelimen IP-osoitetta.

## a)


## b)
Vuokrasin virtuaalisen yksityispalvelimen UpCloud-palveluntarjoajalta. Ensin valitsin serverin sijainnniksi Suomen. Tällöin Suomesta yhteydenottaminen on nopeampaa.
<img width="1504" height="1114" alt="image" src="https://github.com/user-attachments/assets/458cd86c-1376-4363-93f8-eff27399ee50" />
Seuraavaksi valitsin halvimman vaihtoehdon (prosessori, RAM-muisti ja muisti)
<img width="1504" height="522" alt="image" src="https://github.com/user-attachments/assets/e394ce20-1ad7-4a4b-bee1-3499bd5b1aa9" />
Storage ja automated backups kohdat skippasin. Operating system kohdassa valitsin Debian GNU/Linux 13 (Trixie), koska sitä suositeltiin tunnilla.
<img width="1504" height="448" alt="image" src="https://github.com/user-attachments/assets/43477adb-abe7-47c8-8db6-66051ef4a27a" />
Network kohdan myös skippasin. Login method valitsin SSH keys. Tein koululla tämän, joten en muista komentoa miten löysin avaimen. Kun olin löytänyt otin yhteyttä palvelimeen onnistuneesti.

## c)
Aloitin tekemällä virtuaalipalvelimelleni sudo-käyttäjän omalla nimellä. Ensin lisäsin käyttäjän adduser tiia ja sen jälkeen annoin sudo oikeudet adduser tiia sudo
<img width="676" height="345" alt="image" src="https://github.com/user-attachments/assets/dfb8d208-6fc2-41ce-ad96-eb54c96414fd" />
Tämän jälkeen asensin tulimuurin 




## Lähteet
Niemi 2025: H4 Tehtävät 
