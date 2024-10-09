*(English below)*

# 🇫🇷 *Web scraper* pour créer des cartes Anki en LSF à partir d'[Elix](https://dico.elix-lsf.fr/) 

Voici un jeu de cartes Anki prêt à l'emploi créé avec cet outil : https://ankiweb.net/shared/info/1368632736

## Créer vos propres cartes

Deux notebooks Python sont proposés :
- `batch.ipynb`: pour télécharger tous les mots d'une liste (par défaut, [1400 mots fréquemment utilisés](https://github.com/nmondon/mots-frequents/blob/master/frequence.csv)),
- `interactive.ipynb`: pour décider si on souhaite créer une carte ou non pour chacune des définitions.

Notez qu'une fois que vous avez exécuté les notebooks, le texte qui accompagne les vidéos sera stocké dans un fichier `cards.csv`. Vous aurez besoin d'un modèle de cartes Anki pour l'importer, je vous recommande d'utiliser celui fourni dans mon deck Anki (voir le lien ci-dessus).

Les vidéos seront téléchargées dans un sous-dossier (`/videos` par défaut). Il est préférable de compresser un peu les vidéos. Vous pouvez utiliser [ffmpeg](https://ffmpeg.org/) comme ceci :
```bash
ffmpeg -i input.mp4 -vcodec libx264 -crf 40 output.mp4
```
Vous pouvez faire une boucle `for` en bash pour traiter toutes les vidéos. L'option `-vf "scale=-2:'min(480,ih)'"` permet de limiter la hauteur des vidéos à 480 pixels.

Ensuite, une fois que le CSV est importé dans Anki, vous devez copier les fichiers vidéo dans le [dossier média](https://docs.ankiweb.net/files.html#file-locations) de votre installation Anki (par exemple `%APPDATA%\Anki\<PROFILENAME>\collection.media` sous Windows).

⚠️ Le nom des fichiers vidéo doit être identique à celui de la dernière colonne du CSV (au format `[sound:NOMDUFICHIER]`) !

🙏 Si vous téléchargez des vidéos depuis Elix, attendez quelques secondes entre chaque requête et essayez de le faire en-dehors des heures de pointe (mieux vaut le lancer pendant la nuit - heure de Paris). Vous ne voudriez pas casser un site aussi merveilleux.

---

# 🤟 [Elix](https://dico.elix-lsf.fr/) scraper for French Sign Language to create Anki cards

Here is a ready-to-use Anki deck created with this tool: https://ankiweb.net/shared/info/1368632736

## Creating you own cards

Two Python notebooks are available:
- `batch.ipynb`: to download all words from a list (by default, [1400 frequently used French words](https://github.com/nmondon/mots-frequents/blob/master/frequence.csv)),
- `interactive.ipynb`: lets you decide, for each definition, whether to create a card or not.

Note that once you run the notebooks, the text content will be stored in a `cards.csv` file. You need an Anki card template to import it, I recommend you use the one provided in my Anki deck (see link above).

The videos will be stored in a subfolder (`/videos` by default). It is a good idea to compress the videos a little. You can use [ffmpeg](https://ffmpeg.org/) like so:
```bash
ffmpeg -i input.mp4 -vcodec libx264 -crf 40 output.mp4
```
You can do a bash `for` loop to process all the videos. The option `-vf "scale=-2:'min(480,ih)'"` limits the height of the video to 480 pixels.

Then, once the CSV is imported in Anki, you need to copy the video files into the [media folder](https://docs.ankiweb.net/files.html#file-locations) of your Anki installation (e.g. `%APPDATA%\Anki\<PROFILENAME>\collection.media` on Windows).

⚠️ The name of the video files must be identical to those in the last column of the CSV (with format `[sound:FILENAME]`)!

🙏 If you scrap Elix, keep a `time.sleep()` between request, and try to do it outside peak hours (better to launch it at night, Paris time). You wouldn't want to break such a wonderful website.
