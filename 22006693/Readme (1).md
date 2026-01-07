# COURS DE SCIENCE DES DONNÉES

# A.LARHLIMI

## Draigui Salma
## 22006693
<img src="acc392d2-a729-4bde-b19b-eba784d21385.jfif" style="height:540px;margin-right:393px"/>

## École Nationale de Commerce et de Gestion (ENCG) - 4ème Année

## Analyse des données relatives aux notes des étudiants aux examens
---
Voici un **contexte, un objectif (but), une introduction possible et une conclusion** pour l’analyse du jeu de données accessible via le lien que tu as fourni — Student Exam Score Dataset Analysis — sur Kaggle.
## 📝 Introduction type (à commencer ton rapport ou ton notebook)

> L’éducation et la réussite scolaire dépendent non seulement des capacités intellectuelles des étudiants, mais aussi de leurs habitudes (étude, sommeil), de leur assiduité, et de leurs antécédents académiques. À travers l’analyse du dataset « Student Exam Score Dataset Analysis », composé de 200 étudiants et de 6 variables — heures d’étude, sommeil, assiduité, scores antérieurs, score final —, l’objectif est de comprendre comment ces facteurs interagissent pour influencer la performance finale à l’examen. Cette étude permettra d’identifier les déterminants clés de la réussite et d’évaluer dans quelle mesure il est possible de **prédire le score final** à partir des comportements et antécédents des étudiants.

## 🎯 Contexte & description du dataset

* Le dataset « Student Exam Score Dataset Analysis » a été publié par l’utilisateur / contributeur « grandmaster07 » sur Kaggle. ([Kaggle][1])

* Ce dataset contient **200 lignes (200 étudiants)** et **6 colonnes** : `student_id`, `hours_studied`, `sleep_hours`, `attendance_percent`, `previous_scores`, `exam_score`. ([Baselight][2])

* En d’autres termes, chaque entrée correspond à un étudiant, avec des informations sur :

  * le nombre d’heures d’étude (`hours_studied`)
  * le nombre d’heures de sommeil (`sleep_hours`)
  * le pourcentage de présence / assiduité (`attendance_percent`)
  * les scores précédents (par ex. d’examens antérieurs) (`previous_scores`)
  * le score final de l’examen actuel (`exam_score`)

* L’idée est de lier des **habitudes, comportements ou antécédents académiques** à la **performance finale** — c.-à-d. examiner comment l’étude, le sommeil, l’assiduité ou les résultats antérieurs influencent le score à l’examen. ([Kaggle][3])

## 📘 Objectif / But de l’analyse

L’objectif principal de l’analyse de ce dataset est de **comprendre les facteurs qui influencent la réussite scolaire (exam_score)**. Concrètement, cela peut se traduire par des questions comme :

* Est-ce que **plus d’heures d’étude** se traduisent par de **meilleurs scores** ?
* Quelle est l’influence du **sommeil** sur la performance ?
* L’**assiduité (attendance)** joue-t-elle un rôle significatif ?
* Les **scores antérieurs (previous_scores)** sont-ils un bon prédicteur du score final ?
* Peut-on construire un modèle (régression, classification…) capable de **prédire le score d’un étudiant** à partir de ces variables ?

De façon plus large, l’analyse vise à dégager des **insights éducatifs** qui pourraient aider à identifier les comportements/conditions favorables à la réussite, ou à repérer des étudiants à risque.

# ⭐ **INTERPRÉTATION DE CHAQUE CODE DU NOTEBOOK**
1️⃣ student_id

Ce que c’est : un identifiant unique pour chaque étudiant.

Interprétation :

Sert uniquement à distinguer les étudiants.

N’a aucune valeur statistique ou explicative.

On ne l’utilise jamais dans une analyse ou dans un modèle.

2️⃣ hours_studied

Ce que c’est : nombre d'heures d'étude.

Interprétation :

Plus ce nombre est élevé, plus l’étudiant a travaillé.

Hypothèse courante : plus d’heures d’étude → meilleur score.

On l’utilise pour vérifier si l’effort (temps passé) a un impact sur le résultat de l’examen.

Exemple d’interprétation :
Si la corrélation est forte, cela signifie que l’étude explique une partie importante de la réussite.

3️⃣ sleep_hours

Ce que c’est : nombre d'heures de sommeil.

Interprétation :

Mesure le niveau de repos de l’étudiant.

Trop peu de sommeil peut réduire les performances.

Trop de sommeil peut aussi être un signe de désorganisation.

On vérifie souvent s’il existe un niveau optimal de sommeil.

Exemple :
Si les étudiants avec 6–8 heures dorment mieux et ont les meilleurs scores → effet positif du manque ou surplus de sommeil.

4️⃣ attendance_percent

Ce que c’est : le pourcentage de présence en cours.

Interprétation :

Mesure l’assiduité et l’implication.

Plus le pourcentage est élevé, plus l’étudiant assiste aux cours.

Souvent, la présence est un excellent prédicteur du score final.

Exemple d’analyse :
Si un étudiant a 30% de présence mais 90% d’examen, c’est atypique.
Si 90% de présence = bons résultats, cela confirme l’importance de l’assiduité.

5️⃣ previous_scores

Ce que c’est : score(s) obtenus précédemment.

Interprétation :

Mesure le niveau académique historique de l’étudiant.

Les étudiants avec de bons résultats dans le passé ont statistiquement plus de chances de réussir encore.

C’est une variable très utile pour prédire le score final.

Exemple :
Un étudiant avec 95 de moyenne avant a plus de chances d’avoir un bon score à l’examen final.

6️⃣ exam_score (variable cible)

Ce que c’est : score final de l’examen.

Interprétation :

C’est le résultat final, la variable que l’on cherche à expliquer.

On va analyser comment les autres variables (étude, sommeil, présence, scores précédents) influencent ce score.

Exemple :
Si hours_studied explique 40% de la variation du score → bonne prédiction.
Si sleep_hours n’a aucun effet → variable non déterminante.
---
7️⃣Interprétation du graphique
plt.figure(figsize=(8, 6))
sns.histplot(data['exam_score'], kde=True, bins=10, color='skyblue')
plt.title("Target Distribution")
plt.xlabel("exam_score")
plt.ylabel("Count")
plt.show()

Ce graphique représente la distribution de la variable exam_score, c’est-à-dire la répartition des notes finales des étudiants.
<img src="téléchargement.png" style="height:540px;margin-right:393px"/>

Voici ce que l’on observe :

✅ 1) Forme générale : distribution quasi-normale

La courbe bleue ressemble à une courbe en cloche (distribution normale).

Cela signifie que :

La majorité des étudiants ont des scores proches de la moyenne.

Peu d’étudiants ont des scores très bas ou très élevés.

👉 Interprétation :
La performance des étudiants est centrée autour d’un score moyen et varie normalement — c’est un bon signe pour utiliser des méthodes statistiques classiques (corrélations, régression linéaire…).

✅ 2) Score moyen autour de 32–35

Le “pic” du histogramme est autour de 30–35.

Donc, la plupart des étudiants obtiennent une note dans cette zone.

👉 Interprétation :
Le niveau général est moyen à légèrement bon.

✅ 3) Symétrie

La distribution semble assez symétrique, mais peut-être légèrement plus étalée vers la droite (scores plus élevés).

👉 Interprétation :
Pas de forte asymétrie → pas de biais important dans les scores.

✅ 4) Pas de valeurs extrêmes évidentes

On voit très peu de notes < 20 ou > 50.

Cela signifie que le dataset est propre et ne contient pas d’outliers problématiques.
8️⃣Interprétation complète de la matrice
plt.figure(figsize=(12, 10))
corr = data.corr()

sns.heatmap(
    corr,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1,
    linewidths=0.5
)

plt.title("Correlation Matrix of Student Exam Scores Data")
plt.show()
Voici ce que signifie chaque corrélation importante :
<img src="téléchargement (2).png" style="height:540px;margin-right:393px"/>

🔥 1. La corrélation la plus forte : hours_studied → exam_score (0.78)

Valeur : +0.78, très forte corrélation positive.

Interprétation : Plus un étudiant étudie, plus son score augmente.
👉 C’est le facteur le plus déterminant de la réussite.

➡ C’est une corrélation presque “linéaire” : les heures d’étude expliquent beaucoup la note.

⭐ 2. previous_scores → exam_score (0.43)

Corrélation modérée à forte.

Interprétation :
Les étudiants qui avaient de bonnes notes avant ont tendance à réussir encore.

➡ Cela montre une continuité du niveau académique.

👍 3. attendance_percent → exam_score (0.23)

Corrélation faible mais positive.

Interprétation :
Être présent en cours aide un peu, mais pas autant que les heures d’étude.

➡ La présence est utile, mais moins déterminante que le travail personnel.

😴 4. sleep_hours → exam_score (0.19)

Corrélation faible positive.

Interprétation :
Dormir un peu plus semble aider, mais l’effet est limité.

➡ Peut refléter un meilleur état mental → meilleure concentration.

💤 5. previous_scores ↔ sleep_hours (-0.19)

Corrélation négative faible.

Interprétation :
Les étudiants qui dormaient moins avaient parfois de meilleurs scores précédents.
(Peut être dû à des étudiants stressés / très travailleurs.)

➡ Rien de sérieux : faible corrélation.

❌ Variables inutiles dans l’analyse : student_id

Corrélations d’environ 0, donc non interprétables.

C’est normal : l’identifiant est juste un numéro.
9️⃣Interprétation du graphe
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Exemple de DataFrame selon les variables visibles dans le graphique
df = pd.DataFrame({
    "student_id": [...],
    "hours_studied": [...],
    "sleep_hours": [...],
    "attendance_percent": [...],
    "previous_scores": [...],
    "exam_score": [...]
})

# Calcul de la matrice de corrélation
corr_matrix = df.corr()

# Taille du graphe
plt.figure(figsize=(10, 8))

# Heatmap
sns.heatmap(
    corr_matrix,
    annot=True,
    cmap="Blues",
    linewidths=0.5,
    fmt=".2f"
)

plt.title("Matrice de corrélations")
plt.show()
heatmap montre les corrélations entre :

hours_studied

sleep_hours

attendance_percent

previous_scores

exam_score
<img src="téléchargement (3).png" style="height:540px;margin-right:393px"/>
et on voit plusieurs choses importantes :

🔵 1. hours_studied → exam_score (corrélation positive forte)

Dans ton graphique, la corrélation entre hours_studied et exam_score est élevée (environ ~0.75).

➡️ Plus un étudiant étudie, meilleur est son score d’examen.
C’est la relation la plus forte du graphe.

🔵 2. previous_scores → exam_score (corrélation faiblement positive)

La corrélation est faible (autour de 0.40).

➡️ Les étudiants ayant eu de bons résultats auparavant ont une légère tendance à réussir aussi l’examen.
Mais ce n’est pas un facteur très dominant.

🔵 3. sleep_hours → exam_score (corrélation faible)

Dans le graphe, cette corrélation est proche de zéro.

➡️ Le sommeil ne prédit presque pas le score dans ton dataset.
Cela veut dire que dormir plus n'influence pas directement la note.

🔵 4. attendance_percent → other variables

attendance_percent ne montre pas de corrélation forte avec exam_score ni avec les autres variables.

➡️ La présence n’est pas un facteur déterminant dans ce dataset.
Elle ne prédit pas les performances de l’étudiant.

🔵 5. student_id est non pertinent

La diagonale montre 1.0 (normal), mais toutes les autres corrélations sont très proches de 0.

➡️ student_id n’a aucun lien avec les variables académiques, ce qui est normal (simple identifiant).
---


## ✅ Conclusion type (résultats attendus & portée)

> L’analyse de ce dataset peut permettre d’établir des relations claires entre les habitudes (étude, sommeil), l’assiduité, les performances passées et le résultat final à l’examen. Si des corrélations significatives sont trouvées — par exemple, plus d’heures d’étude ou une meilleure assiduité associées à un score plus élevé — cela pourrait offrir des recommandations pratiques pour améliorer la réussite des étudiants. De plus, avec un modèle de prédiction (régression ou classification), il serait possible d’anticiper la performance des étudiants, identifier ceux à risque, et ainsi proposer des interventions ciblées (soutien, tutorat, conseils d’étude). Enfin, ce type d’analyse illustre l’intérêt de l’**analyse de données éducatives** pour mieux comprendre la dynamique de l’apprentissage — un atout potentiel pour enseignants, administration scolaire, et politiques éducatives.



