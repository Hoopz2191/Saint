Devoloped by knkwq

Saint UI Library

A modern, dark-themed UI library for Roblox with smooth animations and a clean interface.

Features

· 🎨 Dark theme with smooth animations
· 🖱️ Draggable windows and floating button
· 📱 Responsive design
· 🎯 Multiple UI elements (buttons, toggles, sliders, dropdowns, etc.)
· ⌨️ Keybind support
· 🔔 Notification system
· 💻 Built-in console/terminal

Installation

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Hoopz2191/Saint/refs/heads/main/Saint%20Interface"))()
```

Basic Usage

Creating a Window

```lua
local Window = Library.new({
    Title = "My Script",
    Description = "Cool script by me",
    Keybind = Enum.KeyCode.RightControl, -- Optional keybind to toggle UI
    Logo = "rbxassetid://18810965406", -- Optional logo
    Size = UDim2.new(0.1, 445, 0.1, 315) -- Window size
})
```

Adding Tabs

```lua
local MainTab = Window:NewTab({
    Title = "Main",
    Description = "Main Features",
    Icon = "rbxassetid://7733964640"
})

local SettingsTab = Window:NewTab({
    Title = "Settings",
    Description = "Configuration",
    Icon = "rbxassetid://7733993211"
})
```

Adding Sections

```lua
local CombatSection = MainTab:NewSection({
    Position = "Left", -- "Left" or "Right"
    Title = "Combat",
    Icon = "rbxassetid://7733964640"
})

local MovementSection = MainTab:NewSection({
    Position = "Right",
    Title = "Movement",
    Icon = "rbxassetid://7733993369"
})
```

UI Elements

Button

```lua
CombatSection:NewButton({
    Title = "Kill All",
    Callback = function()
        print("Killing all players...")
        -- Your code here
    end
})
```

Toggle

```lua
local AutoFarmToggle = CombatSection:NewToggle({
    Title = "Auto Farm",
    Default = false,
    Callback = function(Value)
        print("Auto Farm:", Value)
        -- Your toggle logic here
    end
})

-- Later update the toggle value
AutoFarmToggle:Value(true)
```

Slider

```lua
CombatSection:NewSlider({
    Title = "WalkSpeed",
    Min = 16,
    Max = 200,
    Default = 16,
    Step = 1,
    Callback = function(Value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
    end
})
```

Dropdown

```lua
local WeaponDropdown = CombatSection:NewDropdown({
    Title = "Weapon",
    Data = {"Sword", "Axe", "Bow", "Staff"},
    Default = "Sword",
    Callback = function(Value)
        print("Selected weapon:", Value)
    end
})

-- Update dropdown options later
WeaponDropdown:Set({"New", "Weapon", "List"})
WeaponDropdown:Value("Bow")
```

Keybind

```lua
CombatSection:NewKeybind({
    Title = "Toggle Menu",
    Default = Enum.KeyCode.F,
    Callback = function(Key)
        print("Keybind pressed:", Key)
        Window.WindowToggle = not Window.WindowToggle
        Window.Update()
    end
})
```

Textbox

```lua
CombatSection:NewTextbox({
    Title = "Player Name",
    Default = "",
    FileType = ".txt", -- Optional file type display
    Callback = function(Text)
        print("Searching for:", Text)
    end
})
```

Title (Label)

```lua
CombatSection:NewTitle("Important Features")
```

Advanced Features

Notifications

```lua
local Notify = Library.Notification()

Notify:new({
    Title = "Success",
    Description = "Script loaded successfully!",
    Duration = 5,
    Icon = "rbxassetid://7733993369"
})
```

Console/Terminal

```lua
local Console = Library:Console()

-- Add custom commands
Console:add("hello", function(args)
    Console:print("Hello World!")
end)

Console:add("print", function(args)
    Console:print(table.concat(args, " "))
end)
```

Custom Effects

```lua
-- Add gradient effect to window
Window.AddEffect(Color3.fromRGB(255, 0, 0)) -- Red effect
Window.AddEffect(Color3.fromRGB(0, 255, 0)) -- Green effect
```

Complete Example

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/your-repo/main.lua"))()

local Window = Library.new({
    Title = "Hack Script",
    Description = "Best script ever",
    Keybind = Enum.KeyCode.RightControl,
    Logo = "rbxassetid://18810965406"
})

-- Main Tab
local MainTab = Window:NewTab({
    Title = "Main",
    Description = "Main Features",
    Icon = "rbxassetid://7733964640"
})

local CombatSection = MainTab:NewSection({
    Position = "Left",
    Title = "Combat",
    Icon = "rbxassetid://7733964640"
})

local MovementSection = MainTab:NewSection({
    Position = "Right",
    Title = "Movement",
    Icon = "rbxassetid://7733993369"
})

-- Combat Features
CombatSection:NewTitle("Combat Features")

CombatSection:NewToggle({
    Title = "Kill Aura",
    Default = false,
    Callback = function(Value)
        print("Kill Aura:", Value)
    end
})

CombatSection:NewButton({
    Title = "Teleport to Boss",
    Callback = function()
        print("Teleporting to boss...")
    end
})

CombatSection:NewSlider({
    Title = "Damage Multiplier",
    Min = 1,
    Max = 10,
    Default = 1,
    Step = 0.1,
    Callback = function(Value)
        print("Damage Multiplier:", Value)
    end
})

-- Movement Features
MovementSection:NewTitle("Movement Features")

MovementSection:NewToggle({
    Title = "Speed Hack",
    Default = false,
    Callback = function(Value)
        print("Speed Hack:", Value)
    end
})

MovementSection:NewKeybind({
    Title = "Fly Toggle",
    Default = Enum.KeyCode.X,
    Callback = function(Key)
        print("Fly toggled with:", Key)
    end
})

MovementSection:NewDropdown({
    Title = "Teleport Locations",
    Data = {"Spawn", "Safe Zone", "Boss Arena", "Secret Base"},
    Default = "Spawn",
    Callback = function(Value)
        print("Teleporting to:", Value)
    end
})

-- Settings Tab
local SettingsTab = Window:NewTab({
    Title = "Settings",
    Description = "Configuration",
    Icon = "rbxassetid://7733993211"
})

local ConfigSection = SettingsTab:NewSection({
    Position = "Left",
    Title = "Configuration",
    Icon = "rbxassetid://7733993211"
})

ConfigSection:NewButton({
    Title = "Save Config",
    Callback = function()
        Library.Notification():new({
            Title = "Success",
            Description = "Configuration saved!",
            Duration = 3,
            Icon = "rbxassetid://7733993369"
        })
    end
})

ConfigSection:NewTextbox({
    Title = "Config Name",
    Default = "MyConfig",
    Callback = function(Text)
        print("Config name:", Text)
    end
})

-- Show notification when script loads
task.spawn(function()
    task.wait(1)
    Library.Notification():new({
        Title = "Script Loaded",
        Description = "Hack script successfully loaded!",
        Duration = 5,
        Icon = "rbxassetid://7733964640"
    })
end)
```

API Reference

Window Methods

· Window:NewTab(config) - Create new tab
· Window.AddEffect(color) - Add gradient effect
· Window.WindowToggle - Window visibility state
· Window.Update() - Force UI update

Tab Methods

· Tab:NewSection(config) - Create new section

Section Methods

· Section:NewButton(config) - Create button
· Section:NewToggle(config) - Create toggle
· Section:NewSlider(config) - Create slider
· Section:NewDropdown(config) - Create dropdown
· Section:NewKeybind(config) - Create keybind
· Section:NewTextbox(config) - Create textbox
· Section:NewTitle(text) - Create title/label

Toggle Methods

· Toggle:Value(newValue) - Update toggle state
· Toggle:Visible(visible) - Show/hide toggle

Dropdown Methods

· Dropdown:Value(value) - Set dropdown value
· Dropdown:Set(data) - Update dropdown options
· Dropdown:Clear() - Clear dropdown options
· Dropdown:Open() - Open dropdown
· Dropdown:Close() - Close dropdown

Tips

· Use Position = "Left" or "Right" to organize sections
· Set appropriate Step values for sliders
· Use notifications for user feedback
· The floating button can be dragged to reposition
· Window is draggable when open
· Keybinds work even when UI is closed

License

MIT License - Feel free to use in your projects!
