Ce projet s’inscrit dans un cadre strictement légal et défensif : il vise à former l’apprenant à l’audit de sécurité d’applications Android en utilisant uniquement des APK pédagogiques (ex. DIVA) ou des applications internes autorisées. L’objectif est d’acquérir les compétences nécessaires pour organiser un audit défensif, collecter des signaux d’exposition, trier les résultats, identifier les faux positifs, corréler avec les standards OWASP, et produire un rapport exploitable – sans jamais exploiter activement les vulnérabilités ni perturber les cibles.

        Outils utilisés :

BeVigil (plateforme de recherche et d’analyse statique)

Yaazhini (analyseur de vulnérabilités Android)

APK pédagogique : DIVA (Damn Insecure and Vulnerable App) – fourni par l’enseignant

         Prérequis :

Connaissances de base en sécurité informatique

Ordinateur avec accès internet

Comptes/accès aux outils BeVigil et Yaazhini (fournis par l’enseignant)

Rappel des règles déontologiques :

Travail uniquement sur l’APK pédagogique ou cible autorisée

Interdiction formelle d’exploiter les vulnérabilités, de faire des tests intrusifs, de contourner des mécanismes de sécurité

Masquage de toute donnée sensible dans les rapports

Aucune action pouvant endommager ou surcharger une cible

Explication de chaque capture

            1. Capture 155812.png – Interface d’analyse statique :
Contexte :
Cette capture montre le tableau de bord d’un outil d’analyse de sécurité (probablement BeVigil ou Asset Explorer) appliqué à l’APK Diva (jakhar.aseem.diva version 1.0). L’outil effectue une analyse statique : extraction du manifeste, des chaînes de caractères, détection de vulnérabilités connues.

Éléments clés :

Total Detected Issues : 1 High, 1 Med, 1 Low (graphique avec axe X = High/Med/Low, Y = 0/1).

Next Course of Action : note globale 8.2 Rating - GOOD (sur 10). L’outil indique que la note peut être améliorée en corrigeant les problèmes.

Impact :

MED: Non-parameterized SQL Query – vulnérabilité d’injection SQL (requête non paramétrée).

LOW: Possible Secret Detected – possible secret (clé API, mot de passe) en clair dans le code.

Sections : VULNERABILITIES, STRINGS, MANIFEST SCANNER, ASSETS.

Lien vers Google Play (redondant, car l’APK est pédagogique).

              2. Capture 155928.png – Graphique de scores :

Remarque : l’image est tronquée, ne montrant que des valeurs numériques éparses (4.0, 3.5, 2.0, 1, …).

Contexte :
Il s’agit probablement d’un graphique ou d’un tableau de scores généré par un outil comme Yaazhini ou BeVigil (partie “Ratings” ou “CVSS scores”). Les valeurs (1, 2, 4, etc.) pourraient représenter des notes individuelles par catégorie de vulnérabilité ou par composant.

Interprétation possible :

Une échelle de 0 à 10 (ou 0 à 4) où plus le score est bas, plus le risque est élevé (ou l’inverse).

Les nombres comme 4.0, 3.5, 2.0 suggèrent des notes moyennes ou des pondérations.

Utilité dans le projet :
L’apprenant doit apprendre à lire et interpréter ces métriques sans se laisser impressionner par des chiffres bruts. Par exemple :

Un score de 1 peut indiquer une vulnérabilité critique.

Un score de 4.0 peut représenter un risque moyen.

Il faut toujours croiser avec la description textuelle (ex. la vulnérabilité SQL Med de la capture précédente).
Cette étape permet de trier les résultats et d’identifier les faux positifs (un score élevé sur un élément anodin).

             3. Capture 154353.png – Configuration d’un proxy manuel sur Android
Contexte :
Écran des paramètres Wi‑Fi Android (identique à 2.png vu précédemment). Bien que ce laboratoire porte sur l’analyse statique (interdiction de tests intrusifs), cet écran est montré ici à titre pédagogique pour comprendre comment un testeur dynamique configurerait un proxy (Burp Suite, mitmproxy) – mais cette action n’est pas autorisée dans le cadre strict de ce lab défensif.

Éléments :

Proxy hostname : 192.168.100.57 (IP du PC outil)

Proxy port : 8080

Bypass proxy for : domaines exclus

Message : “The HTTP proxy is used by the browser but may not be used by the other apps.”



Conséquence :
L’apprenant ne doit pas configurer ce proxy sur son appareil pour ce lab. Il se contente de reconnaître l’écran comme une connaissance annexe, mais n’exécute pas l’action.
