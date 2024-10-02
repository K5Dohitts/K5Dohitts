local screenGui = Instance.new("ScreenGui")
screenGui.Name = "Dohitts14HubGui"
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Name = "MainFrame"
frame.Size = UDim2.new(0.5, 0, 0.5, 0)
frame.Position = UDim2.new(0.25, 0, 0.25, 0)
frame.BackgroundColor3 = Color3.fromRGB(0, 0, 255) -- Blue color
frame.Parent = screenGui

local titleLabel = Instance.new("TextLabel")
titleLabel.Name = "TitleLabel"
titleLabel.Size = UDim2.new(1, 0, 0.2, 0)
titleLabel.Position = UDim2.new(0, 0, 0, 0)
titleLabel.Text = "dohitts14 hub"
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255) -- White text
titleLabel.TextScaled = true
titleLabel.BackgroundTransparency = 1
titleLabel.Parent = frame

local infJumpButton = Instance.new("TextButton")
infJumpButton.Name = "InfJumpButton"
infJumpButton.Size = UDim2.new(0.8, 0, 0.2, 0)
infJumpButton.Position = UDim2.new(0.1, 0, 0.3, 0)
infJumpButton.Text = "Toggle Infinite Jump"
infJumpButton.TextColor3 = Color3.fromRGB(255, 255, 255) -- White text
infJumpButton.BackgroundColor3 = Color3.fromRGB(0, 128, 0) -- Green color
infJumpButton.TextScaled = true
infJumpButton.Parent = frame

local flyButton = Instance.new("TextButton")
flyButton.Name = "FlyButton"
flyButton.Size = UDim2.new(0.8, 0, 0.2, 0)
flyButton.Position = UDim2.new(0.1, 0, 0.6, 0)
flyButton.Text = "Toggle Fly"
flyButton.TextColor3 = Color3.fromRGB(255, 255, 255) -- White text
flyButton.BackgroundColor3 = Color3.fromRGB(0, 0, 128) -- Dark blue color
flyButton.TextScaled = true
flyButton.Parent = frame

local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local infJumpEnabled = false
local flyEnabled = false
local flying = false
local bodyVelocity = Instance.new("BodyVelocity")
bodyVelocity.MaxForce = Vector3.new()
bodyVelocity.Velocity = Vector3.new()
bodyVelocity.Parent = character:WaitForChild("HumanoidRootPart")

local function toggleInfiniteJump()
    infJumpEnabled = not infJumpEnabled
    if infJumpEnabled then
        infJumpButton.Text = "Infinite Jump: ON"
        humanoid.JumpPower = 50 -- Set jump power to a high value
    else
        infJumpButton.Text = "Toggle Infinite Jump"
        humanoid.JumpPower = 50 -- Restore default jump power (or adjust as needed)
    end
end

local function toggleFly()
    flyEnabled = not flyEnabled
    if flyEnabled then
        flyButton.Text = "Fly: ON"
        flying = true
        bodyVelocity.MaxForce = Vector3.new(4000, 4000, 4000)
        bodyVelocity.Velocity = Vector3.new(0, 0, 0)
    else
        flyButton.Text = "Toggle Fly"
        flying = false
        bodyVelocity.MaxForce = Vector3.new()
    end
end

infJumpButton.MouseButton1Click:Connect(toggleInfiniteJump)
flyButton.MouseButton1Click:Connect(toggleFly)

-- Update character reference if respawned
player.CharacterAdded:Connect(function(char)
    character = char
    humanoid = character:WaitForChild("Humanoid")
    local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
    bodyVelocity.Parent = humanoidRootPart
end)

game:GetService("RunService").RenderStepped:Connect(function()
    if flying and humanoid and humanoid:GetState() == Enum.HumanoidStateType.Physics then
        bodyVelocity.Velocity = (UserInputService:GetMouse().Unit * 50) -- Adjust flying speed
    end
end)
