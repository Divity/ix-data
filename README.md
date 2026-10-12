# IW7 Workshop

The content list for the Workshop in iw7-mod, the Call of Duty: Infinite Warfare client.

The Workshop is a menu in the game. It reads `index.json` from this repository, shows every map and mod in it, and installs them for you:

- Maps go to `usermaps/<id>/`
- Mods go to `mods/<id>/`

Every file is checked against the hash in `index.json` before it is installed. A file that does not match is deleted.

## Using it

Open the game console and run this once. The setting is saved.

```
workshop_url https://raw.githubusercontent.com/Divity/ix-data/main/index.json
```

Then open WORKSHOP from the main menu.

## Submitting

Read [FAQ.md](FAQ.md).
