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




## b) Moottorix


## c) Automoottorix


# Lähteet
https://terokarvinen.com/apache-ansible/

https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html
