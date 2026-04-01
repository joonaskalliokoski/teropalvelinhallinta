# H1

x)

<p>- Ei tarvi mennä sshd_configure tiedostoon muokkamaan asetuksia, SSH avaimen käyttö toimii automaattisesti.</p>
<p>- hosts.ini tiedostoon pitää kirjoittaa localhost ei käyttäjä@localhost mutta uskon molemmat käy.</p>

a)

<p>Seurasin ohjeita teron ohjeiden mukaan. Asensin OpenSSH:n ajamalla komennon sudo apt install ssh.</p>
<p>Seuraavaksi käynnistin SSH:n komenolla sudo systemctl enable ssh.</p>
<p>Loin yhteyden komenolla ssh localhost ja yhdistin onnistuneesti.</p>
<p>Katkaisin yhteyden komennolla exit.</p>
<p>SSH:n lataus ja testaus tapahtui onnistuneesti.</p>

b)

<p>Generoin SSH-avaimet komenolla ssh-keygen.</p>
<p>Seuraavaksi kopion julkisen avaimen localhostiin.</p>
<p>Testasin yhdistämällä SSH:n ja yhdistin ilman salasanalla eli SSH-avaimen luominen ja siirtäminen onnistui.</p>

c)

<p>Aloitin lataamalla ansible ja muita sovelluksia ohjeiden mukaisesti komenolla sudo apt-get install ansible micro bash-completion tree.</p>
<p>Lataus tapahtui onnistuneesti.</p>

<p>Seuraavaksi tein hakemistopuun ansible:le ja loin host.ini tiedoston johon kirjoitin localhost.</p>
<p>Testaus tapahtui onnistuneesti.</p>

<p>Poistin python varoituksen</p>

<pre>
[all:vars]
ansible_python_interpreter=/usr/bin/python3
</pre>

<p>Tein ansible.cfg ja kirjoitin</p>

<pre>
[defaults]
inventory = hosts.ini
</pre>

<p>Seuraavaksi tein site.yml ja kirjoitin</p>

<pre>
- hosts: all
  roles:
    - hello
</pre>

<p>Aluksi oli pieniä syntax virheitä mutta sain korjattua.</p>

<p>Tein kansion roles/hello/tasks/ ja kansioon loin main.yml ja kirjoitin tiedostoon</p>

<pre>
- copy:
    dest: /tmp/hello-ansible
    content: "See you at TeroKarvinen.com!\n"
</pre>

<p>Ilmeni onglema testaukseb kanssa mutta selitän myöhemmin.</p>

<p>Menin seuraavaksi lisäämään ansible.cfg tiedoston</p>

<pre>
[defaults]
...
display_args_to_stdout = true
</pre>

## Ongelma

<p>Testasin ssh localhost 'cat /tmp/hello-ansible' mutta ilmeni error</p>

<pre>
cat: /tmp/hello-ansible/: Not a directory
</pre>

<p>En löytänyt ratkaisua muuten kaikki toimi tehtävään liittyen.</p>

## References

https://terokarvinen.com/ssh-public-key-login-without-password/  
https://terokarvinen.com/hello-ansible/
