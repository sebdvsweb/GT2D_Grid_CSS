# Exercice : reconstruire une page avec CSS Grid

## Objectif

Reproduire la mise en page du schéma **CSS Grid** en deux versions :

- **PC** : une grille avec 4 colonnes et 4 lignes
- **Mobile** : tous les blocs empilés les uns sous les autres

Tu vas utiliser une nouvelle technique, **CSS Grid**, qui permet de placer des blocs comme sur un quadrillage. Tu as déjà les couleurs, les noms des zones et les tailles : à toi de construire la grille !

---

## Étape 0 : Préparer ton pen

1. Ouvre le pen de départ et clique sur **Fork** pour avoir ta propre copie.
2. Colle le HTML ci-dessous dans le panneau **HTML**.
3. Colle le CSS de départ (plus bas) dans le panneau **CSS**.
4. Pense à cliquer sur **Save** régulièrement !

### HTML (à coller tel quel, ne le modifie pas)

```html
<div class="conteneur">
  <header class="entete">En-tête</header>
  <aside class="lateral">Barre latérale</aside>
  <main class="principal">Main</main>
  <section class="contenu1">Contenu 1</section>
  <section class="contenu2">Contenu 2</section>
  <section class="contenu3">Contenu 3</section>
  <footer class="pied">Pied de page</footer>
</div>
```

---

## Ce qu'il faut savoir sur CSS Grid

| Propriété | À quoi elle sert | Exemple |
|---|---|---|
| `display: grid;` | Transforme un bloc en grille (à écrire sur le **parent**) | `.conteneur { display: grid; }` |
| `grid-template-columns` | Définit le nombre et la largeur des colonnes | `200px 1fr 1fr` = 3 colonnes |
| `grid-template-rows` | Définit le nombre et la hauteur des lignes | `90px 300px` = 2 lignes |
| `grid-template-areas` | Dessine la page avec des noms de zones | voir ci-dessous |
| `grid-area` | Dit à un bloc dans quelle zone il se place (à écrire sur chaque **enfant**) | `.entete { grid-area: entete; }` |
| `gap` | Espace entre les blocs | `gap: 15px;` |

**À retenir :**
- `px` est une taille fixe. `1fr` signifie « une part de l'espace restant » : `1fr 1fr 1fr` donne trois colonnes de largeur égale.
- Avec `grid-template-areas`, chaque ligne de texte entre guillemets est une ligne de la grille. Chaque mot est une case. Si un mot est répété, la zone s'étend sur plusieurs cases.

```css
grid-template-areas:
  "haut haut"
  "gauche droite";
```

Ici, `haut` occupe toute la première ligne (2 colonnes), puis `gauche` et `droite` se partagent la deuxième.

---

## Le CSS de départ

Remplace chaque commentaire `/* ... */` par le bon code.

```css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 20px;
  font-family: Arial, sans-serif;
  font-weight: bold;
  text-transform: uppercase;
  text-align: center;
}

/* ===== VERSION PC ===== */

.conteneur {
  /* 1. Transforme .conteneur en grille */

  /* 2. Espace entre les blocs : 15px */

  /* 3. COLONNES (4 colonnes) :
        - colonne 1 : 200px (la barre latérale)
        - colonnes 2, 3 et 4 : trois colonnes égales (1fr chacune) */

  /* 4. LIGNES (4 lignes) :
        - ligne 1 : 90px  (en-tête)
        - ligne 2 : 350px (main)
        - ligne 3 : 180px (contenus 1, 2 et 3)
        - ligne 4 : 90px  (pied de page) */

  /* 5. ZONES : dessine la page avec grid-template-areas
        Les noms à utiliser : entete, lateral, principal, contenu1, contenu2, contenu3, pied
        Indices :
        - l'en-tête occupe toute la ligne 1 (les 4 colonnes)
        - la barre latérale occupe la colonne 1 sur les lignes 2, 3 et 4
        - main occupe les colonnes 2 à 4 de la ligne 2
        - contenu1, contenu2 et contenu3 sont sur la ligne 3, un par colonne (2, 3 et 4)
        - le pied de page occupe les colonnes 2 à 4 de la ligne 4 */
}

/* 6. Place chaque bloc dans sa zone avec grid-area et donne-lui sa couleur :

   .entete    -> zone : entete     | couleur de fond : #e94e1b (orange)
   .lateral   -> zone : lateral    | couleur de fond : #ffdd11 (jaune)
   .principal -> zone : principal  | couleur de fond : #1271b8 (bleu)
   .contenu1  -> zone : contenu1   | couleur de fond : #1271b8 (bleu)
   .contenu2  -> zone : contenu2   | couleur de fond : #1271b8 (bleu)
   .contenu3  -> zone : contenu3   | couleur de fond : #1271b8 (bleu)
   .pied      -> zone : pied       | couleur de fond : #e6007e (rose)
*/


/* 7. Style commun à tous les blocs (utilise le sélecteur .conteneur > * ) :
      - padding : 20px
      - border-radius : 25px  (coins arrondis, nouvelle propriété !)
      - font-size : 24px */


/* ===== VERSION MOBILE ===== */

/* 8. Écris une media query pour les écrans de 768px de large ou moins :
      @media (max-width: 768px) {
         ... ton code ici ...
      }

   À l'intérieur, redéfinis .conteneur pour avoir :
   - UNE seule colonne : 1fr
   - des lignes de hauteur automatique : auto
   - les zones empilées dans cet ordre (une par ligne) :
       entete
       lateral
       principal
       contenu1
       contenu2
       contenu3
       pied

   Puis règle les hauteurs minimum (propriété min-height) :
   - .principal : 250px
   - .contenu1, .contenu2, .contenu3 : 80px, avec font-size : 20px
*/
```

---

## Comment tester la version mobile ?

Réduis la largeur de la fenêtre de résultat de CodePen en faisant glisser la barre qui sépare le code du résultat. Dès que la largeur passe sous 768px, les blocs doivent s'empiler.

---

## Check-list finale

- [ ] En version PC, ma page ressemble au schéma (barre latérale jaune à gauche sur toute la hauteur)
- [ ] Les contenus 1, 2 et 3 sont côte à côte, de même largeur
- [ ] Le pied de page est rose, à droite de la barre latérale
- [ ] Les blocs ont des coins arrondis et 15px d'espace entre eux
- [ ] En version mobile, les 7 blocs sont empilés dans le bon ordre
- [ ] J'ai cliqué sur **Save** et je peux envoyer le lien de mon pen

---

## Défis bonus

1. Change `768px` par une autre valeur et observe ce qui se passe.
2. Ajoute une troisième version pour les très petits écrans (`max-width: 480px`) où `font-size` passe à 16px.
3. Change la disposition PC : place la barre latérale à **droite** au lieu de la gauche (il suffit de modifier `grid-template-columns` et `grid-template-areas`).
4. Ajoute un 4ᵉ bloc de contenu et adapte la grille.
