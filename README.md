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
P9:	Il est composé ainsi: username : userid : lm hash : ntlm hash
P10:Parce qu'ils partagent les mêmes mots de passe
P11:
P12:
P13	: C'est pour signifier qu'il s'agit d'une compte machine
P14	: 
P15	: 
P16 : 
P17 :
P18 : get_user_spns renvoie une seule entrée, car un seul arbitrary spn (MSSQL) , avec un mot de passe plus court et quasiment jamais changé
P19 : MSSQLSvc/WAD-SQLSRV01.WAD.local:1433
P20 : adm-sql avec le mot de passe Andromeda1
P21	: 
P22	:
P23	: Il  faut des privilèges administrateurs car psexec lance des services Windows et il faut être admin pour le faire
P24	: [dire que module a été utilie pour trouver le ntlm etc]
P25	: 
P26	: Pour des configurations larges sur tout les domaines, pour promouvoir des utilisateurs en admin, etc
P27	: En empêchant l'accès à l'ordinateur qui contient le Domain Admin depuis le réseau par exemple
P28	: On reçoit un system error comme quoi on n'est pas log avec un utilisateur ayant les bons privilèges
P29	: La seconde fois le système nous le permet. En forgeant le golden_ticket, on a accès aux droits de tous les utilisateurs,
y compris celui du Domain Admin, ce qui nous donne le droit de faire ce qu'on veut sur cette machine, y compris monter un partage.
P30	: 
