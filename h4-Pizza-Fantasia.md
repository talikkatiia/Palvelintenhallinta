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


## b) Automaatti


## c) Asetus


## d) Paikka remonttiin


## e) Idempotentti


## Lähteet

Karvinen, T. 2023. Väitöskirja. Configuration Management of Distributed Systems over Unreliable and Hostile Networks. University of Westminster
