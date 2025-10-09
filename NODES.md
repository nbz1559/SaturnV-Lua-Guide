# Nodes
Nodes are what the actions and toggles etc are in your script, when you do menu.action() for example, it will return an ID of the node, which you can do multiple things with, like re-parent it, re-name it, change the description, delete it and more

# node.rename(node, name)
Example:
```lua
local my_root = menu.my_root()
local action = menu.action(my_root, "To be renamed", "", function()

end)

node.rename(action, "This has been renamed")
```
That will change the name to "This has been renamed"
If you want to change the name of the node use this

# node.rename_desc(node, desc)

Example:
```lua
local my_root = menu.my_root()
local action = menu.action(my_root, "Test", "", function()

end)

node.rename_desc(action, "Description")
```
That will change the description to "Description"
If you want to rename the description/information use this

#node.parent(node, parent)

Example:
```lua
local my_root = menu.my_root()
local action = menu.action(my_root, "Test", "", function()

end)

local list = menu.list(my_root, "List", "A list with some options")

node.parent(node, list)
```
That will place the node inside of 'list' instead of the root

#node.delete(node)

Example:
```lua
local action = menu.action(my_root, "Test", "", function()

end)

local list = menu.list(my_root, "List", "A list with some options")

node.delete(node)
```

This will remove the node from the GUI aswell as all of its children if its a list. This erases the node from the node controller in the asi file, meaning it can no longer be used.
