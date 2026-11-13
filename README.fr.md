# Jouer à Beat Saber sur Quest 3 et montrer la partie sur un téléviseur Samsung sous Tizen

[العربية](README.ar.md) · [中文](README.zh.md) · [English](README.md) · [Français](README.fr.md) · [Русский](README.ru.md) · [Español](README.es.md)

**Un joueur, deux écrans.** Le PC Windows fait tourner Beat Saber. Virtual Desktop transmet le jeu au casque Quest 3. En parallèle, Sunshine capture le bureau du PC et le transmet sur le réseau domestique à Moonlight sur un Samsung BU8000. Le public voit ce qui apparaît sur le moniteur du PC.

**Matériel nécessaire.** Un PC Windows équipé de la version PC de Beat Saber, un Quest 3 déjà configuré pour la VR sur PC avec Virtual Desktop et un Samsung BU8000 sur le même réseau domestique. Lors de l’essai, le téléviseur utilisait Tizen 6.5 et le PC de jeu était relié au réseau par Ethernet. Un autre ordinateur Windows a servi à installer l’application sur le téléviseur.

## Configuration initiale

1. **Sur le PC de jeu**, installez [Sunshine pour Windows](https://github.com/SunshineStream/Sunshine/releases/latest). Ouvrez le [panneau local de Sunshine](https://localhost:47990) sur ce même PC et créez un identifiant et un mot de passe. Conservez l’entrée **Desktop** dans la liste des applications.
2. **Sur le téléviseur**, ouvrez **Apps** et saisissez **12345** pour accéder au menu développeur. Activez **Developer Mode**. Dans **Host PC IP**, indiquez l’adresse IP locale de l’ordinateur qui servira à installer Moonlight. Redémarrez le téléviseur si vous avez modifié ce réglage. Lors de l’essai, cette adresse était celle de l’ordinateur utilisé pour l’installation. [Guide d’installation de Moonlight pour Tizen](https://github.com/brightcraft/moonlight-tizen/wiki/Installation-Guide)
3. **Sur l’ordinateur d’installation**, téléchargez le fichier standard **Moonlight.wgt** depuis la [page des versions de Moonlight Tizen](https://github.com/brightcraft/moonlight-tizen/releases). Installez-le sur le téléviseur avec **Apps2Samsung**. Lors de l’essai, l’outil a réutilisé un certificat Samsung Partner déjà valide pour ce téléviseur. Pour une première installation, suivez les indications de l’outil pour créer le certificat. [Apps2Samsung](https://github.com/Apps2Samsung/Apps2Samsung)
4. **Sur le téléviseur**, ouvrez Moonlight et sélectionnez le PC de jeu. Au besoin, ajoutez manuellement l’adresse IP locale de son interface Ethernet. Moonlight affiche un code PIN. Dans le panneau Sunshine du PC de jeu, ouvrez **PIN**, sélectionnez la demande du téléviseur et saisissez le code.

Avec Apps2Samsung CLI pour Windows, exécutez cette commande depuis le dossier contenant l’outil et le paquet. Remplacez `TV_IP` et `INSTALL_PC_IP` par les adresses locales du téléviseur et de l’ordinateur d’installation.

```powershell
.\apps2samsung-cli.exe install .\Moonlight.wgt --tv TV_IP --local-ip INSTALL_PC_IP
```

## Pour montrer une partie

Lancez la version PC de Beat Saber depuis Virtual Desktop dans le Quest 3. Vérifiez que le moniteur du PC affiche la vue que vous souhaitez partager. Sur le téléviseur, ouvrez **Moonlight → PC de jeu → Desktop**. Si le public voit le bureau Windows, vérifiez d’abord ce qui est affiché sur le moniteur capturé par Sunshine.

**Résultat de l’essai.** Le joueur a confirmé avoir lancé Beat Saber. Sunshine a enregistré l’appairage du BU8000 et le début d’une session avec encodage matériel H.264 sur une RTX 3070, une cadence demandée de 60 images/s et une capture audio stéréo. La fenêtre utilisée pour montrer le jeu n’a pas été consignée et la latence de bout en bout n’a pas été mesurée.
