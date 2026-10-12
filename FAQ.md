# FAQ

## How do I submit a map or mod?

1. Upload your files to a release on your own GitHub repository.
2. Fork this repository.
3. Add an entry for your map or mod to `index.json`.
4. Open a pull request.

Your files stay on your repository. This repository only holds the list.

## What files can a map have?

Only these, where `<id>` is your map name:

| File | Required |
|---|---|
| `<id>.ff` | Yes |
| `<id>_load.ff` | No |
| `<id>_art.ff` | No |
| `<id>.arena` | No |
| `<id>.pak` | No |
| `<id>.sabl` | No |
| `<id>.sabs` | No |
| `<language>_<id>.ff` (for example `eng_<id>.ff`) | No |

These are the same files that go in `usermaps/<id>/`.

## What files can a mod have?

Only these:

| File | Required |
|---|---|
| `mod.ff` | Yes |
| `mod.sabl` | No |
| `mod.sabs` | No |

These are the same files that go in `mods/<id>/`. Anything else is skipped.

## What can the id be?

Lowercase letters, numbers and `_`, up to 64 characters.

- For a map, the id is the map name, for example `cp_asylum_sh`.
- For a mod, the id is the folder name it installs to, for example `my_weapons`.

## What does an entry look like?

A map:

```json
{
    "id": "cp_example",
    "type": "map",
    "name": "Example",
    "author": "you",
    "version": "1",
    "description": "One or two sentences about the map.",
    "image": "https://github.com/you/your-repo/releases/download/v1/preview.png",
    "files": [
        {
            "name": "cp_example.ff",
            "size": 640057512,
            "hash": "",
            "urls": [
                "https://github.com/you/your-repo/releases/download/v1/cp_example.ff"
            ]
        }
    ]
}
```

A mod is the same, with `"type": "mod"` and the mod files:

```json
{
    "id": "my_weapons",
    "type": "mod",
    "name": "My Weapons",
    "author": "you",
    "version": "1",
    "description": "One or two sentences about the mod.",
    "image": "https://github.com/you/your-repo/releases/download/v1/preview.png",
    "files": [
        {
            "name": "mod.ff",
            "size": 442344768,
            "hash": "",
            "urls": [
                "https://github.com/you/your-repo/releases/download/v1/mod.ff"
            ]
        }
    ]
}
```

- `name` is the title shown on the card.
- `description` is shown on the card and in the details panel. Keep it short.
- `size` is the file size in bytes.
- Leave `hash` empty. It is filled in when your submission is reviewed.
- Every link must be a direct `https://` download. GitHub release links work. Google Drive, Mega and similar links do not.

## What should the preview image be?

A PNG or JPG, 16:9, no larger than 16 MB. 1920x1080 or 1280x720 is ideal. Use an in-game screenshot.

## My file is bigger than 2 GB. What do I do?

GitHub releases do not allow files of 2 GB or more. Split the file into parts under 1.9 GB and upload every part. List the parts in order under `urls`:

```json
{
    "name": "cp_example.pak",
    "size": 6442450944,
    "hash": "",
    "urls": [
        "https://github.com/you/your-repo/releases/download/v1/cp_example.pak.001",
        "https://github.com/you/your-repo/releases/download/v1/cp_example.pak.002",
        "https://github.com/you/your-repo/releases/download/v1/cp_example.pak.003",
        "https://github.com/you/your-repo/releases/download/v1/cp_example.pak.004"
    ]
}
```

The game downloads the parts and joins them back into one file.

## How do I update my map or mod?

Make a new release with the new files, then open a pull request that changes your entry: new `version`, new links, new sizes. Players who have the old version see UPDATE in the Workshop and only download the files that changed.

## Can I change the files after my submission is accepted?

No. Every file has a hash. If a file changes, it no longer matches and the game will refuse to install it. Submit an update instead.

## What gets a submission rejected?

- Files that are not on the lists above.
- Links that are not direct downloads.
- A missing main file (`<id>.ff` for a map, `mod.ff` for a mod).
- An id that clashes with an existing entry.
- A map or mod that does not load.
