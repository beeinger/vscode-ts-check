# vscode-ts-check

## Update: I've created a [VSCode extension](https://marketplace.visualstudio.com/items?itemName=beeinger.ts-live-checks) instead, works even better!

Solution for VSCode that enables project wide typescript checking

Typescript in VSCode defaultly checks only the files that are currently opened in the editor, nothing else.

### To check your whole project for type error you would have to either:

- go through all files one by one
- manually outside of VSCode run type checking or build

Both "solutions" are bad, building or running some command in order to get type checks is annoying.

And this has always hurt me as for example JetBrains Webstorm has that out of the box :c

So here it is - the solution.

Just put this task in ```tasks.js``` inside the .vscode folder, and real-time project wide type checking will become a reality.

```json
{
    "version": "2.0.0",
    "tasks": [
      {
        "label": "tsc-watch project",
        "type": "typescript",
        "tsconfig": "tsconfig.json",
        "option": "watch",
        "problemMatcher": ["$tsc-watch"],
        "group": "build",
        "runOptions": {
          "runOn": "folderOpen"
        },
        "presentation": { "reveal": "never" }
      }
    ]
}
```

When first opening the repo with this task inside you should be asked whether to enable ```Automatic Tasks in Folder```, if not then do:

- **⌘⇧p** 
- ```Manage Automatic Tasks in Folder```
- ```Allow Automatic Tasks in Folder```

Now when the project directiory will be opened the ts checking starts and works real-time highlighting errors in the whole repo
