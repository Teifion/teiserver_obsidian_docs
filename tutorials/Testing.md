---
tags:
  - tutorial
  - testing
---
## Testing
Run with
```sh
iex -S mix phx.server
```

Then load up your BAR client of choice. Set the server to `localhost` and connect. If you are familiar with Elixir then the above command has put the server in console mode and you can execute commands through the modules there too as needed.

## Integration tests ([[hailstorm/readme|Hailstorm]])
We have a separate project to perform integration tests on Teiserver called [Hailstorm](https://github.com/beyond-all-reason/hailstorm). All Hailstorm documentation is located on the [Hailstorm repo](https://github.com/beyond-all-reason/hailstorm).

## Debugging with VSCode using ElixirLS
You can run the server in the visual studio code debugger using the ElixirLS extension

#### Windows and WSL users
For WSL users make sure Visual Studio Code is running using the WSL extention and is connected remotely to your WSL instance, for more info on how to do this consult [the relevant microsoft documentation](https://code.visualstudio.com/docs/remote/wsl) 

Next in the teiserver root directory open VSCode with 
```sh
code .
```

In extensions you need to install [ElixirLS](https://marketplace.visualstudio.com/items?itemName=JakeBecker.elixir-ls) 
If you have no Terminal open go to Terminal>Run to open a terminal in VS Code then click on Debug Console to have access to the program output and the Interactive REPL mode while debugging

Then make sure you have any elixir file selected and in the run and debug panel click on **create a launch.json file**

In the file you need to add the line `"task": "phx.server",` to the first configuration

the full launch.json should look like that:
```json
{
    "version": "0.2.0",
    "configurations": [

        {
            "type": "mix_task",
            "name": "mix (Default task)",
            "request": "launch",
            "task": "phx.server",
            "projectDir": "${workspaceRoot}"
        },
        {
            "type": "mix_task",
            "name": "mix test",
            "request": "launch",
            "task": "test",
            "taskArgs": [
                "--trace"
            ],
            "startApps": true,
            "projectDir": "${workspaceRoot}",
            "requireFiles": [
                "test/**/test_helper.exs",
                "test/**/*_test.exs"
            ]
        }
    ]
}
```

Then you can press the mix (Default task) button or F5 to start debugging. **It may take a while to start**