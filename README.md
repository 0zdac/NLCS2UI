# Neverlose UI Document
This UI isn't official port to roblox from neverlose.cc.
The source code is ready for obfuscate using Luraph.

## Using Library
```lua
local NeverLose = loadstring(game:HttpGet("https://raw.githubusercontent.com/0zdac/NLCS2UI/refs/heads/main/source.luau"))()
```
For Roblox Game
```lua
local NeverLose = require(script:WaitForChild('PATH_TO_MODULE'));
```

## Creating Loader
```lua
local Loader = NeverLose.new({
	Name = "Neverlose",
	Content = "Available Products",
	Process = "Script will automatically load.",
	Default = "",
	Yield = true,
	DefaultVersion = nil,
	Versions = {
		{
			Idx = "v1",
			Name = "Version 1.0",
			Content = "Stable release",
		},
	},
	OnGetKey = function()
		-- Called when "Get Key" button is clicked
	end,
	OnRedeem = function(inputText)
		-- Return true to proceed, false + reason on failure
		if inputText == "valid-key" then
			return true
		end
		return false, "Invalid Key"
	end,
})
```
Await (Yield until login or close):
```lua
local result = Loader:Await() --> DefaultVersion, input text, or nil if closed
```
Set Status Text:
```lua
Loader:SetStatus("Authenticating...") -- Custom text
Loader:SetStatus() -- Reset to default Config.Process
```
Unload Loader:
```lua
Loader:Unload()
```
> The loader includes a built-in close button (×) in the top-right corner. Clicking it calls `:Unload()` internally and releases `:Await()` with `nil`.

## Creating Notification
```lua
local Notification = NeverLose:CreateNotification();
```
Usage:
```lua
Notification.new({
	Title = "Title",
	Content = "Content",
	Duration = 7,
})
```

## Creating Logger
```lua
local Logging = NeverLose:CreateLogger();
```
Usage:
```lua
Logging.new("crosshairs",'Hit {PLAYER_NAME} in the neck for 100 damage',15)
```
## Creating Indicator
```lua
local Indicator = NeverLose:CreateIndicator();
```
Usage:
```lua
local HitChance = Indicator.new({
	Name = "HC",
	Icon = 'crosshairs',
	Color = 'Red',
})
```
Visible:
```lua
HitChance:SetRender(<boolean>)
```
Set Color:
- Red
- Green
- White
```lua
HitChance:SetColor(<string>)
```
Edit Text:
```lua
HitChance:SetText(<string>)
```

## Creating Window
```lua
local Window = NeverLose:CreateWindow({
		Logo = NeverLose.GlobalLogo,
		Name = "Neverlose",
		Content = "Counter-Strike 2",
		Size = NeverLose.Scales.Default,
		ConfigFolder = "NeverLoseConfigs",
		Enable3DRenderer = false,
		Keybind = "Insert"
});
```
## Creating Watermark
```lua
local Watermark = window:Watermark();
```
Usage:
```lua
local pings = Watermark:AddBlock(
  "chart-four-vertical-bars" , -- Icon <string>
  "0MS", -- Default Text <string>
);
```
Edit Text:
```lua
pings:SetText(tostring(game:GetService('Players').LocalPlayer:GetNetworkPing())..'MS')
```
Set Visible:
```lua
ping:SetVisible(<boolean>)
```
Add Input Signal:
```lua
ping:Input(function()
	print("click!")
end);
```
## User Settings
```lua
Window.UserSettings
```
Example:
```lua
Window.UserSettings:AddLabel('Synchronization'):AddToggle({
	Default = true,
	Callback = function(v)
		
	end,
})
```
## Set Window Size
```lua
Window:SetSize(<UDim2>)
```
## Toggle Window
```lua
Window:ToggleInterface()
```
## 3D Menu
Make sure "Enable3DRenderer" is enabled
```lua
Window:Set3DRender(<bool>)
```
## Set Profile
Set user profile ex: username , profile , expires date
```lua
Window:SetAccount({
  Profile = <string> or nil,
  Username = <string> or nil,
  Expires = <string> or nil
})
```
### Creating Tab Label
```lua
window:AddTabLabel('AIMBOT')
```
## Creating Tab
```lua
local Tab = window:AddTab({
	Icon = 'crosshairs',
	Name = "Rage",
})
```
## Creating Section
```lua
local Section = Tab:AddSection({
	Name = "MAIN"
})
```
### Creating Label
```
Text: <string> , Warp: <boolean>
```
```lua
local Label = Section:AddLabel('Label',false);
```
### Creating ToolTip
```lua
Label:ToolTip("Long Text, Something ...");
```
### Creating Toggle
```lua
Label:AddToggle({
  Default = false,
  Flag = "MyToggle",
  Callback = function(bool)
  
  end,
})
```

### Creating Slider
```lua
Label:AddSlider({
  Default = 50,
  Min = 0,
  Max = 10,
  Type = "", -- Optional
  Rounding = 0,
  
  Nums = { -- Optional
    [0] = "Off",
    [10] = "Max",
  },
  
  Flag = "MySlider",
  Size = 125, -- Size of Slider <Pixel> (Optional)
  Callback = function(value)
  
  end,
})
```
### Creating Option
- 1 > Gear Icon
- 2 > Chevron Right Icon
```lua
Label:AddOption(<number (Optional)>)
```
Usage:
```lua
local Label = Section:AddLabel("Enabled");
Label:AddToggle({
	Default = false,
	Callback = print;
	Flag = "Ragebot",
})

local LabelOption = Label:AddOption();
LabelOption:AddLabel("Force Shoot"):AddToggle({
	Default = false,
	Callback = print,
	Flag = "FS"
})

-- LabelOption:... like section
```
### Creating Color Picker
```lua
Label:AddColorPicker({
  Default = Color3.fromRGB(255, 255, 255), -- Color 3 or Hex Code
  Flag = "MyColor",
  Callback  = function()
    
  end,
})
```
### Creating Keybind
```lua
Label:AddKeybind({
    Default = "K", -- Enum.KeyCode, String or nil
    Blacklist = {},
    Callback = function()
    end,
    Flag = "MyKeybind"
  })
```
### Creating Text Input
```lua
Label:AddTextInput({
  Default = "",
  Placeholder = "Placeholder",
  Callback = function()
  end,
  Flag = "MyText",
  Size = 100, -- Size of Textbox <Pixel> (Optional)
  Numeric = false,
})
```
### Creating Dropdown
```lua
Label:AddDropdown({
  Default = "1",
  Values = {"1","2","3","4"},
  Multi = false,
  Callback = function()
  end,
  AutoUpdate = false,
  Flag = "MySingleDropdown",
  Size = 100, -- Size of Dropdown <Pixel> (Optional)
})
```
Multiple Dropdown
```lua
Label:AddDropdown({
  Default = {
    ["1"] = true,
  },
  Values = {"1","2","3","4"},
  Multi = true,
  Callback = function()
  end,
  AutoUpdate = false,
  Flag = "MySingleDropdown",
  Size = 100, -- Size of Dropdown <Pixel> (Optional)
})
```
# Other Functions
## Get Value
Get current value of item
```lua
Element:GetValue() -> any , bool , table , something
```
## Set Value
Set value of item
```lua
Element:SetValue(<any , bool , table , something>)
```
## Set List Value
Set new item list of dropdown
```lua
Dropdown:SetValues({a,b,c,d})
```
## Accessing Flags
Get the global flags table:
```lua
NeverLose.Flags --> { ["MyToggle"] = true, ["MySlider"] = 50, ... }
```
## Available Scales
```lua
NeverLose.Scales.Small    --> UDim2.fromOffset(540, 380)
NeverLose.Scales.Mobile   --> UDim2.fromOffset(640, 385)
NeverLose.Scales.Default  --> UDim2.fromOffset(640, 480)
NeverLose.Scales.Large    --> UDim2.fromOffset(800, 600)
```
## Available Icon Names
Icons use Roblox's **BuilderIcons** font. Common examples:
```
crosshairs, gear, eye, heart, star, flame, bell, key,
shield-check, lock-closed, magnifying-glass, house,
chain-link, gift-card, chart-four-vertical-bars,
arrow-spin-clockwise, xmark, person, trophy, discord,
circle-check, triangle-exclamation, lightning-bolt
```
Use the `-bold` suffix for bold variant: `"crosshairs-bold"`

## Unload
Destroy the UI and disconnect all signals:
```lua
NeverLose:Unload()
```
> Make sure `NeverLose.UnloadEnabled = true` is set before creating the window for Unload to work.

---

# Full Usage Example
```lua
-- Load the library
local NeverLose = loadstring(game:HttpGet("https://raw.githubusercontent.com/0zdac/NLCS2UI/refs/heads/main/source.luau"))()

-- Enable unloading (must be set before creating window)
NeverLose.UnloadEnabled = true;

-- Create notification system
local Notification = NeverLose:CreateNotification();

-- Create the main window
local Window = NeverLose:CreateWindow({
	Logo = NeverLose.GlobalLogo,
	Name = "My Script",
	Content = "v1.0.0",
	Size = NeverLose.Scales.Default,
	ConfigFolder = "MyScriptConfigs",
	Enable3DRenderer = false,
	Keybind = "Insert"
});

-- Set user profile
Window:SetAccount({
	Username = game.Players.LocalPlayer.DisplayName,
	Expires = "Lifetime",
});

-- Create watermark
local Watermark = Window:Watermark();
local pingBlock = Watermark:AddBlock("chart-four-vertical-bars", "0MS");

-- Add tab label + tab
Window:AddTabLabel('COMBAT');
local RageTab = Window:AddTab({
	Icon = 'crosshairs',
	Name = "Rage",
});

-- Create sections
local MainSection = RageTab:AddSection({ Name = "MAIN" });

-- Toggle
MainSection:AddLabel('Enabled'):AddToggle({
	Default = false,
	Flag = "RagebotEnabled",
	Callback = function(value)
		Notification.new({
			Title = "Ragebot",
			Content = value and "Enabled" or "Disabled",
			Duration = 3,
		});
	end,
});

-- Slider
MainSection:AddLabel('Hit Chance'):AddSlider({
	Default = 75,
	Min = 0,
	Max = 100,
	Type = "%%",
	Rounding = 0,
	Nums = {
		[0] = "Off",
		[100] = "Max",
	},
	Flag = "HitChance",
	Callback = function(value) end,
});

-- Dropdown
MainSection:AddLabel('Target'):AddDropdown({
	Default = "Head",
	Values = { "Head", "Torso", "Limbs", "Auto" },
	Multi = false,
	Flag = "TargetHitbox",
	Callback = function(value) end,
});

-- Keybind
MainSection:AddLabel('Panic Key'):AddKeybind({
	Default = "P",
	Flag = "PanicKey",
	Callback = function()
		NeverLose:Unload();
	end,
});

-- Color Picker
MainSection:AddLabel('ESP Color'):AddColorPicker({
	Default = Color3.fromRGB(78, 127, 252),
	Flag = "ESPColor",
	Callback = function(color) end,
});

-- Text Input
MainSection:AddLabel('Webhook URL'):AddTextInput({
	Default = "",
	Placeholder = "https://discord.com/api/webhooks/...",
	Flag = "WebhookURL",
	Size = 200,
	Callback = function(text) end,
});

-- Label with option (sub-menu)
local AdvLabel = MainSection:AddLabel('Advanced');
AdvLabel:AddToggle({
	Default = false,
	Flag = "AdvancedMode",
	Callback = function() end,
});
AdvLabel:ToolTip('Enable advanced targeting options');

local AdvOption = AdvLabel:AddOption();
AdvOption:AddLabel('Force Shoot'):AddToggle({
	Default = false,
	Flag = "ForceShoot",
	Callback = function() end,
});
AdvOption:AddLabel('Silent Aim'):AddToggle({
	Default = true,
	Flag = "SilentAim",
	Callback = function() end,
});

-- User Settings (built-in settings tab)
Window.UserSettings:AddLabel('Auto Save'):AddToggle({
	Default = true,
	Callback = function(v) end,
});

-- Update watermark ping
task.spawn(function()
	while task.wait(1) do
		local ping = math.round(game.Players.LocalPlayer:GetNetworkPing() * 1000);
		pingBlock:SetText(tostring(ping) .. "MS");
	end;
end);

-- Access flags anywhere
print(NeverLose.Flags["RagebotEnabled"]) --> true/false
print(NeverLose.Flags["HitChance"])      --> 75
print(NeverLose.Flags["TargetHitbox"])   --> "Head"
```
