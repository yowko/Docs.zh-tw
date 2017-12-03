---
title: 210 - MessageThrottleExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c39c454e3a9bb70840b47271432d555d24fb167a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="210---messagethrottleexceeded"></a><span data-ttu-id="dcb14-102">210 - MessageThrottleExceeded</span><span class="sxs-lookup"><span data-stu-id="dcb14-102">210 - MessageThrottleExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="dcb14-103">屬性</span><span class="sxs-lookup"><span data-stu-id="dcb14-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcb14-104">ID</span><span class="sxs-lookup"><span data-stu-id="dcb14-104">ID</span></span>|<span data-ttu-id="dcb14-105">210</span><span class="sxs-lookup"><span data-stu-id="dcb14-105">210</span></span>|  
|<span data-ttu-id="dcb14-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="dcb14-106">Keywords</span></span>|<span data-ttu-id="dcb14-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dcb14-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="dcb14-108">層級</span><span class="sxs-lookup"><span data-stu-id="dcb14-108">Level</span></span>|<span data-ttu-id="dcb14-109">警告</span><span class="sxs-lookup"><span data-stu-id="dcb14-109">Warning</span></span>|  
|<span data-ttu-id="dcb14-110">通道</span><span class="sxs-lookup"><span data-stu-id="dcb14-110">Channel</span></span>|<span data-ttu-id="dcb14-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="dcb14-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dcb14-112">描述</span><span class="sxs-lookup"><span data-stu-id="dcb14-112">Description</span></span>  
 <span data-ttu-id="dcb14-113">有三個主要的服務節流閥，只要其中一個超出，則會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="dcb14-113">This event is emitted when one of the three main service throttles have been exceeded.</span></span> <span data-ttu-id="dcb14-114">請注意，此事件只有在節流閥限制初次超過時才會發出。</span><span class="sxs-lookup"><span data-stu-id="dcb14-114">Note that this event is only emitted when the throttle limit is initially exceeded.</span></span> <span data-ttu-id="dcb14-115">例如，假設同時呼叫的節流閥限制是 10，則第 11 個同時呼叫會引起 `MessageThrottleExceeded` 事件。</span><span class="sxs-lookup"><span data-stu-id="dcb14-115">For example, if the throttle limit for concurrent calls is 10, the 11th concurrent call results in a `MessageThrottleExceeded` event.</span></span> <span data-ttu-id="dcb14-116">第 12 個呼叫不會引起另一個事件。</span><span class="sxs-lookup"><span data-stu-id="dcb14-116">The 12th call does not result in another event.</span></span> <span data-ttu-id="dcb14-117">此外，為了避免太多事件資料流，在限制範圍附近的活動並不會造成另一個事件。</span><span class="sxs-lookup"><span data-stu-id="dcb14-117">Additionally, to avoid a noisy event stream, activity that hovers around the limit does not result in another event.</span></span> <span data-ttu-id="dcb14-118">在此範例中，如果有數個呼叫完成，就會有 9 個同時呼叫。</span><span class="sxs-lookup"><span data-stu-id="dcb14-118">In this example, if a couple of calls complete then there are 9 concurrent calls.</span></span> <span data-ttu-id="dcb14-119">如果後續又有兩個呼叫，目前的值會再變成 11。</span><span class="sxs-lookup"><span data-stu-id="dcb14-119">If subsequently two more calls come in, the current value is again 11.</span></span> <span data-ttu-id="dcb14-120">這並不會引起另一個事件。</span><span class="sxs-lookup"><span data-stu-id="dcb14-120">This does not result in another event.</span></span> <span data-ttu-id="dcb14-121">當目前的值降至節流閥限制的 70%，就會發出不同的事件，指出活動已經減慢。</span><span class="sxs-lookup"><span data-stu-id="dcb14-121">When the current value falls to 70 percent of the throttle limit a different event is emitted that indicates that the activity has slowed.</span></span> <span data-ttu-id="dcb14-122">未來超出限制的活動，將會引起另一個 `MessageThrottleExceeded` 事件發出。</span><span class="sxs-lookup"><span data-stu-id="dcb14-122">Future activity that exceeds the limit results in another `MessageThrottleExceeded` event being emitted.</span></span> <span data-ttu-id="dcb14-123">在此範例中，如果同時呼叫的數量降到 7 個，然後再次達到 11 個，就會發出另一個 `MessageThrottleExceeded` 事件。</span><span class="sxs-lookup"><span data-stu-id="dcb14-123">In this example, if the amount of concurrent calls falls to 7 and then again reaches 11 and another `MessageThrottleExceeded` event is emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dcb14-124">訊息</span><span class="sxs-lookup"><span data-stu-id="dcb14-124">Message</span></span>  
 <span data-ttu-id="dcb14-125">已達到 '%1' 的節流閥限制 '%2'。</span><span class="sxs-lookup"><span data-stu-id="dcb14-125">The '%1' throttle limit of '%2' was hit.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dcb14-126">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dcb14-126">Details</span></span>  
  
|<span data-ttu-id="dcb14-127">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="dcb14-127">Data Item Name</span></span>|<span data-ttu-id="dcb14-128">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="dcb14-128">Data Item Type</span></span>|<span data-ttu-id="dcb14-129">描述</span><span class="sxs-lookup"><span data-stu-id="dcb14-129">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dcb14-130">節流閥名稱</span><span class="sxs-lookup"><span data-stu-id="dcb14-130">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="dcb14-131">已超出的節流閥名稱。</span><span class="sxs-lookup"><span data-stu-id="dcb14-131">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="dcb14-132">`MaxConcurrentCalls`、`MaxConcurrentInstances` 或 `MaxConcurrentSessions`。</span><span class="sxs-lookup"><span data-stu-id="dcb14-132">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="dcb14-133">限制</span><span class="sxs-lookup"><span data-stu-id="dcb14-133">Limit</span></span>|`xs:long`|<span data-ttu-id="dcb14-134">目前設定的節流閥限制。</span><span class="sxs-lookup"><span data-stu-id="dcb14-134">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="dcb14-135">HostReference</span><span class="sxs-lookup"><span data-stu-id="dcb14-135">HostReference</span></span>|`xs:string`|<span data-ttu-id="dcb14-136">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="dcb14-136">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="dcb14-137">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="dcb14-137">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="dcb14-138">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="dcb14-138">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="dcb14-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dcb14-139">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dcb14-140">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="dcb14-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
