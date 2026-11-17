# Page de capture Grimoire (LM05)

En ligne : https://grimoire.nicolasdequiedt.com

Deux pages statiques, sans build.

- `index.html` : page de capture (email seul). Le formulaire envoie l'inscription au formulaire Brevo « FORM GRIMOIRE », puis ouvre `/acces`.
- `acces.html` : « Accès débloqué » (3,8 s), puis redirection vers la page vidéo Podia `https://www.nicolasdequiedt.com/video_grimoire`. Un lien de secours reste affiché.
- `assets/` : jaquette (`jaquette.webp`), fond flouté (`fond.jpg`), image de partage (`og.jpg`, 1200x630), polices hébergées ici (aucun appel à Google Fonts).

Le Grimoire lui-même est envoyé par le mail transactionnel de l'automatisation Brevo, pas par cette page.

## À changer un jour

- Adresse du formulaire Brevo : `CONFIG.brevoUrl` dans `index.html`.
- Page vidéo : `VIDEO_URL` dans `acces.html` (et le lien de secours juste au-dessus), plus la balise `noscript`.
- Durée de l'écran « Accès débloqué » : `TOTAL_MS` dans `acces.html` (et la durée de l'animation `fill` dans le CSS).

## Source de trafic

`?src=youtube-xxx` est lu par la page et envoyé à Brevo dans le champ `SOURCE`. Il n'est enregistré que si l'attribut `SOURCE` existe dans Brevo (oui) ET qu'il est ajouté au formulaire « FORM GRIMOIRE » en champ caché, formulaire republié (pas encore fait au 17/11/2026).

## Limite à connaître

L'envoi vers Brevo se fait en `no-cors` : la page ne peut pas lire la réponse de Brevo. Elle détecte une panne réseau, mais pas un refus de Brevo (captcha activé, formulaire modifié). Après toute modification du formulaire Brevo, refaire un test avec une vraie adresse.

## Versions

- V01 (17/11/2026) : première version, gabarit Afuera (LM04) adapté au Grimoire V2 (24 fiches).
