--SAMUEL SCRIPT
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

windows
local Window = Library.CreateLib("TITLE", "Sentinel")

--tabs
local Tab = Window:NewTab("script")

Section:NewLabel("script")


--comeco

Section:NewButton("ButtonText", "ButtonInfo", function()
    print("-- Auto Farm de level, ESP para ver o nível e vida dos jogadores, e função para ativar/desativar

local AutoFarmEnabled = false
local ESPEnabled = false

-- Função para alternar Auto Farm
local function toggleAutoFarm()
    AutoFarmEnabled = not AutoFarmEnabled
    if AutoFarmEnabled then
        print("Auto Farm Ativado")
        while AutoFarmEnabled do
            -- Lógica de Auto Farm aqui
            -- Adicione aqui a lógica para atacar inimigos e ganhar XP
            wait(1) -- Espera 1 segundo antes de repetir
        end
    else
        print("Auto Farm Desativado")
    end
end

-- Função para alternar ESP
local function toggleESP()
    ESPEnabled = not ESPEnabled
    if ESPEnabled then
        print("ESP Ativado")
        -- Lógica de ESP aqui
        for _, player in pairs(game.Players:GetPlayers()) do
            if player ~= game.Players.LocalPlayer then
                local billboard = Instance.new("BillboardGui", player.Character.Head)
                billboard.Size = UDim2.new(0, 200, 0, 50)
                billboard.Adornee = player.Character.Head
                billboard.AlwaysOnTop = true

                local nameLabel = Instance.new("TextLabel", billboard)
                nameLabel.Size = UDim2.new(1, 0, 1, 0)
                nameLabel.Text = player.Name .. " | Nível: " .. player.Level .. " | Vida: " .. player.Character.Humanoid.Health
                nameLabel.TextColor3 = Color3.new(1, 0, 0)
                nameLabel.BackgroundTransparency = 1
            end
        end
    else
        print("ESP Desativado")
        -- Remover ESP
        for _, player in pairs(game.Players:GetPlayers()) do
            if player.Character.Head:FindFirstChild("BillboardGui") then
                player.Character.Head.BillboardGui:Destroy()
            end
        end
    end
end

-- Bind para ativar/desativar Auto Farm (tecla F)
game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.F then
        toggleAutoFarm()
    end
end)

-- Bind para ativar/desativar ESP (tecla G)
game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.G then
        toggleESP()
    end
end)

print("Script iniciado. Pressione F para Auto Farm e G para ESP.")")
end)


--toggles usavel
Section:NewToggle("ToggleText", "ToggleInfo", function(state)
    if state then
        print("Toggle On")
    else
        print("Toggle Off")
    end
end)

--sladers
Section:NewSlider("SliderText", "SliderInfo", 500, 0, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)
