#Cooking Smart

**Cooking Smart** is a responsive, local-first recipe companion: enter the ingredients you have, choose a few preferences, and receive a practical recipe without any API key or paid dependency.

## Run locally

This is a static ES module application. Serve the project folder with any local web server, then open the shown URL:

```bash
python3 -m http.server 8000
```

Visit `http://localhost:8000` in Chrome, Edge, or Firefox. (Using a server rather than opening `index.html` directly allows ES modules to load consistently.)

## Project structure

```text
index.html              App shell, semantic header/navigation/main structure
css/style.css           Mobile-first tokens, layout, components, states, animation
css/responsive.css      Tablet and desktop layout enhancements
js/data.js              Searchable local recipe catalogue and category list
js/navigation.js        Four-screen hash router and active-navigation state
js/recipes.js           Local recipe templates and future AI replacement seam
js/storage.js           Safe LocalStorage CRUD helpers
js/app.js               View rendering, interaction handling, and app state
```

## Navigation

The hash router exposes exactly four main screens: `#home`, `#generate`, `#recipe`, and `#saved`. Persistent desktop navigation and a mobile bottom navigation keep Home, Generate, and Saved available throughout; recipe pages also include contextual Home, ingredients, and saved actions.

## LocalStorage

Saved recipes are stored under the `cooking-smart-recipes` key. `storage.js` provides `saveRecipe`, `getSavedRecipes`, `deleteRecipe`, and `clearSavedRecipes`, each guarded so storage failures show a friendly UI message instead of breaking the app.

## Future AI integration

`js/recipes.js` contains `generateRecipeWithAI()`. It currently returns the local template-based result, but is the deliberate replacement point for a future backend API call. Keep AI credentials on a server and retain the recipe object shape so the rest of the UI stays unchanged.

## Current scope

Version 1 uses deterministic local recipe templates rather than live AI, and food imagery is built from lightweight original CSS/emoji visuals rather than external image assets. Recipes are stored per browser/device via LocalStorage and are not synced between devices.
css/responsive.css
css/responsive.css
