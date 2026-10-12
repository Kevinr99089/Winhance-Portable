<div align="center">

# Winhance Portable

**Créez un `autounattend.xml` pour Windows depuis n'importe quel appareil, directement dans votre navigateur.**

[🇬🇧 English](README.md) · [🇫🇷 Français](REAMEfr.md)

🌐 **[Ouvrir Winhance Portable](https://kevinr99089.github.io/Winhance-Portable/)**

</div>

---

## Qu'est-ce que Winhance Portable ?

Winhance Portable est une page HTML unique et autonome qui prolonge l'idée de [Winhance](https://github.com/memstechtips/Winhance) pour la rendre accessible sur davantage d'appareils. Ouvrez-la sur un téléphone, une tablette ou un ordinateur, choisissez les réglages Windows, les applications et les ajustements souhaités, et elle génère un fichier `autounattend.xml` pour une installation de Windows sans intervention.

**Rien n'est exécuté sur l'appareil où vous ouvrez la page.** Elle fabrique uniquement un fichier XML. Les actions ont lieu plus tard, au premier démarrage de Windows, lorsque ce fichier est utilisé comme `autounattend.xml`.

## Pourquoi Winhance Portable ?

Winhance est un excellent outil, mais il fonctionne sous Windows. Winhance Portable permet de préparer le même type de configuration depuis n'importe où :

- **Tous les appareils** : Android, iOS, tablette, Linux, macOS ou Windows. Un navigateur récent suffit.
- **Interface pensée pour le mobile** : grandes zones tactiles, navigation par dock en bas d'écran, prise en charge des zones sûres.
- **Aucune installation, aucun backend** : c'est une page `.html` statique unique, hébergée sur GitHub Pages, utilisable directement depuis votre navigateur. Vous pouvez aussi enregistrer le fichier et l'utiliser hors ligne.
- **Confidentialité** : vos choix restent dans le stockage local de votre navigateur et ne sont jamais envoyés ailleurs.

## Fonctionnalités

- **Plus de 700 options** réparties sur 12 onglets, avec une recherche instantanée sur l'ensemble.
- **Applications et fonctionnalités Windows** : retrait des applications intégrées, des capacités Windows et des fonctionnalités facultatives.
- **Logiciels externes** : installation via `winget` (ou le Store, Chocolatey ou un téléchargement direct pour quelques-uns), avec en plus des **logiciels tiers absents de Winhance**, comme Bitwarden, NordPass, qBittorrent, Signal, Docker Desktop, CPU-Z, GPU-Z, HWMonitor, OCCT, CrystalDiskMark, MSI Afterburner, balenaEtcher, TranslucentTB, Plex, Logitech G HUB, SteelSeries GG et Corsair iCUE.
- **Optimisations** : Confidentialité & Sécurité (dont les fonctions d'IA de Windows, Edge et Office), Alimentation (valeurs sur secteur et sur batterie), Jeux et Performances, Mise à jour, Notifications et Son.
- **Personnalisations** : thème Windows, barre des tâches, menu Démarrer et Explorateur.
- **Préréglages en un geste** pour l'onglet courant ou pour tous les onglets :
  - **Recommandé Winhance** : les choix suggérés par Winhance.
  - **Défaut Windows** : retour aux valeurs d'origine de Windows.
- **Import** d'un fichier `.winhance` ou XML existant pour repartir de celui-ci.
- **Export** du résultat : téléchargement du `.xml`, copie ou sélection du texte.
- **Interface bilingue** (français et anglais), détectée automatiquement selon la langue de l'appareil.
- **Thèmes clair et sombre** qui suivent le réglage du système.

## Utilisation

1. Ouvrez [Winhance Portable](https://kevinr99089.github.io/Winhance-Portable/) dans votre navigateur (ou ouvrez une copie enregistrée du fichier HTML).
2. Parcourez les groupes (**Logiciels & Apps**, **Optimisations**, **Personnalisations**) et leurs onglets, ou utilisez la barre de recherche.
3. Faites vos choix :
   - **Apps Windows** : case cochée = retirée.
   - **Apps externes** : case cochée = installée.
   - **Réglages** : utilisez l'interrupteur pour Activé/Désactivé, ou choisissez une option dans la liste.
4. Appliquez éventuellement un préréglage (**Recommandé Winhance** ou **Défaut Windows**) depuis la barre du bas ou le menu.
5. Ouvrez le panneau **XML**, puis téléchargez ou copiez l'`autounattend.xml` généré.
6. Utilisez-le avec votre support d'installation de Windows ou votre procédure de déploiement.

> Décocher une app ne fait jamais l'inverse : une app Windows décochée est laissée telle quelle (jamais réinstallée), et une app externe décochée n'est simplement pas installée (jamais désinstallée).

## Les onglets en un coup d'œil

| Groupe | Onglets |
| --- | --- |
| Logiciels & Apps | Applications et fonctionnalités Windows · Logiciels externes |
| Optimisations | Confidentialité & Sécurité · Alimentation · Jeux et Performances · Mise à jour · Notifications · Son |
| Personnalisations | Thème Windows · Barre des tâches · Menu Démarrer · Explorateur |

## À savoir

- Le fichier généré **ne gère ni les disques ni les comptes**.
- Les réglages utilisateur (HKCU) s'appliquent au **premier compte qui se connecte**.
- Les apps `winget`, le raccourci Winhance et la recherche de mises à jour **demandent une connexion réseau**.
- Un réglage sans valeur d'origine connue (les actions de nettoyage, par exemple) n'est pas modifié par **Défaut Windows**.
- Lors de l'import d'un fichier, les parties non gérées par cette page (scripts, services, tâches) sont ignorées.
- **Testez toujours dans une machine virtuelle avant une vraie machine.** Ces ajustements modifient des réglages profonds du système.

## Crédits

Winhance Portable s'inspire de [Winhance](https://github.com/memstechtips/Winhance) de memstechtips, dont il est un prolongement. Il s'agit d'un projet indépendant, sans affiliation ni approbation de l'auteur original ou de Microsoft.

## Avertissement

Cet outil est fourni tel quel, sans aucune garantie. Vous êtes responsable de la configuration que vous générez et de son test avant tout déploiement.