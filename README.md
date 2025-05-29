# TP React Hooks - Application de Gestion de Produits

## Rendu

### Exercice 1 : État et Effets 

J’ai utilisé useState pour stocker la valeur saisie dans le champ de recherche (searchTerm). Avec useEffect, j’ai appliqué un délai de 300ms (debounce) avant de filtrer les produits, ce qui évite d’exécuter la recherche à chaque frappe. Le filtrage est fait via products.filter en comparant les titres en minuscules.
Cela améliore la performance et l'expérience utilisateur en limitant les calculs inutiles.

Difficultés rencontrées :
Au début, je n’avais pas nettoyé le timeout dans le useEffect (avec clearTimeout), ce qui causait plusieurs appels simultanés. J’ai corrigé cela en ajoutant la fonction de nettoyage dans le retour du useEffect.

![alt text](<images/Ex 1.png>)

### Exercice 2 : Context et Internationalisation

J’ai créé un LanguageContext avec createContext et un provider qui stocke la langue sélectionnée (fr, en, etc.). Ce contexte est utilisé dans toute l’application pour afficher les textes dans la langue choisie.

Le sélecteur de langue est un simple <select> dans le header qui met à jour la langue dans le contexte. Les composants utilisent ensuite useContext(LanguageContext) pour afficher les textes traduits.

Difficultés rencontrées :
La gestion des traductions dans tous les composants demande de bien passer le contexte. Au début, certains composants n’étaient pas mis à jour car ils ne consommaient pas correctement le contexte.

![alt text](<images/Ex 2.png>)

### Exercice 3 : Hooks Personnalisés

J’ai extrait la logique de debounce dans un hook useDebounce qui prend une valeur et un délai, et renvoie une valeur "décalée" mise à jour uniquement après le délai. Cela permet de réutiliser facilement le debounce dans différents composants.

Le hook useLocalStorage permet de stocker et récupérer une valeur dans le localStorage, avec synchronisation automatique via un useState et useEffect. Cela facilite la persistance des préférences utilisateur (comme la langue ou le thème).

Difficultés rencontrées :
Bien gérer les effets de synchronisation avec localStorage, notamment lors de la mise à jour des valeurs, et éviter des boucles infinies dans les hooks.

![alt text](<images/Ex 3.png>)

### Exercice 4 : Gestion Asynchrone et Pagination

J’ai ajouté un bouton de rechargement qui rappelle la fonction de récupération des données. J’ai aussi implémenté la pagination avec des états pour la page courante et le nombre total de pages, et deux boutons "Précédent" et "Suivant" pour naviguer.

Le chargement est affiché via un spinner Bootstrap pendant que les données sont récupérées. En cas d’erreur, un message d’alerte est affiché.

Difficultés rencontrées :
Gérer la pagination avec les changements de page sans recharger toute la page, et s’assurer que les boutons sont désactivés aux bornes (page 1 et dernière page).

![alt text](<images/Ex 4.png>)

### Remarques générales

Toutes les captures d’écran sont dans le dossier images à la racine du projet.

Chaque exercice a fait l’objet d’au moins un commit avec un message clair mentionnant le numéro de l’exercice (ex : feat: exercice 1 - recherche et debounce)