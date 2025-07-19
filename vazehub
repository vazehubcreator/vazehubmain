local player = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
gui.Name = "LoadingScreen"
gui.IgnoreGuiInset = true
gui.ResetOnSpawn = false

-- Freeze movement
player.CharacterAdded:Connect(function(char)
    local hum = char:WaitForChild("Humanoid")
    hum.WalkSpeed = 0
    hum.JumpPower = 0
end)
if player.Character then
    local hum = player.Character:FindFirstChild("Humanoid")
    if hum then
        hum.WalkSpeed = 0
        hum.JumpPower = 0
    end
end

-- Hide CoreGui
game:GetService("StarterGui"):SetCoreGuiEnabled(Enum.CoreGuiType.All, false)

-- Background
local bg = Instance.new("Frame", gui)
bg.Size = UDim2.new(1, 0, 1, 0)
bg.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

-- Message
local msg = Instance.new("TextLabel", gui)
msg.Size = UDim2.new(1, 0, 0.2, 0)
msg.Position = UDim2.new(0, 0, 0.35, 0)
msg.BackgroundTransparency = 1
msg.Text = "We're teleporting you to an old server,\nplease be patient"
msg.TextColor3 = Color3.new(1, 1, 1)
msg.TextScaled = true
msg.Font = Enum.Font.GothamBlack

-- Progress bar background
local barBg = Instance.new("Frame", gui)
barBg.Size = UDim2.new(0.7, 0, 0.05, 0)
barBg.Position = UDim2.new(0.15, 0, 0.75, 0)
barBg.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
barBg.BorderSizePixel = 0
barBg.ClipsDescendants = true

-- Progress bar fill
local fill = Instance.new("Frame", barBg)
fill.Size = UDim2.new(0, 0, 1, 0)
fill.Position = UDim2.new(0, 0, 0, 0)
fill.BackgroundColor3 = Color3.fromRGB(255, 165, 0)
fill.BorderSizePixel = 0

-- Percentage
local percent = Instance.new("TextLabel", barBg)
percent.Size = UDim2.new(1, 0, 1, 0)
percent.BackgroundTransparency = 1
percent.TextColor3 = Color3.new(1, 1, 1)
percent.TextScaled = true
percent.Font = Enum.Font.GothamSemibold
percent.Text = "0%"

-- Progress logic
task.spawn(function()
    for i = 1, 100 do
        fill:TweenSize(UDim2.new(i / 100, 0, 1, 0), "Out", "Linear", 1, false)
        percent.Text = i .. "%"
        task.wait(3) -- 3 seconds per percent = 5 minutes total
    end
end)
