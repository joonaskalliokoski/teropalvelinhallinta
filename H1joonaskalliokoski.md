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
	<p>[all:vars]</p>
	<p>ansible_python_interpreter=/usr/bin/python3</p>

	<p>Tein ansible.cfg ja kirjoitin</p>
	<p>[defaults]</p>
	<p>inventory = hosts.ini</p>

	<p>Seuraavaksi tein site.yml ja kirjoitin</p>
	<p>- hosts: all</p>
	<p>  roles:</p>
	<p>    - hello</p>

	<p>Aluksi oli pieniä syntax virheitä mutta sain korjattua</p>

	<p>Tein kansion roles/hello/tasks/</p>
	<p>ja kansioon loin main.yml ja kirjoitin tiedostoon</p>
	<p>- copy:</p>
	<p>    dest: /tmp/hello-ansible</p>
	<p>    content: "See you at TeroKarvinen.com!\n"</p>

	<p>Ilmeni onglema testaukseb kanssa mutta selitän myöhemmin</p>

	<p>Menin seuraavaksi lisäämään ansible.cfg tiedston</p>
	<p>[defaults]</p>
	<p>...</p>
	<p>display_args_to_stdout = true</p>

## Ongelma
	Testasin ssh localhost 'cat /tmp/hello-ansible' mutta ilmeni error
	cat: /tmp/hello-ansible/: Not a directory
	En löytänyt ratkaisua muuten kaikki toimi tehtävään liittyen.

## References
https://terokarvinen.com/ssh-public-key-login-without-password/
https://terokarvinen.com/hello-ansible/
