# CSV to gettext converter for Godot

- [✨ Features](#-features)
- [📦 Installation](#-installation)
- [⚙️ Usage](#️-usage)
- [📂 Example Output](#-example-output)
- [📖 Loading Translations in Godot](#-loading-translations-in-godot)
- [💡 Use Cases](#-use-cases)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)

A Godot Editor addon that converts translation data stored in CSV files into [gettext](https://www.gnu.org/software/gettext/) `.po` and `.pot` files.

Translations based on CSV files are easy to work with and kick start the localization of your project, but at the same time are limited in how they can be processed in Godot, e.g. translation context and plural forms are available only with gettext.

This addon makes it easier to convert existing CSV translation files into the gettext format, allowing it to be edited with professional localization software like [Poedit](https://poedit.net/) to take advantage of all localization features, including translation context and plural forms, that are required for many languages.

Quoting [Godot Docs - Localization using gettext](https://docs.godotengine.org/en/stable/tutorials/i18n/localization_using_gettext.html), other advantages of using gettext over CSV are:
- gettext is a standard format, which can be edited using any text editor or GUI editors such as Poedit.
- gettext is supported by translation platforms such as Transifex and Weblate, which makes it easier for people to collaborate to localization.
- Compared to CSV, gettext works better with version control systems like Git, as each locale has its own messages file.
- Multiline strings are more convenient to edit in gettext files compared to CSV files.

**If your project still runs on CSV translation, now is the best time to easily convert it to gettext!**

---

### ✨ Features

- 📑 Convert CSV translations directly into `.po` and `.pot` files  
- 🛠 Works as a Godot **Editor Plugin** – no external tools required  
- 🔄 Supports multi-language CSVs with one source language and multiple target languages  
- 📝 Automatically generates `.pot` template files from source text  
- 📂 Output organized in the same directory as source file for easy integration with translation workflows  

---

### 📦 Installation

1. Copy the `addons/csv_to_gettext_converter/` folder into your Godot project’s `addons/` directory  
2. In Godot, go to **Project > Project Settings > Plugins**  
3. Enable **CSV to gettext converter**  

<img width="1200" height="188" alt="image" src="https://github.com/user-attachments/assets/2dcaafc9-77db-4df3-9eb2-bd828ab7b6e5" />

---

### ⚙️ Usage

1. Prepare your translation CSV. Example format:  

   | key          | en           | de           | pl             |
   |--------------|--------------|--------------|----------------|
   | hello_world  | Hello World! | Hallo Welt!  | Witaj świecie! |
   | exit_game    | Exit Game    | Spiel Beenden| Wyjdź z gry    |

   - The first column is the **translation key**  
   - The following columns represent **languages** (`en`, `de`, `pl`, …)  

2. In the **FileSystem dock**, right-click on your CSV file  
3. Select **Convert CSV to gettext**

<img width="579" height="544" alt="image" src="https://github.com/user-attachments/assets/039fd8ca-2e80-4640-8265-0f1bd0c84011" />

4. If any `.po` or `.pot` files already exist in that directory, you’ll be asked whether they should be overwritten

<img width="277" height="201" alt="image" src="https://github.com/user-attachments/assets/fc4b53f9-23ab-47d4-9703-c5890650c37a" />

5. After confirmation, the plugin generates:  
   - A `.pot` template file from the source language  
   - `.po` files for each target language  

<img width="338" height="224" alt="image" src="https://github.com/user-attachments/assets/7713fd44-c2b5-4c42-b2b5-59676b8dcf58" />

---

### 📂 Example Output

Source file:
- `/translation/translation.csv`

Generated files:
- `/translation/translation.pot`
- `/translation/en.po`
- `/translation/de.po`
- `/translation/pl.po`

The `translation.pot` file will contain only keys without any translations: 
```
msgid "hello_world"
msgstr ""

msgid "exit_game"
msgstr ""
```

Each `.po` file will contain a key with translation, e.g. `en.po` will contain:
```
msgid "hello_world"
msgstr "Hello World!"

msgid "exit_game"
msgstr "Exit Game"
```

You can find more details on how to work with gettext format here: [Godot Docs - Localization using gettext](https://docs.godotengine.org/en/stable/tutorials/i18n/localization_using_gettext.html).

---

### 📖 Loading Translations in Godot

To use the generated `.po` files in your game:

1. In Godot, go to **Project > Project Settings > Localization > Translations**  
2. Click **Add...** button
3. Find all `.po` files and add them to the list

<img width="1197" height="247" alt="image" src="https://github.com/user-attachments/assets/67167c0c-a0a3-41c5-a6e0-867b4ca31385" />

Or add it through code:

```gdscript
# Load a PO file into the TranslationServer
var translation: Translation = load("res://translation/de.po")
TranslationServer.add_translation(translation)

# Switch active locale
TranslationServer.set_locale("de")

# Use translations
print(tr("hello_world"))  # → Hallo Welt!
```

---

### 💡 Use Cases

- 🕹 **Indie game developers** starting with CSV translations but needing plural forms and context for more complex localization  
- 🌍 **Teams using localization platforms** (e.g., Weblate, Transifex) who require `.po` files for collaboration  
- 📝 **Projects with non-technical translators** who prefer GUI tools like Poedit over raw CSV editing  
- 🔄 **Migrating existing projects** from CSV to gettext for better version control and long-term maintainability  
- 🚀 **Prototyping games quickly** with CSV, then seamlessly switching to gettext for production  

---

### 🤝 Contributing

Pull requests, bug reports, and suggestions are welcome!
If you’d like to add features, feel free to fork and submit a PR.

---

### 📜 License

[MIT License](https://github.com/Wiechciu/csv-to-gettext-converter?tab=MIT-1-ov-file) – feel free to use in commercial or open-source projects.

