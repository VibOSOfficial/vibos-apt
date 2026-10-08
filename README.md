# VibOS Official APT Repository

Dépôt signé pour VibOS basé sur Debian 13 (Trixie), architecture amd64.

## Publication

Publier le contenu de ce dossier à la racine de GitHub Pages du dépôt `vibos-apt`.
L’URL attendue sera : `https://vibosofficial.github.io/vibos-apt/`

## Installation sur VibOS 1.0.1

Remplacer `vibosofficial` si le nom GitHub final est différent :

```bash
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://vibosofficial.github.io/vibos-apt/vibos-archive-keyring.asc \
  | sudo tee /etc/apt/keyrings/vibos-archive-keyring.asc >/dev/null
sudo chmod 0644 /etc/apt/keyrings/vibos-archive-keyring.asc
printf '%s\n' \
  'deb [arch=amd64 signed-by=/etc/apt/keyrings/vibos-archive-keyring.asc] https://vibosofficial.github.io/vibos-apt trixie main' \
  | sudo tee /etc/apt/sources.list.d/vibos.list >/dev/null
sudo apt update
sudo apt install --only-upgrade vibupdater vibapps
```

VibUpdater peut ensuite rechercher et installer les mises à jour normalement.

## Sécurité

Ne pas retirer `signed-by`. APT doit vérifier `InRelease` avec la clé publique VibOS.
La clé privée de signature ne doit jamais être publiée.
