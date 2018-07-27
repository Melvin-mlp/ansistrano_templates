# MIGRATION VERS CIRCLECI 2

## CIRCLECI 2

Créer le nouveau dossier de configuration:

```
# On définit une variable temporaire histoire de copier coller les commandes rapidement
export PROJECT_ROOT_PATH="/PATH/TO/PROJECT"
mkdir -p "$PROJECT_ROOT_PATH"/.circleci
```

Importer le template du fichier de configuration Cirleci2:

```
wget -O "$PROJECT_ROOT_PATH"/.circleci/config.yml "https://gist.githubusercontent.com/Melvin-mlp/bea421b4fced65556bc89428bc4a6bf3/raw/67d5f043e922ee111afcdb328e99b1ff7b11d51d/circleci2_config.yml"
```

Modifier le template en fonction de vos besoins.
PS: Toutes les commandes seront exécutées dans le container [6d6c70/php:php7.0-jessie](https://hub.docker.com/r/6d6c70/php/)

## Ansistrano

On s'assure que le dossier de destination soit présent:

```
mkdir -p "$PROJECT_ROOT_PATH"/app/config
```

Importer les templates Ansistrano:

```
wget -O tmp.zip "https://github.com/Melvin-mlp/ansistrano_templates/archive/master.zip" \
&& unzip tmp.zip -d "$PROJECT_ROOT_PATH"/app/config \
&& mv "$PROJECT_ROOT_PATH"/app/config/ansistrano_templates-master "$PROJECT_ROOT_PATH"/app/config/ansistrano \
&& rm -f tmp.zip

unset PROJECT_ROOT_PATH
```

Modifier les templates en fonction de vos besoins.
