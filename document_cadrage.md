# Document de cadrage — Cabinet Maître Devalle (Bordeaux, 12 avocats)

> Sources : entretien du 06/10/2026 avec Maître Élise Devalle (réponses notées Qn,
> voir `notes_entretien.md`) et extrait du registre des décisions
> (`data/Rendez-vous client décisions.csv`).

## 1. Synthèse exécutive (5-6 lignes — rédigée EN DERNIER)
_Besoin réel + solution proposée (famille, pas la stack) + 2-3 indicateurs clés._

> **Imprévu client (14h30) — ce que ça change** : le prestataire informatique quitte
> le cabinet au 31/12, et **plus personne ne maintiendra le serveur**. L'outil ne doit
> donc **rien héberger au cabinet** : il sera hébergé et maintenu chez un hébergeur
> français, et **les décisions doivent être copiées et sauvegardées avant le 31/12**.
> Mis à jour : §2 (contrainte), §3 (décisions), §4 (nouveau risque 🔴, droits, sécurité),
> §5 et schéma (hébergement), §6 (étape urgente, questions).

## 2. Besoin métier et contexte

**Demande exprimée** : « un assistant pour aller plus vite » sur les courriers
types, et « retrouver les bonnes jurisprudences en 30 secondes au lieu de 30 minutes ».
**Besoin réel** : le cabinet n'exploite pas ce qu'il a déjà produit. « Notre vraie
richesse, ce sont nos propres dossiers » (Q12). Ses décisions sont sur un serveur
et se retrouvent « par nom de fichier… ou on demande au collègue qui s'en souvient ».
Les courriers sont recopiés à partir d'anciens courriers, et le dossier de modèles
date de 2019 (Q3). **Priorité 1** : retrouver ses propres décisions (environ 10
recherches par jour × 30 min, soit environ 5 h par jour pour le cabinet, Q4).
**Priorité 2** : produire plus vite les courriers types (environ 15 par jour, Q4).
La jurisprudence publique est déjà couverte par un abonnement : elle est **hors
périmètre** (Q12). **Contraintes** : périmètre recouvrement et baux commerciaux,
droit de la famille exclu, jugé « trop sensible » (Q1) ; **aucune information
invérifiable** (« tout doit être vérifiable », Q7) ; pas de cloud américain, un
hébergeur français sous contrat est accepté (Q10) ; budget de 15 k€ puis quelques
centaines d'euros par mois (Q8) ; un avocat relit et signe tout courrier (Q3) ;
**plus de prestataire informatique après le 31/12** (imprévu), donc aucune
maintenance possible côté cabinet.

**Objectif à recalibrer.** La cliente vise « une heure par avocat et par jour » (Q9),
soit **12 h par jour** pour le cabinet. La recherche peut en rapporter environ
**4 h 50** (10 × 30 min aujourd'hui → 10 × 1 min). Il faudrait donc gagner environ
**7 h 10 sur 15 courriers, soit environ 29 min par courrier**, ce qui suppose qu'un
courrier prenne aujourd'hui plus de 30 min et 0 avec l'outil. C'est peu réaliste
pour des textes qui « se ressemblent tous » (Q1), d'autant que ce sont les
assistantes qui les préparent (Q3). **Objectif proposé : environ 5 à 6 h gagnées
par jour pour le cabinet** (environ 25-30 min par avocat), à confirmer une fois
mesurée la durée actuelle d'un courrier (question ouverte §6).

## 3. Données

| Donnée | Existante / à acquérir | Volume, qualité estimée | Personnelle ? |
|---|---|---|---|
| Décisions obtenues par le cabinet | Existante (serveur de fichiers, **sans maintenance après le 31/12** → copie à faire avant) | Environ 2 000 sur 15 ans ; PDF, Word, et **scans anciens peu lisibles** (Q5) → OCR nécessaire, qualité 🟠 | Oui : parties, adversaires, parfois situation financière |
| Registre des décisions (n°, date, matière, juridiction, issue, fichier) | Existante (tenu par une assistante) | Extrait de 20 lignes ; **métadonnées déjà structurées = filtres prêts** ; qualité 🟠 (voir constats) | Non dans l'extrait |
| Anciens courriers | Existante (dans les dossiers clients) | « Des milliers » (Q5), **non classés par type**, éparpillés sur les postes | Oui : débiteurs, montants |
| Modèles de courriers | Existante mais **obsolète** | Dossier partagé de 2019, jamais mis à jour ; **aucun modèle de mise en demeure** disponible | Non |
| Données de dossier (débiteur, montant, échéances) | Existante (logiciel de gestion hébergé en France, Q11) | Structurée ; **accès par export ou API inconnu** | Oui |
| Modèles de courriers validés | **À acquérir** (à reconstituer avec un avocat référent) | 5 à 10 modèles pour couvrir l'essentiel (hypothèse) | Non |
| Jeu de recherches réelles (question → bonne décision) | **À acquérir** (atelier avec 2-3 avocats) | Environ 30 cas, qui servent de jeu de test aux KPI | Non |

**Constats sur l'extrait du registre (20 lignes)** :
1. **5 lignes sur 20 sont en droit de la famille**, alors que la cliente veut l'exclure. Il faut un filtre dès l'entrée.
2. Les **20 décisions sont attribuées au « TJ Bordeaux »**, y compris les prud'hommes (qui relèvent normalement du Conseil de prud'hommes). La saisie est approximative, et le filtre par juridiction n'est pas fiable en l'état.
3. Les dates vont de **2020 à 2025** et tous les fichiers sont en `.pdf`, alors que la cliente parle de 15 ans d'archive en PDF, Word et scans : l'exhaustivité du registre est à vérifier.

**Labels** : le registre fournit matière et issue, ce qui suffit pour **filtrer**. En
revanche, **rien n'indique le sujet juridique** traité dans chaque décision : la
recherche par argument (« clause résolutoire ») nécessite d'indexer le **texte**
des décisions.

## 4. Risques et conformité

**Usage réel** : un avocat ou une assistante tape une recherche et obtient une
**liste de décisions du cabinet avec un lien vers le document original**. Il les
lit lui-même avant de s'en servir. Pour les courriers, l'outil pré-remplit un
modèle validé, que l'avocat relit et signe. L'outil ne prend **aucune décision** :
il retrouve et pré-remplit, et l'avocat peut toujours ignorer le résultat.

**Qualification AI Act** : **pas de haut risque, aucune obligation spécifique**
(seule s'applique la maîtrise de l'IA par les équipes, art. 4). L'Annexe III, point 8 a,
vise l'IA utilisée **par une autorité judiciaire** ou en son nom pour rechercher et
interpréter les faits et le droit. Un cabinet d'avocats n'en est pas une, et l'outil
n'aide pas à décider d'un litige. Il n'y a pas non plus d'obligation de transparence
(art. 50) : pas de chatbot face au public, pas de contenu généré au lot 1.
**Conditions de bascule** : (1) l'outil est mis à disposition d'une juridiction, ou il
**prédit l'issue d'un litige** pour orienter une décision → à requalifier au regard
de l'Annexe III 8 a ; (2) le champ « issue » sert à **évaluer les performances des
avocats** → Annexe III 4 b (gestion des travailleurs), haut risque ; (3) un LLM
**génère du texte** → obligations de transparence (art. 50) et nouvelle analyse.

**RGPD** : le cabinet est **responsable de traitement**. **Base légale proposée :
intérêt légitime (art. 6.1.f)**, à savoir l'intérêt du cabinet à réutiliser sa propre
production pour mieux défendre ses clients. Le consentement est écarté (impossible à
recueillir auprès des parties adverses), tout comme le contrat (les adversaires n'ont
aucun contrat avec le cabinet). La mise en balance tient pour plusieurs raisons :
les données sont déjà détenues légalement, l'usage est interne et couvert par le
secret professionnel, et les données sont minimisées (droit de la famille exclu,
accès restreint). Cette mise en balance doit être **documentée**, et la réutilisation
jugée **compatible** avec la finalité d'origine (art. 6.4). L'information des
personnes peut être écartée au titre de l'art. 14.5 d (secret professionnel).
L'hébergeur est un **sous-traitant** et doit signer un contrat art. 28.
**Profilage** : non, aucune personne n'est évaluée (sauf dans la bascule 2).
**Art. 22** : non applicable, car aucune décision n'est **exclusivement automatisée**
(l'avocat lit et signe), et il n'y a pas d'effet juridique produit par l'outil.

| Risque (éthique, métier, conformité) | 🔴/🟠/🟡 | Obligation ou raison | Traitement dans l'archi |
|---|---|---|---|
| Décision ou jurisprudence **inventée** | 🔴 | Responsabilité professionnelle (Q7) | **Pas de génération** au lot 1 : chaque résultat est un **lien vers un document réel** du serveur |
| Erreur de montant ou de délai dans un courrier | 🔴 | Responsabilité professionnelle (Q7) | Champs remplis **depuis le logiciel de gestion**, pas saisis ni générés ; relecture et signature de l'avocat obligatoires |
| Données hors de France / cloud US | 🔴 | Secret professionnel, exigence client (Q10) | Outil et index hébergés **chez un hébergeur français** sous contrat art. 28 ; aucun appel à une API étrangère |
| **Serveur du cabinet sans maintenance après le 31/12** : panne, perte de l'archive, failles non corrigées | 🔴 | Continuité du cabinet ; sécurité des dossiers (imprévu) | **Copie des décisions vers l'hébergeur avant le 31/12**, avec sauvegarde ; l'outil **ne dépend plus du serveur** |
| Décisions de droit de la famille indexées par erreur | 🟠 | Exclusion demandée (Q1), données sensibles | **Filtre `matiere ≠ famille`** à l'indexation et contrôle d'un échantillon |
| Accès d'un collaborateur à des dossiers qui ne le concernent pas | 🟠 | Secret professionnel, conflits d'intérêts | **Comptes nominatifs** gérés dans l'outil par un référent du cabinet (plus de droits hérités du serveur) ; journal des consultations |
| Décision introuvable (scan illisible) | 🟠 | Fausse impression d'exhaustivité | Score de qualité OCR ; liste des documents non indexables, à re-numériser |
| Registre erroné (juridiction, dates) | 🟡 | Filtres trompeurs | Audit du registre avant import ; recherche plein texte en complément des filtres |
| Usage détourné du champ « issue » pour noter les avocats | 🟡 | Bascule haut risque (Annexe III 4 b) | Aucune statistique par avocat dans l'outil |

**Sécurité du modèle** — exposition : **outil interne**, pas d'API publique, pas
de réentraînement sur les retours des utilisateurs, **pas de LLM au lot 1**.

| Menace | Plausibilité sur CE cas | Mitigation proposée | Risque résiduel |
|---|---|---|---|
| **Fuite / exfiltration** via le moteur (extraction massive de décisions) | 🟠 L'outil concentre 15 ans de dossiers confidentiels en un seul point de recherche | Comptes nominatifs, **limitation du nombre d'ouvertures et d'exports**, alerte sur volume anormal | Un collaborateur autorisé et mal intentionné |
| **Empoisonnement de l'index** (document piégé ou mal classé) | 🟡 Le serveur n'est plus administré, donc ce qui s'y dépose n'est plus contrôlé | Après la copie initiale, **ajout de décisions uniquement par l'assistante** qui tient le registre | Erreur de classement non repérée |
| Prompt injection | ⚪ Sans objet au lot 1 (pas de LLM). **Devient 🟠 si un LLM est ajouté** : des conclusions adverses indexées pourraient contenir des instructions cachées (injection indirecte) | — | — |
| Adversarial example / vol de modèle | ⚪ Aucun attaquant ne soumet d'entrée, aucun modèle entraîné sur les données du cabinet | — | — |

## 5. Architecture cible et sobriété

Schéma détaillé : `schema_archi_cible.md`. Le projet se fait en **deux lots, hébergés
et maintenus chez un hébergeur français** : rien n'est installé sur le serveur du
cabinet, qui ne sera plus maintenu après le 31/12. Les décisions y sont copiées une fois.
**Lot 1** : un **moteur de recherche interne** sur les décisions du cabinet.
L'ingestion filtre le droit de la famille, l'OCR traite les scans, l'index combine
le texte et les filtres du registre, et chaque résultat est un lien vers l'original.
**Lot 2** : des **modèles de courriers validés**, pré-remplis depuis le logiciel de
gestion, puis relus et signés par l'avocat.

**LLM refusé.** La cliente ne tolère aucune information invérifiable (Q7) : un moteur
de recherche renvoie des documents réels, un LLM peut en inventer. Les courriers
types, eux, n'ont besoin que de modèles et de champs déjà présents dans le logiciel de gestion.
**Écartés** : RAG et base vectorielle (la recherche sémantique n'est envisagée que
si le jeu de test montre que la recherche plein texte rate trop de décisions),
jurisprudence publique (déjà couverte, Q12), réentraînement, statistiques par avocat.

## 6. Indicateurs, seuils, questions ouvertes

| Indicateur | Départ → cible | Seuil d'acceptabilité | Comment on le mesure |
|---|---|---|---|
| Temps pour retrouver une décision | 30 min → **< 1 min** (Q9) | ≤ 3 min (le gain reste d'environ 4 h 30 par jour) | Chronométrage sur le jeu de 30 recherches réelles, puis suivi dans le journal |
| **Rappel** : part des recherches où la bonne décision apparaît dans les 10 premiers résultats | — → **≥ 90 %** | ≥ 80 % : en dessous, les avocats reviennent à « demander au collègue ». L'erreur est récupérable, d'où un seuil souple | Jeu de test (question → décision attendue) |
| Décision ou référence **inventée** | — → **0** | **0** : l'erreur est critique, car elle engage la responsabilité professionnelle (Q7) | Garanti par l'architecture (liens vers les originaux) ; contrôle mensuel d'un échantillon |
| Courriers pré-remplis avec une erreur de montant ou de délai | — → **0 envoyé** ; < 2 % corrigés à la relecture | 0 courrier envoyé avec une erreur | L'avocat signale chaque correction à la relecture ; le journal compte |
| Temps gagné par le cabinet | 0 → **5 à 6 h par jour** (objectif recalibré, §2) | ≥ 4 h par jour (le gain de la recherche seule) | (durée de référence − durée mesurée) × volumes quotidiens (Q4) |

**Prochaines étapes** :
0. **Urgent, avant le 31/12** : copier et sauvegarder les décisions du serveur chez l'hébergeur retenu, indépendamment du reste du projet.
1. **Atelier de 2 h avec 2-3 avocats** : recueillir 30 recherches réelles (le jeu de test) et chronométrer les courriers pendant une semaine.
2. **Préparer les données et le cadre** : audit du registre complet, comptage des scans illisibles, choix d'un hébergeur français (contrat art. 28), mise en balance RGPD documentée.
3. **POC du lot 1** sur le recouvrement et les baux commerciaux, mesuré sur le jeu de test → décision de continuer ou d'arrêter avant le lot 2.

**Questions ouvertes** :
- **Durée actuelle d'un courrier type** (non demandée) : elle conditionne l'objectif global (§2).
- **Répartition du temps entre assistantes et avocats** pour les recherches et les courriers.
- Le registre couvre-t-il toute l'archive ? L'extrait va de 2020 à 2025, alors que l'archive porte sur 15 ans. Quelle part de scans illisibles ?
- Le logiciel de gestion permet-il un **export ou un accès par API** (débiteur, montant, échéance) ?
- Qui valide les modèles de référence ? Où sont localisées les données Microsoft 365 ? Quel délai ?
- **Imprévu** : existe-t-il une sauvegarde à jour du serveur ? Qui sera le référent interne (comptes, droits) en attendant le nouveau prestataire ? L'hébergement infogéré reste-t-il dans « quelques centaines d'euros par mois » ?
