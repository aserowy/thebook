# Visual Studio

## Code cleanup

With the introduction of .editorconfig you can introduce style profiles on a solution basis. Thus, every developer uses the same formatting. .editorconfig is inheritable. You can specify a root config on solution level and add specific customizations on project level.

- <https://docs.microsoft.com/en-us/visualstudio/ide/code-styles-and-code-cleanup>
- <https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave>

## Commands

| Command | Scheme | Binding |
|---|---|---|
| Edit.GoToAll | Visual Studio 6 | `CTRL + ,` |

## Configurations

- Options > Environment > Tabs and Windows > "Pinned Tabs: Show pinned tabs in separate row"
- Options > Projects and Solutions > General > "Track Active Item in Solution Explorer"

## Features

### Adding naming conventions for private fields with underscore

- Options > Text Editor > C# > Code Style > Naming
- Manage naming styles > Add
  - Name: "Begins with _"
  - Required Prefix: "_"
  - Capitalization: camel Case Name
- Add
  - Specification: Private or Internal Field
  - Required Style: Begins with _
