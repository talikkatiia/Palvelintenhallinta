# h1 Hei Ansiblen maailma

## x) Lue ja tiivistä
Karvinen 2026: SSH public key - Login without password:
- SSH on yleinen ja turvallinen tapa kirjautua palvelimelle.
- Git, rsync ja Ansible käyttävät SSH:ta taustalla.
- Julkinen avain on kätevä tapa kirjautumiseen, koska ei tarvitse kirjoittaa salasanaa.
- Voi parantaa tietoturvaa.
- Olemassa olevaa avainparia ei saa korvata uudella.
- Samaa julkista avainta voi käyttää kaikilla palvelimilla.

Karvinen 2026: Hello Ansible:
- Ansible on asetustenhallintatyökalu.
- Ansible tekee muutoksia vain silloin, kun niitä tarvitaan.
- Ansible toimii SSH:n kautta.
- Hallittavalla koneella ei tarvitse olla erillistä Ansible-taustaohjelmaa, koska Ansiblea kutsutaan agentittomaksi.
- Hallittavalla koneella pitää olla SSH-palvelu ja Python.

## a) Paikallista
Asensin Debian 13 h0 tehtävässä: https://github.com/talikkatiia/Palvelintenhallinta/blob/main/h0-Oikeasti-netiss%C3%A4.md
- RAM muisti 2048Mt
- CPU 2
- Virtuaalilevy 25Gt
- Kieliasetukset englanti
- Lokaation Suomi
- Näppäimistön suomi
- Hostname debian13
- Username tiia
  
## b) Sshecrets
Ensiksi päivitin järjestelmän, jotta se on valmis komennolla: sudo apt-get update. Latauksen tein komennolla: sudo apt-get install -y ssh. SSH yhteyden käynnistyminen aina boottauksen yhteydessä ajoin komennon: sudo systemctl enable --now ssh. Lopuksi testasin yhteyden komennolla: ssh tiia@localhost.

<img width="811" height="236" alt="image" src="https://github.com/user-attachments/assets/1330af43-8c90-4e74-b219-1767df7edff9" />

## c) Pubkey
Julkisen avaimen asensin komennolla: ssh keygen sen jälkeen kopioin sen omalla palvelimelleni komennolla: ssh-copy-id tiia@localhost. Testasin vielä kirjautumisen SSH avulla ja pääsin sisälle.

## d) Hei Ansible
Aloitin taas suorittamalla päivitykset komennolla: sudo apt-get update. Asensin Ansiblen, micro-tekstieditorin, bash-completionin ja treen komennolla: sudo apt-get install ansible micro bash-completion tree. Sittne loin Ansiblelle kansion ja sinne tekstitiedoston hosts.ini. Ajoin komennon: ansible all -a 'uptime' -i hosts.ini, jotta tietän, että Ansible käyttää SSH:ta. Ensimmäisellä kerralla tuli varoitus, poistin sen lisäämällä hosts.ini tiedostoon: [all:vars] ansible_python_interpreter=/usr/bin/python3

<img width="797" height="302" alt="image" src="https://github.com/user-attachments/assets/3568f598-4d5a-4351-986e-05ea88e21c7c" />

Tämän jälkeen loin rooleille kansion komennolla: mkdir -p roles/hello/tasks ja sinne loin main.yml tiedoston komennolla: micro roles/hello/tasks/main.yml. Tiedostoon kirjoitin: - copy: dest: /tmp/hello-ansible content: "Hei maailma\n". Loin rooleille site.yml tiedoston kommennolla: micro site.yml, sinne kirjoitin - hosts: all roles: - hello. Testasin, että toimii myös ssh:n yli komennolla: ssh localhost ’cat /tmp/hello-ansible.

<img width="677" height="90" alt="image" src="https://github.com/user-attachments/assets/91ffb0c6-6c3c-4141-851d-883f6f685f0c" />

Lisäsin hosts.ini-tiedoston ansible.cfg-asetustiedostoon. Lopuksi ajoin komennon: ansible-playbook site.yml, joka tulosti hyväksytyn tuloksen.

<img width="812" height="285" alt="image" src="https://github.com/user-attachments/assets/f145acb0-67cd-4365-8cd0-1e461a728aeb" />

## Lähteet
Karvinen 2026: SSH public key - Login without password
Karvinen 2026: Hello Ansible
