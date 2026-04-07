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

