# Schéma d'architecture cible — Cabinet Maître Devalle

> Niveau composants (la stack précise relève de M8-B2). Tout est hébergé et maintenu
> **chez un hébergeur français sous contrat** (Q10) : aucun flux hors de France.
> **Imprévu du 31/12** : le serveur du cabinet n'aura plus de maintenance. Il ne sert
> donc qu'à une **copie initiale** des décisions, et rien n'y est installé.

```mermaid
flowchart LR
    subgraph L1["Lot 1 — Retrouver nos décisions (priorité)"]
        SRV[("Serveur du cabinet<br/>~2 000 décisions")] -->|"copie unique avant le 31/12"| STO[("Stockage + sauvegarde<br/>hébergeur français")]
        STO --> ING["Ingestion<br/>filtre matière ≠ famille"]
        ASS(["Assistante<br/>ajoute les nouvelles décisions"]) --> STO
        REG[("Registre des décisions<br/>matière, date, issue")] --> ING
        ING --> OCR["Extraction du texte<br/>OCR des scans"]
        OCR --> Q{"Texte lisible ?"}
        Q -->|non| REV["Liste à re-numériser<br/>(assistante)"]
        Q -->|oui| IDX[("Index de recherche<br/>texte + filtres")]
        IDX --> UI["Interface de recherche<br/>comptes nominatifs"]
        UI -->|"liens vers les originaux"| AV1(["Avocat / assistante<br/>lit la décision source"])
    end

    subgraph L2["Lot 2 — Courriers types"]
        MOD[("Modèles validés<br/>par un avocat référent")] --> FUS["Pré-remplissage<br/>du modèle"]
        LGC[("Logiciel de gestion<br/>débiteur, montant, échéance")] --> FUS
        FUS --> BRO["Brouillon Word"]
        BRO --> V{"L'avocat relit<br/>et signe ?"}
        V -->|correction| BRO
        V -->|oui| ENV(["Envoi"])
    end

    UI --> LOG[("Journal + suivi<br/>consultations, volumes anormaux,<br/>recherches sans résultat")]
    FUS --> LOG
```

**Composants** :
- **Stockage + sauvegarde (hébergeur français)** : reçoit une copie unique des décisions avant le 31/12. Les nouvelles décisions sont ajoutées par l'assistante, ce qui supprime la dépendance au serveur non maintenu.
- **Ingestion** : lit le stockage et le registre, **exclut le droit de la famille** (risque §4) et n'accepte que les dépôts de l'assistante (empoisonnement de l'index).
- **Extraction du texte / OCR** : rend les scans cherchables. Le nœud « Texte lisible ? » évite une fausse impression d'exhaustivité en listant ce qui reste introuvable.
- **Index de recherche** : recherche dans le texte, combinée aux filtres du registre (matière, date, issue).
- **Interface de recherche** : **comptes nominatifs** gérés par un référent du cabinet, résultats sous forme de **liens vers les documents originaux**. Il n'y a aucun texte généré, donc aucune décision inventée.
- **Pré-remplissage** : remplit les modèles validés **depuis le logiciel de gestion**, ce qui évite toute saisie ou génération de montant ou de délai.
- **Validation humaine** : l'avocat relit et signe avant tout envoi (processus actuel conservé, Q3).
- **Journal + suivi** : sert à la sécurité (volumes anormaux, exfiltration) et aux KPI (temps de recherche, recherches sans résultat).

**Ce qu'on n'a PAS mis** (et pourquoi) :
- **Pas de LLM génératif** : le risque n°1 est l'invention (Q7), et ni la recherche ni les courriers types n'en ont besoin.
- **Pas de base vectorielle ni de RAG** : la recherche plein texte et les filtres du registre sont essayés d'abord. Une recherche sémantique ne serait ajoutée que si le jeu de test (§3) montre qu'elle rate trop de décisions.
- **Pas de jurisprudence publique** : elle est déjà couverte par l'abonnement du cabinet (Q12).
- **Pas de réentraînement** sur les retours des utilisateurs : il n'y a pas de modèle entraîné, donc pas de boucle d'empoisonnement.
- **Pas de statistiques par avocat** : elles feraient basculer l'outil en haut risque (§4, Annexe III 4 b).
