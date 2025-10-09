# GUI API

# My Root
## menu.my_root()

my_root is what you use to define where your functions will be displayed.

Example:
```lua
local my_root = menu.my_root()
```
This is the most important part, because otherwise you wouldn't have anywhere to start.

# Lists (Submenus)
## menu.list(Parent, name, desc)

Example:
```lua
local my_root = menu.my_root()
local my_list = menu.list(my_root, "Test", "Open this")
```

In other menu API, for the parent you can either put my_root down (This just attaches it to the base) or you could put a list variable down.

# Actions
## menu.action(Parent, name, desc)

Example:
```lua
local my_root = menu.my_root()
menu.action(my_root, "Test", "Does something", function()
-- Do something here
end)
```

Example 2 (With a list/submenu):
```lua
local my_root = menu.my_root()
local my_list = menu.list(my_root, "Test", "Open this")
menu.action(my_list, "Test", "Does something", function()
-- Also do something here
end)
```

There are some options you can do, if you dont want a description, just leave the 'desc' param like "", without any words in it.
Actions are the things in the menu that you click (Press enter on), and it runs a single function.

# Toggles
## menu.toggle(Parent, name, desc, default, loop)

Example:
```lua
local my_root = menu.my_root()
menu.toggle(my_root, "Test", "Toggle something", false, false, function(state)
if state == true then
-- Do something if the user toggles it on
else
-- Do something if the user toggles it off
end
end)
```

Example 2 (With loop on)
```lua
local my_root = menu.my_root()
menu.toggle(my_root, "Test", "Toggle something", false, true, function(state)
if state == true then
-- Run something that has to be called every frame, like a Graphics native
else
-- Do something if the user toggles it off
end
end)
```

### What each param means
Parent name and desc are pretty straight foward, they are exactly like the others.
'default' is the default value, if set to true, the toggle will be on automatically.
If the default is set to false, it will be false.

If 'loop' is on, that means the code inside of the toggle will run every frame.
If 'loop' is off, the code will run once.

# Sliders
## menu.slider(parent, name, desc, minval, maxval, increment, defaultval, isSliderClick)

Example:
```lua
local my_root = menu.my_root()
menu.slider(my_root, "Test", "Pick a value", 0, 10, 1, 0, true, function(value)
-- Example code
PLAYER.SET_PLAYER_WANTED_LEVEL(PLAYER.PLAYER_ID(), val, false)
PLAYER.SET_PLAYER_WANTED_LEVEL_NOW(PLAYER.PLAYER_ID(), false)
end)
```

### What each param means
'minval' Is the lowest value the slider can go to, i haven't tested negative numbers, they might work who knows.
'maxval' Is the opposite of minval, its the maximum value the slider can go to.
'increment' Is how much the slider goes up by every time the user presses the arrow key, if it set to 1 it will go up by 1, if its 2 it will go up by 2
'defaultval' Is the value the slider is set to on default
'isSliderClick' Means when the user presses enter on the slider, if isSliderClick is set to true, it will run the callback, if set to false it will prompt them with a textbox to input a value

# Slider Floats
## menu.slider_float(parent, name, desc, minval, maxval, increment, defaultval, isSliderClick)

#### Explanation
The difference between a slider and slider_float is slider_float can take decimels, where are sliders can only take integers, like 1, 2, 3, and slider floats can take 1.1, 2.2, 3.3333
Example:
```lua
local my_root = menu.my_root()
menu.slider_float(my_root, "Test", "Choose an option from 0.0, 7.7", 0.0, 7.7, 1.2, 0.5, true, function(value)
-- Do something with the number given
end)
```

### WHat each param means
All parameters are the same as a regular slider

# Text sliders
## menu.text_slider(parent, name, desc, defaultindex, {Options table})

Example:
```lua
local my_root = menu.my_root()
local text_slider_1_options = {"Option1", "Option2", "Option3"} -- Your options table
menu.text_slider(my_root, "Test", "Pick a option", 0, text_slider_1_options, function(index)
-- Example code
if index == 0 then
-- Do a function
end
end)
```

### What each param means
First off, a bit about 'indexs', in the options table, Option 1 will always be 0, then after that, option 2 = 1, option 3 = 2 and so on

'defaultindex' Is the same as 'defaultval' from before, set it to 0 if you want your Option1 to be the default
'{Options table}' Is where the options for your text_slider will be

# Text inputs
## menu.text_input(parent, name, desc)

Example:
```lua
local my_root = menu.my_root()
menu.text_input(my_root, "Test", "Input a value", function(text)
-- Do something with the users input
end)
```

### What each param means
All of them are the same as others
The call back (text) is a string, to convert it to a number, do ```tonumber(text) ```

# Place holders
## menu.place_holder(parent, name)

Example:
```lua
local my_root = menu.my_root()
menu.place_holder(my_root, " -- Cars -- ")
```

Personally i like to use this layout ``` -- Text -- ``` because it looks neat, but you can do whatever

A place holder is something that is just there, to tell the user something like whats below it. in SaturnV > Lua Scripts > Your script, there is a place holder called ``` -- Lua Functions -- ```
That is an example of a place holder

# Hyper Links
## menu.hyper_link(parent, name, desc, url)

Example:
```lua
local my_root = menu.my_root()
menu.hyper_link(my_root, "Open Youtube", "Directs you to youtube", "youtube.com")
```

Pretty straight foward, make sure to wrap your url in quotation marks
