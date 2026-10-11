# Filo Rosso: progetto Android (Capacitor)

Questo progetto impacchetta il gioco (www/index.html) in un'app Android.
Non e' un APK gia' compilato: l'APK va generato sul tuo computer con i passaggi sotto.

## Requisiti
- Node.js 18 o superiore
- JDK 17
- Android Studio (con Android SDK installato)

## Passaggi
1. Apri un terminale in questa cartella ed esegui:
   npm install
   npx cap add android
2. Apri android/app/src/main/AndroidManifest.xml e, dentro il tag <activity ...>,
   aggiungi:  android:screenOrientation="sensorLandscape"
3. Esegui:
   npx cap sync android
   cd android
   ./gradlew assembleDebug        (su Windows: gradlew.bat assembleDebug)
4. L'APK si trova in:
   android/app/build/outputs/apk/debug/app-debug.apk
   Copialo sul telefono e installalo (consenti "origini sconosciute").

In alternativa: npx cap open android, poi in Android Studio premi Run con il telefono collegato.

## Note
- Il gioco carica three.js e il font da internet (cdnjs e Google Fonts), quindi serve la connessione.
- Per aggiornare il gioco sostituisci www/index.html e rilancia "npx cap sync android".

## Metodo online (senza installare nulla): GitHub Actions
1. Crea un account su github.com e un nuovo repository vuoto.
2. Estrai questo zip, poi in "Add file > Upload files" trascina TUTTO il contenuto
   (package.json, capacitor.config.json, cartella www, cartella .github) e fai Commit.
3. Vai nella scheda "Actions", scegli "Build APK" e premi "Run workflow".
4. Quando e' verde (3-6 minuti), apri l'esecuzione e scarica "filo-rosso-apk" da Artifacts.
5. Estrai lo zip scaricato: dentro c'e' app-debug.apk da installare sul telefono.
