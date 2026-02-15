# IrukaUI Executive Library

IrukaUI is a secure, high-performance UI library for Roblox executors. It features advanced anti-detection through runtime element randomization and a comprehensive suite of modern UI components.

## Library Initialization

```lua
local IrukaUI = loadstring(game:HttpGet(('YOUR_LINK_HERE')))()

local Window = IrukaUI:MakeWindow({
    Name = "IrukaUI Script",
    HidePremium = true,
    SaveConfig = true,
    ConfigFolder = "IrukaConfigs",
    IntroEnabled = true,
    IntroText = "Iruka Library",
    KeyToOpenWindow = "RightShift"
})
```

## Tabs and Sections

```lua
local Tab = Window:MakeTab({
    Name = "Tab Name",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

local Section = Tab:AddSection({
    Name = "Section Name"
})

-- GroupBoxes provide a cleaner organization within tabs
local LeftGroup = Tab:LeftGroupBox("Left Side")
local RightGroup = Tab:RightGroupBox("Right Side")
```

## UI Elements

### Button
```lua
Tab:AddButton({
    Name = "Button Name",
    Callback = function()
        print("Button Clicked")
    end
})
```

### Toggle
```lua
Tab:AddToggle({
    Name = "Toggle Name",
    Default = false,
    Callback = function(Value)
        print("Toggle State: ", Value)
    end
})
```

### Slider
```lua
Tab:AddSlider({
    Name = "Slider Name",
    Min = 0,
    Max = 100,
    Default = 50,
    Color = Color3.fromRGB(255, 255, 255),
    Increment = 1,
    ValueName = "units",
    Callback = function(Value)
        print("Slider Value: ", Value)
    end
})
```

### Dropdown (Single Selection)
```lua
Tab:AddDropdown({
    Name = "Dropdown Name",
    Default = "Option 1",
    Options = {"Option 1", "Option 2", "Option 3"},
    Callback = function(Value)
        print("Selected: ", Value)
    end
})
```

### Multiple Dropdown (Multi-Selection)
```lua
Tab:AddMultipleDropdown({
    Name = "Multiple Dropdown",
    Default = "Option 1",
    Options = {"Option 1", "Option 2", "Option 3"},
    Callback = function(Table)
        -- Table contains all selected options
        for i, v in pairs(Table) do
            print("Selected: ", v)
        end
    end
})
```

### Keybind
```lua
Tab:AddBind({
    Name = "Bind Name",
    Default = Enum.KeyCode.F,
    Hold = false,
    Callback = function()
        print("Bind Triggered")
    end
})
```

### Textbox
```lua
Tab:AddTextbox({
    Name = "Textbox Name",
    Default = "Default Text",
    TextDisappear = true,
    Callback = function(Value)
        print("Input: ", Value)
    end
})
```

### Colorpicker
```lua
Tab:AddColorpicker({
    Name = "Colorpicker Name",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(Value)
        print("Selected Color: ", Value)
    end
})
```

### Label and Paragraph
```lua
Tab:AddLabel("Simple Text Label")

Tab:AddParagraph("Paragraph Title", "Detailed content text goes here.")
```

## Player Utilities

### Player List (Detailed)
```lua
Tab:AddPlayerList({
    Name = "Players",
    Multi = true,
    Big = true, -- Displays icons and display names
    Callback = function(SelectedList)
        -- SelectedList is a table of usernames
    end
})
```

### Players Dropdown (Compact)
```lua
Tab:AddPlayersDropdown({
    Name = "Select Player",
    MultipleSelection = false,
    Callback = function(Value)
        print("Selected Player: ", Value)
    end
})
```

### Player Paragraph
```lua
-- Displays static info for a specific UserID
Tab:AddPlayerParagraph(game.Players.LocalPlayer.UserId)
```

## System Managers

These features automate settings and configuration management within a specified tab.

```lua
local SettingsTab = Window:MakeTab({Name = "Settings"})

-- InterFace: Handles Theme, Transparency, and Accent Color controls
IrukaUI.InterFace():SetTab(SettingsTab)

-- ConfigManager: Handles Save, Load, and Delete UI for configurations
IrukaUI:ConfigManager():SetTab(SettingsTab)
```

## Notifications

```lua
IrukaUI:MakeNotification({
    Name = "Title",
    Content = "Notification Message",
    Time = 5
})
```

## Cleanup

```lua
IrukaUI:Init() -- Call after all elements are added

-- To completely remove the UI
IrukaUI:Destroy()
```
