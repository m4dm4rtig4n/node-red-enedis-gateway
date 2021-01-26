# node-red-enedis-gateway

Pour l'installation et la mise à jour du flow, j'utilise les APIs de Node-RED afin de faciliter les mises à jours.

Pour plus d'information : https://forum.hacf.fr/t/linky-enedis-gateway/868

**Attention, le flow n'est pas compatible avec InfluxDB >= 2.0. Je conseille pour l'instant de rester en 1.8.**

**Pre-Installation**

Installer les palettes :
- node-red-contrib-credentials
- node-red-contrib-influxdb
- node-red-contrib-unit-converter
- node-red-contrib-stoptimer-varidelay
- node-red-contrib-simple-message-queue

**Installation**
- Crée un flux vide "Enedis" (le nom du flow est important).
- Importer ce flow : https://raw.githubusercontent.com/m4dm4rtig4n/node-red-enedis-gateway/main/import.json
- Renseigné le user_nr & password_nr si vous avez activer l'authenfication Node-RED (laissez vide sinon).
- Lancer l'inject "Import".
- Cliquer sur "Review changes"
- Puis "Merge" ou "Review changes" si vous désirez voir les changements.
- Ne pas oublier d'adapter la configuration des différents nodes (Credential, MQTT, InfluxDB).

**Mise à jour**
- Lancer l'inject "Import" en haut.
- Cliquer sur "Review changes"
- Puis "Merge" ou "Review changes" si vous désirez voir les changements.
- C'est up-to-date :)
- Pour les nodes avec configurations, il faut ouvrir/done chaque nodes pour en reload la config.

### #enjoy

PS : Merci ArminasTV pour cette 1er esquise de subflow d'import/export Github.
Il est encore en phase de test, mais normalement fonctionnel.

# F.A.Q :

* Pourquoi je récupére l'erreur "credentials node sending empty value for msg.user_nr; configured?" ?

Lors de l'import initial, il faut parfois ouvrir le node credential une fois, puis le fermer & deployer afin de set correctement
les variables.

* Pourquoi je récupére l'erreur "TypeError: msg.payload.forEach is not a function" lors de l'importation ?

Probablement parce que vous avez activer l'authentification sur NodeRED et que vous n'avez pas renseigné vos credential
dans le node "credential".
  