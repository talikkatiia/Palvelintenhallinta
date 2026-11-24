# h4 Pizza Fantasia
## x) Lue ja tiivistä

Karvinen 2023
4.12.1 Size and Complexity of Some DSLs:
- DSL kielet voivat kasvaa suuriksi ja monimutkaisiksi.
- Salt:issa on 510 toimintoa, joiden avulla järjestelmänvalvoja voi hallita tietokoneiden asetuksia. Dokumentaatiossa on yli 20 000 riviä ja 75 000 sanaa.
- Puppet:issa on 113 valmista toimintoa

4.12.2 Use of DSL Functions in Case Configuration:
- Vaikka Salt ja Puppet sisältää paljon toimintoja käytännön määrityksissä tarvitaan yleensa vain pientä osaa niistä.
- Tutkimuksessa tarkasteltiin kahta Puppet konfiguraatiota. Yhdysvaltain valtionhallinnon määrityksiä ja Mozillan julkaisuympäristön määrityksiä.
- Yleisimmin käytettyjä toimintoja olivat file, package, service ja exec.

4.12.3.1 Dependencies Between Main Functions:
- Järjestelmän tulee olla idempotentti, eli muutoksia tehdään vain silloin, kun järjestelmän asetukset eivät ole halutussa tilassa. Turhia muutoksia ei tehdä, jos kaikki on jo oikein.
- Monet toiminnot perustuvat kahteen perustoimintoon exec (ohjelmien suorittaminen) ja file (tiedostojen luominen ja hallinta).

## a) Räpylä

Aluksi päivitin, jonka jälkeen asennetaan Redis. 
````
sudo apt update
````
````
sudo apt install redis-server
````
Tämän jälkeen käynnistin sen ja asetin sen käynnistymään automaattisesti tietokoneen käynnistyessä.
````
sudo systemctl start redis-server
````
````
sudo systemctl enable redis-server
````
Testasin, että Redis toimii `redis-cli ping` ja vastaukseksi tuli PONG. Eli se on käynnissä ja toimiva.

<img width="387" height="42" alt="image" src="https://github.com/user-attachments/assets/609d9e78-b633-4be3-a4c3-37a73f933399" />

## b) Automaatti


## c) Asetus


## d) Paikka remonttiin


## e) Idempotentti


## Lähteet

Karvinen, T. 2023. Väitöskirja. Configuration Management of Distributed Systems over Unreliable and Hostile Networks. University of Westminster
