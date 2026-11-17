# h3 Demoni
## x) Lue ja tiivistä
Karvinen 2026: Apache installed with Ansible - quick notes:
- Apache2 on verkkopalvelin, joka voidaan asentaa automaattisesti Ansiblen avulla.
- Verkkosivun sisältöä voidaan muokata tavallisena käyttäjänä ilman pääkäyttäjän oikeuksia.
- Apache2-palvelimen avulla voidaan julkaista verkkosivu, joka näkyy osoitteessa http://localhost
 
Ansible Community Documentation: Handlers: running operations on change:
- Tehtävät voivat ilmoittaa yhdelle tai useammalle handlerille, että niiden pitää suorittaa toiminto. Tähän käytetään notify sanaa.
- Handlerit suoritetaan siinä järjestyksessä, jossa ne on määritelty handlers-osiossa. Eikä siinä järjestyksessä, jossa ne on lueteltu notify-kohdassa.
- Vaikka useampi tehtävä kutsuisi samaa handleria, handeri suoritetaan vain kerran.

'ansible-doc service':
- MODULE: Service-moduulilla voidaan hallita Linuxin palveluita Ansiblen avulla, esimerkiksi käynnistää tai pysäyttää palveluita.
- enabled: Määrittää, käynnistyykö palvelu automaattisesti tietokoneen käynnistyessä.
- name: Määrittää sen palvelun nimen, jota halutaan hallita.
- state: Määrittää palvelun tilan. Esimerkiksi started käynnistää palvelun, stopped pysäyttää sen ja restarted käynnistää sen uudelleen.

## y) Infra-uutiset



## a) Apassi

Aloitin päivittämällä kaiken ja asentamalla apache2.
````
sudo apt-get update
sudo apt-get upgrade
sudo apt install apache2
````
Testasin komennolla `systemctl status apache2`, että apache toimii. Jonka jälkeen testasin http://localhost, että sivu näkyy.

<img width="656" height="72" alt="image" src="https://github.com/user-attachments/assets/0772fce4-f94a-4650-9aaf-8cf79b3f5f5f" />

<img width="668" height="252" alt="image" src="https://github.com/user-attachments/assets/94c9784b-a66c-4586-9b14-288866e4eaa7" />

Loin uuden kansion `mkdir publicsite` ja sinne tiedoston `nano publicsite/index.html` 

<img width="296" height="138" alt="image" src="https://github.com/user-attachments/assets/608015fb-7f2d-4f59-a914-7bb323b999ed" />

Sitten annoin oikeudet

<img width="440" height="70" alt="image" src="https://github.com/user-attachments/assets/a1401591-955d-4647-ae49-621c26558254" />

Muutin apachen konfiguraatiota.

<img width="392" height="158" alt="image" src="https://github.com/user-attachments/assets/028427a3-6799-4a64-bf01-101f115077e4" />

Sitten otin oman sivuni käyttöön `sudo a2ensite publicsite.conf`. Otin apachen oletussivun pois käytöstä `sudo a2dissite 000-default.conf`. Tarkistin apachen asetukset `sudo apache2ctl configtest` ja tuli Syntax OK. Tämän jälkeen Päivitin apachen `sudo systemctl reload apache2` ja sivu tuli näkyviin.

<img width="610" height="214" alt="image" src="https://github.com/user-attachments/assets/f968483e-50b7-460a-99ec-08ca89114266" />

<img width="368" height="105" alt="image" src="https://github.com/user-attachments/assets/b46131b6-ae7f-44c3-ae84-e09924fbe846" />

Lopuksi kirjauduin toiselle käyttäjällä ssh ansible@localhost ja kävin tiedostossa `nano /home/tiia/ansible/publicsite/index.html` muokkasin sitä ja se onnistui.

<img width="562" height="98" alt="image" src="https://github.com/user-attachments/assets/f8bf3742-50e2-4052-9561-3f6ab995bd6a" />

## b) Moottorix

Asensin Nginxin `sudo apt install nginx`. Tämän jälkeen sammutin apachen `sudo systemctl stop apache2`. Katsoin apachen tilan `sudo systemctl status apache2`. Käynnistin myös nginxin `sudo systemctl start nignx` ja katsoin sen tilan samalla tavalla.

<img width="606" height="94" alt="image" src="https://github.com/user-attachments/assets/b644fce6-2976-4303-a00f-87984ac63cde" />

<img width="626" height="72" alt="image" src="https://github.com/user-attachments/assets/d0d095da-f04f-41d7-b023-e66e2d0aee9e" />

Muutin nginxin konfiguraatiota `sudo nano /etc/nginx/sites-available/default`

<img width="310" height="34" alt="image" src="https://github.com/user-attachments/assets/fd901718-50d7-4914-bd78-f4455b30bdd4" />

Käynnistin nginxin uudelleen `sudo systemctl restart nginx` avasin http://localhost ja sivu näkyi taas

<img width="576" height="98" alt="image" src="https://github.com/user-attachments/assets/ef569f15-cbc7-4879-b887-6cfadeddae34" />

Sekä edelleen pystyin muokkaamaan sitä toisella käyttäjällä.

<img width="322" height="85" alt="image" src="https://github.com/user-attachments/assets/57cd7dd0-89e4-4704-9c84-140dc96d2d0e" />

## c) Automoottorix

Ensiksi loin kansiot

<img width="422" height="50" alt="image" src="https://github.com/user-attachments/assets/7c325001-5660-4003-ab86-4be08656f992" />

files/default konfigurointi tiedosto

<img width="366" height="210" alt="image" src="https://github.com/user-attachments/assets/aa4e573d-057c-4066-8a80-289c3a4862d8" />

Sitten `nano roles/nginx/tasks/main.yml`

<img width="378" height="222" alt="image" src="https://github.com/user-attachments/assets/83c0c825-e462-4fed-9adc-7c93a791c83f" />






# Lähteet
https://terokarvinen.com/apache-ansible/

https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html
