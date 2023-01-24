+++
author = "Paul Mairot"
title = "Expérimentation : ElectronJS"
date = "2023-01-13"
description = "Test de ElectronJS"
tags = [
    "experimentation",
    "js"
]
+++

Test de ElectronJS, un cadre open-source qui permet de créer des applications de bureau multiplateformes en utilisant JavaScript, HTML et CSS. Il est basé sur le moteur Chromium de Google et Node.js, et permet aux développeurs de construire des applications qui fonctionnent sur Windows, Mac et Linux en utilisant une seule base de code. Il est utilisé pour créer des applications de bureau telles que Visual Studio Code, Slack et Discord. <!--more-->

[Lien vers la documentation](https://www.electronjs.org/docs/latest/)

## Comment l'installer ?
ElectronJS peut s'installer simplmenent sur n'importe quel projets utilisant NodeJS.
```
npm install --save-dev electron
```

## Utilisation
Pour cette expérimentation, j'ai créé une simple application TO-DO avec une fonctionalité d'ajout à la liste. Une fois cette application fait, il n'y a qu'à ajouté le package electron et l'ajouter au script de démarrage :
```json
"scripts": {
    "start" : "electron .",
    "test": "echo \"Error: no test specified\" && exit 1"
}
```

Nous devons ensuite configurer le fichier ```main.js``` du projet afin de définir les options basiques d'Electron, comme par exemple la taille de la fenêtre ou le fichier à load lors du démarrage de l'application.

```javascript
const { app, BrowserWindow } = require("electron");
const path = require("path");

const loadMainWindow = () => {
    const mainWindow = new BrowserWindow({
        width : 1200,
        height: 800,
        webPreferences: {
            nodeIntegration: true
        }
    });

    mainWindow.loadFile(path.join(__dirname, "index.html"));
}

app.on("ready", loadMainWindow);

app.on("window-all-closed", () => {
    if (process.platform !== "darwin") {
      app.quit();
    }
});
```


### Notifications
Comme dit précedemment, Electron permet d'utiliser des fonctionnalités propres aux applications desktop. J'ai alors décidé d'implémenter un système de notifications à la TODO-list lors de l'ajout de tâche.

Pour cela rien de plus simple. Il faut commencer par prévoir les notifications dans ```main.js``` en ajoutant les lignes suivants :

```javascript
const { Notification } = require("electron");


ipcMain.handle('show-notification', (event, ...args) => {
    const notification = {
        title: 'New Task',
        body: `Added: ${args[0]}`
    }

    new Notification(notification).show()
});
```

Il faut ensuite créer la notification lors de l'ajout d'une tâche. Notre ```script.js``` gérant l'ajout de tâche ressemblera donc à ceci :

```javascript
const { ipcRenderer } = require('electron');

let list = document.getElementById("list");
let newTask = document.getElementById("newTask");

document.getElementById("addTask").addEventListener('click', () => {
    list.insertAdjacentHTML('beforeend', `<li class="list-group-item">${newTask.value}</li>`)
    ipcRenderer.invoke('show-notification', newTask.value);
    newTask.value = '';
});
```

#### Résultat

![Notification Electron](../ElectronNotification.png)


## Ce que j'ai retenu
J'avais déjà pu utiliser Electron pour des projets personels et professionels. Dans le domaine professionel, ce package m'a permis de fournir une application à des clients afin de leur simplifier l'utilisation de l'application développée.

Electron est très complet et propose de nombreuses fonctionalité d'application desktop (ex.: Les notifications), je pense donc pouvoir le réutiliser dans mon avenir professionnel.