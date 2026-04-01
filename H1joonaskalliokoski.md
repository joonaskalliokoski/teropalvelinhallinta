# H1

x)
	<p>- Ei tarvi mennä sshd_configure tiedostoon muokkamaan asetuksia, SSH avaimen käyttö toimii automaattisesti.</p>
	<p>- hosts.ini tiedostoon pitää kirjoittaa localhost ei käyttäjä@localhost mutta uskon molemmat käy.</p>

a)
	<p>Seurasin ohjeita teron ohjeiden mukaan. Asensin OpenSSH:n ajamalla komennon sudo apt install ssh. 
	<p>Seuraavaksi käynnistin SSH:n komenolla sudo systemctl enable ssh. 
	<p>Loin yhteyden komenolla ssh localhost ja yhdistin onnistuneesti.
	<p>Katkaisin yhteyden komennolla exit.
	<p>SSH:n lataus ja testaus tapahtui onnistuneesti.

b)
	<p>Generoin SSH-avaimet komenolla ssh-keygen.
	<p>Seuraavaksi kopion julkisen avaimen localhostiin
	<p>Testasin yhdistämällä SSH:n ja yhdistin ilman salasanalla eli SSH-avaimen luominen ja siirtäminen onnistui.

c)
	<p>Aloitin lataamalla ansible ja muita sovelluksia ohjeiden mukaisesti komenolla sudo apt-get install ansible micro bash-completion tree.
	<p>Lataus tapahtui onnistuneesti.
  
	<p>Seuraavaksi tein hakemistopuun ansible:le ja loin host.ini tiedoston johon kirjoitin localhost
	<p>Testaus tapahtui onnistuneesti

	<p>Poistin python varoituksen 
	<p>[all:vars]
	<p>ansible_python_interpreter=/usr/bin/python3

	<p>Tein ansible.cfg ja kirjoitin
	<p>[defaults]
	<p>inventory = hosts.ini

	<p>Seuraavaksi tein site.yml ja kirjoitin
	<p>- hosts: all
	  roles:
	    - hello

	<p>Aluksi oli pieniä syntax virheitä mutta sain korjattua

	<p>Tein kansion roles/hello/tasks/
	<p>ja kansioon loin main.yml ja kirjoitin tiedostoon
	- copy:
	    dest: /tmp/hello-ansible
	    content: "See you at TeroKarvinen.com!\n"

	<p>Ilmeni onglema testaukseb kanssa mutta selitän myöhemmin

	<p>Menin seuraavaksi lisäämään ansible.cfg tiedston
	[defaults]
	...
	display_args_to_stdout = true

## Ongelma
	Testasin ssh localhost 'cat /tmp/hello-ansible' mutta ilmeni error
	cat: /tmp/hello-ansible/: Not a directory
	En löytänyt ratkaisua muuten kaikki toimi tehtävään liittyen.

## References
https://terokarvinen.com/ssh-public-key-login-without-password/
https://terokarvinen.com/hello-ansible/
