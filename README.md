# componentUI
* summer 2023
<br> framework to build desktop apps with a simple format. Uses -UI components and webview2
<br>
the grid stucture is created using html and a special file assigns a UI component to each tile

### layout:

![img](./assets/layout.png "")

each section can be split into any 4 subsections (top bottom left right center). a full length/width bar can be added to any edge and also in layers. also tabs can be built in to each section without needing a subsection


## UI components:
* [Tabs-UI](https://github.com/kachbit/Tabs-UI)
* [FileTree-UI](https://github.com/kachbit/FileTree-UI) 
* [Menubar-UI](https://github.com/kachbit/Menubar-UI) 
* more coming soon
<br>

``` yaml
# layout designer is in yaml
# vscode layout example for dynamic components

# setup requires layout paramters as well as corresponding numbers components
setup: 
    layout: [[1,1,1]
            ,[2,3,3]
            ,[2,4,4]] # must be a 3x3 2d array. sets of same number must be recatngular
    1: menubar
    2: filetree
    3: textbox
    4: custom1
    edgebars: B # not required
    
# then define all components from corresponding files
menubar:
    path: ./components/menubar.cui
filetree:
    path: ./components/filetree.cui
```
.cui filed are in xml format. <br>``menubar.cui``:
``` xml
<menu>
<data>
{
  "name of first dropdown": {
    "content": "dropdown_1 {% raw %}{%optionalFunctionNameHere%}{% endraw %}", // custom function name goes in:{% raw %} {%%} {% endraw %}
    subMenu:false
  },
  "name of second dropdown": {
    "content": "dropdown_2",
    submenu:false
  }
}
</data>
<funcs>
// javascript
function optionalFunctionNameHere() {
  console.log('first dropdown was clicked')
}
function dropdown_2() {
  console.log('second dropdown was clicked')
}
</funcs>
<style>
/* overwrite custom css style for menubar */
menubar {
    background: white;
    padding: 10px;
}
</style>
</menu>
```
