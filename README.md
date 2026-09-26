local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local Stats = game:GetService("Stats")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local UserInputService = game:GetService("UserInputService")
local LocalPlayer = Players.LocalPlayer

local isMobile = UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled

local executorName = "UNKNOWN EXECUTOR"
pcall(function()
    if identifyexecutor then
        executorName = identifyexecutor()
    elseif getexecutorname then
        executorName = getexecutorname()
    elseif fluxus then
        executorName = "Fluxus"
    elseif syn then
        executorName = "Synapse X"
    elseif hydrogen then
        executorName = "Hydrogen"
    elseif delta then
        executorName = "Delta"
    elseif arceus then
        executorName = "Arceus X"
    end
end)

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "DoryHubNeedleHaystackUltraFull"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = CoreGui

local ImageAssetId = "dory_logo_gemini_nobg.png"
local DiscordImageAssetId = "discord_logo_nobg.png"

local function GetImageAsset(url, fileId)
    if writefile and isfile and not isfile(fileId) then
        pcall(function()
            writefile(fileId, game:HttpGet(url))
        end)
    end
    if getcustomasset and isfile and isfile(fileId) then
        return getcustomasset(fileId)
    end
    return url
end

local ImageUrl = "https://media.discordapp.net/attachments/1551215135903715458/1551959472048443443/Gemini_Generated_Image_o315zxo315zxo315-removebg-preview.png?ex=6ab3de64&is=6ab28ce4&hm=cc3d4e08ab6ddbdc52a26ea1bde954a38117cb5d9618504f2da7c4bd65b580f8&=&format=webp&quality=lossless"
local DiscordUrl = "https://media.discordapp.net/attachments/1551215135903715458/1553319984116146327/2026-09-26_151731-removebg-preview.png?ex=6ab8d177&is=6ab77ff7&hm=ff261c21e43c59ce72117838d44eac6061166b6571257df45b45becd57270c65&=&format=webp&quality=lossless"

local FinalImageAsset = GetImageAsset(ImageUrl, ImageAssetId)
local FinalDiscordAsset = GetImageAsset(DiscordUrl, DiscordImageAssetId)

local LoadingFrame = Instance.new("Frame")
LoadingFrame.Name = "LoadingFrame"
LoadingFrame.Size = UDim2.new(1, 0, 1, 0)
LoadingFrame.BackgroundTransparency = 1
LoadingFrame.BorderSizePixel = 0
LoadingFrame.ZIndex = 100
LoadingFrame.Parent = ScreenGui

local LoadingLogo = Instance.new("ImageLabel")
LoadingLogo.Name = "LoadingLogo"
LoadingLogo.Size = UDim2.new(0, isMobile and 140 or 320, 0, isMobile and 70 or 160)
LoadingLogo.Position = UDim2.new(0.5, isMobile and -70 or -160, 0.4, isMobile and -35 or -80)
LoadingLogo.BackgroundTransparency = 1
LoadingLogo.BorderSizePixel = 0
LoadingLogo.Image = FinalImageAsset
LoadingLogo.ScaleType = Enum.ScaleType.Fit
LoadingLogo.ZIndex = 101
LoadingLogo.Parent = LoadingFrame

local LoadingText = Instance.new("TextLabel")
LoadingText.Name = "LoadingText"
LoadingText.Size = UDim2.new(0, 300, 0, 30)
LoadingText.Position = UDim2.new(0.5, -150, 0.4, isMobile and 40 or 90)
LoadingText.BackgroundTransparency = 1
LoadingText.BorderSizePixel = 0
LoadingText.Text = "LOADING ULTRA ENGINE..."
LoadingText.TextColor3 = Color3.fromRGB(255, 255, 255)
LoadingText.TextSize = isMobile and 9 or 14
LoadingText.Font = Enum.Font.Arcade
LoadingText.ZIndex = 101
LoadingText.Parent = LoadingFrame

local MinimisedBox = Instance.new("ImageButton")
MinimisedBox.Name = "MinimisedBox"
MinimisedBox.Size = UDim2.new(0, isMobile and 45 or 140, 0, isMobile and 45 or 70)
MinimisedBox.Position = UDim2.new(0.5, isMobile and -22 or -70, 0.02, 0)
MinimisedBox.BackgroundTransparency = 1
MinimisedBox.BorderSizePixel = 0
MinimisedBox.Image = FinalImageAsset
MinimisedBox.ScaleType = Enum.ScaleType.Fit
MinimisedBox.Active = true
MinimisedBox.Draggable = true
MinimisedBox.Visible = false
MinimisedBox.ZIndex = 50
MinimisedBox.Parent = ScreenGui

local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = isMobile and UDim2.new(0, 260, 0, 180) or UDim2.new(0, 780, 0, 460)
MainFrame.Position = isMobile and UDim2.new(0.5, -130, 0.5, -90) or UDim2.new(0.5, -390, 0.5, -230)
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 17)
MainFrame.BackgroundTransparency = 0.05
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Visible = false
MainFrame.ZIndex = 1
MainFrame.Parent = ScreenGui

Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, isMobile and 8 or 12)

local TopBar = Instance.new("Frame")
TopBar.Name = "TopBar"
TopBar.Size = UDim2.new(1, 0, 0, isMobile and 28 or 48)
TopBar.BackgroundTransparency = 1
TopBar.BorderSizePixel = 0
TopBar.ZIndex = 2
TopBar.Parent = MainFrame

local LogoImg = Instance.new("ImageLabel")
LogoImg.Size = UDim2.new(0, isMobile and 14 or 24, 0, isMobile and 14 or 24)
LogoImg.Position = UDim2.new(0, isMobile and 6 or 16, 0.5, isMobile and -7 or -12)
LogoImg.BackgroundTransparency = 1
LogoImg.Image = FinalImageAsset
LogoImg.ScaleType = Enum.ScaleType.Fit
LogoImg.ZIndex = 2
LogoImg.Parent = TopBar

local TitleLabel = Instance.new("TextLabel")
TitleLabel.Name = "TitleLabel"
TitleLabel.Size = UDim2.new(0, isMobile and 120 or 350, 1, 0)
TitleLabel.Position = UDim2.new(0, isMobile and 24 or 48, 0, 0)
TitleLabel.BackgroundTransparency = 1
TitleLabel.BorderSizePixel = 0
TitleLabel.Text = "DORY HUB <font color=\"rgb(130,130,140)\">ULTRA</font>"
TitleLabel.TextColor3 = Color3.fromRGB(240, 240, 245)
TitleLabel.TextSize = isMobile and 8 or 12
TitleLabel.Font = Enum.Font.Arcade
TitleLabel.TextXAlignment = Enum.TextXAlignment.Left
TitleLabel.RichText = true
TitleLabel.ZIndex = 2
TitleLabel.Parent = TopBar

local VersionBadge = Instance.new("Frame")
VersionBadge.Size = UDim2.new(0, isMobile and 24 or 36, 0, isMobile and 14 or 20)
VersionBadge.Position = UDim2.new(0, isMobile and 95 or 225, 0.5, isMobile and -7 or -10)
VersionBadge.BackgroundColor3 = Color3.fromRGB(30, 30, 36)
VersionBadge.BorderSizePixel = 0
VersionBadge.ZIndex = 2
VersionBadge.Parent = TopBar

Instance.new("UICorner", VersionBadge).CornerRadius = UDim.new(0, 4)

local VB_Text = Instance.new("TextLabel")
VB_Text.Size = UDim2.new(1, 0, 1, 0)
VB_Text.BackgroundTransparency = 1
VB_Text.Text = isMobile and "MOB" or "PC"
VB_Text.TextColor3 = Color3.fromRGB(180, 180, 190)
VB_Text.TextSize = isMobile and 7 or 10
VB_Text.Font = Enum.Font.Arcade
VB_Text.ZIndex = 2
VB_Text.Parent = VersionBadge

local ControlFrame = Instance.new("Frame")
ControlFrame.Name = "ControlFrame"
ControlFrame.Size = UDim2.new(0, isMobile and 100 or 200, 1, 0)
ControlFrame.Position = UDim2.new(1, isMobile and -100 or -200, 0, 0)
ControlFrame.BackgroundTransparency = 1
ControlFrame.BorderSizePixel = 0
ControlFrame.ZIndex = 2
ControlFrame.Parent = TopBar

local DiscordBtn = Instance.new("ImageButton")
DiscordBtn.Name = "DiscordBtn"
DiscordBtn.Size = UDim2.new(0, isMobile and 16 or 26, 0, isMobile and 16 or 26)
DiscordBtn.Position = UDim2.new(0, isMobile and 2 or 15, 0.5, isMobile and -8 or -13)
DiscordBtn.BackgroundTransparency = 1
DiscordBtn.Image = FinalDiscordAsset
DiscordBtn.ScaleType = Enum.ScaleType.Fit
DiscordBtn.ZIndex = 2
DiscordBtn.Parent = ControlFrame

DiscordBtn.MouseButton1Click:Connect(function()
    if setclipboard then
        setclipboard("https://discord.gg/Wnk2NCw4EN")
    end
end)

local PingLabel = Instance.new("TextLabel")
PingLabel.Size = UDim2.new(0, isMobile and 35 or 65, 1, 0)
PingLabel.Position = UDim2.new(0, isMobile and 20 or 48, 0, 0)
PingLabel.BackgroundTransparency = 1
PingLabel.Text = "PING"
PingLabel.TextColor3 = Color3.fromRGB(130, 130, 140)
PingLabel.TextSize = isMobile and 7 or 10
PingLabel.Font = Enum.Font.Arcade
PingLabel.TextXAlignment = Enum.TextXAlignment.Right
PingLabel.ZIndex = 2
PingLabel.Parent = ControlFrame

task.spawn(function()
    while true do
        pcall(function()
            local ping = math.floor(Stats.Network.ServerStatsItem["Data Ping"]:GetValue())
            PingLabel.Text = ping .. "MS"
            if ping < 100 then
                PingLabel.TextColor3 = Color3.fromRGB(80, 200, 120)
            elseif ping < 200 then
                PingLabel.TextColor3 = Color3.fromRGB(240, 200, 80)
            else
                PingLabel.TextColor3 = Color3.fromRGB(220, 80, 80)
            end
        end)
        task.wait(1)
    end
end)

local MinimizeBtn = Instance.new("TextButton")
MinimizeBtn.Name = "MinimizeBtn"
MinimizeBtn.Size = UDim2.new(0, isMobile and 18 or 28, 0, isMobile and 18 or 28)
MinimizeBtn.Position = UDim2.new(0, isMobile and 58 or 115, 0.5, isMobile and -9 or -14)
MinimizeBtn.BackgroundTransparency = 1
MinimizeBtn.Text = "-"
MinimizeBtn.TextColor3 = Color3.fromRGB(160, 160, 170)
MinimizeBtn.TextSize = isMobile and 10 or 14
MinimizeBtn.Font = Enum.Font.Arcade
MinimizeBtn.ZIndex = 2
MinimizeBtn.Parent = ControlFrame

local CloseBtn = Instance.new("TextButton")
CloseBtn.Name = "CloseBtn"
CloseBtn.Size = UDim2.new(0, isMobile and 18 or 28, 0, isMobile and 18 or 28)
CloseBtn.Position = UDim2.new(0, isMobile and 78 or 150, 0.5, isMobile and -9 or -14)
CloseBtn.BackgroundTransparency = 1
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.fromRGB(160, 160, 170)
CloseBtn.TextSize = isMobile and 8 or 12
CloseBtn.Font = Enum.Font.Arcade
CloseBtn.ZIndex = 2
CloseBtn.Parent = ControlFrame

local Sidebar = Instance.new("ScrollingFrame")
Sidebar.Name = "Sidebar"
Sidebar.Size = UDim2.new(0, isMobile and 70 or 150, 1, isMobile and -35 or -60)
Sidebar.Position = UDim2.new(0, isMobile and 6 or 12, 0, isMobile and 30 or 50)
Sidebar.BackgroundTransparency = 1
Sidebar.BorderSizePixel = 0
Sidebar.CanvasSize = UDim2.new(0, 0, 0, 0)
Sidebar.ScrollBarThickness = 0
Sidebar.ZIndex = 2
Sidebar.Parent = MainFrame

local SB_Layout = Instance.new("UIListLayout")
SB_Layout.SortOrder = Enum.SortOrder.LayoutOrder
SB_Layout.Padding = UDim.new(0, isMobile and 2 or 4)
SB_Layout.Parent = Sidebar

local UserProfileBox = Instance.new("Frame")
UserProfileBox.Size = UDim2.new(0, isMobile and 70 or 150, 0, isMobile and 28 or 50)
UserProfileBox.Position = UDim2.new(0, isMobile and 6 or 12, 1, isMobile and -32 or -60)
UserProfileBox.BackgroundTransparency = 1
UserProfileBox.ZIndex = 2
UserProfileBox.Parent = MainFrame

local UserAvatar = Instance.new("ImageLabel")
UserAvatar.Size = UDim2.new(0, isMobile and 20 or 36, 0, isMobile and 20 or 36)
UserAvatar.Position = UDim2.new(0, 0, 0.5, isMobile and -10 or -18)
UserAvatar.BackgroundTransparency = 1
UserAvatar.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"
UserAvatar.ZIndex = 2
UserAvatar.Parent = UserProfileBox

Instance.new("UICorner", UserAvatar).CornerRadius = UDim.new(1, 0)

task.spawn(function()
    local success, content = pcall(function()
        return Players:GetUserThumbnailAsync(LocalPlayer.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size100x100)
    end)
    if success then UserAvatar.Image = content end
end)

local UserNameLbl = Instance.new("TextLabel")
UserNameLbl.Size = UDim2.new(1, isMobile and -22 or -44, 1, 0)
UserNameLbl.Position = UDim2.new(0, isMobile and 22 or 42, 0, 0)
UserNameLbl.BackgroundTransparency = 1
UserNameLbl.Text = LocalPlayer.Name
UserNameLbl.TextColor3 = Color3.fromRGB(220, 220, 230)
UserNameLbl.TextSize = isMobile and 7 or 10
UserNameLbl.Font = Enum.Font.Arcade
UserNameLbl.TextXAlignment = Enum.TextXAlignment.Left
UserNameLbl.ZIndex = 2
UserNameLbl.Parent = UserProfileBox

local ContentArea = Instance.new("Frame")
ContentArea.Name = "ContentArea"
ContentArea.Size = UDim2.new(1, isMobile and -82 or -180, 1, isMobile and -36 or -64)
ContentArea.Position = UDim2.new(0, isMobile and 78 or 172, 0, isMobile and 30 or 52)
ContentArea.BackgroundTransparency = 1
ContentArea.BorderSizePixel = 0
ContentArea.ZIndex = 2
ContentArea.Parent = MainFrame

local activeTabBtn = nil
local activeTabPage = nil

local function CreateTab(name, isDefault)
    local TabBtn = Instance.new("TextButton")
    TabBtn.Size = UDim2.new(1, 0, 0, isMobile and 22 or 36)
    TabBtn.BackgroundTransparency = isDefault and 0 or 1
    TabBtn.BackgroundColor3 = Color3.fromRGB(25, 25, 30)
    TabBtn.BorderSizePixel = 0
    TabBtn.Text = (isMobile and "" or "   ") .. string.upper(name)
    TabBtn.TextColor3 = isDefault and Color3.fromRGB(255, 255, 255) or Color3.fromRGB(130, 130, 140)
    TabBtn.TextSize = isMobile and 7 or 10
    TabBtn.Font = Enum.Font.Arcade
    TabBtn.TextXAlignment = isMobile and Enum.TextXAlignment.Center or Enum.TextXAlignment.Left
    TabBtn.ZIndex = 2
    TabBtn.Parent = Sidebar

    Instance.new("UICorner", TabBtn).CornerRadius = UDim.new(0, isMobile and 6 or 8)

    local TabPage = Instance.new("ScrollingFrame")
    TabPage.Size = UDim2.new(1, 0, 1, 0)
    TabPage.BackgroundTransparency = 1
    TabPage.BorderSizePixel = 0
    TabPage.Visible = isDefault
    TabPage.CanvasSize = UDim2.new(0, 0, 0, 0)
    TabPage.AutomaticCanvasSize = Enum.AutomaticSize.Y
    TabPage.ScrollBarThickness = 2
    TabPage.ZIndex = 2
    TabPage.Parent = ContentArea

    local PageLayout = Instance.new("UIListLayout")
    PageLayout.SortOrder = Enum.SortOrder.LayoutOrder
    PageLayout.Padding = UDim.new(0, isMobile and 4 or 10)
    PageLayout.Parent = TabPage

    if isDefault then
        activeTabBtn = TabBtn
        activeTabPage = TabPage
    end

    TabBtn.MouseButton1Click:Connect(function()
        if activeTabPage then activeTabPage.Visible = false end
        if activeTabBtn then 
            activeTabBtn.TextColor3 = Color3.fromRGB(130, 130, 140)
            activeTabBtn.BackgroundTransparency = 1
        end
        TabPage.Visible = true
        TabBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
        TabBtn.BackgroundTransparency = 0
        activeTabPage = TabPage
        activeTabBtn = TabBtn
    end)

    return TabPage
end

local HomeTab = CreateTab("Home", true)

local HomeCenterContainer = Instance.new("Frame")
HomeCenterContainer.Size = isMobile and UDim2.new(1, 0, 1, 0) or UDim2.new(0, 560, 0, 380)
HomeCenterContainer.Position = isMobile and UDim2.new(0, 0, 0, 0) or UDim2.new(0.5, -280, 0.5, -190)
HomeCenterContainer.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
HomeCenterContainer.BackgroundTransparency = 0.4
HomeCenterContainer.BorderSizePixel = 0
HomeCenterContainer.ZIndex = 2
HomeCenterContainer.Parent = HomeTab
Instance.new("UICorner", HomeCenterContainer).CornerRadius = UDim.new(0, isMobile and 8 or 12)

local BigAvatar = Instance.new("ImageLabel")
BigAvatar.Size = UDim2.new(0, isMobile and 32 or 80, 0, isMobile and 32 or 80)
BigAvatar.Position = UDim2.new(0, isMobile and 8 or 25, 0, isMobile and 8 or 25)
BigAvatar.BackgroundTransparency = 1
BigAvatar.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"
BigAvatar.ZIndex = 2
BigAvatar.Parent = HomeCenterContainer
Instance.new("UICorner", BigAvatar).CornerRadius = UDim.new(1, 0)

task.spawn(function()
    local success, content = pcall(function()
        return Players:GetUserThumbnailAsync(LocalPlayer.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size420x420)
    end)
    if success then BigAvatar.Image = content end
end)

local ProfileNameLbl = Instance.new("TextLabel")
ProfileNameLbl.Size = UDim2.new(0, isMobile and 120 or 300, 0, isMobile and 15 or 24)
ProfileNameLbl.Position = UDim2.new(0, isMobile and 45 or 120, 0, isMobile and 8 or 28)
ProfileNameLbl.BackgroundTransparency = 1
ProfileNameLbl.Text = LocalPlayer.Name
ProfileNameLbl.TextColor3 = Color3.fromRGB(255, 255, 255)
ProfileNameLbl.TextSize = isMobile and 8 or 14
ProfileNameLbl.Font = Enum.Font.Arcade
ProfileNameLbl.TextXAlignment = Enum.TextXAlignment.Left
ProfileNameLbl.ZIndex = 2
ProfileNameLbl.Parent = HomeCenterContainer

local ProfileSubLbl = Instance.new("TextLabel")
ProfileSubLbl.Size = UDim2.new(0, isMobile and 120 or 300, 0, isMobile and 12 or 20)
ProfileSubLbl.Position = UDim2.new(0, isMobile and 45 or 120, 0, isMobile and 22 or 54)
ProfileSubLbl.BackgroundTransparency = 1
ProfileSubLbl.Text = "DEVICE: " .. (isMobile and "MOBILE" or "PC") .. " | EXECUTOR: " .. string.upper(executorName)
ProfileSubLbl.TextColor3 = Color3.fromRGB(130, 130, 140)
ProfileSubLbl.TextSize = isMobile and 6 or 9
ProfileSubLbl.Font = Enum.Font.Arcade
ProfileSubLbl.TextXAlignment = Enum.TextXAlignment.Left
ProfileSubLbl.ZIndex = 2
ProfileSubLbl.Parent = HomeCenterContainer

local StatsContainer = Instance.new("Frame")
StatsContainer.Size = isMobile and UDim2.new(1, -16, 0, 45) or UDim2.new(1, -50, 0, 90)
StatsContainer.Position = isMobile and UDim2.new(0, 8, 0, 46) or UDim2.new(0, 25, 0, 125)
StatsContainer.BackgroundColor3 = Color3.fromRGB(25, 25, 32)
StatsContainer.BackgroundTransparency = 0.3
StatsContainer.BorderSizePixel = 0
StatsContainer.ZIndex = 2
StatsContainer.Parent = HomeCenterContainer
Instance.new("UICorner", StatsContainer).CornerRadius = UDim.new(0, isMobile and 6 or 10)

local GameInfoLbl = Instance.new("TextLabel")
GameInfoLbl.Size = UDim2.new(0.5, -6, 0, isMobile and 18 or 40)
GameInfoLbl.Position = UDim2.new(0, 6, 0, 4)
GameInfoLbl.BackgroundTransparency = 1
GameInfoLbl.Text = "NEEDLE HAYSTACK ULTRA"
GameInfoLbl.TextColor3 = Color3.fromRGB(100, 200, 255)
GameInfoLbl.TextSize = isMobile and 7 or 10
GameInfoLbl.Font = Enum.Font.Arcade
GameInfoLbl.TextXAlignment = Enum.TextXAlignment.Left
GameInfoLbl.ZIndex = 2
GameInfoLbl.Parent = StatsContainer

local FpsInfoLbl = Instance.new("TextLabel")
FpsInfoLbl.Size = UDim2.new(0.5, -6, 0, isMobile and 18 or 30)
FpsInfoLbl.Position = UDim2.new(0, 6, 0, isMobile and 22 or 50)
FpsInfoLbl.BackgroundTransparency = 1
FpsInfoLbl.Text = "FPS: 60"
FpsInfoLbl.TextColor3 = Color3.fromRGB(80, 200, 120)
FpsInfoLbl.TextSize = isMobile and 7 or 10
FpsInfoLbl.Font = Enum.Font.Arcade
FpsInfoLbl.TextXAlignment = Enum.TextXAlignment.Left
FpsInfoLbl.ZIndex = 2
FpsInfoLbl.Parent = StatsContainer

task.spawn(function()
    local lastTick = tick()
    local frameCount = 0
    RunService.RenderStepped:Connect(function()
        frameCount = frameCount + 1
        if tick() - lastTick >= 1 then
            FpsInfoLbl.Text = "FPS: " .. math.floor(frameCount / (tick() - lastTick))
            frameCount = 0
            lastTick = tick()
        end
    end)
end)

local WelcomeBanner = Instance.new("Frame")
WelcomeBanner.Size = isMobile and UDim2.new(1, -16, 0, 48) or UDim2.new(1, -50, 0, 105)
WelcomeBanner.Position = isMobile and UDim2.new(0, 8, 0, 96) or UDim2.new(0, 25, 0, 235)
WelcomeBanner.BackgroundColor3 = Color3.fromRGB(25, 25, 32)
WelcomeBanner.BackgroundTransparency = 0.3
WelcomeBanner.BorderSizePixel = 0
WelcomeBanner.ZIndex = 2
WelcomeBanner.Parent = HomeCenterContainer
Instance.new("UICorner", WelcomeBanner).CornerRadius = UDim.new(0, isMobile and 6 or 10)

local WB_Desc = Instance.new("TextLabel")
WB_Desc.Size = UDim2.new(1, -12, 1, 0)
WB_Desc.Position = UDim2.new(0, 6, 0, 0)
WB_Desc.BackgroundTransparency = 1
WB_Desc.Text = "TIDCRAM SUITE. MOBILE UI OPTIMIZED. EXECUTOR: " .. string.upper(executorName)
WB_Desc.TextColor3 = Color3.fromRGB(140, 140, 150)
WB_Desc.TextSize = isMobile and 6 or 9
WB_Desc.Font = Enum.Font.Arcade
WB_Desc.TextXAlignment = Enum.TextXAlignment.Left
WB_Desc.TextWrapped = true
WB_Desc.ZIndex = 2
WB_Desc.Parent = WelcomeBanner

local AutoFarmTab = CreateTab("Farm", false)

local FarmSection = Instance.new("Frame")
FarmSection.Size = isMobile and UDim2.new(1, 0, 1, 0) or UDim2.new(0, 560, 0, 415)
FarmSection.Position = isMobile and UDim2.new(0, 0, 0, 0) or UDim2.new(0.5, -280, 0, 0)
FarmSection.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
FarmSection.BackgroundTransparency = 0.6
FarmSection.BorderSizePixel = 0
FarmSection.ZIndex = 2
FarmSection.Parent = AutoFarmTab
Instance.new("UICorner", FarmSection).CornerRadius = UDim.new(0, isMobile and 6 or 10)

local ToggleCollectBtn = Instance.new("TextButton")
ToggleCollectBtn.Size = isMobile and UDim2.new(1, -16, 0, 26) or UDim2.new(0, 260, 0, 36)
ToggleCollectBtn.Position = isMobile and UDim2.new(0, 8, 0, 6) or UDim2.new(0, 12, 0, 38)
ToggleCollectBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
ToggleCollectBtn.BorderSizePixel = 0
ToggleCollectBtn.Text = "AUTO COLLECT: OFF"
ToggleCollectBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
ToggleCollectBtn.TextSize = isMobile and 7 or 9
ToggleCollectBtn.Font = Enum.Font.Arcade
ToggleCollectBtn.ZIndex = 2
ToggleCollectBtn.Parent = FarmSection
Instance.new("UICorner", ToggleCollectBtn).CornerRadius = UDim.new(0, isMobile and 6 or 8)

local ToggleSellBtn = Instance.new("TextButton")
ToggleSellBtn.Size = isMobile and UDim2.new(1, -16, 0, 26) or UDim2.new(0, 260, 0, 36)
ToggleSellBtn.Position = isMobile and UDim2.new(0, 8, 0, 36) or UDim2.new(0, 288, 0, 38)
ToggleSellBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
ToggleSellBtn.BorderSizePixel = 0
ToggleSellBtn.Text = "AUTO SELL: OFF"
ToggleSellBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
ToggleSellBtn.TextSize = isMobile and 7 or 9
ToggleSellBtn.Font = Enum.Font.Arcade
ToggleSellBtn.ZIndex = 2
ToggleSellBtn.Parent = FarmSection
Instance.new("UICorner", ToggleSellBtn).CornerRadius = UDim.new(0, isMobile and 6 or 8)

local ToggleRideBtn = Instance.new("TextButton")
ToggleRideBtn.Size = isMobile and UDim2.new(1, -16, 0, 26) or UDim2.new(0, 536, 0, 36)
ToggleRideBtn.Position = isMobile and UDim2.new(0, 8, 0, 66) or UDim2.new(0, 12, 0, 82)
ToggleRideBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
ToggleRideBtn.BorderSizePixel = 0
ToggleRideBtn.Text = "INSTANT RIDE A PET: OFF"
ToggleRideBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
ToggleRideBtn.TextSize = isMobile and 7 or 9
ToggleRideBtn.Font = Enum.Font.Arcade
ToggleRideBtn.ZIndex = 2
ToggleRideBtn.Parent = FarmSection
Instance.new("UICorner", ToggleRideBtn).CornerRadius = UDim.new(0, isMobile and 6 or 8)

local FarmLogFrame = Instance.new("ScrollingFrame")
FarmLogFrame.Size = isMobile and UDim2.new(1, -16, 0, 56) or UDim2.new(1, -24, 0, 260)
FarmLogFrame.Position = isMobile and UDim2.new(0, 8, 0, 96) or UDim2.new(0, 12, 0, 128)
FarmLogFrame.BackgroundColor3 = Color3.fromRGB(22, 22, 26)
FarmLogFrame.BackgroundTransparency = 0.5
FarmLogFrame.BorderSizePixel = 0
FarmLogFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
FarmLogFrame.AutomaticCanvasSize = Enum.AutomaticSize.Y
FarmLogFrame.ScrollBarThickness = 2
FarmLogFrame.ZIndex = 2
FarmLogFrame.Parent = FarmSection
Instance.new("UICorner", FarmLogFrame).CornerRadius = UDim.new(0, isMobile and 6 or 8)

local FL_Layout = Instance.new("UIListLayout")
FL_Layout.SortOrder = Enum.SortOrder.LayoutOrder
FL_Layout.Padding = UDim.new(0, 3)
FL_Layout.Parent = FarmLogFrame

local function AddFarmLog(txt)
    local lbl = Instance.new("TextLabel")
    lbl.Size = UDim2.new(1, 0, 0, isMobile and 14 or 18)
    lbl.BackgroundTransparency = 1
    lbl.Text = "> " .. string.upper(txt)
    lbl.TextColor3 = Color3.fromRGB(210, 210, 220)
    lbl.TextSize = isMobile and 6 or 9
    lbl.Font = Enum.Font.Arcade
    lbl.TextXAlignment = Enum.TextXAlignment.Left
    lbl.ZIndex = 2
    lbl.Parent = FarmLogFrame
end

AddFarmLog("Engine online. Device: " .. (isMobile and "Mobile" or "PC"))

local isAutoCollectActive = false
local isAutoSellActive = false
local isInstantRideActive = false

ToggleCollectBtn.MouseButton1Click:Connect(function()
    isAutoCollectActive = not isAutoCollectActive
    if isAutoCollectActive then
        ToggleCollectBtn.Text = "AUTO COLLECT: ON"
        ToggleCollectBtn.TextColor3 = Color3.fromRGB(80, 200, 120)
        ToggleCollectBtn.BackgroundColor3 = Color3.fromRGB(30, 60, 40)
        AddFarmLog("Collection started.")
    else
        ToggleCollectBtn.Text = "AUTO COLLECT: OFF"
        ToggleCollectBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
        ToggleCollectBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
        AddFarmLog("Collection stopped.")
    end
end)

ToggleSellBtn.MouseButton1Click:Connect(function()
    isAutoSellActive = not isAutoSellActive
    if isAutoSellActive then
        ToggleSellBtn.Text = "AUTO SELL: ON"
        ToggleSellBtn.TextColor3 = Color3.fromRGB(80, 200, 120)
        ToggleSellBtn.BackgroundColor3 = Color3.fromRGB(30, 60, 40)
        AddFarmLog("Auto selling started.")
    else
        ToggleSellBtn.Text = "AUTO SELL: OFF"
        ToggleSellBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
        ToggleSellBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
        AddFarmLog("Auto selling stopped.")
    end
end)

ToggleRideBtn.MouseButton1Click:Connect(function()
    isInstantRideActive = not isInstantRideActive
    if isInstantRideActive then
        ToggleRideBtn.Text = "INSTANT RIDE A PET: ON"
        ToggleRideBtn.TextColor3 = Color3.fromRGB(80, 200, 120)
        ToggleRideBtn.BackgroundColor3 = Color3.fromRGB(30, 60, 40)
        AddFarmLog("Instant ride pet active.")
    else
        ToggleRideBtn.Text = "INSTANT RIDE A PET: OFF"
        ToggleRideBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
        ToggleRideBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
        AddFarmLog("Instant ride pet stopped.")
    end
end)

local function GetTargetRemote()
    local folder = ReplicatedStorage:FindFirstChild("NeedleHaystack")
    if folder then
        for _, child in ipairs(folder:GetChildren()) do
            if child:IsA("RemoteEvent") and (string.find(string.lower(child.Name), "pick") or string.lower(child.Name) == "pickhay" or string.find(string.lower(child.Name), "collect") or string.find(string.lower(child.Name), "get")) then
                return child
            end
        end
        return folder:FindFirstChild("PickHay")
    end
    return nil
end

local function InspectAndCollectAllObjects()
    pcall(function()
        local workspaceObjects = workspace:GetDescendants()
        for _, obj in ipairs(workspaceObjects) do
            if obj:IsA("BasePart") or obj:IsA("Model") then
                local name = string.lower(obj.Name)
                if string.find(name, "hay") or string.find(name, "needle") or string.find(name, "item") or string.find(name, "collect") then
                    if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                        local root = LocalPlayer.Character.HumanoidRootPart
                        local targetPos = obj:IsA("Model") and obj:GetPivot().Position or obj.Position
                        if (root.Position - targetPos).Magnitude < 100 then
                            firetouchinterest(root, obj, 0)
                            firetouchinterest(root, obj, 1)
                        end
                    end
                end
            end
        end
    end)
end

task.spawn(function()
    while true do
        if isAutoCollectActive then
            pcall(function()
                local remote = GetTargetRemote()
                if remote then
                    for i = 1, 15 do
                        task.spawn(function()
                            remote:FireServer(9467, {})
                            remote:FireServer()
                        end)
                    end
                end
                InspectAndCollectAllObjects()
            end)
        end
        task.wait(0.02)
    end
end)

task.spawn(function()
    while true do
        if isAutoSellActive then
            pcall(function()
                local folder = ReplicatedStorage:FindFirstChild("NeedleHaystack")
                if folder then
                    local sellRemote = folder:FindFirstChild("SellHay")
                    if sellRemote then
                        sellRemote:FireServer()
                    end
                end
            end)
        end
        task.wait(1)
    end
end)

task.spawn(function()
    while true do
        if isInstantRideActive then
            pcall(function()
                if isMobile then
                    task.wait(3.5)
                end
                pcall(function()
                    local folder = ReplicatedStorage:FindFirstChild("NeedleHaystack")
                    if folder then
                        for _, child in ipairs(folder:GetChildren()) do
                            if child:IsA("RemoteEvent") and (string.find(string.lower(child.Name), "ride") or string.find(string.lower(child.Name), "pet") or string.find(string.lower(child.Name), "mount")) then
                                child:FireServer(true)
                                child:FireServer(1)
                                child:FireServer()
                            end
                        end
                    end
                    local char = LocalPlayer.Character
                    if char then
                        for _, obj in ipairs(char:GetDescendants()) do
                            if obj:IsA("RemoteEvent") then
                                obj:FireServer(true)
                            end
                        end
                    end
                end)
            end)
        end
        task.wait(0.1)
    end
end)

local MiscTab = CreateTab("Misc", false)

local MiscSection = Instance.new("Frame")
MiscSection.Size = isMobile and UDim2.new(1, 0, 1, 0) or UDim2.new(0, 560, 0, 415)
MiscSection.Position = isMobile and UDim2.new(0, 0, 0, 0) or UDim2.new(0.5, -280, 0, 0)
MiscSection.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
MiscSection.BackgroundTransparency = 0.6
MiscSection.BorderSizePixel = 0
MiscSection.ZIndex = 2
MiscSection.Parent = MiscTab
Instance.new("UICorner", MiscSection).CornerRadius = UDim.new(0, isMobile and 6 or 10)

local RejoinBtn = Instance.new("TextButton")
RejoinBtn.Size = isMobile and UDim2.new(1, -16, 0, 26) or UDim2.new(0, 536, 0, 36)
RejoinBtn.Position = isMobile and UDim2.new(0, 8, 0, 6) or UDim2.new(0, 12, 0, 38)
RejoinBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
RejoinBtn.BorderSizePixel = 0
RejoinBtn.Text = "REJOIN SERVER"
RejoinBtn.TextColor3 = Color3.fromRGB(240, 100, 100)
RejoinBtn.TextSize = isMobile and 7 or 9
RejoinBtn.Font = Enum.Font.Arcade
RejoinBtn.ZIndex = 2
RejoinBtn.Parent = MiscSection
Instance.new("UICorner", RejoinBtn).CornerRadius = UDim.new(0, isMobile and 6 or 8)

RejoinBtn.MouseButton1Click:Connect(function()
    game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, game.JobId, LocalPlayer)
end)

local isOpen = false
local isAnimating = false

local function OpenUI()
    if isAnimating or isOpen then return end
    isAnimating = true
    isOpen = true
    MinimisedBox.Visible = false
    MainFrame.Position = MinimisedBox.Position
    MainFrame.Size = MinimisedBox.Size
    MainFrame.BackgroundTransparency = 0.05
    MainFrame.Visible = true
    
    local targetSize = isMobile and UDim2.new(0, 260, 0, 180) or UDim2.new(0, 780, 0, 460)
    local targetPos = isMobile and UDim2.new(0.5, -130, 0.5, -90) or UDim2.new(0.5, -390, 0.5, -230)
    local tweenInfo = TweenInfo.new(0.35, Enum.EasingStyle.Quart, Enum.EasingDirection.Out)
    TweenService:Create(MainFrame, tweenInfo, {Position = targetPos, Size = targetSize}):Play()
    task.wait(0.35)
    isAnimating = false
end

local function CloseUI()
    if isAnimating or not isOpen then return end
    isAnimating = true
    isOpen = false
    
    local tweenInfo = TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.In)
    TweenService:Create(MainFrame, tweenInfo, {Position = MinimisedBox.Position, Size = MinimisedBox.Size, BackgroundTransparency = 1}):Play()
    task.wait(0.3)
    MainFrame.Visible = false
    MinimisedBox.Visible = true
    isAnimating = false
end

MinimisedBox.MouseButton1Click:Connect(OpenUI)
MinimizeBtn.MouseButton1Click:Connect(CloseUI)
CloseBtn.MouseButton1Click:Connect(function() ScreenGui:Destroy() end)

task.spawn(function()
    task.wait(0.5)
    for i = 1, 3 do
        LoadingText.Text = "LOADING ULTRA ENGINE."
        task.wait(0.33)
        LoadingText.Text = "LOADING ULTRA ENGINE.."
        task.wait(0.33)
        LoadingText.Text = "LOADING ULTRA ENGINE..."
        task.wait(0.34)
    end
    local fadeTween = TweenService:GetRegistry and TweenService:Create(LoadingFrame, TweenInfo.new(0.5), {BackgroundTransparency = 1}) or TweenService:Create(LoadingFrame, TweenInfo.new(0.5), {BackgroundTransparency = 1})
    fadeTween:Play()
    task.wait(0.5)
    LoadingFrame:Destroy()
    OpenUI()
end)
