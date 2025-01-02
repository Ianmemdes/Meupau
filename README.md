local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local function updateHighlights()
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character and not player.Character:FindFirstChild("Highlight") then
            local highlight = Instance.new("Highlight")
            highlight.Adornee = player.Character
            highlight.FillColor = Color3.new(1, 0, 0)
            highlight.FillTransparency = 0.5
            highlight.OutlineTransparency = 1
            highlight.Parent = player.Character
        end
    end
end

Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function()
        updateHighlights()
    end)
end)

while true do
    updateHighlights()
    task.wait(1)
end
