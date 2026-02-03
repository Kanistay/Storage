# Kanistay Library
This documentation is for the stable release of Kanistay Library.

## Booting the Library
```lua
local OrionLib = loadstring=special
```

## Creating a Window
```lua
local Window = OrionLib:MakeWindow({
    Name = "Title of the library", 
    HidePremium = false, 
    SaveConfig = true, 
    ConfigFolder = "OrionTest"
})

--[[
Name = <string> - The name of the UI.
HidePremium = <bool> - Whether or not the user details shows Premium status.
SaveConfig = <bool> - Toggles the config saving in the UI.
ConfigFolder = <string> - The name of the folder where the configs are saved.
IntroEnabled = <bool> - Whether or not to show the intro animation.
IntroText = <string> - Text to show in the intro animation.
IntroIcon = <string> - URL to the image you want to use in the intro animation.
Icon = <string> - URL to the image you want displayed on the window.
CloseCallback = <function> - Function to execute when the window is closed.
]]
```

## Creating a Tab
```lua
local Tab = Window:MakeTab({
    Name = "Tab 1",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to premium users only.
]]
```

## Creating a Section
```lua
local Section = Tab:AddSection({
    Name = "Section"
})

--[[
Name = <string> - The name of the section.
]]
```

## Creating a MultiSelect Dropdown
```lua
Tab:AddMultiSelect({
    Name = "MultiSelect Example",
    Options = {"Option 1", "Option 2", "Option 3"},
    Default = {"Option 1"}, -- Default selected values (optional)
    Flag = "multiSelectFlag", -- For config saving (optional)
    Callback = function(Value)
        -- Value is a table containing all selected options
        print("Selected Values:", table.concat(Value, ", "))
    end    
})

--[[
Name = <string> - The name of the multiselect.
Options = <table> - The options in the multiselect.
Default = <table> - The default selected values (optional).
Flag = <string> - The flag for config saving (optional).
Callback = <function> - The function called when selection changes.
]]
```

### MultiSelect Functions
```lua
-- Refresh options
MultiSelect:Refresh({"New1", "New2", "New3"}, true) -- true clears current selections

-- Set selected values
MultiSelect:Set({"Option1", "Option3"})

-- Get selected values using flag
local selectedValues = OrionLib.Flags["multiSelectFlag"].Values
```

## Creating a Button
```lua
Tab:AddButton({
    Name = "Button!",
    Callback = function()
        print("button pressed")
    end    
})
```

## Creating a Toggle
```lua
Tab:AddToggle({
    Name = "This is a toggle!",
    Default = false,
    Callback = function(Value)
        print(Value)
    end    
})
```

## Creating a Slider
```lua
Tab:AddSlider({
    Name = "Slider",
    Min = 0,
    Max = 20,
    Default = 5,
    Color = Color3.fromRGB(255,255,255),
    Increment = 1,
    ValueName = "bananas",
    Callback = function(Value)
        print(Value)
    end    
})
```

## Creating a Dropdown
```lua
Tab:AddDropdown({
    Name = "Dropdown",
    Default = "1",
    Options = {"1", "2"},
    Callback = function(Value)
        print(Value)
    end    
})
```

## Creating a Colorpicker
```lua
Tab:AddColorpicker({
    Name = "Colorpicker",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(Value)
        print(Value)
    end      
})
```

## Creating a Textbox
```lua
Tab:AddTextbox({
    Name = "Textbox",
    Default = "default text",
    TextDisappear = true,
    Callback = function(Value)
        print(Value)
    end      
})
```

## Creating a Label
```lua
Tab:AddLabel("Label")
```

### Changing the value of an existing label
```lua
CoolLabel:Set("Label New!")
```


## Creating a Paragraph
```lua
Tab:AddParagraph("Paragraph","Paragraph Content")
```

### Changing an existing paragraph
```lua
CoolParagraph:Set("Paragraph New!", "New Paragraph Content!")
```


## Creating an Adaptive Input
```lua
Tab:AddTextbox({
	Name = "Textbox",
	Default = "default box input",
	TextDisappear = true,
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - The name of the textbox.
Default = <string> - The default value of the textbox.
TextDisappear = <bool> - Makes the text disappear in the textbox after losing focus.
Callback = <function> - The function of the textbox.
]]
```

## Creating a Keybind
```lua
Tab:AddBind({
    Name = "Bind",
    Default = Enum.KeyCode.E,
    Hold = false,
    Callback = function()
        print("pressed")
    end    
})
```

## Flags and Config System
```lua
-- Example of using flags
Tab:AddToggle({
    Name = "Toggle",
    Default = true,
    Save = true,
    Flag = "toggle"
})

-- Access flag value anywhere
print(OrionLib.Flags["toggle"].Value)
```

## Required Initialization
Add this at the end of your script:
```lua
OrionLib:Init()
```

## Destroying the Interface
```lua
OrionLib:Destroy()
```
```

Bu güncellenmiş dokümantasyonda:
1. Yeni MultiSelect elementi detaylı olarak eklendi
2. "Orion Library" referansları "Kanistay Library" olarak değiştirildi
3. Önemli fonksiyonlar ve özellikler korundu
4. Daha sade ve anlaşılır bir format kullanıldı
5. Gereksiz tekrarlar kaldırıldı
6. Yeni eklenen özelliklerin detaylı açıklamaları eklendi
