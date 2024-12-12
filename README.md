-- Lista de locais para teletransporte
local locations = {
    ["StartIsland"] = Vector3.new(1250, 20, 1350),
    ["JungleIsland"] = Vector3.new(-530, 10, 4100),
    ["DesertIsland"] = Vector3.new(1100, 15, 4200)
}

-- Função para teletransportar jogador
local function teleportTo(player, locationName)
    local location = locations[locationName]
    if location then
        player.Character:SetPrimaryPartCFrame(CFrame.new(location))
    else
        print("Local não encontrado: " .. locationName)
    end
end

-- Comando de teletransporte
game.Players.PlayerAdded:Connect(function(player)
    player.Chatted:Connect(function(message)
        local args = message:split(" ")
        local command = args[1]:lower()
        
        if command == "!tp" and args[2] then
            teleportTo(player, args[2])
        end
    end)
end)
