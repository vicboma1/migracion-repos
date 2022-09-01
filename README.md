# migracion-repos

```
#!/bin/bash

REPO=$1
SOURCE_USER=$2
SOURCE_PATH=$3
TARGET_PATH=$4
URL_CLONE=https://$SOURCE_USER@$SOURCE_PATH/$REPO.git
URL_NUEVO_REPO=https://$TARGET_PATH/$REPO.git

git clone --bare $URL_CLONE
cd $REPO.git

# crear el repo en el target nuevo (gitlab/github....) y poner rama 'default' igual que el source

git fetch -u $URL_CLONE +refs/heads/*:refs/heads/*
git fetch -u $URL_CLONE +refs/tags/*:refs/tags/*
git fetch -u $URL_CLONE +refs/notes/*:refs/notes/*

git fetch --all

git push --mirror $URL_NUEVO_REPO

```


Ej

```
REPO=prueba-migracion
SOURCE_USER=vicboma
SOURCE_PATH=bitbucket.org/projects/
TARGET_PATH=gitlab.alfatecsistemas.es/projects/otros
```

