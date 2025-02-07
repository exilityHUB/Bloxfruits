--// my first auto farm 

local Debug = false

function Script()
    spawn(
        function()
            _G.AfkCooldown = 30
            _G.IsFarming = false
            _G.SelectedAlien = "HeatBlast"
            _G.useZ = true
            _G.useX = true
            _G.useC = true
            _G.useV = true
            _G.CurrentQuest = "MechaDroid"
            _G.FarmMetod = "Level Farm"
            _G.TweenDistance = 5
            _G.SecurityMode = "Kick"
            _G.TweenSetting = "Above"
            _G.VerifFarm = "Max"
            _G.CheckQuest = false
            _G.SelectedPlayer = game.Players.LocalPlayer.Name

            game:GetService("StarterGui"):SetCore(
                "SendNotification",
                {
                    Title = "Quasar Hub",
                    Text = "Execute after game load!",
                    Icon = "rbxthumb://type=AvatarHeadShot&id=" ..
                        game:GetService("Players").LocalPlayer.UserId .. "&w=180&h=180 true",
                    Duration = 5
                }
            )
            if not game.Loaded then
                repeat
                    task.wait()
                until game.Loaded
            end
            local function generatefloat()
                local ScreenGui = Instance.new("ScreenGui")
                local ImageButton = Instance.new("ImageButton")
                local UICorner = Instance.new("UICorner")

                ScreenGui.Parent = game:GetService("CoreGui")
                ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

                ImageButton.Parent = ScreenGui
                ImageButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ImageButton.Position = UDim2.new(0.10615778, 0, 0.16217947, 0)
                ImageButton.Size = UDim2.new(0, 50, 0, 50)
                ImageButton.Image = "rbxassetid://17229118960"
                ImageButton.Draggable = true
                ImageButton.Active = true
                ImageButton.Selectable = true

                UICorner.CornerRadius = UDim.new(0, 30)
                UICorner.Parent = ImageButton

                ImageButton.MouseButton1Click:Connect(
                    function()
                        game:GetService("VirtualInputManager"):SendKeyEvent(true, Enum.KeyCode.End, false, game)
                    end
                )
            end

            if game:GetService("UserInputService").TouchEnabled then
                generatefloat()
            end

            local Missions = {
                Quest1 = {"AddQuest", "QuestM1"},
                Quest2 = {"AddQuest", "QuestM2"},
                Quest3 = {"AddQuest", "QuestM3"},
                Quest4 = {"AddQuest", "QuestM4"},
                Quest5 = {"AddQuest", "QuestM5"},
                Quest6 = {"AddQuest", "QuestM6"},
                Quest7 = {"AddQuest", "QuestM7"},
                Quest8 = {"AddQuest", "QuestM8"},
                Quest9 = {"AddQuest", "QuestM9"}
            }

            local QuestManager = {
                Quests = {
                    QuestM1 = {
                        questType = 1,
                        minPlayerLevel = 0,
                        maxPlayerLevel = 7,
                        enemys = {MiniRobot = 6},
                        reward = {experience = 40, gold = 80},
                        description = "Main - Kill 6 Droids",
                        npcDescription = "The Droids are attacking everyone here. Help us by defeating 6 of them."
                    },
                    QuestM2 = {
                        questType = 1,
                        minPlayerLevel = 7,
                        maxPlayerLevel = 12,
                        enemys = {SpinRobot = 5},
                        reward = {experience = 80, gold = 160},
                        description = "Main - Kill 5 Mechadroid",
                        npcDescription = "The Mechadroid are attacking everyone here. Help us by defeating 5 of them."
                    },
                    QuestM3 = {
                        questType = 1,
                        minPlayerLevel = 13,
                        maxPlayerLevel = 21,
                        enemys = {GiantMechadroid = 1},
                        reward = {experience = 140, gold = 320, DNA = 3},
                        description = "Main - Kill 1 Giant Mechadroid",
                        npcDescription = "The Giant Mechadroid is causing destruction defeat it."
                    },
                    QuestM4 = {
                        questType = 1,
                        minPlayerLevel = 21,
                        maxPlayerLevel = 29,
                        enemys = {GiantFrog = 5},
                        reward = {experience = 200, gold = 300},
                        description = "Main - Kill 5 Giant Frogs",
                        npcDescription = "Yuck! There are several giant frogs in this swamp. Please, get rid of them."
                    },
                    QuestM5 = {
                        questType = 1,
                        minPlayerLevel = 29,
                        maxPlayerLevel = 35,
                        enemys = {TRex = 4},
                        reward = {experience = 250, gold = 500},
                        description = "Main - Kill 4 Giant T-Rex",
                        npcDescription = "Please help us. A Crazy Man created several giant ferocious dinosaurs, I took care of him and help us recover the laboratory."
                    },
                    QuestM6 = {
                        questType = 1,
                        minPlayerLevel = 35,
                        maxPlayerLevel = 40,
                        enemys = {DrAnimal = 1},
                        reward = {experience = 300, gold = 700, DNA = 5},
                        description = "Main - Kill 1 Crazy Scientist",
                        npcDescription = "He's in there. He didn't win a Nobel Prize and decided to destroy the laboratory. Please, defeat him!!"
                    },
                    QuestM7 = {
                        questType = 1,
                        minPlayerLevel = 40,
                        maxPlayerLevel = 45,
                        enemys = {EternalKnight = 7},
                        reward = {experience = 300, gold = 800},
                        description = "Main - Kill 7 Eternal Knight",
                        npcDescription = "Pleaseee, kill some eternal knights they're making me angry!!"
                    },
                    QuestM8 = {
                        questType = 1,
                        minPlayerLevel = 45,
                        maxPlayerLevel = 55,
                        enemys = {SwordsmanEternalKnight = 8},
                        reward = {experience = 350, gold = 450},
                        description = "Main - Kill 8 Swordsman Eternal Knight",
                        npcDescription = "In a distant land, the Star Tear has vanished. The King calls upon heroes to retrieve it. Adventure, magic, and danger await. Will you be able to help?"
                    },
                    QuestM9 = {
                        questType = 1,
                        minPlayerLevel = 55,
                        maxPlayerLevel = 55,
                        enemys = {CrazyClown = 10},
                        reward = {experience = 400, gold = 550},
                        description = "Main - Kill 10 Crazy Clowns",
                        npcDescription = "I will offer you a magic if you neutralize these Crazy Clowns!!"
                    },
                    QuestS1 = {
                        questType = 2,
                        minPlayerLevel = 15,
                        maxPlayerLevel = 90,
                        enemys = {InsectMan = 2},
                        reward = {experience = 2000, gold = 1000, DNA = 50},
                        description = "Secondary - Kill 2 Insect Man",
                        npcDescription = "Hey buddy, we need help! The Insect Man is terrorizing us. Our weapons are useless against him. Please, accept this challenge and put an end to this nightmare!"
                    }
                }
                
            }

            local Codes = {
                [1] = "NewAliens",
                [2] = "Update",
                [3] = "BugsFixed",
                [4] = "SORRYFORDELAY2",
                [5] = "SORRYFORDELAY",
                [6] = "RELEASE"
            }

            local function TpToQuest(Quest)
                local Questi = workspace.ModelMapa.QuestDummy.Main:FindFirstChild(Quest).HumanoidRootPart
                local Distance = (Questi.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
                local Speed = 300
                local CFrameTarget = CFrame.new(Questi.Position.X, Questi.Position.Y, Questi.Position.Z) -- Target CFrame
                local a = game:GetService("TweenService"):Create(
                    game.Players.LocalPlayer.Character.HumanoidRootPart,
                    TweenInfo.new(Distance / Speed, Enum.EasingStyle.Linear),
                    {
                        CFrame = CFrameTarget
                    }
                )
                a:Play()
                a.Completed:Wait()
            end

            local function CheckMission()
                local quests = game:GetService("Players").LocalPlayer.Quests:GetChildren()
                for _, quest in pairs(quests) do
                    if quest:IsA("Folder") then
                        return false
                    end
                end
                return true
            end

            local function TakeQuest(Quest)
                if _G.FarmMetod == "Level Farm" then
                    if _G.CheckQuest then
                        if CheckMission() then
                            game:GetService("ReplicatedStorage").Events.QuestEvent:FireServer(unpack(Quest))
                        end
                    else
                        game:GetService("ReplicatedStorage").Events.QuestEvent:FireServer(unpack(Quest))
                    end
                end
            end

            local function UseSkill(Letter)
                game:GetService("ReplicatedStorage").Events.OmnitrixEvent:FireServer("CastSkill", Letter)
            end

            local function transform(Value)
                if game.Players.LocalPlayer:GetAttribute("battery") >= 40 then
                     game:GetService("ReplicatedStorage").Events.OmnitrixEvent:FireServer("Transform", Value)
               end
            end

            --AUTO FARM

            local function TweenToTarget(P1)
                local Distance = (P1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
                local Speed = 800
                local hp = game.Players.LocalPlayer.Character.Humanoid.Health
                local CFrameTarget
                if _G.TweenSetting == "Above" then
                    if hp < 25 then
                        CFrameTarget = CFrame.new(P1.Position.X, P1.Position.Y + 50, P1.Position.Z)
                    else
                        CFrameTarget = CFrame.new(P1.Position.X, P1.Position.Y + _G.TweenDistance, P1.Position.Z)
                    end
                elseif _G.TweenSetting == "Below" then
                    if hp < 25 then
                        CFrameTarget = CFrame.new(P1.Position.X, P1.Position.Y - 50, P1.Position.Z)
                    else
                        CFrameTarget = CFrame.new(P1.Position.X, P1.Position.Y - _G.TweenDistance, P1.Position.Z)
                    end
                end
                local a =
                    game:GetService("TweenService"):Create(
                    game.Players.LocalPlayer.Character.HumanoidRootPart,
                    TweenInfo.new(Distance / Speed, Enum.EasingStyle.Linear),
                    {
                        CFrame = CFrameTarget
                    }
                )
                a:Play()
                if _G.IsFarming == false then
                    a:Cancel()
                end
                a.Completed:Wait()
            end

            local function AttackEnemy(Enemy)
                TweenToTarget(Enemy)
                if _G.useZ then
                    UseSkill(Enum.KeyCode.Z)
                end
                if _G.useX then
                    UseSkill(Enum.KeyCode.X)
                end
                if _G.useC then
                    UseSkill(Enum.KeyCode.C)
                end
                if _G.useV then
                    UseSkill(Enum.KeyCode.V)
                end
                UseSkill(Enum.UserInputType.MouseButton1)
                task.wait(0.055)
            end

            local function AutoFarm(Instance, EspecialObj, Value, Quest, Alien)
                while _G.IsFarming do
                    pcall(
                        function()
                            if _G.VerifFarm == "Max" then
                                transform(Alien)
                            end
                            TakeQuest(Quest)

                            local enemies = Instance
                            for _, enemy in pairs(enemies) do
                                if enemy:IsA("Model") and enemy:FindFirstChild(EspecialObj) and _G.IsFarming then
                                    transform(Alien)
                                    local Hitbox = enemy:FindFirstChild(EspecialObj)

                                    while enemy:FindFirstChild("Humanoid") and
                                        enemy:FindFirstChild("Humanoid").Health > 0 and
                                        _G.IsFarming do
                                        AttackEnemy(Hitbox)
                                        if _G.VerifFarm == "Max" then
                                            transform(Alien)
                                        end
                                    end
                                    if _G.VerifFarm == "Max" then
                                        transform(Alien)
                                    end
                                    TakeQuest(Quest)
                                end
                            end
                        end
                    )
                    task.wait(0.055)
                end
            end

            local Aliens = {
                HeatBlast = 1,
                Diamond = 2,
                XRL8 = 3,
                GrayMatter = 4,
                FourArms = 5,
                WildMutt = 6,
                Stinkfly = 7,
                Aquatic = 8,
                Upgrade = 9,
                Ghostfreak = 10
            }

            local getalien = function()
                return Aliens[_G.SelectedAlien]
            end

            local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()

            local Window = Fluent:CreateWindow(
                {
                    Title = "Quasar Hub | Benverse",
                    SubTitle = "Made by Frost Team",
                    TabWidth = 145,
                    Size = UDim2.fromOffset(525, 360),
                    Acrylic = false,
                    Theme = "Rose",
                    MinimizeKey = Enum.KeyCode.End
                }
            )

            local Tabs = {
                Main = Window:AddTab({Title = "Main", Icon = "home"}),
                Security = Window:AddTab({Title = "Security", Icon = "rbxassetid://7734056608"}),
                Settings = Window:AddTab({Title = "Settings", Icon = "settings"}),
                Itens = Window:AddTab({Title = "Itens", Icon = "backpack"}),
                Teleport = Window:AddTab({Title = "Teleport", Icon = "map"}),
                pvp = Window:AddTab({Title = "PVP", Icon = "swords"}),
                Misc = Window:AddTab({Title = "Misc", Icon = "rbxassetid://4370318685"})
            }
            Window:SelectTab(1)
            local Options = Fluent.Options
            do
                Tabs.Main:AddParagraph(
                    {
                        Title = "Auto Farm",
                        Content = "Auto Farm Section!"
                    }
                )

                local Dropdown =
                    Tabs.Main:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Auto Farm Mob",
                        Values = {
                            "MechaDroid",
                            "SpinBot",
                            "SpinBot Boss",
                            "Frog",
                            "T-Rex",
                            "Eternal",
                            "Elite Eternal",
                            "Clown"
                        },
                        Multi = false,
                        Default = "MechaDroid"
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        _G.CurrentQuest = Value
                    end
                )

                local Toggle = Tabs.Main:AddToggle("AutoFarmLevel", {Title = "Auto Farm Level", Default = false })

                Toggle:OnChanged(function()
                    _G.IsFarming = Options.AutoFarmLevel.Value
                    while Options.AutoFarmLevel.Value == true do
                        task.wait(0.055)
                        if game.Players.LocalPlayer:GetAttribute("level") >= QuestManager.Quests.QuestM1.minPlayerLevel and game.Players.LocalPlayer:GetAttribute("level") < QuestManager.Quests.QuestM1.maxPlayerLevel then
                            AutoFarm(
                                workspace.Enemys.Instances:GetChildren(),
                                "mechadroid.000_mechadroid.021",
                                _G.IsFarming,
                                Missions.Quest1,
                                getalien()
                            )
                            task.wait(0.055)
                        elseif game.Players.LocalPlayer:GetAttribute("level") >= QuestManager.Quests.QuestM2.minPlayerLevel and game.Players.LocalPlayer:GetAttribute("level") < QuestManager.Quests.QuestM3.maxPlayerLevel then
                            AutoFarm(
                                workspace.Enemys.Instances:GetChildren(),
                                "Circle.000_Circle.006",
                                _G.IsFarming,
                                Missions.Quest2,
                                getalien()
                            )
                            task.wait(0.055)
                        elseif game.Players.LocalPlayer:GetAttribute("level") >= QuestManager.Quests.QuestM4.minPlayerLevel and game.Players.LocalPlayer:GetAttribute("level") < QuestManager.Quests.QuestM4.maxPlayerLevel then
                            AutoFarm(
                                workspace.Enemys.Instances:GetChildren(),
                                "Cube.000_Cube.004",
                                _G.IsFarming,
                                Missions.Quest4,
                                getalien()
                            )
                            task.wait(0.055)
                        elseif game.Players.LocalPlayer:GetAttribute("level") >= QuestManager.Quests.QuestM5.minPlayerLevel and game.Players.LocalPlayer:GetAttribute("level") < QuestManager.Quests.QuestM5.maxPlayerLevel then
                            AutoFarm(
                                workspace.Enemys.Instances:GetChildren(),
                                "TRex_30M_part01",
                                _G.IsFarming,
                                Missions.Quest5,
                                getalien()
                            )
                            task.wait(0.055)
                        elseif game.Players.LocalPlayer:GetAttribute("level") >= QuestManager.Quests.QuestM6.minPlayerLevel and game.Players.LocalPlayer:GetAttribute("level") < QuestManager.Quests.QuestM6.maxPlayerLevel then
                            while _G.IsFarming and Options.AutoFarmLevel.Value do
                                pcall(
                                    function()
                                        transform(getalien())
                                        if _G.FarmMetod == "Level Farm" then
                                            TakeQuest(Missions.Quest7)
                                        end
                                        local enemies = workspace.Enemys.Instances:GetChildren()
                                        for _, enemy in pairs(enemies) do
                                            if _G.FarmMetod == "Level Farm" then
                                                TakeQuest(Missions.Quest7)
                                            end
                                            if
                                                enemy:IsA("Model") and enemy:FindFirstChild("Spear") and
                                                    enemy.Spear:FindFirstChild("Center") and
                                                    _G.IsFarming
                                             then
                                                if _G.FarmMetod == "Level Farm" then
                                                    TakeQuest(Missions.Quest7)
                                                end
                                                transform(getalien())
                                                local Hitbox = enemy.Spear.Center

                                                while enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 and
                                                    _G.IsFarming do
                                                    if _G.FarmMetod == "Level Farm" then
                                                        TakeQuest(Missions.Quest7)
                                                    end
                                                    transform(getalien())
                                                    AttackEnemy(Hitbox)
                                                end
                                                transform(getalien())
                                                if _G.FarmMetod == "Level Farm" then
                                                    TakeQuest(Missions.Quest7)
                                                end
                                            end
                                        end
                                    end
                                )
                                wait(.1)
                            end
                        elseif game.Players.LocalPlayer:GetAttribute("level") >= QuestManager.Quests.QuestM7.minPlayerLevel and game.Players.LocalPlayer:GetAttribute("level") < QuestManager.Quests.QuestM7.maxPlayerLevel then
                            while _G.IsFarming do
                                pcall(
                                    function()
                                        transform(getalien())
                                        if _G.FarmMetod == "Level Farm" then
                                            TakeQuest(Missions.Quest8)
                                        end
                                        local enemies = workspace.Enemys.Instances:GetChildren()
                                        for _, enemy in pairs(enemies) do
                                            if _G.FarmMetod == "Level Farm" then
                                                TakeQuest(Missions.Quest8)
                                            end
                                            if
                                                enemy:IsA("Model") and enemy:FindFirstChild("Sword") and
                                                    enemy.Sword:FindFirstChild("Center") and
                                                    _G.IsFarming
                                             then
                                                if _G.FarmMetod == "Level Farm" then
                                                    TakeQuest(Missions.Quest8)
                                                end
                                                transform(getalien())
                                                local Hitbox = enemy.Sword.Center

                                                while enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 and
                                                    _G.IsFarming do
                                                    if _G.FarmMetod == "Level Farm" then
                                                        TakeQuest(Missions.Quest8)
                                                    end
                                                    transform(getalien())
                                                    AttackEnemy(Hitbox)
                                                end
                                                transform(getalien())
                                                if _G.FarmMetod == "Level Farm" then
                                                    TakeQuest(Missions.Quest8)
                                                end
                                            elseif _G.CurrentQuest == "Clown" then
                                                AutoFarm(
                                                    workspace.Enemys.Instances:GetChildren(),
                                                    "Handle",
                                                    _G.IsFarming,
                                                    Missions.Quest9,
                                                    getalien()
                                                )
                                            end
                                        end
                                    end
                                )
                                wait(0.1)
                                -- end
                            end
                        end
                    end
                end)


                local ToggleLevel =
                    Tabs.Main:AddToggle(
                    "AutoFarm",
                    {Title = "Farm Specific", Description = "Farm Specific Enemy", Default = false}
                )
                ToggleLevel:OnChanged(
                    function(Value)
                        -- while task.wait(0.090) do
                        _G.IsFarming = Value
                        while Value do
                            task.wait(0.55)
                            if _G.CurrentQuest == "MechaDroid" then
                                AutoFarm(
                                    workspace.Enemys.Instances:GetChildren(),
                                    "mechadroid.000_mechadroid.021",
                                    _G.IsFarming,
                                    Missions.Quest1,
                                    getalien()
                                )
                            elseif _G.CurrentQuest == "SpinBot" then
                                AutoFarm(
                                    workspace.Enemys.Instances:GetChildren(),
                                    "Circle.000_Circle.006",
                                    _G.IsFarming,
                                    Missions.Quest2,
                                    getalien()
                                )
                            elseif _G.CurrentQuest == "SpinBot Boss" then
                                AutoFarm(
                                    workspace.Enemys.Instances:GetChildren(),
                                    "obj1.005_obj1.001",
                                    _G.IsFarming,
                                    Missions.Quest3,
                                    getalien()
                                )
                            elseif _G.CurrentQuest == "Frog" then
                                AutoFarm(
                                    workspace.Enemys.Instances:GetChildren(),
                                    "Cube.000_Cube.004",
                                    _G.IsFarming,
                                    Missions.Quest4,
                                    getalien()
                                )
                            elseif _G.CurrentQuest == "T-Rex" then
                                AutoFarm(
                                    workspace.Enemys.Instances:GetChildren(),
                                    "TRex_30M_part01",
                                    _G.IsFarming,
                                    Missions.Quest5,
                                    getalien()
                                )
                            elseif _G.CurrentQuest == "Eternal" then
                                while _G.IsFarming and Value do
                                    pcall(
                                        function()
                                            transform(getalien())
                                            if _G.FarmMetod == "Level Farm" then
                                                TakeQuest(Missions.Quest7)
                                            end
                                            local enemies = workspace.Enemys.Instances:GetChildren()
                                            for _, enemy in pairs(enemies) do
                                                if _G.FarmMetod == "Level Farm" then
                                                    TakeQuest(Missions.Quest7)
                                                end
                                                if
                                                    enemy:IsA("Model") and enemy:FindFirstChild("Spear") and
                                                        enemy.Spear:FindFirstChild("Center") and
                                                        _G.IsFarming
                                                 then
                                                    if _G.FarmMetod == "Level Farm" then
                                                        TakeQuest(Missions.Quest7)
                                                    end
                                                    transform(getalien())
                                                    local Hitbox = enemy.Spear.Center

                                                    while enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 and
                                                        _G.IsFarming do
                                                        if _G.FarmMetod == "Level Farm" then
                                                            TakeQuest(Missions.Quest7)
                                                        end
                                                        transform(getalien())
                                                        AttackEnemy(Hitbox)
                                                    end
                                                    transform(getalien())
                                                    if _G.FarmMetod == "Level Farm" then
                                                        TakeQuest(Missions.Quest7)
                                                    end
                                                end
                                            end
                                        end
                                    )
                                    wait(.1)
                                end
                            elseif _G.CurrentQuest == "Elite Eternal" then
                                while _G.IsFarming do
                                    pcall(
                                        function()
                                            transform(getalien())
                                            if _G.FarmMetod == "Level Farm" then
                                                TakeQuest(Missions.Quest8)
                                            end
                                            local enemies = workspace.Enemys.Instances:GetChildren()
                                            for _, enemy in pairs(enemies) do
                                                if _G.FarmMetod == "Level Farm" then
                                                    TakeQuest(Missions.Quest8)
                                                end
                                                if
                                                    enemy:IsA("Model") and enemy:FindFirstChild("Sword") and
                                                        enemy.Sword:FindFirstChild("Center") and
                                                        _G.IsFarming
                                                 then
                                                    if _G.FarmMetod == "Level Farm" then
                                                        TakeQuest(Missions.Quest8)
                                                    end
                                                    transform(getalien())
                                                    local Hitbox = enemy.Sword.Center

                                                    while enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 and
                                                        _G.IsFarming do
                                                        if _G.FarmMetod == "Level Farm" then
                                                            TakeQuest(Missions.Quest8)
                                                        end
                                                        transform(getalien())
                                                        AttackEnemy(Hitbox)
                                                    end
                                                    transform(getalien())
                                                    if _G.FarmMetod == "Level Farm" then
                                                        TakeQuest(Missions.Quest8)
                                                    end
                                                elseif _G.CurrentQuest == "Clown" then
                                                    AutoFarm(
                                                        workspace.Enemys.Instances:GetChildren(),
                                                        "Handle",
                                                        _G.IsFarming,
                                                        Missions.Quest9,
                                                        getalien()
                                                    )
                                                end
                                            end
                                        end
                                    )
                                    wait(0.1)
                                    -- end
                                end
                            end
                        end
                        while Value do
                            _G.IsFarming = Value
                            wait(1)
                        end
                    end
                )

                local Dropdown =
                    Tabs.Security:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Security Config",
                        Values = {"Kick", "Hop"},
                        Multi = false,
                        Default = "Kick"
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        _G.SecurityMode = Value
                    end
                )

                local MultiDropdown =
                    Tabs.Settings:AddDropdown(
                    "MultiDropdown",
                    {
                        Title = "Use Attacks",
                        Description = "Use Attacks for farming",
                        Values = {"Z", "X", "C", "V"},
                        Multi = true,
                        Default = {"Z", "X", "C", "V"}
                    }
                )

                MultiDropdown:OnChanged(
                    function(Value)
                        _G.useZ = Value.Z
                        _G.useX = Value.X
                        _G.useC = Value.C
                        _G.useV = Value.V
                    end
                )

                local Dropdown =
                    Tabs.Settings:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Auto Farm Mode",
                        Values = {"Level Farm", "No Quest"},
                        Multi = false,
                        Default = "Level Farm"
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        _G.FarmMetod = Value
                    end
                )

                local Dropdown =
                    Tabs.Settings:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Farm Verification Mode",
                        Values = {"Mid", "Max"},
                        Multi = false,
                        Default = "Max"
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        _G.VerifFarm = Value
                    end
                )

                local Toggle = Tabs.Settings:AddToggle("MyToggle", {Title = "Check Quest", Default = false})

                Toggle:OnChanged(
                    function(Value)
                        _G.CheckQuest = Value
                    end
                )

                local Dropdown =
                    Tabs.Settings:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Alien",
                        Values = {
                            "HeatBlast",
                            "Diamond",
                            "XRL8",
                            "GrayMatter",
                            "FourArms",
                            "WildMutt",
                            "Stinkfly",
                            "Aquatic",
                            "Upgrade",
                            "Ghostfreak"
                        },
                        Multi = false,
                        Default = "HeatBlast"
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        _G.SelectedAlien = Value
                    end
                )

                local Dropdown =
                    Tabs.Settings:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Tween Settings",
                        Values = {"Above", "Below"},
                        Multi = false,
                        Default = "Above"
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        _G.TweenSetting = Value
                    end
                )

                local AntiAfk =
                    Tabs.Settings:AddToggle(
                    "AntiAfk",
                    {Title = "Anti Afk", Description = "Anti Idle Kick", Default = true}
                )
                AntiAfk:OnChanged(
                    function(Value)
                        if Value then
                            game:GetService("Players").LocalPlayer.Idled:connect(
                                function()
                                    game:GetService("VirtualUser"):Button2Down(
                                        Vector2.new(0, 0),
                                        workspace.CurrentCamera.CFrame
                                    )
                                    wait(1)
                                    game:GetService("VirtualUser"):Button2Up(
                                        Vector2.new(0, 0),
                                        workspace.CurrentCamera.CFrame
                                    )
                                end
                            )
                        end
                    end
                )

                local Slider =
                    Tabs.Settings:AddSlider(
                    "Slider",
                    {
                        Title = "Distance",
                        Description = "Tween Distance",
                        Default = 5,
                        Min = 0,
                        Max = 50,
                        Rounding = 2,
                        Callback = function(Value)
                            _G.TweenDistance = Value
                        end
                    }
                )

                Slider:OnChanged(
                    function(Value)
                        _G.TweenDistance = Value
                    end
                )

                local Toggle = Tabs.Itens:AddToggle("MyToggle", {Title = "Auto Roll Skin", Default = false})

                Toggle:OnChanged(
                    function(Value)
                        while Value do
                            game:GetService("ReplicatedStorage").Events.SkinEvent:FireServer("SummonSkin")
                            task.wait(1.5)
                        end
                    end
                )

                local Dropdown =
                    Tabs.Teleport:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Quests",
                        Values = {
                            "None",
                            "QuestM1",
                            "QuestM2",
                            "QuestM3",
                            "QuestM4",
                            "QuestM5",
                            "QuestM6",
                            "QuestM7",
                            "QuestM8",
                            "QuestM9"
                        },
                        Multi = false,
                        Default = "None"
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        if Value ~= "None" then
                            TpToQuest(Value)
                        end
                    end
                )

                Tabs.Teleport:AddButton(
                    {
                        Title = "AFK Mode",
                        Description = "Teleport you to AFK",
                        Callback = function()
                            game:GetService("TeleportService"):Teleport(16810818923)
                        end
                    }
                )

                Tabs.Misc:AddButton(
                    {
                        Title = "Redeem Codes",
                        Description = "Redeem all Codes",
                        Callback = function()
                            for _, code in pairs(Codes) do
                                game:GetService("ReplicatedStorage").Events.CodesEvent:FireServer("GetCode", code)
                            end
                        end
                    }
                )

                local Slider =
                    Tabs.Misc:AddSlider(
                    "Slider",
                    {
                        Title = "Speed",
                        Description = "Set Player WalkSpeed",
                        Default = game.Players.LocalPlayer.Character.Humanoid.WalkSpeed,
                        Min = 16,
                        Max = 300,
                        Rounding = 1,
                        Callback = function(Value)
                            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
                        end
                    }
                )

                Slider:OnChanged(
                    function(Value)
                        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
                    end
                )

                local Slider =
                    Tabs.Misc:AddSlider(
                    "Slider",
                    {
                        Title = "Jump",
                        Description = "Set Player JumpPower",
                        Default = game.Players.LocalPlayer.Character.Humanoid.JumpPower,
                        Min = 16,
                        Max = 300,
                        Rounding = 1,
                        Callback = function(Value)
                            game.Players.LocalPlayer.Character.Humanoid.JumpPower = Value
                        end
                    }
                )

                Slider:OnChanged(
                    function(Value)
                        game.Players.LocalPlayer.Character.Humanoid.JumpPower = Value
                    end
                )

                local function getplayers()
                    local players = {}

                    for i, v in ipairs(game.Players:GetPlayers()) do
                        if (v ~= game.Players.LocalPlayer) then
                            table.insert(players, v.Name)
                        end
                    end
                    return players
                end

                local Dropdown =
                    Tabs.pvp:AddDropdown(
                    "Dropdown",
                    {
                        Title = "Players",
                        Values = getplayers(),
                        Multi = false,
                        Default = 1
                    }
                )

                Dropdown:OnChanged(
                    function(Value)
                        _G.SelectedPlayer = Value
                    end
                )

                local Toggle = Tabs.pvp:AddToggle("MyToggle", {Title = "Kill Player", Default = false})

                Toggle:OnChanged(
                    function(Value)
                        _G.IsFarming = true
                        while workspace[_G.SelectedPlayer].Humanoid.Health > 0 and Value do
                            transform(getalien())
                            local TpPart =
                                workspace[_G.SelectedPlayer]:FindFirstChildOfClass("Part") or
                                workspace[_G.SelectedPlayer]:FindFirstChildOfClass("MeshPart") or
                                workspace[_G.SelectedPlayer].Parts:FindFirstChildOfClass("Part") or
                                workspace[_G.SelectedPlayer].Parts:FindFirstChildOfClass("Part")
                            AttackEnemy(TpPart)
                        end
                        _G.IsFarming = false
                    end
                )
            end
        end
    )
end

pcall(Script)--// This need a URGENT Rewrite btw

getgenv().thealienx = nil

local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "Quasar-Hub | OMNI X", HidePremium = false, SaveConfig = true, Icon = "rbxassetid://16452461925", ConfigFolder = "FrostHub", IntroEnabled = true, IntroText = "Welcome ".. game.Players.LocalPlayer.Name.. " to Quasar Hub"})
function Teleportplayer1(x, y, z)
game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(x, y, z))
end

function TweenTp(x, y, z, speed)
  local tween_s = game:GetService('TweenService')
  local tweeninfo = TweenInfo.new(speed, Enum.EasingStyle.Linear)
  local lp = game.Players.LocalPlayer
    local cf = CFrame.new(Vector3.new(x, y, z))
    local a = tween_s:Create(lp.Character.HumanoidRootPart, tweeninfo, {CFrame = cf})
    a:Play()
end

if _G.device == "Mobile" then
    local Revert = {
        [1] = "/otimizar ",
        [2] = "All"
    }
    
    game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(unpack(Revert))
    
    OrionLib:MakeNotification({
        Name = "exility Hub",
        Content = "o seu jogo foi otimizado para mobile",
        Image = "rbxassetid://4483345998",
        Time = 5
    })
end

local Tab = Window:MakeTab({
	Name = "All Aliens",
	Icon = "rbxassetid://12974446859",
	PremiumOnly = false

})

local Section = Tab:AddSection({
	Name = "Aliens Prototype/Recalibrated/Super"
})

local alienx = {
    [1] = "AF",
    [2] = "alienx",
    [3] = 240,
    [4] = true
}

--------ultratrix aliens----------

local fogofatuos = {
    [1] = "UA",
    [2] = "uswampfire",
    [3] = 360,
    [4] = true
}

local ecoecos = {
    [1] = "UA",
    [2] = "uechoecho",
    [3] = 360,
    [4] = true
}

local enormossauros = {
    [1] = "UA",
    [2] = "uhumungosaur",
    [3] = 360,
    [4] = true
}

local arraiajatos = {
    [1] = "UA",
    [2] = "ujetray",
    [3] = 360,
    [4] = true
}

local friagems = {
    [1] = "UA",
    [2] = "ubigchill",
    [3] = 360,
    [4] = true
}

local cromaticos = {
    [1] = "UA",
    [2] = "uchromastone",
    [3] = 360,
    [4] = true
}

local artropodes = {
    [1] = "UA",
    [2] = "ubrainstorm",
    [3] = 360,
    [4] = true
}

local gosmas = {
    [1] = "UA",
    [2] = "ugoop",
    [3] = 360,
    [4] = true
}

local insectoides = {
    [1] = "UA",
    [2] = "stinkfly",
    [3] = 360,
    [4] = true,
    [5] = true
}

local function transform(var)
    game:GetService("ReplicatedStorage").Remotes.AlienMorph:FireServer(unpack(var))
end

local alienxs = {
    [1] = "UA",
    [2] = "alienx",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local mamacoaranhas = {
    [1] = "UA",
    [2] = "spidermonkey",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local estrelapolares = {
    [1] = "UA",
    [2] = "lodestar",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local nanomechs = {
    [1] = "UA",
    [2] = "nanomech",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local fourarmsS = {
    [1] = "UA",
    [2] = "fourarms",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local MCinzentaS = {
    [1] = "UA",
    [2] = "graymatter",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}


local RathS = {
    [1] = "UA",
    [2] = "rath",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local ChamaS = {
    [1] = "UA",
    [2] = "heatblast",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local DiamanteS = {
    [1] = "UA",
    [2] = "diamond",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}



local BestaS = {
    [1] = "UA",
    [2] = "wildmutt",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local gigantes = {
    [1] = "UA",
    [2] = "waybig",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

local Xrl8S = {
    [1] = "UA",
    [2] = "xrl8",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = true
}

local evilgigantes = {
    [1] = "UA",
    [2] = "evilwaybig",
    [3] = 0,
    [4] = true,
}

local boladecanhaoS = {
    [1] = "UA",
    [2] = "cannonbolt",
    [3] = 0,
    [4] = true,
    [5] = true,
    [6] = false
}

--------------aliens clÃ¡ssico--------------



local Chama = {
    [1] = "OS",
    [2] = "heatblast",
    [3] = 120,
    [4] = true
}

local Besta = {
    [1] = "OS",
    [2] = "wildmutt",
    [3] = 120,
    [4] = true
}

local Diamante = {
    [1] = "OS",
    [2] = "diamond",
    [3] = 120,
    [4] = true
}

local Xrl8 = {
    [1] = "OS",
    [2] = "xrl8",
    [3] = 120,
    [4] = true
}

local MCinzenta = {
    [1] = "OS",
    [2] = "graymatter",
    [3] = 120,
    [4] = true
}

local fourarms = {
    [1] = "OS",
    [2] = "fourarms",
    [3] = 120,
    [4] = true
}

local insectoid = {
    [1] = "OS",
    [2] = "stinkfly",
    [3] = 120,
    [4] = true
}
local Aquatico = {
    [1] = "OS",
    [2] = "ripjaws",
    [3] = 120,
    [4] = true
}

local ultrat = {
    [1] = "OS",
    [2] = "ultrat",
    [3] = 120,
    [4] = true
}

local fantasmatico = {
    [1] = "OS",
    [2] = "ghostfreak",
    [3] = 120,
    [4] = true
}

local boladecanhao = {
    [1] = "OS",
    [2] = "cannonbolt",
    [3] = 120,
    [4] = true
}

local siposelvagem = {
    [1] = "OS",
    [2] = "wildvine",
    [3] = 120,
    [4] = true
}

local lobisben = {
    [1] = "OS",
    [2] = "blitzwolfer",
    [3] = 120,
    [4] = true
}

local benmumia = {
    [1] = "OS",
    [2] = "snareoh",
    [3] = 120,
    [4] = true
}

local frankenstrike = {
    [1] = "OS",
    [2] = "frankenstrike",
    [3] = 120,
    [4] = true
}

local glutao = {
    [1] = "OS",
    [2] = "upchuck",
    [3] = 120,
    [4] = true
}

local megaolhos = {
    [1] = "OS",
    [2] = "eyeguy",
    [3] = 120,
    [4] = true
}

local gigante = {
    [1] = "OS",
    [2] = "waybig",
    [3] = 120,
    [4] = true
}

local ditto = {
    [1] = "OS",
    [2] = "ditto",
    [3] = 120,
    [4] = true
}

local feedback = {
    [1] = "OS",
    [2] = "feedback",
    [3] = 120,
    [4] = true
}

local chocante = {
    [1] = "OS",
    [2] = "buzzshock",
    [3] = 120,
    [4] = true
}

local iguanartica = {
    [1] = "OS",
    [2] = "articguana",
    [3] = 120,
    [4] = true
}

local cuspidor = {
    [1] = "OS",
    [2] = "spitter",
    [3] = 120,
    [4] = true
}

local contratempo = {
    [1] = "OS",
    [2] = "clockwork",
    [3] = 120,
    [4] = true
}

-----------------Recalibrado--------------

	local fogofatuo = {
    [1] = "AF",
    [2] = "swampfire",
    [3] = 240,
    [4] = true
}

local echoecho = {
    [1] = "AF",
    [2] = "echoecho",
    [3] = 240,
    [4] = true
}

local enormossauro = {
    [1] = "AF",
    [2] = "humungosaur",
    [3] = 240,
    [4] = true
}

local arraiajato = {
    [1] = "AF",
    [2] = "jetray",
    [3] = 240,
    [4] = true
}

local friagem = {
    [1] = "AF",
    [2] = "bigchill",
    [3] = 240,
    [4] = true
}

local cromatico = {
    [1] = "AF",
    [2] = "chromastone",
    [3] = 240,
    [4] = true
}

local artropode = {
    [1] = "AF",
    [2] = "brainstorm",
    [3] = 240,
    [4] = true
}

local macacoaranha = {
    [1] = "AF",
    [2] = "spidermonkey",
    [3] = 240,
    [4] = true
}

local gosma = {
    [1] = "AF",
    [2] = "goop",
    [3] = 240,
    [4] = true
}

local estrelapolar = {
    [1] = "AF",
    [2] = "lodestar",
    [3] = 240,
    [4] = true
}

local rath = {
    [1] = "AF",
    [2] = "rath",
    [3] = 240,
    [4] = true
}

local nanomech = {
    [1] = "AF",
    [2] = "nanomech",
    [3] = 240,
    [4] = true
}

local Revert = {
    [1] = false
}

----------Transformar nos aliens----------
Tab:AddDropdown({
	Name = "Prototype",
	Default = "Nothing",
	Options = {"Nothing", "HeatBlast", "Beast", "DiamondHead", "XRL8", "Gray matter", "Four arms", "Insectoid", "Aquatic", "Ultra T", "Ghost Freak", "Cannon ball", "Wild Vine", "BlitzWolfer", "Mummy", "Frankstein", "upchuck", "Mega Eyes", "Giant", "Ditto", "FeedBack", "buzzshock", "articguana", "spitter", "Clockwork"},
	Callback = function(Alien)
		if Alien == "HeatBlast" then
		transform(Chama)
		elseif Alien == "Beast" then
		transform(Besta)
		elseif Alien == "DiamondHead" then
		transform(Diamante)
		elseif Alien == "XRL8" then
		transform(Xrl8)
		elseif Alien == "Gray matter" then
		transform(MCinzenta)
		elseif Alien == "Four arms" then
		transform(fourarms)
		elseif Alien == "Insectoid" then
		transform(insectoid)
		elseif Alien == "Aquatic" then
		transform(Aquatico)
		elseif Alien == "Ultra T" then
		transform(ultrat)
		elseif Alien == "Ghost Freak" then
		transform(fantasmatico)
		elseif Alien == "Cannon ball" then
		transform(boladecanhao)
		elseif Alien == "Wild Vine" then
		transform(siposelvagem)
		elseif Alien == "BlitzWolfer" then
		transform(lobisben)
        elseif Alien == "Mummy" then
        transform(benmumia)
        elseif Alien == "Frankstein" then
        transform(benmumia)
        elseif Alien == "upchuck" then
        transform(glutao)
        elseif Alien == "Mega Eyes" then
        transform(megaolhos)
        elseif Alien == "Giant" then
        transform(gigante)
        elseif Alien == "Ditto" then
        transform(ditto)
        elseif Alien == "FeedBack" then
        transform(feedback)
        elseif Alien == "buzzshock" then
        transform(chocante)
        elseif Alien == "articguana" then
        transform(iguanartica)
        elseif Alien == "spitter" then
        transform(cuspidor)
        elseif Alien == "Clockwork" then
        transform(contratempo)
        end
	end    
})

Tab:AddDropdown({ 
	Name = "Recalibrated", 
	Default = "Nothing",
 	Options = {"Nothing", "Swampfire", "Echo Echo", "Humungosaur", "Jetray", "Bigchill", "Chromastone", "Brainstorm", "Spidermonkey", "Goop", "Lodestar", "Rath", "Nanomech"},
 	Callback = function(Alien) 		
         if Alien == "Swampfire" then
            transform(fogofatuo)
         elseif Alien == "Echo Echo" then
            transform(echoecho)
          elseif Alien == "Humungosaur" then
             transform(enormossauro)
          elseif Alien == "Jetray" then
          transform(arraiajato)
          elseif Alien == "Bigchill" then
          transform(friagem)
          elseif Alien == "Chromastone" then
          transform(cromatico)
          elseif Alien == "Brainstorm" then
          transform(artropode)
          elseif Alien == "Spidermonkey" then
          transform(macacoaranha)
          elseif Alien == "Goop" then
          transform(gosma)
          elseif Alien == "Lodestar" then
          transform(estrelapolar)
          elseif Alien == "Rath" then
          transform(rath)
          elseif Alien == "Nanomech" then
          transform(nanomech)
         end
  end 
})

Tab:AddDropdown({
	Name = "Ultimatrix",
	Default = "Nothing",
	Options = {"Nothing", "Ultimate Swamp Fire", "Ultimate Echo Echo", "Ultimate Humungosaur", "Ultimate Jetray", "Ultimate BigChill", "Ultimate Chromastone", "Ultimate Brainstorm", "Ultimate Spidermonkey", "Ultimate Goop", "Ultimate Lodestar", "Ultimate Nanomech", "Ultimate Alien X", "Ultimate GrayMatter", "Ultimate Rath", "Ultimate HeatBlast", "Ultimate DiamondHead", "Ultimate WildMutt", "Ultimate WayBig", "Ultimate StinkyFly", "Ultimate XRL8", "Ultimate Four Arms", "Ultimate Cannonbolt"},
	Callback = function(Alien)
		if Alien == "Ultimate Swamp Fire" then
		transform(fogofatuos)
		elseif Alien == "Ultimate Echo Echo" then
		transform(ecoecos)
		elseif Alien == "Ultimate Humungosaur" then
		transform(enormossauros)
		elseif Alien == "Ultimate Jetray" then
		transform(arraiajatos)
		elseif Alien == "Ultimate BigChill" then
		transform(friagems)
		elseif Alien == "Ultimate Chromastone" then
		transform(cromaticos)
		elseif Alien == "Ultimate Brainstorm" then
		transform(artropodes)
		elseif Alien == "Ultimate Spidermonkey" then
		transform(mamacoaranhas)
		elseif Alien == "Ultimate Goop" then
		transform(gosmas)
		elseif Alien == "Ultimate Lodestar" then
		transform(estrelapolares)
		elseif Alien == "Ultimate Nanomech" then
		    transform(nanomechs)
        elseif Alien == "Ultimate GrayMatter" then
            transform(MCinzentaS)
        elseif Alien == "Ultimate Rath" then
            transform(RathS)
        elseif Alien == "Ultimate HeatBlast" then
            transform(ChamaS)
        elseif Alien == "Ultimate DiamondHead" then
            transform(DiamanteS)
        elseif Alien == "Ultimate WildMutt" then
            transform(BestaS)
        elseif Alien == "Ultimate WayBig" then
           transform(gigantes)
           elseif Alien == "Ultimate StinkyFly" then
               transform(insectoides)
            elseif Alien == "Ultimate XRL8" then
               transform(Xrl8S)
             elseif Alien == "Ultimate Four Arms" then
               transform(fourarmsS)
             elseif Alien == "Ultimate Cannonbolt" then
                transform(boladecanhaoS)
		end
	end    
})

Tab:AddDropdown({
	Name = "Extras",
	Default = "None",
	Options = {"None", "Alien X",  "Ultimate Alien X", "Evil WayBig"},
	Callback = function(alien)
		if alien == "Alien X" then
		   transform(alienx)
		   getgenv().thealienx = "Normal"
	     elseif alien == "Ultimate Alien X" then
	        transform(alienxs)
	        getgenv().thealienx = "Ultimate"
	     elseif alien == "Evil WayBig" then
	        transform(evilgigantes)
     	end
	end    
})


Tab:AddButton({
	Name = "UnMorph",
	Callback = function()
    game:GetService("ReplicatedStorage").Remotes.UnMorph:FireServer(unpack(Revert))
    getgenv().thealienx = nil
  end
})


local Tab = Window:MakeTab({
	Name = "Teleport",
	Icon = "rbxassetid://7733992829",
	PremiumOnly = false
})

Tab:AddDropdown({
    Name = "Raids",
    Default = "Nenhuma",
    Options = {"Nenhuma", "Vilgax 1", "Animal Doctor", "Eternals", "Vilgax 2", "DNAliens", "WayBig",  "Altiare Potis"},
    Callback = function(raid)
        local locais = {
            Vilgax = {10811, -143, 597, 10}, -- level 25
            Animal = {5249, -142, -2310, 10}, -- level 100
            eternos = {1479, -142, 3280, 10}, -- level 250
            RaidVilgax2 = {-4427, 5715, 17335, 10}, -- level 400
            DNAliens = { 11477, 303, 3506, 10}, -- level 750
            WayBig = {1000000, 25000, 1000000, 15} --1500
        }

        local informacoes = {
            maxlevel = game:GetService("ReplicatedStorage"):FindFirstChild("Valores").MaxLevel.Value,
            LevelAtual = game:GetService("Players").LocalPlayer.atributos:WaitForChild("Level").Value,
            classe = game:GetService("Players").LocalPlayer.atributos:WaitForChild("CLASSPLAYER").Value
        }

        local char = game:GetService("Players").LocalPlayer.Character
        if raid == "Vilgax 1" then
            if informacoes.LevelAtual >= 25 then
                TweenTp(unpack(locais.Vilgax))
            else
                OrionLib:MakeNotification({
                    Title = "Quasar-Hub",
                    Text = "To access this area or content, you need the level:25 Your current level is ".. informacoes.LevelAtual,
                    Icon = "rbxassetid://4483345998",
                    Duration = 5
                })
            end
        elseif raid == "Animal Doctor" then
            if informacoes.LevelAtual >= 100 then
                TweenTp(unpack(locais.Animal))
            else
                OrionLib:MakeNotification({
                    Title = "Quasar-Hub",
                    Text = "To access this area or content, you need the level:100 Your current level is ".. informacoes.LevelAtual,
                    Icon = "rbxassetid://4483345998",
                    Duration = 5
                })
            end
        elseif raid == "Eternals" then
            if informacoes.LevelAtual >= 250 then
                TweenTp(unpack(locais.eternos))
            else
                OrionLib:MakeNotification({
                    Title = "Quasar-Hub",
                    Text = "To access this area or content, you need the level:250 Your current level is ".. informacoes.LevelAtual,
                    Icon = "rbxassetid://4483345998",
                    Duration = 5
                })
            end
        elseif raid == "Vilgax 2" then
            if informacoes.LevelAtual >= 400 then
                TweenTp(unpack(locais.RaidVilgax2))
            else
                OrionLib:MakeNotification({
                    Title = "Quasar-Hub",
                    Text = "To access this area or content, you need the level:400 Your current level is ".. informacoes.LevelAtual,
                    Icon = "rbxassetid://4483345998",
                    Duration = 5
                })
            end
        elseif raid == "DNAliens" then
            if informacoes.LevelAtual >= 750 then
                TweenTp(unpack(locais.DNAliens))
            else
                OrionLib:MakeNotification({
                    Title = "Quasar-Hub",
                    Text = "To access this area or content, you need the level:750. Your current level is ".. informacoes.LevelAtual,
                    Icon = "rbxassetid://4483345998",
                    Duration = 5
                })
            end
        elseif raid == "WayBig" then
            TweenTp(unpack(locais.WayBig))
        elseif raid == "Altiare Potis" then
            if informacoes.LevelAtual >= 1500 then
            TweenTp(-125128,26627,24639, 5)
            else
                OrionLib:MakeNotification({
                    Title = "exility Hub",
                    Text = "To access this area or content, you need the level:1500. Your current level is ".. informacoes.LevelAtual,
                    Icon = "rbxassetid://4483345998",
                    Duration = 5
                })
            end
        end
    end
})


Tab:AddDropdown({
	Name = "Direct",
	Default = "Nenhum",
	Options = {"Nenhum", "Main Game", "Raid Ultratrix", "Raid Alien X"},
	Callback = function(experiencia)
        
		if experiencia == "Main Game" then
		game:GetService("TeleportService"):Teleport(5210095481)
		elseif experiencia == "Raid Ultratrix" then
		game:GetService("TeleportService"):Teleport(16091658541) 
		elseif experiencia == "Raid Alien X" then
		game:GetService("TeleportService"):Teleport(16029997375)
		end
	end    
})

Tab:AddDropdown({
	Name = "UltraTrix Parts",
	Default = "Nenhuma",
	Options = {"Nenhuma", "Bracelet", "Core"},
	Callback = function(peca)
		if peca == "Bracelet" then
		TweenTp(-5091, 6, -8426, 5)
		elseif peca == "Core" then
		TweenTp(89046, -272, -42247, 5)
		end
	end    
})

Tab:AddDropdown({
	Name = "Altiare Potis",
	Default = "Nothing",
	Options = {"Nothing", "Mountain","Galvan Prime", "Unknown", "Pisciss", "Moon", "Beach", "Magma and Ice", "Mars"},
	Callback = function(locale)
		if locale == "Mountain" then
            TweenTp(5644,719,-8382, 3)
        elseif locale == "Galvan Prime" then
            TweenTp(88488,-117,-42276, 3)
        elseif locale == "Unknown" then
            TweenTp(-68280,29453,32773, 5)
        elseif locale == "Pisciss" then
            TweenTp(-1538,-192,-71868, 5)
        elseif locale == "Moon" then
            TweenTp(-1253,7,50409, 5)
        elseif locale == "Beach" then
            TweenTp(11874,-145,-3694, 3)
        elseif locale == "Magma and Ice" then
            TweenTp(-1053,7,90790, 5)
        elseif locale == "Mars" then
            TweenTp(64854,7,66908, 5)
        end
	end    
})


Tab:AddButton({
	Name = "Teleport Lugar Raid Diagon",
	Callback = function()
Teleportplayer1(-7185, -1162, -4509)	
  	end    
})

Tab:AddButton({
Name = "Castle",
Callback = function()
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(2453, 299, -6988)))
end
})

Tab:AddDropdown({
	Name = "Alien X Parts",
	Default = "Nenhuma",
	Options = {"Nenhuma", "Part 1", "Part 2", "Part 3", "Cube"},
	Callback = function(peca)
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
		if peca == "Part 1" then
            character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(-1916, -895, 933)))
        elseif peca == "Part 2" then
            character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(-743, -193, -73714)))
        elseif peca == "Part 3" then
            character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(94, 144, 92835)))
        elseif peca == "Cube" then
            character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(101218, 1251, -1666)))
        end
	end    
})

local plr = game.Players.LocalPlayer
local char = plr.Character

Tab:AddDropdown({
	Name = "Omnitrix",
	Default = "Nenhum",
	Options = {"Nenhum", "Prototype", "Recalibrated/reset class"},
	Callback = function(rolex)
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
		if rolex == "Prototype" then
            character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(-392, -44, -4353)))
        elseif rolex == "Recalibrated/reset class" then
            character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(419, 35290, 244)))
        end
	end    
})

--------plataforma----------

local Section = Tab:AddSection({Name = "Platform"})

Tab:AddButton({
Name = "Platform",
Callback = function()
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(0, 100000, 0)))
local platform = Instance.new("Part")
platform.Size = Vector3.new(100, 1, 100) -- 2
platform.Position = character.PrimaryPart.Position - Vector3.new(0, 5, 0)
platform.Anchored = true
platform.Parent = game.Workspace
end})

local Tab = Window:MakeTab({
	Name = "Auto",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})


local Section = Tab:AddSection({
	Name = "Kill Aura, Auto save and Auto Raid"
})
Tab:AddToggle({
	Name = "Kill Aura",
	Default = false,
	Callback = function(Value)
		while Value == true do
              game:GetService("ReplicatedStorage").Remotes.PunchDummy:FireServer(150,999)
              wait(0.1)
		end
	end    
})




---------auto save----------

Tab:AddToggle({
	Name = "Auto Save",
	Default = false,
	Callback = function(Value)

		while Value == true do

			game:GetService("ReplicatedStorage").Remotes.SaveAll:FireServer()

                        wait(100)
		end
	end    
})

Tab:AddToggle({
	Name = "Auto Perm Alien X",
	Default = false,
	Callback = function(Value)
	getgenv().autoperm = Value
	end    
})

---------auto kill raid eternos-----------

local Section = Tab:AddSection({
	Name = "Auto Raid"
})

Tab:AddToggle({
    Name = "Auto Raid Dr Animal",
    Default = false,
    Callback = function(Value)
    if Value then
        local HumanoidRootPart = game.Players.LocalPlayer.Character.HumanoidRootPart
                    TweenTp(5214.32763671875, -125.01702117919922, -2312.417724609375, 0.5)
                   -- wait(0.25)
                    while Value do
                    wait(0.5)
                    HumanoidRootPart.Anchored = true
                    game:GetService("ReplicatedStorage").Remotes.PunchDummy:FireServer(150,999)
                    end
             else
                    game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
                    
     end
    end
})

Tab:AddToggle({
	Name = "Auto Raid Vilgax 2",
	Default = false,
	Callback = function(Value)
	
	if Value == true then
	TweenTp(-4600.39794921875, 6110, 17077.130859375, 0,5)
	end
	
	while Value do
		if Value == true then
		     game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
	       	wait(0.5)
		     game:GetService("ReplicatedStorage").Remotes.PunchDummy:FireServer(150,999)
		else
	  	game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
		end
	end
	end    
})

local Noclip = nil
        local Clip = nil
        
        local function noclip()
            Clip = false
            local function Nocl()
                if Clip == false and game.Players.LocalPlayer.Character ~= nil then
                    for _,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                        if v:IsA('BasePart') and v.CanCollide and v.Name ~= floatName then
                            v.CanCollide = false
                        end
                    end
                end
                wait(0.21)
            end
            Noclip = game:GetService('RunService').Stepped:Connect(Nocl)
        end
        
        local function clip()
            if Noclip then Noclip:Disconnect() end
            Clip = true
        end
        
        

Tab:AddButton({
	Name = "Auto Raid DNAliens",
	Callback = function()
      		TweenTp(11487.5859375, 662.8220825195312, 3102.034423828125, 0.5)
      noclip()
     -- transform(cromaticos))
               game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
                while wait(0.5) do
            
                game:GetService("ReplicatedStorage").Remotes.PunchDummy:FireServer(150,999)
          	end    
end
})

Tab:AddButton({
Name = "Auto Raid Eternals",
Callback = function()
TweenTp(1449.2724609375, -116.6343994140625, 3390.023193359375, 0.5)
game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
while wait(0.5) do
game:GetService("ReplicatedStorage").Remotes.PunchDummy:FireServer(150,999)
end
end})

local function KillAlbedo()
local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    
    local posantes = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
    character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(-125128, 26672.4, 24664.3)))
    
    local platform = Instance.new("Part")
    platform.Size = Vector3.new(10, 1, 10) -- 2
    platform.Position = character.PrimaryPart.Position - Vector3.new(0, 5, 0)
    platform.Anchored = true
    platform.Parent = game.Workspace
    wait(1)
    game:GetService("ReplicatedStorage").Remotes.AlienMorph:FireServer(unpack(alienx))
    wait(2)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(1)
    game:GetService("ReplicatedStorage").AliensPowerRemotes.alienx.Explos:FireServer() 
    wait(5)
      game:GetService("ReplicatedStorage").Remotes.UnMorph:FireServer(unpack(Revert))
      end
Tab:AddButton({
    Name = "Kill Albedo",
    Callback = function()
    KillAlbedo()
end})
    
    Tab:AddToggle({
	Name = "Auto Potis Altiarie",
	Default = false,
Callback = function(Value)
while Value do
--game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
    for _,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
        if v:IsA('BasePart') and v.CanCollide and v.Name ~= floatName then
           v.CanCollide = false
       end
     end
     transform(cromaticos)
     local function Tp(x, y, z)
        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(x, y, z))
        end
        wait(3)
Tp(5643.18994, 719.616943, -8380.25586)

wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part1.PR.ProximityPrompt, 100)
end
wait(1)
if Value then
Tp(-1253.40967, 8.55848694, 50413.1406)
end
wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part2.PR.ProximityPrompt, 100)
end
wait(1)
if Value then
Tp(-1053.55334, 8.48646927, 90785.5859)
end
wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part3.PR.ProximityPrompt, 100)
end
wait(1)
if Value then
Tp(64851.125, 8.48646927, 66906.2188)
end
wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part4.PR.ProximityPrompt, 100)
end
wait(1)
if Value then
Tp(11876.5244, -144.071625, -3692.88281)
end
wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part5.PR.ProximityPrompt, 100)
end
wait(1)
if Value then
Tp(-1538.32812, -191.003342, -71865.6172)
end
wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part6.PR.ProximityPrompt, 100)
end
wait(1)
if Value then
Tp(-68280.7188, 29453.8125, 32773.2812)
end
wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part7.PR.ProximityPrompt, 100)
end
wait(1)
if Value then
Tp(88486.625, -115.589577, -42278.9688)
end
wait(1)
if Value then
fireproximityprompt(workspace.Map.PotisRaid.Part8.PR.ProximityPrompt, 100)
end
wait(0.055)
Tp(-125128, 26604.7539, 24653.6367)
wait(0.5)
game:GetService("ReplicatedStorage").Storage:Destroy()
fireproximityprompt(workspace.Map.PotisRaid.SpawnBoss.PR.ProximityPrompt, 100)
wait(1)
local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    
    local posantes = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
    character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(-125128, 26672.4, 24664.3)))
    
    local platform = Instance.new("Part")
    platform.Size = Vector3.new(10, 1, 10) -- 2
    platform.Position = character.PrimaryPart.Position - Vector3.new(0, 5, 0)
    platform.Anchored = true
    platform.Parent = game.Workspace
    wait(1)
    if Value then
    KillAlbedo()
    end
      wait(5)
      end
end})
--------anti afk-----------




local Tab = Window:MakeTab({
	Name = "Misc",
	Icon = "rbxassetid://12967712847",
	PremiumOnly = false
})


Tab:AddButton({
	Name = "Credits",
	Callback = function()

      		OrionLib:MakeNotification({
	Name = "Credits.",
	Content = "Script made by exility",
	Image = "rbxassetid://4483345998",
	Time = 15
})
  	end    
})

local Section = Tab:AddSection({
	Name = "Anti AFK e Reset"

})


Tab:AddButton({
  Name = "Anti AFK",
  Callback = function()
    
wait(0.5)local ba=Instance.new("ScreenGui")
local ca=Instance.new("TextLabel")local da=Instance.new("Frame")
local _b=Instance.new("TextLabel")local ab=Instance.new("TextLabel")ba.Parent=game.CoreGui
ba.ZIndexBehavior=Enum.ZIndexBehavior.Sibling;ca.Parent=ba;ca.Active=true
ca.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ca.Draggable=true
ca.Position=UDim2.new(0.698610067,0,0.098096624,0)ca.Size=UDim2.new(0,370,0,52)
ca.Font=Enum.Font.SourceSansSemibold;ca.Text="Anti Afk"ca.TextColor3=Color3.new(0,1,1)
ca.TextSize=22;da.Parent=ca
da.BackgroundColor3=Color3.new(0.196078,0.196078,0.196078)da.Position=UDim2.new(0,0,1.0192306,0)
da.Size=UDim2.new(0,370,0,107)_b.Parent=da
_b.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)_b.Position=UDim2.new(0,0,0.800455689,0)
_b.Size=UDim2.new(0,370,0,21)_b.Font=Enum.Font.Arial;_b.Text="Made by luca#5432"
_b.TextColor3=Color3.new(0,1,1)_b.TextSize=20;ab.Parent=da
ab.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ab.Position=UDim2.new(0,0,0.158377,0)
ab.Size=UDim2.new(0,370,0,44)ab.Font=Enum.Font.ArialBold;ab.Text="Status: Active"
ab.TextColor3=Color3.new(0,1,1)ab.TextSize=20;local bb=game:service'VirtualUser'
game:service'Players'.LocalPlayer.Idled:connect(function()
bb:CaptureController()bb:ClickButton2(Vector2.new())
ab.Text="Roblox tried kicking you buy I didnt let them!"wait(2)ab.Text="Status : Active"end)
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()


while wait(5) do
  
character:SetPrimaryPartCFrame(CFrame.new(Vector3.new(0, 100005, 0)))

end
  end
})


Tab:AddButton({
  Name = "Reset",
  Callback = function()
    
    game:GetService("ReplicatedStorage").Remotes.LoadCHCopy:FireServer()
end})

Tab:AddButton({
  Name = "Rejoin",
  Callback = function()
local TeleportService = game:GetService("TeleportService")
TeleportService:Teleport(game.PlaceId)
end})


Tab:AddButton({
  Name = "Infinite Yield",
  Callback = function()
loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
end})

local Section = Tab:AddSection({
	Name = "Server Hop"
})


Tab:AddButton({
  Name = "Search for server with few players",
  Callback = function()
    
local Http = game:GetService("HttpService")
local TPS = game:GetService("TeleportService")
local Api = "https://games.roblox.com/v1/games/"
local _place = game.PlaceId
local _servers = Api.._place.."/servers/Public?sortOrder=Asc&limit=100"
function ListServers(cursor)
   local Raw = game:HttpGet(_servers .. ((cursor and "&cursor="..cursor) or ""))
   return Http:JSONDecode(Raw)

end

local Server, Next; repeat
   local Servers = ListServers(Next)
   Server = Servers.data[1]
   Next = Servers.nextPageCursor
until Server

TPS:TeleportToPlaceInstance(_place,Server.id,game:GetService('Players').LocalPlayer)

end
})


Tab:AddButton({ 

Name = "Discord", 

Callback = function() 	

setclipboard("https://discord.com/invite/2vGDDGdC")

OrionLib:MakeNotification({
	Name = "Quasar-Hub",
	Content = "Script has been sent to you clipboard\nO Script Foi Enviado para sua area de transferencia",
	Image = "rbxassetid://4483345998",
	Time = 15
})



end })



Tab:AddDropdown({
    Name = "Speed",
    Default = "16",
    Options = {"16", "30", "50"},
    Callback = function(Value)
        if Value == "16" then
game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = 16
elseif Value == "30" then
game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = 30
elseif Value == "50" then
game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = 50
end
    end    
})

Tab:AddButton({
	Name = "Reset (not used in raid)",
	Callback = function()
      		game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").Health = 0
  	end    

})

Tab:AddButton({
	Name = "Remove Anchor",
	Callback = function()
      		game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
  	end    
})

Tab:AddTextbox({
	Name = "Teleport to Player",
	Default = "",
	TextDisappear = false,
	Callback = function(Value)
			local pos = game.Workspace:FindFirstChild(Value).HumanoidRootPart.Position
            local mathematicpov = {}
            TweenTp(pos, 7.5)
	end	  
})



local Tab = Window:MakeTab({
	Name = "Debug",
	Icon = "rbxassetid://11422151787",
	PremiumOnly = false
})

Tab:AddButton({
	Name = "Current Max Level",
	Callback = function()
      		local informacoes = {
    maxlevel = game:GetService("ReplicatedStorage"):FindFirstChild("Valores").MaxLevel.Value,
    LevelAtual = game:GetService("Players").LocalPlayer.atributos:WaitForChild("Level").Value,
    classe = game:GetService("Players").LocalPlayer.atributos:WaitForChild("CLASSPLAYER").Value
}

OrionLib:MakeNotification({
	Name = "Quasar-Hub",
	Content = "The current Max Level is: ".. informacoes.maxlevel,
	Image = "rbxassetid://4483345998",
	Time = 5
})
  	end    
})

Tab:AddButton({
	Name = "Find out which omnitrix you are using",
	Callback = function()
        local classe=game:GetService("Players").LocalPlayer.atributos:WaitForChild("CLASSPLAYER").Value
      		if classe == "OS" then
                OrionLib:MakeNotification({
                    Name = "Quasar-Hub",
                    Content = "VocÃª esta usando o omnitrix prototipo prossiga ate o level 190 para obter o omnitrix recalibrado" / "You are using the prototype omnitrix, proceed to level 190 to obtain the recalibrated omnitrix",
                    Image = "rbxassetid://4483345998",
                    Time = 5
                })
            elseif classe == "AF" then
                OrionLib:MakeNotification({
                    Name = "Quasar-Hub",
                    Content = "VocÃª esta usando o omnitrix recalibrado, prossiga ate o level 500 para obter o SuperOmnitrix" / "You are using the recalibrated omnitrix, proceed to level 500 to obtain the Super Omnitrix",
                    Image = "rbxassetid://4483345998",
                    Time = 5
                })
            elseif class == "UA" then
                OrionLib:MakeNotification({
                    Name = "Quasar-Hub",
                    Content = "VocÃª esta usando a evoluÃ§Ã£o final atualmente do omnitrix, o SuperOmnitrix" / "You are currently using the final evolution of the omnitrix, the SuperOmnitri",
                    Image = "rbxassetid://4483345998",
                    Time = 5
                })
            end
  	end    
})

OrionLib:Init()

game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16

game.ReplicatedStorage.AliensPowerRemotes.alienx.Negado.OnClientEvent:Connect(function()
		if getgenv().autoperm then
	    	if getgenv().thealienx == "Normal" then
		        transform(alienx)
	    	elseif getgenv().thealienx == "Ultimate" then
		         transform(alienxs)
	    	end
		end
end)
