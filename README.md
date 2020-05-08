# gltp-static-generator

tool for generating simple static readers for Greek Learner Texts

This is currently a work in progress but will be turned into a Python package which can be used via a GitHub Action to automatically generate GitHub Pages for a Greek Learner Texts repository.

At a bare minimum, you just create a JSON configuration file in your repo and then call `./build.py <config-file>`.

The config file should look something like the following:

```
{
    "SRC_PATTERN": "./{source}.txt",
    "OUTPUT_DIRECTORY": "docs/",
    "collection": "GNT Texts",
    "subtitle": "Converted to GLTP format by James Tauber",
    "repo_link": "https://github.com/jtauber/gnt-texts",
    "works": [
        {
            "source": "sblgnt",
            "title": "SBLGNT",
            "levels": ["book", "chapter", "verse"]
        },
        {
            "source": "nestle1904",
            "title": "Nestle 1904",
            "levels": ["book", "chapter", "verse"]
        }
    ]
}
```

You can override templates (or create new ones for levels you've identified) in a `templates/` directory adjacent to your config file. 

A template file exists for every level type (e.g. "chapter" will use "chapter.html") so arbitrary levels can be used as long as there is a template for it.

Out of the box, there are templates for level types: `book`, `section`, `chapter`, `verse`, `sentence`, `speech`.
