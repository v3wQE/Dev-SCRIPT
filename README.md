 local function callback(Text)
 if Text == "Button1 text" then
  print ("Answer")
elseif Text == ("Button2 text") then
 print ("Answer2")
 end
end

local NotificationBindable = Instance.new("BindableFunction")
NotificationBindable.OnInvoke = callback
--
game.StarterGui:SetCore("SendNotification",  {
 Title = "v3w#9205";
 Text = "I Hope You Enjoin :)";
 Icon = "";
 Duration = 5;
 Callback = NotificationBindable;
})

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Hub For Devs", "Synapse")

local Tab = Window:NewTab("Main")
local Section = Tab:NewSection("Main")
Section:NewButton("CopyYouPosition", "", function()
setclipboard(tostring(game.Players.LocalPlayer.Character.HumanoidRootPart.Position))
end)

Section:NewButton("CopyTpCFrameScript", "", function()
setclipboard("game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new()")
toclipboard("game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new()")
end)

local speed = Window:NewTab("CFrameSpeed")
local rs = speed:NewSection("CFrame Speed")
rs:NewButton("CFrame Guns FIX", "ButtonInfo", function()
    for _, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
        if v:IsA("Script") and v.Name ~= "Health" and v.Name ~= "Sound" and v:FindFirstChild("LocalScript") then
            v:Destroy()
        end
    end
    game.Players.LocalPlayer.CharacterAdded:Connect(function(char)
        repeat
            wait()
        until game.Players.LocalPlayer.Character
        char.ChildAdded:Connect(function(child)
            if child:IsA("Script") then 
                wait(0.1)
                if child:FindFirstChild("LocalScript") then
                    child.LocalScript:FireServer()
                end
            end
        end)
    end)
end)
rs:NewButton("CFrame Speed (Z)", "ButtonInfo", function()
        repeat
        wait()
    until game:IsLoaded()
    local L_134_ = game:service('Players')
    local L_135_ = L_134_.LocalPlayer
    repeat
        wait()
    until L_135_.Character
    local L_136_ = game:service('UserInputService')
    local L_137_ = game:service('RunService')
    getgenv().Multiplier = 0.5
    local L_138_ = true
    local L_139_
    L_136_.InputBegan:connect(function(L_140_arg0)
        if L_140_arg0.KeyCode == Enum.KeyCode.LeftBracket then
            Multiplier = Multiplier + 0.01
            print(Multiplier)
            wait(0.2)
            while L_136_:IsKeyDown(Enum.KeyCode.LeftBracket) do
                wait()
                Multiplier = Multiplier + 0.01
                print(Multiplier)
            end
        end
        if L_140_arg0.KeyCode == Enum.KeyCode.RightBracket then
            Multiplier = Multiplier - 0.01
            print(Multiplier)
            wait(0.2)
            while L_136_:IsKeyDown(Enum.KeyCode.RightBracket) do
                wait()
                Multiplier = Multiplier - 0.01
                print(Multiplier)
            end
        end
        if L_140_arg0.KeyCode == Enum.KeyCode.Z then
            L_138_ = not L_138_
            if L_138_ == true then
                repeat
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.Humanoid.MoveDirection * Multiplier
                    game:GetService("RunService").Stepped:wait()
                until L_138_ == false
            end
        end
    end)
end)
rs:NewSlider("CFrame Speed ", "SliderInfo", 5, 0, function(s) -- 500 (MaxValue) | 0 (MinValue)
    getgenv().Multiplier = s
end)

local Tab = Window:NewTab("Character")
local Section = Tab:NewSection("Character")

Section:NewButton("HeadlessAndKorblox", "Enjoin My Script:)", function()
    local L_393_ = game.Players.LocalPlayer.Character
    local L_394_ = L_393_:WaitForChild("Head")
    local L_395_ = L_394_:WaitForChild("face")
    L_395_.Transparency = 1 --Texture = "rbxassetid://209712379"
    L_394_.Transparency = 1
    local L_396_ = game.Players.LocalPlayer.Character
    local L_397_ = game.Players.LocalPlayer.Character
    local L_398_ = L_396_.Head
    local L_399_ = L_398_.face
    local L_400_ = L_397_.RightFoot
    local L_401_ = L_397_.RightLowerLeg
    local L_402_ = L_397_.RightUpperLeg
    local L_403_ = L_397_.LeftFoot
    local L_404_ = L_397_.LeftLowerLeg
    local L_405_ = L_397_.LeftUpperLeg
    L_400_.MeshId = "http://www.roblox.com/asset/?id=902942093"
    L_401_.MeshId = "http://www.roblox.com/asset/?id=902942093"
    L_402_.MeshId = "http://www.roblox.com/asset/?id=902942096"
    L_402_.TextureID = "http://roblox.com/asset/?id=902843398"
    L_400_.Transparency = 1
    L_401_.Transparency = 1
end)

Section:NewSlider("WalkSpeed", "SliderInfo", 500, 0, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)

Section:NewSlider("JumpPower", "SliderInfo", 500, 0, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
end)

Section:NewButton("Reset", "", function()
game.Players.LocalPlayer.Character.Humanoid.Health = 0
end)

Section:NewButton("InfinteJump", "", function()
local Player = game:GetService'Players'.LocalPlayer;
local UIS = game:GetService'UserInputService';

_G.JumpHeight = 50;

function Action(Object, Function) if Object ~= nil then Function(Object); end end

UIS.InputBegan:connect(function(UserInput)
    if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.Space then
        Action(Player.Character.Humanoid, function(self)
            if self:GetState() == Enum.HumanoidStateType.Jumping or self:GetState() == Enum.HumanoidStateType.Freefall then
                Action(self.Parent.HumanoidRootPart, function(self)
                    self.Velocity = Vector3.new(0, _G.JumpHeight, 0);
                end)
            end
        end)
    end
end)
end)

Section:NewButton("FlyGui", "", function()local FlyGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextButton = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")

FlyGui.Name = "FlyGui"
FlyGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

Frame.Parent = FlyGui
Frame.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.0685602352, 0, 0.168769717, 0)
Frame.Size = UDim2.new(0.264544547, 0, 0.100000024, 0)

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.fromRGB(66, 66, 66)
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.06324628, 0, 0.400667697, 0)
TextButton.Size = UDim2.new(0.871157169, 0, 0.495614201, 0)
TextButton.Font = Enum.Font.ArialBold
TextButton.Text = "Fly"
TextButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton.TextScaled = true
TextButton.TextSize = 14.000
TextButton.TextStrokeTransparency = 0.000
TextButton.TextWrapped = true

local function NQWSTGE_fake_script() -- Frame.Fly 
	local script = Instance.new('LocalScript', Frame)

	local plr = script.Parent.Parent.Parent.Parent
	repeat wait() until plr and plr.Character and plr.Character:findFirstChild("HumanoidRootPart") and plr.Character:findFirstChild("Humanoid") 
	local mouse = game.Players.LocalPlayer:GetMouse()  
	repeat wait() until mouse
	
	local torso = plr.Character.HumanoidRootPart 
	local flying = false
	local deb = true 
	local ctrl = {f = 0, b = 0, l = 0, r = 0} 
	local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
	local maxspeed = 1000 
	local speed = 50
	function Fly() 
	local bg = Instance.new("BodyGyro", torso) 
	bg.P = 9e4 
	bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
	bg.cframe = torso.CFrame 
	local bv = Instance.new("BodyVelocity", torso) 
	bv.velocity = Vector3.new(0,0.1,0) 
	bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
	repeat wait() 
	plr.Character.Humanoid.PlatformStand = true 
	if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then 
	speed = speed+.5+(speed/maxspeed) 
	if speed > maxspeed then 
	speed = maxspeed 
	end 
	elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then 
	speed = speed-1 
	if speed < 0 then 
					speed = 0
				else
					speed = 50
	end 
	end 
	if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then 
	bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
	lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
	elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then 
	bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
	else 
	bv.velocity = Vector3.new(0,0.1,0) 
	end 
	bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
	until not flying 
	ctrl = {f = 0, b = 0, l = 0, r = 0} 
	lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		
	bg:Destroy() 
	bv:Destroy() 
		plr.Character.Humanoid.PlatformStand = false 
		speed = 50
	end 
	
	mouse.KeyDown:connect(function(key) 
	if key:lower() == "e" then 
			if flying then flying = false 
				speed = 50
	else 
	flying = true 
	Fly()
	
	end 
	elseif key:lower() == "w" then 
	ctrl.f = 1 
	elseif key:lower() == "s" then 
	ctrl.b = -1 
	elseif key:lower() == "a" then 
	ctrl.l = -1 
	elseif key:lower() == "d" then 
	ctrl.r = 1 
	end 
	end) 
	mouse.KeyUp:connect(function(key) 
	if key:lower() == "w" then 
	ctrl.f = 0 
	elseif key:lower() == "s" then 
	ctrl.b = 0 
	elseif key:lower() == "a" then 
	ctrl.l = 0 
	elseif key:lower() == "d" then 
	ctrl.r = 0 
	end 
	end)
	
	plr.Character.Humanoid.StateChanged:Connect(function(o,n)
		if n == Enum.HumanoidStateType.Running then
			ctrl.f = 1
		else
			ctrl.f = 0
		end
	
	end)
	script.Parent.TextButton.MouseButton1Click:Connect(function()
		if flying then
			flying = false
			speed = 50
		else
			flying = true
			Fly()
		end
	end)
	
end
coroutine.wrap(NQWSTGE_fake_script)()
local function RAQA_fake_script() -- Frame.Buttons 
	local script = Instance.new('LocalScript', Frame)

	local Trigger = script.Parent.MiniTrext
	local IsMini = false
	function CreateTween(Instance,Style,Direction,Time,table,RepeatCount,CanRepeat,Delay)
		local ts = game:GetService("TweenService")
		local TweenInfo = TweenInfo.new(Time,Style,Direction,RepeatCount,CanRepeat,Delay)
		local Tween = ts:Create(Instance,TweenInfo,table)
		repeat wait() until Tween ~= nil
		return Tween
		
	end
	Trigger.MouseButton1Click:Connect(function()
		if IsMini then
			CreateTween(script.Parent,Enum.EasingStyle.Quad,Enum.EasingDirection.Out,0.5,{Size = UDim2.new(0.265, 0,0.1, 0)},0,false,0.1):Play()
			IsMini = false
			Trigger.Text = "-"
		else
			CreateTween(script.Parent,Enum.EasingStyle.Quad,Enum.EasingDirection.Out,0.5,{Size = UDim2.new(0.265, 0,0.042, 0)},0,false,0.1):Play()
			IsMini = true
			Trigger.Text = "+"
		end
	end)
	script.Parent.Delete.MouseButton1Click:Connect(function()
		script.Parent.Parent:Destroy()
	end)
end
coroutine.wrap(RAQA_fake_script)()
local function TKVUMP_fake_script() -- Frame.Drag Gui 
	local script = Instance.new('LocalScript', Frame)

	local UserInputService = game:GetService("UserInputService")
	
	local gui = script.Parent
	
	local dragging
	local dragInput
	local dragStart
	local startPos
	
	local function update(input)
		local delta = input.Position - dragStart
		gui.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
	end
	
	gui.InputBegan:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
			dragging = true
			dragStart = input.Position
			startPos = gui.Position
			
			input.Changed:Connect(function()
				if input.UserInputState == Enum.UserInputState.End then
					dragging = false
				end
			end)
		end
	end)
	
	gui.InputChanged:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
			dragInput = input
		end
	end)
	
	UserInputService.InputChanged:Connect(function(input)
		if input == dragInput and dragging then
			update(input)
		end
	end)
end
coroutine.wrap(TKVUMP_fake_script)()
end)

local Tab = Window:NewTab("Misc")
local Section = Tab:NewSection("Misc")
Section:NewButton("Rejoin", "Very OP Enjoin:)", function()
repeat
    wait()  
until game:IsLoaded() 
game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId,game.JobId)
end)

local Tab = Window:NewTab("Executor")
local Section = Tab:NewSection("Executor")
Section:NewButton("Executor", "Very OP Enjoin:)", function()
      loadstring(game:HttpGet("https://raw.githubusercontent.com/v3wQE/Executor/main/README.md"))();
end)

local Tab = Window:NewTab("Toggle")
local Section = Tab:NewSection("Toggle")
Section:NewKeybind("UiToggle", "KeybindInfo", Enum.KeyCode.RightControl, function()
	Library:ToggleUI()
end)
