# h2 Voileipä 

## x) Lue ja tiivistä
Karvinen 2026: Sudo without password:
- Ansible tarvitsee pääkäyttäjän (root) oikeudet hallittavalla koneella
- Artikkelissa luodaan käyttäjäryhmä sudoless, jolle annetaan oikeus käyttää sudoa ilman salasanaa.
- visudo-komennolla voidaan muokata sudo-asetuksia ja tarkistaa niiden oikeellisuus.
- **Oma huomio**: Salasanaton sudo helpottaa Ansiblen käyttöä, koska salasanaa ei tarvitse kirjoittaa joka kerta.

Munroe 2006: xkcd 149: Sandwitch:
- Henkilö pyytää toista muuttamaan hänet voileiväksi -> toinen kyseenalaistaa.
- Henkilö lisää alkuun sudo -> toinen ei kysele enään vaan suorittaa.
- Eli sudo avulla voidaan ajaa mitä vain.

Karvinen 2026: Passwordless Sudo with Ansible:
- Artikkelin tarkoituksena on automatisoida salasanattoman sudon käyttöönotto, tämän mahdollistaa SSH avain. 
- Määritykset laitetaan hakemistopolkuun roles/antero/tasks/main.yml -> tekstitiedostoon tulee määritykset -> site.yml tiedostoon lisäys become: true.
- Tärkeää on oikeuksien määrittäminen / ymmärtäminen mitä ne tekee, jotta ei anna vääriä oikeuksia.

Ansiblen sisäänrakennettu dokumentaatio ansible-doc -kommennolla
**Module:** 
- Apt-moduulia käytetään ohjelmien asentamiseen, poistamiseen ja hallintaan Debian- ja Ubuntu-pohjaisissa Linux-järjestelmissä.
 
**Optio:**
- name -> ohjelman nimi, jota käsitellään
- state -> määrittää ohjelmistopaketin halutun tilan
- update_cache -> päivittää ohjelmistopakettien listauksen
 
**Examples:**
- name: Install apache httpd
   ansible.builtin.apt:
     name: apache2
     state: present


## a) Sudoless


## b) Antero


## c) Package


## d) File


## e) Jotain muuta 


## Lähteet
Karvinen, T. 2026. Sudo without password. Luettavissa: https://terokarvinen.com/passwordless-sudo/ (Luettu: 6.11.2026)

Munroe. 2026. xkcd 149: Sandwitch. Luettavissa: https://xkcd.com/149/ (Luettu: 6.11.2026)

Karvinen, T. 2026. Passwordless Sudo with Ansible. Luettavissa: https://terokarvinen.com/passwordless-sudo-with-ansible/ (Luettu: 6.11.2026)
