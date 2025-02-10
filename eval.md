# POC Quizz

Bonjour,

Je suis CEO d'une entreprise de divertissement et nous avons comme projet de développer un jeu de type quizz compétitif. Nous recherchons une équipe de développeurs pour réaliser un Proof of concept (POC), c'est-à-dire un projet reprennant les mécaniques principales, pour voir si cela est réalisable et fonctionnel selon nos enjeux.

Les compétences attendues pour cette mission sont :

-   **Maitriser le découpage algorythmique du projet.**
-   **Maitriser la création de composants React.**
-   **Passer des props entre composants.**
-   **Gérer la logique d'un quizz (navigation entre les questions, comptage des points).**

Nous souhaiterions utiliser l'API publique de [Open Trivia Database](https://opentdb.com/api_config.php).

Pour vous accompagner dans ce projet, notre CTO a rédigé un brief détaillé pour vous guider dans le développement de ce POC. Cela vous permettra de mieux comprendre les technologies, les attentes et les fonctionnalités à implémenter et de vous concentrer sur la réalisation du projet.

## 1. Mise en place du projet

### Création de l'application

1. Créez un nouveau projet React avec ViteJS :

```bash
npm create vite@latest
```

2. Nettoyez le projet de base en supprimant les fichiers inutiles (logo, CSS inutile, etc.).

### Structure des dossiers

Nous vous proposons la structure suivante mais vous pouvez l'adapter selon vos préférences :

```
/src
  /components
    - Home.js
    - Quiz.js
    - Question.js
    - Result.js
  App.js
  index.js
```

---

## 2. Page de présentation (Home)

Votre page d'accueil doit captiver l'utilisateur dès les premières secondes. Imaginez que vous créez une landing page qui donne envie de cliquer sur "Commencer le Quizz".

### Ce que j'attends :

1. **Design moderne et engageant**.
2. **Structure claire et aérée**.
3. **Interactivité**.

Si vous avez l'occasion d'aller plus loin, comme de gérer le responsive design, d'ajouter des animations, des couleurs vives et engageantes, cela ne donnera que plus de valeur au POC.
Toutefois, si vous vous contentez d'une bonne structure React, cela est tout a fait acceptable.

### Contenu :

-   **Titre accrocheur** : "Prêt à tester tes connaissances ? 🌟"
-   **Sous-titre dynamique** : "Challenge-toi avec notre super quizz interactif !"
-   **Description** : "10 questions, 4 réponses, un seul champion. Réussiras-tu à atteindre le score parfait ?"
-   **Illustration ou image** : Ajoutez une image ou une illustration fun pour donner de la vie à la page.
-   **Bouton déclencheur** : "Commencer le Quizz" (avec une animation au clic qui lance le quizz).

### Tâches pour l'équipe :

1. **Création du composant `Home.js` :**

    - Structurez le HTML avec des sections claires.
    - Stylisez avec CSS.

    Si vous parvenez a mettre en place des modules CSS, cela permettra la réutilisation des composants lors du projet réel et fera gagner énormément de temps a l'équipe de développement.

2. **Ajout d'animations :**

    - Utilisez des transitions CSS pour le bouton (ex : changement de couleur au survol).
    - Ajoutez une animation d'entrée pour les textes (par exemple, un fade-in ou un slide-in).

3. **Gestion de la navigation :**

    - Dans `App.js`, gérez l'affichage entre `Home` et `Quiz` avec un état :
    - Si le quizz a commencé, alors afficher le composant Quizz.
    - Si le quizz n'a pas commencé, alors afficher le composant Home.

### Bonus :

-   Ajoutez un footer avec des liens fictifs comme "A propos", "Contact", ou "Mentions légales" pour rendre la page encore plus réaliste.
-   Ajouter des composants Header et Footer qui seront autour de Home et Quizz, pour afficher le logo de notre application et ces fameux liens vers notre plateforme de divertissement.

### Choix de développement :

Vous pouvez choisir l'une des deux approches suivantes pour la création de vos composants :

1. **Utilisation d'une librairie de composants UI** :

    - Par exemple, utilisez **Material-UI**, **Chakra UI** ou **React-Bootstrap** pour accélérer la création de vos composants.
    - Nous vous conseiller **Material-UI**.
    - Avantage : Gain de temps sur le design et les comportements standards.
    - Vous pouvez utilisez des composants customs ET une librairie de composants pour obtenir le meilleur des deux mondes : des composants préformatés mais aussi des composants développés à la main.

2. **Création de vos propres composants** :
    - Développez et stylisez vos propres boutons, cartes, et modales à partir de zéro.
    - Avantage : Meilleure maîtrise de la personnalisation et de la logique des composants.

Quel que soit votre choix, assurez-vous de bien organiser et réutiliser vos composants pour garantir un code propre et modulable.

---

## 3. Récupération des questions (API)

Utilisez l'API [Open Trivia Database](https://opentdb.com/api_config.php) pour récupérer des questions.

### API Endpoint :

Utilisez cet endpoint pour obtenir 10 questions de type choix multiple :\
`https://opentdb.com/api.php?amount=10&type=multiple`

### Tâches :

1. Créez un composant `Quiz.js`.
2. Permettre a l'utilisateur de cliquer sur un bouton "Jeu classic" (nous envisageons de développer d'autres modes de jeux par la suite).
3. Lorsque le bouton est cliqué, les questions doivent être chargées et stockées dans ce composant.
4. Pensez a garder en mémoire la question en cours. Plusieurs solutions sont possibles, nous voulons savoir où en est le déroulement du quizz.

---

## 4. Affichage des questions et des réponses

Chaque question doit être affichée avec 4 réponses possibles, dont une correcte.

### Tâches :

1. Créez un composant `Question.js` qui recevra les données de la question en props.
2. Affichez la question et les 4 réponses de manière aléatoire (pensez à mélanger les réponses).
3. Lorsqu'une réponse est cliquée, vérifiez si elle est correcte et passez à la question suivante.

### Gestion du score :

-   Créez un état `score` dans `Quiz.js`.
-   Incrémentez le score si la réponse est correcte.

### Bonus :

-   Tout joueur aimerai savoir s'il s'est trompé et quelle est la bonne réponse. Si vous arrivez a faire cela, cela serait génial pour notre entreprise ! Nous n'avons pas encore décidé où afficher cette information :
-   1. Vous pouvez l'afficher après chaque question.
-   2. Vous pouvez afficher toutes les questions et les bonnes réponses a la fin du quizz, dans la page de résultat.
-   3. Si vous arrivez a afficher la réponse de l'utilisateur et la bonne réponse, avec du rouge si l'utilisateur s'est trompé, cela serait parfait !

---

## 5. Affichage du résultat

Après la dernière question, affichez la page de résultats.

### Tâches :

1. Créez un composant `Result.js`.
2. Affichez le score final avec un message adapté :
    - **0-4/10** : "Oups, tu peux mieux faire !"
    - **5-7/10** : "Pas mal, tu t'en sors bien !"
    - **8-10/10** : "Félicitations, tu es un expert !"
3. Proposez un bouton pour rejouer le quizz.

---

## 6. Bonus (Facultatif). C'est du vrai bonus, ces fonctionnalités seront reportées au premier sprint du projet autrement.

Si vous avez terminé avant le temps imparti, vous pouvez ajouter des fonctionnalités supplémentaires :

1. **Choix de la catégorie et de la difficulté** : Utilisez les paramètres de l'API pour personnaliser le quizz.
2. **Animation des réponses** : Ajoutez des effets visuels pour les réponses correctes et incorrectes.
3. **Sauvegarde du score** : Utilisez `localStorage` pour enregistrer le meilleur score.
4. **Mode Survival** :
    - **Principe** : Le joueur commence avec 10 vies. Chaque mauvaise réponse fait perdre une vie. Le but est d'aller le plus loin possible.
    - **Tâches** :
        1. Ajoutez un état `lives` dans `Quiz.js` initialisé à 10.
        2. Diminuez `lives` de 1 en cas de mauvaise réponse.
        3. Le quizz continue jusqu'à ce que les vies atteignent 0.
        4. Réutilisez les composants existants (`Question.js`, `Result.js`) en adaptant la logique.
        5. Affichez le nombre de vies restantes à l'écran et un message de fin spécifique au mode Survival.

---

## Livrable attendu

-   Une application React fonctionnelle avec une page de présentation engageante, un quizz de 10 questions, et une page de résultat.
-   Code propre et bien organisé, avec des composants réutilisables.
-   Gestion correcte des états et des props.

Vous pouvez fournir le code via un repository github ou bien sous forme de ZIP dépossé dans le dossier Teams prévus a cet effet.

Vous devez rendre le code avant 16h00. **A partir de 16h00**, vous et vos concurrents ferez une présentation de votre projet, incluant une démonstration de l'application, une explication de votre code et notamment de la manière dont vous avez stocker l'état du jeu. Vous pourrez répondre aux questions de l'audience.

Bon courage et amusez-vous bien ! 🎉
