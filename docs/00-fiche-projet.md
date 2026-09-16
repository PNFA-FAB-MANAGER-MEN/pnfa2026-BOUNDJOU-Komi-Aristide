# Fiche projet — Groupe 11
Membres : 
* BOUNDJOU Komi Aristide
* AKATA Richard
* ABALO Honorine
* KASSA Kodjo
---

> **Livrable L2 · Jalon J1 (samedi 29 août 2026)** · validée par l'encadreur référent.  

## 1. Titre et accroche
* **Nom du dispositif :** **Mini Robot QCM**
* **Phrase de présentation :** il s'agit d'un compagnon robotique interactif et autonome qui dynamise l'apprentissage par le jeu de quiz vocal et visuel, favorisant l'engagement direct des élèves en classe.

## 2. Besoin et bénéficiaires
* **Difficulté d'apprentissage visée :** Rendre l'évaluation formative plus ludique, réduire l'anxiété liée aux notes et stimuler la mémorisation active des notions.
* **Élèves concernés :** tout élève de tout niveau et à toute discipline pouvant necessité une revision ou évaluation par QCM
* **Établissement d'accueil :** Établissement scolaire

## 3. Objectifs d'apprentissage
Trois objectifs observables rattachés au programme officiel :
1. Restituer et identifier correctement les notions à partir de questions interactives.
2. Analyser un énoncé oral ou textuel et sélectionner la bonne réponse parmi quatre propositions en temps limité.
3. Auto-évaluer ses connaissances grâce aux feedbacks audio et visuels immédiats du robot (succès/erreur).

## 4. Description du dispositif
* **Ce que l'objet fait :** Le robot lit dynamiquement un fichier de quiz, énonce les questions par synthèse vocale (fichiers MP3 sur carte SD), affiche le texte et le score sur un écran OLED, anime sa tête via un servomoteur et évalue les réponses des élèves transmises par quatre boutons physiques (A, B, C, D).
* **Ce que l'élève fait avec :** L'élève écoute ou lit la question posée par le Robot, analyse les propositions, et valide sa réponse en appuyant physiquement sur l'un des boutons de couleur (A, B, C ou D) situés sur le socle, puis prend connaissance du retour immédiat.
* **Croquis ou esquisse :** Versé dans `docs/medias/`.

## 5. Architecture technique pressentie
* **Capteurs :** Boutons poussoirs (A, B, C, D, retour, next) en entrées logiques, potentiomètre rotatif analogique (réglage du volume).
* **Actionneurs :** Haut-parleur 3W (audio), Servomoteur SG90 (orientation de la tête), Écran OLED SSD1306 (affichage visuel).
* **Liaison :** Protocole SPI (carte micro-SD), Protocole I2C (écran OLED), Bus I2S (flux audio numérique vers l'ampli MAX98357A).
* **Application :** Microcontrôleur ESP32 programmé en C++ (IDE Arduino) avec une architecture en machine à états. 
* **Procédés de fabrication envisagés (au moins trois distincts) :**
  1. Impression 3D (FDM) pour la fabrication de la coque en PLA (corps et tête).
  2. Soudure de composants électroniques sur plaque à bandes (PCB / perfboard) pour le circuit d'alimentation et d'interfaçage.
  3. Assemblage mécanique et ajustement de précision pour l'intégration de la visserie, des boutons et de l'axe du servomoteur.

## 6. Rôle des élèves
* **Position sur le continuum :** **PAR** (Conception et fabrication complète du dispositif par les élèves dans le cadre du projet FabLab).
* **Extension PAR décrite :** Les élèves concepteurs fabriquent l'objet de A à Z (modélisation CAO, impression 3D, câblage électronique, code ESP32, génération des questionnaires via Python) puis le déploient et l'expérimentent en situation réelle auprès de leurs pairs.

## 7. Ancrage réseau et implantation
* **Lab de rattachement :** FabLab / CRIT.
* **Lieu d'usage :** Salles de classe ou maison pour usage personnel.
* **Conditions matérielles de la salle :** Autonomie assurée par batterie Li-Ion (fonctionnement sans fil sur table), éclairage standard, niveau sonore modéré gérable via le potentiomètre de volume intégré.

## 8. Périmètre
| Contenu |
|---|
| **Dans la v1.0 (Socle)** | Socle fixe, 4 boutons de réponse (A, B, C, D), lecteur carte SD unique, amplificateur I2S + haut-parleur, écran OLED 0.96", tête orientable par servomoteur, réglage du volume par potentiomètre, alimentation sur batterie 18650 avec recharge USB-C. |
| **En option (Avancé / Expert)** | Configuration des quiz en Wi-Fi (serveur web embarqué sur l'ESP32 pour mettre à jour les JSON et MP3 sans démonter la carte SD). |
| **Explicitement exclu** | Déplacement autonome du robot sur roulettes dans la pièce (maintien d'un corps fixe pour garantir la stabilité lors des votes). |

## 9. Risques et parades
| Risque | Type | Parade |
|---|---|---|
| Retard dans l'impression 3D des pièces complexes ou assemblage bloqué. | calendrier | Réalisation d'une impression test simplifiée en mode "brouillon" dès le début du jalon et modularité de la coque en deux parties. |
| Les élèves appuient trop brutalement sur les boutons ou déséquilibrent le robot. | pédagogique | Conception d'un corps trapézoïdal large assurant une stabilité maximale sur la table. |

## 10. Budget matière estimé
* **Grandes masses en FCFA (Plafond indicatif : 50 000 FCFA) :**
  * Microcontrôleur ESP32 + Carte SD + Module SD : ~ 6 500 FCFA
  * Électronique Audio (Ampli I2S + HP 3W) : ~ 3 500 FCFA
  * Électronique Énergie (Batterie 18650, Support, TP4056, Boost 5V, Interrupteur) : ~ 4 500 FCFA
  * Interface et Animation (4 boutons, Servomoteur SG90, Écran OLED, Potentiomètre) : ~ 5 500 FCFA
  * Consommables (Filament PLA, câblage, visserie, plaque à souder) : ~ 6 000 FCFA
  * **Total estimé : ~ 26 000 FCFA** (Inférieur au plafond de 60 000 FCFA).

## 11. Licences et diffusion
* **Licences choisies et motivation :** Licence Creative Commons Attribution-ShareAlike (CC BY-SA) pour le design 3D et le matériel, et Licence MIT pour le code source logiciel. Permet à la communauté éducative et aux autres FabLabs de réutiliser et améliorer le robot librement.
* **Accord de l'équipe :** Oui, accord total de l'équipe pour la mise en avant réseau.

## Exemptions demandées
- [ ] ET-FAB-06 (moulage) — justification : *Non concerné.*
- [ ] ET-MEC-01 (fonction motorisée) — justification : *Le projet intègre une fonction motorisée simple et maîtrisée (servomoteur SG90 pour l'orientation de la tête) sans nécessiter d'exemption particulière.*