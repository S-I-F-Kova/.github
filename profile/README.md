# 💡 S-I-F-Kova — Écosystème d'Éclairage Adaptatif & Connecté

![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=flat-square)
![Hardware](https://img.shields.io/badge/Hardware-ESP32--C6%20%7C%20ESP--IDF-E7352C?style=flat-square&logo=espressif&logoColor=white)
![Connectivity](https://img.shields.io/badge/Mesh-BLE%20Mesh%20%7C%20Proxy%20GATT-0082FC?style=flat-square&logo=bluetooth&logoColor=white)
![Backend](https://img.shields.io/badge/Backend-Node.js%20%7C%20Drizzle%20%7C%20PostgreSQL-339933?style=flat-square&logo=node.js&logoColor=white)
![Auth](https://img.shields.io/badge/Auth-Firebase%20Admin-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![Mobile](https://img.shields.io/badge/Mobile-iOS%20%7C%20Android-000000?style=flat-square&logo=apple&logoColor=white)

## 🎯 Mission & Problème Résolu

**Kova** conçoit une nouvelle génération d'objets connectés et d'éclairage ambiant intelligent capables d'anticiper les besoins de l'utilisateur plutôt que d'attendre des commandes manuelles répétitives.

* **Le problème :** Les systèmes d'éclairage connecté actuels exigent une configuration complexe, dépendent souvent d'un hub propriétaire et obligent l'utilisateur à ouvrir constamment son téléphone pour changer l'ambiance.
* **La solution Kova :** Un écosystème *Plug-and-Play* combinant capteurs embarqués (présence, son, luminosité, gestes tactiles), contexte environnemental (heure, météo, saison) et apprentissage adaptatif sur 12 thèmes lumineux — fonctionnant aussi bien de manière autonome dès le déballage qu'en réseau maillé synchronisé via l'application mobile.

---

## 🗺️ Projets GitHub (`Kova 1.0.0`)

L'organisation s'articule autour de **4 tableaux GitHub Projects** pilotant le cycle de vie du produit, de l'idée initiale jusqu'à l'implémentation technique :

| Projet | Rôle & Périmètre |
| :--- | :--- |
| **[Kova 1.0.0 - Management](https://github.com/orgs/S-I-F-Kova/projects/2)** | **Hub Produit & Backlog :** Rédaction des User Stories (`[US]`), spécifications fonctionnelles, contrats d'interface partagés et triage avant dispatch. |
| **[Kova 1.0.0 - Infrastructure](https://github.com/orgs/S-I-F-Kova/projects/1)** | **Back-end & Cloud :** Microservices API, base de données PostgreSQL, authentification Firebase, moteur d'apprentissage contextuel, CDN et OTA. |
| **[Kova 1.0.0 - Device](https://github.com/orgs/S-I-F-Kova/projects/6)** | **Embarqué & Matériel :** Firmware commun ESP32-C6 (`Device Core`), réseau BLE Mesh / Proxy GATT, passerelle Wi-Fi, produits spécifiques (`Lamp`) et PCB. |
| **[Kova 1.0.0 - Mobile](https://github.com/orgs/S-I-F-Kova/projects/7)** | **Applications Clients :** Applications natives iOS et Android, onboarding QR/BLE, questionnaire initial, gestion des pièces et contrôle manuel. |

---

## 📦 Architecture des Dépôts

<details open>
<summary><strong>☁️ Infrastructure / API</strong> — <em>Services cloud, base de données, passerelle API, authentification et moteur d'apprentissage</em></summary>
<br>

| Dépôt | Description | Releases |
| :--- | :--- | :--- |
| **[`infrastructure`](https://github.com/S-I-F-Kova/infrastructure)** *(Main)* | Point d'entrée principal de l'infrastructure, orchestration Docker/Nginx Gateway et suivi des tâches techniques globales. | [Releases](https://github.com/S-I-F-Kova/infrastructure/releases) |
| **[`authenticationMS`](https://github.com/S-I-F-Kova/authenticationMS)** | Microservice de gestion des sessions, validation des jetons Firebase Admin SDK et injection des *Custom Claims*. | [Releases](https://github.com/S-I-F-Kova/authenticationMS/releases) |
| **[`ProfileMS`](https://github.com/S-I-F-Kova/ProfileMS)** | Microservice de gestion des profils utilisateurs, préférences initiales (archétypes) et localisation géographique. | [Releases](https://github.com/S-I-F-Kova/ProfileMS/releases) |
| **[`DB`](https://github.com/S-I-F-Kova/DB)** | Configuration PostgreSQL, isolation des schémas (`auth`, `user_domain`) et migrations Drizzle ORM. | [Releases](https://github.com/S-I-F-Kova/DB/releases) |
| **[`Middleware`](https://github.com/S-I-F-Kova/Middleware)** | Package partagé de validation JWT, contrôle d'accès, gestion d'erreurs normalisées et validation Zod. | [Releases](https://github.com/S-I-F-Kova/Middleware/releases) |

</details>

<details>
<summary><strong>💡 Device</strong> — <em>Noyau firmware embarqué ESP32-C6, réseau BLE Mesh, capteurs et déclinaisons produits</em></summary>
<br>

| Dépôt | Description | Releases |
| :--- | :--- | :--- |
| **[`Device`](https://github.com/S-I-F-Kova/kova-device-core)** *(Main)* | Socle firmware commun (`Device Core`) : stack BLE Mesh, Proxy GATT, élection de passerelle Wi-Fi, stockage NVS, bus d'événements et client OTA. | [Releases](https://github.com/S-I-F-Kova/Device/releases) |
| **[`Lamp`](https://github.com/S-I-F-Kova/Lamp)** | Implémentation produit de la lampe adaptative Kova : moteur de rendu des 12 thèmes LED, reconnaissance des gestes tactiles et capteurs ambiants. | [Releases](https://github.com/S-I-F-Kova/Lamp/releases) |

</details>

<details>
<summary><strong>📱 Mobile</strong> — <em>Applications mobiles iOS et Android pour l'appairage, la personnalisation et le contrôle</em></summary>
<br>

| Dépôt | Description | Releases |
| :--- | :--- | :--- |
| **[`Mobile-main`](https://github.com/S-I-F-Kova/kova-mobile-main)** *(Main)* | Dépôt central de coordination mobile, architecture partagée et suivi des fonctionnalités transversales iOS / Android. | [Releases](https://github.com/S-I-F-Kova/Mobile-main/releases) |
| **[`kova-mobile-ios`](https://github.com/S-I-F-Kova/kova-mobile-ios)** | Application native iOS (Swift / SwiftUI), intégration CoreBluetooth (BLE Mesh Proxy), CoreLocation et Sign in with Apple. | [Releases](https://github.com/S-I-F-Kova/kova-mobile-ios/releases) |
| **[`kova-mobile-android`](https://github.com/S-I-F-Kova/kova-mobile-android)** | Application native Android (Kotlin), gestion BLE Mesh, permissions de localisation et authentification multi-providers. | [Releases](https://github.com/S-I-F-Kova/kova-mobile-android/releases) |

</details>

---

## 📋 Conventions & Workflow Agile (`[US]` & `[TECH]`)

Toutes les évolutions fonctionnelles et techniques de l'organisation suivent une nomenclature strictement normalisée entre **[`kova-management`](https://github.com/S-I-F-Kova/kova-management)** et les dépôts d'exécution :

### 1. User Stories — `[US]`
* **Où :** Créées exclusivement dans [`kova-management`](https://github.com/S-I-F-Kova/kova-management) via le formulaire `.github/ISSUE_TEMPLATE/user-story.yml` et pilotées dans **Kova 1.0.0 - Management**.
* **Format :** Titre en anglais préfixé par `[US]` (ex. : `[US] Profile & Location Update`), description fonctionnelle en français, énoncé (*En tant que / Je veux / Afin de*), diagramme de flux **Mermaid** et critères d'acceptation **Gherkin** (*Happy Path* & *Edge Case*).

### 2. Tâches Techniques — `[TECH]`
* **Où :** Créées dans les dépôts principaux (`infrastructure`, `Device`, `Mobile-main`) via `.github/ISSUE_TEMPLATE/issue.yml`, puis découpées en *Sub-issues* vers les dépôts spécialisés.
* **Format :** Titre en anglais préfixé par `[TECH]` (ex. : `[TECH] Implement profile and location update endpoint`), référence à la User Story mère (`#ID`), objectif technique, liste d'implémentation (`- [ ] **Repo/Ressource** : Action`) et scénarios de validation technique.
