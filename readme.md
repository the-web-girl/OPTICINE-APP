🎬 Prompt complet – Bibliothèque Films & Séries

Crée-moi une application web et mobile (HTML, CSS, JavaScript) qui soit :

1. Accessibilité & design

Responsive : compatible ordinateurs, tablettes, smartphones.

Accessible WCAG 2.1 (niveaux A/AA au minimum).

Mode sombre par défaut pour le confort visuel.

Palette simple et sobre : noir, blanc, gris, rouge.

Design clair et lisible (grandes polices, contrastes suffisants, aria-labels, navigation clavier).

2. Fonctionnalités principales

Ajout de films et séries à ma collection.

Ajout possible par titre ou via une barre de recherche connectée à une API (ex : TMDB, AlloCiné, IMDb).

Chaque ajout représente un seul film ou une seule saison, jamais une série complète automatiquement.

Un film/série peut avoir des attributs :

Formats : DVD / Blu-ray / 4K.

Édition : Simple ou Steelbook.

Saga/trilogie/univers (ex. Star Wars, MCU…).

Si une saga est renseignée, afficher un regroupement :

Soit une colonne Saga/Trilogie à côté du titre.

Soit un bloc/titre principal regroupant toutes les entrées liées.

Case à cocher Possédé :

Si décochée → l’entrée est dans ma liste de souhaits.

Si cochée → l’entrée passe automatiquement dans la collection possédée.

Recherche par acteurs :

Exemple : en tapant Bruce Willis, je vois :

Les films/séries de ma collection avec cet acteur.

Les films/séries de ma liste de souhaits avec cet acteur.

3. Gestion & multi-utilisateurs

La collection doit être partagée entre plusieurs utilisateurs (minimum 4 personnes).

Plusieurs utilisateurs doivent pouvoir ajouter/modifier en même temps, depuis différents appareils.

4. Stockage

Étape 1 (local) : possibilité de sauvegarder dans LocalStorage pour tests rapides.

Étape 2 (base de données Firebase) :

Relier l’application à Firebase Firestore pour la gestion multi-utilisateurs.

Stocker les films/séries avec tous leurs attributs.

Chaque modification est synchronisée en temps réel entre tous les appareils.

5. Autres options

Barre de recherche universelle pour filtrer la collection par :

Titre

Acteur

Saga/Univers

Format (DVD, Blu-ray, 4K, Steelbook)

Interface sobre et ergonomique (cartes ou tableau clair).

Compatible avec navigation clavier et lecteurs d’écran.

🔥 Instructions Firebase pas à pas (à inclure dans l’app générée)
Étape 1 – Créer un projet Firebase

Va sur https://console.firebase.google.com

const firebaseConfig = {
  apiKey: "XXXXXXX",
  authDomain: "ton-projet.firebaseapp.com",
  projectId: "ton-projet",
  storageBucket: "ton-projet.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};

⚠️ Ce code doit être collé dans ton fichier index.html ou app.js à l’endroit prévu dans l’app.

Étape 4 – Installer Firebase (optionnel si juste HTML/JS)

Si tu codes en pur HTML/JS, ajoute dans ton <head> :
<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.3/firebase-app.js";
  import { getFirestore } from "https://www.gstatic.com/firebasejs/10.12.3/firebase-firestore.js";

  const app = initializeApp(firebaseConfig);
  const db = getFirestore(app);
</script>

Étape 5 – Vérifier la synchro

Chaque ajout/modification doit être enregistré dans la collection Firestore :

Collection : users → document par utilisateur → sous-collection items.

Exemple structure Firestore :
users
 └── userId (auto ou login Google)
      └── items
           ├── film_123
           │    ├── title: "Die Hard"
           │    ├── format: "Blu-ray"
           │    ├── owned: true
           │    └── saga: "Die Hard"
           └── film_456
                ├── title: "Star Wars IV"
                ├── format: "4K Steelbook"
                ├── owned: false
                └── saga: "Star Wars"


Étape 6 – Multi-utilisateurs

Active Authentication Firebase si tu veux gérer plusieurs comptes (Google, Email, etc.).

Sinon, on peut générer un userId aléatoire stocké dans LocalStorage pour différencier les utilisateurs.

Firestore gère automatiquement la mise à jour en temps réel entre plusieurs appareils.

✅ Résumé :

Le site est responsive, accessible (WCAG), sobre, mode sombre.

On peut ajouter/chercher films & séries (titre, acteurs, saga, formats, steelbook).

Distinction entre possédé et souhait.

Données locales → puis Firebase Firestore pour synchro multi-utilisateurs.

Fournir dans le code une zone claire où insérer firebaseConfig.

