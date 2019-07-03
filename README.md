# [🦏 Rhino Secrets](https://runxel.github.io/rhino-secrets/)
A collection of cool stuff and facts on Rhino you might or might not know.

## Rhino
### Symbols in command line
Ever wondered what the specials chars in commands meant? Or are you always forgetting?  

| Char | Meaning |
| --- | --- |
| `*` | Causes the command to repeat automatically without pressing <kbd>Enter</kbd> to restart. (used in macros) |
| `!` | Cancels the previous command. |
| `_` | Runs command as English command name. |
| `-` | Suppress any dialog box. |
| `'` | The apostrophe tells that next command is a nestable command. (geometry creations are never nestable) |
| `/` | If the first character in a toolbar macro is not "!" and the last character is" /", the script runs on the command line without <kbd>Enter</kbd>, so more information can be added. |
| `~` | Suppresses command options for clutter free command feedback. |
| `;` | Comment. (used in macros) |

### Rebuild your edges
If you use the `RebuildEdges` command it will restore the original trimmed or non-trimmed edges of a surface. This will vastly reduce the amount of newly added control points of most surfaces that are extruded from- or matched to the surface with rebuilt edges.  
You can usethis macro with polysurfaces:
```
! _Explode
_RebuildEdges _Enter
_Join
```

### Different looking
Take advantage of the possibility to assign a display mode to an object via `_SetObjectDisplayMode`.
![set object display mode](/img/set_obj_display_mode.pg "Artic Viewport with transparent paraboloid")

<hr>

## Grasshopper
### What does the red wire do?
You probably already asked yourself what the red wire does in Grasshopper when you accidentally pressed <kbd>Alt</kbd> on your keyboard while wiring components.  
The answer: it names e.g. relays!  
_(Note: at least for me the behaviour is bugged and you need to do this twice, bevor the name gets auto propagated.)_  
![red wiring](/img/red-wiring_1.png)

![red wiring](/img/red-wiring_2.png)
