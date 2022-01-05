# Yomichad
Yomichad is a Japanese pop-up dictionary that can display readings and English
definitions of Japanese words, kanji, and optionally named entities. It is
similar to [yomichan](https://github.com/FooSoft/yomichan),
[10ten](https://github.com/birchill/10ten-ja-reader), and
[rikaikun](https://github.com/melink14/rikaikun) in spirit, but targets
[qutebrowser](https://github.com/qutebrowser/qutebrowser). Yomichad is here to help you master <ins>読み</ins>方 like a
<ins>chad</ins>!

[Yomichad demonstration](https://user-images.githubusercontent.com/53401822/148242852-ba19e2f6-2a62-4808-bf10-8014336423d8.mp4)

## Installation
Yomichad must be installed as a qutebrowser
[userscript](https://www.qutebrowser.org/doc/userscripts.html). This can be
done, for example, by cloning this repository and symlinking the `yomichad`
executable to a directory that qutebrowser scans for scripts (e.g.
`~/.local/share/qutebrowser/userscripts`). Yomichad relies on the following
third-party libraries, so make sure they are installed:
* [jamdict](https://pypi.org/project/jamdict),
  [jamdict-data](https://pypi.org/project/jamdict-data): Required for querying
  different Japanese language resources.
* [PyQt5](https://pypi.org/project/PyQt5): Used to create the pop-up dictionary
  UI. This should already be shipped with qutebrowser and is only listed here
  for completeness.
* [python-xlib](https://pypi.org/project/python-xlib) (optional): When this is
  installed, yomichad tries to center the pop-up dictionary in the qutebrowser
  window. This uses low-level X11 hacks, so if you experience bugs, please open
  an [issue](https://github.com/potamides/yomichad/issues). If this is not
  installed, the popup dictionary is simply centered on the screen.

## Usage
First, some keybindings should be configured for launching yomichad from
qutebrowser. You can, for example, add the following lines to your
`~/.config/qutebrowser/config.py`:
```python
for mode in ["normal", "caret"]:
    config.bind('gs', 'spawn --userscript yomichad', mode=mode)
    config.bind('gS', 'spawn --userscript yomichad --prefix-search', mode=mode)
```
Yomichad uses selected text as a query, so make sure to select the phrase you
want to look up (e.g. in `caret` mode or using the mouse) before you run this
script! The following flags can be used to customize yomichad to your workflow:
* `--no-kanji`: Do not lookup individual kanji.
* `--names`: Enable the lookup of Japanese names.
* `--prefix-search`: Treat selected text as a prefix and search for words
  starting with it.
