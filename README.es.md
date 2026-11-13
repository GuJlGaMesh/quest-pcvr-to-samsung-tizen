# Cómo jugar a Beat Saber en Quest 3 y mostrar la partida en un televisor Samsung con Tizen

[العربية](README.ar.md) · [中文](README.zh.md) · [English](README.md) · [Français](README.fr.md) · [Русский](README.ru.md) · [Español](README.es.md)

**Un jugador, dos pantallas.** El PC con Windows ejecuta Beat Saber. Virtual Desktop envía el juego al visor Quest 3. Al mismo tiempo, Sunshine captura el escritorio del PC y lo transmite por la red doméstica a Moonlight en un Samsung BU8000. El público ve lo que aparece en el monitor del PC.

**Equipo necesario.** Un PC con Windows y la versión de Beat Saber para PC, un Quest 3 ya configurado para jugar en PCVR con Virtual Desktop y un Samsung BU8000 en la misma red doméstica. El televisor de la prueba tenía Tizen 6.5 y el PC de juego estaba conectado por Ethernet. Se utilizó otro equipo con Windows para instalar la aplicación en el televisor.

## Configuración inicial

1. **En el PC de juego**, instale [Sunshine para Windows](https://github.com/SunshineStream/Sunshine/releases/latest). Abra el [panel local de Sunshine](https://localhost:47990) en ese mismo PC y cree un usuario y una contraseña. Conserve la entrada **Desktop** en la lista de aplicaciones.
2. **En el televisor**, abra **Apps** e introduzca **12345** para acceder al menú de desarrollo. Active **Developer Mode**. En **Host PC IP**, introduzca la dirección IP local del equipo desde el que instalará Moonlight. Reinicie el televisor si ha cambiado la configuración. En la prueba se usó la dirección del equipo de instalación. [Guía de instalación de Moonlight para Tizen](https://github.com/brightcraft/moonlight-tizen/wiki/Installation-Guide)
3. **En el equipo de instalación**, descargue el archivo estándar **Moonlight.wgt** de la [página de versiones de Moonlight Tizen](https://github.com/brightcraft/moonlight-tizen/releases). Instálelo en el televisor con **Apps2Samsung**. En la prueba se reutilizó un certificado Samsung Partner válido para ese televisor. Si es la primera instalación, siga las indicaciones del instalador para crear el certificado. [Apps2Samsung](https://github.com/Apps2Samsung/Apps2Samsung)
4. **En el televisor**, abra Moonlight y seleccione el PC de juego. Si no aparece, añada manualmente la IP local de su conexión Ethernet. Moonlight mostrará un PIN. En el panel de Sunshine del PC de juego, abra **PIN**, seleccione la solicitud del televisor e introduzca el código.

Si usa Apps2Samsung CLI para Windows, ejecute este comando desde la carpeta que contiene la herramienta y el paquete. Sustituya `TV_IP` e `INSTALL_PC_IP` por las direcciones locales del televisor y del equipo de instalación.

```powershell
.\apps2samsung-cli.exe install .\Moonlight.wgt --tv TV_IP --local-ip INSTALL_PC_IP
```

## Para mostrar una partida

Inicie la versión para PC de Beat Saber desde Virtual Desktop en Quest 3. Compruebe que el monitor del PC muestra la vista que quiere compartir. En el televisor, abra **Moonlight → PC de juego → Desktop**. Si el público ve el escritorio de Windows, compruebe primero qué aparece en el monitor que captura Sunshine.

**Resultado de la prueba.** El jugador confirmó que había iniciado Beat Saber. Sunshine registró el emparejamiento del BU8000 y el inicio de una sesión con codificación H.264 por hardware en una RTX 3070, una frecuencia solicitada de 60 fps y captura de audio estéreo. No se anotó qué ventana mostraba el juego ni se midió la latencia de extremo a extremo.
