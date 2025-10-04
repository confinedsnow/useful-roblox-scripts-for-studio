-- LocalScript in StarterPlayerScripts

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Create ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "UsernameGeneratorGui"
screenGui.Parent = playerGui

-- Create Label
local label = Instance.new("TextLabel")
label.Parent = screenGui
label.Size = UDim2.new(0.5, 0, 0.15, 0)
label.Position = UDim2.new(0.5, 0, 0.3, 0)
label.AnchorPoint = Vector2.new(0.5, 0.5)
label.BackgroundColor3 = Color3.fromRGB(230, 230, 230)
label.TextColor3 = Color3.new(0, 0, 0)
label.TextSize = 36
label.FontFace = Font.new("rbxassetid://8836875837") -- Lobster font
label.Text = "Click the button below!"

-- Create Button
local button = Instance.new("TextButton")
button.Parent = screenGui
button.Size = UDim2.new(0.3, 0, 0.1, 0)
button.Position = UDim2.new(0.5, 0, 0.6, 0)
button.AnchorPoint = Vector2.new(0.5, 0.5)
button.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
button.TextColor3 = Color3.new(0, 0, 0)
button.TextSize = 24
button.FontFace = Font.new("rbxassetid://8836875837") -- Lobster font
button.Text = "Generate Username"

-- Word lists
local adjectives = {"Epic", "Cool", "Fast", "Lucky", "Sneaky"}
local nouns = {"Dragon", "Ninja", "Pirate", "Wizard", "Warrior"}

math.randomseed(tick())

-- Function to generate a username
local function generateUsername()
    local adj = adjectives[math.random(#adjectives)]
    local noun = nouns[math.random(#nouns)]
    local num = math.random(0, 999)
    return adj .. noun .. num
end

-- Button click event
button.MouseButton1Click:Connect(function()
    label.Text = generateUsername()
end)
