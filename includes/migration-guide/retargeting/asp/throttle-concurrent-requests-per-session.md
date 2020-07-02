---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614325"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="361b1-101">每一個工作階段的節流閥並行要求數目</span><span class="sxs-lookup"><span data-stu-id="361b1-101">Throttle concurrent requests per session</span></span>

#### <a name="details"></a><span data-ttu-id="361b1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="361b1-102">Details</span></span>

<span data-ttu-id="361b1-103">在 .NET Framework 4.6.2 和更早版本中，ASP.NET 會使用相同的 Sessionid 循序執行要求，且 ASP.NET 預設一律會透過 Cookie 發出 Sessionid。</span><span class="sxs-lookup"><span data-stu-id="361b1-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="361b1-104">如果頁面需要很長的時間來回應，則只要在瀏覽器上按<kbd>F5</kbd> ，就會大幅降低伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="361b1-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing <kbd>F5</kbd> on the browser.</span></span> <span data-ttu-id="361b1-105">在修正程式中，我們新增了一個計數器來追蹤佇列要求，並在超過指定限制時終止要求。</span><span class="sxs-lookup"><span data-stu-id="361b1-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="361b1-106">預設值是 50。</span><span class="sxs-lookup"><span data-stu-id="361b1-106">The default value is 50.</span></span> <span data-ttu-id="361b1-107">如果達到限制，會在事件記錄檔記錄警告並在 IIS 記錄檔中記錄 HTTP 500 回應。</span><span class="sxs-lookup"><span data-stu-id="361b1-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="361b1-108">建議</span><span class="sxs-lookup"><span data-stu-id="361b1-108">Suggestion</span></span>

<span data-ttu-id="361b1-109">若要還原舊行為，您可以將下列設定加入您的 web.config 檔案以選擇退出新行為。</span><span class="sxs-lookup"><span data-stu-id="361b1-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span>

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| <span data-ttu-id="361b1-110">名稱</span><span class="sxs-lookup"><span data-stu-id="361b1-110">Name</span></span>    | <span data-ttu-id="361b1-111">值</span><span class="sxs-lookup"><span data-stu-id="361b1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="361b1-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="361b1-112">Scope</span></span>   | <span data-ttu-id="361b1-113">Edge</span><span class="sxs-lookup"><span data-stu-id="361b1-113">Edge</span></span>        |
| <span data-ttu-id="361b1-114">版本</span><span class="sxs-lookup"><span data-stu-id="361b1-114">Version</span></span> | <span data-ttu-id="361b1-115">4.7</span><span class="sxs-lookup"><span data-stu-id="361b1-115">4.7</span></span>         |
| <span data-ttu-id="361b1-116">類型</span><span class="sxs-lookup"><span data-stu-id="361b1-116">Type</span></span>    | <span data-ttu-id="361b1-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="361b1-117">Retargeting</span></span> |
