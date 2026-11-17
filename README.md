# dl

An https wrapper for app deep links, for places that only accept http(s) links (Notion, some chat apps, email clients).

Put the deep link after `#`:

```
https://nobilix.github.io/dl/#claude://code/new?folder=%2FUsers%2Fme%2Fproject&q=hello
https://nobilix.github.io/dl/#obsidian://open?vault=Content&file=note
https://nobilix.github.io/dl/#vscode://file/Users/me/project/README.md
```

The page calls `location.replace()` with everything after `#`. The hash is never sent to the server and is not decoded, so encode the inner link as you would for the app itself (JS `encodeURIComponent` for query values).

Any custom scheme works. `http`, `https`, `javascript`, `data`, `vbscript`, `file`, `blob` and `about` are refused, so the page cannot be used as an open redirect or to run scripts.

If the browser blocks the automatic switch to the app, the page shows an "Open manually" link.
