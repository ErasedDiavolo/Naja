# NaJa UI

It's a UI library for Roblox. Not much more to it than that, but it actually works without making your game lag to death.

I built this because I got tired of libraries that look pretty in screenshots but fall apart the second you try to do anything dynamic. You know the ones "responsive layouts" that break when you add more than 3 buttons, dropdowns that clip through the map, that whole deal.

This one handles large scripts without choking. Sections resize themselves, canvas expands automatically, paragraphs wrap properly. You shouldn't have to babysit your UI framework.

---

## What's Actually In It

**Basic stuff:** Buttons, toggles, checkboxes, keybinds, sliders, textboxes, inputs, regular dropdowns, multi-dropdowns.

**The good stuff:** Searchable dropdowns with real-time filtering, floating dropdown panels that don't render behind your screen, and a transparency engine that doesn't look like garbage.

**Visual fluff:** Glassmorphism (if you're into that), animated text that types itself out, background images on tabs, zoomable images, video support, profile cards. Use it if you want, ignore it if you don't.

**Framework things:** Global settings, notification system, auto-scaling, draggable window, toggle keybind. The boring infrastructure that actually matters.

---

## Getting Started

```lua
local Library = loadstring(game:HttpGet("YOUR_LINK_HERE"))()
```

Yeah, standard loadstring. Nothing revolutionary here.

```lua
local Window = Library:NaJa({
    Title = "NaJa UI",
    Desc = "Modern Roblox UI Framework",
    Bind = Enum.KeyCode.RightShift,
    Discord = "https://discord.gg/example"
})
```

`Bind` is your toggle key. `Discord` shows up in the UI if someone wants to join. Pretty self-explanatory.

---

## Tabs & Sections

```lua
local MainTab = Window:Tab("Main", "home")
```

Second argument is the icon. Use Lucide names or whatever the icon system expects.

```lua
local LeftSection = MainTab:Section("Main Features", "Left")
local RightSection = MainTab:Section("Extra Features", "Right")
```

"Left" and "Right" are the columns. It'll balance them automatically. Don't overthink it.

---

## Elements

**Label** plain text. Boring but necessary.
```lua
LeftSection:Label("Hello World")
```

**Colored Label** same thing but you pick the color.
```lua
LeftSection:LabelColor("Colored Text", Color3.fromRGB(255,100,100))
```

**Paragraph** wraps text so it doesn't overflow everywhere.
```lua
LeftSection:Paragraph("This is a wrapped paragraph.", Color3.fromRGB(150,150,150))
```

**Animated Paragraph** types out like someone's actually typing it.
```lua
LeftSection:AnimatedParagraph("Animated typing text.", 0.04)
```

0.04 is the speed. Lower = faster. If you set it to 0.001 it'll take forever and your users will hate you.

**Button**
```lua
LeftSection:Button("Click Me", function()
    print("Clicked")
end)
```

**Toggle**
```lua
LeftSection:Toggle("Auto Farm", false, function(state)
    print(state)
end)
```

`false` is the default state.

**Checkbox** basically a toggle but looks like a checkbox. Some people prefer them visually.
```lua
LeftSection:Checkbox("ESP", false, function(state)
    print(state)
end)
```

**Keybind**
```lua
LeftSection:Keybind("Fly", Enum.KeyCode.F, function(key)
    print(key.Name)
end)
```

**Slider**
```lua
LeftSection:Slider("WalkSpeed", false, 16, 500, 16, function(value)
    print(value)
end)
```

Arguments are: name, showValue (bool), min, max, default, callback. `false` hides the number if you don't want it cluttering the UI.

**Textbox** single line.
```lua
LeftSection:Textbox("Username", "Enter Username", function(text)
    print(text)
end)
```

**InputSmall** slightly different styling, same idea.
```lua
LeftSection:InputSmall("Username", "Type Here", function(text)
    print(text)
end)
```

**InputLarge** multi-line. Good for descriptions or when you need someone to paste a webhook URL or whatever.
```lua
LeftSection:InputLarge("Description", "Write Something", function(text)
    print(text)
end)
```

---

## Dropdowns (The Part Everyone Messes Up)

**Regular dropdown:**
```lua
LeftSection:Dropdown("Weapon", {"Sword", "Gun", "Bow"}, "Sword", function(selected)
    print(selected)
end)
```

**Multi-dropdown** returns a table of selected stuff.
```lua
LeftSection:MultiDropdown("Fruits", {"Apple", "Banana", "Orange"}, {"Apple"}, function(selected)
    print(selected)
end)
```

**Searchable dropdown** add `true` at the end to enable filtering. Honestly this should probably just be default but here we are.
```lua
LeftSection:Dropdown("Search", {"Item 1", "Item 2", "Item 3"}, "Item 1", function(selected)
    print(selected)
end, true)
```

**Floating Dropdown V2** detached panel that floats instead of pushing content down. Use this if your dropdown has 50 options and you don't want it to resize your entire section.
```lua
LeftSection:DropdownV2("Weapon", {"Sword", "Gun", "Bow"}, "Sword", function(selected)
    print(selected)
end)
```

---

## Media Stuff

**Image**
```lua
LeftSection:Image({
    Name = "Preview",
    Image = "rbxassetid://0",
    Height = 150
})
```

**Video** yes, it plays videos. No, don't autoplay loud ones. Please.
```lua
LeftSection:Video({
    Name = "Preview Video",
    Video = "rbxassetid://0",
    Height = 150,
    Playing = true,
    Looped = true
})
```

---

## Profile Cards

If you want to flex or show credits or whatever.
```lua
MainTab:ProfileCard({
    Banner = "rbxassetid://0",
    BannerHeight = 120,
    Pfp = "rbxassetid://0",
    Name = "NaJa UI",
    Description = "Modern Roblox UI Framework"
})
```

---

## Tab Backgrounds

```lua
MainTab:SetTabImage("rbxassetid://0", 0.15)
```

0.15 is the transparency. 0 = opaque, 1 = invisible. Play around with it.

---

## Notifications

```lua
Window:Notify("NaJa UI", "Loaded Successfully", 5)
```

Title, message, duration in seconds. They stack properly and don't overlap each other like some libraries do.

---

## Methods You Might Actually Use

Most elements have `:Set(text)` or `:Update(state)`. Dropdowns have `:Add(item)` and `:Clear()`. Sliders have `:Set(value)`. Images have `:SetImage(id)` and `:SetHeight(px)`. Profile cards have banner/pfp/name/description setters.

I won't list every single one because you can figure it out from the pattern. If an element exists, it probably has a setter.

---

## Why This Instead of [Other Library]?

Honestly? Use whatever works for your project. But if you're building something with a lot of moving parts — dynamic sections, live updating content, dropdowns that need to not suck this handles it without you writing a bunch of manual layout code.

The layout system actually responds to content changes. Sections don't break when you add 12 toggles. Dropdowns filter in real-time without lagging. It's built for scripts that do things, not just static menus.

---

## Known Realities

- It's not the lightest library ever made. It does things dynamically, which costs some performance. If you're making a 2-button script, you might be better off with something minimal.
- Glassmorphism looks cool until you put it over a busy background. Use responsibly.
- The animated text is fun but don't spam it everywhere or your UI will feel like it's having a stroke.

---

## Credits

Built by Diablo. Azurey helped with some of the architecture stuff.

If something's broken, it's probably my fault. If something works really well, Azurey probably wrote that part.
