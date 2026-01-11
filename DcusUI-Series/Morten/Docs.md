# Dcus UI Library v2.3 - Documentation

## iksuwuによって作成された、洗練されたダークテーマのRoblox用UIライブラリです。PC環境での動作に最適化されています
### ブレインロットを盗むなどで検知されず、使いやすくオシャレなUIとなっています。※当ドキュメントはAI ( Gemini )により生成されました

---

## 🚀 導入方法

まずはライブラリを `loadstring` で読み込み、メインウィンドウを初期化します。

``lua
local UI = require(game.ReplicatedStorage.Lib)

local Window = UI:New({
    Title = "Iksuwu Hub",
    Footer = "By iksuwu • v2.3"
})
``

---

## 📂 カテゴリ（タブ）の追加

サイドバーに新しいタブを作成します。返り値の `Tab` オブジェクトに対して各コンポーネントを追加していきます。

``lua
local PlayerTab = Window:NewTab("Player")
``

---

## 🛠 利用可能なコンポーネント

### 1. ラベル (Label)
ユーザーへの指示や情報を表示します。
``lua
Tab:Label({ Text = "説明文をここに記載" })
``

### 2. 段落 (Paragraph)
タイトル付きのより詳細な説明セクションです。
``lua
Tab:Paragraph({ Title = "注意", Content = "ここに詳細な内容を記載します。" })
``

### 3. ボタン (Button)
クリック時に特定の関数を実行します。
``lua
Tab:Button({
    Name = "Execute Script",
    Callback = function() print("実行されました") end
})
``

### 4. トグル (Toggle)
オン/オフの切り替えスイッチです。
``lua
Tab:Toggle({
    Name = "Infinite Jump",
    Default = false,
    Callback = function(state) print("現在の状態:", state) end
})
``

### 5. スライダー (Slider)
数値の調整を行います。
``lua
Tab:Slider({
    Name = "WalkSpeed",
    Min = 16, Max = 100, Default = 16, Rounding = 0,
    Callback = function(v) print("値:", v) end
})
``

### 6. ドロップダウン (Dropdown)
リストから1つの項目を選択させます。
``lua
Tab:Dropdown({
    Name = "Select Tool",
    List = {"Tool A", "Tool B", "Tool C"},
    Callback = function(selected) print("選択:", selected) end
})
``

---

## 📱 モバイル & 利便性機能

- **オートスケーリング**: モバイル端末ではUI全体が自動で0.8倍になり、操作性を確保。
- **ドラッグ移動**: タイトルバーを掴んでウィンドウを自由に移動可能（スマホのタップにも対応）。
- **ウィンドウ開閉**: 右上の「≡」ボタンでメニューを折り畳めます。

---

## 📜 完全な実装例

``lua
local UI = require(game.ReplicatedStorage.Lib)

local Window = UI:New({
	Title = "Iksuwu Hub",
	Footer = "By iksuwu • v2.3"
})

local PlayerTab = Window:NewTab("Player")

PlayerTab:Toggle({
	Name = "Infinite Jump",
	Default = false,
	Callback = function(v) _G.InfJump = v end
})

PlayerTab:Slider({
	Name = "WalkSpeed",
	Min = 16, Max = 150, Default = 16, Rounding = 0,
	Callback = function(v)
		local hum = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
		if hum then hum.WalkSpeed = v end
	end
})

local TrollTab = Window:NewTab("Troll")
TrollTab:Dropdown({
	Name = "Annoy",
	List = {"Fling", "Freeze", "Kill"},
	Callback = function(s) print("Selected action: " .. s) end
})
``
