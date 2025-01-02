-- Função para adicionar destaque a todos os jogadores
local function destacarJogadores()
    -- Percorre todos os jogadores no jogo
    for _, player in pairs(game.Players:GetPlayers()) do
        -- Verifica se o jogador tem um personagem
        if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            -- Cria o Highlight
            local highlight = Instance.new("Highlight")
            highlight.Parent = player.Character
            highlight.Adornee = player.Character
            highlight.FillColor = Color3.fromRGB(255, 0, 0)  -- Cor do destaque (vermelho neste caso)
            highlight.FillTransparency = 0.5  -- Transparência do destaque
            highlight.OutlineColor = Color3.fromRGB(255, 255, 0)  -- Cor da borda do destaque (amarelo)
            highlight.OutlineTransparency = 0.5  -- Transparência da borda do destaque
        end
    end
end

-- Chama a função para destacar os jogadores no início
destacarJogadores()

-- Adiciona uma atualização para destacar jogadores sempre que novos jogadores entrarem
game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        -- Aguarda até o personagem estar carregado antes de adicionar o highlight
        wait(1)
        local highlight = Instance.new("Highlight")
        highlight.Parent = character
        highlight.Adornee = character
        highlight.FillColor = Color3.fromRGB(255, 0, 0)  -- Cor do destaque (vermelho neste caso)
        highlight.FillTransparency = 0.5  -- Transparência do destaque
        highlight.OutlineColor = Color3.fromRGB(255, 255, 0)  -- Cor da borda do destaque (amarelo)
        highlight.OutlineTransparency = 0.5  -- Transparência da borda do destaque
    end)
end)
