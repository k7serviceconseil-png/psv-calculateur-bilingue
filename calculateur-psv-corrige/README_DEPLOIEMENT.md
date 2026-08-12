# PSV Calculator Global

Ce dépôt contient les deux versions du calculateur PSV Global.

- `/fr/` : français, avec CAD, EUR et CHF.
- `/en/` : anglais, avec CAD, USD, GBP et AUD.
- `/` : choix de la langue.

## Netlify

Connecter ce dépôt à un seul projet Netlify. Aucun script de construction n'est
requis. Le dossier de publication est `.` et le fichier `netlify.toml` contient
déjà ce réglage.

Après validation du déploiement, ajouter le domaine `calculator.psv-global.com`
dans la gestion des domaines. Un sous-domaine de psv-global.com vaut mieux
qu'une adresse `netlify.app` : l'autorité acquise revient au domaine principal.

Ne pas activer GA4 avant d'avoir ajouté l'identifiant officiel et le mécanisme
de consentement approprié.

## Mise à jour du 12 août 2026 — nouvelle tarification

Le calculateur affichait encore l'ancienne grille. Corrigé :

| Marché | Avant | Après |
|---|---|---|
| Canada · international francophone | 125 CAD | **495 CAD** |
| France · Belgique | 80 EUR | **310 EUR** |
| Suisse | 80 CHF | **300 CHF** |

Le ratio se recalcule automatiquement : le coût estimé divisé par le prix du
marché sélectionné. Aucune autre modification n'était nécessaire, la logique
étant déjà dynamique.

**Bouton d'appel à l'action** : il menait vers `/commande/`, une grille de prix.
Il mène maintenant vers `/fiche-de-poste/`, conformément au nouveau parcours —
décrire le poste d'abord, voir le prix ensuite. Le paramètre `?market=` est
conservé, le marché choisi dans le calculateur suit donc le visiteur.

**Consentement** : une seconde case, facultative et non précochée, a été ajoutée
pour le suivi commercial. La Loi 25 exige un consentement distinct par finalité :
répondre à une demande d'analyse et solliciter commercialement sont deux
finalités différentes. La première case reste obligatoire, la seconde ne l'est
pas — et le texte le dit.

Les avis de confidentialité ont été alignés en conséquence, et les coordonnées
du responsable de la protection des renseignements personnels y figurent
désormais, comme l'exige la loi.

## Version anglaise — corrigée le 12 août 2026

| Marché | Avant | Après |
|---|---|---|
| Canada | 125 CAD | **495 CAD** |
| États-Unis · international | 90 USD | **350 USD** |
| Royaume-Uni | 70 GBP | **270 GBP** |
| Australie | 130 AUD | **500 AUD** |

Bouton d'appel à l'action redirigé vers `/en/role-brief/?market=`, seconde case
de consentement ajoutée, avis de confidentialité aligné.

Les huit prix des deux calculateurs correspondent maintenant exactement aux
montants des liens de paiement Stripe.

## À ne pas oublier lors d'une révision tarifaire

Le prix figure à **trois** endroits distincts, dans **trois dépôts** différents :

1. Stripe — les douze liens de paiement
2. `regional-pricing.js` du site principal
3. `fr/index.html` et `en/index.html` de ce dépôt

Les deux premiers sont proches l'un de l'autre ; le troisième est facile à
oublier. Toute modification de prix doit passer par les trois.
