## ~~免費仔的窮途末路之旅~~
>💭如果有長期營運的決心，還是要花點錢比較好，不管是用雲端、樹莓派還是虛擬主機，<br>為了服務穩定花錢處理對應的配套措施（成本考量或不斷電系統等，根據方式不同有所差異）都是值得的

~~老家用弟弟電腦架站的研究也是同步進行中，目前弟弟想投資路由器， 電腦有人日常使用不適合當Server了~~但實在還是對網路上的各項免費方案很好奇...

雖然觀望了很久，但到目前為止都沒架成功一個穩定的後端服務在網際網路上=_=（目前只做到用Replit串Supabase開演示給他人看）

不過我深覺當個免費仔是件很困難的事情，故在這邊整理這份筆記...

***
## 前端類
### Netlify
以前拿來架過Hexo，有每個月部署限額次數，但老實說個人使用好像就蠻...堪用的...？（可能有些人網站做很大流量特別高啊><||）
### Vercel
下方後端有用到會詳細說明
### [Render](https://render.com/)
後端要錢，Docker上去發現是後端也一樣[要錢](https://ithelp.ithome.com.tw/articles/10255630)
***
## 資料庫
### Supabase
DB：沒連接一週會睡著，要上後台叫醒，其他很讚了

![image](https://github.com/x200706/Free-to-play-Adventure/assets/99391710/94674fe6-9eae-4595-8a7d-6e9ab4289649)

### 甲骨文免費方案
內含DB及效能不差的免費ARM主機，但驗證刷卡好難過，20230108用新卡號又試了一次還是不行;w;

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

- [Reddit的相關討論](https://www.reddit.com/r/googlecloud/comments/jocln7/is_google_compute_engine_free_tier_really_free/)
- 其他逛Reddit V2EX討論連結沒放，但這邊有看下來的心得~~懶人包~~：
  - GCP每月1GB網路流量某些情境不太夠
***
## 檔案儲存類
一些功能類似S3的產品
### Supabase Storage
上方的Supabase也有個產品叫Storage->20240502更新：Larvel Driver稀少，要10含以上才有開源Driver能用；雖然Supabase官方說跟S3相容，但用flysystem S3 driver一直遇到路徑錯誤（例如他把我endpoint後方有個`v1/s3/storage`重複兩次變成`v1/s3/storage/v1/s3/storage`）導致各種異常（像是找不到桶子）的問題
### Cloudinary
後來逛紅迪網，有網友推薦[Cloudinary](https://cloudinary.com/)，可以做為S3的替代品（雖然不是S3相容），查網路資料，原來之前Heroku還是免費但不好儲存資料時，就很多人使用它作為雲端儲存的方案了

我把Laravel接通的過程放在[這邊](https://x200706.bearblog.dev/serverless-laravelcloudinary)

***
## 全／後端類
### GCP永久免費主機
但網路流量超過要錢rr（延伸閱讀：[紅迪上大家的投票（關於如何託管Laravel）](https://www.reddit.com/r/laravel/comments/xyphv9/how_do_you_host_laravel_app/)，這篇有人AWS帳單好高rrr，雲端真心貴）

話說如果用GCP架設的話，不能只懂Compute Engine，防火牆規則之類可能要了解下，預設VM那邊只能開80跟443－但設置後會不會觸發計費得詳讀條款！！

### [Vercel](https://vercel.com/)
20240427在幫Laravel找尋雲端PaSS以外的可能性，先是在Profreehost[折騰一番](https://x200706.bearblog.dev/composer-install/)後，發現這種傳統免空日後困難可能更多，實在不是一個很有效率的方式

去紅迪看看大家推薦近年來免費部署Laravel最佳方式，找到這個（其實之前聽過，但當時以為很複雜一直沒學><||）

我的Laravel嘗試，原本寫在這裡，但因為篇幅越來越長+後續只更新在部落格[那篇](https://x200706.bearblog.dev/vercellaravel-admin/)，這邊就把舊有內容移除了

***
## 網路組
### 免費域名
#### eu.org
- <https://nic.eu.org/>

### 免費DNS託管
（待撰）

### 免費憑證
- 上方服務商有的會自行提供
#### Let's Encrypt
- Let's Encrypt+主機跑排程自動展延
