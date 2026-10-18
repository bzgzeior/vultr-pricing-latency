# Vultr主機：方案價格與東京機房延遲全解析，新手註冊領 300 美元體驗金

主要客群在台灣、又想把 VPS 月費壓在幾美元，Vultr 是少數能同時滿足這兩個條件的主機商：東京機房 ping 台灣大約 50ms，最低方案每月 2.5 美元起，新用戶註冊還能領 300 美元、30 天內有效的體驗金。這篇把官網目前的產品線、價格、機房選擇邏輯和註冊流程整理成一份可以直接照做的指南，順便講清楚幾個只藏在官方文件裡的限制。

> **選購速覽**
> - 大多數台灣用戶：東京機房 + AMD High Performance 方案，最低約每月 6 美元，延遲約 50ms
> - 純練手測試：美國機房每月 2.5 美元方案最便宜，但只提供 IPv6
> - 新用戶透過活動連結註冊、綁定沒用過的付款方式，即可領 300 美元體驗金，30 天有效
> - 👉 [前往 Vultr 領取 300 美元體驗金](https://bit.ly/VulTR)

## Vultr 主機是什麼定位？適合誰用？

Vultr 走的是自助租用路線：選機房、選規格、選系統，開機後按小時計費，主機刪掉就停止扣款。它在 2014 年成立，母公司 Choopa 本身經營資料中心，目前在 33 個雲端資料中心提供服務，常被拿來跟 DigitalOcean、Linode 一起比較。

幾個對使用體驗影響比較大的特點：

- 儲存全線採用 SSD，較新的方案用 NVMe
- 作業系統涵蓋 Ubuntu、Debian、CentOS 等常見 Linux 發行版，也能直接開 Windows Server
- Marketplace 提供一鍵安裝 WordPress、Docker、GitLab、Joomla、Minecraft 伺服器
- 另有 DNS、雲端儲存服務；自動備份、快照、DDoS 防護屬於加購項目
- 流量從每月 0.5TB 到 15TB、頻寬 1~10Gbps，依方案而定

先說不適合的人：如果你完全不想碰指令，只想上傳檔案就架站，Vultr 會讓你覺得麻煩——它的日常管理基本靠 SSH，後台主要負責開機、重灌和看數據。想省事可以選 RunCloud、Gridpane 這類面板透過 API 接管主機，或直接用 Cloudways 這種全託管服務，代價是單價高一截。

## 全方案價格整理：五條產品線，最低每月 2.5 美元

Vultr 按「產品線 × 規格」組合計價，官網定價頁目前分成五條產品線，Windows 需另外加計授權費。CPU 從 1 核到 24 核、記憶體 1GB 到 96GB、硬碟 25GB 到 1600GB 都有對應方案。

| 產品線 | 硬體規格 | 適合用途 | 價格 | 購買連結 |
| --- | --- | --- | --- | --- |
| 雲端運算（常規性能） | 上一代 Intel CPU + SSD | 部落格、輕量網站、開發測試 | 美國最低 $2.5/月（僅 IPv6），東京 $5/月起 | [查看方案](https://www.vultr.com/pricing/?ref=7268283) |
| 雲端運算（高性能） | 新一代 AMD EPYC / Intel Xeon + NVMe | 效能要求較高的網站與應用 | 東京、大阪最低方案約 $6/月 | [查看方案](https://www.vultr.com/pricing/?ref=7268283) |
| 雲端運算（高頻） | 3GHz+ Intel Xeon + NVMe | 對反應速度敏感的任務 | 東京、大阪最低方案約 $6/月 | [查看方案](https://www.vultr.com/pricing/?ref=7268283) |
| Optimized Cloud Compute | 獨佔新一代 AMD EPYC vCPU + NVMe | 電商、遊戲伺服器、資料庫、影音串流 | 依規格計價 | [查看方案](https://www.vultr.com/pricing/?ref=7268283) |
| VX1 | 獨佔 CPU，網路最高 50Gbps | 雲原生與企業級工作負載 | 依規格計價，按實際使用小時收費 | [查看方案](https://www.vultr.com/pricing/?ref=7268283) |
| Cloud GPU | NVIDIA、AMD 多款 GPU | AI 訓練與推論、高效能運算 | 按小時計費 | [查看方案](https://www.vultr.com/pricing/?ref=7268283) |
| Bare Metal | 整台實體伺服器 | 需要完整硬體資源的場景 | 依規格計價 | [查看方案](https://www.vultr.com/pricing/?ref=7268283) |
| Windows Server | Linux 方案 + Windows 授權 | 需要 Windows 環境的應用 | 實際月費 $26 起 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |

幾個從定價頁挖出來、多數教學不會提的細節：

- VX1 是較新的產品線，官方宣稱每美元效能最高比大型雲商的成本優化方案好 82%，15 秒內開機，而且按每月實際使用小時計費，沒有每月 672 小時的封頂
- Optimized Cloud Compute 的 vCPU 是獨佔的，效能穩定性比共享型方案好；底下還細分通用、CPU 優化、記憶體優化、儲存優化四種取向，分別對應關聯式資料庫、影片編碼與批次處理、MySQL 與快取、MongoDB 這類工作負載
- Cloud GPU 從 NVIDIA 的 H100、L40S 到 AMD 的 MI300X、MI325X 都能按小時租，短時間跑 AI 任務成本可控

### Windows 主機要另計授權費，這筆錢常比主機本身還貴

Windows Server 授權在開機時自動附加在帳單上，費用依方案而定。目前官網列出的配置與價格如下：

| 儲存 | CPU / 記憶體 | 每月流量 | 主機月費 | Windows 授權費 | 購買連結 |
| --- | --- | --- | --- | --- | --- |
| 55GB SSD | 1 核 / 2GB | 2TB | $10 | $16 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |
| 65GB SSD | 2 核 / 2GB | 3TB | $15 | $32 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |
| 80GB SSD | 2 核 / 4GB | 3TB | $20 | $32 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |
| 160GB SSD | 4 核 / 8GB | 4TB | $40 | $64 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |
| 320GB SSD | 6 核 / 16GB | 5TB | $80 | $96 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |
| 640GB SSD | 8 核 / 32GB | 6TB | $160 | $128 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |
| 1280GB SSD | 16 核 / 64GB | 10TB | $320 | $256 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |
| 1600GB SSD | 24 核 / 96GB | 15TB | $640 | $384 | [查看方案](https://www.vultr.com/servers/windows/?ref=7268283) |

實際算下來，最便宜的 Windows 主機每月要付 26 美元（10 美元主機費 + 16 美元授權費），比起最低 2.5 美元的 Linux 方案貴了十倍有餘。系統版本可選 Windows Server 2016 到 2025 的 Datacenter、Standard 與 Core 版。還有一點容易忽略：你手上既有的 Windows 授權不能轉移到 Vultr 使用，這筆費用省不掉。

👉 [查看 Windows 主機全部方案與授權費用](https://www.vultr.com/servers/windows/?ref=7268283)

## 機房怎麼選？台灣用戶首選東京

33 個資料中心裡，亞洲有東京、大阪、新加坡、首爾。對台灣用戶，選擇邏輯很直接：主要客群在台灣，優先東京。

- 東京：ping 台灣約 50ms，線路多走 NTT，偶爾走 PCCW
- 大阪：2023 年啟用的新機房，地理位置離台灣更近，延遲反而比東京多 5~10ms，走 PCCW
- 新加坡、首爾：適合客群在東南亞或韓國
- 洛杉磯：客戶在歐美或做外貿時，全球訪問速度比較平均

機房表現會浮動。有站長在 2023 年重測東京與大阪的 6 美元方案時發現：東京機房較新的 AMD High Performance 效能已經追過 Intel High Frequency；大阪機房剛啟用時效能特別突出，之後隨用戶增多有所回落。同一方案隔一年測出的數字都可能差好幾倍，所以下單前值得自己驗一次——Vultr 把各機房測速點放在官網常見問題裡，東京的 Looking Glass 網址是 hnd-jp-ping.vultr.com，在 CMD 執行 `ping hnd-jp-ping.vultr.com` 就能看到延遲。

延遲多少算合理？雲端服務商 Scaleway 談網路延遲時給過一個參考值：100ms 以內都算可接受。東京機房的 50ms 餘量相當充足。

👉 [查看 Vultr 全部方案與各機房價格](https://www.vultr.com/pricing/?ref=7268283)

## 註冊與開通教學：六步開好第一台主機

整個流程在後台就能完成，大約十分鐘：

1. **註冊帳號**：輸入信箱與密碼建立帳號，收信完成驗證。要領 300 美元體驗金，需使用未註冊過的信箱。
2. **綁定付款方式**：信用卡、銀聯、PayPal、支付寶都支援。只想先用體驗金的話，綁卡時可選「I just want to link my credit card」，先不儲值；用 PayPal 或支付寶付款則從 Account → Make a Payment 進入，過程中留意頁面是否顯示 $300 贈送提示。
3. **補齊資料**：Account → Profile 填基本資訊，建議用英文與半形數字，台灣地址可用中華郵政的地址英譯服務。
4. **部署主機**：點右上角 Deploy+ → Deploy New Server，依序選主機類型、機房、作業系統與規格。想架 WordPress 就到 Marketplace Apps 分頁一鍵安裝。
5. **確認附加功能**：自動備份會加價，自己有備份方案的話可以關掉，再按 Deploy Now。
6. **SSH 連線**：Windows 內建 CMD 執行 `ssh root@你的IP`，第一次連線輸入 yes，密碼在後台 Overview 頁複製，在 CMD 裡按滑鼠右鍵貼上。

👉 [註冊 Vultr 帳號，領取體驗金後開通第一台主機](https://bit.ly/VulTR)

## 按小時計費，但這四個坑要先知道

計費方式本身很簡單：以小時為單位按實際使用時長扣費，主機刪除後停止計費。麻煩的是幾個藏在條款和後台提示裡的限制：

1. **體驗金 30 天過期**：300 美元體驗金超過期限未用完會自動失效，註冊後就把測試排進行事曆。
2. **新帳號預設只能開 1 台**：Vultr 為保護資源，預設每位用戶每月只能建 1 台伺服器，開第二台會跳出限額提示，點 Request a limit increase 提交申請後才會放開。
3. **IP 無法訪問可以換**：刪掉實例重建就能拿到新 IP，在按小時計費的模式下這樣操作沒有額外成本。
4. **規格隨時可調**：Settings → Change Plan 就能升級或降級，不需要重灌系統。

## 開通後怎麼驗證主機性能？

連進主機跑兩個常用的測試腳本，就能有基本判斷：


wget -qO- bench.sh | bash


Bench.sh 負責基本資訊、I/O 和下載速度測試。


wget -qO- https://raw.githubusercontent.com/LemonBench/LemonBench/main/LemonBench.sh | bash -s -- --full


LemonBench 測得更全面，不過路由追蹤節點以中國電信為主，台灣用戶看結果時要留意這個偏差。

前面提到的那次 2023 年測試還有一個附帶結論：東京、大阪各兩台 6 美元機器，測出來的數字和一年前幾乎完全不同。與其糾結任何一篇的測分，不如用體驗金多開幾台、各跑一小時再刪掉，成本幾乎為零，數據卻最貼近你自己的使用環境。

## 常見問題

**Vultr 主機一個月實際花多少錢？**
東京 Linux 主機最低每月 5~6 美元（依方案類型），美國最低 2.5 美元但僅提供 IPv6；Windows 主機計入授權費後最低每月 26 美元。自動備份、快照、DDoS 防護另外加價。

**可以用哪些方式付款？**
信用卡、銀聯、PayPal、支付寶都有支援。

**300 美元體驗金為什麼消失？**
體驗金有效期 30 天，過期未用完會自動失效。領取條件是未註冊過的信箱，加上沒在 Vultr 綁定過的付款方式，兩個條件都要符合。

**完全不懂指令能用嗎？**
開機後可以用後台的 View Console 操作，但日常管理仍以 SSH 為主。只想架網站的話，可以接 RunCloud、Gridpane 這類面板做視覺化管理；想連伺服器都不碰，就選 Cloudways 這類全託管服務，單價會更高。

## 按你的情況這樣選

- 主要客群在台灣、預算有限：東京 AMD High Performance，每月 6 美元上下，先領體驗金開機測一輪再決定續不續
- 純練手、跑腳本：美國 2.5 美元方案夠用，注意它沒有 IPv4
- 要跑 Windows 應用：把授權費算進預算，最低每月 26 美元起
- 電商、資料庫等吃效能的應用：直接看 Optimized Cloud Compute 或 VX1 的獨佔 CPU 方案

下單前最後確認兩件事：到 Account → Make a Payment 看體驗金是否已到帳，以及決定要不要關掉自動備份省點月費。體驗金的窗口只有 30 天，測試節奏排緊一點；用完的機器記得刪掉——按小時計費的規則下，閒置的主機也是錢。

👉 [領取 Vultr 300 美元體驗金，開通第一台主機](https://bit.ly/VulTR)
