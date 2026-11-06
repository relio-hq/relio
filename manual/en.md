# Relio User Guide

Relio is an ERD and database modeling tool that opens and saves ERMaster (`.erm`) files as they are. This guide is built into the app, so you can read it without an internet connection.

## Getting started

- **Open an existing file**: File › Open… (Ctrl+O), or drag an `.erm` file onto the window. Opening a file that is already open takes you to its tab. Several files open as tabs.
- **Create a new one**: File › New diagram (Ctrl+N) and choose the database type. You choose the location and name when you save for the first time.
- **Open a sample**: on the start screen or in Help › Open sample, choose PostgreSQL (online bookstore, 19 tables) or MySQL (users and permissions, 16 tables). The samples are built into the app, so they open without an internet connection, and they open as a new untitled document (a copy), so your changes never touch the sample. Saving opens the Save as dialog. When you report a problem, reproducing it with a sample helps us check it quickly.
- **Physical name, logical name and word**: the **physical name** is the name the database uses (`EMP_NO` — it goes into the DDL, usually letters, digits and `_`). The **logical name** is the name people read (`Employee number` — shown on screen, in documents and in DDL comments, any language). The View menu chooses which one the canvas shows. A **word** is an entry of the word dictionary (physical name, logical name, type, length and description together); columns point to a word, so columns that share a word change together. When you type only the physical name, the logical name follows it (or takes the logical name of a dictionary word with the same physical name) until you edit the logical name yourself.
- **Save**: File › Save (Ctrl+S) · Save as… (Ctrl+Shift+S). Relio writes a temporary file completely and then swaps it in, so the original file is not damaged even if the app stops while saving.
- **Opening damaged files**: a damaged file is repaired as far as possible and opened, and what was repaired is shown in a window and in the problem list. Items marked "Needs review" are shown first in yellow.
- **Automatic backup**: while there are unsaved changes, Relio keeps the latest 10 copies per file in the `backup` folder of the settings folder at a set interval (5 minutes by default). If Relio stopped unexpectedly, it offers to recover the next time it starts.
- **Recent files**: File › Recent files shows each file name with its folder. "Clear list" at the bottom empties it.
- To reopen last session's documents at startup, turn this on in Tools › Settings › General.

## Keyboard shortcuts

Help › Keyboard shortcuts lists them all; change them in Tools › Settings › Shortcuts. Frequently used keys:

| Action | Keys |
|---|---|
| New diagram / open | Ctrl+N / Ctrl+O |
| Save / save as | Ctrl+S / Ctrl+Shift+S |
| Close / print | Ctrl+W / Ctrl+P |
| Undo / redo | Ctrl+Z / Ctrl+Y (or Ctrl+Shift+Z) |
| Cut / copy / paste / select all | Ctrl+X / Ctrl+C / Ctrl+V / Ctrl+A |
| Delete | Delete |
| Find bar / find and replace dialog | Ctrl+F / Ctrl+H |
| Next / previous find result | Enter·F3 / Shift+Enter·Shift+F3 |
| Next / previous design check finding | F8 / Shift+F8 |
| Merge view: next / previous conflict · current / incoming / both · apply | F8 / Shift+F8 · 1 / 2 / 3 · Ctrl+Enter |
| Rename in place / open properties | F2 / Enter |
| Cancel the tool or clear the selection | Esc |
| Zoom in / zoom out / 100% | Ctrl+= / Ctrl+- / Ctrl+0 |
| Zoom (mouse) | Ctrl+mouse wheel |
| Pan the view | Hold Space and drag |
| Next / previous document tab | Ctrl+Tab / Ctrl+Shift+Tab |
| Tools: select · table · view · 1:N relationship · note · category | V · T · W · R · N · C |
| Move the selection | Arrow keys (1) / Shift+arrow keys (10) |
| User guide | F1 |

## The window

- **Menus**: File · Edit · View · Arrange · Model · Tools · Help.
- **Toolbar**: frequent actions such as save, undo and zoom.
- **Palette** (left): select, table, view, 1:N relationship, relationship using existing columns, N:M relationship, self-referencing relationship, note, note connection, category, insert image.
- **Canvas**: where you draw. Hold Space and drag to move the view; Ctrl+mouse wheel zooms in and out.
- **Outline** (right): group columns, word dictionary, tables, views, triggers, sequences, indexes and tablespaces. Find by name; double-click to open the properties dialog. Drag a word or group onto a table on the canvas to add it as a column.
- **Problem list** (bottom): design check findings (errors, warnings and info), file repairs, and DDL export warnings. Click an item to go to the object and highlight it briefly; double-click to open its properties. Clicking "Problems: Error n · Warning n" in the status bar also opens it (or View › Panels › Problem list).
- **Document tabs** (top): one tab per open file. Drag a tab to reorder. Right-click a tab for Close · Close other tabs · Close all · Copy path · Show in folder. A middle click closes the tab.
- **Category tabs** (bottom): "All" plus one tab per category. A category tab shows only the objects in that category (turn on Model › Category › Show referencing tables to also show referencing tables, dimmed).
- **Status bar**: database type, number of tables, columns and relationships, and zoom.

## Drawing and editing

- **Tables, views, notes**: pick from the palette (T · W · N) and click on the canvas. Double-click or press Enter for the properties dialog; press F2 to rename in place.
- **Relationships**: with 1:N relationship (R), drag from the parent table and drop on the child table, or click the parent table and then the child table; FK columns are created following the parent's primary key (an empty spot or Esc cancels). To use columns that already exist, use "Relationship using existing columns". An N:M relationship creates an intersection table between two tables. A self-referencing relationship uses one table.
- **Categories**: drag with the category tool (C) to make an area. Objects placed inside the area belong to that category.
- **Select and move**: click, Shift+click to add, drag on empty space to select several. Arrow keys move by 1, Shift+arrow keys by 10. Drag a connector to add bend points; Arrange › Right-angle connectors · Restore defaults.
- **Arrange menu**: align (left, center, right, top, bottom), same width or height, distribute horizontally or vertically, auto size, background color, font.
- **Copy and paste**: objects can be pasted into another document as well. Copy selected columns to paste them into another table.
- **Undo**: every edit can be undone with Ctrl+Z and redone with Ctrl+Y.
- **Find and replace**: Ctrl+F opens the find bar over the canvas (see "Find and highlight" below), and Ctrl+H opens the find and replace dialog. The dialog searches names, comments, types and more, and replaces them in one go. Edit › Edit all properties edits column properties of many tables in one grid.
- **View menu**: view mode (logical, physical or both), notation (IE, IDEF1X), notation level, design, show in upper case, stamp, curved connectors, grid. These settings are saved in the document and can be undone.

## Properties dialogs

- **Table**: names and comment, columns (add, delete, reorder, primary key, NOT NULL, unique, auto increment, default), indexes, composite unique keys, and advanced settings (tablespace, schema, database options). Columns share words from the word dictionary, so renaming a word in one place renames every column that uses it.
- **Relationship**: name, referenced key (primary key or a unique key), update and delete actions, parent and child cardinality. When you delete a relationship, Relio asks whether to delete its FK columns too.
- **Note connection**: double-click it to open the connection properties dialog and change the line color.
- **Model menu**: manage categories, manage groups (column sets shared by several tables), word dictionary, change history (view the data of that time or restore it), translation management, test data, options (DDL and check settings), and model properties (author, version and other stamp contents).
- **Sequences, triggers, tablespaces, indexes**: add them by right-clicking in the outline and edit them by double-clicking.

## Find and highlight

- **Find bar** (Ctrl+F): a bar opens over the canvas. As you type, every matching table, column, relationship and note name (physical or logical) is highlighted and everything else is dimmed. Korean initial consonants also match. Turn on the bar option to search descriptions too.
- **Moving between results**: Enter or F3 goes to the next result and Shift+Enter or Shift+F3 to the previous one; the result flashes once. Enter pressed while composing Korean text does not move. Esc closes the bar and clears the highlight. Open the original find and replace dialog with Ctrl+H or the button on the bar.
- **Connection highlight**: hover over a table, relationship line or column, and the connected lines and tables and the matching PK and FK columns become slightly stronger (the rest stays as it is). Click to select it, and only the connected objects stay sharp while the rest is dimmed. Selecting a category area only shows its selection border. Hovering over a table or column shows its type, NOT NULL, FK target and description in a tooltip.
- **Settings**: in Tools › Settings › General › Highlight, turn off hover or selection highlight and dimming when finding or selecting, and choose the dim level (light, medium, strong) and the flash count and length. With **Reduce motion** on (default: follow the system setting), nothing flashes and only a thick outline is shown. Motion always ends within 3 seconds.
- Highlights exist only on screen; they never appear in image or HTML exports or in print.

## Design check and suggestions

- **Design check**: the model is checked after every edit. Table headers on the canvas get a mark (error ●, warning ▲) and column rows get a wavy underline; hover to read the finding. Info findings (i) are only in the problem list by default; turn on View › Show info marks on canvas to draw them there too. View › Show design check marks turns all marks on or off. The "Problems" button in the status bar counts only errors and warnings and hides when there are none. Errors make DDL fail when run, warnings are worth fixing, and info is good to know. None of them blocks saving or exporting.
- **Rules**: no primary key, foreign key without an index, columns with the same name but different types, reserved words as names (tables, columns, indexes, sequences, triggers), empty physical name, empty type, tables with the same name, Korean letters or spaces in a physical name, and the earlier checks such as no columns and duplicate names.
- **Problem list**: toggle each severity, filter by name, and group by rule. Use the **Fix** button on an item (for example, create the FK index or match the type) or **Fix all** on a rule header; one undo reverts it. Select several rows with Ctrl or Shift and right-click to fix, ignore, or copy as Markdown or CSV. Info findings are folded into one line per rule; click it to expand. Right-click an object on the canvas to fix it from "Findings (n) ▸" at the bottom of the menu.
- **F8 / Shift+F8**: go to the next or previous finding.
- **Ignore**: "Ignore here" hides that finding, and "Turn off '…' for this file" turns that rule off for the file. Ignores are recorded per file in the app settings on this PC, and the `.erm` is not changed (the document is not marked as modified). Undo them from "Show ignored" in the problem list.
- **Tools › Settings › Design check**: turn each rule on or off and change its severity, and turn off canvas marks, suggestions while typing and relationship name matching.
- **Notes where you type**: the table and column properties dialogs show a line under the field for an empty physical name, a table with the same name, Korean letters, spaces, reserved words and an empty type (nothing is blocked). The DDL dialog shows how many errors will make the DDL fail. In a new column dialog, notes for fields you have not touched wait until you type in that field or leave it once.
- **Suggestions while typing**: when you type a physical or logical name in the column properties dialog, candidates come from the word dictionary and the columns of other tables. The list opens above the field so it does not cover the fields below. Pick with ↓/↑ and accept with Enter or Tab to fill the name, type, length and logical name at once (Enter accepts only a row picked with ↓; hovering a row does not pick it, and clicking a row accepts it). Click "Undo fill" if it was the wrong one.
- **Relationship name matching**: with the 1:N relationship tool, clicking the parent table highlights child tables that have columns with matching names. If a new relationship leaves two columns with the same name, the button on the notice bar turns the existing column into the foreign key in one step.

## Merge (three-way merge)

When the same `.erm` was changed in two places, Relio merges by model object (tables, columns, relationships and their fields), not by line. Tables added on both sides merge without conflicts, and you only choose where the same field was changed differently. The result is always a valid `.erm`.

- **When the file changed outside Relio**: click **Merge…** in the check before saving, or in the notice shown when you return to the window, to open a merge tab that combines your changes with the incoming ones.
- **Resolve a Git merge conflict**: File › Compare and merge › Resolve Git merge conflict…. An `.erm` that still has conflict markers (`<<<<<<<`) can be resolved right from the notice that appears when you open it. A notice bar appears at the top when you open a file in a conflicted state.
- **Merge with another branch**: choose a branch in File › Compare and merge › Merge with another branch version…. A file that shows traces of a line-based merge can be merged again with "Redo the merge at the model level" on the notice bar.
- **Merge tab**: the list is split into conflicts, needs review, and automatic (current only, incoming only, same on both sides). Expand an item to see the base, current and incoming value of each field and choose per row. The canvas switches between the result, current and incoming previews and highlights conflicting objects. Keys: ↑↓ move, 1 current · 2 incoming · 3 both, F8 / Shift+F8 next or previous conflict, Ctrl+Enter apply.
- **Apply**: when no conflicts remain, **Apply** puts the result into the document. The whole merge is undone with a single Ctrl+Z. After you resolve a Git conflict and save, the status bar reminds you to run `git add` — Relio never writes to the Git repository.
- Register the command-line `relio merge` as a Git merge driver to merge by model object automatically during `git merge` (see "Command line" below).

## DDL

- File › Export › DDL. Choose the database and version, and the preview updates immediately. Supported: PostgreSQL · MySQL · MariaDB · Oracle · SQL Server · Db2 · H2 · HSQLDB · SQLite · Informix · MS Access · standard SQL.
- Choose what to create (drop statements, tables, indexes, FKs, sequences, triggers, views, comments and so on), the environment, the encoding and the line ending. The settings are saved in the document and used next time.
- Syntax that the chosen version cannot run is removed or changed, with a warning. Warnings are also listed in the problem list.
- On a fresh database, drop statements can fail with "does not exist". Databases with an existence check syntax use it; for the others a note is added at the top.

## Export

- Choose the kind in File › Export. The settings you choose are saved in the document.
- **Excel**: 4 built-in templates (Korean table definition, English, Japanese, Chinese) and your own templates (`.xlsx`, or ERMaster `.xls`). The output is `.xlsx`. Register your templates in Tools › Settings › Excel template; you can also save a built-in template to a file and edit it.
- **HTML**: a static document you can read offline (diagram, tables, columns, indexes).
- **Image**: PNG · JPG · BMP · SVG, with margins and per-category images.
- **Dictionary**: the word dictionary as CSV. **Translation dictionary**: pairs of physical and logical names (used to fill logical names when importing from a database).
- **Test data**: SQL (INSERT) · DBUnit XML. **Java**: class sources and Hibernate mappings, or the "JPA Entity" format (`@Entity` classes — package `jakarta` or `javax`, dates as `java.time` or `java.util.Date`, child list fields, foreign keys as value fields).
- **Print**: File › Page setup, File › Print (Ctrl+P) — check the page breaks in the preview, then send it to the system print dialog.

## Other formats

- **Export**: File › Export › DBML · Mermaid · Markdown document · Model JSON. Choose the scope (all, a category, or the tables selected on the canvas), the output file, the encoding, the line ending and the format options. For DBML, Mermaid and Markdown, "Copy to clipboard" lets you paste the result without a file.
- **DBML**: the text format used by dbdiagram.io and other tools. Column groups are written as TablePartial and notes as sticky notes.
- **Mermaid**: an `erDiagram` that GitHub, Notion and other tools render as a diagram. Logical names can be used as aliases, and each category can go to its own file.
- **Markdown document**: a schema document with a table of contents, a Mermaid diagram, and column, foreign key and index tables for each table. You can export only the tables or group them by category.
- **Model JSON**: the whole model as JSON, with a JSON Schema that describes it (command line `--print-schema`). Use it to integrate with other tools.
- The last settings of these exports are remembered per file in the app settings on this computer. The document (`.erm`) is not changed, so exporting does not mark it as changed.
- **Import**: File › Import › From SQL, DBML, Mermaid or Markdown. Pick a file or paste text, and choose the format (detect automatically, SQL, DBML, Mermaid, Markdown) and the SQL dialect (PostgreSQL, MySQL/MariaDB, Oracle, SQL Server, standard SQL — detected automatically). Files with `CREATE TABLE` statements, such as `pg_dump`, `mysqldump`, SSMS scripts or Oracle DDL, are read as they are.
- **Import into**: a new document (a new untitled tab) or the current document (merge). When merging tables with the same name, choose overwrite, skip or add with a new name. The whole merge is one undo step.
- **Preview**: before anything is added, see how many tables, columns, relationships and indexes were found, and the warnings. After the import, the result window lists the warnings (line, column, message, skipped text); "Copy list" copies them, and they are also kept in the problem list.
- Drag an `.sql`, `.ddl`, `.dbml`, `.mmd` or `.md` file onto the window to open the import dialog with that file (nothing is added until you confirm).
- Safety: files up to 32 MB and pasted text up to 8 MB. The encoding is never guessed (for a file that is not UTF-8 and has no BOM, you are asked to choose one). Statements that cannot be read are skipped with a warning.

## Working with databases

- **Import**: File › Import › From DB — connect → choose schemas → choose objects → add to the document. When names already exist, choose skip, rename or overwrite. Logical names can be filled from translation dictionaries. The whole import is one undo step.
- **Export to DB**: File › Export › Export to DB — the SQL to run is shown first; on databases that support it, everything runs in one transaction and is rolled back if a statement fails.
- **Import from another file**: File › Import › From file — pick objects from another `.erm`.
- **Direct connection**: the drivers for PostgreSQL · MySQL · MariaDB · SQL Server · SQLite are built into the app, so nothing else needs to be installed.
- **Oracle**: download Oracle Instant Client (Basic or Basic Light) from the Oracle website, unzip it, and register that folder (the one with `oci.dll`) as "Oracle Instant Client folder" in Tools › Settings › DB connections. If none is registered, PATH is searched.
- **Db2 · Informix · MS Access**: install the database's ODBC driver and enter a DSN or driver name (as shown in the ODBC Data Source Administrator) in the connection dialog. Set the default driver name for each database in Tools › Settings › DB connections. To use a driver **file** (`.dll`) directly, register it there.
- **H2 · HSQLDB**: no direct connection. Export a DDL file and run it.
- **Passwords**: stored in the Windows Credential Manager by default (entries starting with `relio:`). You can also choose not to store them and be asked each time. To store them inside the `.erm` like ERMaster, turn it on per file (anyone you give the file to also gets the password). See and delete stored passwords in Tools › Settings › Password.
- **Security**: driver files, network paths (`\\server\…`) and DSN files specified in an `.erm` you received are not used. Enter the values you need directly in the connection dialog, or register them in Settings.

## Settings

Tools › Settings. Changes are saved immediately.

- **General**: display language (한국어 · English · 日本語 · 中文; empty means the system language — Japanese and Chinese only have the text translated up to 0.12.0, and newer text appears in English), theme (System, Light, Dark, Cherry blossom, Lavender, Everforest, Catppuccin Mocha or Frost — node colors such as tables are drawn as in the Light theme for light themes; the dark themes (Catppuccin Mocha and Frost) color only the window, menus and panels, and keep the default dark canvas; exports and printing always use light colors. On Windows 11, Cherry blossom, Lavender, Everforest, Catppuccin Mocha and Frost also color the window title bar), canvas colors (Theme or Light — Light keeps the canvas light with a dark theme), automatic backup interval, reopening the last documents, cleaning up per-file records, and highlight (connection highlight, dim level, flashing, reduce motion).
- **Global groups**: column groups shared by several files.
- **Translation dictionary**: the list and order of dictionaries used for database import.
- **Excel template**: save built-in templates to files, register your own templates.
- **DB connections**: rename or delete saved connections, the Oracle Instant Client folder, and the ODBC driver for each database.
- **Design check**: turn each rule on or off and set its severity; canvas marks, suggestions while typing and relationship name matching.
- **Shortcuts**: view and change shortcuts. Keys used twice are flagged.
- **Password**: passwords in the secure store, and deleting them.
- Settings are kept in `%APPDATA%\Relio`. They remain after uninstalling and reinstalling the app.

## Command line

The same executable (`relio`) exports, imports, compares, merges, checks and works with databases without a window. It fits well in build scripts and CI.

```
relio export ddl --input model.erm --output model.sql --db-version 17
relio export excel --input model.erm --output model.xlsx --template default_en
relio export dbml --input model.erm --output model.dbml
relio export mermaid --input model.erm --output - --category Sales
relio export json --input model.erm --output model.json --include images,history
relio export java --input model.erm --output-dir src --style jpa
relio import auto --input schema.sql --output schema.erm
relio diff old.erm new.erm --format markdown --output diff.md --exit-code
relio merge base.erm mine.erm theirs.erm -o merged.erm --report -
relio lint model.erm --format markdown --fail-on error
relio db test --db PostgreSQL --server localhost --database app --user dev --password-env PGPASSWORD
relio db import --db MySQL --database shop --user dev --output shop.erm
```

- **Export kinds**: `ddl` · `image` · `html` · `excel` · `testdata` · `dictionary` · `translation` · `java` · `dbml` · `mermaid` · `markdown` · `json`. Without options, the last export settings saved in the `.erm` are used.
- **Text format options**: `--category <name>` (only that category), `--line-feed crlf`, Mermaid `--split-categories` (one `<name>-<category>.mmd` per category), JSON `--include images,history` · `--exclude layout` · `--timestamp` · `--print-schema` (prints the JSON Schema), Java `--style jpa` with `--jpa-namespace javax` · `--jpa-legacy-date` · `--jpa-collections` · `--jpa-fk-as-value`.
- **Output path rules**: an existing output file is overwritten without asking, and a missing output folder is created. If the output path is the input `.erm` (or another open `.erm`), nothing is written and the command fails. Without `--output`, the path saved in the `.erm` is used only when it points inside the folder of the `.erm` — an absolute path outside it, another drive, a network path or `..` fails with a request to use `--output` (so an `.erm` from someone else cannot overwrite other files). If the extension does not match the kind, a warning is shown and the file is written.
- **Standard output**: `--output -` writes to standard output for the text kinds (`ddl` · `dictionary` · `translation` · `dbml` · `mermaid` · `markdown` · `json`).
- **`--encoding`**: UTF-8 (default) · UTF-8 BOM · UTF-16LE · UTF-16BE · EUC-KR · CP949 (MS949) · Shift_JIS · GBK. An unknown name is an error (it is never silently replaced by UTF-8).
- **`relio import <format>`**: the format is `auto` · `ddl` · `dbml` · `mermaid` · `markdown`; `--input` is a file or `-` (standard input); `--output` is a new `.erm` (an existing one is overwritten only with `--force`). Also `--dialect` (SQL dialect) · `--db` (database of the new document) · `--comment auto|description|logical` · `--name-case asis|db` · `--encoding` · `--strict` (nothing is created if there are warnings). Warnings go to standard error as `<input>:<line>:<column>: warning: <message>`.
- **`relio diff`**: `relio diff A.erm B.erm`, `relio diff --rev REV file.erm` (that version in the Git repository ↔ the disk), `relio diff --rev REV1 --rev REV2 file.erm`. `--format markdown|json|csv`, `--output` (`-` for standard output), `--include structure,docs,layout,settings`, `--lang`, `--exit-code` (4 when there are differences). Nothing is written to the repository and no network is used. It works as a Git diff tool: `git difftool -x "relio diff" -- model.erm`.
- **`relio merge`**: `relio merge base.erm current.erm incoming.erm -o result.erm`. The result never contains conflict markers (always a valid `.erm`); when conflicts remain, the value from `--on-conflict ours|theirs` (default ours) is used and the command ends with exit code 5. Also `--keep-numbers ours|theirs` (the side whose numbers are kept), `--report <path|->` · `--report-format markdown|json` (report of conflicts and automatic items), `--label-base` · `--label-ours` · `--label-theirs` (labels), `--no-sort` (turn off sorted saving) and `--lang`. `-o` may be the same path as the current input. Nothing is written to the repository.
- **Git merge driver**: add one line to `.gitattributes` in the repository and register the driver in the Git configuration, and `git merge` and `git rebase` merge `.erm` files by model object. When conflicts remain (exit code 5), Git leaves the file conflicted; open it in Relio and finish with File › Compare and merge › Resolve Git merge conflict…. The installer does not add `relio` to the PATH, so on Windows write the full path of the installed `relio.exe` with `/` and wrap it in quotes (the first example below). Also put `text eol=lf` in `.gitattributes` so line endings inside commits are always LF — in teams that mix ERMaster (CRLF) and Relio (LF), every merge and save would otherwise show the whole file as changed because of line endings. `--label-base %S` labels the base with the common ancestor's name instead of Git's temporary file name in the report. The driver is Git configuration and does not travel with the repository, so **everyone who merges, including teammates who use ERMaster**, must register it on their own PC (without it, `git merge` merges by line and leaves conflict markers). **Caution**: if the driver is registered but Git cannot find it (wrong path — a line such as `relio: command not found` in the output), Git marks the file conflicted but **leaves only your side, with no conflict markers**. Running `git add` as is would drop the incoming changes, so after registering, check that the path from `git config --get merge.relio.driver` prints a version with `"…/relio.exe" --version`, and that `git check-attr merge -- model.erm` shows `merge: relio`.

```
# .gitattributes
*.erm text eol=lf merge=relio

git config merge.relio.name "Relio model merge"

# Windows (Git Bash) — full path of the installed relio.exe
git config merge.relio.driver '"C:/Users/<user>/AppData/Local/Relio/relio.exe" merge %O %A %B -o %A --label-base %S --label-ours %X --label-theirs %Y'

# when relio is on the PATH
git config merge.relio.driver "relio merge %O %A %B -o %A --label-base %S --label-ours %X --label-theirs %Y"
```

- **`relio lint`**: `relio lint model.erm`. `--format text|markdown|json`, `--output` (default `-`, standard output), `--fail-on error|warning|info|none` (exit code 6 when there are findings at or above this severity; default warning), `--disable` and `--only` (comma-separated rule IDs, for example `pk-missing`, `fk-no-index`, `reserved-word`), `--db-version` and `--lang`. Ignores made in the app are not applied, so the result is the same on every PC; turn rules off with `--disable`. `relio export ddl` also prints one line to standard error when there are errors that will make the DDL fail.
- **`relio db`**: `test` (connection test) · `export` (export to a database) · `import` (import from a database) · `roundtrip` (round-trip test). Pass the password with `--password-env <environment variable>`.
- See the options with `relio --help`, `relio export <kind> --help`, `relio import --help`, `relio diff --help`, `relio merge --help`, `relio lint --help` and `relio db <command> --help`. Output follows the app language; set `RELIO_LANG` (ko · en · ja · zh) to change it.

| Exit code | Meaning |
|---|---|
| 0 | Success (including warnings) — with `diff --exit-code`, no differences |
| 1 | Input or option error (import: no tables found, or warnings with `--strict`) |
| 2 | Output write failure (import: an existing `.erm` without `--force`) |
| 3 | Cannot convert to this database |
| 4 | Differences found (`db roundtrip`, `diff --exit-code`) |
| 5 | Merge conflicts remain (`merge`) |
| 6 | Findings at or above the `--fail-on` level (`lint`) |

## Where your data is stored

| What | Where |
|---|---|
| Models | The `.erm` files you save |
| App settings · connection list · recent files · per-file records (DDL target version, text export settings and so on) | `%APPDATA%\Relio` |
| Automatic backups (latest 10 per file) | `%APPDATA%\Relio\backup` |
| Database passwords | Windows Credential Manager (entries starting with `relio:`) — inside the `.erm` if turned on per file |

Relio never connects to the internet on its own, and never sends usage data, error reports or file contents anywhere.

## Installing and uninstalling

- **Install**: run the installer (`Relio_<version>_x64-setup.exe`). It installs for the current user only, without administrator rights. You choose whether to add a desktop shortcut during setup. The portable version (`Relio_<version>_x64_portable.zip`), which needs no installation, uses the same settings folder.
- **Supported**: Windows 10 · 11 (64-bit). Microsoft Edge WebView2, which Relio uses to display its interface, is built into Windows 10 and 11.
- **Update**: run the new installer; it installs over the old version and keeps your settings.
- **Uninstall**: remove Relio in Windows Settings › Apps. Settings, connection list and backups (`%APPDATA%\Relio`) remain and are used again if you reinstall.
- **Remove everything**: after uninstalling, delete the `%APPDATA%\Relio` folder and the Windows Credential Manager entries starting with `relio:` (you can also delete them first in Tools › Settings › Password).

## Troubleshooting

- **A file does not open**: the error shows the line and column. Files with an abnormal structure, such as extremely deep nesting, are refused for safety. If a file was repaired while opening, review the repairs.
- **Another program changed the file**: when you return to the window, Relio asks whether to reload. If you have unsaved changes, choose between **Merge…** (combine your changes with the incoming ones by model object), reloading (discarding your changes) and "Keep my changes".
- **A file does not open after a Git merge**: if it still has conflict markers (`<<<<<<<`), the notice takes you straight to resolving the Git merge conflict. For a file broken by a line-based "accept both", the repairs show which table and column were affected, and "Redo the merge at the model level" merges it again.
- **Relio stopped unexpectedly**: when you start it again, it offers to recover from the automatic backup. Backups are also in the `backup` folder of the settings folder.
- **Cannot connect to a database**: check the server, port, database name and firewall. For servers with a self-signed certificate, turn on "Trust server certificate (self-signed)" in the connection dialog. For Oracle, check the Instant Client folder; for Db2 · Informix · MS Access, check that the ODBC driver is installed.
- **"For security, … are not used"**: a driver file, network path or DSN file written in the document was blocked. If you trust the value, register it in Settings or enter it directly in the connection dialog.
- **Windows warning when running the installer**: the Relio installer (`Relio_<version>_x64-setup.exe`) is not code-signed yet, so the first run may show a "Windows protected your PC" window. Check that the file came from where you expected, then click **More info → Run anyway**. If your company PC blocks unsigned programs, ask your IT administrator.
- **Screen text is in the wrong language**: choose the display language in Tools › Settings › General.
- **Diagnostic log**: Relio keeps diagnostic information such as errors and start-up time only in the `logs` folder of its settings folder on this PC (last 7 days, 5 MB in total). It is never sent over the internet and contains no file contents, table names, paths or user names. In Help › Report a problem, use "Open diagnostic log folder" to see the files or "Copy recent log" to copy the last 200 lines and paste them into your report — it helps find the cause quickly. If Relio closed unexpectedly, it tells you once the next time it starts. To stop it, turn it off in Tools › Settings › General › Diagnostics, and remove existing files with "Delete diagnostic log".
- **To report a problem**: Help › Report a problem opens a report form with the version filled in, or copies its content. If you worry about company files, attach a copy made with "Save anonymized copy…" in that dialog, which removes names and descriptions.

## Differences from ERMaster

- Runs on its own without Eclipse. Files stay compatible: files saved in Relio open in ERMaster too.
- Known ERMaster problems are fixed. For example: saving and reopening files with views or self-referencing relationships, DDL syntax that failed on some databases, quotes and empty values in test data SQL, objects from other databases mixed into a MySQL import, and the translation dictionary changing letter case.
- Excel output is `.xlsx` (ERMaster `.xls` templates still work).
- Database passwords are stored in the Windows Credential Manager by default, not in the `.erm`.
- The interface is in Korean and English. Japanese and Chinese are partial; untranslated text appears in English. You can choose light, dark, Cherry blossom, Lavender, Everforest, Catppuccin Mocha or Frost themes.
- Git merge conflicts are resolved by model object (`relio merge` also works as a Git merge driver), and there are design checks, suggestions while typing and find bar highlights.
- You can export to DBML, Mermaid, Markdown and model JSON, and import from SQL (`CREATE TABLE`), DBML, Mermaid and Markdown.
- Usage data, error reports and file contents are never sent anywhere. Every feature works without the internet.
