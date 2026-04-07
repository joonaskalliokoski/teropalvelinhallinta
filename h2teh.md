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

Luodaan ensin oma kansio ja main.yml uudelle roolille 

<img width="325" height="224" alt="image" src="https://github.com/user-attachments/assets/f3a34f8c-d21e-4ccf-819f-41d0a33b12bb" />



