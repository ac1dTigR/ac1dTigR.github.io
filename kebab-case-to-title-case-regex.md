# Convert Kebab Case to Title Case In VSCode Snippet Using RegEx

Here is the solution, assuming that your file names are alphanumeric and in lower [kebab case](https://developer.mozilla.org/en-US/docs/Glossary/Kebab_case):

```
${TM_FILENAME_BASE/\-?([0-9a-z]+)/ ${2:/capitalize}/g
```

e.g. For a file titled **"my-file-name-123.md"**, this will return: **" My File Name 123"**.

This is in a [VSCode snippet](https://code.visualstudio.com/docs/editor/userdefinedsnippets) and uses the [environment variable](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_variables) `TM_FILENAME_BASE` to get the current filename without the extension. I used this for my [`new-note.template` file](https://foambubble.github.io/foam/user/features/note-templates.html#default-template) in the [Foam extension for VSCode](https://marketplace.visualstudio.com/items?itemName=foam.foam-vscode), which I use to edit notes in my [Zettelkasten](https://zettelkasten.de/overview/).

The second section (`\-?([0-9a-z]+)`) is the RegEx to match each word in the title. I haven't tested this, but replacing `[0-9a-z]` with `[^\-]` would probably work just as well if you use filenames that contain non-alphanumeric characters.

The third section specifies the format to which the mathed RegEx should be converted. I used ` ${1:/capitalize}` to change each word to be preceded by a space instead of a `-` and to be capitalized. Note that the first word in the filename will also be preceded by a space, so effectively an extra space will be added before the first word. Transform grammar and examples can be found [here](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_variable-transforms).

The final section (`g`) is to indicate that every string in the filename that matches the RegEx should be transformed, not just the first one.
