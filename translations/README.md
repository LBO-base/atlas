# Translating Atlas

Every string in the interface lives in one self-contained language file. Translating Atlas
means copying one file and replacing the English text on the right of each line. There is no
build step and nothing else to touch.

## How to add a language

1. Copy `lang-en.js` to `lang-xx.js`, where `xx` is your language code (`de`, `fr`, `es`,
   `pt-br` and so on).
2. Change the three registration lines at the top to your code, and set the language name in
   the form speakers of that language would recognise:

   ```js
   LANGS.de = 'Deutsch';
   MONTHS.de = ['Jan', 'Feb', ...];
   LOCALES.de = { ... };
   ```

3. Translate the values, leaving the keys untouched. `'btn.delete': 'Delete'` becomes
   `'btn.delete': 'Löschen'`.
4. Open an issue or send the file, and it will be included in the next release.

## Things worth knowing

**Placeholders must survive.** Some entries are functions rather than plain strings:

```js
'search.hits': ({ n, plus }) => `${n}${plus} hit${plus ? 's' : plEN(n)}`,
```

Keep the `${...}` parts exactly as they are; only the words around them change. If your
language pluralises differently, write your own rule inside your file. Russian does this with
a three-form helper:

```js
function plRU(n, one, few, many) { ... }
'forks.count': ({ n }) => `${n} ${plRU(n, 'группа', 'группы', 'групп')}`,
```

**`\n` in a tooltip is meaningful.** The first line is rendered in bold as a title, the rest
as the body. Keep the split where it makes sense in your language.

**Keys are the contract.** Do not rename or remove keys. If a key is missing from your file,
Atlas falls back to English for that string, so a partial translation still works and can be
completed later.

**Some names stay in English.** Product and tool names (Atlas, Claude Code, Codex, Windows
Terminal) are normally left as they are.

**Please use straight quotes and plain hyphens** rather than typographic quotes, em dashes or
arrows, so the interface matches the existing style.

## Checking your work

The file is plain JavaScript, so a syntax error breaks the interface. Before sending it:

```
node --check lang-xx.js
```

If you have a copy of Atlas installed, you can test live: drop `lang-xx.js` into the `ui`
folder next to `atlas.exe`, add a `<script src="/lang-xx.js"></script>` line to `ui/index.html`
and `ui/palette.html` alongside the existing language files, then restart Atlas. Your language
appears in Settings > General automatically.
