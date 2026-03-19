# Guide de migration SwiftKey → HeliBoard

> **⚠️ Date limite : 31 mai 2026** — Les données des comptes SwiftKey seront définitivement supprimées après cette date. Exportez vos données avant cette échéance.

Un guide complet, sans ADB, pour migrer votre vocabulaire appris et vos paramètres SwiftKey vers [HeliBoard](https://github.com/Helium314/HeliBoard), un clavier Android open source respectueux de la vie privée.

---

## Table des matières

- [Pourquoi HeliBoard ?](#pourquoi-heliboard)

1. [Exporter vos données SwiftKey](#1-exporter-vos-données-swiftkey)
2. [Convertir le dictionnaire](#2-convertir-le-dictionnaire)
3. [Installer HeliBoard](#3-installer-heliboard)
4. [Importer votre dictionnaire](#4-importer-votre-dictionnaire)
5. [Configurer HeliBoard comme SwiftKey](#5-configurer-heliboard-comme-swiftkey)
6. [Sauvegarder les paramètres HeliBoard](#6-sauvegarder-les-paramètres-heliboard)
7. [Désinstaller UDM](#7-désinstaller-udm)
8. [Ce qui ne transfère pas](#8-ce-qui-ne-transfère-pas)

---

## Pourquoi HeliBoard ?

La migration forcée de SwiftKey vers les comptes Microsoft est une bonne occasion de reconsidérer quel clavier vous faites confiance avec tout ce que vous tapez. Voici pourquoi HeliBoard est un excellent choix.

### 🔒 Zéro accès réseau — par conception

HeliBoard **ne demande aucune permission Internet**. Tout ce que vous tapez reste sur votre appareil — aucune frappe, aucun mot appris, aucune donnée personnelle ne quitte votre téléphone. SwiftKey et Gboard envoient tous deux des données de frappe vers des serveurs cloud pour améliorer les prédictions. HeliBoard fonctionne entièrement hors ligne.

### 🆓 Gratuit, open source, sans publicité

HeliBoard est entièrement open source (licence Apache 2.0), sans publicité, sans abonnement et sans télémétrie. Le code source est publiquement auditable sur [GitHub](https://github.com/Helium314/HeliBoard), ce qui signifie que les affirmations en matière de confidentialité peuvent réellement être vérifiées — contrairement aux alternatives propriétaires.

### ⚙️ Plus personnalisable que Gboard ou SwiftKey

HeliBoard égale ou dépasse Gboard et SwiftKey en termes de fonctionnalités :

- Historique du presse-papiers illimité (Gboard est limité à 5 éléments et se réinitialise toutes les heures)
- Icônes de barre d'outils entièrement personnalisables
- Hauteur, espacement et disposition des touches sur mesure
- Thème dynamique Material You + images de fond personnalisées
- Mode incognito forcé (désactive l'apprentissage pour les contextes sensibles)
- Dispositions et touches personnalisées par langue

### 🌍 Excellent support multilingue

Vous pouvez taper dans plusieurs langues simultanément sans changer manuellement — HeliBoard détecte la langue en cours de phrase. Les dictionnaires sont téléchargés localement par langue et fonctionnent entièrement hors ligne.

### 🛠️ Activement maintenu

HeliBoard est basé sur AOSP/OpenBoard et activement maintenu par la communauté sur GitHub. Les rapports de bugs et les demandes de fonctionnalités sont traités publiquement et de manière transparente.

### ⚖️ Limitations honnêtes

HeliBoard n'est pas parfait :

- **La prédiction de texte** est bonne mais pas encore au niveau du modèle neuronal de SwiftKey — elle s'améliorera au fur et à mesure qu'il apprend vos habitudes
- **La saisie par glissement** nécessite un téléchargement de bibliothèque séparé (propriétaire, optionnel)
- **La configuration prend quelques minutes** — il ne vient pas préconfiguré comme Gboard
- **Les mises à jour sont moins fréquentes** que les claviers commerciaux

Pour la plupart des utilisateurs venant de SwiftKey, le compromis est clair : vous perdez un modèle de correction automatique cloud légèrement plus intelligent, et vous gagnez une confidentialité totale, aucune exigence de compte et aucun risque de migration forcée future.

### 📊 Comparatif : HeliBoard vs FUTO Keyboard

| Critère | HeliBoard | FUTO Keyboard |
|---|---|---|
| **Licence** | Open source — Apache 2.0  [github](https://github.com/HeliBorg/HeliBoard) | Open source — code public sur GitHub  [cybersecuritythreatai](https://cybersecuritythreatai.com/futo-keyboard-fortifying-your-mobile-privacy-against-ai-powered-data-leaks-and-keyboard-tracking-threats/) |
| **Accès Internet** | ❌ Aucun  [discuss.privacyguides](https://discuss.privacyguides.net/t/heliboard-offline-keyboard-for-android/28093) | ❌ Aucun  [cybersecuritythreatai](https://cybersecuritythreatai.com/futo-keyboard-fortifying-your-mobile-privacy-against-ai-powered-data-leaks-and-keyboard-tracking-threats/) |
| **Saisie par glissement** | ✅ Via bibliothèque externe à télécharger  [forum.f-droid](https://forum.f-droid.org/t/heliboard-the-best-gboard-alternative/32634) | ✅ Intégré nativement (alpha)  [thecadmasters](https://thecadmasters.com/futo-keyboard-secure-offline-typing-for-the-privacy-conscious/) |
| **Saisie vocale hors ligne** | ❌ Non inclus | ✅ Inclus nativement, modèles téléchargeables  [windowsforum](https://windowsforum.com/threads/futo-keyboard-the-offline-first-android-keyboard-for-true-on-device-privacy.405419/) |
| **Qualité d'autocorrection** | ⭐⭐⭐ Bonne, s'améliore avec l'usage  [reddit](https://www.reddit.com/r/privacy/comments/1lksnc5/fossify_or_futo_keyboard/) | ⭐⭐⭐⭐ Supérieure selon les retours utilisateurs  [lemmy.dbzer0](https://lemmy.dbzer0.com/post/35503843) |
| **Support multilingue** | ✅ Excellent — détection automatique mid-phrase  [github](https://github.com/Helium314/HeliBoard/discussions/550) | ⚠️ Limité, moins mature  [reddit](https://www.reddit.com/r/foss/comments/1n3c0q0/heliboard_vs_futo_keyboard/) |
| **Personnalisation** | ⭐⭐⭐⭐⭐ Très avancée — hauteur, thèmes, toolbar, layouts  [discuss.privacyguides](https://discuss.privacyguides.net/t/heliboard-offline-keyboard-for-android/28093) | ⭐⭐ Basique — thèmes en cours de développement  [lemmy.dbzer0](https://lemmy.dbzer0.com/post/35503843) |
| **Maturité / stabilité** | ✅ Stable, v2.x+ | ⚠️ Encore en alpha/bêta  [forum.f-droid](https://forum.f-droid.org/t/heliboard-the-best-gboard-alternative/32634) |
| **Disponibilité** | F-Droid, GitHub | F-Droid, Play Store, APK direct  [cybersecuritythreatai](https://cybersecuritythreatai.com/futo-keyboard-fortifying-your-mobile-privacy-against-ai-powered-data-leaks-and-keyboard-tracking-threats/) |
| **Migration depuis SwiftKey** | ✅ Via ce guide | ❌ Pas de procédure documentée |

---

## 1. Exporter vos données SwiftKey

SwiftKey ne permet pas d'export local — vous devez passer par son portail web, qui nécessite un compte Microsoft.

**Si vous avez déjà un compte Microsoft**, passez directement à l'étape 4 ci-dessous.

**Si vous n'avez pas de compte Microsoft :**

1. Créez un **compte Microsoft temporaire** sur [account.microsoft.com](https://account.microsoft.com)
   - Vous pouvez utiliser une adresse e-mail jetable (ex. [temp-mail.org](https://temp-mail.org))
2. Dans SwiftKey → **Paramètres → Compte → Se connecter** avec ce compte
3. Attendez quelques secondes que la synchronisation se termine

**Étapes d'export (tous les utilisateurs) :**

4. Sur un PC, rendez-vous sur [data.swiftkey.com](https://data.swiftkey.com) et connectez-vous
5. Cliquez sur **Voir les données → Tout exporter**
6. Téléchargez le fichier ZIP — il sera nommé `userdata-{votre-id}-{date}.zip`
7. Extrayez le ZIP — vous trouverez :
   - `demographics.json` ← ignorez ce fichier
   - `services/sync_words.json` ← **c'est votre dictionnaire**
8. Copiez `sync_words.json` dans le dossier où vous exécuterez le script de conversion

> Vous pouvez supprimer le compte Microsoft temporaire après l'opération si vous en avez créé un pour cela.

---

## 2. Convertir le dictionnaire

HeliBoard ne peut pas importer directement le format JSON de SwiftKey. Les données brutes contiennent également du bruit (URLs, adresses e-mail, chiffres, horodatages) qui polluerait votre dictionnaire. Le script ci-dessous nettoie et convertit les données.

**Prérequis :** Python 3 installé sur votre PC ([python.org](https://python.org))

Enregistrez le script suivant sous le nom `convert.py` dans le même dossier que `sync_words.json` :

```python
import json, re

with open("sync_words.json", encoding="utf-8") as f:
    data = json.load(f)

terms = data.get("terms", [])

def is_valid_word(w):
    if len(w) < 2 or len(w) > 50:
        return False
    if re.search(r'\d', w):           # supprime tout ce qui contient des chiffres
        return False
    if re.search(r'[@/:\.\\]', w):    # supprime e-mails, URLs, chemins
        return False
    if not re.search(r'[a-zA-ZÀ-ÿ]', w):  # doit contenir au moins une lettre
        return False
    return True

cleaned = sorted(set(filter(is_valid_word, terms)))

with open("heliboard_wordlist.txt", "w", encoding="utf-8") as f:
    f.write("\n".join(cleaned))

print(f"Terminé : {len(cleaned)} mots exportés sur {len(terms)} termes au total.")
```

Exécutez-le :

```bash
python convert.py
```

Cela produit `heliboard_wordlist.txt` — une liste de mots en texte brut prête à être importée.

---

## 3. Installer HeliBoard

Installez HeliBoard depuis l'une de ces sources :

- [F-Droid](https://f-droid.org/packages/helium314.keyboard/) *(recommandé — sans Google)*
- [GitHub Releases](https://github.com/Helium314/HeliBoard/releases)

Puis activez-le comme clavier par défaut :

1. **Paramètres Android → Système → Langue et saisie → Clavier à l'écran → Gérer les claviers** → activer HeliBoard
2. Appuyez sur **Sélectionner le clavier** dans n'importe quel champ de texte → choisissez HeliBoard

---

## 4. Importer votre dictionnaire

[UDM (User Dictionary Manager)](https://play.google.com/store/apps/details?id=com.dooboolab.UDM) est nécessaire comme pont pour injecter les mots dans le dictionnaire système Android, que HeliBoard utilise.

1. Installez **UDM** depuis F-Droid ou le Play Store
2. Copiez `heliboard_wordlist.txt` sur votre téléphone
3. Ouvrez UDM → **Importer**
4. Sélectionnez le format : **Plain Text / Word List** *(pas Gboard/CSV)*
5. Sélectionnez votre fichier
6. Assignez la langue : `fr_FR`, `en_US`, ou **Toutes les langues** selon votre cas d'usage
7. Appuyez sur **Démarrer**

**Vérifiez l'import :**

Allez dans **HeliBoard Paramètres → Dictionnaire → Dictionnaire personnel** — vous devriez voir vos mots listés.

---

## 5. Configurer HeliBoard comme SwiftKey

### 5.1 Saisie multilingue (ex. français + anglais simultanément)

> ⚠️ Vous devez appuyer sur le **nom de la langue** — pas sur le bouton bascule — pour accéder aux options multilingues.

1. **Paramètres → Langues & Dispositions** → appuyez sur **+ Ajouter une langue** → sélectionnez `French (fr_FR)`
2. Appuyez sur le **nom de la langue française** → appuyez sur **+** à côté de *Saisie multilingue* → ajoutez `English (en_US)`
3. **Paramètres → Dictionnaire → Ajouter un dictionnaire** → téléchargez les dictionnaires pour `fr_FR` et `en_US`

### 5.2 Barre de suggestions (3 mots, espace = valider le mot central)

Dans **Paramètres → Correction du texte**, activez les options suivantes :

| Paramètre | Valeur |
|---|---|
| Afficher les suggestions | ✅ Activé |
| Toujours afficher la suggestion centrale | ✅ Activé |
| Remplacer automatiquement par la suggestion centrale | ✅ Activé |
| Correction automatique | *Modeste* (à ajuster selon vos préférences) |
| Suggestions de mot suivant | ✅ Activé |

> Le mot central apparaît en **gras** lorsqu'il diffère de ce que vous avez tapé (la correction automatique se déclenchera à l'espace). S'il n'est pas en gras, appuyer sur espace conserve votre mot tel quel.

### 5.3 Saisie par glissement (optionnel)

HeliBoard n'inclut pas la bibliothèque de gestes pour des raisons de licence. Pour l'activer :

1. Téléchargez `gesture_typing_library.zip` depuis la [page des releases GitHub de HeliBoard](https://github.com/Helium314/HeliBoard/releases)
2. Extrayez le fichier `.so` correspondant à votre architecture CPU (généralement `arm64-v8a`)
3. Dans HeliBoard : **Paramètres → Avancé → Charger la bibliothèque de saisie gestuelle** → sélectionnez le fichier `.so`

### 5.4 Confort et disposition

| Fonctionnalité | Chemin |
|---|---|
| Rangée de chiffres | Paramètres → Préférences → Rangée de chiffres ✅ |
| Double espace = point | Paramètres → Saisie → Période double espace ✅ |
| Glisser sur la barre d'espace pour changer de langue | Paramètres → Avancé → Glissement horizontal barre d'espace → *Changer de langue* |
| Hauteur / espacement des touches | Paramètres → Apparence → Hauteur de touche personnalisée |
| Thème (Material You) | Paramètres → Apparence → Thème → *Material You* |

### 5.5 Personnalisation de la barre d'outils

**Paramètres → Apparence → Personnaliser les icônes de la barre d'outils** — icônes recommandées :

- Presse-papiers
- Annuler / Rétablir
- Sélectionner un mot
- Saisie vocale *(optionnel)*

### 5.6 Correctif pour Reddit et Google Keep (Bug d'absence de suggestions)

Ce bug est bien connu et a une cause précise : l'app Reddit (et certaines autres) positionne un flag `TYPE_TEXT_FLAG_NO_SUGGESTIONS` sur ses champs de texte. HeliBoard respecte ce flag par défaut — contrairement à SwiftKey ou Gboard qui l'ignorent.

Le correctif en une manipulation :

**HeliBoard Paramètres → Correction du texte → Always show suggestions** → ✅ Activer

Et vérifiez aussi que cette option est désactivée :

**Correction du texte → Don't show suggestions for web edit fields** → ❌ Désactiver

C'est tout. Les suggestions apparaîtront désormais dans Reddit, Google Keep, et tous les autres champs qui utilisaient ce flag.

---

## 6. Sauvegarder les paramètres HeliBoard

Une fois tout configuré, sauvegardez vos paramètres pour ne jamais avoir à recommencer :

**HeliBoard Paramètres → Avancé → Sauvegarder les paramètres** → conservez le fichier en lieu sûr.

Pour restaurer sur un nouvel appareil : **Paramètres → Avancé → Restaurer les paramètres** → sélectionnez le fichier de sauvegarde.

---

## 7. Désinstaller UDM

**Vous pouvez désinstaller UDM immédiatement** après l'import. UDM n'est qu'un outil de transfert. Une fois les mots injectés dans le dictionnaire personnel système d'Android, ils appartiennent à HeliBoard et UDM ne joue plus aucun rôle.

---

## 8. Ce qui ne transfère pas

| Fonctionnalité SwiftKey | Statut |
|---|---|
| Modèle de correction appris / prédictions IA | ❌ HeliBoard réapprend depuis zéro |
| Thèmes | ❌ À reconfigurer manuellement |
| Historique du presse-papiers | ❌ Non exporté par SwiftKey |
| Dictionnaire personnel (mots ajoutés manuellement) | ✅ Transféré via ce guide |
| Vocabulaire appris (mots tapés) | ✅ Transféré via ce guide |

---

## Crédits et références

- [Portail de données SwiftKey](https://data.swiftkey.com)
- [HeliBoard GitHub](https://github.com/Helium314/HeliBoard)
- [User Dictionary Manager (UDM)](https://play.google.com/store/apps/details?id=com.dooboolab.UDM)
- Concept original du convertisseur : [AiCurv/SwiftKey-to-HeliBoard (GitHub Gist)](https://gist.github.com/AiCurv/dc16a89ffe09c0d25f24049dcff40005)

---

*Guide rédigé en mars 2026. Testé sur Android 13/14. Date limite de suppression des comptes SwiftKey : 31 mai 2026.*
