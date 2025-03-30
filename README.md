Truenas Scale
Création par M Michael Vandevelde
Date de
création
Catégorie
Réviseurs M Michael Vandevelde E Etienne Verschuere
B Bastien Llorca F Frederic Perry
Introduction
Objectif  Présenter l'installation et la configuration de deux machines
virtuelles VM, l'une hébergeant un serveur TrueNAS Scale et l'autre une
distribution Debian avec une interface graphique.
Contexte  Ce projet vise à démontrer la mise en place d'un serveur de
stockage sécurisé et accessible via différents protocoles.
Étape 1 : Configuration des Machines Virtuelles
VM 1 : Serveur TrueNAS Scale
 Téléchargement de TrueNAS Scale :
Rendez-vous sur le site officiel de TrueNAS.
Téléchargez l'image ISO de TrueNAS Scale.
nous prenons soins de télécharger sur le site officiel la dernière version
stable
TrueNAS SCALE 24.10.2
site officiel : https://www.truenas.com/download-truenas-scale/
 Création de la VM :25 mars 2025 0942Truenas ScaleProcesseur  Allouez 2 cœurs pour assurer des performances
adéquates.
Mémoire vive RAM  Configurez 4 Go de RAM pour gérer
efficacement les opérations de stockage. ; Au regard de notre allez plus
loin nous changerons cela en 10 Go
Disques durs :
Ajoutez 2 disques de 16 Go pour le système d'exploitation et les
données système.
Ajoutez 5 disques de 2 To pour le stockage des données utilisateur.
 Installation de TrueNAS Scale :
Montez l'ISO téléchargée dans le lecteur virtuel de la VM.
Démarrez la VM et suivez les instructions à l'écran pour installer
TrueNAS Scale sur l'un des disques de 16 Go.
Configurez les paramètres réseau de base pour accéder à l'interface
web.
VM 2 : Debian avec Interface Graphique
 Création de la VM :
Processeur  Allouez 2 cœurs pour une utilisation fluide de l'interface
graphique.
Mémoire vive RAM  Configurez 2 Go de RAM.
Disque dur  Ajoutez un disque de 8 Go pour le système d'exploitation
et les applications.
 Installation de Debian :
Téléchargez l'image ISO de Debian depuis le site officiel.
Montez l'ISO et démarrez la VM.
Suivez les instructions pour installer Debian avec une interface
graphique (par exemple, GNOME ou Xfce).
Étape 2 : Configuration du RAID 6 sur TrueNAS Scale
 Accès au Portail Administrateur :Truenas ScaleUne fois l'installation terminée, accédez à l'interface web de TrueNAS
Scale via un navigateur en utilisant l'adresse IP de la VM et le port
HTTPS (par défaut, 443.
Connectez-vous avec les identifiants configurés lors de l'installation.
 Création du RAID 6 :
Allez dans la section "Storage" Stockage) de l'interface.
Sélectionnez les 5 disques de 2 To pour créer un pool de stockage.
Choisissez RAID 6 pour la redondance et la tolérance aux pannes.
Nommez le pool "Stockage" et finalisez la configuration.
Étape 3 : Connexions au Serveur
 Connexion SSH :
Dans l'interface de TrueNAS Scale, activez le service SSH.
Ensuite nous prenons soins de changer le port part defaut par un port
autre par mesure de sécurité
Notez l'adresse IP du serveur TrueNAS Scale.
Sur la VM Debian, utilisez un client SSH (comme OpenSSH pour vous
connecter au serveur TrueNAS Scale.
Sur La CM Cdebien nous installons le packet ssh openssh-server.
 Connexion HTTPS :
Accédez à l'interface web de TrueNAS Scale pour vérifier les mises à
jour disponibles.
Reconnectez-vous à l'interface web après le redémarrage.
 Connexion SFTP :
Activez le service SFTP sur TrueNAS Scale.
Configurez plusieurs sessions SFTP, chacune avec un dossier dédié et
un dossier public pour le partage de fichiers.
Modifiez le port de connexion SFTP par défaut 22 pour améliorer la
sécurité. Notez le nouveau port.Truenas ScaleÉtape 4 : Vérification et Tests
 Test des Connexions :
Sur la VM Debian, utilisez un client SFTP (comme FileZilla) pour vous
connecter au serveur TrueNAS Scale en utilisant le nouveau port
configuré.
Vérifiez que vous pouvez accéder aux dossiers configurés et transférer
des fichiers entre la VM Debian et le serveur TrueNAS Scale.
Avantages et Inconvénients de TrueNAS Scale
Avantages
 Open Source  TrueNAS Scale est une solution open source, ce qui permet
une grande flexibilité et une personnalisation selon les besoins.
 Scalabilité  Conçu pour être évolutif, TrueNAS Scale peut gérer de grandes
quantités de données et s'adapter à l'augmentation des besoins de
stockage.
 Interface Utilisateur  L'interface web est intuitive et facilite la gestion du
stockage, des utilisateurs et des permissions.
 Fonctionnalités Avancées  Supporte des fonctionnalités avancées comme
le RAID, les snapshots, et la réplication.
 Communauté Active  Une communauté active et un support disponible
pour aider à résoudre les problèmes.
Inconvénients
 Complexité  La configuration initiale peut être complexe pour les
utilisateurs non techniques.
 Ressources Système  Nécessite des ressources matérielles substantielles
pour fonctionner de manière optimale.
 Stabilité  Étant une solution relativement nouvelle, elle peut présenter des
bugs ou des problèmes de stabilité.
 Documentation  Bien que la documentation soit disponible, elle peut ne
pas couvrir tous les cas d'utilisation spécifiques.
Conclusion sur TrueNAS ScaleTruenas ScaleTrueNAS Scale est une solution de stockage open source puissante et flexible,
idéale pour les environnements nécessitant une gestion robuste et sécurisée
des données. Sa capacité à évoluer avec les besoins des utilisateurs, combinée
à des fonctionnalités avancées comme le RAID et les snapshots, en fait un
choix fiable pour protéger l'intégrité des données.
L'interface intuitive facilite la gestion, même pour les utilisateurs non
techniques, tandis que les options de sécurité renforcée, telles que les
connexions SSH et SFTP, garantissent la confidentialité des données. Bien que
la configuration initiale puisse être complexe, la communauté active et le
support disponible aident à surmonter ces défis.
En résumé, TrueNAS Scale offre une solution complète pour la gestion du
stockage, alliant performance, sécurité et flexibilité.
Étape 5 : Mise en place dʼun emulateur sur true nas , en
utilisant kvm
Nous avons choisit dʼinstaller un émulateur multi systeme , avec des roms
publiques
qui fonctionnne sous KVM.
nous telechargeons lʼemulateur Batocera.linux
le lien directe : https://batocera.org/download
attention a la virtualisation imbriqué qui peu tposer probleme dans ce cas la :
cmd en mode administrateur : (important)
"bcdedit /set hypervisorlaunchtype off"
ensuite cmd fonction avancées decocher hyper v , virtualisation
attebion un redémarrage est imperatifTruenas Scaleafin de contourner tout probleme techniques, nous avons decider de ne pas
installer une image iso simple mais nous avons utiliser des fichiers de
configurations
nous avons parametrer la machine suivant nos besoins.Truenas Scal
