# H1

x)
	Ei tarvi mennä sshd_configure tiedostoon muokkamaan asetuksia, SSH avaimen käyttö toimii automaattisesti.
	hosts.ini tiedostoon pitää kirjoittaa localhost ei käyttäjä@localhost mutta uskon molemmat käy.

a)
	Seurasin ohjeita teron ohjeiden mukaan. Asensin OpenSSH:n ajamalla komennon sudo apt install ssh. 
	Seuraavaksi käynnistin SSH:n komenolla sudo systemctl enable ssh. 
	Loin yhteyden komenolla ssh localhost ja yhdistin onnistuneesti.
	Katkaisin yhteyden komennolla exit.
	SSH:n lataus ja testaus tapahtui onnistuneesti.

b)
	Generoin SSH-avaimet komenolla ssh-keygen.
	Seuraavaksi kopion julkisen avaimen localhostiin
	Testasin yhdistämällä SSH:n ja yhdistin ilman salasanalla eli SSH-avaimen luominen ja siirtäminen onnistui.

c)
	Aloitin lataamalla ansible ja muita sovelluksia ohjeiden mukaisesti komenolla sudo apt-get install ansible micro bash-completion tree.
	Lataus tapahtui onnistuneesti.
  
	Seuraavaksi tein hakemistopuun ansible:le ja loin host.ini tiedoston johon kirjoitin localhost
	Testaus tapahtui onnistuneesti

	Poistin python varoituksen 
	[all:vars]
	ansible_python_interpreter=/usr/bin/python3

	Tein ansible.cfg ja kirjoitin
	[defaults]
	inventory = hosts.ini

	Seuraavaksi tein site.yml ja kirjoitin
	- hosts: all
	  roles:
	    - hello

	Aluksi oli pieniä syntax virheitä mutta sain korjattua

	Tein kansion roles/hello/tasks/
	ja kansioon loin main.yml ja kirjoitin tiedostoon
	- copy:
	    dest: /tmp/hello-ansible
	    content: "See you at TeroKarvinen.com!\n"

	Ilmeni onglema testaukseb kanssa mutta selitän myöhemmin

	Menin seuraavaksi lisäämään ansible.cfg tiedston
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
