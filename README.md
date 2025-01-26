-- Script de auto farm para Blox Fruits

-- Função para mover o personagem
function moveTo(x, y, z)
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(x, y, z)
end

-- Função para atacar
function attack()
    local player = game.Players.LocalPlayer
    local character = player.Character
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    
    if humanoid then
        humanoid:MoveTo(Vector3.new(0, 0, 0)) -- Define a posição para atacar
        humanoid:MoveToFinished:Wait()
        humanoid:Move(Vector3.new(0, 0, 0))
    end
end

-- Função de auto farm
function autoFarm()
    while true do
        -- Coordenadas de exemplo para diferentes locais de NPCs
        local npcLocations = {
            {x = 100, y = 10, z = 100},
            {x = 150, y = 10, z = 150},
            {x = 200, y = 10, z = 200}
        }
        
        for _, location in ipairs(npcLocations) do
            moveTo(location.x, location.y, location.z)
            attack()
            wait(1) -- Espera 1 segundo entre ataques
        end
    end
end

-- Inicia a função de auto farm
autoFarm()
