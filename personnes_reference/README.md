# Photos de référence

Placez ici les photos des personnes que l'application doit reconnaître.

- Formats acceptés : `.jpg`, `.jpeg`, `.png`
- Le **nom du fichier** devient le nom affiché par l'application : `Ahmed_1.jpg` → `Ahmed`, `Sara.jpg` → `Sara`
- Le suffixe `_N` est automatiquement supprimé : plusieurs photos (`Ahmed_1.jpg`, `Ahmed_2.jpg`) regroupent la même personne
- Une photo par personne suffit, mais plusieurs angles améliorent la précision

Exemple :

```
personnes_reference/
├── Ahmed_1.jpg
├── Ahmed_2.jpg
└── Sara.jpg
```

> Ce fichier existe pour que le dossier soit versionné dans Git (Git ne suit pas les dossiers vides). Vous pouvez le conserver ou le supprimer après avoir ajouté vos photos.
