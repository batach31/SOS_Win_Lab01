# SOS_Win_Lab01

P1: -Pn traite tous les hôtes comme étant en ligne -> cela permet de passer outre la découverte des hôtes

P2: WAD-DC-SRV2
	On peut le déterminer en faisant les manipulations présentées dans le laboratoire (en scannant le port 445 (smb)) 
et en regardant leur nom (celui dont le nom comporte DC)
La deuxième méthode se fait en scannant grâce à un nmap sur port 88 car c'est sur ce port que tourne kerberos qui est 
propre au domain controler.

P3: ip vulnérable: 172.22.4.6
	On obtient les droits d'exécution SYSTEM
P4: La faille MS17-010 permet à l'attaquant d'exécuter n'importe quelle commande et donc, d'avoir les privilèges system.
P5: 188 powershell.exe (grâce aux commandes getpid et ps dans le meterpreter)
P6: Un reverse shell fait en sorte que la victime vienne se connecter à un port définit par l'attaquant (sur sa machine) alors qu'un bind shell consiste à ouvrir un port sur la machine de la victime et à s'y connecter.
P7: Il est recommandé d'utiliser un reverse shell lorsqu'il y a un firewall protegeant la victime (qui risquerait d'empecher un bind)
P8: Il s'agit de composants payload (comme Meterpreter dans notre cas) qui sont téléchargés depuis un Stager.
	Les Stagers permettant eux de créer une connection entre l'attaquant et la victime.