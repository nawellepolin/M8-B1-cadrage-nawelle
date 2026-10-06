# Notes d'entretien — Cas A : Cabinet Maître Devalle (Bordeaux, 12 avocats)

> Mini-cours `01`. Ce fichier sert d'abord à **toi** ; il est aussi lu pour
> évaluer ta préparation.

**Ce que dit déjà le briefing** (ne pas reposer) : 12 avocats, Bordeaux,
interlocutrice Maître Élise Devalle. Demande : un assistant pour rédiger plus vite
les courriers types (mise en demeure, transmission de dossier) et pour retrouver
une jurisprudence « en 30 s au lieu de 30 min ».

## 1. Avant le rendez-vous — 12 questions + 3 de réserve

> Le client accorde **12 réponses**. **Une question à la fois**. Classe par
> priorité : si tu n'en poses que 8, ce doivent être les 8 plus utiles.

| # | Priorité (1-3) | Catégorie | Question | Ce que je cherche à savoir |
|---|---|---|---|---|
| 1 | 1 | Besoin | Qu'est-ce qui vous a décidée à lancer ce projet maintenant ? | Le besoin réel derrière « aller plus vite » (surcharge, délais ratés, temps non facturable…) |
| 2 | 1 | Besoin | Si l'outil ne devait traiter qu'un seul des deux sujets au départ, les courriers ou la jurisprudence, lequel choisiriez-vous ? | Le périmètre prioritaire ; oriente Q3, Q5 et Q6 (voir variantes plus bas) |
| 3 | 1 | Processus actuel | Pouvez-vous me décrire, étape par étape, comment une mise en demeure est rédigée aujourd'hui au cabinet ? | Qui rédige, à partir de quoi, où se perd le temps |
| 4 | 1 | Critère de succès | À peu près combien de courriers types le cabinet envoie-t-il par semaine ? | La fréquence, pour chiffrer le gain (estimation client, à vérifier) |
| 5 | 1 | Données (volume labellisé — question imposée) | Combien d'anciens courriers avez-vous conservés, et sont-ils classés par type (mise en demeure, transmission…) ? | Existence, volume et étiquetage des données ; conditionne le choix ML/DL en M8-B2 |
| 6 | 1 | Données (extrait) | Pourriez-vous m'envoyer un exemple de courrier que vous jugez réussi, anonymisé ? | La qualité et le format réels ; ce qui varie d'un dossier à l'autre |
| 7 | 1 | Critère de succès | Dans six mois, qu'est-ce qui vous ferait dire que le projet est réussi ? | Un critère chiffrable (relancer : « combien de temps gagné ? ») |
| 8 | 2 | Coût d'une erreur | Que se passerait-il si un courrier partait avec une erreur, par exemple un mauvais délai ou un mauvais montant ? | La gravité d'une erreur, donc le niveau de contrôle humain nécessaire |
| 9 | 2 | Données personnelles / confidentialité | Quelles informations sur vos clients figurent dans ces courriers ? | Les catégories de données (santé, pénal, famille ?), le secret professionnel, la minimisation |
| 10 | 2 | Utilisateurs / validation | Qui relit et signe un courrier avant qu'il parte ? | La validation humaine, qui est responsable |
| 11 | 2 | SI / hébergement | Où sont stockés vos dossiers clients aujourd'hui : sur un serveur au cabinet ou dans un logiciel en ligne ? | Les contraintes d'hébergement et d'intégration (secret professionnel) |
| 12 | 3 | Budget | Quel budget envisagez-vous pour ce projet ? | L'ordre de grandeur, qui conditionne l'architecture et la sobriété |
| R1 | réserve | Processus actuel (jurisprudence) | Où cherchez-vous vos jurisprudences aujourd'hui ? | Les outils et abonnements existants (bases payantes ?), le point de départ du gain de 30 min |
| R2 | réserve | Délai | Pour quand aimeriez-vous que l'outil soit utilisable ? | La contrainte de calendrier |
| R3 | réserve | Déjà essayé | Avez-vous déjà essayé un outil ou une méthode pour gagner du temps sur ces tâches ? | Les échecs passés et les attentes implicites |

**Variantes si Q2 = jurisprudence** (remplacer Q3, Q5 et Q6) :
- Q3 → « Pouvez-vous me raconter votre dernière recherche de jurisprudence, de la question de départ au résultat ? »
- Q5 → « Gardez-vous une trace des jurisprudences que vous avez déjà trouvées et utilisées, et combien environ ? »
- Q6 → « Pourriez-vous m'envoyer un exemple de recherche : la question posée et la décision retenue ? »
- Q4 → passer R1 en priorité 1.

**Relance type** : « Pouvez-vous me donner un exemple concret ? »

## 2. Pendant le rendez-vous — dit / interprété

| # | Question posée (telle quelle) | Ce que le client a **dit** (citation) | Ce que j'en **interprète** |
|---|---|---|---|
| 1 | Qu'est-ce qui vous a décidée à lancer ce projet maintenant ? | « Le recouvrement et les baux commerciaux : c'est le gros de notre activité, et les courriers se ressemblent tous. Le droit de la famille, je préfère attendre : c'est trop sensible pour un premier essai. » | Pas de déclencheur donné, mais le **périmètre** est clair : recouvrement et baux commerciaux. Le droit de la famille est **exclu par la cliente** pour cause de sensibilité (→ §4). |
| 2 | Si l'outil ne devait traiter qu'un seul des deux sujets au départ, les courriers ou la jurisprudence, lequel choisiriez-vous ? | « Deux choses. D'abord les courriers types […] on les réécrit à partir d'anciens courriers, c'est du temps perdu. Ensuite, et c'est le plus pénible, retrouver une décision qu'on a déjà obtenue ou étudiée : trente minutes pour ce qui devrait en prendre trente secondes. » | Pas de choix, mais la recherche est « le plus pénible ». **Point clé** : il s'agit de retrouver des décisions **déjà obtenues ou étudiées par le cabinet**, donc de chercher dans **l'archive interne**, pas dans toute la jurisprudence. |
| 2 bis (relance) | Si vous ne deviez en garder qu'un : les courriers types ou la recherche de décisions ? | Réponse identique à la Q2. | La cliente refuse de choisir : **les deux sujets restent dans le périmètre**. La phrase « le plus pénible » et les volumes de la Q4 orientent vers la recherche en priorité. _Relance car pas de choix explicite à la Q2._ |
| 3 | Pouvez-vous me décrire, étape par étape, comment une mise en demeure est rédigée aujourd'hui au cabinet ? | « Chaque avocat a ses vieux courriers sur son poste, et on copie-colle. Il y a bien un dossier "modèles" partagé, mais il date de 2019 et personne ne le met à jour. Les assistantes préparent, l'avocat relit et signe. » | Pas de référentiel à jour : les données sont **dispersées sur les postes**. Utilisateurs : les **assistantes** (préparation) et les **avocats** (validation). La validation humaine existe déjà, il faut la conserver. |
| 4 | À peu près combien de courriers types le cabinet envoie-t-il par semaine ? | « Pour tout le cabinet, une quinzaine de courriers types par jour, et une dizaine de recherches de jurisprudence interne par jour. C'est surtout la recherche qui prend du temps. » | Environ 15 courriers par jour et environ 10 recherches par jour. À 30 min par recherche, ça fait **environ 5 h par jour** pour tout le cabinet (estimation client). La recherche est confirmée comme priorité. |
| 5 | Combien d'anciens courriers avez-vous conservés, et sont-ils classés par type (mise en demeure, transmission…) ? | « Environ 2 000 décisions sur les quinze dernières années, en PDF ou en Word, plus des milliers de courriers archivés dans les dossiers clients. Les plus anciennes décisions sont des scans papier, pas toujours très lisibles. » | Il y a 2 000 décisions (PDF, Word, scans) : c'est un volume modeste, et les scans anciens imposent un **OCR de qualité incertaine**. Les courriers sont **non classés** et noyés dans les dossiers clients. |
| 6 | Pourriez-vous m'envoyer un exemple de courrier que vous jugez réussi, anonymisé ? | « Une assistante tient un registre des décisions : numéro, date, matière, juridiction, issue, et le nom du fichier. Je vous en transmets un extrait, seulement le registre, pas les décisions elles-mêmes, vous comprendrez pourquoi. » (fichier transmis) | J'ai reçu le **registre**, pas un courrier. Il donne des **métadonnées déjà structurées** (matière, juridiction, issue) qui sont utiles pour filtrer la recherche. Le refus d'envoyer les décisions montre une **forte sensibilité à la confidentialité**. → Télécharger et analyser le fichier. |
| 7 | Que se passerait-il si un courrier partait avec une erreur, par exemple un mauvais délai ou un mauvais montant ? | « Une erreur dans un courrier ou une jurisprudence qui n'existe pas, c'est ma responsabilité professionnelle engagée. J'ai lu cette histoire d'avocats américains qui ont cité des décisions inventées par une IA. Ça, jamais chez nous. Tout doit être vérifiable. » | **Zéro tolérance pour l'invention.** Chaque résultat doit renvoyer à un **document source réel** du cabinet. Il faut privilégier la recherche ou l'extraction plutôt que la génération libre. Le risque d'hallucination est 🔴. |
| 8 | Quel budget envisagez-vous pour ce projet ? | « Serré. […] Mettons 15 000 euros pour démarrer, et ensuite un abonnement mensuel raisonnable, pas plus de quelques centaines d'euros par mois. » | **15 k€ pour démarrer** et **quelques centaines d'euros par mois** ensuite : c'est un argument pour une solution sobre et sur étagère. |
| 9 | Dans six mois, qu'est-ce qui vous ferait dire que le projet est réussi ? | « Si chaque avocat gagne une heure par jour sans prendre le moindre risque déontologique, je signe tout de suite. Et pour la recherche : retrouver la bonne décision en moins d'une minute. » | KPI : **1 h gagnée par avocat et par jour**, **recherche en moins d'1 min**, **0 incident déontologique**. L'objectif d'1 h par avocat (12 h par jour) semble ambitieux face aux environ 5 h de recherche estimées → à challenger. |
| 10 | Vos documents peuvent-ils être envoyés à un service en ligne, hors du cabinet ? | « Je ne veux pas que mes dossiers partent dans un cloud américain. Un hébergeur français avec un contrat sérieux, pourquoi pas, notre logiciel de gestion de cabinet l'est déjà. Mais il faudra me l'expliquer simplement. » | **Pas de cloud US.** Un cloud **hébergé en France sous contrat** est acceptable, ce qui exclut les API LLM américaines classiques. Il faudra **expliquer simplement** à la cliente, donc pédagogie dans le cadrage. |
| 11 | Où sont stockés vos dossiers aujourd'hui : sur un serveur au cabinet ou dans un logiciel en ligne ? | « Un logiciel de gestion de cabinet du marché pour les dossiers et la facturation, hébergé en France, Microsoft 365 pour les mails et Word, et un serveur de fichiers au cabinet pour les documents. » | Il y a trois briques : le logiciel métier (hébergé en France), M365 et le **serveur de fichiers local**. Les décisions et courriers sont sans doute sur ce serveur, qui est la source à indexer. M365 pose la question de la localisation des données Microsoft. |
| 12 (rendue) | Pouvez-vous m'envoyer un des modèles de mise en demeure du dossier partagé ? | Pas de modèle de mise en demeure disponible (question rendue). | **Il n'existe aucun modèle à jour** : il faudra en constituer un à partir des anciens courriers, ce qui est un préalable au volet courriers. |
| 12 | Donnez-moi un exemple de recherche faite récemment : que cherchiez-vous ? | « Pour la jurisprudence publique, on a un abonnement à une base juridique en ligne. Mais notre vraie richesse, ce sont nos propres dossiers : les décisions qu'on a obtenues ici, à Bordeaux. Elles sont rangées dans des dossiers sur le serveur, et on cherche par nom de fichier… ou on demande au collègue qui s'en souvient. » | Pas d'exemple concret, mais le besoin est **confirmé** : la jurisprudence publique est **déjà couverte** (abonnement), donc **hors périmètre**. La cible, c'est **l'archive interne** sur le serveur de fichiers. Aujourd'hui, la recherche se fait par **nom de fichier** ou par **mémoire des collègues** : le savoir est tacite et fragile (départ d'un collègue = perte). |

_Relance non prévue ? Note-la aussi, avec la raison (« réponse surprenante sur… »)._

### Boussole — ce que j'ai déjà obtenu

> Mets-la à jour **après chaque réponse**. Elle suit des **informations**, pas
> tes questions : une réponse peut en remplir plusieurs, une autre aucune.
> Quand il te reste 3-4 questions, regarde les 🔴 : lequel manquera le plus à
> ton cadrage ? C'est à toi de formuler la question.
>
> 🟢 obtenu · 🟠 partiel / à vérifier · 🔴 à obtenir · ⬜ pas demandé (→ §3)

| Information | Statut | Réponse n° |
|---|---|---|
| Besoin réel (≠ demande exprimée) | 🟢 retrouver et réutiliser la production interne du cabinet (décisions, courriers) | 2, 4 |
| Processus actuel | 🟢 copier-coller depuis les postes, modèles de 2019 non tenus à jour | 3 |
| Données : existence | 🟢 décisions, registre, courriers dans les dossiers clients | 5, 6 |
| Données : volume | 🟢 environ 2 000 décisions sur 15 ans, des milliers de courriers | 5 |
| Données : qualité | 🟠 formats mixtes, scans anciens peu lisibles, courriers non classés | 5 |
| Données : extrait obtenu | 🟢 registre des décisions (métadonnées), à analyser | 6 |
| Données personnelles / confidentialité | 🟢 droit de la famille exclu ; pas de cloud US, hébergeur français sous contrat accepté | 1, 6, 10 |
| Critère de succès chiffré | 🟢 1 h par avocat et par jour, recherche en moins d'1 min | 9 |
| Coût d'une erreur | 🟢 responsabilité professionnelle engagée | 7 |
| Erreurs tolérées (chiffre : fausses alertes, mauvais routage…) | 🟠 zéro décision inventée ; tolérance sur une recherche incomplète inconnue | 7 |
| Utilisateurs | 🟢 assistantes (préparation) et 12 avocats | 3 |
| Validation humaine / qui décide | 🟢 l'avocat relit et signe | 3 |
| SI / hébergement | 🟢 logiciel de gestion de cabinet (hébergé en France), M365, serveur de fichiers local | 10, 11 |
| Budget | 🟢 15 k€ pour démarrer, quelques centaines d'euros par mois | 8 |
| Délai | ⬜ | |
| Ce qui a déjà été essayé | 🟠 abonnement à une base juridique en ligne (jurisprudence publique) ; rien pour l'archive interne | 12 |

## 3. Après — ce que je n'ai pas pu demander → questions ouvertes

| Je n'ai pas pu demander / pas eu de réponse claire | Pourquoi c'est important | → §6 du cadrage |
|---|---|---|
| Exemple concret de recherche (par critères ou par argument juridique ?) | Décide si le registre suffit ou s'il faut indexer le contenu des PDF | Atelier avec 2-3 avocats : collecter 10 recherches réelles comme jeu de test |
| Le registre ne couvre que 2020-2025 (extrait) alors que l'archive porte sur 15 ans | Couverture réelle de l'index, décisions anciennes introuvables | Vérifier l'exhaustivité du registre complet |
| Qualité de saisie du registre (prud'hommes saisis en « TJ Bordeaux ») | Un filtre par juridiction serait faux | Audit d'un échantillon du registre |
| Part des scans illisibles parmi les 2 000 décisions | Coût et qualité de l'OCR | Comptage sur le serveur |
| Absence de modèle de courrier à jour | Le volet courriers suppose d'abord de constituer des modèles | Qui valide les modèles de référence ? |
| Localisation des données Microsoft 365 | Cohérence avec le refus du cloud US | Vérifier le contrat M365 |
| Délai | Planification du lot 1 | À fixer avec la cliente |
| Qui anonymise ou filtre le droit de la famille à l'entrée | Exclusion demandée par la cliente | Règle de filtrage sur la colonne `matiere` |
