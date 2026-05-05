# 🌿 TontineChain

**TontineChain** est une application mobile qui sécurise les tontines (épargne collective) grâce à la blockchain **Celo**. Elle permet à des groupes de personnes de créer et gérer une tontine dont les règles sont **automatiquement appliquées** par un smart contract, sans risque de détournement ni de litige.

---

## 🎯 Problème résolu

Au Bénin :
- **60 à 70 %** des adultes participent à des tontines
- **15 à 20 %** des tontines subissent chaque année un incident grave (détournement, litige, impayé)
- **70 %** des participants sont des femmes, premières victimes de ces incidents

Les tontines traditionnelles reposent uniquement sur la confiance. Quand un organisateur disparaît avec la caisse ou qu'un membre refuse de payer, **les pertes sont définitives**.

---

## 💡 Solution

TontineChain transforme une tontine traditionnelle en **smart contract** sur la blockchain Celo :

| Problème | Solution TontineChain |
|----------|----------------------|
| L'organisateur peut voler la caisse | L'argent est **verrouillé** dans le smart contract |
| Les règles peuvent être contestées | Les règles sont **immuables** (personne ne peut les modifier) |
| Litige sur l'ordre des bénéficiaires | L'ordre est **défini à l'avance** et appliqué automatiquement |
| Un membre ne paie pas | Le contrat peut **exclure** le membre défaillant |
| Aucune transparence | Chaque membre peut **vérifier** qui a payé et le montant collecté |

---

## 🛠️ Technologies utilisées

| Composant | Technologie | Version |
|-----------|-------------|---------|
| **Frontend** | Flutter (Dart) | 3.19+ |
| **Blockchain** | Celo Alfajores (testnet) | - |
| **Smart Contract** | Solidity | 0.8.0+ |
| **State Management** | Riverpod | 2.5+ |
| **Stockage sécurisé** | flutter_secure_storage | 9.0+ |
| **Stockage local** | Hive | 4.0+ |
| **Navigation** | GoRouter | 13.0+ |
| **QR Code** | mobile_scanner + qr_flutter | 4.0+ |
| **Stablecoin** | cUSD (Celo Dollar) | - |

---

## 📱 Fonctionnalités principales

### 🔐 Sécurité du wallet
- Création de wallet avec **PIN à 6 chiffres**
- Génération d'une **phrase de récupération (12 mots)**
- Validation par **confirmation de 3 mots aléatoires**
- Stockage chiffré via `flutter_secure_storage`

### 🏦 Gestion des tontines
- Création d'une tontine : nom, montant (cUSD), fréquence, liste des membres
- Définition de l'ordre des bénéficiaires
- Visualisation détaillée (tour actuel, bénéficiaire, montant collecté, progression)
- Paiement de cotisation en **cUSD**
- Libération **automatique** de la cagnotte au bénéficiaire
- Exclusion d'un **membre défaillant** (admin uniquement)

### 📷 Scanner QR Code
- Scanner l'adresse d'un membre pour l'ajouter
- Scanner une demande de paiement
- Générer son propre QR code pour être ajouté

### 🔔 Notifications
- Rappel quand c'est son tour de payer
- Alerte quand un membre paie
- Confirmation quand la cagnotte est libérée

## 📜 Smart Contract (Phase 3 - En cours de développement)

### État actuel

| Élément | Statut |
|---------|--------|
| Spécifications fonctionnelles | ✅ Complètes |
| Architecture du contrat | ✅ Définie |
| Code Solidity | ⚠️ **En cours d'écriture** |
| Déploiement sur Celo Alfajores | 📋 Planifié (Phase 3) |
| Tests sur testnet | 📋 Planifié (Phase 3) |

> **Note importante** : Le smart contract est la dernière pièce du puzzle. Conformément au cahier des charges du hackathon, le développement du contrat Solidity est prévu pour la **Phase 3** (Finale). Les Phases 1 et 2 (maquettes, site vitrine, application Flutter, wallet, QR code) sont entièrement fonctionnelles.

### Spécifications du futur smart contract

Voici les règles qui seront encodées dans le contrat Solidity sur **Celo Alfajores** :

| Règle | Description |
|-------|-------------|
| `montantCotisation` | Montant fixe en cUSD défini par le groupe |
| `frequence` | Périodicité (hebdomadaire / mensuelle) |
| `ordreBeneficiaires` | Ordre immuable des bénéficiaires |
| `payerCotisation()` | Vérifie que le membre existe et n'a pas déjà payé |
| `libererCagnotte()` | Transfère automatiquement la cagnotte au bénéficiaire |
| `exclureMembre()` | Permet au créateur d'exclure un membre défaillant |


## 📦 Installation

### Prérequis
- Téléphone Android 8.0 (API 27) ou supérieur
- Autorisation "Sources inconnues" activée (pour installer l'APK)

### Étapes d'installation

1. **Télécharger l'APK**  
   Le fichier `app-arm64-v8a-release.apk` est fourni dans la livraison

2. **Transférer sur le téléphone**  
   Via USB, Bluetooth ou transfert cloud

3. **Installer l'APK**  
   - Ouvrir le fichier APK
   - Autoriser "Installation depuis des sources inconnues" si demandé
   - Suivre les instructions

4. **Lancer l'application**  
   Ouvrir TontineChain depuis le lanceur d'applications

### Configuration blockchain (automatique)
- L'application communique avec le testnet **Celo Alfajores**
- Les transactions utilisent le stablecoin **cUSD** (valeur stable)
- Aucune configuration manuelle requise

---

## 🎮 Guide d'utilisation

### 1. Créer son wallet (premier lancement)

| Étape | Action |
|-------|--------|
| 1 | Choisir un **PIN à 6 chiffres** (ex: 123456) |
| 2 | Noter la **phrase de récupération** (12 mots) sur un papier |
| 3 | Confirmer 3 mots aléatoires de la phrase |
| 4 | Le wallet est créé et sécurisé |

> ⚠️ **Conservez précieusement votre phrase de récupération !** Elle est le seul moyen de restaurer votre wallet.

### 2. Créer une tontine

| Étape | Action |
|-------|--------|
| 1 | Depuis l'écran d'accueil, appuyer sur le bouton **+** |
| 2 | Remplir le formulaire : nom, montant (cUSD), fréquence |
| 3 | Ajouter les adresses des membres (via saisie ou QR code) |
| 4 | Définir l'ordre des bénéficiaires (manuel ou aléatoire) |
| 5 | Valider et attendre le déploiement du smart contract |

### 3. Payer sa cotisation

| Étape | Action |
|-------|--------|
| 1 | Ouvrir la tontine concernée |
| 2 | Vérifier le bénéficiaire et le montant |
| 3 | Appuyer sur **"Payer ma cotisation"** |
| 4 | Confirmer la transaction |
| 5 | La progression de la cagnotte se met à jour |

### 4. Gérer un incident (admin)

| Étape | Action |
|-------|--------|
| 1 | Si un membre ne paie pas, aller dans "Actions administrateur" |
| 2 | Sélectionner **"Exclure un membre"** |
| 3 | Choisir le membre défaillant |
| 4 | Confirmer : le membre est exclu et remboursé |

---

## 📂 Structure du projet

lib/
├── core/
│ ├── constants/ # Couleurs, constantes de l'application
│ ├── errors/ # Gestion des exceptions
│ ├── themes/ # Thèmes clair/sombre
│ └── utils/ # Formateurs, validateurs
│
├── features/
│ ├── auth/ # Wallet, PIN, seed phrase
│ ├── tontine/ # Création, paiement, détails
│ ├── scan/ # QR code (lecture/génération)
│ └── notification/ # Notifications push
│
├── di/ # Injection de dépendances (Riverpod)
├── main.dart
└── app.dart # Configuration de l'application


---

## 🖼️ Captures d'écran

| Écran | Description |
|-------|-------------|
| Wallet PIN | Création du code secret |
| Phrase secrète | 12 mots à sauvegarder |
| Confirmation | Vérification de la phrase |
| Tableau de bord | Liste des tontines et solde cUSD |
| Création tontine | Formulaire de nouvelle tontine |
| Détail tontine | Tour actuel, progression, membres |
| Paiement | Confirmation de cotisation |

---

## 🙏 Remerciements

- **Miabe Hackathon 2026** – Organisation et cadre du projet
- **Celo Blockchain** – Infrastructure blockchain et stablecoin cUSD
- **NOVATECH** – Support technique

---

## 📄 Licence

MIT © 2026 TontineChain

---

## 📞 Contact

Pour toute question ou suggestion :
- Téléphone : [0190569553]
