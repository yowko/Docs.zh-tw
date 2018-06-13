---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460391"
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="19274-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="19274-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="19274-103">屬性</span><span class="sxs-lookup"><span data-stu-id="19274-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19274-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="19274-104">ID</span></span>|<span data-ttu-id="19274-105">224</span><span class="sxs-lookup"><span data-stu-id="19274-105">224</span></span>|  
|<span data-ttu-id="19274-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="19274-106">Keywords</span></span>|<span data-ttu-id="19274-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="19274-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="19274-108">層級</span><span class="sxs-lookup"><span data-stu-id="19274-108">Level</span></span>|<span data-ttu-id="19274-109">警告</span><span class="sxs-lookup"><span data-stu-id="19274-109">Warning</span></span>|  
|<span data-ttu-id="19274-110">通道</span><span class="sxs-lookup"><span data-stu-id="19274-110">Channel</span></span>|<span data-ttu-id="19274-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="19274-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="19274-112">描述</span><span class="sxs-lookup"><span data-stu-id="19274-112">Description</span></span>  
 <span data-ttu-id="19274-113">當超出其中一個主要服務節流閥時，便會發出 `MessageThrottleExceeded` 事件。</span><span class="sxs-lookup"><span data-stu-id="19274-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="19274-114">當活動增量速度變慢且節流閥的目前值為目前限制的 70% 時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="19274-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="19274-115">請注意，此事件只會在活動速度變慢時發出一次。</span><span class="sxs-lookup"><span data-stu-id="19274-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="19274-116">如果目前值停在 70% 標記處 (例如 70,69,70,71,70,69)，則只會在出現第一個 70% 時發出此事件。</span><span class="sxs-lookup"><span data-stu-id="19274-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="19274-117">此事件發出之後，後續出現超出節流閥限制的情況都會造成 `MessageThrottleExceeded` 事件。</span><span class="sxs-lookup"><span data-stu-id="19274-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="19274-118">訊息</span><span class="sxs-lookup"><span data-stu-id="19274-118">Message</span></span>  
 <span data-ttu-id="19274-119">'%2' 的 '%1' 節流閥限制為 70%%。</span><span class="sxs-lookup"><span data-stu-id="19274-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="19274-120">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19274-120">Details</span></span>  
  
|<span data-ttu-id="19274-121">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="19274-121">Data Item Name</span></span>|<span data-ttu-id="19274-122">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="19274-122">Data Item Type</span></span>|<span data-ttu-id="19274-123">描述</span><span class="sxs-lookup"><span data-stu-id="19274-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="19274-124">節流閥名稱</span><span class="sxs-lookup"><span data-stu-id="19274-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="19274-125">已超出的節流閥名稱。</span><span class="sxs-lookup"><span data-stu-id="19274-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="19274-126">`MaxConcurrentCalls`、`MaxConcurrentInstances` 或 `MaxConcurrentSessions`。</span><span class="sxs-lookup"><span data-stu-id="19274-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="19274-127">限制</span><span class="sxs-lookup"><span data-stu-id="19274-127">Limit</span></span>|`xs:long`|<span data-ttu-id="19274-128">目前設定的節流閥限制。</span><span class="sxs-lookup"><span data-stu-id="19274-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="19274-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="19274-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="19274-130">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="19274-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="19274-131">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="19274-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="19274-132">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="19274-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="19274-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="19274-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="19274-134">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="19274-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
