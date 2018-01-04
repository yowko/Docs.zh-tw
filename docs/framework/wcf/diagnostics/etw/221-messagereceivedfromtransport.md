---
title: 221 - MessageReceivedFromTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 139ca9e0fbe4d3f59d3d593f7785d5fb65e64702
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="b3158-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="b3158-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="b3158-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b3158-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b3158-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="b3158-104">ID</span></span>|<span data-ttu-id="b3158-105">221</span><span class="sxs-lookup"><span data-stu-id="b3158-105">221</span></span>|  
|<span data-ttu-id="b3158-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b3158-106">Keywords</span></span>|<span data-ttu-id="b3158-107">EndToEndMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b3158-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b3158-108">層級</span><span class="sxs-lookup"><span data-stu-id="b3158-108">Level</span></span>|<span data-ttu-id="b3158-109">資訊</span><span class="sxs-lookup"><span data-stu-id="b3158-109">Information</span></span>|  
|<span data-ttu-id="b3158-110">通道</span><span class="sxs-lookup"><span data-stu-id="b3158-110">Channel</span></span>|<span data-ttu-id="b3158-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b3158-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b3158-112">描述</span><span class="sxs-lookup"><span data-stu-id="b3158-112">Description</span></span>  
 <span data-ttu-id="b3158-113">當服務模型收到來自傳輸的訊息時，便會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="b3158-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b3158-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b3158-114">Message</span></span>  
 <span data-ttu-id="b3158-115">發送器收到來自傳輸的訊息。</span><span class="sxs-lookup"><span data-stu-id="b3158-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="b3158-116">相互關聯 ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="b3158-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b3158-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b3158-117">Details</span></span>  
  
|<span data-ttu-id="b3158-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b3158-118">Data Item Name</span></span>|<span data-ttu-id="b3158-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b3158-119">Data Item Type</span></span>|<span data-ttu-id="b3158-120">描述</span><span class="sxs-lookup"><span data-stu-id="b3158-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b3158-121">相互關聯 ID</span><span class="sxs-lookup"><span data-stu-id="b3158-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="b3158-122">活動識別碼，會將來自服務或用戶端的 `MessageSentToTransport` 事件，與另一端對應的 `MessageReceivedFromTransport` 相互關聯。</span><span class="sxs-lookup"><span data-stu-id="b3158-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="b3158-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="b3158-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="b3158-124">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="b3158-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b3158-125">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="b3158-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b3158-126">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="b3158-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b3158-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b3158-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b3158-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b3158-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
