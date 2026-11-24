# Copilot Instructions

Copilot instructions shared between projects such as `pepc`, `wult`, and `stats-collect`.

## Usage

Clone this repository and configure your AI tool to load the files from the `instructions`
sub-directory.

For example, in VS Code, add the following in user settings or in the workspace file:

```jsonc
"chat.instructionsFilesLocations": {
    "~/git/copilot-instructions/instructions": true
}
```

 Another option is to symlink or copy the files into the `.github/instructions` directory of a
 project.
