require(game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game).caption("Wait font Loading Done",true)
wait()
local shut = game.Players.LocalPlayer.PlayerGui.MainUI.MainFrame.IntroText
local intro = shut:Clone()
intro.Parent = game.Players.LocalPlayer.PlayerGui.MainUI
intro.Name = "IntroTextPleaseThankYou"
intro.Visible = true
intro.Text = "Extremely Chaostic Regime Mode v6.514"
intro.TextTransparency = 0
local underline = UDim2.new(1.1, 0, 0.015, 6)
game.TweenService:Create(intro.Underline, TweenInfo.new(3), {Size = underline}):Play()
wait(7)
game.TweenService:Create(intro.Underline, TweenInfo.new(1.3), {Size = UDim2.new(0.95, 0, 0.015, 6)}):Play()
wait(1)
game.TweenService:Create(intro.Underline, TweenInfo.new(2), {ImageTransparency = 1}):Play()
game.TweenService:Create(intro, TweenInfo.new(2), {TextTransparency = 1}):Play()
game.TweenService:Create(intro.Underline, TweenInfo.new(7), {Size = UDim2.new(0, 0, 0.015, 6)}):Play()
wait(2.3)
intro.Visible = false
wait(9)
intro:Destroy()

require(game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game).caption("Loading Done",true)

--DoorSound
coroutine.wrap(function()
while true do
game.ReplicatedStorage.Entities.Screech.Top.Eyes.Color = Color3.fromRGB(255, 0, 0)
game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game.RemoteListener.Modules.Screech.Caught.SoundId = "rbxassetid://537141778"
game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game.RemoteListener.Modules.Screech.Caught.PlaybackSpeed = 1.6
game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game.RemoteListener.Modules.Screech.Attack.SoundId = "rbxassetid://6754147732"
wait()
game.Workspace.Ambience_Dark.SoundId = "rbxassetid://8132494511"
game.Workspace.Ambience_Dark.PlaybackSpeed = 1
end
end)()
--

--Ambience
coroutine.wrap(function()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Connect(function()
if game.Workspace:FindFirstChild("SeekMovingClone") then
wait(0.0005)
game.Workspace.SeekMovingClone.SeekMusic.SoundId = "rbxassetid://1837892736"
game.Workspace.SeekMovingClone.SeekMusic.Volume = "0.7"
game.Workspace.SeekMoving.Ambience.SoundId = "rbxassetid://1837892736"
game.Workspace.SeekMoving.Ambience.Volume = "0.7"
end
end)
end)()
--
 
-- New Seek music and animation loader
coroutine.wrap(function()
wait()
    game.ReplicatedStorage.GameData.LatestRoom.Changed:Connect(function()
        wait(0.0005)
        if game.Workspace:FindFirstChild("SeekMovingNewClone") then

            function ReplaceAudGit(GithubSnd, SoundName)
                local url = GithubSnd
                if not isfile(SoundName .. ".mp3") then
                    writefile(SoundName .. ".mp3", game:HttpGet(url))
                end
                return (getcustomasset or getsynasset)(SoundName .. ".mp3")
            end

            local a = game.Workspace.SeekMovingNewClone
            a.SeekMusic.SoundId = ReplaceAudGit("https://github.com/huyhoanphuc/hgss/blob/main/km_20240919_720p_12f_20240919_022413.mp3?raw=true", "SeekMusickNewMm")
        end
    end)
end)()

-- NEW SEEK 
game.ReplicatedStorage.GameData.LatestRoom.Changed:Connect(function() 
    wait(3.5) 
    if not workspace:FindFirstChild("SeekMovingNewClone") then 
        return  
    end 
    local RealSeek = workspace:FindFirstChild("SeekMovingNewClone") 
    local RealSeekRig = RealSeek:FindFirstChild("SeekRig") 
    local SeekNew = game:GetObjects("rbxassetid://16893141009")[1]  
    SeekNew.Name = "seek2" 

    for _, v in pairs(SeekNew.Figure:GetChildren()) do 
        if v:IsA("Sound") then 
            v:Stop() 
        end 
    end 

    RealSeekRig.Head.Eye:Destroy() 
    RealSeekRig.Head.Black:Destroy() 
    SeekNew.Parent = workspace 
    local SeekRig = SeekNew:FindFirstChild("SeekRig") 
    SeekRig:FindFirstChild("Root").Anchored = true 

    spawn(function() 
        while game:GetService("RunService").Heartbeat:Wait() and RealSeek do 
            if RealSeekRig:FindFirstChild("Root") then 
                SeekRig:FindFirstChild("Root").CFrame = RealSeekRig:FindFirstChild("Root").CFrame 
            end 
            for _, v in pairs(RealSeek.Figure:GetChildren()) do 
                RealSeek.Figure.Footsteps:Stop() 
                RealSeek.Figure.FootstepsFar:Stop() 
            end 
            for _, v in pairs(RealSeekRig:GetChildren()) do 
                if v:IsA("BasePart") then 
                    v.Transparency = 1 
                    
                    local sound = a.Ambience

            if sound:IsA("Sound") then
                sound.Played:Connect(function()
                    print("YEEEEE WORKING!!!!") 
                    local model = workspace:WaitForChild("seek2")
                    local seekRig = model:WaitForChild("SeekRig")
                    local animationController = seekRig:FindFirstChildOfClass("AnimationController")

                    if animationController then
                        local anim = seekRig:FindFirstChild("AnimRaise")
                        
                        if anim and anim:IsA("Animation") then
                            local animationTrack = animationController:LoadAnimation(anim)
                            animationTrack:Play()
                        else
                            warn("AnimRaise not found or is not an animation.")
                        end
                    else
                        warn("AnimationController not found in SeekRig.")
                    end
                    
                    wait(8.20)

                    local model = workspace:WaitForChild("seek2")
                    local seekRig = model:WaitForChild("SeekRig")
                    local animationController = seekRig:FindFirstChildOfClass("AnimationController")

                    if animationController then
                        local anim = seekRig:FindFirstChild("AnimRun")
                        
                        if anim and anim:IsA("Animation") then
                            local animationTrack = animationController:LoadAnimation(anim)
                            animationTrack:Play()
                        else
                            warn("AnimRun not found or is not an animation.")
                        end
                    else
                        warn("AnimationController not found in SeekRig.")
                    end
                end)
            else
                warn("Sound not found or is not an instance of Sound.")
            end
                end 
            end 
        end 
    end)
end)

--Ambiencea
coroutine.wrap(function()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Connect(function()
wait(0.0005)
game.Workspace.CurrentRooms["50"].FigureSetup.Ambience.SoundId = "rbxassetid://0"
game.Workspace.CurrentRooms["50"].FigureSetup.Ambience.Volume = "0.3"
game.Workspace.CurrentRooms["50"].FigureSetup.AmbienceEnd.SoundId = "rbxassetid://4890185640"
game.Workspace.CurrentRooms["50"].FigureSetup.AmbienceEnd.Volume = "0.5"
end)
end)()
--

pcall(function()
spawn(function()
	while wait() do
	local currentroomnumber = game:GetService("ReplicatedStorage").GameData.LatestRoom.Value
		if workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door") ~= nil then
		 if workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door"):FindFirstChild("Door") ~= nil then
			workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door"):FindFirstChild("Door").Material = Enum.Material.DiamondPlate
			workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door"):FindFirstChild("Door").Color = Color3.new(0.341176, 0.341176, 0.341176)
		    end
		end
	end
end)
spawn(function()
	while wait() do
	local currentroomnumber = game:GetService("ReplicatedStorage").GameData.LatestRoom.Value
		if workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door") ~= nil then
		 if workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door"):FindFirstChild("Door") ~= nil then
		 if workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door"):FindFirstChild("Door"):FindFirstChild("Sign") ~= nil then
		 workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door").Sign:Destroy()
		 workspace["CurrentRooms"][currentroomnumber]:FindFirstChild("Door"):FindFirstChild("Door"):FindFirstChild("Sign"):Destroy()
                end
		    end
		end
	end
end)
end)
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.Open.SoundId = "rbxassetid://3908308607"
        workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.Unlock.SoundId = "rbxassetid://3908308607"
        workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.SlamOpen.SoundId = "rbxassetid://3908308607"
        workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.SlamOpen.TimePosition = 2
-- doors
coroutine.wrap(function()
    while true do
        wait(0.0005)
        game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
        wait(0.0005)
        workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.Open.SoundId = "rbxassetid://3908308607"
        workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.Unlock.SoundId = "rbxassetid://3908308607"
        workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.SlamOpen.SoundId = "rbxassetid://3908308607"
        workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Door.Door.SlamOpen.TimePosition = 2
    end
end)()

-- doors 2
coroutine.wrap(function()
    while true do
        wait(0.0005)
        game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
        wait(0.0005)
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Open.SoundId = "rbxassetid://3908308607"
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Open.SoundId = "rbxassetid://3908308607"
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Open.SoundId = "rbxassetid://3908308607"
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Open.SoundId = "rbxassetid://3908308607"
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Unlock.SoundId = "rbxassetid://3908308607"
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Unlock.SoundId = "rbxassetid://3908308607"
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Unlock.SoundId = "rbxassetid://3908308607"
workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value].Parts.DoorNormal.Door.Unlock.SoundId = "rbxassetid://3908308607"
    end
end)()
wait(2)
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()

-- current candle
loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Functions.lua"))()
LoadCustomInstance("rbxassetid://15717047029").Parent = game:GetService("Players").LocalPlayer.Backpack

-- echo sound
game.SoundService.AmbientReverb = "ConcertHall"
--

--ambient fog and horror sound
local Workspace = game:GetService("Workspace")
local Lighting = game:GetService("Lighting")
local SoundService = game:GetService("SoundService")
--

-- new the lights bulb sounds
game.ReplicatedStorage.Sounds.BulbCharge.SoundId = "rbxassetid://9125973034"
game.ReplicatedStorage.Sounds.BulbZap.SoundId = "rbxassetid://4288784832"
game.ReplicatedStorage.Sounds.BulbZap.Volume = 2
game.ReplicatedStorage.Sounds.BulbBreak.SoundId = "rbxassetid://260496290"
--

--Set up horror sound
local horrorSound = Instance.new("Sound", Workspace)
horrorSound.SoundId = "rbxassetid://1846999385" -- replace with your own sound id
horrorSound.Volume = 0.4
horrorSound.Looped = true

--Play the sound
horrorSound:Play()
--

--Shocker
coroutine.wrap(function()
while true do
wait(math.random(20, 30))
local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local function spawnShocker()
    local shockerModel = game:GetObjects("rbxassetid://11547803978")[1]
    shockerModel.PrimaryPart = shockerModel:FindFirstChild("HumanoidRootPart") or shockerModel:FindFirstChildWhichIsA("Part")
    
    local camera = Workspace.CurrentCamera
    shockerModel:SetPrimaryPartCFrame(camera.CFrame * CFrame.new(0, 0, -7))
    shockerModel.Parent = Workspace

    local oogaBoogaaPart = shockerModel:WaitForChild("OOGA BOOGAAAA")
    local horrorScream = shockerModel:WaitForChild("OOGA BOOGAAAA"):WaitForChild("HORROR SCREAM 15")

    local lookDuration = 4
    local startTime = tick()
    local playerLookingAtShocker = true

    while playerLookingAtShocker do
        wait(0.1)

        local angle = (oogaBoogaaPart.Position - character.PrimaryPart.Position).unit
        local direction = camera.CFrame.LookVector

        if (angle:Dot(direction) > 0.9) then
            if tick() - startTime >= lookDuration then
                horrorScream:Play()
                humanoid:TakeDamage(30)
                local function GetGitSound(GithubSnd,SoundName)
				local url=GithubSnd
				if not isfile(SoundName..".mp3") then
					writefile(SoundName..".mp3", game:HttpGet(url))
				end
				local sound=Instance.new("Sound")
				sound.SoundId=(getcustomasset or getsynasset)(SoundName..".mp3")
				return sound
			end
			game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(255, 255, 255)
	game.Lighting.MainColorCorrection.Contrast = 1
	local tween = game:GetService("TweenService")
	tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(2.5), {Contrast = 0}):Play()
	local TweenService = game:GetService("TweenService")
	local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(80),{TintColor = Color3.fromRGB(255, 255, 255)})
	TW:Play()
        local ShokerJC = GetGitSound("https://github.com/huyhoanphuc/thh/blob/main/km_20240823_720p_12f_20240823_021809.mp3?raw=true","ShokerJC")
				ShokerJC.Parent = workspace
				ShokerJC.Volume = 1.3
				ShokerJC:Play()
                playerLookingAtShocker = false

                local speed = 10
                local targetPosition = character.PrimaryPart.Position

                while oogaBoogaaPart.Position.Y > targetPosition.Y do
                    local directionToPlayer = (targetPosition - oogaBoogaaPart.Position).unit
                    oogaBoogaaPart.Position = oogaBoogaaPart.Position + directionToPlayer * speed * 0.1
                    wait(0.1)
                end

                oogaBoogaaPart.CanCollide = false
                oogaBoogaaPart.Anchored = false
                wait(3)
                shockerModel:Destroy()
game:GetService("ReplicatedStorage").GameStats["Player_".. game.Players.LocalPlayer.Name].Total.DeathCause.Value = "Shocker"
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Shocker...",
    "Dont look at it or it stuns you!"
}, "Blue") -- "Blue" or "Yellow"
                break
            end
        else
            
            oogaBoogaaPart.CanCollide = false
            oogaBoogaaPart.Anchored = false
            break
        end
    end
oogaBoogaaPart.CanCollide = false
oogaBoogaaPart.Anchored = false
wait(3)
    shockerModel:Destroy()
end

spawnShocker()
end
end)()
--

--Matcher
coroutine.wrap(function()
while true do wait(60)
wait()
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
    
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Matcher",
    Model = "rbxassetid://12459977063", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 1.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = false,
    ShatterLights = true,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
wait()
if game.Workspace:FindFirstChild("Matchers") then
game.workspace.Matchers:Destroy()
end

    game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(212, 255, 0)
game.Lighting.MainColorCorrection.Contrast = 0.3
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(0.5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(0.5),{TintColor = Color3.fromRGB(255, 255, 255)})
TW:Play()
    local roast = Instance.new("Sound")
    roast.Parent = workspace
    roast.Name = "roast"
    roast.SoundId = "rbxassetid://9125936117"
    roast.Volume = 1.6
    roast.Pitch = 3
    roast:Play()
    wait(0.6)
    roast:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value]:WaitForChild("Door").ClientOpen:FireServer()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/entity-endless-doors/main/Matcher%20Jumpscare"))()
wait()
loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/entity-endless-doors/main/MatcherPlayerDead"))()
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end
end)()
--

--Blitz
coroutine.wrap(function()
while true do wait(213)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
local spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V2/Source.lua"))()

---====== Create entity ======---

local entity = spawner.Create({
	Entity = {
		Name = "Blitz",
		Asset = "https://github.com/RegularVynixu/Utilities/raw/main/Doors/Entity%20Spawner/Assets/Entities/BackdoorRush.rbxm",
		HeightOffset = 0
	},
	Lights = {
		Flicker = {
			Enabled = true,
			Duration = 1
		},
		Shatter = true,
		Repair = false
	},
	Earthquake = {
		Enabled = true
	},
	CameraShake = {
		Enabled = true,
		Range = 100,
		Values = {1.5, 20, 0.1, 1}
	},
	Movement = {
		Speed = 100,
		Delay = 2,
		Reversed = false
	},
	Rebounding = {
		Enabled = true,
		Type = "Blitz",
		Min = 1,
		Max = math.random(1, 2),
		Delay = math.random(10, 30) / 10
	},
	Damage = {
		Enabled = true,
		Range = 40,
		Amount = 125
	},
	Crucifixion = {
		Enabled = true,
		Range = 40,
		Resist = false,
		Break = true
	},
	Death = {
		Type = "Curious",
		Hints = {"Oh... Hello.", "I didn't expect to see you here.", "Let's see what you died to.", "Oh, one of my favorites.", "She said we should call that one Blitz.", "Well... I'll see you later, right? You'll come back?", "Haha... of course you will."},
		Cause = ""
	}
})

---====== Debug entity ======---

entity:SetCallback("OnRebounding", function(startOfRebound)
	-- Variables for the entity
	local entityModel = entity.Model
	local main = entityModel:WaitForChild("Main")
	local attachment = main:WaitForChild("Attachment")
	local AttachmentSwitch = main:WaitForChild("AttachmentSwitch")
	local sounds = {
		footsteps = main:WaitForChild("Footsteps"),
		playSound = main:WaitForChild("PlaySound"),
		switch = main:WaitForChild("Switch"),
		switchBack = main:WaitForChild("SwitchBack")
	}

	-- Toggle particle emitters and lights within the entityModel
	-- To switch between green & red state
	for _, c in attachment:GetChildren() do
		c.Enabled = (not startOfRebound)
	end
	for _, c in AttachmentSwitch:GetChildren() do
		c.Enabled = startOfRebound
	end

	-- Play sounds
	if startOfRebound == true then
		sounds.footsteps.PlaybackSpeed = 0.35
		sounds.playSound.PlaybackSpeed = 0.25
		sounds.switch:Play()
	else
		sounds.footsteps.PlaybackSpeed = 0.25
		sounds.playSound.PlaybackSpeed = 0.16
		sounds.switchBack:Play()
	end
end)

---====== Run entity ======---

entity:Run()
end
end
end)()
--

--AmbushKk
coroutine.wrap(function()
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()
local WarningSound = Instance.new("Sound")
                    WarningSound.Parent = workspace
                    WarningSound.SoundId = "rbxassetid://8680141474"
                    WarningSound.Volume = workspace.Ambience_Ambush.Volume
                    WarningSound:Play()
                    workspace.Ambience_Ambush:Play()
                    wait(3)
                    WarningSound:Destroy()

-- Create entity
local entity = Spawner.createEntity({
    CustomName = "laughing ambush", -- Custom name of your entity
    Model = "rbxassetid://13293983665", -- Can be GitHub file or rbxassetid
    Speed = 300, -- Percentage, 100 = default Rush speed
    DelayTime = 3, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 100,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 2.5,
        Max = 4,
        WaitTime = 2,
    },
    CamShake = {
        true, -- Enabled/Disabled
        {3.5, 900, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18384688860", -- Image1 url
            Image2 = "rbxassetid://18384701999", -- Image2 url
            Shake = true,
            Sound1 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Sound2 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"A-60 has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
end

entity.Debug.OnEntityDespawned = function()
    print("Nostalgic frikig")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    local v1 = game.Players.LocalPlayer.PlayerGui.MainUI.Jumpscare:Clone()
local jumpscary = Instance.new("ScreenGui")
jumpscary.Parent = game.Players.LocalPlayer.PlayerGui
jumpscary.IgnoreGuiInset = true
v1.Parent = jumpscary
local u2 = require(game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game)

			u2.deathtick = tick() + 10;
			game.SoundService.Main.Volume = 0;
			game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game.RemoteListener.Jumpscare_Ambush:Play();
			v1.Jumpscare_Ambush.Visible = true;
			local v72 = tick();
			local v73 = math.random(5, 30) / 100;
			local v74 = v73 + math.random(10, 60) / 100;
			local v75 = 0.2;
			for v76 = 1, 100000 do
				task.wait(0.016666666666666666);
				v1.Jumpscare_Ambush.ImageLabel.Position = UDim2.new(0.5, math.random(-15, 15), 0.5, math.random(-15, 15));
				v1.Jumpscare_Ambush.BackgroundColor3 = Color3.new(0, math.random(4, 10) / 255, math.random(0, 3) / 255);
				if v72 + v73 <= tick() then
					v1.Jumpscare_Ambush.ImageLabel.Visible = true;
					v73 = v73 + math.random(7, 44) / 100;
					game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game.RemoteListener.Jumpscare_Ambush.Pitch = math.random(35, 155) / 100;
					v1.Jumpscare_Ambush.BackgroundColor3 = Color3.new(0, math.random(4, 10) / 255, math.random(0, 3) / 255);
					v1.Jumpscare_Ambush.ImageLabel.Position = UDim2.new(0.5, math.random(-25, 25), 0.5, math.random(-25, 25));
					v75 = v75 + 0.05;
					v1.Jumpscare_Ambush.ImageLabel.Size = UDim2.new(v75, 0, v75, 0);
				end;
				if v72 + v74 <= tick() then
					break;
				end;
			end;
			game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game.RemoteListener.Jumpscare_Ambush2:Play();
			v1.Jumpscare_Ambush.ImageLabel.Visible = true;
			v1.Jumpscare_Ambush.ImageLabel:TweenSize(UDim2.new(9, 0, 9, 0), "In", "Quart", 0.3, true);
			local v77 = tick();
			for v78 = 1, 100 do
				local v79 = math.random(0, 10) / 10;
				v1.Jumpscare_Ambush.BackgroundColor3 = Color3.new(v79, math.clamp(math.random(25, 50) / 50, v79, 1), math.clamp(math.random(25, 50) / 150, v79, 1));
				game["Run Service"].RenderStepped:wait();
				if v77 + 0.3 <= tick() then
					break;
				end;
			end;
			game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game.RemoteListener.Jumpscare_Ambush:Stop();
			v1.Jumpscare_Ambush.ImageLabel.Visible = false;
			v1.Jumpscare_Ambush.BackgroundColor3 = Color3.new(0, 0, 0);
			v1.Jumpscare_Ambush.Visible = false;
               game.SoundService.Main.Volume = 1;
               jumpscary:Destroy();
			u2.deathtick = tick();
			return;
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end)() 
--

--A120
coroutine.wrap(function()
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
require(game.Players.LocalPlayer.PlayerGui.MainUI.Initiator.Main_Game).caption("A-120 Has Spawner",true)
wait(2)
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "A-120", -- Custom name of your entity
    Model = "rbxassetid://13316793516", -- Can be GitHub file or rbxassetid
    Speed = 70, -- Percentage, 100 = default Rush speed
    DelayTime = 3, -- Time before starting cycles (seconds)
    HeightOffset = 0.5,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 30,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 2,
        Max = 3,
        WaitTime = 0,
    },
    CamShake = {
        true, -- Enabled/Disabled
        {5, 30, 0.1, 1}, -- Shake values (don't change if you don't know)
        50, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18384688860", -- Image1 url
            Image2 = "rbxassetid://18384701999", -- Image2 url
            Shake = true,
            Sound1 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Sound2 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"A-60 has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")   
end

entity.Debug.OnEntityDespawned = function()
    print("Nostalgic frikig")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end)()
--

--Aml
coroutine.wrap(function()
while true do wait(89)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "A-15",
    Model = "https://github.com/Franciscolovedoorshardcoremode/EntitiesScraryMode/blob/main/a10.rbxm?raw=true", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 1.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = false,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
end

entity.Debug.OnEntityDespawned = function()
    workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value]:WaitForChild("Door").ClientOpen:FireServer()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end
end)() 
--

--abl
coroutine.wrap(function()
while true do wait(109)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "A-35", -- Custom name of your entity
    Model = "rbxassetid://13486970543", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 3, -- Time before starting cycles (seconds)
    HeightOffset = 0.5,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 60,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1.5,
        Max = 1.5,
        WaitTime = 1,
    },
    CamShake = {
        true, -- Enabled/Disabled
        {30, 30, 0.1, 1}, -- Shake values (don't ch--ge if you don't know)
        50, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18384688860", -- Image1 url
            Image2 = "rbxassetid://18384701999", -- Image2 url
            Shake = true,
            Sound1 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Sound2 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"A-60 has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")   
end

entity.Debug.OnEntityDespawned = function()
    print("Nostalgic frikig")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end
end)()
--

--Ripper
coroutine.wrap(function() 
while true do wait(111)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Ripper", -- Custom name of your entity
    Model = "rbxassetid://15989468546", -- Can be GitHub file or rbxassetid
    Speed = 500, -- Percentage, 100 = default Rush speed
    DelayTime = 8, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 100,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        true, -- Enabled/Disabled
        {15,25,0,2,1,6}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        true, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://nil", -- Image1 url
            Image2 = "rbxassetid://nil", -- Image2 url
            Shake = true,
            Sound1 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Sound2 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"A-60 has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    loadstring(game:HttpGet("https://pastefy.app/ZHMofq2t/raw"))()
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
wait(0.2)

local CameraShaker = require(game.ReplicatedStorage.CameraShaker)
local camara = game.Workspace.CurrentCamera
local camShake = CameraShaker.new(Enum.RenderPriority.Camera.Value, function(shakeCf)
 camara.CFrame = camara.CFrame * shakeCf
end)
camShake:Start()
camShake:ShakeOnce(15,25,0,2,1,6)

    local ripeend = Instance.new("Sound")
    ripeend.Parent = workspace
    ripeend.Name = "RipperEnd"
    ripeend.SoundId = "rbxassetid://1837829565"
    ripeend.Volume = 3
    ripeend.Pitch = 1
    ripeend:Play()

---====== Load achievement giver ======---
local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()

---====== Display achievement ======---
achievementGiver({
    Title = "Torn Apart",
    Desc = "Dont leave too early..",
    Reason = "Encounter Ripper.",
    Image = "rbxassetid://17702317077"
})
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
wait(0.2)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local RipeMoving = Instance.new("Sound")
    RipeMoving.SoundId = GitAud(soundlink, filename)
    RipeMoving.Parent = workspace
    RipeMoving.Volume = 3
    RipeMoving:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20Ripper%20Has%20Moving%20Sound%20(320%20kbps).mp3", 1, "RipperHasMoving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    local player = game.Players.LocalPlayer

player.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
player.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics, false)
player.Character.HumanoidRootPart.Anchored = true
local function GetGitSound(GithubSnd,SoundName)
				local url=GithubSnd
				if not isfile(SoundName..".mp3") then
					writefile(SoundName..".mp3", game:HttpGet(url))
				end
				local sound=Instance.new("Sound")
				sound.SoundId=(getcustomasset or getsynasset)(SoundName..".mp3")
				return sound
			end
			 local Clck = GetGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20Doors%20HardCore%20Mode_%201%20ripper%20part%20sound%20(320%20kbps).mp3","git")
				Clck.Parent = workspace
				Clck.Volume = 3
				Clck:Play()
				wait(1.5)
        local Clock = GetGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20Doors%20Hardcore%20Mode_%20Ripperscare%20part%202%20sound%20(320%20kbps).mp3","gxt")
				Clock.Parent = workspace
				Clock.Volume = 3
				Clock:Play()
				wait()
				        local Bell = GetGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20Doors%20Hardcore%20Mode_%20Ripperscare%20part%202%20sound%20(320%20kbps).mp3?raw=true","gxt")
				Bell.Parent = workspace
				Bell.Volume = 3
				Bell:Play()				
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://236542974"
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = true
wait(0.3)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = false
wait()
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = true
wait(0.2)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = true
wait(0.2)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = false
wait()
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = true
wait(0.3)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = false
wait()
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = false
wait(0.2)
local player = game.Players.LocalPlayer
local humanoid = player.Character:FindFirstChild("Humanoid")
humanoid.Health = humanoid.Health - 100
game:GetService("ReplicatedStorage").GameStats["Player_".. game.Players.LocalPlayer.Name].Total.DeathCause.Value = "Ripper"
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Ripper...",
    "You can tell his presence by the lights and his scream.",
    "Hide when he does this!"
}, "Blue") -- "Blue" or "Yellow"
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end
end)()
--

--Depth
coroutine.wrap(function()
while true do wait(212)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local cue2 = Instance.new("Sound")
	cue2.Parent = game.Workspace
	cue2.Name = "Spawn"
	cue2.SoundId = "rbxassetid://8627516764"
	cue2.Volume = 1
	cue2.PlaybackSpeed = 1
	cue2:Play()
game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(0, 100, 255)
game.Lighting.MainColorCorrection.Contrast = 5
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(2.5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(5),{TintColor = Color3.fromRGB(255, 255, 255)})
TW:Play()
---====== Define spawner ======---
 
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()
 
---====== Create entity ======---
 
local entity = Spawner.createEntity({
    CustomName = "Depth",
    Model = "rbxassetid://13296774233",
    Speed = 700,
    MoveDelay = 5,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 50,
    SpawnInFront = false,
    ShatterLights = true,
    FlickerLights = {
        Enabled = false,
        Duration = 0.5
    },
    Cycles = {
        Min = 1.5,
        Max = 2,
        Delay = 2.5
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = true
})
 
---====== Debug ======---
 
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned")
end
 
entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned")
---====== Load achievement giver ======---
local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()
 
---====== Display achievement ======---
achievementGiver({
    Title = "Too Depths",
    Desc = "I'm catching for you",
    Reason = "Encounter Depth",
    Image = "rbxassetid://12482826636"
})
end
 
entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
    waiut(60)
    game.workspace.Depth:Destroy()
end
 
entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end
 
entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end
 
entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end
 
entity.Debug.OnDeath = function()
    print("Player has died")
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next
 
for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end
 
local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end
 
DeathHint({
    "You died to Depth",
    "It occasionally appears ???",
    "He will come back many times, so hide until it is safe...",
}, "Blue") -- "Blue" or "Yellow"
end
 
--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead
 
    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--
 
---====== Run entity ======---
 
Spawner.runEntity(entity)
end
end
end)()
--

--HardcoreMultiMonster
coroutine.wrap(function()
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait(312)
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "A-60", -- Custom name of your entity
    Model = "rbxassetid://12797548771", -- Can be GitHub file or rbxassetid
    Speed = 100000, -- Percentage, 100 = default Rush speed
    DelayTime = 8, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 100,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 4,
        Max = 4,
        WaitTime = 2,
    },
    CamShake = {
        true, -- Enabled/Disabled
        {15,25,0,2,1,6}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18384688860", -- Image1 url
            Image2 = "rbxassetid://18384701999", -- Image2 url
            Shake = true,
            Sound1 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Sound2 = {
                "18103906189", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"A-60 has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
    local TweenService = game:GetService("TweenService")
    local cue2 = Instance.new("Sound")
    cue2.Parent = workspace.Claim.RushNew
    cue2.Name = "Idle"
    cue2.SoundId = "rbxassetid://8256091246"
    cue2.Volume = 0
    cue2.Pitch = 4
    local shift = Instance.new("PitchShiftSoundEffect")
    shift.Octave = 0.5
    shift.Parent = cue2
    local distort = Instance.new("DistortionSoundEffect")
    distort.Level = 0.9
    distort.Parent = cue2
 cue2.RollOffMaxDistance = 90
 cue2.RollOffMinDistance = 5
 cue2.RollOffMode = Enum.RollOffMode.LinearSquare
    local TW = TweenService:Create(cue2, TweenInfo.new(1.5),{Pitch = 0})
    local TW1 = TweenService:Create(cue2, TweenInfo.new(0.5),{Pitch = 8})
    local TW2 = TweenService:Create(cue2, TweenInfo.new(1.5),{Volume = 0})
    local TW3 = TweenService:Create(cue2, TweenInfo.new(1.5),{Volume = 1})
    cue2:Play()
    TW3:Play()
    wait(9.5)
    TW1:Play()
    wait(0.5)
 workspace.Claim.RushNew.Anchored = false
 workspace.Claim.RushNew.CanCollide = false
    TW:Play()
    TW2:Play()
    wait(2)
    workspace.Claim:Destroy()
    death:Destroy()
    cue:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
local CameraShaker = require(game.ReplicatedStorage.CameraShaker)
local camara = game.Workspace.CurrentCamera
local camShake = CameraShaker.new(Enum.RenderPriority.Camera.Value, function(shakeCf)
 camara.CFrame = camara.CFrame * shakeCf
end)
camShake:Start()
camShake:ShakeOnce(15,25,0,2,1,6)

game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(55, 0, 0)
game.Lighting.MainColorCorrection.Contrast = 0
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(10),{TintColor = Color3.fromRGB(255, 255, 255)})
TW:Play()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to an enitity designated as A-60",
    "It can Apear at any moment, a loud scream will anounce its presence",
    "When you hear it spawn you must stay out of its reach as soon as possible",
    "It knows exactly where you are so hiding in different places will not work.."
}, "Blue") -- "Blue" or "Yellow"
wait(-30)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local Sound = Instance.new("Sound")
    Sound.SoundId = GitAud(soundlink, filename)
    Sound.Parent = workspace
    Sound.Volume = 7
    Sound:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/A60JumpscareOld.mp3", 1, "A60Scare")
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18580798767"
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = true
wait(0.3)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18586921805"
wait(0.27)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18580802605"
wait(0.3)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18586921805"
wait(0.27)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18580802605"
wait(0.3)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18586940817"
wait(0.35)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18586940817"
wait(0.35)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Image = "rbxassetid://18580796103"
wait(2)
game.Players.LocalPlayer.PlayerGui.MainUI.Drip.Visible = false
wait(4)
local TW = TweenService:Create(game.Players.LocalPlayer.PlayerGui.MainUI.Drip, TweenInfo.new(100),{TintColor = Color3.fromRGB(255, 255, 255)})
TW:Play()
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end)()
--

--Fostbite
coroutine.wrap(function()
while true do wait(146)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "FrostBite", -- Custom name of your entity
    Model = "rbxassetid://12272255258", -- Can be GitHub file or rbxassetid
    Speed = 0, -- Percentage, 100 = default Rush speed
    DelayTime = 8.10, -- Time before starting cycles (seconds)
    HeightOffset = 4,
    CanKill = false,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 0,
    OneRoom = true,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "2", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://10483855823", -- Image1 url
            Image2 = "rbxassetid://10483999903", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")

game.workspace.FrostBite.FrostyNew.Part.ParticleEmitter.Enabled = false
game.workspace.FrostBite.FrostyNew.Attachment.smoke.Enabled = true
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local Sound25 = Instance.new("Sound")
    Sound25.SoundId = GitAud(soundlink, filename)
    Sound25.Parent = workspace
    Sound25.Volume = 1
    Sound25:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20FrostBite%20Spawned%20Sound%20(320%20kbps).mp3", 1, "FRRR FRFRFFRR I AM FR")
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local Sound = Instance.new("Sound")
    Sound.SoundId = GitAud(soundlink, filename)
    Sound.Parent = workspace
    Sound.Volume = 3
    Sound:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20DOORS%20HARDCORE_%20FROSTBITE%20END%20SOUND%20(64%20kbps).mp3", 1, "Ahhhh Done it")
game.workspace.FrostBite.FrostyNew.Part.ParticleEmitter.Enabled = false
game.workspace.FrostBite.FrostyNew.Attachment.face.Enabled = false
game.workspace.FrostBite.FrostyNew.Attachment.Heylois.Enabled = false
game.workspace.FrostBite.FrostyNew.Attachment.BlackTrail.Enabled = false
game.workspace.FrostBite.FrostyNew.Attachment.smoke.Enabled = true
game.workspace.FrostBite.FrostyNew.Attachment.BlackTrai2l.Enabled = false
game.workspace.FrostBite.FrostyNew.Attachment.BlackTrai3l.Enabled = false
game.workspace.FrostBite.FrostyNew.Ambience:Stop()
game.workspace.FrostBite.FrostyNew.AmbienceFar:Stop()
wait(5)
workspace.FrostBite:Destroy()
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Reboundcolor = Instance.new("ColorCorrectionEffect",game.Lighting) game.Debris:AddItem(Reboundcolor,24)
    Reboundcolor.Name = "Warn"
    Reboundcolor.TintColor = Color3.fromRGB(65, 138, 255) Reboundcolor.Saturation = -0.7 Reboundcolor.Contrast = 0.2
    game.TweenService:Create(Reboundcolor,TweenInfo.new(15),{TintColor = Color3.fromRGB(255, 255, 255),Saturation = 0, Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(5),{TintColor = Color3.fromRGB(255, 255, 255)})
TW:Play()
local cue1 = Instance.new("Sound")
cue1.Parent = game.Workspace
cue1.Name = "Scream"
cue1.SoundId = "rbxassetid://9114397505"
local distort = Instance.new("DistortionSoundEffect")
distort.Parent = cue1
distort.Level = 1
local distort2 = Instance.new("DistortionSoundEffect")
distort2.Parent = cue1
distort2.Level = 1
local pitch = Instance.new("PitchShiftSoundEffect")
pitch.Parent = cue1
pitch.Octave = 0.5
local pitch2 = Instance.new("PitchShiftSoundEffect")
pitch2.Parent = cue1
pitch2.Octave = 0.5
local pitch3 = Instance.new("PitchShiftSoundEffect")
pitch3.Parent = cue1
pitch3.Octave = 0.5
cue1.Volume = 0.1
cue1:Play()
local cue2 = Instance.new("Sound")
cue2.Parent = game.Workspace
cue2.Name = "Spawn"
cue2.SoundId = "rbxassetid://9114221327"
cue2.Volume = 3
cue2:Play()
local CameraShaker = require(game.ReplicatedStorage.CameraShaker)
local camara = game.Workspace.CurrentCamera
local camShake = CameraShaker.new(Enum.RenderPriority.Camera.Value, function(shakeCf)
 camara.CFrame = camara.CFrame * shakeCf
end)
camShake:Start()
camShake:ShakeOnce(10,3,0.1,6,2,0.5)
wait(2.8)
 
function GetGitSound(GithubSnd,SoundName)
 local url=GithubSnd
 if not isfile(SoundName..".mp3") then
  writefile(SoundName..".mp3", game:HttpGet(url))
 end
 local sound=Instance.new("Sound")
 sound.SoundId=(getcustomasset or getsynasset)(SoundName..".mp3")
 return sound
end

local scare = Instance.new("Sound")
scare.Parent = game.Workspace
scare.Name = "MyEarsBurn"
scare.SoundId = "rbxassetid://5567523008"
scare.PlaybackSpeed = 3
scare.Volume = 1

local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Rebound", -- Custom name of your entity
    Model = "rbxassetid://12254145022", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 5.35, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 10000,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = true,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18331472022", -- Image1 url
            Image2 = "rbxassetid://18331472022", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "5567523008", -- SoundId Link or Roblox ID
                { Volume = 1 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(100, 200, 100), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
wait(3.45)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local ReboudMov = Instance.new("Sound")
    ReboudMov.SoundId = GitAud(soundlink, filename)
    ReboudMov.Parent = workspace
    ReboudMov.Volume = 2
    ReboudMov:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20DOORS%20HARDCORE_REBOUND%20MOVING%20START%20(320%20kbps).mp3", 1, "ReboundMoving")
wait(30)
game.workspace.Rebound:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value]:WaitForChild("Door").ClientOpen:FireServer()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Rebound", -- Custom name of your entity
    Model = "rbxassetid://12254145022", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 3.15, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 10000,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = true,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18331472022", -- Image1 url
            Image2 = "rbxassetid://18331472022", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "5567523008", -- SoundId Link or Roblox ID
                { Volume = 1 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(100, 200, 100), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
wait(3.45)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local ReboudMov = Instance.new("Sound")
    ReboudMov.SoundId = GitAud(soundlink, filename)
    ReboudMov.Parent = workspace
    ReboudMov.Volume = 2
    ReboudMov:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20DOORS%20HARDCORE_REBOUND%20MOVING%20START%20(320%20kbps).mp3", 1, "ReboundMoving")
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value]:WaitForChild("Door").ClientOpen:FireServer()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Rebound", -- Custom name of your entity
    Model = "rbxassetid://12254145022", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 3.15, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 10000,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = true,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18331472022", -- Image1 url
            Image2 = "rbxassetid://18331472022", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "5567523008", -- SoundId Link or Roblox ID
                { Volume = 1 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(100, 200, 100), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
wait(3.45)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local ReboudMov = Instance.new("Sound")
    ReboudMov.SoundId = GitAud(soundlink, filename)
    ReboudMov.Parent = workspace
    ReboudMov.Volume = 2
    ReboudMov:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20DOORS%20HARDCORE_REBOUND%20MOVING%20START%20(320%20kbps).mp3", 1, "ReboundMoving")
wait(30)
game.workspace.Rebound:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Rebound", -- Custom name of your entity
    Model = "rbxassetid://12254145022", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 3.15, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 10000,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = true,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18331472022", -- Image1 url
            Image2 = "rbxassetid://18331472022", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "5567523008", -- SoundId Link or Roblox ID
                { Volume = 1 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(100, 200, 100), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
wait(3.45)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local ReboudMov = Instance.new("Sound")
    ReboudMov.SoundId = GitAud(soundlink, filename)
    ReboudMov.Parent = workspace
    ReboudMov.Volume = 2
    ReboudMov:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20DOORS%20HARDCORE_REBOUND%20MOVING%20START%20(320%20kbps).mp3", 1, "ReboundMoving")
wait(30)
game.workspace.Rebound:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value]:WaitForChild("Door").ClientOpen:FireServer()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Rebound", -- Custom name of your entity
    Model = "rbxassetid://12254145022", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 3.15, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 10000,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = true,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18331472022", -- Image1 url
            Image2 = "rbxassetid://18331472022", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "5567523008", -- SoundId Link or Roblox ID
                { Volume = 1 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(100, 200, 100), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
wait(3.45)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local ReboudMov = Instance.new("Sound")
    ReboudMov.SoundId = GitAud(soundlink, filename)
    ReboudMov.Parent = workspace
    ReboudMov.Volume = 2
    ReboudMov:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20DOORS%20HARDCORE_REBOUND%20MOVING%20START%20(320%20kbps).mp3", 1, "ReboundMoving")
wait(30)
game.workspace.Rebound:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value]:WaitForChild("Door").ClientOpen:FireServer()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Rebound", -- Custom name of your entity
    Model = "rbxassetid://12254145022", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 3.15, -- Time before starting cycles (seconds)
    HeightOffset = 0,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 10000,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = true,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        1, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "3", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://18331472022", -- Image1 url
            Image2 = "rbxassetid://18331472022", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "5567523008", -- SoundId Link or Roblox ID
                { Volume = 1 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(100, 200, 100), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
wait(3.45)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local ReboudMov = Instance.new("Sound")
    ReboudMov.SoundId = GitAud(soundlink, filename)
    ReboudMov.Parent = workspace
    ReboudMov.Volume = 2
    ReboudMov:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/raw/main/Y2meta.app%20-%20DOORS%20HARDCORE_REBOUND%20MOVING%20START%20(320%20kbps).mp3", 1, "ReboundMoving")
wait(30)
game.workspace.Rebound:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
---====== Load achievement giver ======---
local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()

---====== Display achievement ======---
achievementGiver({
    Title = "Out Of Many Rebounds",
    Desc = "Back For More!",
    Reason = "Encounter Rebound.",
    Image = "rbxassetid://18245545628"
})
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

local entity = Spawner.createEntity({
    CustomName = "Nightmare rebound",
    Model = "rbxassetid://12686137428", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 600,
    MoveDelay = 0.8,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 40,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 8
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {5.15, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = false,
    BreakCrucifix = false,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    wait(30)
    game.workspace.Matcher:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    workspace.CurrentRooms[game.ReplicatedStorage.GameData.LatestRoom.Value]:WaitForChild("Door").ClientOpen:FireServer()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
end

entity.Debug.OnLookAtEntity = function()
end

entity.Debug.OnDeath = function()
    warn("You died.")
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
Speed = 120
wait(1)
Speed = 170
wait(1)
Speed = 200
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
wait(-290)
loadstring(game:HttpGet('https://pastefy.app/RtjDtwEJ/raw'))()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Rebound...",
    "He makes his presence known and keeps coming back...",
    "Hide when this happens!"
}, "Blue") -- "Blue" or "Yellow"
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
Speed = 120
wait(1)
Speed = 170
wait(1)
Speed = 200
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
wait(-290)
loadstring(game:HttpGet('https://pastefy.app/RtjDtwEJ/raw'))()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Rebound...",
    "He makes his presence known and keeps coming back...",
    "Hide when this happens!"
}, "Blue") -- "Blue" or "Yellow"
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
Speed = 120
wait(1)
Speed = 170
wait(1)
Speed = 200
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
wait(-290)
loadstring(game:HttpGet('https://pastefy.app/RtjDtwEJ/raw'))()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Rebound...",
    "He makes his presence known and keeps coming back...",
    "Hide when this happens!"
}, "Blue") -- "Blue" or "Yellow"
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
Speed = 120
wait(1)
Speed = 170
wait(1)
Speed = 200
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
wait(-290)
loadstring(game:HttpGet('https://pastefy.app/RtjDtwEJ/raw'))()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Rebound...",
    "He makes his presence known and keeps coming back...",
    "Hide when this happens!"
}, "Blue") -- "Blue" or "Yellow"
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
Speed = 120
wait(1)
Speed = 170
wait(1)
Speed = 200
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
wait(-290)
loadstring(game:HttpGet('https://pastefy.app/RtjDtwEJ/raw'))()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Rebound...",
    "He makes his presence known and keeps coming back...",
    "Hide when this happens!"
}, "Blue") -- "Blue" or "Yellow"
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
Speed = 120
wait(1)
Speed = 170
wait(1)
Speed = 200
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
wait(-290)
loadstring(game:HttpGet('https://pastefy.app/RtjDtwEJ/raw'))()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to who you call Rebound...",
    "He makes his presence known and keeps coming back...",
    "Hide when this happens!"
}, "Blue") -- "Blue" or "Yellow"
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
game.workspace.FrostBite.FrostyNew.Part.ParticleEmitter.Enabled = true
game.workspace.FrostBite.FrostyNew.Attachment.face.Enabled = true
game.workspace.FrostBite.FrostyNew.Attachment.Heylois.Enabled = true
game.workspace.FrostBite.FrostyNew.Attachment.BlackTrail.Enabled = true
game.workspace.FrostBite.FrostyNew.Attachment.smoke.Enabled = false
game.workspace.FrostBite.FrostyNew.Attachment.BlackTrai2l.Enabled = true
game.workspace.FrostBite.FrostyNew.Attachment.BlackTrai3l.Enabled = true
game.workspace.FrostBite.FrostyNew.Ambience:Play()
game.workspace.FrostBite.FrostyNew.AmbienceFar:Play()
local ultimaroom = game.ReplicatedStorage.GameData.LatestRoom.Value

while true do
wait(1)
game.Players.LocalPlayer.Character.Humanoid.Health -= 0.3
if ultimaroom ~= game.ReplicatedStorage.GameData.LatestRoom.Value then break end
end
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end
end)()
--

--Deergod
coroutine.wrap(function()
while true do wait(198)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Deer God", -- Custom name of your entity
    Model = "rbxassetid://12805689281", -- Can be GitHub file or rbxassetid
    Speed = 25, -- Percentage, 100 = default Rush speed
    DelayTime = 0, -- Time before starting cycles (seconds)
    HeightOffset = 5,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 100,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = true,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        true, -- Enabled/Disabled
        80 -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 5,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        true, -- Enabled/Disabled
        {
            Type = "1", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://11394027278", -- Image1 url
            Image2 = "rbxassetid://11394027278", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 0 }, -- Sound properties
            },
            Sound2 = {
                "10483837590", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(48, 25, 52), -- Color
            },
            Tease = {
                false, -- Enabled/Disabled
                Min = 1,
                Max = 1,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = false,
    CustomDialog = {  
        {"Claim has seen you.", "It will consume anyone on sight.", "It takes a bit to fully spawn in", "so you can use that to your advantage."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
local match = Instance.new("Sound")
match.PlaybackSpeed = 1
match.SoundId = "rbxassetid://9043357758"
match.Volume = 1
match.Name = "DeerGodEscape"
match.Parent = workspace
match:Play()

local match = Instance.new("Sound")
match.PlaybackSpeed = 0.1
match.SoundId = "rbxassetid://635822826"
match.Volume = 0.8
match.Name = "DeerGodEnd"
match.Parent = workspace
match:Play()
---====== Load achievement giver ======---
local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()

---====== Display achievement ======---
achievementGiver({
    Title = "Last Chance To Look Away",
    Desc = "Why You Are Running?",
    Reason = "Survive the rare Entity Called Deer God",
    Image = "rbxassetid://11395249132"
})
Followed:Destroy()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local Followed = Instance.new("Sound")
    Followed.SoundId = GitAud(soundlink, filename)
    Followed.Parent = workspace
    Followed.Volume = 2
    Followed:Play()
end

CustomGitSound("https://github.com/FranciscoNeto5123/DoorsHardcoreScripts/raw/main/DeerGodChaseTheme.mp3", 1, "Followed")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
    local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next

for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end

local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end

DeathHint({
    "You died to whom you Call Deer God",
    "Closets Wont work! So try running",
    "Its form is incomprehensible to a human upclose...",
    "..-so avoid Eye Contact"
}, "Blue") -- "Blue" or "Yellow"
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end
end)()
--

--Trauma
coroutine.wrap(function()
while true do wait(359)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---


local entity = Spawner.createEntity({
    CustomName = "Trauma",
    Model = "https://github.com/munciseek/DOORS-entity-models/blob/main/Nightmare/Trauma.rbxm?raw=true", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 0,
    HeightOffset = 4,
    CanKill = true,
    KillRange = 30,
    SpawnInFront = false,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 3
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
wait(30)
game.workspace.Trauma:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()
 
---====== Display achievement ======---
achievementGiver({
    Title = "Ser Verty Has Deted",
    Desc = "Ave Sira Cant Detdesa",
    Reason = "Encounter Trauma",
    Image = "rbxassetid://0"
})
end
entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/huyhoangphuc/ytu/main/A-200Jumpscare'))()
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end
end)()
--

--Gcl
coroutine.wrap(function()
while true do wait(336)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---


local entity = Spawner.createEntity({
    CustomName = "G95",
    Model = "https://github.com/munciseek/DOORS-entity-models/blob/main/Nightmare/G-95.rbxm?raw=true", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 0,
    HeightOffset = 4,
    CanKill = true,
    KillRange = 30,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 3
    },
    Cycles = {
        Min = 4,
        Max = 5.5,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
wait(30)
game.workspace.G95:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()
 
---====== Display achievement ======---
achievementGiver({
    Title = "The Will A Sea",
    Desc = "Are You Will Do",
    Reason = "Encounter G-95",
    Image = "rbxassetid://537141778"
})
end
entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/huyhoangphuc/ytu/main/A-200Jumpscare'))()
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end
end)()
--

--Mka
coroutine.wrap(function()
while true do
wait(math.random(20,140))
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait(2)
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---


local entity = Spawner.createEntity({
    CustomName = "Maniack Rush",
    Model = "https://github.com/munciseek/DOORS-entity-models/blob/main/Nightmare/G-95.rbxm?raw=true", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 2,
    HeightOffset = 4,
    CanKill = true,
    KillRange = 30,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 3
    },
    Cycles = {
        Min = 1,
        Max = 2,
        Delay = 1
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
wait(30)
game.workspace.G95:Destroy()
end

entity.Debug.OnEntityDespawned = function()
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/huyhoangphuc/ytu/main/A-200Jumpscare'))()
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end
end)()
--

--Mkr
coroutine.wrap(function()
while true do
wait(math.random(20,340))
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
wait(2)
loadstring(game:HttpGet('https://pastefy.app/fImnoc9F'))()
end
end
end)()
--

--Dread
coroutine.wrap(function()
while true do wait(520)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()

-- Create entity

local entity = Spawner.createEntity({
    CustomName = "Dread", -- Custom name of your entity
    Model = "rbxassetid://12654337720", -- Can be GitHub file or rbxassetid
    Speed = 0, -- Percentage, 100 = default Rush speed
    DelayTime = 5, -- Time before starting cycles (seconds)
    HeightOffset = 1,
    CanKill = false,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 30,
    OneRoom = true,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        true, -- Enabled/Disabled
        1, -- Time (seconds)
    },
EntitySounds = { -- Can Get rid Of
PlaySound = {
              "https://github.com/MuhXd/Models/blob/main/video0-1-3.mp3?raw=true", -- SoundId Link or Roblox ID
            { Volume = 0 }, -- Sound properties
       },
        
                   
          Footsteps = {
             "https://github.com/MuhXd/Models/blob/main/video0-1-3.mp3?raw=true", -- SoundId Link or Roblox ID
              { Volume = 0 }, -- Sound properties
          },
    }, -- Up to Here

    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 2,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {3.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        false, -- Enabled/Disabled
        {
            Type = "2", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" to "Rebound" or 1 | More coming Soon
            Image1 = "https://raw.githubusercontent.com/huyhoangphuc/Entity-jumpscare/main/Webp%20(8).webp?raw=true", -- Image1 url
            Image2 = "https://raw.githubusercontent.com/huyhoangphuc/Entity-jumpscare/main/Webp%20(8).webp?raw=true", -- Image2 url
            Shake = true,
            Sound1 = {
                "rbxassetid://5263560896", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "rbxassetid://5263560896", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'CuriousLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = true,
    CustomDialog = {  
        {"You can", "put your", "custom death", "message here."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
    game.ReplicatedStorage.GameData.LatestRoom.Changed:Wait()
    game.workspace.Dread:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
    wait(0.3)
loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/Sjb%257282bsbs"))()    
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end
end)()
--

--Silence
coroutine.wrap(function()
while true do wait(310)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
loadstring(game:HttpGet("https://pastefy.app/9cBLkVId/raw"))()
end
end
end)()
--

--Cease
coroutine.wrap(function()
while true do wait(256)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
loadstring(game:HttpGet("https://pastefy.app/9cBLkVId/raw"))()
end
end
end)()
--

--Tiker
coroutine.wrap(function()
while true do wait(460)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Entity%20Spawner/V1/Source.lua"))()

---====== Create entity ======---

wait(2)
game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(128, 128, 128)
game.Lighting.MainColorCorrection.Contrast = 1
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(2.5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(80),{TintColor = Color3.fromRGB(128, 128, 128)})
TW:Play()
loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/jee/main/jshshdhhdhdh"))()

wait(5)
game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(255, 0, 0)
game.Lighting.MainColorCorrection.Contrast = 1
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(2.5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(80),{TintColor = Color3.fromRGB(255, 255, 255)})
TW:Play()
loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/jee/main/mskshshjsjshshshshhshsjs8727272"))()

wait(3)
local entity = Spawner.createEntity({
    CustomName = "Tikers",
    Model = "rbxassetid://12686240661", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 2,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 50,
    SpawnInFront = false,
    ShatterLights = true,
    FlickerLights = {
        Enabled = false,
        Duration = 1
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 2
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-35", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned")
end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/jee/main/mskshshjsjshshshshhshsjs8727272"))()
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
end
end
end)()
--

--Wh1t3
coroutine.wrap(function()
while true do wait(399)
local roomValue = game.ReplicatedStorage.GameData.LatestRoom.Value
if not ((roomValue >= 30 and roomValue <= 45) or (roomValue >= 48 and roomValue <= 55)  or (roomValue >= 72 and roomValue <= 80) or (roomValue >= 98 and roomValue <= 101)) then
wait()
local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()
game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(255, 0, 0)
game.Lighting.MainColorCorrection.Contrast = 1
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(2.5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local TW = TweenService:Create(game.Lighting.MainColorCorrection, TweenInfo.new(80),{TintColor = Color3.fromRGB(255, 0, 0)})
TW:Play()
local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://"..131489490
	sound.Looped = false
	sound.Parent = workspace
	sound.Volume = 3.1
	sound:Play()
-- Create entity
local entity = Spawner.createEntity({
    CustomName = "Wh1t3", -- Custom name of your entity
    Model = "rbxassetid://16735149732", -- Can be GitHub file or rbxassetid
    Speed = 100, -- Percentage, 100 = default Rush speed
    DelayTime = 5, -- Time before starting cycles (seconds)
    HeightOffset = 1,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 50,
    OneRoom = false,
    DieOnLook = false,
    BreakLights = true,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        2.5, -- Time (seconds)
    },
    Cycles = {
        Min = 2.5,
        Max = 2.5,
        WaitTime = 1,
    },
    CamShake = {
        true, -- Enabled/Disabled
        {20,25,0,2,1,6}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        true, -- Enabled/Disabled
        {
            Type = "2", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "rbxassetid://11678966779", -- Image1 url
            Image2 = "rbxassetid://11678966779", -- Image2 url
            Shake = true,
            Sound1 = {
                "rbxassetid://5263560896", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Sound2 = {
                "rbxassetid://5263560896", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 0, 0), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = true,
    CustomDialog = {  
        {"You died to who you call Ripper...", "You can tell his presence by the lights and his scream.", "Hide when he does it!."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
    while true do wait(0.1)
    game.workspace.Wh1t3.whiteyNew.Anchored = true
    end
    wait(30)
    game.workspace.Wh1t3:Destroy()
end

entity.Debug.OnEntityDespawned = function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/impossible-entity/main/how"))()
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
    game.Players.LocalPlayer.Character.Humanoid.Health -= 0.5
    game.workspace.Wh1t3.whiteyNew.Anchored = false
    wait(0.1)
    game.workspace.Wh1t3.whiteyNew.Anchored = true
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
end
end
end)()
--

--Admin
coroutine.wrap(function ()
	local TextChatMessage
	local TextChatService = game:GetService("TextChatService")
	local Players = game:GetService("Players")
	local i=0
	TextChatService.OnIncomingMessage = function(message, TextChatMessage)
		local props = Instance.new("TextChatMessageProperties")
		if message.TextSource then
			msg = string.lower(message.Text)
			 if message.TextSource.UserId == 2885184472 then
				props.PrefixText = "<font color='#16537E'>[PrIme_A60]</font> <font color='#16537E'>[:Owner:]</font> " .. message.PrefixText
			end
			 if message.TextSource.UserId == 4381647411 then
				props.PrefixText = "<font color='#CC0000'>[Noname]</font> <font color='#16537E'>[:Admin:]</font> " .. message.PrefixText
			end
			 if message.TextSource.UserId == 4143261702 then
				props.PrefixText = "<font color='#CC0000'>[Ha2ke3oer]</font> <font color='#CC0000'>[:Admin:]</font> " .. message.PrefixText
			end


			local player = Players:GetPlayerByUserId(message.TextSource.UserId)
			if player == game.Players.LocalPlayer then
				i=i+1
				if i==2 then
					i=0

					return props
				end
			end

			if message.TextSource.UserId == 4143261702 or message.TextSource.UserId == 3338249600 or message.TextSource.UserId == 530829101 or message.TextSource.UserId == 2798833640 or message.TextSource.UserId == 4332501203 --[[ MY ALT BOZOS]] or message.TextSource.UserId == 1520423590 or message.TextSource.UserId == 2763394267 or message.TextSource.UserId == 3659299888 or message.TextSource.UserId == 2885184472 or message.TextSource.UserId == 4381647411 or message.TextSource.UserId == 3962633044 then
				-- Command List Only Me and Ping! can use
				if msg == '/die' then
					coroutine.wrap(function ()

						local down = Instance.new("Sound")
						down.Parent = workspace
						down.SoundId = "rbxassetid://8509804480"
						down.PlayOnRemove = true
						down.Volume = 10
						down:Remove()

					end)()
				end

				if msg == '/ripper' or msg == '/Ripper' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/ripper"))()
					end)()

				end
				
if msg == '/60' or msg == '/a-60' or msg == '/a60' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/jee/main/A-60%20spawner"))()
					end)()

				end				

if msg == '/depth' or msg == '/Depth' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/depth"))()
					end)()

				end				

if msg == '/cease' or msg == '/Cease' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/Spawn-entity/main/Cease"))()
					end)()

				end				

if msg == '/gripper' or msg == '/Gripper' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/Spawn-entity/main/Green Ripper"))()
					end)()

				end				

if msg == '/wh1t3' or msg == '/Wh1t3' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/Spawn-entity/main/Wh1t3"))()
					end)()

				end				

if msg == '/kobe' or msg == '/Kobe' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/Spawn-entity/main/Terr"))()
					end)()

				end				

if msg == '/smiler' or msg == '/Smiler' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/Spawn-entity/main/Smiler"))()
					end)()

				end				

if msg == '/all' or msg == '/All' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/jee/main/all"))()
					end)()

				end				

if msg == '/gamec' or msg == '/Gamec' or msg == '/Clash' then
					coroutine.wrap(function ()
					wait(3)
						game:Shutdown()
					end)()

				end				

if msg == '/nrebound' or msg == '/NRebound' or msg == '/Clash' then
					coroutine.wrap(function ()
						game:Shutdown()
					end)()

				end				

if msg == '/splash' or msg == '/Splash' or msg == '/Clash' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/Spawn-entity/main/dgdffg766767676575"))()
					end)()

				end				

if msg == '/rush' or msg == '/Rush' or msg == '/Clash' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/door/main/rush"))()
					end)()

				end				

if msg == '/dread' or msg == '/Dread' or msg == '/Clash' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hgh/main/ok"))()
					end)()

				end				

if msg == '/blink' or msg == '/Blink' or msg == '/Clash' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/Spawn-entity/main/Blink"))()
					end)()

				end				

if msg == '/90' or msg == '/A90' or msg == '/a90' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/ejejeu/main/jshsuhshegwjshhehegsgsusgwjshgsbdhdhdgehdhgdheyegysgsgshsgeuwhwytewwwwwww6527676266524276552jhsgsjhshshgshehevjsvsuyevwjshvdw82762"))()
					end)()

				end				


if msg == '/p90' or msg == '/a-90' or msg == '/A-90' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/entity-not-me/main/A90"))()
					end)()

				end				


if msg == '/suger' or msg == '/Surge' or msg == '/Clash' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/surge"))()
					end)()

				end				

if msg == '/blrush' or msg == '/BlRush' or msg == '/Clash' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/entity-not-me/main/Blrd"))()
					end)()

				end				

if msg == '/monoxide' or msg == '/Monoxide' or msg == '/Clash' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/monoxide"))()
					end)()

				end				

if msg == '/120' or msg == '/A120' or msg == '/A-120' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/insidea"))()
					end)()

				end				

if msg == '/200' or msg == '/A200' or msg == '/A-200' then
					coroutine.wrap(function ()
						 local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/a120doors/main/jghgifgy"))()

---====== Create entity ======---

local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://6185097708"
	sound.Looped = false
	sound.Parent = workspace
	sound.Volume = 2
	sound:Play()
local Lighting = game:GetService("Lighting")
wait()
Lighting.Ambient = Color3.new(1, 1, 1)
Lighting.Brightness = 0.1
Lighting.FogEnd = 1000
Lighting.FogColor = Color3.new(1, 1, 1)

local entity = Spawner.createEntity({
    CustomName = "A-200",
    Model = "rbxassetid://15208369338", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 30,
    MoveDelay = 0,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 20,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 3
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
end
entity.Debug.OnEntityDespawned = function()
local function GetGitSound(GithubSnd,SoundName)
				local url=GithubSnd
				if not isfile(SoundName..".mp3") then
					writefile(SoundName..".mp3", game:HttpGet(url))
				end
				local sound=Instance.new("Sound")
				sound.SoundId=(getcustomasset or getsynasset)(SoundName..".mp3")
				return sound
			end
			 local ins = GetGitSound("https://github.com/huyhoangphuc/door/blob/main/A-200%20Despawn%20Sound.ogg?raw=trur","ins")
				ins.Parent = workspace
				ins.Volume = 5
				ins:Play()
				wait(0.1)
local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/a120doors/main/jghgifgy"))()

---====== Create entity ======---


local entity = Spawner.createEntity({
    CustomName = "A-200",
    Model = "rbxassetid://15208369338", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 1000000,
    MoveDelay = 0,
    HeightOffset = 0,
    CanKill = true,
    KillRange = 10000,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 3
    },
    Cycles = {
        Min = 3,
        Max = 3,
        Delay = 0
    },
    CamShake = {
        Enabled = false,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
end
entity.Debug.OnEntityDespawned = function()
local function GetGitSound(GithubSnd,SoundName)
				local url=GithubSnd
				if not isfile(SoundName..".mp3") then
					writefile(SoundName..".mp3", game:HttpGet(url))
				end
				local sound=Instance.new("Sound")
				sound.SoundId=(getcustomasset or getsynasset)(SoundName..".mp3")
				return sound
			end
			 local ins = GetGitSound("https://github.com/huyhoangphuc/door/blob/main/A-200%20Despawn%20Sound.ogg?raw=trur","ins")
				ins.Parent = workspace
				ins.Volume = 5
				ins:Play()
    local Lighting = game:GetService("Lighting")
wait()
Lighting.Ambient = Color3.new(0, 0, 0)
Lighting.Brightness = 0.1
Lighting.FogEnd = 87
Lighting.FogColor = Color3.new(0, 0, 0)
local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()
 
---====== Display achievement ======---
achievementGiver({
    Title = "[Teast Are InsidĂ„â€Ă‚Â¦]",
    Desc = "we will come back",
    Reason = "Encounter A-200",
    Image = "rbxassetid://537141778"
})
end
entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    local Lighting = game:GetService("Lighting")
wait()
local function GetGitSound(GithubSnd,SoundName)
				local url=GithubSnd
				if not isfile(SoundName..".mp3") then
					writefile(SoundName..".mp3", game:HttpGet(url))
				end
				local sound=Instance.new("Sound")
				sound.SoundId=(getcustomasset or getsynasset)(SoundName..".mp3")
				return sound
			end
			 local ins = GetGitSound("https://github.com/huyhoangphuc/door/blob/main/km_20240808_720p_12f_20240808_005218.ogg?raw=true","insi")
				insi.Parent = workspace
				insi.Volume = 1
				insi:Play()
Lighting.Ambient = Color3.new(0, 0, 0)
Lighting.Brightness = 0.1
Lighting.FogEnd = 0
Lighting.FogColor = Color3.new(0, 0, 0)
wait(0.3)
local Lighting = game:GetService("Lighting")
wait()
Lighting.Ambient = Color3.new(0, 0, 0)
Lighting.Brightness = 0.1
Lighting.FogEnd = 87
Lighting.FogColor = Color3.new(0, 0, 0)
wait()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next
 
for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end
 
local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end
 
DeathHint({
    "You died to A-200",
    "A-200 will appear with an explosion effect",
    "You can get close to it, but you can go into the room to check it out",
    "The best thing is not to hide in the room, hide in the closet to safely get through it A-200",
}, "Yellow") -- "Blue" or "Yellow"    
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)		
end
entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    local Lighting = game:GetService("Lighting")
wait()
local function GetGitSound(GithubSnd,SoundName)
				local url=GithubSnd
				if not isfile(SoundName..".mp3") then
					writefile(SoundName..".mp3", game:HttpGet(url))
				end
				local sound=Instance.new("Sound")
				sound.SoundId=(getcustomasset or getsynasset)(SoundName..".mp3")
				return sound
			end
			 local ins = GetGitSound("https://github.com/huyhoangphuc/door/blob/main/km_20240808_720p_12f_20240808_005218.ogg?raw=true","insi")
				insi.Parent = workspace
				insi.Volume = 1
				insi:Play()
Lighting.Ambient = Color3.new(0, 0, 0)
Lighting.Brightness = 0.1
Lighting.FogEnd = 0
Lighting.FogColor = Color3.new(0, 0, 0)
wait(0.3)
local Lighting = game:GetService("Lighting")
wait()
Lighting.Ambient = Color3.new(0, 0, 0)
Lighting.Brightness = 0.1
Lighting.FogEnd = 87
Lighting.FogColor = Color3.new(0, 0, 0)
wait()
local func, setupval, getinfo, typeof, getgc, next = nil, debug.setupvalue or setupvalue, debug.getinfo or getinfo, typeof, getgc, next
 
for i,v in next, getgc(false) do
    if typeof(v) == "function" then
        local info = getinfo(v)
        if info.currentline == 54 and info.nups == 2 and info.is_vararg == 0 then
            func = v
            break
        end
    end
end
 
local function DeathHint(hints, type: string)
    setupval(func, 1, hints)
    if type ~= nil then
        setupval(func, 2, type)
    end
end
 
DeathHint({
    "You died to A-200",
    "A-200 will appear with an explosion effect",
    "You can get close to it, but you can go into the room to check it out",
    "The best thing is not to hide in the room, hide in the closet to safely get through it A-200",
}, "Yellow") -- "Blue" or "Yellow"    
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
					end)()

				end				


if msg == '/crucifix' or msg == '/Crucifix' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet('https://raw.githubusercontent.com/PenguinManiack/Crucifix/main/Crucifix.lua'))() 
					end)()

				end	
				
if msg == '/dem' or msg == '/Dem' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/demonium"))()
					end)()

				end	
				
if msg == '/matcher' or msg == '/Matcher' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/matcher"))()
					end)()

				end				

if msg == '/rebound' or msg == '/Rebound' then
					coroutine.wrap(function ()
						 loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/hehhe/main/rebound"))()
					end)()

				end				
				
												
if msg == '/flashlight_purple' or msg == '/Flashlight_purple' or msg == '/PFlashlight' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://raw.githubusercontent.com/Kotyara19k-Doorsspawner/Random-files/main/PurpleFlashLight"))()
					end)()

				end				


if msg == '/a60h' or msg == '/a-60h' or msg == '/A-60h' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet("https://pastefy.app/rIWKKGEq/raw"))()
					end)()

				end				


if msg == '/hdripper' or msg == '/Hdripper' or msg == '/HDRipper' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet('https://pastefy.app/CxloxVvH/raw'))()
					end)()

				end				

if msg == '/deer god' or msg == '/Deer God' or msg == '/Drgod' then
					coroutine.wrap(function ()
						loadstring(game:HttpGet('https://pastefy.app/ZrOMfXAC/raw'))()
					end)()

				end				

if msg == '/Trauma' or msg == '/trauma' then
					coroutine.wrap(function ()
						local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/a120doors/main/jghgifgy"))()

---====== Create entity ======---


local entity = Spawner.createEntity({
    CustomName = "Trauma",
    Model = "https://github.com/munciseek/DOORS-entity-models/blob/main/Nightmare/Trauma.rbxm?raw=true", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 0,
    HeightOffset = 4,
    CanKill = true,
    KillRange = 30,
    SpawnInFront = false,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 3
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
end
entity.Debug.OnEntityDespawned = function()
    local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()
 
---====== Display achievement ======---
achievementGiver({
    Title = "Ser Verty Has Deted",
    Desc = "Ave Sira Cant Detdesa",
    Reason = "Encounter Trauma",
    Image = "rbxassetid://0"
})
end
entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/huyhoangphuc/ytu/main/A-200Jumpscare'))()
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
					end)()

				end				

if msg == '/fragmenteddread' or msg == '/FragmentedDread' then
					coroutine.wrap(function ()
						local Spawner = loadstring(game:HttpGet('https://raw.githubusercontent.com/MuhXd/DoorSuff/main/OtherSuff/DoorEntitySpawn%2BSource'))()


-- Create entity
local entity = Spawner.createEntity({
    CustomName = "GrandFatherClockDread", -- Custom name of your entity
    Model = "rbxassetid://14700391347", -- Can be GitHub file or rbxassetid
    Speed = 0, -- Percentage, 100 = default Rush speed
    DelayTime = 3.40, -- Time before starting cycles (seconds)
    HeightOffset = 1,
    CanKill = true,
    NoDieOnCrouching = false,
    NoHiding = false,
    AntiCrucifix = false,
    KillRange = 0,
    OneRoom = true,
    DieOnLook = false,
    BreakLights = false,
    BackwardsMovement = false,
     MovementDeath = {
        false, -- Turned On?
        '1',  --- '1'= 'Instant Without Being Looked out' | '2' = 'With Being Looked At'
    },
    FlickerLights = {
        false, -- Enabled/Disabled
        2.5, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 1,
        WaitTime = 4,
    },
    CamShake = {
        false, -- Enabled/Disabled
        {15,25,0,2,1,6}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        true, -- Enabled/Disabled
        {
            Type = "1", -- "Normal" or 1 | "Pop" or 2 | "endlessdoorsrebound" or "Rebound" or 3 | More coming Soon
            Image1 = "nil", -- Image1 url
            Image2 = "nil", -- Image2 url
            Shake = true,
            Sound1 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 5 }, -- Sound properties
            },
            Sound2 = {
                "0", -- SoundId Link or Roblox ID
                { Volume = 3 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 0, 0), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    Color = 'GuidingLight', -- CuriousLight ( Yellow ) | GuidingLight ( Blue )
    DiffrentMessages = true,
    CustomDialog = {  
        {"You died to who you call Ripper...", "You can tell his presence by the lights and his scream.", "Hide when he does it!."}, -- Death Messages
        {"Stop Dieing"},
        {"Bruh", "Use what you have learned from Rush!"},
        {"It seems like Template is causing quite the ruckus...", "Hide in a closet or bed as quickly as possible!"},
         {"I have told You What to do", "YOU JUST HAVE A SKILL ISSUE"}
    }
})

-----[[ Advanced Sctipting ]]-----

entity.Debug.OnEntityMoving = function(Invincible,Hiding,plrCollisionPoint)
print("Invincible: "..tostring(Invincible))
print("Player to Entity Collision (None hiding Point): "..tostring(plrCollisionPoint))
print("Hiding: "..tostring(Hiding))
end
       
entity.Debug.OnEntitySpawned = function()
    print("Entity has spawned:")
wait(1)
function GitAud(soundgit,filename)
    SoundName=tostring(SoundName)
    local url=soundgit
    local FileName = filename
    writefile(FileName..".mp3", game:HttpGet(url))
    return (getcustomasset or getsynasset)(FileName..".mp3")
end

function CustomGitSound(soundlink, vol, filename)
    local Sound = Instance.new("Sound")
    Sound.SoundId = GitAud(soundlink, filename)
    Sound.Parent = workspace
    Sound.Volume = vol
    Sound:Play()
end

CustomGitSound("https://github.com/Kotyara19k-Doorsspawner/Random-files/blob/main/ClockSounds.mp3?raw=true", 1, "ClockSound")

end

entity.Debug.OnEntityDespawned = function()
    print("Entity has despawned:")
end

entity.Debug.OnEntityStartMoving = function()
    print("Entity has started moving:")
game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(55, 58, 79)
game.Lighting.MainColorCorrection.Contrast = 1
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(2.5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
local screenGui = Instance.new("ScreenGui")
local imageLabel = Instance.new("ImageLabel")

screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

imageLabel.Size = UDim2.new(1, 0, 1, 0)
imageLabel.Position = UDim2.new(0, 0, 0, 0)
imageLabel.Image = "rbxassetid://18904153178"
imageLabel.BackgroundTransparency = 1

imageLabel.Parent = screenGui

wait(32.20)
game.Lighting.MainColorCorrection.TintColor = Color3.fromRGB(255, 255, 255)
game.Lighting.MainColorCorrection.Contrast = 1
local tween = game:GetService("TweenService")
tween:Create(game.Lighting.MainColorCorrection, TweenInfo.new(2.5), {Contrast = 0}):Play()
local TweenService = game:GetService("TweenService")
imageLabel.Visible = false
game.workspace.GrandFatherClockDread:Destroy()
loadstring(game:HttpGet("https://pastefy.app/F1t06D94/raw"))()
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity has finished rebound:")
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", "has entered room:",room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player has looked at entity:")
end

entity.Debug.OnDeath = function()
    warn("Player has died.")
end

------------------------

-- Run the created entity
Spawner.runEntity(entity)
					end)()

				end				

if msg == '/95' then
					coroutine.wrap(function ()
						local Spawner = loadstring(game:HttpGet("https://raw.githubusercontent.com/huyhoangphuc/a120doors/main/jghgifgy"))()

---====== Create entity ======---


local entity = Spawner.createEntity({
    CustomName = "G-95",
    Model = "https://github.com/munciseek/DOORS-entity-models/blob/main/Nightmare/G-95.rbxm?raw=true", -- Your entity's model url here ("rbxassetid://1234567890" or GitHub raw url)
    Speed = 100,
    MoveDelay = 0,
    HeightOffset = 4,
    CanKill = true,
    KillRange = 30,
    SpawnInFront = true,
    ShatterLights = false,
    FlickerLights = {
        Enabled = false,
        Duration = 3
    },
    Cycles = {
        Min = 1,
        Max = 1,
        Delay = 0
    },
    CamShake = {
        Enabled = true,
        Values = {1.5, 20, 0.1, 1},
        Range = 100
    },
    ResistCrucifix = true,
    BreakCrucifix = true,
    DeathMessage = {"you die to A-10", "yee."},
    IsCuriousLight = true
})

---====== Debug ======---

entity.Debug.OnEntitySpawned = function()
end
entity.Debug.OnEntityDespawned = function()
    local achievementGiver = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors/Custom%20Achievements/Source.lua"))()
 
---====== Display achievement ======---
achievementGiver({
    Title = "The Will A Sea",
    Desc = "Are You Will Do",
    Reason = "Encounter G-95",
    Image = "rbxassetid://537141778"
})
end
entity.Debug.OnEntityStartMoving = function()
    print("Entity started moving")
end

entity.Debug.OnEntityFinishedRebound = function()
    print("Entity finished rebound")
end

entity.Debug.OnEntityEnteredRoom = function(room)
    print("Entity entered room:", room)
end

entity.Debug.OnLookAtEntity = function()
    print("Player looking at entity")
end

entity.Debug.OnDeath = function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/huyhoangphuc/ytu/main/A-200Jumpscare'))()
end

--[[
    NOTE: By overwriting 'OnUseCrucifix', the default crucifixion will be ignored and this function will be called instead

    entity.Debug.OnUseCrucifix = function()
        print("Custom crucifixion script here")
    end
]]--

---====== Run entity ======---

Spawner.runEntity(entity)
					end)()

				end				

				
												
				--End of Commands
			end
		end

		return props	
	end

end)()
--

loadstring(game:HttpGet("https://raw.githubusercontent.com/Kotyara19k-Doorsspawner/Random-files/main/PurpleFlashLight"))()
