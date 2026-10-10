# Dépôt officiel VibOS

Dépôt APT signé pour VibOS Ubuntu/Cinnamon, architecture `amd64`.

## Mises à jour publiées

- `vibapps 0.3.0` : Firefox, Vib Network, fond VibOS et logo V du menu.
- `vibupdater 2.1.0` : icône VibUpdater dédiée.

## Installation sur une VibOS déjà installée

```bash
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://vibosofficial.github.io/vibos-apt/vibos-archive-keyring.asc \
  | sudo tee /etc/apt/keyrings/vibos-archive-keyring.asc >/dev/null
sudo chmod 0644 /etc/apt/keyrings/vibos-archive-keyring.asc
printf '%s\n' \
  'deb [arch=amd64 signed-by=/etc/apt/keyrings/vibos-archive-keyring.asc] https://vibosofficial.github.io/vibos-apt noble main' \
  | sudo tee /etc/apt/sources.list.d/vibos.list >/dev/null
sudo apt update
sudo apt install --only-upgrade vibupdater vibapps
```

Ensuite, lancez **VibUpdater** depuis le menu VibOS et cliquez sur **Rechercher les mises à jour**.

Ne retirez jamais l’option `signed-by` : APT vérifie ainsi la signature `InRelease` avec la clé publique VibOS.
