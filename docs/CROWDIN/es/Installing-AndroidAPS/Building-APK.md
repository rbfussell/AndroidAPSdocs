# Construyendo la APK

## Construyela tú mismo en lugar de descargarla

**AndroidAPS no está disponible como descarga debido a la regulación de los dispositivos mediales. ¡Es legal construir la aplicación para su propio uso, pero no debe dar una copia a los demás! Consulte la página [FAQ](../Getting-Started/FAQ.md) para obtener detalles.**

## Notas importantes

* Por favor utilice **[Android Studio Versión 4.1.1](https://developer.android.com/studio/)** o más reciente para construir el apk.
* [Windows 10 sistemas de 32 bits](../Installing-AndroidAPS/troubleshooting_androidstudio#unable-to-start-daemon-process) no son compatibles con Android Studio 4.1.1.

**Configuración bajo demanda** no está soportada por la versión actual del plugin de Gradle de Android!

Si la compilación falla con un error en la configuración personalizada, puede realizar lo siguiente:

* Abra la ventana de Preferencias, haga clic en Archivo > Configuración (en Mac, Android Studio > Preferencias).
* En el panel de la izquierda, pulse Compilar, Ejecución, Deployment > Compilador.
* Desmarque la casilla de verificación Configurar bajo demanda.
* Haga clic en Aplicar o en Aceptar.

## Recommended specification of computer for building apk file

<table class="tg">
  
<thead>
  <tr>
    <th class="tg-baqh">OS(Only 64 bit)</th>
    <th class="tg-baqh">Windows 8 or higher</th>
    <th class="tg-baqh">Mac OS 10.14 or higher</th>
    <th class="tg-baqh">Any Linux supports Gnome, KDE, or Unity DE;&nbsp;&nbsp;GNU C Library 2.31 or later</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-baqh"><p align="center">CPU(Only 64 bit)</td>
    <td class="tg-baqh">x86_64 CPU architecture; 2nd generation Intel Core or newer, or AMD CPU with support for a <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-windows" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Windows Hypervisor</span></a></td>
    <td class="tg-baqh">ARM-based chips, or 2nd generation Intel Core or newer with support for <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-mac" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Hypervisor.Framework</span></a></td>
    <td class="tg-baqh">x86_64 CPU architecture; 2nd generation Intel Core or newer, or AMD processor with support for AMD Virtualization (AMD-V) and SSSE3</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">RAM</td>
    <td class="tg-baqh" colspan="3"><p align="center">8GB or more</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Disk</td>
    <td class="tg-baqh" colspan="3"><p align="center">At least 30GB free space. SSD is recommended.</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Resolution</td>
    <td class="tg-baqh" colspan="3"><p align="center">1280 x 800 Minimum <br></td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Internet</td>
    <td class="tg-baqh" colspan="3"><p align="center">Broadband</td>
  </tr>
</tbody>
</table>

Please be in mind that both **64 bit CPU and 64 bit OS are mandatory condition.** If your system DOES NOT meet this condition, you have to change affected hardware or software or the whole system. **It is strongly recommended to use SSD(Solid State Disk) instead of HDD(Hard Disk Drive) because it will take less time when you are building the APS installation apk file.** Recommended is just recommended and it is not a mandatory. However, you may still use a HDD when you are building apk file if you can spend a long time ALONE to complete the build.

* * *

### Este artículo se divide en dos partes.

* En la parte de descripción general hay una explicación sobre qué pasos son necesarios para crear el archivo APK.
* En el paso paso a paso encontrará las capturas de pantalla de una instalación en concreto. Debido a que las versiones de Android Studio - el entorno de desarrollo de software que usaremos para construir el APK - cambia muy rápidamente hace que esta guía no será idéntica a su instalación, pero debería darte un buen punto de partida. Android Studio también se ejecuta en Windows, Mac OS X y Linux y es posible que haya pequeñas diferencias en algunos aspectos entre cada plataforma. If you find that something important is wrong or missing, please inform the facebook group "AndroidAPS users" or in the Discord chat [Android APS](https://discord.gg/4fQUWHZ4Mw) so that we can have a look at this.

## Inicio

In general, the steps necessary to build the APK file:

1. [Instala Git](../Installing-AndroidAPS/git-install.rst)
2. [Instalar Android Studio](../Installing-AndroidAPS/Building-APK#install-android-studio)
3. [Establecer la ruta git en las preferencias de Android Studio](../Installing-AndroidAPS/Building-APK#set-git-path-in-preferences)
4. [Descargar código de AndroidAPS](../Installing-AndroidAPS/Building-APK#download-androidaps-code)
5. [Descargar Android SDK](../Installing-AndroidAPS/Building-APK#download-android-sdk)
6. [ Construir la aplicación ](../Installing-AndroidAPS/Building-APK#generate-signed-apk) (generar apk firmado)
7. [Transferir el archivo apk a su teléfono](../Installing-AndroidAPS/Building-APK#transfer-apk-to-smartphone)
8. [Identificar receptor si se utiliza xDrip+](../Installing-AndroidAPS/Building-APK#identify-receiver-if-using-xdrip)

## Step by step walkthrough

Detailed description of the steps necessary to build the APK file.

## Instalar git (si no lo tienes ya)

Siga el manual en [git página de instalación](../Installing-AndroidAPS/git-install.rst).

## Instalar Android Studio

The following screenshots have been taken from Android Studio Version 3.6.1. Your screen might look a bit different if you use a newer version of Android Studio. But you should be able to find your way through. [Help from the community](../Where-To-Go-For-Help/Connect-with-other-users.md) is provided.

One of the most important things when installing Android Studio: **Be patient!** During installation and setup Android Studio is downloading a lot of stuff which will take its time.

Install [Android Studio](https://developer.android.com/studio/install.html) and setup during first start.

Select "Do not import settings" as you have not used it before.

![Do not import settings](../images/AndroidStudio361_01.png)

Decide whether you want to share data with Google or not.

![Share data with Google](../images/AndroidStudio361_02.png)

On the following screen click "Next".

![Welcome screen](../images/AndroidStudio361_03.png)

Select "Standard" installation and click "Next".

![Standard installation](../images/AndroidStudio361_04.png)

Select the theme for the user interface you like. (In this manual we used "Light".) Then click "Next". This is just the color scheme. You can select any you like (i.e. "Darcula" for dark mode). This selection has no influence on building the APK.

![UI color scheme](../images/AndroidStudio361_05.png)

Click "Finish" on the "Verify Settings" dialog.

![Verify settings](../images/AndroidStudio361_06.png)

Wait while Android Studio downloads additional components and be patient. Once everything is downloaded button "Finish" turns blue. Click the button now.

![Downloading components](../images/AndroidStudio361_07.png)

## Set git path in preferences

Make sure [git is installed](../Installing-AndroidAPS/git-install.rst) on your computer.

On the Android Studio welcome screen click the small triangle (1. in next screenshot) and select "Settings" (2.).

![Android Studio settings from welcome screen](../images/AndroidStudio361_08.png)

### Windows

* Haga clic en el triángulo pequeño junto a Control de versiones (1.) para abrir el submenú.
* Haga clic en Git (2.).
* Asegúrese de que el método de actualización "Merge" (3.) está seleccionado.
* Compruebe si Android Studio puede localizar la ruta a git.exe automáticamente haciendo clic en el botón "Test" (4.)
    
    ![Ajustes de Android Studio](../images/AndroidStudio361_09.png)

* Si la configuración automática es correcta, se mostrará la versión git.

* Haga clic en "Aceptar" en el cuadro de diálogo (1.) y en "Aceptar" en la ventana de configuración (2.).
    
    ![Instalación automática de git satisfactoria](../images/AndroidStudio361_10.png)

* En caso de archivo git.exe no se puede encontrar clic en "OK" en el cuadro de diálogo (1.) y luego el botón con los tres puntos (2.).

* Utilice la función de búsqueda [](https://www.tenforums.com/tutorials/94452-search-file-explorer-windows-10-a.html) en el explorador de Windows para encontrar "git.exe" si no está seguro de dónde se encuentra. Está buscando git.exe ubicado en la carpeta \bin\.
* Seleccione la vía de acceso a git.exe y asegúrese de seleccionar la carpeta en ** \bin\ ** carpeta (3.) y haga clic en "Aceptar" (4.).
* Cierre la ventana de configuración haciendo clic en el botón "Aceptar" (5.).
    
    ![Error en la instalación automática de git](../images/AndroidStudio361_11.png)

* **Reinicie el sistema para actualizar el entorno del sistema.**

### Mac

* Cualquier versión de git sirve. For example <https://git-scm.com/download/mac>.
* Utilice homebrew para instalar git: ```$brew install git```.
* Para más detalles sobre la instalación de git, consulte la documentación oficial del [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
* Si instala git a través de un homebrew, no es necesario cambiar ninguna preferencia. Solo por caso: se puedan encontrar aquí: Android Studio - Preferencias.

## Descargar código de AndroidAPS

* **Si aún no ha reiniciado su equipo después de configurar la ruta de git en las preferencias, hágalo ahora. El entorno del sistema debe actualizarse.**

* There are two options to start a new project:
    
    * On the Android Studio welcome screen click "Get from version control"
        
        ![Revisa el proyecto desde el control de versiones desde la pantalla de bienvenida](../images/AndroidStudio_GetFromVersionControl.PNG)
    
    * If you already opened Android Studio and do not see the welcome screen anymore select File (1.) > New (2.) > Project from Version Control... (3.)
        
        ![Check out project from version control within Android Studio](../images/AndroidStudio_FileNew.PNG)

* Fill in the URL to the main AndroidAPS repository (https://github.com/nightscout/AndroidAPS) (1.).

* Elija el directorio en el que desea guardar el código clonado. (2.)
* Haga clic en el botón "Clonar" (3.).
    
    ![Clonar repositorio](../images/AndroidStudio_NewURL.PNG)

* Do not click "Background" while repository is cloned!
    
    ![No background action](../images/AndroidStudio361_15.png)

* After repository is cloned successfully open your local copy by clicking "Yes".
    
    ![Abrir repositorio](../images/AndroidStudio361_16.png)

* In the lower right corner you will see the information that Android Studio is running background tasks.
    
    ![Tareas en segundo plano](../images/AndroidStudio361_17.png)

* Grant access if your firewall is asking for permission.
    
    ![Permiso de cortafuegos java](../images/AndroidStudio361_18.png)

* Once the background tasks are finished you will probably see the following error message:
    
    ![Licencia SDK](../images/AndroidStudio361_19.png)

## Descargar Android SDK

* Haga clic en Archivo > Configuración.
    
    ![Abrir ajustes](../images/AndroidStudio361_20.png)

* Click the small triangle next to Appearance & Behaviour (1.).

* Click the small triangle next to System Settings (2.) and select Android SDK (3.)
* Check the box left of "Android 9.0 (Pie)" (4.) (API Level 28).
    
    ![Ajustes de SDK](../images/AndroidStudio361_21.png)

* Confirme los cambios pulsando Aceptar.
    
    ![Confirmar cambios de SDK](../images/AndroidStudio361_22.png)

* Acepte el acuerdo de licencia (1.) y haga clic en "Next" (2.).
    
    ![Aceptar licencia SDK](../images/AndroidStudio361_23.png)

* Espere hasta que termine la instalación.
    
    ![Espere durante la instalación de SDK](../images/AndroidStudio361_24.png)

* Cuando se complete la instalación de SDK el botón "Finalizar" se volverá azul. Pulse el botón.
    
    ![Finalizar la instalación del SDK](../images/AndroidStudio361_25.png)

* Android Studio might recommend to update the gradle system. **Never update gradle!** This might lead to difficulties!

* If you see an information on the lower right side of your Android Studio window that Android Gradle Plugin is ready to update click on the text "update" (1.) and in the dialog box on "Don't remind me again for this project" (2.).
    
    ![No cradle update](../images/AndroidStudio361_26.png)

## Generar APK firmado

Signing means that you indicate your app to be your own creation but in a digital way as a kind of digital fingerprint within the app itself. That is necessary because Android has a rule that it only accepts signed code to run for security reasons. For more information on this topic, follow [this link](https://developer.android.com/studio/publish/app-signing.html#generate-key).

* Click "Build" in the menu bar and select "Generate Signed Bundle / APK...".
    
    ![Crear apk](../images/AndroidStudio361_27.png)

* Seleccione "APK" (1.) en lugar de "Android App Bundle" y haga clic en "Next" (2.).
    
    ![APK instead of bundle](../images/AndroidStudio361_28.png)

* Make sure that module is set to "app" (1.).

* Click "Create new..." (2.) to start creating your key store.
    
    A key store in this case is nothing more than a file in which the information for signing is stored. Está encriptado y la información está protegida con contraseñas.
    
    ![Create key store](../images/AndroidStudio361_29.png)

* Click the folder symbol (1.) to select your key store path.

* Select the path where your key store shall be saved (2.). **Do not save in same folder as project. You must use a different directory!** One option might be your home folder.
* Type a file name for your key store (3.).
* Click "OK" (4.).
* Passwords for key store and key do not have to be very sophisticated. Make sure to remember those or make a note in a safe place. In case you will not remember your passwords in the future you see [troubleshooting for lost key store](../Installing-AndroidAPS/troubleshooting_androidstudio#lost-keystore).
* Enter (5.) and confirm (6.) the password for your key store.
* Do the same for your key (7. + 8.).
* Validity (9.) is 25 years by default. You do not have to change the default value.
* First and last name must be entered (10.). All other information is optional.
* Click "OK" (11.) when you are done.
    
    ![Ruta de almacén de claves](../images/AndroidStudio361_30.png)

* Make sure the box to remember passwords is checked (1.). So you don't have to enter them again next time you build the apk (i.e. when updating to a new AndroidAPS version).

* Haga clic en "Next" (2.).
    
    ![Recordar contraseñas](../images/AndroidStudio361_31.png)

* Seleccione la variante de compilación "fullRelease" (1.).

* Marque las casillas V1 y V2 para las versiones de firma (2.).
* Haga clic en "Finalizar". (3.)
    
    ![Finalizar construcción](../images/AndroidStudio361_32.png)

* Android Studio mostrará la información "APK(s) generados con éxito..." una vez finalizada la compilación.

* En caso de que la compilación no fuera exitosa, consulte la sección [solución de problemas](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).
* Easiest way to find the apk is to click on "Event log".
    
    ![Build successfully - event log](../images/AndroidStudio361_33.png)

* In the event log section click "locate".
    
    ![Event log - locate apk](../images/AndroidStudio361_34.png)

* app-full-release.apk is the file you are looking for.
    
    ![File location apk](../images/AndroidStudio361_35.png)

## Transferir APK a smartphone

Easiest way to transfer app-full-release.apk to your phone is via [USB cable or Google Drive](https://support.google.com/android/answer/9064445?hl=en). Please note that transfer by mail might cause difficulties and is not the preferred way.

On your phone you have to allow installation from unknown sources. Manuals how to do this can be found on the internet (i.e. [here](https://www.expressvpn.com/de/support/vpn-setup/enable-apk-installs-android/) or [here](https://www.androidcentral.com/unknown-sources)).

## Identificar receptor si se utiliza xDrip+

[See xDrip+ page](../Configuration/xdrip#identify-receiver)

## Solución de problemas

Consulte la página separada [para la resolución de problemas de Android Studio](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).