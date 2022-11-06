local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "DarkHallowX | DOORS 👁️", HidePremium = false, IntroText = "Doors Supported!",SaveConfig = true, ConfigFolder = "DarkHallowCF"})

local PrivateTab = Window:MakeTab({
	Name = "(Private features)",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

GameTab:AddToggle({
    Name = "Avoid Rush/Ambush",
    Default = false,
    Flag = "AvoidRushToggle",
    Save = true
})
GameTab:AddToggle({
    Name = "Notify when mob spawns",
    Default = false,
    Flag = "MobToggle" ,
    Save = true
})

GameTab:AddToggle({
    Name = "Predict chases",
    Default = false,
    Flag = "PredictToggle" ,
    Save = true
})

--//code start here
local NotificationCoroutine = coroutine.create(function()
    LatestRoom.Changed:Connect(function()
        if OrionLib.Flags["PredictToggle"].Value == true then
            local n = ChaseStart.Value - LatestRoom.Value
            if 0 < n and n < 4 then
                OrionLib:MakeNotification({
                    Name = "Warning!",
                    Content = "Event in " .. tostring(n) .. " rooms.",
                    Time = 5
                })
            end
        end
workspace.ChildAdded:Connect(function(inst)
        if inst.Name == "RushMoving" and OrionLib.Flags["MobToggle"].Value == true then
            if OrionLib.Flags["AvoidRushToggle"].Value == true then
                OrionLib:MakeNotification({
                    Name = "Warning!",
                    Content = "Avoiding Rush. Please wait.",
                    Time = 5
                })
                local OldPos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
                local con = game:GetService("RunService").Heartbeat:Connect(function()
                    game.Players.LocalPlayer.Character:MoveTo(OldPos + Vector3.new(0,20,0))
                end)
                
                inst.Destroying:Wait()
                con:Disconnect()
 
                game.Players.LocalPlayer.Character:MoveTo(OldPos)
            else
                OrionLib:MakeNotification({
                    Name = "Warning!",
                    Content = "Rush has spawned, hide!",
                    Time = 5
                })
            end
elseif inst.Name == "AmbushMoving" and OrionLib.Flags["MobToggle"].Value == true then
            if OrionLib.Flags["AvoidRushToggle"].Value == true then
                OrionLib:MakeNotification({
                    Name = "Warning!",
                    Content = "Avoiding Ambush. Please wait.",
                    Time = 5
                })
                local OldPos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
                local con = game:GetService("RunService").Heartbeat:Connect(function()
                    game.Players.LocalPlayer.Character:MoveTo(OldPos + Vector3.new(0,20,0))
                end)
                
                inst.Destroying:Wait()
                con:Disconnect()
                
                game.Players.LocalPlayer.Character:MoveTo(OldPos)
            else
                OrionLib:MakeNotification({
                    Name = "Warning!",
                    Content = "Ambush has spawned, hide!",
                    Time = 5
                })
            end
        end
    end)
end)


OrionLib:Destroy()
