# SOS_Win_Lab01

P1: -Pn traite tous les hôtes comme étant en ligne -> cela permet de passer outre la découverte des hôtes

P2: WAD-DC-SRV2
	On peut le déterminer en faisant les manipulations présentées dans le laboratoire (en scannant le port 445 (smb)) 
et en regardant leur nom (celui dont le nom comporte DC)
La deuxième méthode se fait en scannant grâce à un nmap sur port 88 car c'est sur ce port que tourne kerberos qui est 
propre au domain controler.

P3: ip vulnérable: 172.22.4.6
	On obtient les droits d'exécution SYSTEM
P4: 
P5: 
