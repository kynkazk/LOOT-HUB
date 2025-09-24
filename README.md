--[[ 
    LOOT HUB Roblox Menu Script
    Features: Speed Booster, Jump Booster
    Author: kynkazk
    Usage: Place this script in StarterGui > LocalScript in Roblox Studio.
    Note: You must upload the image to Roblox as a decal and use its asset ID below.
--]]

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

-- Replace this with your uploaded decal asset ID after uploading the provided image
local IMAGE_ASSET_ID = "rbxassetid://108149498699782"

-- GUI Creation
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "LootHubGUI"
screenGui.ResetOnSpawn = false

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 350, 0, 400)
frame.Position = UDim2.new(0.5, -175, 0.5, -200)
frame.BackgroundColor3 = Color3.fromRGB(18, 18, 18)
frame.BorderSizePixel = 0
frame.Parent = screenGui

-- Image
local imageLabel = Instance.new("ImageLabel")
imageLabel.Size = UDim2.new(0, 250, 0, 250)
imageLabel.Position = UDim2.new(0.5, -125, 0, 10)
imageLabel.BackgroundTransparency = 1
imageLabel.Image = IMAGE_ASSET_ID
imageLabel.Parent = frame

-- Title
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.Position = UDim2.new(0, 0, 0, 265)
title.BackgroundTransparency = 1
title.Text = "LOOT HUB"
title.TextColor3 = Color3.fromRGB(255, 60, 60)
title.Font = Enum.Font.GothamBlack
title.TextScaled = true
title.Parent = frame

-- Speed Booster Button
local speedBtn = Instance.new("TextButton")
speedBtn.Size = UDim2.new(0.8, 0, 0, 40)
speedBtn.Position = UDim2.new(0.1, 0, 0, 320)
speedBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
speedBtn.Text = "Speed Booster"
speedBtn.TextColor3 = Color3.new(1,1,1)
speedBtn.Font = Enum.Font.GothamBold
speedBtn.TextScaled = true
speedBtn.Parent = frame

-- Jump Booster Button
local jumpBtn = Instance.new("TextButton")
jumpBtn.Size = UDim2.new(0.8, 0, 0, 40)
jumpBtn.Position = UDim2.new(0.1, 0, 0, 370)
jumpBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
jumpBtn.Text = "Jump Booster"
jumpBtn.TextColor3 = Color3.new(1,1,1)
jumpBtn.Font = Enum.Font.GothamBold
jumpBtn.TextScaled = true
jumpBtn.Parent = frame

-- Booster Logic
local normalWalkSpeed = humanoid.WalkSpeed
local normalJumpPower = humanoid.JumpPower

speedBtn.MouseButton1Click:Connect(function()
    if humanoid.WalkSpeed == normalWalkSpeed then
        humanoid.WalkSpeed = normalWalkSpeed * 2 -- Double speed
        speedBtn.Text = "Speed: ON"
        speedBtn.BackgroundColor3 = Color3.fromRGB(62, 180, 137)
    else
        humanoid.WalkSpeed = normalWalkSpeed
        speedBtn.Text = "Speed Booster"
        speedBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    end
end)

jumpBtn.MouseButton1Click:Connect(function()
    if humanoid.JumpPower == normalJumpPower then
        humanoid.JumpPower = normalJumpPower * 2 -- Double jump
        jumpBtn.Text = "Jump: ON"
        jumpBtn.BackgroundColor3 = Color3.fromRGB(62, 180, 137)
    else
        humanoid.JumpPower = normalJumpPower
        jumpBtn.Text = "Jump Booster"
        jumpBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    end
end)

screenGui.Parent = player:WaitForChild("PlayerGui")
