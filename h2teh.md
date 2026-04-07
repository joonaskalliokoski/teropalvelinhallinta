# h2
x) 

Karvinen 2026: Sudo without password
    
  -- Tärkeintä on lisätä tiedostoon /etc/sudoers.d/sudoless:
  <pre>%sudoless ALL = (ALL) NOPASSWD: ALL</pre>
  -- sudo adduser -> sudo groupadd -> sudo adduser *user* *group*.

  Munroe 2006: xkcd 149: Sandwitch

  -- Internet huumoria.

  Karvinen 2026: Passwordless Sudo with Ansible

  -- main.yml tärkein tiedosto. Suurin osa koodista sijoittuu sinne. 

  -- sites.yml:n pitää myös tehdä lisäyksiä.

  -- SSH-avain pitää generoida erikseen.

Ansible sisäänrakennettu dokumentaatio

-- Hyvin kätevä mielestäni

-- Samat tiedot löytää internetistä


a)

Luodaan ensin oma kansio ja main.yml uudelle roolille nimeltään lumiukko.

<img width="355" height="280" alt="image" src="https://github.com/user-attachments/assets/477d70a1-70bf-49b3-a639-5c837d95e4d8" />

Seuravaaksi kirjoitin lumiukko käyttäjän main.yml:n nämä komennot:

<img width="950" height="327" alt="image" src="https://github.com/user-attachments/assets/8587d212-6f08-4de0-af22-69cc204fe96e" />

Lisäsin myös lumiukko site.yml:n "become: true":n lisäksi

<img width="235" height="142" alt="image" src="https://github.com/user-attachments/assets/b4013938-5a91-4ef1-91da-0c9acdf67d34" />

Sen jälkeen ajoin site.yml:n ansible-playbook komenolla 

<img width="1161" height="550" alt="image" src="https://github.com/user-attachments/assets/e68948c6-4a48-4781-928f-ffb14ac05f2a" />

Seuraavaksi testataan toimiiko käyttäjä niin, että ssh ja sudo toimii automaattisesti

<img width="941" height="254" alt="image" src="https://github.com/user-attachments/assets/890aaa48-e171-456f-b190-610ce7d03d00" />

ssh yhdisti ilman, että kysyisi salasanaa

sudo ei kysynyt salasanaa. Sanoisin, että testaus onnistui

b)

Sama kuin tehtävässä a) loin käyttäjälle antero oman ansible rooli kansion ja main.yml:n

<img width="517" height="279" alt="image" src="https://github.com/user-attachments/assets/93474740-c41e-4989-a38a-0fbcb77ea48e" />

Seuraavaksi menin antero käyttäjän main.yml:n automatisoimaan ssh:n

<img width="1146" height="166" alt="image" src="https://github.com/user-attachments/assets/4d9228b0-1843-4801-8ea3-9df1211c618b" />

Ja lisäsin site.yml:n anteron

<img width="211" height="147" alt="image" src="https://github.com/user-attachments/assets/c9e9d59a-7f36-4df9-bbcd-2a84c6fc4f96" />

Ajoin sen jäkeen site.yml:n

<img width="1190" height="568" alt="image" src="https://github.com/user-attachments/assets/a3934e5f-1075-4d2d-8500-1282edb09550" />

Testataan toimiiko ssh ilman salasanaa.

<img width="1003" height="194" alt="image" src="https://github.com/user-attachments/assets/007405fc-3720-4934-9a11-c6e625cde9a5" />

Yhdistäminen onnistui ilman salasanaa.

c)

Käytän käyttäjää lumiukko tässä tehtävässä eli meen käyttäjän lumiukko main.yml tiedostoon

<img width="288" height="123" alt="image" src="https://github.com/user-attachments/assets/2c2ff148-0779-4273-a631-816790115596" />

ajatetaan site.yml

<img width="1039" height="141" alt="image" src="https://github.com/user-attachments/assets/155e5f90-5077-4e7b-ba4c-3235c8981ff2" />

Hups, veikkaan syntax virhe. Korjaan koodin ja ajan tiedoston uudellen

<img width="260" height="117" alt="image" src="https://github.com/user-attachments/assets/806eebc7-7667-4566-905e-2fa07fb13d5c" />

Vaihdetaan paketti.

<img width="1165" height="259" alt="image" src="https://github.com/user-attachments/assets/69b2b606-d318-447d-a31a-87566ea8b095" />

Ajaminen onnistui

<img width="997" height="46" alt="image" src="https://github.com/user-attachments/assets/e80a9371-ce8a-43c2-839c-57db6962bfde" />

Testataan

<img width="206" height="38" alt="image" src="https://github.com/user-attachments/assets/b8c5d422-64fb-48b2-b533-78d8c44983fc" />

htop

<img width="1200" height="570" alt="image" src="https://github.com/user-attachments/assets/63f4322c-9229-4b71-81ac-2b0587a4bbf9" />

d)

Käytän käyttäjää antero tässä tehtävässä. 

<img width="246" height="74" alt="image" src="https://github.com/user-attachments/assets/e5793f64-9e2b-4f3e-bbf7-4dfc08fd5ff6" />

Ajan site.yml:n

<img width="1210" height="115" alt="image" src="https://github.com/user-attachments/assets/03e0c250-c7ce-4f30-821a-7e7fbb2267e0" />

Testataan löytyykö tiedosto ja se löytyy 

<img width="549" height="135" alt="image" src="https://github.com/user-attachments/assets/e08901e6-ff72-45ff-b4cf-684771c37a7d" />

-rwxr--r-- selitys.
(-)rwxr--r-- suluissa oleva tarkoittaa minkälainen erikoisoikeuksia tiedostolla. - tarkoittaa, että ei ole mitään erikoisoikeuksia

-(rwx)r--r-- suluissa kertoo tiedoston omistajan oikeudet. rwx tarkoittaa, että omistajalla on kaikki oikeudet, kirjoitus, luku ja ajamis oikeudet

-rwx(r--)r-- tarkoitta millä oikeuksia omistajan olemassa ryhmällä on. Tässä tapauksessa ryhmällä on vain lukemis oikeukset.

-rwxr--(r--) tarkoittaa mitä oikeuksia on muilla eli "others". Tässä tapauksessa on lukuoikeudet.

e)



# References
ansible-doc apt
ansible-doc copy
https://stackoverflow.com/questions/47791302/how-to-add-multiple-lines-in-ansible
https://stackoverflow.com/questions/77343074/how-to-check-uptime-of-remote-server-thru-ansible-and-send-report-as-csv-and-h
