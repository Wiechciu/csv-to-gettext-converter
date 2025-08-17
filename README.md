# CSV to Gettext (PO/POT) Converter for Godot

A Godot Editor addon that converts translation data stored in CSV files into [gettext](https://www.gnu.org/software/gettext/) `.po` and `.pot` files.  
This makes it easier to work with translators and standard localization workflows while keeping your project’s translation sources editable in a simple CSV format.  

---

## ✨ Features

- 📑 Convert CSV translations directly into `.po` and `.pot` files  
- 🛠 Works as a Godot **Editor Plugin** – no external tools required  
- 🔄 Supports multi-language CSVs with one source language and multiple target languages  
- 📝 Automatically generates `.pot` template files from source text  
- 📂 Output organized in the same directory as source file for easy integration with translation workflows  

---

## 📦 Installation

1. Copy the `addons/csv_to_gettext_converter/` folder into your Godot project’s `addons/` directory  
2. In Godot, go to **Project > Project Settings > Plugins**  
3. Enable **CSV to gettext converter**  

---

## ⚙️ Usage

1. Prepare your translation CSV. Example format:  

   | key          | en           | de           | pl             |
   |--------------|--------------|--------------|----------------|
   | hello_world  | Hello World! | Hallo Welt!  | Witaj świecie! |
   | exit_game    | Exit Game    | Spiel Beenden| Wyjdź z gry    |

   - The first column is the **translation key**  
   - The following columns represent **languages** (`en`, `de`, `pl`, …)  

2. In the **FileSystem dock**, right-click on your CSV file  
3. Select **Convert CSV to Gettext**  
4. If any `.po` or `.pot` files already exist in that directory, you’ll be asked whether they should be overwritten  
5. After confirmation, the plugin generates:  
   - A `.pot` template file from the source language  
   - `.po` files for each target language  

---

## 📂 Example Output

- /translations/
- messages.pot
- en.po
- de.po
- pl.po


---

## 📖 Loading Translations in Godot

To use the generated `.po` files in your game:

```gdscript
# Load a PO file into the TranslationServer
var translation = load("res://translations/de.po")
TranslationServer.add_translation(translation)

# Switch active locale
TranslationServer.set_locale("de")

# Use translations
print(tr("hello_world"))  # → Hallo Welt!
```

## 🤝 Contributing

Pull requests, bug reports, and suggestions are welcome!
If you’d like to add features, feel free to fork and submit a PR.

## 📜 License

MIT License – feel free to use in commercial or open-source projects.

