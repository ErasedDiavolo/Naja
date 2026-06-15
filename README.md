# NaJa UI

## Install
```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/ErasedDiavolo/Naja/refs/heads/main/Nja"))()
```

## Create Window
```lua
local Window = Library:NaJa({
    Title = "NaJa UI",
    Desc = "UI Library",
    Bind = Enum.KeyCode.RightShift,
    Discord = ""
})
```

## Tab & Section
```lua
local MainTab = Window:Tab("Main", "home")

local LeftSection = MainTab:Section("Main", "Left")
local RightSection = MainTab:Section("Extra", "Right")
```

## Labels
```lua
LeftSection:Label("Hello World")

LeftSection:LabelColor(
    "Colored Label",
    Color3.fromRGB(255, 100, 100)
)

LeftSection:Paragraph("Paragraph Text")

LeftSection:AnimatedParagraph(
    "Animated Text",
    0.04
)
```

## Buttons & Toggles
```lua
LeftSection:Button("Button", function()
    print("Clicked")
end)

LeftSection:Toggle("Toggle", false, function(state)
    print(state)
end)

LeftSection:Checkbox("Checkbox", false, function(state)
    print(state)
end)

LeftSection:Keybind("Keybind", Enum.KeyCode.F, function(key)
    print(key.Name)
end)
```

## Inputs
```lua
LeftSection:Textbox(
    "Textbox",
    "Enter Text",
    function(text)
        print(text)
    end
)

LeftSection:InputSmall(
    "Small Input",
    "Type Here",
    function(text)
        print(text)
    end
)

LeftSection:InputLarge(
    "Large Input",
    "Write Something",
    function(text)
        print(text)
    end
)
```

## Slider
```lua
LeftSection:Slider(
    "Slider",
    false,
    0,
    100,
    50,
    function(value)
        print(value)
    end
)
```

## Dropdowns
```lua
LeftSection:Dropdown(
    "Dropdown",
    {"Option 1", "Option 2", "Option 3"},
    "Option 1",
    function(selected)
        print(selected)
    end
)

LeftSection:MultiDropdown(
    "Multi Dropdown",
    {"Option 1", "Option 2", "Option 3"},
    {"Option 1"},
    function(selected)
        print(selected)
    end
)

LeftSection:Dropdown(
    "Search Dropdown",
    {"Option 1", "Option 2", "Option 3"},
    "Option 1",
    function(selected)
        print(selected)
    end,
    true
)

LeftSection:DropdownV2(
    "Floating Dropdown",
    {"Option 1", "Option 2", "Option 3"},
    "Option 1",
    function(selected)
        print(selected)
    end
)
```

## Images
```lua
LeftSection:Image({
    Name = "Preview",
    Image = "rbxassetid://0",
    Height = 150
})
```

## Videos
```lua
LeftSection:Video({
    Name = "Video",
    Video = "rbxassetid://0",
    Height = 150,
    Playing = true,
    Looped = true
})
```

## Profile Card
```lua
MainTab:ProfileCard({
    Banner = "rbxassetid://0",
    BannerHeight = 120,
    Pfp = "rbxassetid://0",
    Name = "NaJa UI",
    Description = "UI Library"
})
```

## Tab Background
```lua
MainTab:SetTabImage(
    "rbxassetid://0",
    0.15
)
```

## Notifications
```lua
Window:Notify(
    "NaJa UI",
    "Loaded Successfully",
    5
)
```

## Credits

- Diablo
