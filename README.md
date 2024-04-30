## ~~免費仔的窮途末路之旅~~
>💭如果有長期營運的決心，還是要花點錢比較好，不管是用雲端、樹莓派還是虛擬主機，<br>為了服務穩定花錢處理對應的配套措施（成本考量或不斷電系統等，根據方式不同有所差異）都是值得的

~~老家用弟弟電腦架站的研究也是同步進行中，目前弟弟想投資路由器， 電腦有人日常使用不適合當Server了~~但實在還是對網路上的各項免費方案很好奇...

雖然觀望了很久，但到目前為止都沒架成功一個穩定的後端服務在網際網路上=_=（目前只做到用Replit串Supabase開演示給他人看）

不過我深覺當個免費仔是件很困難的事情，故在這邊整理這份筆記...

***
## 前端類
- Netlify：以前拿來價過Hexo，有每個月部署限額次數，但老實說個人使用好像就蠻...堪用的...？（可能有些人網站做很大流量特別高啊><||）

***
## 資料庫&檔案儲存篇
### Supabase
DB：沒連接一週會睡著，要上後台叫醒，其他很讚了

![image](https://github.com/x200706/Free-to-play-Adventure/assets/99391710/94674fe6-9eae-4595-8a7d-6e9ab4289649)

還有個storage 似乎可以做為S3的替代品？！

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
## 全／後端類
### Laravel雲端PaSS以外的可能性？
20240427在Profreehost[折騰一番](https://x200706.bearblog.dev/composer-install/)後發現日後困難可能更多，實在不是一個很有效率的方式

去紅迪看看大家推薦近年來免費部署Laravel最佳方式，大概有這些服務（這些也可以部署Node.js甚至有的可以部署docker），其實都紅一陣子了~~
- [Render](https://render.com/)<-這個[部後端要錢？！](https://ithelp.ithome.com.tw/articles/10255630)
- [Vercel](https://vercel.com/)
  - [這文章適合"入門"](https://dev.to/kenean50/free-serverless-laravel-deployment-1e9n)
    - 但牽涉到描靜態資產就..
    - [影片版－用CLI](https://www.youtube.com/watch?v=dERa0R2zLqc&t=1s)
  - 遇到以下問題
    >php: error while loading shared libraries: libssl.so.10: cannot open shared object file: No such file or directory

    可參考[這篇](https://stackoverflow.com/questions/78242231/error-while-deploying-laravel-app-on-vercel-project)
    版本指定問題～
  - 靜態資產一直404可參考[這個庫](https://github.com/jamiedavenport/laravel-vercel-example/blob/main/vercel.json)描vercel.json，build換成你要描的路徑；另外可能要留意允許HTTPS的問題
    - 官方討論區那個最佳解我看著它描不出來..
    - 這幾個庫描法也可以參考 [1](https://github.com/treckstar/vercel-laravel-10-starter) [2](https://github.com/guoxiangke/laravel-vercel)<-有些其他方面的說明也不錯
    - 描太粗
      ```js
          "routes": [
        {
            "src": "/(.*)",
            "dest": "/public/$1"
        },
        {
            "src": "/(.*)",
            "dest": "/api/index.php"
        }
      ],
      ```
      打開網站會變成下載==...
  - [這個Repository](https://github.com/aungmyatmoethegreat/laravel-on-vercel) 沒描靜態資產，但如果有遇到API路徑問題，或許可以參考？
    - 我自己在`route/web`寫了一個`/hihi`的get router測試倒是不受影響，`route/api`就真的很尷尬-.-
## 剩餘的嘗試更新在blog[這篇](https://x200706.bearblog.dev/vercellaravel-admin/)

- 延伸閱讀：[紅迪上大家的投票（關於如何託管Laravel）](https://www.reddit.com/r/laravel/comments/xyphv9/how_do_you_host_laravel_app/)
  - 這篇有人AWS帳單好高rrr
  - 話說如果用GCP架設的話，防火牆規則之類可能要了解下（預設VM那邊只能開80跟443）......

***
## 網路組
### 免費域名
- <https://nic.eu.org/>

### 免費DNS託管
（待撰）

### 免費憑證
- Let's Encrypt+主機跑排程自動展延
- 上方服務商有的會自行提供
