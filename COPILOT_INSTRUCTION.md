# 🩺 Instructions COPILOT - Site Dr. Doha Ophtalmologue

## 📋 Vue d'ensemble du projet

Site web professionnel one-page pour ophtalmologue spécialisé en chirurgie réfractive. Design moderne, animations élégantes, et optimisé pour la conversion de patients.

**Technologies utilisées :**

- HTML5 sémantique
- Tailwind CSS + CSS personnalisé
- JavaScript Vanilla
- Font Awesome (icônes)
- Google Fonts (Inter)

---

## 🎨 Comment modifier le contenu

### 1. Informations du docteur

**Fichier :** `index.html`
**Section :** `#about`

```html
<!-- Modifier ces éléments -->
<h2>Dr. Doha</h2>
<!-- Nom du docteur -->
<h3>Ophtalmologue Expert</h3>
<!-- Titre -->
<p>Avec plus de 15 ans d'expérience...</p>
<!-- Bio -->
```

### 2. Coordonnées de contact

**Fichier :** `index.html`
**Section :** `#contact`

```html
<!-- Adresse -->
<p>123 Avenue de la Santé<br />75014 Paris, France</p>

<!-- Téléphone -->
<a href="tel:+33123456789">+33 1 23 45 67 89</a>

<!-- WhatsApp -->
<a href="https://wa.me/33123456789">+33 1 23 45 67 89</a>
```

### 3. Horaires d'ouverture

**Fichier :** `index.html`
**Section :** `#contact`

```html
<div class="text-white/90 space-y-1">
  <p>Lundi - Vendredi: 8h30 - 18h30</p>
  <p>Samedi: 9h00 - 13h00</p>
  <p>Dimanche: Fermé</p>
</div>
```

### 4. Services proposés

**Fichier :** `index.html`
**Section :** `#services`

Modifier le contenu des cartes de service :

```html
<h3>Nom du service</h3>
<p>Description du service...</p>
```

### 5. Articles de blog

**Fichier :** `index.html`
**Section :** `#blogs`

```html
<span>Date</span>
<h3>Titre de l'article</h3>
<p>Extrait de l'article...</p>
```

---

## 🎨 Comment modifier les couleurs

### Couleur principale (#0c4853)

**Fichier :** `styles.css`

```css
:root {
  --primary-color: #0c4853; /* Couleur principale */
  --primary-light: #0f5a67; /* Version claire */
  --primary-dark: #083840; /* Version foncée */
}
```

**ET** `index.html` (config Tailwind) :

```javascript
tailwind.config = {
  theme: {
    extend: {
      colors: {
        primary: "#0c4853" /* Nouvelle couleur */,
        "primary-light": "#0f5a67" /* Version claire */,
        "primary-dark": "#083840" /* Version foncée */,
      },
    },
  },
};
```

### Classes Tailwind disponibles

Après modification, utilisez ces classes :

- `bg-primary` (arrière-plan)
- `text-primary` (texte)
- `border-primary` (bordure)
- `hover:bg-primary-dark` (hover states)

---

## 🖼️ Comment changer les images

### 1. Images principales

Remplacez les fichiers dans `/assets/` :

- `doctor-photo.jpg` - Photo du docteur (800x800px)
- `smile-illustration.jpg` - Illustration SMILE
- `lasik-illustration.jpg` - Illustration LASIK
- `pkr-illustration.jpg` - Illustration PKR
- `blog1.jpg`, `blog2.jpg`, `blog3.jpg` - Images de blog

### 2. Image de fond Hero

**Fichier :** `styles.css`

```css
.bg-hero-pattern {
  background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.6)),
    url("NOUVELLE_IMAGE_URL");
}
```

### 3. Google Maps

**Fichier :** `index.html`
**Section :** `#contact`

1. Aller sur Google Maps
2. Chercher votre adresse
3. Cliquer "Partager" > "Intégrer une carte"
4. Copier le code iframe
5. Remplacer l'iframe existant

---

## ⚙️ Comment modifier les animations

### 1. Vitesse des animations

**Fichier :** `styles.css`

```css
/* Modifier les durées */
.animate-fade-up {
  animation: fadeUp 1s ease-out forwards; /* Changer 1s */
}

/* Transitions */
.service-card {
  transition: all 0.3s ease; /* Changer 0.3s */
}
```

### 2. Désactiver les animations

**Fichier :** `script.js`

```javascript
// Commenter cette ligne pour désactiver les animations scroll
// initScrollAnimations();
```

### 3. Délais d'animation

**Fichier :** `styles.css`

```css
.animation-delay-300 {
  animation-delay: 0.3s; /* Modifier le délai */
}
```

---

## 📱 Comment gérer les sous-menus "Chirurgie Réfractive"

### 1. Ajouter une nouvelle technique

**Fichier :** `index.html`

```html
<!-- Ajouter un bouton -->
<button class="technique-btn" data-technique="nouvelle-technique">
  Nouvelle Technique
</button>
```

**Fichier :** `script.js`

```javascript
// Ajouter dans techniqueData
const techniqueData = {
  // ... techniques existantes
  "nouvelle-technique": {
    title: "Nouvelle Technique",
    description: "Description...",
    benefits: ["Avantage 1", "Avantage 2"],
    image: "assets/nouvelle-technique.jpg",
    cta: "Consultation",
  },
};
```

### 2. Modifier une technique existante

**Fichier :** `script.js`

Modifier l'objet `techniqueData` dans la fonction `showTechniqueContent()`.

---

## 📧 Comment configurer le formulaire de contact

### 1. Intégration avec un service email

#### Option A : Formspree (Recommandé)

1. Aller sur https://formspree.io/
2. Créer un compte gratuit
3. Créer un nouveau formulaire
4. **Modifier `script.js`** :

```javascript
function handleFormSubmission(form) {
  const formData = new FormData(form);

  fetch("https://formspree.io/f/VOTRE_ID", {
    method: "POST",
    body: formData,
    headers: {
      Accept: "application/json",
    },
  })
    .then((response) => {
      if (response.ok) {
        showNotification("Message envoyé avec succès!", "success");
        form.reset();
      } else {
        throw new Error("Erreur réseau");
      }
    })
    .catch((error) => {
      showNotification("Erreur lors de l'envoi. Réessayez.", "error");
    });
}
```

#### Option B : Netlify Forms

1. Ajouter `data-netlify="true"` au formulaire
2. **Modifier `index.html`** :

```html
<form id="contact-form" data-netlify="true" netlify-honeypot="bot-field"></form>
```

#### Option C : EmailJS

1. Créer compte sur EmailJS
2. Configurer service email
3. Intégrer le SDK EmailJS

### 2. Ajouter des champs au formulaire

**Fichier :** `index.html`

```html
<!-- Nouveau champ -->
<div>
  <label class="block text-gray-700 font-semibold mb-2">Nouveau champ</label>
  <input
    type="text"
    name="nouveau_champ"
    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:border-primary focus:ring-2 focus:ring-primary/20 outline-none transition-all"
  />
</div>
```

---

## 🚀 Comment déployer le site

### Option 1 : Netlify (Recommandé - Gratuit)

1. **Préparer les fichiers :**

   ```bash
   # Votre structure doit être :
   /
   ├── index.html
   ├── styles.css
   ├── script.js
   └── assets/
       └── *.jpg
   ```

2. **Déployer :**

   - Aller sur https://netlify.com/
   - Glisser-déposer le dossier complet du site
   - Ou connecter un repo GitHub

3. **Configuration domaine personnalisé :**
   - Dans Netlify Dashboard > Domain settings
   - Ajouter votre domaine
   - Configurer les DNS

### Option 2 : Vercel (Gratuit)

1. **Installation :**

   ```bash
   npm i -g vercel
   vercel login
   vercel
   ```

2. **Ou via interface web :**
   - Aller sur https://vercel.com/
   - Importer depuis GitHub

### Option 3 : GitHub Pages (Gratuit)

1. **Créer un repo GitHub**
2. **Uploader les fichiers**
3. **Activer Pages :**
   - Settings > Pages
   - Source: Deploy from branch
   - Branch: main

### Option 4 : Hébergement traditionnel (cPanel)

1. **Créer un dossier sur votre serveur**
2. **Uploader via FTP tous les fichiers**
3. **Pointer votre domaine vers ce dossier**

---

## 📊 Comment configurer Google Analytics

### 1. Créer un compte GA4

1. Aller sur https://analytics.google.com/
2. Créer une propriété
3. Récupérer l'ID de mesure (G-XXXXXXXXXX)

### 2. Intégrer le code

**Fichier :** `index.html` (dans `<head>`)

```html
<!-- Google Analytics -->
<script
  async
  src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"
></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag() {
    dataLayer.push(arguments);
  }
  gtag("js", new Date());
  gtag("config", "G-XXXXXXXXXX");
</script>
```

### 3. Événements personnalisés

Le script `script.js` inclut déjà le tracking pour :

- Soumissions de formulaire
- Clics sur CTA
- Scroll depth
- Erreurs JavaScript

---

## 🔧 Comment ajouter de nouveaux blogs/articles

### 1. Ajouter un article de blog

**Fichier :** `index.html`
**Section :** `#blogs`

```html
<!-- Nouvel article -->
<article
  class="blog-card bg-white rounded-xl shadow-lg overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 animate-on-scroll"
>
  <img
    src="assets/nouveau-blog.jpg"
    alt="Titre"
    class="w-full h-48 object-cover"
  />
  <div class="p-6">
    <span class="text-primary text-sm font-semibold">Date</span>
    <h3 class="text-xl font-bold text-gray-800 mb-3 mt-2">
      Titre de l'article
    </h3>
    <p class="text-gray-600 mb-4">Extrait de l'article...</p>
    <a
      href="blog-article.html"
      class="text-primary font-semibold hover:underline"
    >
      Lire l'article complet →
    </a>
  </div>
</article>
```

### 2. Créer une page blog séparée

**Créer :** `blog.html`

Utiliser la même structure que `index.html` mais avec :

- Section hero adaptée
- Grille d'articles complète
- Pagination si nécessaire

### 3. Articles individuels

**Créer :** `blog/article-slug.html`

Structure recommandée :

```html
<!DOCTYPE html>
<html lang="fr">
  <head>
    <!-- Meta tags spécifiques à l'article -->
  </head>
  <body>
    <!-- Navigation -->
    <!-- Article complet -->
    <!-- Articles similaires -->
    <!-- Footer -->
  </body>
</html>
```

---

## 📱 Comment optimiser pour mobile

### 1. Tester la responsivité

- Utiliser DevTools (F12) > Mode responsive
- Tester sur vrais appareils
- Outils : BrowserStack, LambdaTest

### 2. Ajuster les breakpoints

**Fichier :** `styles.css`

```css
/* Ajuster si nécessaire */
@media (max-width: 768px) {
  /* Styles mobile */
}

@media (min-width: 768px) and (max-width: 1024px) {
  /* Styles tablet */
}
```

### 3. Performance mobile

- Optimiser images (WebP, compression)
- Lazy loading pour images
- Minifier CSS/JS en production

---

## ⚡ Comment optimiser les performances

### 1. Images

```bash
# Compression recommandée
# JPEG : 85-90% qualité
# PNG : TinyPNG
# WebP : conversion recommandée
```

### 2. CSS/JS minification

**Pour production :**

- CSS : https://cssminifier.com/
- JS : https://javascript-minifier.com/

### 3. Lazy loading

**Fichier :** `index.html`

```html
<!-- Ajouter loading="lazy" aux images -->
<img src="image.jpg" alt="..." loading="lazy" />
```

### 4. Préchargement

**Fichier :** `index.html` (dans `<head>`)

```html
<!-- Précharger ressources critiques -->
<link rel="preload" href="styles.css" as="style" />
<link rel="preload" href="script.js" as="script" />
```

---

## 🔒 Sécurité et RGPD

### 1. Politique de confidentialité

**Créer :** `privacy-policy.html`

Inclure :

- Collecte de données
- Utilisation des cookies
- Droits utilisateurs
- Contact DPO

### 2. Mentions légales

**Créer :** `legal-notice.html`

Inclure :

- Informations éditeur
- Hébergement
- Propriété intellectuelle
- Responsabilité

### 3. Cookies et tracking

**Ajouter banner cookies si nécessaire :**

```html
<!-- Banner cookies -->
<div
  id="cookie-banner"
  class="fixed bottom-0 left-0 right-0 bg-gray-900 text-white p-4 z-50"
>
  <div class="container mx-auto flex justify-between items-center">
    <p>Nous utilisons des cookies pour améliorer votre expérience.</p>
    <button onclick="acceptCookies()" class="bg-primary px-4 py-2 rounded">
      Accepter
    </button>
  </div>
</div>
```

---

## 🐛 Résolution de problèmes courants

### 1. Les animations ne fonctionnent pas

- Vérifier que `script.js` est bien chargé
- Ouvrir Console (F12) pour voir les erreurs
- Vérifier que Intersection Observer est supporté

### 2. Le formulaire ne s'envoie pas

- Vérifier la configuration du service email
- Tester en console les erreurs réseau
- Vérifier les champs requis

### 3. Images qui ne s'affichent pas

- Vérifier les chemins relatifs
- Vérifier que les fichiers existent
- Tester avec images en ligne temporairement

### 4. Site lent sur mobile

- Compresser les images
- Vérifier la taille des ressources
- Utiliser PageSpeed Insights

### 5. Problèmes de responsive

- Tester avec vrais appareils
- Utiliser DevTools responsive mode
- Vérifier les breakpoints CSS

---

## 📞 Support et maintenance

### Structure des fichiers

```
dr-doha/
├── index.html          # Page principale
├── styles.css          # Styles personnalisés
├── script.js           # JavaScript
├── assets/             # Images et ressources
│   ├── README.md       # Guide des images
│   └── *.jpg          # Images du site
├── COPILOT_INSTRUCTION.md  # Ce fichier
└── README.md           # Documentation générale
```

### Versioning recommandé

- Utiliser Git pour versioning
- Créer branches pour nouvelles fonctionnalités
- Sauvegarder avant modifications importantes

### Monitoring

- Google Analytics pour le trafic
- Search Console pour SEO
- Uptime monitoring (UptimeRobot)

---

## 🎯 Checklist de lancement

### Avant mise en ligne :

- [ ] Remplacer toutes les informations placeholder
- [ ] Ajouter vraies images dans `/assets/`
- [ ] Configurer formulaire de contact
- [ ] Tester sur mobile et desktop
- [ ] Configurer Google Analytics
- [ ] Vérifier liens internes/externes
- [ ] Optimiser images
- [ ] Ajouter politique de confidentialité
- [ ] Tester vitesse avec PageSpeed Insights

### Après mise en ligne :

- [ ] Configurer domaine personnalisé
- [ ] Soumettre sitemap à Google
- [ ] Configurer redirections si nécessaire
- [ ] Mettre en place monitoring
- [ ] Sauvegarder site complet

---

**🩺 Site Dr. Doha prêt pour le succès !**

_Pour toute question technique, n'hésitez pas à consulter cette documentation ou à demander de l'aide._
