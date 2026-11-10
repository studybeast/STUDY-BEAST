# Study Beasts – Android and desktop apps

Olympiad and school-exam practice with original collectible study beasts.

Main sections: **Today** (daily goal, streak, daily challenge, mistake notebook, weak chapters, focus timer), **My quests** and **Battle test** (olympiads), **School exams** (notes, test papers, answer training), and the **Beast Ledger**.

## Get the APK (no Android Studio needed)

1. Sign in at github.com (a free account is enough).
2. Create a new repository, for example `study-beasts`. It can be private.
3. On the repository page choose **Add file → Upload files**, and drag in everything inside this folder, including the hidden `.github` folder. (On Windows or Mac, turn on "show hidden files" first, or upload the two files in `.github/workflows` separately.) Press **Commit changes**.
4. Open the **Actions** tab. A run called "Build Study Beasts APK" starts by itself and takes about 5–8 minutes.
5. When it shows a green tick, open the run and download **StudyBeasts-APK** from the Artifacts section. Unzip it to get `StudyBeasts.apk`.
6. Copy the APK to the phone and open it. Android asks once to allow installing from this source; allow it.

## Get the desktop apps (Windows, Mac, Linux)

The same upload also builds the desktop apps. In the **Actions** tab, open the run called "Build Study Beasts desktop apps". When it shows a green tick, download:

- **StudyBeasts-Windows** – contains `Study-Beasts-Setup-1.2.0.exe` (installer) and `Study-Beasts-Portable-1.2.0.exe` (runs without installing). Windows may show "Windows protected your PC" because the app is not code-signed: click **More info → Run anyway**.
- **StudyBeasts-macOS** – contains a `.dmg`. Open it and drag Study Beasts to Applications. The first time, right-click the app and choose **Open**, because it is not signed by Apple.
- **StudyBeasts-Linux** – contains an `.AppImage`. Make it executable (`chmod +x`) and double-click it.

To run the desktop app from source instead: install Node.js, open the `desktop` folder in a terminal, run `npm install`, then `npm start`.

## Build with Android Studio instead

Open this folder in Android Studio, let it sync, then choose **Build → Build APK(s)**.

## The free offline library (Class 6–12: CBSE school subjects and olympiads)

Students get free notes and test papers without any AI key from the library you build:

1. Open the **Beast Library Builder** page in claude.ai. Tick the classes and subjects you want (Maths, Science, Social Science for Class 6–10; Physics, Chemistry, Biology, Maths, Accountancy, Business Studies and Economics for Class 11–12), press **Write all ticked**, review, then **Approve all ticked**. Each class also has olympiad and entrance topics to tick: IMO, NSO, NCO and IEO for Class 6–12, IGKO and ISSO for Class 6–10, NSEJS for Class 8–10, IOQM for Class 8–12, and NSEP, NSEC, NSEB, NSEA and NEET for Class 11–12.
2. Press **Download ticked** to save one file per class, for example `cbse-class-8.json`.
3. Copy the files into **both** `app/src/main/assets/library/` and `desktop/web/library/`, then upload to GitHub again to rebuild the apps.

Olympiad topics from the library appear in **Training camp** (offline notes) and their questions are used in **Battle test** and the daily challenge.

Students can also load a library file themselves: School exams → **Load library file**. That's handy for sharing a new class over WhatsApp without a new app version.

Without a key, objective answers are marked by the app and students check written answers themselves against the model answer and marking points. With a key, they also get notes on any topic, fresh papers and examiner-style marking.

## Turning on the AI features

Notes, test papers, answer marking and fresh olympiad papers use Claude through an Anthropic API key:

1. Create a key at console.anthropic.com (usage is billed to that account).
2. In the app, tap or click **Add AI key** at the bottom-right corner, paste the key and press Save.

The key is stored only on that device. Everything else – the free library notes and papers, the question bank, mock tests, XP, beasts and badges – works without a key.

## Where things are saved

- Progress, beasts, notes and papers are saved inside the app on that device.
- On Android, question papers and answer keys you save go to **Downloads/Study Beasts** as HTML files you can open and print.
- On desktop, a Save dialog lets you pick where the file goes (Downloads by default).

## Publishing on the Play Store

The APK built above is a debug build for sideloading. For the Play Store you need a signed release build (Android Studio: **Build → Generate Signed Bundle / APK**) and a Google Play developer account.

## Project layout

- `app/src/main/assets/index.html` – the whole Study Beasts app (the desktop copy is in `desktop/web/`)
- `app/src/main/assets/bridge.js` – connects the app to Claude and to file saving
- `app/src/main/java/com/studybeasts/app/MainActivity.java` – the Android screen that hosts the app
- `desktop/main.js` and `desktop/preload.js` – the desktop window and file saving
- `.github/workflows/build-apk.yml` – builds the APK on GitHub
- `.github/workflows/build-desktop.yml` – builds the Windows, Mac and Linux apps on GitHub

## Copyright safety

- All beasts, names and artwork are original to Study Beasts.
- Library notes and questions are written fresh under strict originality rules: no text, examples, activities or exercises copied or closely paraphrased from NCERT or other textbooks, guides, past papers or websites, and no poems, lyrics or story passages. School English is not in the library. For the English olympiad (IEO), every reading passage, dialogue and example sentence is newly invented; nothing is quoted, excerpted or retold from any book, story, poem, song, speech or article.
- The app and every library file state that Study Beasts is not affiliated with or endorsed by CBSE, NCERT, SOF, IAPT, HBCSE, NTA or any exam body.
- Olympiad questions are new questions in a similar style; none are taken or adapted from real olympiad papers, sample papers or workbooks.
- Before each release, read the chapters and remove anything that looks copied. Do not add NCERT logos, scanned pages, textbook figures or photos taken from the web.
