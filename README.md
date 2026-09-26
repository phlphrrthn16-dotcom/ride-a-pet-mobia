-- 🌟 BOT CONTEXT: TIDCRAM PYTHON/LUAU SCRIPT ASSISTANT 🌟
-- 👑 USER: TIDCRAM[cite: 3]

local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")
local TweenService = game:GetService("TweenService")
local MarketplaceService = game:GetService("MarketplaceService")
local TeleportService = game:GetService("TeleportService")
local Workspace = game:GetService("Workspace")
local RunService = game:GetService("RunService")
local Stats = game:GetService("Stats")
local VirtualInputManager = game:GetService("VirtualInputManager")
local HttpService = game:GetService("HttpService")
local LocalPlayer = Players.LocalPlayer

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "DoryHubMobilePro"
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
LoadingLogo.Size = UDim2.new(0, 220, 0, 110)
LoadingLogo.Position = UDim2.new(0.5, -110, 0.4, -55)
LoadingLogo.BackgroundTransparency = 1
LoadingLogo.BorderSizePixel = 0
LoadingLogo.Image = FinalImageAsset
LoadingLogo.ScaleType = Enum.ScaleType.Fit
LoadingLogo.ZIndex = 101
LoadingLogo.Parent = LoadingFrame

local LoadingText = Instance.new("TextLabel")
LoadingText.Name = "LoadingText"
LoadingText.Size = UDim2.new(0, 250, 0, 30)
LoadingText.Position = UDim2.new(0.5, -125, 0.4, 65)
LoadingText.BackgroundTransparency = 1
LoadingText.BorderSizePixel = 0
LoadingText.Text = "LOADING MOBILE DORY HUB..."
LoadingText.TextColor3 = Color3.fromRGB(255, 255, 255)
LoadingText.TextSize = 11
LoadingText.Font = Enum.Font.Arcade
LoadingText.ZIndex = 101
LoadingText.Parent = LoadingFrame

local MinimisedBox = Instance.new("ImageButton")
MinimisedBox.Name = "MinimisedBox"
MinimisedBox.Size = UDim2.new(0, 110, 0, 55)
MinimisedBox.Position = UDim2.new(0.5, -55, 0.02, 0)
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
MainFrame.Size = UDim2.new(0, 480, 0, 290)
MainFrame.Position = UDim2.new(0.5, -240, 0.5, -145)
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 17)
MainFrame.BackgroundTransparency = 0.05
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Visible = false
MainFrame.ZIndex = 1
MainFrame.Parent = ScreenGui

local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0, 10)
MainCorner.Parent = MainFrame

local TopBar = Instance.new("Frame")
TopBar.Name = "TopBar"
TopBar.Size = UDim2.new(1, 0, 0, 38)
TopBar.BackgroundTransparency = 1
TopBar.BorderSizePixel = 0
TopBar.ZIndex = 2
TopBar.Parent = MainFrame

local LogoImg = Instance.new("ImageLabel")
LogoImg.Size = UDim2.new(0, 20, 0, 20)
LogoImg.Position = UDim2.new(0, 10, 0.5, -10)
LogoImg.BackgroundTransparency = 1
LogoImg.Image = FinalImageAsset
LogoImg.ScaleType = Enum.ScaleType.Fit
LogoImg.ZIndex = 2
LogoImg.Parent = TopBar

local TitleLabel = Instance.new("TextLabel")
TitleLabel.Name = "TitleLabel"
TitleLabel.Size = UDim2.new(0, 220, 1, 0)
TitleLabel.Position = UDim2.new(0, 35, 0, 0)
TitleLabel.BackgroundTransparency = 1
TitleLabel.BorderSizePixel = 0
TitleLabel.Text = "DORY HUB <font color=\"rgb(130,130,140)\">MOBILE V7</font>"
TitleLabel.TextColor3 = Color3.fromRGB(240, 240, 245)
TitleLabel.TextSize = 10
TitleLabel.Font = Enum.Font.Arcade
TitleLabel.TextXAlignment = Enum.TextXAlignment.Left
TitleLabel.RichText = true
TitleLabel.ZIndex = 2
TitleLabel.Parent = TopBar

local ControlFrame = Instance.new("Frame")
ControlFrame.Name = "ControlFrame"
ControlFrame.Size = UDim2.new(0, 180, 1, 0)
ControlFrame.Position = UDim2.new(1, -180, 0, 0)
ControlFrame.BackgroundTransparency = 1
ControlFrame.BorderSizePixel = 0
ControlFrame.ZIndex = 2
ControlFrame.Parent = TopBar

local DiscordBtn = Instance.new("ImageButton")
DiscordBtn.Name = "DiscordBtn"
DiscordBtn.Size = UDim2.new(0, 22, 0, 22)
DiscordBtn.Position = UDim2.new(0, 5, 0.5, -11)
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
PingLabel.Size = UDim2.new(0, 55, 1, 0)
PingLabel.Position = UDim2.new(0, 30, 0, 0)
PingLabel.BackgroundTransparency = 1
PingLabel.Text = "0MS"
PingLabel.TextColor3 = Color3.fromRGB(130, 130, 140)
PingLabel.TextSize = 9
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
MinimizeBtn.Size = UDim2.new(0, 24, 0, 24)
MinimizeBtn.Position = UDim2.new(0, 100, 0.5, -12)
MinimizeBtn.BackgroundTransparency = 1
MinimizeBtn.Text = "-"
MinimizeBtn.TextColor3 = Color3.fromRGB(160, 160, 170)
MinimizeBtn.TextSize = 12
MinimizeBtn.Font = Enum.Font.Arcade
MinimizeBtn.ZIndex = 2
MinimizeBtn.Parent = ControlFrame

local CloseBtn = Instance.new("TextButton")
CloseBtn.Name = "CloseBtn"
CloseBtn.Size = UDim2.new(0, 24, 0, 24)
CloseBtn.Position = UDim2.new(0, 130, 0.5, -12)
CloseBtn.BackgroundTransparency = 1
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.fromRGB(160, 160, 170)
CloseBtn.TextSize = 10
CloseBtn.Font = Enum.Font.Arcade
CloseBtn.ZIndex = 2
CloseBtn.Parent = ControlFrame

local Sidebar = Instance.new("ScrollingFrame")
Sidebar.Name = "Sidebar"
Sidebar.Size = UDim2.new(0, 100, 1, -45)
Sidebar.Position = UDim2.new(0, 8, 0, 40)
Sidebar.BackgroundTransparency = 1
Sidebar.BorderSizePixel = 0
Sidebar.CanvasSize = UDim2.new(0, 0, 0, 0)
Sidebar.ScrollBarThickness = 0
Sidebar.ZIndex = 2
Sidebar.Parent = MainFrame

local SB_Layout = Instance.new("UIListLayout")
SB_Layout.SortOrder = Enum.SortOrder.LayoutOrder
SB_Layout.Padding = UDim.new(0, 4)
SB_Layout.Parent = Sidebar

local ContentArea = Instance.new("Frame")
ContentArea.Name = "ContentArea"
ContentArea.Size = UDim2.new(1, -120, 1, -45)
ContentArea.Position = UDim2.new(0, 114, 0, 40)
ContentArea.BackgroundTransparency = 1
ContentArea.BorderSizePixel = 0
ContentArea.ZIndex = 2
ContentArea.Parent = MainFrame

local activeTabBtn = nil
local activeTabPage = nil

local function CreateTab(name, isDefault)
    local TabBtn = Instance.new("TextButton")
    TabBtn.Size = UDim2.new(1, 0, 0, 30)
    TabBtn.BackgroundTransparency = isDefault and 0 or 1
    TabBtn.BackgroundColor3 = Color3.fromRGB(25, 25, 30)
    TabBtn.BorderSizePixel = 0
    TabBtn.Text = " " .. string.upper(name)
    TabBtn.TextColor3 = isDefault and Color3.fromRGB(255, 255, 255) or Color3.fromRGB(130, 130, 140)
    TabBtn.TextSize = 9
    TabBtn.Font = Enum.Font.Arcade
    TabBtn.TextXAlignment = Enum.TextXAlignment.Left
    TabBtn.ZIndex = 2
    TabBtn.Parent = Sidebar

    local TB_Corner = Instance.new("UICorner")
    TB_Corner.CornerRadius = UDim.new(0, 6)
    TB_Corner.Parent = TabBtn

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
    PageLayout.Padding = UDim.new(0, 8)
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

local HomeTab = CreateTab("Home", false)

local HomeCenterContainer = Instance.new("Frame")
HomeCenterContainer.Size = UDim2.new(1, 0, 1, 0)
HomeCenterContainer.Position = UDim2.new(0, 0, 0, 0)
HomeCenterContainer.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
HomeCenterContainer.BackgroundTransparency = 0.5
HomeCenterContainer.BorderSizePixel = 0
HomeCenterContainer.ZIndex = 2
HomeCenterContainer.Parent = HomeTab
Instance.new("UICorner", HomeCenterContainer).CornerRadius = UDim.new(0, 8)

local ProfileNameLbl = Instance.new("TextLabel")
ProfileNameLbl.Size = UDim2.new(1, -10, 0, 24)
ProfileNameLbl.Position = UDim2.new(0, 5, 0, 10)
ProfileNameLbl.BackgroundTransparency = 1
ProfileNameLbl.Text = "USER: " .. LocalPlayer.Name
ProfileNameLbl.TextColor3 = Color3.fromRGB(255, 255, 255)
ProfileNameLbl.TextSize = 10
ProfileNameLbl.Font = Enum.Font.Arcade
ProfileNameLbl.TextXAlignment = Enum.TextXAlignment.Left
ProfileNameLbl.ZIndex = 2
ProfileNameLbl.Parent = HomeCenterContainer

local ExecutorLbl = Instance.new("TextLabel")
ExecutorLbl.Size = UDim2.new(1, -10, 0, 24)
ExecutorLbl.Position = UDim2.new(0, 5, 0, 38)
ExecutorLbl.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
ExecutorLbl.BackgroundTransparency = 0.3
ExecutorLbl.BorderSizePixel = 0
ExecutorLbl.Text = " EXECUTOR: " .. (identifyexecutor and identifyexecutor() or "UNKNOWN")
ExecutorLbl.TextColor3 = Color3.fromRGB(100, 200, 255)
ExecutorLbl.TextSize = 9
ExecutorLbl.Font = Enum.Font.Arcade
ExecutorLbl.TextXAlignment = Enum.TextXAlignment.Left
ExecutorLbl.ZIndex = 2
ExecutorLbl.Parent = HomeCenterContainer
Instance.new("UICorner", ExecutorLbl).CornerRadius = UDim.new(0, 6)

local DeviceLbl = Instance.new("TextLabel")
DeviceLbl.Size = UDim2.new(1, -10, 0, 24)
DeviceLbl.Position = UDim2.new(0, 5, 0, 68)
DeviceLbl.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
DeviceLbl.BackgroundTransparency = 0.3
DeviceLbl.BorderSizePixel = 0
DeviceLbl.Text = " PLATFORM: MOBILE / TOUCH"
DeviceLbl.TextColor3 = Color3.fromRGB(240, 200, 80)
DeviceLbl.TextSize = 9
DeviceLbl.Font = Enum.Font.Arcade
DeviceLbl.TextXAlignment = Enum.TextXAlignment.Left
DeviceLbl.ZIndex = 2
DeviceLbl.Parent = HomeCenterContainer
Instance.new("UICorner", DeviceLbl).CornerRadius = UDim.new(0, 6)

local GameInfoLbl = Instance.new("TextLabel")
GameInfoLbl.Size = UDim2.new(1, -10, 0, 24)
GameInfoLbl.Position = UDim2.new(0, 5, 0, 98)
GameInfoLbl.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
GameInfoLbl.BackgroundTransparency = 0.3
GameInfoLbl.BorderSizePixel = 0
GameInfoLbl.Text = " GAME: RIDE A PET"
GameInfoLbl.TextColor3 = Color3.fromRGB(180, 100, 255)
GameInfoLbl.TextSize = 9
GameInfoLbl.Font = Enum.Font.Arcade
GameInfoLbl.TextXAlignment = Enum.TextXAlignment.Left
GameInfoLbl.ZIndex = 2
GameInfoLbl.Parent = HomeCenterContainer
Instance.new("UICorner", GameInfoLbl).CornerRadius = UDim.new(0, 6)

local ExtraInfoLbl = Instance.new("TextLabel")
ExtraInfoLbl.Size = UDim2.new(1, -10, 0, 24)
ExtraInfoLbl.Position = UDim2.new(0, 5, 0, 128)
ExtraInfoLbl.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
ExtraInfoLbl.BackgroundTransparency = 0.3
ExtraInfoLbl.BorderSizePixel = 0
ExtraInfoLbl.Text = " PING: 0 MS"
ExtraInfoLbl.TextColor3 = Color3.fromRGB(80, 200, 120)
ExtraInfoLbl.TextSize = 9
ExtraInfoLbl.Font = Enum.Font.Arcade
ExtraInfoLbl.TextXAlignment = Enum.TextXAlignment.Left
ExtraInfoLbl.ZIndex = 2
ExtraInfoLbl.Parent = HomeCenterContainer
Instance.new("UICorner", ExtraInfoLbl).CornerRadius = UDim.new(0, 6)

task.spawn(function()
    while true do
        pcall(function()
            local ping = math.floor(Stats.Network.ServerStatsItem["Data Ping"]:GetValue())
            ExtraInfoLbl.Text = " PING: " .. ping .. " MS"
        end)
        task.wait(1)
    end
end)

local MainTab = CreateTab("Main", true)

local StealingSection = Instance.new("Frame")
StealingSection.Size = UDim2.new(1, 0, 0, 235)
StealingSection.Position = UDim2.new(0, 0, 0, 0)
StealingSection.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
StealingSection.BackgroundTransparency = 0.6
StealingSection.BorderSizePixel = 0
StealingSection.ZIndex = 2
StealingSection.Parent = MainTab
Instance.new("UICorner", StealingSection).CornerRadius = UDim.new(0, 8)

local SS_Title = Instance.new("TextLabel")
SS_Title.Size = UDim2.new(1, -10, 0, 20)
SS_Title.Position = UDim2.new(0, 6, 0, 4)
SS_Title.BackgroundTransparency = 1
SS_Title.Text = "EGG STEALER CONTROLLER"
SS_Title.TextColor3 = Color3.fromRGB(140, 140, 150)
SS_Title.TextSize = 9
SS_Title.Font = Enum.Font.Arcade
SS_Title.TextXAlignment = Enum.TextXAlignment.Left
SS_Title.ZIndex = 2
SS_Title.Parent = StealingSection

local ScanBtn = Instance.new("TextButton")
ScanBtn.Size = UDim2.new(0, 105, 0, 26)
ScanBtn.Position = UDim2.new(0, 6, 0, 26)
ScanBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
ScanBtn.BorderSizePixel = 0
ScanBtn.Text = "SCAN"
ScanBtn.TextColor3 = Color3.fromRGB(240, 200, 80)
ScanBtn.TextSize = 9
ScanBtn.Font = Enum.Font.Arcade
ScanBtn.ZIndex = 2
ScanBtn.Parent = StealingSection
Instance.new("UICorner", ScanBtn).CornerRadius = UDim.new(0, 6)

local SetHomeBtn = Instance.new("TextButton")
SetHomeBtn.Size = UDim2.new(0, 105, 0, 26)
SetHomeBtn.Position = UDim2.new(0, 116, 0, 26)
SetHomeBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
SetHomeBtn.BorderSizePixel = 0
SetHomeBtn.Text = "PIN HOME"
SetHomeBtn.TextColor3 = Color3.fromRGB(200, 200, 210)
SetHomeBtn.TextSize = 9
SetHomeBtn.Font = Enum.Font.Arcade
SetHomeBtn.ZIndex = 2
SetHomeBtn.Parent = StealingSection
Instance.new("UICorner", SetHomeBtn).CornerRadius = UDim.new(0, 6)

local StartStealBtn = Instance.new("TextButton")
StartStealBtn.Size = UDim2.new(0, 115, 0, 26)
StartStealBtn.Position = UDim2.new(0, 226, 0, 26)
StartStealBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
StartStealBtn.BorderSizePixel = 0
StartStealBtn.Text = "START STEAL"
StartStealBtn.TextColor3 = Color3.fromRGB(80, 200, 120)
StartStealBtn.TextSize = 9
StartStealBtn.Font = Enum.Font.Arcade
StartStealBtn.ZIndex = 2
StartStealBtn.Parent = StealingSection
Instance.new("UICorner", StartStealBtn).CornerRadius = UDim.new(0, 6)

local EggListScroll = Instance.new("ScrollingFrame")
EggListScroll.Size = UDim2.new(1, -12, 0, 95)
EggListScroll.Position = UDim2.new(0, 6, 0, 56)
EggListScroll.BackgroundColor3 = Color3.fromRGB(22, 22, 26)
EggListScroll.BackgroundTransparency = 0.5
EggListScroll.BorderSizePixel = 0
EggListScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
EggListScroll.AutomaticCanvasSize = Enum.AutomaticSize.Y
EggListScroll.ScrollBarThickness = 2
EggListScroll.ZIndex = 2
EggListScroll.Parent = StealingSection
Instance.new("UICorner", EggListScroll).CornerRadius = UDim.new(0, 6)
local ELS_Layout = Instance.new("UIListLayout") ELS_Layout.SortOrder = Enum.SortOrder.LayoutOrder ELS_Layout.Padding = UDim.new(0, 4) ELS_Layout.Parent = EggListScroll

local LogFrame = Instance.new("ScrollingFrame")
LogFrame.Size = UDim2.new(1, -12, 0, 70)
LogFrame.Position = UDim2.new(0, 6, 0, 156)
LogFrame.BackgroundColor3 = Color3.fromRGB(22, 22, 26)
LogFrame.BackgroundTransparency = 0.5
LogFrame.BorderSizePixel = 0
LogFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
LogFrame.AutomaticCanvasSize = Enum.AutomaticSize.Y
LogFrame.ScrollBarThickness = 2
LogFrame.ZIndex = 2
LogFrame.Parent = StealingSection
Instance.new("UICorner", LogFrame).CornerRadius = UDim.new(0, 6)
local LF_Layout = Instance.new("UIListLayout") LF_Layout.SortOrder = Enum.SortOrder.LayoutOrder LF_Layout.Padding = UDim.new(0, 4) LF_Layout.Parent = LogFrame

local function AddLog(txt)
    local lbl = Instance.new("TextLabel")
    lbl.Size = UDim2.new(1, 0, 0, 18)
    lbl.BackgroundTransparency = 1
    lbl.Text = "> " .. string.upper(txt)
    lbl.TextColor3 = Color3.fromRGB(210, 210, 220)
    lbl.TextSize = 8
    lbl.Font = Enum.Font.Arcade
    lbl.TextXAlignment = Enum.TextXAlignment.Left
    lbl.ZIndex = 2
    lbl.Parent = LogFrame
end

AddLog("Mobile system ready.")

local availableEggs = {}
local isStealingActive = false
local savedHomePosition = nil

SetHomeBtn.MouseButton1Click:Connect(function()
    if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        savedHomePosition = LocalPlayer.Character.HumanoidRootPart.CFrame
        SetHomeBtn.TextColor3 = Color3.fromRGB(80, 200, 120)
        AddLog("Home pinned.")
    end
end)

local function GetRealEggInfo(obj)
    local foundText = ""
    for _, desc in ipairs(obj:GetDescendants()) do
        if desc:IsA("TextLabel") or desc:IsA("TextBox") then
            local t = desc.Text
            if t and t ~= "" and not string.find(string.upper(t), "DORY") then
                foundText = t
                break
            end
        end
    end
    if foundText == "" then
        for _, desc in ipairs(obj.Parent:GetChildren()) do
            if desc ~= obj and desc:IsA("BillboardGui") then
                for _, subDesc in ipairs(desc:GetDescendants()) do
                    if (subDesc:IsA("TextLabel") or subDesc:IsA("TextBox")) and subDesc.Text ~= "" then
                        foundText = subDesc.Text
                        break
                    end
                end
            end
        end
    end
    if foundText == "" then foundText = "Normal Egg" end
    return foundText
end

local function IsInsideAnyPlotOrBase(obj)
    local parent = obj.Parent
    while parent and parent ~= Workspace do
        local nameLower = string.lower(parent.Name)
        if string.find(nameLower, "plot") or string.find(nameLower, "base") or string.find(nameLower, "house") or string.find(nameLower, "home") or string.find(nameLower, "owner") or string.find(nameLower, "ไร่ของ") or string.find(nameLower, "pen") or string.find(nameLower, "barn") or string.find(nameLower, "coop") then
            return true
        end
        parent = parent.Parent
    end
    return false
end

local function IsEggCollected(obj)
    if not obj or not obj.Parent then return true end
    if obj:FindFirstChild("Transparency") and obj.Transparency >= 1 then return true end
    local part = obj:FindFirstChild("HumanoidRootPart") or obj:FindFirstChild("PrimaryPart") or obj:FindFirstChildWhichIsA("BasePart")
    if part and part.Transparency >= 1 then return true end
    return false
end

ScanBtn.MouseButton1Click:Connect(function()
    for _, child in ipairs(EggListScroll:GetChildren()) do
        if child:IsA("Frame") then child:Destroy() end
    end
    availableEggs = {}
    local scannedIdentifiers = {}
    
    for _, obj in ipairs(Workspace:GetDescendants()) do
        local nameLower = string.lower(obj.Name)
        local isEggOrValidItem = (string.find(nameLower, "egg") or string.find(nameLower, "item")) and not obj:FindFirstChildOfClass("Humanoid")
        local isPlayerMount = string.find(nameLower, "mount") or string.find(nameLower, "ride") or string.find(nameLower, "pet") or obj:FindFirstChildOfClass("Humanoid")
        
        if isEggOrValidItem and not isPlayerMount then
            if not IsInsideAnyPlotOrBase(obj) and not IsEggCollected(obj) then
                local realInfo = GetRealEggInfo(obj)
                local infoUpper = string.upper(realInfo)
                local isTrashOrDuplicated = string.find(infoUpper, "COMMON") or string.find(infoUpper, "NORMAL") or string.find(infoUpper, "GARBAGE")
                
                if not isTrashOrDuplicated and not scannedIdentifiers[obj.Name .. realInfo] then
                    scannedIdentifiers[obj.Name .. realInfo] = true
                    local part = obj:FindFirstChild("HumanoidRootPart") or obj:FindFirstChild("PrimaryPart") or obj:FindFirstChildWhichIsA("BasePart")
                    if part then
                        local eggData = {
                            model = obj,
                            part = part,
                            name = obj.Name,
                            info = realInfo,
                            selected = false
                        }
                        table.insert(availableEggs, eggData)
                    end
                end
            end
        end
    end
    
    AddLog("Found " .. #availableEggs .. " items.")
    
    for i, data in ipairs(availableEggs) do
        local row = Instance.new("Frame")
        row.Size = UDim2.new(1, 0, 0, 24)
        row.BackgroundColor3 = Color3.fromRGB(30, 30, 38)
        row.BorderSizePixel = 0
        row.ZIndex = 2
        row.Parent = EggListScroll
        Instance.new("UICorner", row).CornerRadius = UDim.new(0, 4)
        
        local lbl = Instance.new("TextLabel")
        lbl.Size = UDim2.new(1, -55, 1, 0)
        lbl.Position = UDim2.new(0, 6, 0, 0)
        lbl.BackgroundTransparency = 1
        lbl.Text = data.name .. " (" .. data.info .. ")"
        lbl.TextColor3 = Color3.fromRGB(220, 220, 230)
        lbl.TextSize = 8
        lbl.Font = Enum.Font.Arcade
        lbl.TextXAlignment = Enum.TextXAlignment.Left
        lbl.ZIndex = 2
        lbl.Parent = row
        
        local toggleBtn = Instance.new("TextButton")
        toggleBtn.Size = UDim2.new(0, 42, 0, 18)
        toggleBtn.Position = UDim2.new(1, -45, 0.5, -9)
        toggleBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 60)
        toggleBtn.BorderSizePixel = 0
        toggleBtn.Text = "OFF"
        toggleBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
        toggleBtn.TextSize = 8
        toggleBtn.Font = Enum.Font.Arcade
        toggleBtn.ZIndex = 2
        toggleBtn.Parent = row
        Instance.new("UICorner", toggleBtn).CornerRadius = UDim.new(0, 4)
        
        toggleBtn.MouseButton1Click:Connect(function()
            data.selected = not data.selected
            if data.selected then
                toggleBtn.Text = "ON"
                toggleBtn.TextColor3 = Color3.fromRGB(80, 200, 120)
                toggleBtn.BackgroundColor3 = Color3.fromRGB(30, 60, 40)
            else
                toggleBtn.Text = "OFF"
                toggleBtn.TextColor3 = Color3.fromRGB(220, 80, 80)
                toggleBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 60)
            end
        end)
    end
end)

StartStealBtn.MouseButton1Click:Connect(function()
    isStealingActive = not isStealingActive
    if isStealingActive then
        StartStealBtn.Text = "ACTIVE"
        StartStealBtn.TextColor3 = Color3.fromRGB(240, 200, 80)
    else
        StartStealBtn.Text = "START STEAL"
        StartStealBtn.TextColor3 = Color3.fromRGB(80, 200, 120)
        AddLog("Stopped.")
    end
end)

RunService.Stepped:Connect(function()
    if isStealingActive and LocalPlayer.Character then
        for _, part in ipairs(LocalPlayer.Character:GetDescendants()) do
            if part:IsA("BasePart") then part.CanCollide = false end
        end
    end
end)

task.spawn(function()
    while true do
        if isStealingActive then
            pcall(function()
                local char = LocalPlayer.Character
                if char and char:FindFirstChild("HumanoidRootPart") then
                    local hrp = char.HumanoidRootPart
                    local targetFound = false
                    
                    for _, data in ipairs(availableEggs) do
                        if data.selected and data.part and data.part.Parent and not IsEggCollected(data.model) and isStealingActive then
                            targetFound = true
                            AddLog("Going: " .. data.name)
                            
                            local targetPart = data.part
                            while targetPart and targetPart.Parent and not IsEggCollected(data.model) and isStealingActive and data.selected do
                                local dir = (targetPart.Position - hrp.Position)
                                if dir.Magnitude < 5 then break end
                                hrp.Velocity = Vector3.new(0, 0, 0)
                                hrp.CFrame = CFrame.new(hrp.Position, targetPart.Position) + (dir.Unit * math.min(70 * 0.1, dir.Magnitude))
                                RunService.Heartbeat:Wait()
                            end
                            
                            AddLog("Collecting...")
                            VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.E, false, game)
                            task.wait(0.2)
                            VirtualInputManager:SendKeyEvent(false, Enum.KeyCode.E, false, game)
                            task.wait(0.5)
                            
                            if savedHomePosition then
                                AddLog("Returning home...")
                                local startT = tick()
                                while (tick() - startT) < 3 and isStealingActive do
                                    local bDir = (savedHomePosition.Position - hrp.Position)
                                    if bDir.Magnitude < 5 then break end
                                    hrp.Velocity = Vector3.new(0, 0, 0)
                                    hrp.CFrame = CFrame.new(hrp.Position, savedHomePosition.Position) + (bDir.Unit * math.min(90 * 0.15, bDir.Magnitude))
                                    RunService.Heartbeat:Wait()
                                end
                                hrp.CFrame = savedHomePosition
                                AddLog("Home safe.")
                            end
                            
                            data.selected = false
                        end
                    end
                    
                    if not targetFound then
                        task.wait(2)
                    end
                end
            end)
        end
        task.wait(1)
    end
end)

local MiscTab = CreateTab("Misc", false)

local MiscSection = Instance.new("Frame")
MiscSection.Size = UDim2.new(1, 0, 0, 160)
MiscSection.Position = UDim2.new(0, 0, 0, 0)
MiscSection.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
MiscSection.BackgroundTransparency = 0.6
MiscSection.BorderSizePixel = 0
MiscSection.ZIndex = 2
MiscSection.Parent = MiscTab
Instance.new("UICorner", MiscSection).CornerRadius = UDim.new(0, 8)

local MS_Title = Instance.new("TextLabel")
MS_Title.Size = UDim2.new(1, -10, 0, 20)
MS_Title.Position = UDim2.new(0, 6, 0, 4)
MS_Title.BackgroundTransparency = 1
MS_Title.Text = "MOBILE UTILITIES"
MS_Title.TextColor3 = Color3.fromRGB(140, 140, 150)
MS_Title.TextSize = 9
MS_Title.Font = Enum.Font.Arcade
MS_Title.TextXAlignment = Enum.TextXAlignment.Left
MS_Title.ZIndex = 2
MS_Title.Parent = MiscSection

local RejoinBtn = Instance.new("TextButton")
RejoinBtn.Size = UDim2.new(1, -12, 0, 30)
RejoinBtn.Position = UDim2.new(0, 6, 0, 30)
RejoinBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
RejoinBtn.BorderSizePixel = 0
RejoinBtn.Text = "REJOIN SERVER"
RejoinBtn.TextColor3 = Color3.fromRGB(240, 100, 100)
RejoinBtn.TextSize = 9
RejoinBtn.Font = Enum.Font.Arcade
RejoinBtn.ZIndex = 2
RejoinBtn.Parent = MiscSection
Instance.new("UICorner", RejoinBtn).CornerRadius = UDim.new(0, 6)

RejoinBtn.MouseButton1Click:Connect(function()
    TeleportService:TeleportToPlaceInstance(game.PlaceId, game.JobId, LocalPlayer)
end)

local LowServerBtn = Instance.new("TextButton")
LowServerBtn.Size = UDim2.new(1, -12, 0, 30)
LowServerBtn.Position = UDim2.new(0, 6, 0, 68)
LowServerBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 34)
LowServerBtn.BorderSizePixel = 0
LowServerBtn.Text = "REHOP LOW SERVER"
LowServerBtn.TextColor3 = Color3.fromRGB(120, 220, 255)
LowServerBtn.TextSize = 9
LowServerBtn.Font = Enum.Font.Arcade
LowServerBtn.ZIndex = 2
LowServerBtn.Parent = MiscSection
Instance.new("UICorner", LowServerBtn).CornerRadius = UDim.new(0, 6)

LowServerBtn.MouseButton1Click:Connect(function()
    pcall(function()
        LowServerBtn.Text = "SEARCHING..."
        local servers = {}
        local cursor = ""
        while true do
            local url = "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100"
            if cursor ~= "" then
                url = url .. "&cursor=" .. cursor
            end
            local success, response = pcall(function()
                return HttpService:JSONDecode(game:HttpGet(url))
            end)
            if success and response and response.data then
                for _, s in ipairs(response.data) do
                    if s.playing and s.maxPlayers and s.playing < s.maxPlayers and s.id ~= game.JobId then
                        table.insert(servers, s.id)
                    end
                end
                if response.nextPageCursor then
                    cursor = response.nextPageCursor
                else
                    break
                end
            else
                break
            end
            if #servers > 0 or not cursor then break end
            task.wait(0.2)
        end
        if #servers > 0 then
            local targetId = servers[math.random(1, #servers)]
            LowServerBtn.Text = "TELEPORTING..."
            TeleportService:TeleportToPlaceInstance(game.PlaceId, targetId, LocalPlayer)
        else
            LowServerBtn.Text = "NO SERVER FOUND"
            task.wait(2)
            LowServerBtn.Text = "REHOP LOW SERVER"
        end
    end)
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
    
    local tweenInfo = TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out)
    TweenService:Create(MainFrame, tweenInfo, {Position = UDim2.new(0.5, -240, 0.5, -145), Size = UDim2.new(0, 480, 0, 290)}):Play()
    task.wait(0.3)
    isAnimating = false
end

local function CloseUI()
    if isAnimating or not isOpen then return end
    isAnimating = true
    isOpen = false
    
    local tweenInfo = TweenInfo.new(0.25, Enum.EasingStyle.Quart, Enum.EasingDirection.In)
    TweenService:Create(MainFrame, tweenInfo, {Position = MinimisedBox.Position, Size = MinimisedBox.Size, BackgroundTransparency = 1}):Play()
    task.wait(0.25)
    MainFrame.Visible = false
    MinimisedBox.Visible = true
    isAnimating = false
end

MinimisedBox.MouseButton1Click:Connect(OpenUI)
MinimizeBtn.MouseButton1Click:Connect(CloseUI)
CloseBtn.MouseButton1Click:Connect(function() ScreenGui:Destroy() end)

task.spawn(function()
    task.wait(0.5)
    for i = 1, 2 do
        LoadingText.Text = "LOADING MOBILE HUB."
        task.wait(0.3)
        LoadingText.Text = "LOADING MOBILE HUB.."
        task.wait(0.3)
        LoadingText.Text = "LOADING MOBILE HUB..."
        task.wait(0.3)
    end
    local fadeTween = TweenService:Create(LoadingFrame, TweenInfo.new(0.4), {BackgroundTransparency = 1})
    local fadeLogo = TweenService:Create(LoadingLogo, TweenInfo.new(0.4), {ImageTransparency = 1})
    local fadeText = TweenService:Create(LoadingText, TweenInfo.new(0.4), {TextTransparency = 1})
    fadeTween:Play()
    fadeLogo:Play()
    fadeText:Play()
    fadeText.Completed:Wait()
    LoadingFrame:Destroy()
    OpenUI()
end)
