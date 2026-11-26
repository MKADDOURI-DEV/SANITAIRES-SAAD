# SANITAIRES SAAD — Site corporate

Site vitrine trilingue (français, anglais, arabe) pour SANITAIRES SAAD SARL,
entreprise d'installations techniques du bâtiment.

- React 19 + Vite + TanStack Start + Tailwind CSS
- Icônes Lucide
- Contenu statique stocké dans le projet (aucune base de données pour les pages)
- Formulaires contact et devis enregistrés via un point d'entrée serveur

---

## 1. Structure du projet

```
src/
  routes/            une page = un fichier (index, a-propos, services, ...)
  components/site/   header, footer, cartes, formulaires, hero de page
  components/home/   sections de la page d'accueil
  content/           textes FR / EN / AR + chemins des images
  lib/i18n.jsx       sélecteur de langue, direction RTL
  lib/server-fns.js  réception des formulaires
public/
  robots.txt, sitemap.xml
```

## 2. Lancer le projet en local

```bash
npm install
npm run dev
```

## 3. Build de production

```bash
npm run build
npm run preview
```

## 4. Récupérer le code source (ZIP / GitHub)

Le projet vit dans l'espace Base44. Pour en obtenir une copie complète :

1. Connectez un dépôt GitHub à l'espace Base44 (synchronisation du code).
2. Clonez ce dépôt, ou téléchargez-le en ZIP depuis GitHub.
3. Le dossier obtenu contient l'intégralité du code, des textes et des images.

## 5. Déployer sur Vercel

1. Importez le dépôt dans Vercel.
2. Build command : `npm run build`
3. Install command : `npm install`
4. Le projet utilise TanStack Start : sélectionnez le preset TanStack Start
   (ou l'adaptateur Vercel correspondant) afin de conserver le rendu serveur.

Le site fonctionne aussi sans rendu serveur pour toutes les pages de contenu :
les textes sont dans `src/content/`. Seuls les formulaires ont besoin d'un
point d'entrée serveur (voir section 6).

## 6. Formulaires contact et devis

Les deux formulaires envoient la demande à `src/lib/server-fns.js`, qui
l'enregistre dans l'entité `QuoteRequest` de la plateforme. Les demandes sont
consultables dans l'espace de gestion des données du site.

**Aucun email n'est envoyé automatiquement.** Pour recevoir une notification,
il faut connecter un service d'envoi d'emails (ou brancher un webhook vers votre
boîte `sanitairesaad@yahoo.fr`).

Hors plateforme (Vercel), remplacez l'appel `base44.entities.QuoteRequest.create`
par votre propre API, un service de formulaires ou une fonction serverless.

## 7. Personnaliser le site

| Élément | Fichier |
| --- | --- |
| Logo | `src/components/site/Logo.jsx` (remplacer le monogramme par le fichier officiel) |
| Images | `src/content/images.js` |
| Textes FR | `src/content/fr.js` |
| Textes EN | `src/content/en.js` |
| Textes AR | `src/content/ar.js` |
| Couleurs / polices | `tailwind.config.js` et `src/index.css` |
| Coordonnées | `company` dans les trois fichiers de contenu |
| Titres et descriptions SEO | fonction `head()` de chaque fichier dans `src/routes/` |

## 8. SEO

- Titres, descriptions et balises Open Graph par page
- `public/robots.txt` et `public/sitemap.xml`
- Remplacez `https://votre-domaine.com` par votre domaine définitif dans ces
  deux fichiers avant la mise en ligne
- Toutes les images ont un texte alternatif descriptif
