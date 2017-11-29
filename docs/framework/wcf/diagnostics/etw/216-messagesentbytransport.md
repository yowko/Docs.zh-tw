---
title: 216 - MessageSentByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b35f46ae7a214ab45e4062928de82c4da6541a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="5cbd6-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="5cbd6-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="5cbd6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5cbd6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cbd6-104">ID</span><span class="sxs-lookup"><span data-stu-id="5cbd6-104">ID</span></span>|<span data-ttu-id="5cbd6-105">216</span><span class="sxs-lookup"><span data-stu-id="5cbd6-105">216</span></span>|  
|<span data-ttu-id="5cbd6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5cbd6-106">Keywords</span></span>|<span data-ttu-id="5cbd6-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5cbd6-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5cbd6-108">層級</span><span class="sxs-lookup"><span data-stu-id="5cbd6-108">Level</span></span>|<span data-ttu-id="5cbd6-109">資訊</span><span class="sxs-lookup"><span data-stu-id="5cbd6-109">Information</span></span>|  
|<span data-ttu-id="5cbd6-110">通道</span><span class="sxs-lookup"><span data-stu-id="5cbd6-110">Channel</span></span>|<span data-ttu-id="5cbd6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5cbd6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5cbd6-112">描述</span><span class="sxs-lookup"><span data-stu-id="5cbd6-112">Description</span></span>  
 <span data-ttu-id="5cbd6-113">這個事件會發生在 TCP 傳輸傳送訊息時。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="5cbd6-114">請注意，在傳輸層級，用戶端與服務之間可以針對單一作業交換多個訊息。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="5cbd6-115">這可能是由於基礎結構行為所致，安全性就是一個很好的例子。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="5cbd6-116">因此，數目**MessageSentByTransport**發出的事件根據服務的繫結和其組態而有所不同。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5cbd6-117">訊息</span><span class="sxs-lookup"><span data-stu-id="5cbd6-117">Message</span></span>  
 <span data-ttu-id="5cbd6-118">傳輸傳送了訊息至 '%1'。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5cbd6-119">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5cbd6-119">Details</span></span>  
  
|<span data-ttu-id="5cbd6-120">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5cbd6-120">Data Item Name</span></span>|<span data-ttu-id="5cbd6-121">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5cbd6-121">Data Item Type</span></span>|<span data-ttu-id="5cbd6-122">描述</span><span class="sxs-lookup"><span data-stu-id="5cbd6-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5cbd6-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="5cbd6-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="5cbd6-124">要求訊息傳送至的位址。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="5cbd6-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="5cbd6-125">HostReference</span></span>|<span data-ttu-id="5cbd6-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="5cbd6-126">xs:string</span></span>|<span data-ttu-id="5cbd6-127">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5cbd6-128">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5cbd6-129">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5cbd6-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5cbd6-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5cbd6-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5cbd6-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
