<img width="805" height="545" alt="Screenshot 2026-01-21 234216" src="https://github.com/user-attachments/assets/fafedffd-5762-498e-87e3-2deec7718a7b" />

# Neverlose
Neverlose Recode UI for Roblox

## Icons?
- Press Win + R
- Enter `%LOCALAPPDATA%\Roblox\Versions\`
- Path to `{ROBLOX VERSION}\ExtraContent\LuaPackages\Packages\_Index\BuilderIcons\BuilderIcons\Font`
- Drop `BuilderIcons-Filled.ttf` to https://fontdrop.info/#/?darkmode=true

done

<img width="528" height="335" alt="image" src="https://github.com/user-attachments/assets/87edd6cc-46fd-46ff-8f83-32c082113d25" />

## Example:
```lua
-- U CAN USE TS IN UR ROBLOX GAME --

local NeverLose = loadstring(game:HttpGet("https://raw.githubusercontent.com/4lpaca-pin/NeverLose/refs/heads/main/source.luau"))() --require(script:WaitForChild('ModuleScript'));

local Notification = NeverLose:CreateNotification();
local Logging = NeverLose:CreateLogger();
local Indicator = NeverLose:CreateIndicator();
local window = NeverLose:CreateWindow({
	Logo = NeverLose.GlobalLogo,
	Name = "Neverlose",
	Content = "Counter-Strike 2",
	Size = NeverLose.Scales.Default,
	ConfigFolder = "NeverLoseConfigs",
	Enable3DRenderer = false,
	Keybind = "Insert"
});

local Watermark = window:Watermark();

local HC = Indicator.new({
	Name = "HC",
	Icon = 'crosshairs',
	Color = 'Red',
})

window:AddTabLabel('AIMBOT')

local ping = Watermark:AddBlock("chart-four-vertical-bars" , "0MS");
local UITogg = Watermark:AddBlock("cube-vertexes" , "Neverlose");

UITogg:Input(function()
	window:ToggleInterface();
end);

task.spawn(function()
	while true do task.wait(1)
		ping:SetText(tostring(math.random(30,90))..'MS')
	end
end)

local Rage = window:AddTab({
	Icon = 'crosshairs',
	Name = "Rage",
})

local Legit = window:AddTab({
	Icon = 'mouse-scrollwheel',
	Name = "Legit"
})
 
local Raging = Rage:AddSection({
	Name = "MAIN"
})

local Selection = Rage:AddSection({
	Name = "SELECTION",
	Position = 'left'
})

local Other = Rage:AddSection({
	
	Name = "OTHER",
	Position = 'right'
})

local AntiAim = Rage:AddSection({
	Name = "ANTI-AIM",
	Position = 'right'
})


-- <STRING : TEXT, BOOLEAN : WARP> --
Raging:AddLabel('Ts so skbidi\nfr noi cap',true)

local EnabledRage = Raging:AddLabel('Enabled')
local SlientAim = Raging:AddLabel('Silent Aim')

EnabledRage:ToolTip("Dynamically adjusts grenade throw angles to counteract\nmovement velocity, allowing precise straight-line throws\neven while strafing")
EnabledRage:AddToggle({
	Default = false,
	Callback = print;
	Flag = "Ragebot",
})

EnabledRage:AddOption():AddLabel("Force Shoot"):AddToggle({
	Default = false,
	Callback = print,
	Flag = "FS"
})

SlientAim:AddToggle({
	Default = false,
	Callback = print,
	Flag = "SLIENTAIM",
})

local opt = SlientAim:AddOption();
opt:AddLabel('Perfect Silent-Aim'):AddToggle({
	Default = false,
	Callback = print,
	Flag = "HideShot",
})

opt:AddLabel('Perfect Silent-Aim'):AddToggle({
	Default = false,
	Callback = print,
	Flag = "HideShot2",
})

Raging:AddLabel('Automatic Fire'):AddToggle({
	Default = false,
	Flag = "AutoFire",
})

Raging:AddLabel('Aim Through Walls'):AddToggle({
	Default = false,
	Flag = "AWALLS",
})

Raging:AddLabel('Field of View'):AddSlider({
	Min = 0,
	Max = 2600,
	Rounding = 1,
	Default = 100,
	Type = "Lv",
	Size = 100,
	Callback = print,
	Flag = "fov",
})

Selection:AddLabel("Target"):AddDropdown({
	Default = 'Hightest Damage',
	Values = {
		'Hightest Damage',
		'Automatic',
		'Lowest Damage'
	},
	Callback = print,
	Flag = "target_box",
})

Selection:AddLabel('Hitboxes'):AddDropdown({
	Default = {'Head'},
	Multi = true,
	Values = {
		'Head',
		'Body',
		'Arms',
		'Legs'
	},
	Flag = "hitboxes",
	Callback = print
})

local Multipoint = Selection:AddLabel('Multipoint')

Multipoint:AddOption():AddLabel('Multipoint'):AddSlider({
	Min = 0,
	Max = 100,
	Default = 75,
	Flag = "multipoint",
	Callback = print
})

Multipoint:AddDropdown({
	Default = {'Head'},
	Multi = true,
	Values = {
		'Head',
		'Body',
		'Arms',
		'Legs'
	},
	Flag = "hitboxmuklti",
	Callback = print
})

local hc = Selection:AddLabel('Hit Chance')

hc:AddSlider({
	Min = 0,
	Max = 100,
	Type = "%",
	Nums = {
		[0] = 'Auto',
	},
	Flag = "hc",
	Size = 95,
	Default = 50,
})

hc:AddOption():AddLabel('Something'):AddToggle({
	Default = false
})

local md = Selection:AddLabel('Min Damage')

md:AddSlider({
	Min = 0,
	Max = 100,
	Nums = {
		[0] = 'Auto',
	},
	Flag = "md",
	Size = 95,
	Default = 15,
})

md:AddOption():AddLabel('Something'):AddToggle({
	Default = false
})

local qs = Selection:AddLabel('Quick Stop')

qs:AddToggle({
	Default = false,
	Flag = "astop",
	Callback = print
})

qs:AddOption():AddLabel('Auto Stop'):AddDropdown({
	Default = {'Early'},
	Multi = true,
	Flag = "astop_module",
	Values = {'Early','In Air','Between Shot' , 'Force Accurate'},
	Callback = print
})

Selection:AddLabel('Quick Scope'):AddToggle({
	Default = false,
	Flag = "ascope",
	Callback = print
})

Other:AddLabel('History'):AddDropdown({
	Default = 'High',
	Values = {'Minimum','Low','High','Maximum'},
	Flag = "backtrack",
	Callback = print
})

Other:AddLabel('Delay Shot'):AddToggle({
	Default = false,
	Flag = "delayshoot",
	Callback = print
})

Other:AddLabel('Remove Recoil'):AddToggle({
	Default = false,
	Flag = "removerecoil",
	Callback = print
})


Other:AddLabel('Remove Spread'):AddToggle({
	Default = false,
	Flag = "removespread",
	Callback = print
})


Other:AddLabel('Duck Peek Assist'):AddToggle({
	Default = false,
	Callback = print
})


local qpa = Other:AddLabel('Quick Peek Assist');
qpa:AddToggle({
	Default = false,
	Flag = "qpa",
	Callback = print
})

qpa:AddOption():AddLabel('Something tung tung')

Other:AddLabel('Double Tap'):AddToggle({
	Default = false,
	Callback = print,
	Flag = "dt",
})

local aa_enable = AntiAim:AddLabel('Enabled');
aa_enable:AddToggle({
	Default = false,
	Flag = "aa",
	Callback = print
})

aa_enable:AddOption():AddLabel('Resolvers tung tung'):AddToggle({
	Default = false,
	Callback = print
})

AntiAim:AddLabel('Pitch'):AddDropdown({
	Default = 'Down',
	Flag = "pitch",
	Values = {'Down','Center','Up','Fake Up','Fake Down'}
})

AntiAim:AddLabel('Yaw'):AddDropdown({
	Default = 'Backwards',
	Flag = "yaw",
	Values = {'Backwards','Left','Right','Forwards'}
})

AntiAim:AddLabel('Freestanding'):AddToggle({
	Default = false,
	Flag = "freestand",
	Callback = print
})

AntiAim:AddLabel('Mouse Override'):AddToggle({
	Default = false,
	Flag = "mouse_override",
	Callback = print
})

---------- Menu Configuration ------------
window.UserSettings:AddLabel("Menu Keybind"):AddKeybind({
	Default = 'Insert',
	Callback = function(v)
		window.Keybind = v;
		
		Logging.new("ps4-touchpad",'Changed ui keybind to '..tostring(v),5)
	end,
})

window.UserSettings:AddLabel('Menu Scale'):AddDropdown({
	Default = "Default",
	Values = {"Default",'Large','Mobile','Small'},
	Callback = function(v)
		window:SetSize(NeverLose.Scales[v]);
		
		Logging.new("crop",'Changed ui size to '..tostring(v),5)
	end,
})

window.UserSettings:AddLabel('3D Menu'):AddToggle({
	Default = false,
	Callback = function(v)
		window:Set3DRender(v);
	end,
})

window.UserSettings:AddButton({
	Icon = 'discord',
	Name = 'Discord',
	Callback = function()
		print('invite')
		
		Logging.new("discord",'Copied discord invite link',5)
	end,
})

Notification.new({
	Title = "Notification",
	Content = "This is Neverlose Notification",
	Duration = 5,
})

task.wait(1)
Notification.new({
	Title = "Neverlose",
	Content = "Initialization in progress",
	Duration = 7,
})

Logging.new("crosshairs",'Hit thatguy in the neck for 100 damage',15)
task.wait(2)
Logging.new("crosshairs-slash",'Missed shot due to prediction error & YOUR NN',15)

HC:SetRender(true);

while true do task.wait(3)
	Watermark:SetRender(true);
	
	HC:SetColor('Red')
	HC:SetText("FL")
	task.wait(3);
	Watermark:SetRender(false);
	HC:SetColor('Green');
	HC:SetText("AUTO")
	task.wait(3)
	Watermark:SetRender(true);
	HC:SetColor('White')
	HC:SetText("HC")
	task.wait(1)
	Watermark:SetRender(false);
	HC:SetRender(false);
	task.wait(1)
	HC:SetRender(true);
end
```

- 4lpacaLoL
