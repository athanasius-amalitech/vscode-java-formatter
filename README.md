# VS Code Java Formatter Profile

An Eclipse formatter profile for the **Language Support for Java by Red Hat** extension
in VS Code. Point your user settings at it once, and every Java project you open is
formatted the same way.

It follows the AmaliTech Coding Standards, Java Edition (§7.8 indentation, §11.1 source
files).

## What it does

| Rule | Setting |
|---|---|
| Indentation | 4 spaces per level, never tabs |
| Wrapped lines | 8 spaces (two levels) |
| Line length | 100 columns, for code and comments |
| Long lines | wrapped where necessary, with the operator (`+`, `&&`, `?`) starting the new line |
| Your own line breaks | kept, never joined back |
| Method bodies | no blank line straight after the opening brace |
| End of file | always ends with a newline |

Anything not listed uses the Eclipse built-in defaults.

## Use it

Add these lines to your VS Code **user** `settings.json`
(Ctrl+Shift+P, then "Preferences: Open User Settings (JSON)"):

```json
"java.format.settings.url": "https://raw.githubusercontent.com/athanasius-amalitech/vscode-java-formatter/main/eclipse-java-formatter.xml",
"java.format.settings.profile": "AmaliTech Java",
"[java]": {
    "editor.defaultFormatter": "redhat.java",
    "editor.formatOnSave": true,
    "editor.rulers": [100]
}
```

Then run **"Java: Clean Java Language Server Workspace"** from the command palette, or
reload VS Code, so the extension picks up the profile.

Format a file with **Shift+Alt+F**, or just save it when format-on-save is on.

## Notes

- The settings live in your **user** settings, so they apply to every project. To pin
  them for one project only, put the same lines in that project's
  `.vscode/settings.json` instead.
- The formatter only changes layout. It does not enforce naming, imports or braces. For
  that, add Checkstyle to the project's build.
