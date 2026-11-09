# Modules Personnalisés Odoo - community-test

Ce dépôt héberge le code source des modules et personnalisations Odoo 20 (Community) pour l'instance **community-test** sur la plateforme **Prelium Odoo.sh**.

## Architecture des branches

- **`production`** *(Branche par défaut / Production)* :
  Déployée automatiquement sur l'environnement Live de production. Chaque modification validée et mergée sur cette branche est synchronisée avec l'instance de production du client.
- **Branches de Staging** *(ex: `staging`, `staging1`, `staging2`)* :
  Créées automatiquement à la demande lors du déploiement d'un environnement de staging sur Prelium Odoo.sh. Permettent de tester les développements sur des bases de données isolées et neutralisées avant mise en production.

## Structure des modules Odoo

Chaque dossier à la racine de ce dépôt représente un module Odoo contenant son fichier `__manifest__.py` :

```text
.
├── .gitignore
├── README.md
└── mon_module/
    ├── __init__.py
    ├── __manifest__.py
    ├── models/
    │   ├── __init__.py
    │   └── mon_modele.py
    ├── views/
    │   └── mes_vues.xml
    └── security/
        └── ir.model.access.csv
```

## Synchronisation CI/CD

Les conteneurs Odoo montent directement ce dépôt dans `/mnt/extra-addons`. Lorsque vous poussez du code sur la branche `production` (ou vos branches de staging), le webhook GitHub déclenche automatiquement la synchronisation et la mise à jour sur votre instance Odoo.
