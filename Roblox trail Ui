-- Trail and GUI script for player trail customization

-- Services
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")

-- Player
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Variables
local trailEnabled = false
local currentColor = Color3.fromRGB(255, 255, 255)  -- default trail color
local trail = nil

-- GUI creation
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "TrailCustomizerGui"
screenGui.Parent = playerGui
screenGui.ResetOnSpawn = false

-- Main Frame
local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0.25, 0, 0, 30)  -- width 25% of screen, initial height 30 (will auto expand)
mainFrame.Position = UDim2.new(0, 10, 0, 50)
mainFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
mainFrame.BorderSizePixel = 0
mainFrame.Parent = screenGui
mainFrame.AutomaticSize = Enum.AutomaticSize.Y
local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 6)
mainCorner.Parent = mainFrame

-- UIListLayout for mainFrame (vertical, TitleBar then Content)
local mainLayout = Instance.new("UIListLayout")
mainLayout.FillDirection = Enum.FillDirection.Vertical
mainLayout.SortOrder = Enum.SortOrder.LayoutOrder
mainLayout.Padding = UDim.new(0, 5)
mainLayout.Parent = mainFrame

-- Title Bar
local titleBar = Instance.new("Frame")
titleBar.Name = "TitleBar"
titleBar.Size = UDim2.new(1, 0, 0, 30)
titleBar.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
titleBar.BorderSizePixel = 0
titleBar.LayoutOrder = 1
titleBar.Parent = mainFrame

local titleLabel = Instance.new("TextLabel")
titleLabel.Name = "TitleLabel"
titleLabel.Parent = titleBar
titleLabel.Size = UDim2.new(1, -60, 1, 0)
titleLabel.Position = UDim2.new(0, 10, 0, 0)
titleLabel.BackgroundTransparency = 1
titleLabel.Text = "Trail Settings"
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.Font = Enum.Font.Gotham
titleLabel.TextSize = 18
titleLabel.TextXAlignment = Enum.TextXAlignment.Left

local toggleMinimize = Instance.new("TextButton")
toggleMinimize.Name = "ToggleMinimize"
toggleMinimize.Parent = titleBar
toggleMinimize.Size = UDim2.new(0, 30, 0, 30)
toggleMinimize.Position = UDim2.new(1, -30, 0, 0)
toggleMinimize.AnchorPoint = Vector2.new(0, 0)
toggleMinimize.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
toggleMinimize.BorderSizePixel = 0
toggleMinimize.Font = Enum.Font.Gotham
toggleMinimize.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleMinimize.Text = "-"
toggleMinimize.TextSize = 24
toggleMinimize.TextScaled = false
local minCorner = Instance.new("UICorner")
minCorner.CornerRadius = UDim.new(0, 6)
minCorner.Parent = toggleMinimize

-- Content Frame
local contentFrame = Instance.new("Frame")
contentFrame.Name = "ContentFrame"
contentFrame.Size = UDim2.new(1, 0, 0, 0)
contentFrame.BackgroundTransparency = 1
contentFrame.LayoutOrder = 2
contentFrame.Parent = mainFrame
contentFrame.AutomaticSize = Enum.AutomaticSize.Y

local contentLayout = Instance.new("UIListLayout")
contentLayout.FillDirection = Enum.FillDirection.Vertical
contentLayout.SortOrder = Enum.SortOrder.LayoutOrder
contentLayout.Padding = UDim.new(0, 5)
contentLayout.Parent = contentFrame

-- Toggle Trail Button
local toggleButton = Instance.new("TextButton")
toggleButton.Name = "ToggleTrailButton"
toggleButton.Parent = contentFrame
toggleButton.Size = UDim2.new(1, -20, 0, 30)
toggleButton.Position = UDim2.new(0, 10, 0, 0)
toggleButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
toggleButton.BorderSizePixel = 0
toggleButton.Font = Enum.Font.Gotham
toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleButton.TextSize = 18
toggleButton.Text = "Trail: Off"
toggleButton.LayoutOrder = 1
local toggleButtonCorner = Instance.new("UICorner")
toggleButtonCorner.CornerRadius = UDim.new(0, 6)
toggleButtonCorner.Parent = toggleButton

-- Preset Colors Label
local presetLabel = Instance.new("TextLabel")
presetLabel.Name = "PresetLabel"
presetLabel.Parent = contentFrame
presetLabel.Size = UDim2.new(1, -20, 0, 20)
presetLabel.Position = UDim2.new(0, 10, 0, 0)
presetLabel.BackgroundTransparency = 1
presetLabel.Text = "Preset Colors:"
presetLabel.Font = Enum.Font.Gotham
presetLabel.TextSize = 14
presetLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
presetLabel.TextXAlignment = Enum.TextXAlignment.Left
presetLabel.LayoutOrder = 2

-- Preset Colors Frame
local presetFrame = Instance.new("Frame")
presetFrame.Name = "PresetColors"
presetFrame.Parent = contentFrame
presetFrame.Size = UDim2.new(1, -20, 0, 30)
presetFrame.Position = UDim2.new(0, 10, 0, 0)
presetFrame.BackgroundTransparency = 1
presetFrame.LayoutOrder = 3

local presetLayout = Instance.new("UIListLayout")
presetLayout.FillDirection = Enum.FillDirection.Horizontal
presetLayout.SortOrder = Enum.SortOrder.LayoutOrder
presetLayout.Padding = UDim.new(0, 5)
presetLayout.Parent = presetFrame

-- Preset color buttons
local colors = {
    {Name="Red", Color=Color3.fromRGB(255,0,0)},
    {Name="Green", Color=Color3.fromRGB(0,255,0)},
    {Name="Blue", Color=Color3.fromRGB(0,0,255)}
}
for i, col in ipairs(colors) do
    local btn = Instance.new("TextButton")
    btn.Name = col.Name.."Preset"
    btn.Parent = presetFrame
    btn.Size = UDim2.new(0, 30, 1, 0)
    btn.BackgroundColor3 = col.Color
    btn.BorderSizePixel = 0
    btn.LayoutOrder = i
    local btnCorner = Instance.new("UICorner")
    btnCorner.CornerRadius = UDim.new(0, 4)
    btnCorner.Parent = btn
    btn.Font = Enum.Font.Gotham
    btn.Text = ""
    -- Color selection event
    btn.MouseButton1Click:Connect(function()
        currentColor = col.Color
        if trail then
            trail.Color = ColorSequence.new(currentColor)
        end
    end)
end

-- Color Palette Label
local paletteLabel = Instance.new("TextLabel")
paletteLabel.Name = "PaletteLabel"
paletteLabel.Parent = contentFrame
paletteLabel.Size = UDim2.new(1, -20, 0, 20)
paletteLabel.Position = UDim2.new(0, 10, 0, 0)
paletteLabel.BackgroundTransparency = 1
paletteLabel.Text = "Color Palette:"
paletteLabel.Font = Enum.Font.Gotham
paletteLabel.TextSize = 14
paletteLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
paletteLabel.TextXAlignment = Enum.TextXAlignment.Left
paletteLabel.LayoutOrder = 4

-- Color Palette Frame
local paletteFrame = Instance.new("Frame")
paletteFrame.Name = "Palette"
paletteFrame.Parent = contentFrame
paletteFrame.Size = UDim2.new(1, -20, 0, 30)
paletteFrame.Position = UDim2.new(0, 10, 0, 0)
paletteFrame.BackgroundColor3 = Color3.fromRGB(70,70,70)
paletteFrame.BorderSizePixel = 0
paletteFrame.LayoutOrder = 5
local paletteCorner = Instance.new("UICorner")
paletteCorner.CornerRadius = UDim.new(0, 4)
paletteCorner.Parent = paletteFrame

-- Add gradient to palette
local paletteGradient = Instance.new("UIGradient")
paletteGradient.Parent = paletteFrame
paletteGradient.Rotation = 0
paletteGradient.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),
    ColorSequenceKeypoint.new(0.17, Color3.fromRGB(255, 255, 0)),
    ColorSequenceKeypoint.new(0.33, Color3.fromRGB(0, 255, 0)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0, 255, 255)),
    ColorSequenceKeypoint.new(0.67, Color3.fromRGB(0, 0, 255)),
    ColorSequenceKeypoint.new(0.83, Color3.fromRGB(255, 0, 255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 0, 0))
}

-- Hex Input Label
local hexLabel = Instance.new("TextLabel")
hexLabel.Name = "HexLabel"
hexLabel.Parent = contentFrame
hexLabel.Size = UDim2.new(1, -20, 0, 20)
hexLabel.Position = UDim2.new(0, 10, 0, 0)
hexLabel.BackgroundTransparency = 1
hexLabel.Text = "Hex Color (#RRGGBB):"
hexLabel.Font = Enum.Font.Gotham
hexLabel.TextSize = 14
hexLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
hexLabel.TextXAlignment = Enum.TextXAlignment.Left
hexLabel.LayoutOrder = 6

-- Hex Input Field
local hexInput = Instance.new("TextBox")
hexInput.Name = "HexInput"
hexInput.Parent = contentFrame
hexInput.Size = UDim2.new(1, -20, 0, 30)
hexInput.Position = UDim2.new(0, 10, 0, 0)
hexInput.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
hexInput.BorderSizePixel = 0
hexInput.Font = Enum.Font.Gotham
hexInput.TextColor3 = Color3.fromRGB(255, 255, 255)
hexInput.PlaceholderText = "#RRGGBB"
hexInput.TextSize = 18
hexInput.Text = ""
hexInput.LayoutOrder = 7
local hexInputCorner = Instance.new("UICorner")
hexInputCorner.CornerRadius = UDim.new(0, 6)
hexInputCorner.Parent = hexInput

-- Function to update trail color
local function updateTrailColor(color3)
    currentColor = color3
    if trail then
        trail.Color = ColorSequence.new(currentColor)
    end
end

-- Hex input logic
hexInput.FocusLost:Connect(function(enterPressed)
    if enterPressed then
        local hex = hexInput.Text
        if hex:sub(1,1) == "#" then
            hex = hex:sub(2)
        end
        if #hex == 6 then
            local r = tonumber(hex:sub(1,2), 16)
            local g = tonumber(hex:sub(3,4), 16)
            local b = tonumber(hex:sub(5,6), 16)
            if r and g and b then
                updateTrailColor(Color3.fromRGB(r, g, b))
            end
        end
    end
end)

-- Color palette input logic
local function pickColor(pos)
    local absPos = paletteFrame.AbsolutePosition
    local size = paletteFrame.AbsoluteSize
    local x = math.clamp(pos.X - absPos.X, 0, size.X)
    local ratio = x / size.X
    local stops = {
        {pos = 0, color = Color3.fromRGB(255, 0, 0)},
        {pos = 0.17, color = Color3.fromRGB(255, 255, 0)},
        {pos = 0.33, color = Color3.fromRGB(0, 255, 0)},
        {pos = 0.5, color = Color3.fromRGB(0, 255, 255)},
        {pos = 0.67, color = Color3.fromRGB(0, 0, 255)},
        {pos = 0.83, color = Color3.fromRGB(255, 0, 255)},
        {pos = 1, color = Color3.fromRGB(255, 0, 0)}
    }
    for i = 1, #stops-1 do
        local a = stops[i]
        local b = stops[i+1]
        if ratio >= a.pos and ratio <= b.pos then
            local t = (ratio - a.pos) / (b.pos - a.pos)
            local color = a.color:Lerp(b.color, t)
            updateTrailColor(color)
            break
        end
    end
end

local draggingPalette = false
paletteFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        draggingPalette = true
        pickColor(input.Position)
    end
end)
paletteFrame.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        draggingPalette = false
    end
end)
UserInputService.InputChanged:Connect(function(input)
    if draggingPalette and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
        pickColor(input.Position)
    end
end)

-- Toggle minimize content
toggleMinimize.MouseButton1Click:Connect(function()
    contentFrame.Visible = not contentFrame.Visible
    toggleMinimize.Text = contentFrame.Visible and "-" or "+"
end)

-- Function to create trail on character
local function setupTrail(char)
    local head = char:WaitForChild("Head")
    local root = char:WaitForChild("HumanoidRootPart")
    local attachment0 = Instance.new("Attachment")
    attachment0.Name = "TrailAttachment0"
    attachment0.Parent = head
    local attachment1 = Instance.new("Attachment")
    attachment1.Name = "TrailAttachment1"
    attachment1.Parent = root
    trail = Instance.new("Trail")
    trail.Attachment0 = attachment0
    trail.Attachment1 = attachment1
    trail.Color = ColorSequence.new(currentColor)
    trail.Lifetime = 0.5
    trail.Enabled = trailEnabled
    trail.Parent = head
end

-- Player character spawn
player.CharacterAdded:Connect(function(char)
    char:WaitForChild("HumanoidRootPart")
    char:WaitForChild("Head")
    setupTrail(char)
end)
if player.Character then
    setupTrail(player.Character)
end

-- Toggle trail on/off
toggleButton.MouseButton1Click:Connect(function()
    trailEnabled = not trailEnabled
    toggleButton.Text = trailEnabled and "Trail: On" or "Trail: Off"
    if trail then
        trail.Enabled = trailEnabled
    end
end)
