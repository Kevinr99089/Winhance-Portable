# Winhance Portable

🇫🇷 [Français](READMEfr.md)· 🇬🇧 [English](README.md)

Une page web unique, pensée pour le téléphone, qui fabrique un fichier **`autounattend.xml`** à partir du catalogue de réglages de [Winhance](https://github.com/memstechtips/Winhance). Tout se règle au pouce, en prenant son temps, sans PC et sans rien installer.

**Page en ligne :** <https://kevinr99089.github.io/Winhance-Portable/>

> Projet personnel et non officiel. Il n'est pas affilié à Winhance ni à son auteur. Voir [Licence et crédits](#licence-et-crédits).

---

## Ce que fait la page

La page **n'exécute rien**. Elle assemble un fichier XML. Les actions ont lieu plus tard, au premier démarrage de Windows, quand le fichier sert d'`autounattend.xml` à l'installation.

### Le catalogue

| Contenu | Nombre |
|---|---|
| Réglages Winhance (10 onglets) | 420 |
| Apps Windows à retirer | 56 |
| Capacités Windows à retirer | 10 |
| Fonctionnalités Windows à désactiver | 7 |
| Apps à installer (winget) | 182 |
| Raccourci « Install Winhance » sur les bureaux | 1 |

Onglets de réglages : Confidentialité (90), Jeux et performances (107), Explorateur (87), Alimentation (48), Barre des tâches (28), Notifications (15), Mises à jour (14), Menu Démarrer (14), Thème (10), Son (7).

Les noms et descriptions sont en français quand Winhance les traduit.

### Comment lire les cases

- **Réglages** : trois états. **–** ne touche à rien (Windows garde son état), **On** applique la valeur « activée » de la fonction décrite, **Off** la valeur « désactivée ». Les listes et les cases Secteur/Batterie sont ignorées tant qu'elles restent sur « – ».
- **Apps Windows** : case cochée = l'app est **retirée**. Décochée = elle reste. Jamais de réinstallation.
- **Apps externes** : case cochée = l'app est **installée** (winget). Décochée = rien. Jamais de désinstallation.

### Boutons et navigation

Une barre en bas de l'écran, pour le pouce :

- **Menu** : Recommandé Winhance pour tous les onglets, charger un fichier, vider l'onglet courant, tout réinitialiser, aide.
- **Recommandé** : applique les choix de Winhance à l'**onglet courant** uniquement.
- **Défaut Windows** : remet l'onglet courant aux **valeurs d'origine de Windows**. Sur les onglets d'apps, il devient « Tout décocher ». Il n'existe pas en version globale, volontairement.
- **XML** : ouvre le fichier généré, avec Télécharger, Copier et Sélectionner. Un compteur indique le nombre de choix.

Autres éléments : recherche dans toutes les options, onglets collés en haut, deux colonnes en paysage, notes repliables, messages courts au-dessus de la barre. Les choix sont mémorisés dans le navigateur de l'appareil.

### Charger un fichier existant

Le bouton « Charger un fichier » (dans le Menu) accepte :

- un fichier **`.winhance`** (configuration exportée par Winhance) ;
- un **`autounattend.xml`** créé par Winhance ou par cette page.

La page coche les réglages reconnus. Vous les modifiez, puis vous récupérez un XML. Une partie des éléments d'un autounattend de Winhance peut ne pas être reconnue : le message affiché indique combien l'ont été.

### Réglages spécifiques

- **Plan d'alimentation** : Économie, Équilibré, Performances élevées, Performances ultimes, ou le **plan Winhance** (créé à partir de Performances ultimes). Les réglages d'alimentation cachés de Windows sont déverrouillés avant les valeurs.
- **Edge et OneDrive** : retirés avec les vrais scripts de suppression de Winhance, embarqués dans le XML.
- **Teams et Xbox** : les correctifs de Winhance sont ajoutés quand vous retirez ces apps (arrêt des processus Teams, redirection de la Game Bar).
- **Différer les mises à jour jusqu'au bureau** (onglet « Mises à jour ») : bloque Windows Update pendant l'OOBE sans toucher au réseau ni au compte Microsoft, puis le réactive à la première session et lance une recherche. **Méthode non officielle**, non testée. Sur les ISO récentes, le bouton « Mettre à jour plus tard » de l'OOBE fait aussi l'affaire.

---

## Utilisation

1. Ouvrez la page, choisissez un onglet et réglez ce que vous voulez (ou utilisez **Recommandé**).
2. Passez d'un onglet à l'autre. Le compteur de la barre du bas suit vos choix.
3. Ouvrez **XML**, puis **Télécharger** (ou **Copier** et collez le contenu dans un fichier texte).
4. Enregistrez le fichier sous le nom **`autounattend.xml`** et placez-le à la **racine** de l'ISO ou de la clé USB d'installation de Windows.
5. Lancez l'installation. Les actions s'exécutent à la première ouverture de session.

Testez **toujours dans une machine virtuelle** avant une vraie machine.

---

## Ce que contient le XML

- une passe **windowsPE** minimale (acceptation de la licence), qui garantit que le fichier est bien copié par l'installeur ;
- une passe **specialize** uniquement si la case « Différer les mises à jour » est cochée ;
- une passe **oobeSystem** avec des **commandes au premier démarrage** (`FirstLogonCommands`) : valeurs de registre, tâches planifiées, alimentation, retrait d'apps, installations winget ;
- une section **Extensions** qui embarque les scripts PowerShell nécessaires (Edge, OneDrive, correctifs, réglages à script). Ils sont extraits depuis `C:\Windows\Panther\unattend.xml` au premier démarrage, comme le fait Winhance.

---

## Limites connues

- **Non testé sur Windows.** Les tests portent sur la logique de la page, la validité du XML et le rechargement des choix. Le PowerShell n'a pas été exécuté.
- Le XML produit est **plus simple que celui de Winhance** : une suite de commandes au premier démarrage, pas son script complet. Il n'est donc pas identique octet pour octet.
- **Ni disques ni comptes** : le partitionnement, la création de compte et la langue ne sont pas gérés. Le réseau et le compte Microsoft ne sont pas modifiés.
- Les réglages **utilisateur (HKCU)** s'appliquent au premier compte qui ouvre une session.
- Les extractions de scripts exigent que le fichier serve d'**`autounattend.xml` à l'installation** (copie dans `C:\Windows\Panther`). Appliqué après coup, ce mécanisme peut ne pas fonctionner.
- Les installations **winget**, le raccourci Winhance et la recherche de mises à jour demandent du **réseau** au premier démarrage.
- Les réglages de **services** passent par la valeur `Start` du registre : ils prennent effet au redémarrage.
- Les icônes de la zone de notification ne touchent que les icônes déjà présentes au premier démarrage.
- Certains réglages n'existent que sous Windows 11, d'autres que sous Windows 10 (indiqué dans leur description).
- Retirer **Edge** peut rendre Windows instable, comme Winhance l'indique.
- Le rechargement du XML ne retrouve pas **tous** les choix : environ 13 sur 473 sont perdus lors d'un aller-retour avec le préréglage complet.
- L'option « Afficher toutes les épingles par défaut » repose sur une valeur de registre documentée par Microsoft, sans pouvoir la comparer au code de Winhance.

---

## Confidentialité

Tout se passe dans le navigateur. La page ne contient aucune ressource externe et n'envoie aucune donnée. Les choix sont conservés localement (stockage du navigateur) et les fichiers chargés sont lus sur l'appareil.

---

## Licence et crédits

Winhance est l'œuvre de Marco du Plessis et de ses contributeurs, publié sous licence **PolyForm Shield 1.0.0**. Le catalogue de réglages, les traductions françaises et les scripts embarqués (suppression d'Edge et d'OneDrive, correctifs) en sont issus.

Required Notice: Copyright (c) 2025 Marco du Plessis (https://github.com/Jeyloh/Winhance)

- Licence de Winhance : <https://polyformproject.org/licenses/shield/1.0.0>
- Projet d'origine : <https://github.com/memstechtips/Winhance>

Ce projet est lui aussi distribué sous la licence **PolyForm Shield 1.0.0** (voir le fichier [`LICENSE`](LICENSE)), qui reprend la mention de copyright de Winhance ci-dessus. Cette page est un outil personnel, non affilié, qui n'a pas vocation à remplacer Winhance. Pour l'application complète, utilisez Winhance lui-même.
