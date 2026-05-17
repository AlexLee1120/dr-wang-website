# GitHub 上線完整教學

本教學會帶您一步步把網頁放到 GitHub，並開啟免費的網站託管（GitHub Pages）。

完成後您會得到一個可以分享給病人的網址，例如：
`https://alexlee1120.github.io/wang-tm/`

---

## 推薦做法：GitHub Desktop（不用打指令，最適合初學者）

### Step 1：下載並安裝 GitHub Desktop

1. 開啟瀏覽器到 https://desktop.github.com/
2. 點「Download for Windows」
3. 安裝後開啟，用 GitHub 帳號登入（您的帳號是 `alexlee1120`）

### Step 2：在 GitHub 網站建立新 Repository

1. 開啟瀏覽器到 https://github.com/new
2. 填寫資料：
   - **Repository name**：建議用英文，例如 `dr-wang-website` 或 `wang-tm-orthopedic`
   - **Description**（選填）：王廷明醫師個人網頁
   - **Public**：勾選（GitHub Pages 免費版需要 Public）
   - **Add a README**：**不要勾**（我們本地已經有了）
   - **Add .gitignore**：**不要勾**（我們本地已經有了）
3. 點「Create repository」
4. 出現的頁面先保留不關閉，待會兒會用到

### Step 3：把本地資料夾加入 GitHub Desktop

1. 開啟 GitHub Desktop
2. 上方選單 **File → Add Local Repository**
3. 點「Choose...」選擇資料夾：
   `C:\Alex\Github\Tim\王廷明醫師建立個人網頁`
4. 如果出現「This directory does not appear to be a Git repository」，點「**create a repository**」連結
5. 在彈出視窗：
   - Name：保持預設或改成英文
   - Local path：自動填好
   - 點「**Create Repository**」

### Step 4：第一次 Commit（提交變更）

1. 您會在 GitHub Desktop 左側看到所有檔案的清單
2. 左下角輸入：
   - Summary：`首次提交：王廷明醫師個人網頁`
   - Description（選填）：可空白
3. 點藍色按鈕「**Commit to main**」

### Step 5：推送到 GitHub（Publish）

1. 點上方藍色按鈕「**Publish repository**」
2. 在彈出視窗：
   - Name：保持
   - **取消勾選**「Keep this code private」（因為 GitHub Pages 免費版需要 Public）
3. 點「**Publish Repository**」
4. 等待幾秒鐘上傳完成

### Step 6：開啟 GitHub Pages（讓網頁能線上瀏覽）

1. 開啟瀏覽器，到您剛建立的 repo 頁面，例如：
   `https://github.com/alexlee1120/dr-wang-website`
2. 點上方 **Settings**（設定）
3. 左側選單往下找 **Pages**
4. 在「Build and deployment」區塊：
   - **Source**：選擇「Deploy from a branch」
   - **Branch**：選擇 `main` 和 `/ (root)`，點「Save」
5. 等 1-2 分鐘
6. 重新整理頁面，最上方會出現綠色框：
   ```
   ✓ Your site is live at https://alexlee1120.github.io/dr-wang-website/
   ```
7. 點那個網址就能看到您的網站了！

---

## 進階做法：Git 指令（給熟悉終端機的人）

如果您習慣用 Git Bash 或 Windows Terminal：

```bash
# 切換到專案資料夾
cd "C:\Alex\Github\Tim\王廷明醫師建立個人網頁"

# 初始化 Git
git init

# 加入所有檔案
git add .

# 第一次提交
git commit -m "首次提交：王廷明醫師個人網頁"

# 設定分支名為 main
git branch -M main

# 連接遠端 repo（先到 GitHub 建立 repo 拿到網址）
git remote add origin https://github.com/alexlee1120/dr-wang-website.git

# 推送上去
git push -u origin main
```

然後到 GitHub 網頁開啟 Pages（同上方 Step 6）。

---

## 後續更新流程

每次修改網頁後，要把更新推上 GitHub：

### GitHub Desktop 操作：
1. 開啟 GitHub Desktop
2. 它會自動偵測檔案變更
3. 左下輸入更新說明（例如「更新醫師簡介」）
4. 點「Commit to main」
5. 點上方「Push origin」

### Git 指令操作：
```bash
git add .
git commit -m "更新說明"
git push
```

---

## 自訂網域（選擇性，進階）

如果想用自己的網域（例如 `drwang.tw`）而不是 `github.io`：

1. 到網域註冊商（GoDaddy、Namecheap、Gandi 等）購買網域
2. 在 GitHub repo → Settings → Pages → Custom domain 輸入您的網域
3. 在網域註冊商的 DNS 設定加入：
   - CNAME 記錄：指向 `alexlee1120.github.io`
4. 勾選「Enforce HTTPS」（保護病人隱私）

---

## 常見問題

### Q1：推送時要求輸入密碼？
GitHub 已不支援密碼登入，需要用 Personal Access Token（PAT）：
1. 到 https://github.com/settings/tokens
2. 點「Generate new token (classic)」
3. 勾選「repo」權限
4. 產生後複製，當作密碼使用
5. 用 GitHub Desktop 可以避免這個問題

### Q2：網站上線後修改了沒看到變化？
- GitHub Pages 有快取，等 1-2 分鐘
- 按 Ctrl+Shift+R 強制重新整理
- 確認 Push 真的成功了

### Q3：YouTube 影片在我電腦能播放，網站上不行？
- 這是 YouTube 頻道擁有者禁止嵌入造成的
- 目前網站已改成「點擊跳轉 YouTube」設計來繞過這個限制
- 若希望真正內嵌播放，需請「手術善其事」頻道在 YouTube Studio 開啟嵌入權限

### Q4：要怎麼把網址分享給病人？
- 短網址：用 [Bitly](https://bitly.com/) 或 [PicSee](https://picsee.io/) 縮短
- QR Code：用 [QR Code Generator](https://www.qr-code-generator.com/) 產生
- LINE OA：在主選單加入這個網址

---

## 完成後的建議

1. ✅ 把網址加到 LINE 官方帳號的主選單與自動回覆
2. ✅ 印製 QR Code 海報，放在診間給病人掃描
3. ✅ 加入 Google Search Console 追蹤搜尋曝光
4. ✅ 加入 Google Analytics 看訪客行為
5. ✅ 定期更新衛教影片與測驗題目

需要任何一項的詳細教學，再告訴我。
