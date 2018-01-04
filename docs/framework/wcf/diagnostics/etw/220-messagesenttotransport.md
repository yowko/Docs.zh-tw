---
title: 220 - MessageSentToTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d391d7bb8276f4b20d831acd59aa8a78db38995c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="85e01-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="85e01-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="85e01-103">屬性</span><span class="sxs-lookup"><span data-stu-id="85e01-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85e01-104">ID</span><span class="sxs-lookup"><span data-stu-id="85e01-104">Id</span></span>|<span data-ttu-id="85e01-105">220</span><span class="sxs-lookup"><span data-stu-id="85e01-105">220</span></span>|  
|<span data-ttu-id="85e01-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="85e01-106">Keywords</span></span>|<span data-ttu-id="85e01-107">EndToEndMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="85e01-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="85e01-108">層級</span><span class="sxs-lookup"><span data-stu-id="85e01-108">Level</span></span>|<span data-ttu-id="85e01-109">資訊</span><span class="sxs-lookup"><span data-stu-id="85e01-109">Information</span></span>|  
|<span data-ttu-id="85e01-110">通道</span><span class="sxs-lookup"><span data-stu-id="85e01-110">Channel</span></span>|<span data-ttu-id="85e01-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="85e01-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="85e01-112">描述</span><span class="sxs-lookup"><span data-stu-id="85e01-112">Description</span></span>  
 <span data-ttu-id="85e01-113">服務模型將訊息傳送至傳輸時，便會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="85e01-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85e01-114">單向傳輸將不會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="85e01-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="85e01-115">訊息</span><span class="sxs-lookup"><span data-stu-id="85e01-115">Message</span></span>  
 <span data-ttu-id="85e01-116">發送器已傳送訊息到傳輸。</span><span class="sxs-lookup"><span data-stu-id="85e01-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="85e01-117">相互關聯 ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="85e01-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="85e01-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="85e01-118">Details</span></span>  
  
|<span data-ttu-id="85e01-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="85e01-119">Data Item Name</span></span>|<span data-ttu-id="85e01-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="85e01-120">Data Item Type</span></span>|<span data-ttu-id="85e01-121">描述</span><span class="sxs-lookup"><span data-stu-id="85e01-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="85e01-122">相互關聯 ID</span><span class="sxs-lookup"><span data-stu-id="85e01-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="85e01-123">活動識別碼，會將來自服務或用戶端的 `MessageSentToTransport` 事件，與另一端對應的 `MessageReceivedFromTransport` 相互關聯。</span><span class="sxs-lookup"><span data-stu-id="85e01-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="85e01-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="85e01-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="85e01-125">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="85e01-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="85e01-126">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="85e01-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="85e01-127">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="85e01-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="85e01-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="85e01-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="85e01-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="85e01-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
