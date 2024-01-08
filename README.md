## 免費仔的窮途末路
>💭如果有長期營運的決心，還是要花點錢比較好，不管是用雲端、樹莓派還是虛擬主機，<br>為了服務穩定花錢處理對應的配套措施（成本考量或不斷電系統等，根據方式不同有所差異）都是值得的

本來有望使用老家一台電腦架站，但我發現家人玩遊戲會擔心爆ping，那台電腦有時候會下線=_=...

因為做的東西大部分是實驗性質，而且擔心入不敷出，暫時都在尋求免費方案，雖然到目前為止都沒架成功一個穩定的服務在網際網路上=_=（目前只做到用Replit串Supabase開演示給他人看）

不過我深覺當個免費仔是件很困難的事情

***
## 前端類
- Netlify：有每個月部署限額次數，但老實說個人使用好像就蠻...堪用的...？（可能有些人網站做很大流量特別高啊><||）

***
## 資料庫篇
### Supabase
最大的缺點就是沒連接一週會睡著，要上後台叫醒
![image](https://github.com/x200706/Free-to-play-Adventure/assets/99391710/94674fe6-9eae-4595-8a7d-6e9ab4289649)

### 甲骨文免費方案
內含DB

### GCP VM自架DB
GCP內建的資料庫功能是要錢的，VM某些情境下有永久免費的，但這部分倒是有點眉角，我們看看Bing的說明（喂）
>對的，Google Cloud Platform (GCP) 確實有提供一些免費的服務，這被稱為 "Free Tier"。以下是一些重要的細節：
>
>免費試用期：新的 Google Cloud 和 Google Maps Platform 用戶可以利用一個 90 天的試用期，其中包含 300 美元的免費 Cloud Billing 信用額度，用於探索和評估 Google Cloud 和 Google Maps Platform 的產品和服務。
>
>免費層級：所有 Google Cloud 客戶都可以免費使用選定的 Google Cloud 產品，例如 Compute Engine、Cloud Storage 和 BigQuery，但需在指定的每月使用限制內2。當你在免費層級限制內時，這些資源不會對你的免費試用信用額度或你的 Cloud Billing 帳戶的付款方式收費2。
>
>f1-micro：f1-micro 是一種常見的免費 VM 類型，每月可免費使用 720 小時（1 個月）。
>
>請注意，如果你超出了免費層級的限制，或者你的免費試用期結束後，你將需要支付相應的費用。希望這個信息對你有所幫助！

20240108逛紅迪：
```
https://www.reddit.com/r/googlecloud/comments/jocln7/is_google_compute_engine_free_tier_really_free/
再看一次GCP 免費VM的討論串釐清他們免費的定義（？）
不過不知道是不是一超過就開始計價（試用期就是扣300額度）

他不能設置個警示之類的經過同意再開始扣款嗎 萬一因為意外（例如DDOS之類的）超過用量不是很 :aqua_cry:
```

***
## 後端類

（未完待續）
