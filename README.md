# [🦏 Rhino Secrets](https://runxel.github.io/rhino-secrets/)
A collection of cool stuff and lesser known facts on Rhino you might or might not know.

<hr>

## Rhino

### Explain NURBS to me
Go and see this wonderful explanation: [«Nurbs is just an acronym»](https://wordsandbuttons.online/nurbs_is_just_an_acronym.html)  
![nurbs explaination picture](/img/explain_nurbs.png)

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

### Find layer
Every so often you are in need of finding the layer the object is in – in the layer tree. Of course we can see the layer name of the selected object in the statusbar, but when working with many (and possibly similar named) layers this information alone is sometimes not enough.  
With the object select go to your layers panel and click on the hammer icon, then choose "Select Object Layer". Rhino will unfold the layer structure for you and and highlight the right layer.

### Fast layer assign
To change the layer of the selected object(s) click on the layer name in statusbar and choose another layer.  
Since this pop-up is actually a full-fledged layer manager you can also set your current layer (when no object is selected), or hide/show and lock/unlock layers.

### Different looking
Take advantage of the possibility to assign a display mode to an object via `_SetObjectDisplayMode`.  
![Artic Viewport with transparent paraboloid picture](/img/set_obj_display_mode.png)

### Fast Osnap
Right-mouse click on an osnap filter in the panel to check that one and uncheck all the others. Right click again to restore the state before.

### Osnaps reloaded
Pressing and holding <kbd>shift</kbd> to reverse the effect of your current Ortho setting.  
Pressing and holding <kbd>alt</kbd> suspends any persistent Osnaps without unchecking them.

### Easy dragging
Long-press LMB on an object to drag and Rhino will find the closest snapping point and use that one while dragging.

### Fast angle snap
Hover your mouse over a point during a command and press <kbd>Tab</kbd> to lock the current angle.

### Quick angles
While using a drawing command like `_pline`, you can choose a relative angle to your point by typing in `<angle`. For example: `<35`

### Elevator mode
When drawing a polyline <kbd>ctrl</kbd> + <kbd>click</kbd> on your previous point to draw vertical regarding the Cplane.

### Elevate during drag
Everybody knows <kbd>shift</kbd> for constraining objects orthogonally on plane; use <kbd>shift</kbd> + <kbd>ctrl</kbd> and you can lock it vertically.

### Distance
When prompted for a second point you can also just type in a distance and enter. That constrains the distance from the first point. Then click on something in the correct direction and you're done!

### Select Last
While many operations unselect objects that have just been created or modified, `_SelLast` gives an instant access to them.  
(Mind that the default option `DeselectOthersBeforeSelect` is set to `Yes`. Having changed it once the option will stick.)

### Select specific
`_SelectionFilter` gives you a dockable menu which let you omit whatever geometry types you want from being selected.

### Select in dense areas
When selecting in dense environments, you often want to select around something, but then once clicking to drag your selection window, it already selects something and you end up dragging geometry instead. This can be avoided using the <kbd>alt</kbd> button while making the selection.

### Coordinates
When Rhino prompts for a "next point", typing `.x`, `.y` or `.z` (or even combinations like `.zx`) constrains the following point input to that coordinate type. Very useful when selecting points in different viewports.

### Easy Polysurface editing
Give `_SolidPtOn` a try.  
![solidpt picture](/img/solidpton.png)

### Move on
... with `_MoveUVN`. Works beatifully with `_SelU` and `_SelV`.

### Surfaces want to be one
`_MergeAllFaces` command to turn _coplanar polysurface faces_ into one face.  

`_MergeSrf` command to join surfaces together without making a polysurface (makes a new single surface, even if surfaces are not co-planar).

### Rebuild your edges
If you use the `_RebuildEdges` command it will restore the original trimmed or non-trimmed edges of a surface. This will vastly reduce the amount of newly added control points of most surfaces that are extruded from- or matched to the surface with rebuilt edges.  
You can use this macro with polysurfaces:
```
! _Explode
_RebuildEdges _Enter
_Join
```

### To Infinity...
... and beyond. Use `_IPlane` (alias `ip`) any time you need a plane – to trim with, intersect, Boolean operations, etc. You can even `_FilletSrf` to an IP!

### Gumball galore
Use <kbd>shift</kbd> + <kbd>ctrl</kbd> + <kbd>left click</kbd> to select the faces or edges of polysurfaces. You can then use the gumball to move/scale/rotate the selection.  

Press <kbd>alt</kbd>, then drag gumball arrow to make a copy.  

<kbd>Shift</kbd> + drag gumball scale box to scale in all directions.  

Scale numerically with a value of `0` in one axis using the Gumball to get the same result as `_SetPt_`.  
Use `-1` for fast mirroring in place.  

<iframe title="vimeo-player" src="https://player.vimeo.com/video/260472052" width="640" height="360" frameborder="0" allowfullscreen></iframe>

### Group-on
<kbd>Ctrl</kbd> + <kbd>shift</kbd> click on an object in a group to select that single object without losing the group. 

### They see me rollin'
<kbd>Ctrl</kbd> + <kbd>shift</kbd> + <kbd>RMB-drag</kbd> rotates the camera around the cursor (as long the cursor is hovering over any geometry).  

When spinning the view with RMB-drag, press/hold <kbd>shift</kbd> to limit spin to dominant initial rotation axis.

### Perspective is the way to go
With `_OneView` you get dynamic CPlanes in your perspective viewport.  
![oneview gif](/img/oneview.gif)

### Calibrate your scale
If you're projecting your drawing and want to set it to a specific usable scale, you should set your scale (monitor dependent) via `_Zoom1To1Calibrate`.
![calibrate zoom picture](/img/zoom_to_calibrate.png)

### Get the ZBuffer
With `_ShowZBuffer` you can view a z-buffer output in your viewport. Use the command again to exit the view. Sadly there is currently no way to set a custom render distance – it will be calculated automatically based on the geometry in your scene.  
![zbuffer picture](/img/zbuffer.png)

### Render mesh
Sometimes it might be necessary to see the render mesh of an object. You could achieve this by typing in `_ShowRenderMesh`, but a better way is the command `_ToggleRenderMesh`. This way you can use the same command for showing and hiding the render mesh. Both commands are not available by menu or toolbar, so it might be helpful to create it.

### View it like it's 1999
Because you want it. `_GradientView`

### Adding languages to Rhino
[See on the McNeel Wiki](https://wiki.mcneel.com/rhino/6/addlanguages)

### What are your favorites?
Find your favorite commands in this session with `_PopUpPopular`.

### Be a DJ
Use `_Turntable` to let your camera rotate around your scene. Only thing missing: some sick beats.

### Dual Monitor
Try `TestMooCow` to synchronize 2 viewports.  

EXPERIMENTAL
{: .exp}

### Flashing
`TestRandColor` – Epileptics beware!  

EXPERIMENTAL
{: .exp}

### Sesame Street
Easteregg: `Elmo` is still a valid alias for `_Rebuild`.  
(Why? Because it makes objects soft and friendly...)

### Running Python scripts from aliases or toolbar buttons
[Read on the McNeel forum](https://discourse.mcneel.com/t/running-python-scripts-from-aliases-or-toolbar-buttons/)

<hr>

## Grasshopper

### Understanding Data Trees
The famous [https://vimeo.com/channels/datatreegh]('Data Trees Masterclass with David Rutten') is highly recommended to watch.

Also have a look at this wonderful [/files/Data-Trees-by-Andrew-Heuman.pdf](PDF) made by Andrew Heumann from which the following figures were taken:

![Data trees architectural explanation picture](/img/data_trees_expl_arch.png)

![Data trees explanation picture](/img/data_trees_expl.png)

### Geometry Pipeline
If you haven't already used the "Geometry Pipeline" component in Grasshopper, you should start doing it!  
The geometry pipeline is a link to the opened Rhino doc which lets you auto-reference any geometry. It _pipes_ your geometry into Grasshopper, based on type, name and layer filters.  
The notation for the filter is Regex-style and case sensitive. A double colon `::` is used to get into nested layers.  

| Wildcard | Meaning |
| --- | --- |
| `?` | Any single character |
| `*` | Zero or more character |
| `#` | Any single digit \[0-9\] |
| `[chars]` | Any character from inside the brackets |
| `[!chars]` | Any character _except_ from inside the brackets |

![geo pipeline picture](/img/geo_pipeline.png)

### What does the red wire do?
You probably already asked yourself what the red wire does in Grasshopper when you accidentally pressed <kbd>Alt</kbd> on your keyboard while wiring components.  
The answer: it names relays and also other inputs!  
_(Note: at least for me the behaviour is bugged and you need to do this twice, bevor the name gets auto propagated.)_  
![red wiring picture](/img/red_wiring.png)

### Old components
There might be the need have an old component in your Grasshopper definition, be it due to exchange with someone who is still on Rhino 5 or whatever.  
Searching for the component but putting a `#` in front will yield those old components.

### Code in your editor of choice – Run in Grasshopper
Right click into the GhPython component and choose "Show 'code' input parameter". Now using a "File path" primitive and the "Read File" component we can feed the python component with some external source code.  
![code feed into python picture](/img/code_feed_python.png)

If you want to have autocomplete in your editor, you should have a look at the awesome ["Ironstubs"](https://github.com/gtalarico/ironpython-stubs). It's usable in Atom, Sublime Text, Vim and Visual Studio Code.  
![sublime-large-demo](https://raw.githubusercontent.com/gtalarico/ironpython-stubs/master/docs/sublime/sublime-demo-large.gif)

### Have IO descriptors in python
[Sample file](https://www.grasshopper3d.com/forum/topics/changing-the-description-of-and-input-output-in-python)  

![io picture](/img/python_io_descr.png)

### Python to native GH component
[Tutorial on discourse.mcneel.com](https://discourse.mcneel.com/t/tutorial-creating-a-grasshopper-component-with-the-python-ghpy-compiler/)