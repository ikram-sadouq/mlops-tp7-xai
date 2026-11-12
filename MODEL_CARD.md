
# Model Card - fraude (version servie par l'alias production)

## Modele
Nom et version dans le registre MLflow : fraude, version 1, alias production.
Famille et reglages : RandomForestClassifier, 500 arbres, profondeur maximale 16.
Run d'origine (MLflow) : [RUN_ID DU MODELE TP2].

## Objectif et usage prevu
Détecter les transactions bancaires potentiellement frauduleuses à partir du montant, de l'ancienneté du client, de la fréquence des transactions sur 24 heures et de l'indicateur de paiement nocturne.
Le modèle est destiné à aider à la détection et à la priorisation des transactions nécessitant une vérification.

## Usages exclus
Le modèle ne doit pas être utilisé pour bloquer définitivement un compte ou refuser automatiquement un client sans vérification humaine.
Il ne doit pas être considéré comme un outil de preuve de fraude.

## Donnees
Fichier, nombre de lignes, part de fraudes, empreinte (tag donnees_md5) :
data/transactions.csv, 5 000 lignes, 568 fraudes (11,36 %), empreinte MD5 : [EMPREINTE DU RUN XAI].
Origine des donnees : données synthétiques générées artificiellement, elles ne représentent pas des transactions bancaires réelles.

## Performances (jeu de test, 1 250 transactions)
F1 : 0.8669
Precision : 0.8837
Rappel : 0.8507
AUC : 0.9872

## Methodes d'explicabilite
Globale : importance par permutation et SHAP TreeExplainer.
Locale : SHAP et LIME appliqués aux transactions individuelles, notamment celle de Mme Benali.
Variables les plus influentes : montant, anciennete, nuit et freq_24h selon les résultats SHAP globaux.

## Comparaison avec un modele interpretable
Comparaison avec une régression logistique et un arbre de décision peu profond.
[Ajouter les résultats F1 et le compromis entre performance et lisibilité obtenus à l'activité 5.]

## Limites et risques connus
Les données sont synthétiques et peuvent ne pas représenter la diversité des comportements frauduleux réels.
Les explications SHAP et LIME décrivent le comportement du modèle mais ne démontrent pas une relation de causalité.
Les explications LIME peuvent varier selon l'échantillonnage et la graine aléatoire.

## Recommandations d'utilisation et de surveillance
Maintenir une validation humaine pour les décisions sensibles.
Surveiller régulièrement les performances, la distribution des données et les changements de comportement des transactions.
Réévaluer le modèle en cas de dérive des données.

## Tracabilite
Run des explications (experience tp7-explicabilite) : [RUN_ID ACTIVITE 6].
Auteurs : Ikram Sadouq.
Date : 12/11/2026.
Prochaine revue : à définir.
