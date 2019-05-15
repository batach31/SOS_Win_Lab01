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
	
P9: Il est composé ainsi: username : userid : lm hash : ntlm hash

P10: Le LM hash étant désactivé, il est toujours à la meme valeur, soit la valeur trouvée : aad3b435b51404eeaad3b435b51404ee
Les comptes guest et default account ont également le meme ntlm hash (soit : 31d6cfe0d16ae931b73c59d7e0c089c0), ce qui semble indiquer que ces deux comptes n'ont pas de mot de passe (les noms des compte guest et defaultaccount semblent aller dans ce sens)

P11: Oui, les deux desktop utilisent le meme compte administrator, et toutes les machinent partagent les deux autres comptes (sans mouvoir se connecter cependant)



P13	: C'est pour signifier qu'il s'agit d'une compte machine
P14	: Il faut avoir les droits système pour accèder au GPO sur sysvol (c'est à dire ouvrir un meterpreter via ms17_010_psexec et non via smb/psexec comee on a pu l'essayer)

MODIF P15	: oui, le 'utilisateur svc_sched et le mot de passe K33pAlive4ever sont utilisables sur les machines suivantes

MODIF P16 : 
MODIF P17 : Oui voir capture

P18 : get_user_spns renvoie une seule entrée, car un seul arbitrary spn (MSSQL) a été trouvé. Les arbitrary spn ont en général un mot de passe plus court (car défini par l'utilisateur) et quasiment jamais changé (car devant être changé par l'utilisateur).

P19 : MSSQLSvc/WAD-SQLSRV01.WAD.local:1433

P20 : adm-sql avec le mot de passe Andromeda1
P21	: Oui, voir capture d'écran
MODIF P22	:
P23	: Il  faut des privilèges administrateurs car psexec lance des services Windows et il faut être admin pour le faire
P24	: on utilise pass the hash (la vulnérabilité est que pour l'authentification ne nécessite pas le mot de passe, mais le hash du mot de passe)
P25	: avec load kiwi et creds_all.
P26	: Pour des configurations larges sur tout les domaines, pour promouvoir des utilisateurs en admin, etc
P27	: En empêchant l'accès à l'ordinateur qui contient le Domain Admin depuis le réseau par exemple
P28	: On reçoit un system error comme quoi on n'est pas log avec un utilisateur ayant les bons privilèges
P29	: La seconde fois le système nous le permet. En forgeant le golden_ticket, on a accès aux droits de tous les utilisateurs,
y compris celui du Domain Admin, ce qui nous donne le droit de faire ce qu'on veut sur cette machine, y compris monter un partage.
P30	: On voit plusieurs événement avec l'ID 4624, qui signifie qu'on s'est bien connectés (avec notre compte)
P31: Le golden ticket a la même durée de vie que le DC
PAS SUR      P32 : Surveiller l'activité lié au golden ticket (c'est à dire son utlisateur). Ou refaire tout le domaine.
