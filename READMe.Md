# Saint UI Library

<img src="https://raw.githubusercontent.com/your-repo/Assets/main/logodark.png#gh-dark-mode-only" alt="Saint">

# ⚡ Features
**
 Modern dark theme design
· Smooth animations and transitions
· Draggable windows and floating button
· Multiple UI elements (toggles, buttons, sliders, dropdowns, keybinds, textboxes)
· Built-in notification system
· Console/terminal interface**
  

# 🔌 Installation

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/your-repo/main/main.lua"))()
```

<br/>

# 📜 Usage

**Step 1: Create a Window**

```lua
local Window = Library.new({
    Title = "My Script",
    Description = "Best script ever",
    Keybind = Enum.KeyCode.RightControl, -- Optional
    Logo = "rbxassetid://18810965406", -- Optional
    Size = UDim2.new(0.1, 445, 0.1, 315) -- Optional
})
```

**Step 2: Add Tabs**

```lua
local MainTab = Window:NewTab({
    Title = "Main",
    Description = "Main Features",
    Icon = "rbxassetid://7733964640"
})
```

**Step 3: Add Sections**

```lua
local CombatSection = MainTab:NewSection({
    Position = "Left", -- "Left" or "Right"
    Title = "Combat",
    Icon = "rbxassetid://7733964640"
})
```

**Step 4: Add UI Elements**

**Toggle**

```lua
local MyToggle = CombatSection:NewToggle({
    Title = "Auto Farm",
    Default = false,
    Callback = function(Value)
        print("Auto Farm:", Value)
    end
})

-- Update toggle later
MyToggle:Value(true)
```

Button

```lua
CombatSection:NewButton({
    Title = "Kill All",
    Callback = function()
        print("Button clicked!")
    end
})
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
local MyDropdown = CombatSection:NewDropdown({
    Title = "Weapon",
    Data = {"Sword", "Axe", "Bow"},
    Default = "Sword",
    Callback = function(Value)
        print("Selected:", Value)
    end
})

-- Update dropdown later
MyDropdown:Set({"New", "Weapons"})
MyDropdown:Value("Bow")
```

Keybind

```lua
CombatSection:NewKeybind({
    Title = "Toggle Menu",
    Default = Enum.KeyCode.F,
    Callback = function(Key)
        print("Key pressed:", Key)
    end
})
```

Textbox

```lua
CombatSection:NewTextbox({
    Title = "Player Name",
    Default = "",
    Callback = function(Text)
        print("Text entered:", Text)
    end
})
```

Title (Label)

```lua
CombatSection:NewTitle("Important Features")
```

Step 5: Notifications (Optional)

```lua
local Notify = Library.Notification()

Notify:new({
    Title = "Success",
    Description = "Script loaded!",
    Duration = 5,
    Icon = "rbxassetid://7733993369"
})
```

Step 6: Console (Optional)

```lua
local Console = Library:Console()

-- Add custom commands
Console:add("hello", function(args)
    Console:print("Hello World!")
end)
```

<br/>

📋 Full Example

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/your-repo/main/main.lua"))()

-- Create window
local Window = Library.new({
    Title = "Hack Script",
    Description = "Best script ever",
    Keybind = Enum.KeyCode.RightControl
})

-- Main tab
local MainTab = Window:NewTab({
    Title = "Main",
    Description = "Main Features",
    Icon = "rbxassetid://7733964640"
})

-- Combat section
local CombatSection = MainTab:NewSection({
    Position = "Left",
    Title = "Combat",
    Icon = "rbxassetid://7733964640"
})

-- Add elements to combat section
CombatSection:NewTitle("Combat Features")

local KillAuraToggle = CombatSection:NewToggle({
    Title = "Kill Aura",
    Default = false,
    Callback = function(Value)
        print("Kill Aura:", Value)
    end
})

CombatSection:NewButton({
    Title = "Teleport to Boss",
    Callback = function()
        print("Teleporting...")
    end
})

CombatSection:NewSlider({
    Title = "Damage Multiplier",
    Min = 1,
    Max = 10,
    Default = 1,
    Step = 0.1,
    Callback = function(Value)
        print("Damage:", Value)
    end
})

local WeaponDropdown = CombatSection:NewDropdown({
    Title = "Weapon",
    Data = {"Sword", "Axe", "Bow"},
    Default = "Sword",
    Callback = function(Value)
        print("Weapon:", Value)
    end
})

CombatSection:NewKeybind({
    Title = "Fly Toggle",
    Default = Enum.KeyCode.X,
    Callback = function(Key)
        print("Fly key:", Key)
    end
})

-- Movement section
local MovementSection = MainTab:NewSection({
    Position = "Right",
    Title = "Movement",
    Icon = "rbxassetid://7733993369"
})

MovementSection:NewToggle({
    Title = "Speed Hack",
    Default = false,
    Callback = function(Value)
        print("Speed Hack:", Value)
    end
})

-- Settings tab
local SettingsTab = Window:NewTab({
    Title = "Settings",
    Description = "Configuration",
    Icon = "rbxassetid://7733993211"
})

local ConfigSection = SettingsTab:NewSection({
    Position = "Left",
    Title = "Config",
    Icon = "rbxassetid://7733993211"
})

ConfigSection:NewButton({
    Title = "Save Config",
    Callback = function()
        Library.Notification():new({
            Title = "Success",
            Description = "Config saved!",
            Duration = 3,
            Icon = "rbxassetid://7733993369"
        })
    end
})

-- Show welcome notification
task.spawn(function()
    task.wait(1)
    Library.Notification():new({
        Title = "Welcome",
        Description = "Script loaded successfully!",
        Duration = 5,
        Icon = "rbxassetid://7733964640"
    })
end)
```

🎨 Customization

· Use Window.AddEffect(Color3.fromRGB(255, 0, 0)) for gradient effects
· Drag the floating button to reposition
· Drag the window when open to move it
· Use keybinds to toggle UI visibility

📝 Notes

· All callbacks are executed in a separate thread
· UI elements can be dynamically updated
· Notifications auto-dismiss after duration
· Console supports custom commands

<br/>

Credits

· Inspired by modern UI libraries
· Smooth animations and transitions
· Dark theme design
