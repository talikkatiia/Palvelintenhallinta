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

Aloitin luomalla uuden käyttäjän ansiblea varten komennolla: sudo adduser ansible. Laitoin sille uuden salasanan ja muuten painoin vain enteriä. Tämän jälkeen lisäsin ansible käyttäjän sudoless ryhmään.

<img width="530" height="285" alt="image" src="https://github.com/user-attachments/assets/61db7d2f-eef5-4c72-aae0-19af329934df" />

Loin sudoless oikeudet: sudo visudo /etc/sudoers.d/sudoless ja sinne kirjoitin %sudoless ALL = (ALL) NOPASSWD: ALL
Komennolla: ssh ansible@localhost siirryin ansible käyttäjälle ja suoritin komennon: sudo -k, tämä pakottaa sudon unohtamaan aikaisemman salasanatunnistuksen. Sen jälkeen komento: sudo echo "moikka moi" ja se tulosti kirjoittamani tekstin ilman salasanaa. Kopioin myös jo olemassa olevan avaimen komennolla: ssh-copy-id ansible@localhost. Otin yhteyttä komennolla: ssh ansible@localhost ja pääsin ilman salasanaa.

<img width="436" height="80" alt="image" src="https://github.com/user-attachments/assets/aace9eea-8c34-48db-bef3-639ce396fa9b" />

## b) Antero

Luodaan tiedosto ja kansiot roles/antero/tasks/main.yml

<img width="732" height="337" alt="image" src="https://github.com/user-attachments/assets/47400620-e8aa-4214-993d-6690006f8a50" />

Lisätään site.yml tiedostoon become: true ja rooli

<img width="225" height="132" alt="image" src="https://github.com/user-attachments/assets/039fafd3-4610-4330-90d7-6d75673211e2" />

## c) Package

Tein paketit.yml tiedoston jonne kirjoitin: 

<img width="416" height="236" alt="image" src="https://github.com/user-attachments/assets/0da35abb-a097-4f66-9dbd-f39b050af91a" />

Tämän jälkeen suoritin komennon: ansible-playbook paketit.yml -K

<img width="822" height="307" alt="image" src="https://github.com/user-attachments/assets/c27bae06-ef5d-4481-adcd-a075e3bc4727" />

## d) File

Tein tiedoston, jonne annoin oikeudeksi 0644. Ensimmäinen 0 normaali tiedosto, 6 omistajan oikeudet eli r + w (4+2), 4 ryhmän oikeudet pelkkä r (4) ja 0 muiden oikeudet eli ei mitään.

<img width="425" height="262" alt="image" src="https://github.com/user-attachments/assets/b0772d32-8f5f-48fa-987d-995d6b42225c" />

<img width="812" height="322" alt="image" src="https://github.com/user-attachments/assets/bfa87033-8977-47e9-bac3-62b7eca178e4" />





## e) Jotain muuta 


## Lähteet
Karvinen, T. 2026. Sudo without password. Luettavissa: https://terokarvinen.com/passwordless-sudo/ (Luettu: 6.11.2026)

Munroe. 2026. xkcd 149: Sandwitch. Luettavissa: https://xkcd.com/149/ (Luettu: 6.11.2026)

Karvinen, T. 2026. Passwordless Sudo with Ansible. Luettavissa: https://terokarvinen.com/passwordless-sudo-with-ansible/ (Luettu: 6.11.2026)
