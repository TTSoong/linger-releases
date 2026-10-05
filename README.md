# Linger 下載

Linger 是可以裝在自家 NAS 上的待辦事項與持續提醒服務：資料只存在你自己的 NAS，
Mac App 會在時間到時跳出置頂提醒，處理之前不會消失。

👉 **[前往最新版本下載](https://github.com/TTSoong/linger-releases/releases/latest)**

本頁只提供安裝檔下載；原始碼不公開。

## 系統需求

Linger 很輕量，一般家用 NAS 都跑得動。

| 項目 | 需求 |
| --- | --- |
| 處理器 | Intel／AMD（x86_64）或 64 位元 ARM；平常幾乎不占 CPU。不支援 32 位元 ARM 的舊機種 |
| 記憶體 | 執行時約 250 MB，最多 512 MB；建議 NAS 或虛擬機至少 1 GB（Synology 建議 2 GB 以上） |
| 硬碟 | 約 1 GB（程式約 400 MB，你的資料與每日備份通常只有幾 MB） |
| Synology | DSM 7.2.1 以上，且機型支援 Container Manager（套件中心搜得到 Container Manager 即可） |
| Mac | macOS 13 以上 |

網址一律是 `http://`（不是 https），預設連接埠 8088，安裝時可以改。
安裝與更新都不需要連網；裝好後會定期向 GitHub 查詢有沒有新版本（可關閉）。

## 下載哪一個？

| 我要安裝在 | 下載的檔案 |
| --- | --- |
| NAS 的虛擬機（VM），或裝了 Docker 的 Linux 主機 | `linger-版本-docker.zip` |
| Synology NAS（Intel／AMD 處理器，多數「+」機型） | `linger-版本-synology-x86_64.spk` |
| Synology NAS（ARM 處理器） | `linger-版本-synology-armv8.spk` |
| Mac（Apple M 系列晶片） | `Linger_版本_aarch64.zip` |
| Mac（Intel 處理器） | `Linger_版本_x64.zip` |

不確定 Synology 的處理器：DSM 的「控制台 › 資訊中心 › 一般 › 處理器」。
不確定 Mac 的晶片：左上角蘋果選單 › 關於這台 Mac，看「晶片」或「處理器」。

## 安裝伺服器（擇一）

### 方法一：NAS 的虛擬機或 Linux 主機（docker.zip）

需要：已安裝 Docker 的 Linux（x86_64 或 64 位元 ARM）、記憶體 1 GB 以上、硬碟約 1 GB。

1. 下載 `linger-版本-docker.zip` 並解壓縮，裡面的 `README.txt` 有完整說明
2. 擇一：
   - **交給 AI**：把資料夾交給 AI 助理（例如 Claude Code），說「請依照 AI_INSTALL.md，把 Linger 安裝到我的虛擬機上」。
     AI 會問你主機 IP 和登入帳號；需要管理員密碼時，AI 會給你一行指令讓你自己貼上執行，不用把密碼告訴 AI
   - **自己執行**：把資料夾放到主機上，在資料夾內執行 `sudo sh install.sh`
3. 安裝程式最後會印出網址（例如 `http://192.168.1.50:8088/`），用瀏覽器打開
4. 第一次打開會出現「歡迎使用 Linger」設定頁：在網頁上設定管理員帳號、密碼與時區，完成後登入即可

### 方法二：Synology 套件中心

需要 DSM 7.2.1 以上、記憶體建議 2 GB 以上，並已從套件中心安裝 **Container Manager**（不支援 Container Manager 的機型無法安裝）。

1. 下載對應處理器的 `.spk`
2. 套件中心 › 右上角「手動安裝」› 選擇下載的 `.spk`
3. 出現「第三方套件」提示時按「是」，依畫面完成安裝。安裝精靈會問網頁連接埠，預設 8088；若已被其他服務使用，改成其他數字（例如 18088）
4. 用瀏覽器開啟 `http://<NAS IP>:連接埠/`（預設 `http://<NAS IP>:8088/`），建立你的帳號

## 安裝 Mac App

需要 macOS 13 以上，Apple M 系列晶片或 Intel 處理器皆可。

1. 下載對應晶片的 `.zip`，雙擊解壓縮得到 Linger
2. 雙擊 Linger 開啟。第一次若出現「無法驗證開發者」：
   關閉對話框 › 打開「系統設定 › 隱私權與安全性」› 往下找到「已阻擋 Linger」› 按「強制打開」
3. App 會提示「移到應用程式資料夾」，按一下即完成
4. 輸入 NAS 的位址（例如 `http://192.168.1.10:8088`）並登入

## 更新

- **Mac App**：下載新版 `.zip` 解壓縮後開啟，按「移到應用程式資料夾」就會取代舊版，設定與資料都保留
- **伺服器**：下載新版安裝包，用**當初安裝的同一種方法**再裝一次即可，資料會保留
  （AI 安裝的版本，跟 AI 說「依 AI_INSTALL.md 的『更新到新版本』更新 Linger」）
  - 安裝程式會自動找到原本的安裝位置與資料，不會接到空的資料
  - 虛擬機版與 Synology 套件是兩種獨立的安裝方式，資料放在不同地方，請不要混用
