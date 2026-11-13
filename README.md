# GoldUSD — XAU/USD Trading Desk

Interface web GoldUSD et petit serveur Node.js de départ. GitHub Pages peut publier le site statique et les profils de démonstration; il ne peut pas exécuter les routes serveur d'inscription. Pour les vrais comptes, lancer `server.js` sur Oracle ou un autre hébergeur Node.js et servir l'interface et `/api` depuis le même domaine.

## Profils de démonstration

Sur GitHub Pages, localhost ou le fichier local, ouvrir Connexion/Créer un compte puis choisir New, Silver, Gold ou VIP. Ce sont des profils temporaires dans le navigateur : aucune inscription ni sauvegarde réelle. Ils servent à parcourir les états d'accès. Les abonnements payants et le paiement PayPal ne sont pas activés dans ce paquet de départ; aucune somme ne sera débitée.

## Démarrer le serveur

1. Installer Node.js 20 ou plus récent.
2. Dans ce dossier, exécuter `npm install` puis `npm start`.
3. Le serveur ouvre l’application sur `http://localhost:3000` et crée sa base SQLite automatiquement.
4. Sur Oracle, copier `.env.example` en `.env`, configurer le chemin de base et le chemin privé du PDF. Conserver `.env`, la base et le PDF hors de GitHub.
5. Mettre un proxy HTTPS (Nginx ou Caddy) devant le serveur avant d’accepter des utilisateurs.

Le serveur accepte les comptes gratuits et les connexions. Les formules payantes répondent volontairement « paiement non configuré » et ne donnent pas l’accès premium. Avant un lancement public, ajouter confirmation d’e-mail, récupération de mot de passe, protection anti-abus et flux de paiement PayPal/webhook vérifié.

## Guide PDF privé

Déposer `GoldUSD_Guide_Trading_XAUUSD.pdf` sur Oracle au chemin défini par `PRIVATE_EBOOK_PATH`, par défaut `/var/lib/goldusd/GoldUSD_Guide_Trading_XAUUSD.pdf`. Le PDF ne doit pas être placé dans le dépôt public. La route `/api/ebook` est réservée à une session active dont la formule est premium. Pour le moment, le serveur n’active aucun paiement et les comptes payants ne peuvent pas être créés.

## Personnalisation

Modifier `config.js` : numéro WhatsApp et nom du gestionnaire en haut du fichier. Remplacer `2126XXXXXXXX` avant publication. WhatsApp reste un lien de contact; il ne reçoit aucune inscription ni demande d’abonnement. Le graphique est un espace d’intégration et nécessite une adresse distincte autorisée.

## Fichiers

- `index.html` : sections Marché, Analyses, Calculateur, Bibliothèque, Équipe et Contact.
- `style.css` : palette obsidienne, ardoise, blanc et or champagne, adaptée au mobile.
- `app.js` : navigation, profils démo, calculateur et appels API.
- `config.js` : coordonnées publiques modifiables; aucun secret.
- `server.js` : routes de comptes, sessions SQLite et téléchargement PDF protégé.
- `.env.example` : options privées à configurer sur le serveur.
- `.gitignore` : exclut secrets, base de données et dépendances.

Le contenu de démonstration n'est pas un conseil financier. Les marchés comportent un risque de perte.
