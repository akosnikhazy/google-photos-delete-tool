Hungarian version of the original script by mrishab

# Google Fotók Minden Kép Törlése Eszköz
Ha valaha ki akartad törölni az összes képedet a [Google Fotókból](https://photos.google.com/) de nem találtál könnyű eszközt rá, akkor ez az eszköz számodra. Ez a szkript végigmegy minden képen a Google Fotók app-on és törli azokat. Élőben láthatod, ahogy történik!

# Kezdjünk neki
Kövesd a következő lépéseket!

## Szükséges dolgok
- Egy modern böngésző. Ez a szkript nem lett tesztelve mással, mint Google Chrome `Version 71.0.3578.98`. Innen töltheted le [a legfrissebb Google Chrome verziót](https://www.google.com/chrome/). Ugyan akkor használhatod más modern böngészőkkel is mint [Firefox](https://www.mozilla.org/en-US/firefox/download/thanks/) vagy [IE Edge](https://www.microsoft.com/en-ca/windows/microsoft-edge).

- Használd a [magyar verzióját Google Fotóknak](https://photos.google.com/?hl=hu). Az angol verziós szript [itt található](https://github.com/mrishab/google-photos-delete-tool/blob/master/delete_photos.js) 

## Feltételezések
Feltételezzük, hogy a következő lépések a Google Chrome böngészőben történnek. Más böngészőkben is ezeket a lépéseket kell megtenni, de a használt billentyűk és parancsok különbözhetnek.

## Steps
1) [Jelentkezz be a Google profilodba](https://accounts.google.com/ServiceLogin).

![Google Account Sign-in Page](images/google-signin-page.jpg)

2) Látogasd meg a [Google Fotókat](https://photos.google.com/)

![Google Photos Page](images/google-photos-page.jpg)

_Megjegyzés: Ha be vagy jelentkezve Google-be látni fogod a képeidet._

3) Kapcsold ki a képek megjelenítését a böngésződben.
    
    - **Chrome böngészőben**
        
        1) Kattints a lakatra ( a címsor bal szélén) -> `Webhelybeállítások`
        
        2) Blokkold a képeket megjelenítése jogosultságot
        
        ![Google Chrome Right Click Pop-up Menu](images/image_block.png)
        
        3) Frissítsd a Google Fotók oldalt (F5)
        

4) Nyisd meg a fejlesztői eszközöket a következő 3 módszer egyikével

    - **Billentyűzettel**
        
        Nyomd meg a következő kombinációt - `CTRL + SHIFT + I` vagy nyomj F12-t

    - **Az oldalról**
        
        Egy üres területen nyomj jobb klikket és válaszd ki a `Vizsgálat` menüpontot
        
        ![Google Chrome Right Click Pop-up Menu](images/chrome-popup-menu.jpg)

    - **Menüből**
        
        1) Nyomd meg a Menü gombot ![Google Chrome Menu Icon](images/chrome-menu-icon.jpg) 
        
        2) Válaszd ki a `További eszközök` menüt.
        
        3) Válaszd ki a `Fejlesztői eszközök` menüt.
        
        ![Google Chrome Menu Developer Tools](images/chrome-menu-popup.jpg)

5) A fejlesztői eszközök megnyitása után kattints a `Console` fülre.
    ![Google Chrome Console on Google Photos page](images/chrome-console.jpg)
    
    Megjegyzés: _A fejlesztői konzol lehetővé teszi, hogy egyedi kódokat futtass, mint ez az eszköz! Többet megtudhatsz róla a [Google Console oldalon](https://developers.google.com/web/tools/chrome-devtools/console/)_.
    
    *Látni fogsz egy üzenetet a Google-től: "A konzol használata lehetővé teheti a támadók számára, hogy a Self-XSS nevű támadással visszaéljenek személyes adataiddal és ellopják azokat.Ne írj vagy másolj be olyan kódot, amelyet nem értesz."*

6) Másolj be minden kódot a [delete_photos.js](delete_photos.js) fájlból a konzolba.
    ![The Code in Chrome Console](images/code-in-console.jpg)

    Megjegyzés: A szkript alapból minden képet töröl. Ha csak egy bizonyos számú képet akarsz törölni változtasd meg a `maxImageCount` változó értékét, ahogy a példában látod [example](delete_photos.js#L3).

7) Nyomj **ENTER** gombot miután bemásoltad a kódot a konzolba. A szkript el kezd futni enter után.

8) Kész! Most láthatod, ahogy a szkript tömegesen törli a képeidet. 

Tipp: ctrl+görgetés segítségével lekicsinyítheted a weboldalt, hogy egyszerre több képet tudjon kijelölni a szkript, így gyorsabban tud haladni.

# Hiba keresés

A szkript nem feltétlenül működik jól lassabb internet kapcsolattal. Ebben az esetben növelheted a `DELETE_DELAY_CYCLE` értékét néhány ezer milliszekundummal. Ez biztosítja, hogy a lap betöltődjön, mielőtt a szkript próbálkozik a következő adag törléssel.

# GYIK

1) Csak kijelöli, majd megszünteti a kijelölést, de nem töröl
    - Használd a [magyar nyelvű Google Fotókat](https://photos.google.com/?hl=hu) és futtasd újra az eszközt.

2) Megáll néhány kép törlése után.
    - Növeld a `DELETE_DELAY_CYCLE` értékét néhány ezer milliszekundummal.

3) Késleltetve töltődtek be a képek és az eszköz leállt.
    - Ebben az esetben frissítsd az oldalt és futtasd újra a szkriptet. Nem kell megint bemásolni, elég megnyomnod a konzolban a felfelé nyíl billentyűt, hogy visszahozza a kódot.
