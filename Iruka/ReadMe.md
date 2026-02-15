# 🐬 IrukaUI - Elite Executive Library

IrukaUI is a premium, modern, and highly secure UI library for Roblox executors. It is a heavily modified and enhanced version of the Orion Library, rebuilt from the ground up to prioritize **Anti-Detection**, **Visual Excellence**, and **Developer Workflow**.

---

## Key Features

- **Advanced Anti-Detection**: 
  - Every UI element is assigned a unique, randomized name at runtime.
  - Decoupled internal indexing via a secure mapping system.
  - No global variables (like `gethui`) exposed; uses localized environment detection.
- **Premium Modern Design**:
  - Consistent 8px rounding across all components.
  - Smooth "Fade & Slide" tab transitions.
  - Minimalist scrollbars (2px thin, translucent).
- **Dynamic Theme System**:
  - Centralized **Accent Color** support (all sliders and highlights sync automatically).
  - Background transparency controls with real-time refresh.
- **Automated Managers**:
  - **InterFaceManager**: Add full theme/visual customization to your script in one line.
  - **ConfigManager**: Built-in UI for saving, loading, and deleting configurations.
- **Elite Player Utilities**:
  - Detailed `PlayerList` with avatars and display names.
  - Quick-select `PlayersDropdown`.
  - Identity-focused `PlayerParagraph`.

---

## Quick Start

```lua
local IrukaUI = loadstring(game:HttpGet(('YOUR_LINK_HERE')))()

local Window = IrukaUI:MakeWindow({
    Name = "Project Iruka",
    HidePremium = true,
    SaveConfig = true,
    ConfigFolder = "Iruka_Configs"
})

-- Creating a Tab
local Tab = Window:MakeTab({
    Name = "Main",
    Icon = "rbxassetid://7072718816"
})

-- Common Elements
Tab:AddToggle({
    Name = "Active Feature",
    Default = false,
    Callback = function(Value) print(Value) end
})

Tab:AddButton({
    Name = "Click Me",
    Callback = function() print("Button Pressed") end
})

IrukaUI:Init()
```

---

## Component Documentation

### Window Configuration
| Property | Type | Description |
| :--- | :--- | :--- |
| `Name` | string | Title of your UI Window. |
| `SaveConfig` | boolean | Enables automatic configuration saving. |
| `ConfigFolder` | string | Name of the folder where configs are stored in workspace. |
| `IntroEnabled` | boolean | Show the Iruka splash animation on load. |
| `KeyToOpenWindow` | string | KeyCode to toggle the UI (Default: `RightShift`). |

### New Component: PlayerList
```lua
Tab:AddPlayerList({
    Name = "Kill List",
    Multi = true, -- Allow selecting multiple players
    Big = true,   -- Show detailed info (Icon, Username, DisplayName)
    Callback = function(Selected)
        -- 'Selected' is a table of Usernames
    end
})
```

### Automated Managers (Settings Tab)
Add these to your settings tab to give your users full control without writing extra code:
```lua
local SettingsTab = Window:MakeTab({Name = "Settings"})

-- Visual/Theme Controller
IrukaUI.InterFace():SetTab(SettingsTab)

-- Save/Load Config Controller
IrukaUI:ConfigManager():SetTab(SettingsTab)
```

---

## Themes
IrukaUI comes with several built-in premium themes:
- `Default` (Minimalist Dark)
- `Blue` (Electric Blue)
- `Lavender` (Purple Glow)
- `Cyberpunk` (Neon Pink/Aqua)
- `Emerald`, `Midnight`, `Rose`, `Aqua`

---

---
*Developed with ❤️ for the executive community.*
