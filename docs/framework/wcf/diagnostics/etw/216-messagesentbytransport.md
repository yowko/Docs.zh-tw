---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: b3e9e1a48951ad5a2e5e7820dc1828c20e310635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278904"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="255f0-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="255f0-102">216 - MessageSentByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="255f0-103">屬性</span><span class="sxs-lookup"><span data-stu-id="255f0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="255f0-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="255f0-104">ID</span></span>|<span data-ttu-id="255f0-105">216</span><span class="sxs-lookup"><span data-stu-id="255f0-105">216</span></span>|  
|<span data-ttu-id="255f0-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="255f0-106">Keywords</span></span>|<span data-ttu-id="255f0-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="255f0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="255f0-108">層級</span><span class="sxs-lookup"><span data-stu-id="255f0-108">Level</span></span>|<span data-ttu-id="255f0-109">資訊</span><span class="sxs-lookup"><span data-stu-id="255f0-109">Information</span></span>|  
|<span data-ttu-id="255f0-110">通路</span><span class="sxs-lookup"><span data-stu-id="255f0-110">Channel</span></span>|<span data-ttu-id="255f0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="255f0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="255f0-112">描述</span><span class="sxs-lookup"><span data-stu-id="255f0-112">Description</span></span>  

 <span data-ttu-id="255f0-113">這個事件會發生在 TCP 傳輸傳送訊息時。</span><span class="sxs-lookup"><span data-stu-id="255f0-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="255f0-114">請注意，在傳輸層級，用戶端與服務之間可以針對單一作業交換多個訊息。</span><span class="sxs-lookup"><span data-stu-id="255f0-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="255f0-115">這可能是由於基礎結構行為所致，安全性就是一個很好的例子。</span><span class="sxs-lookup"><span data-stu-id="255f0-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="255f0-116">因此，發出的 **MessageSentByTransport** 事件數目會根據您服務的系結及其設定而有所不同。</span><span class="sxs-lookup"><span data-stu-id="255f0-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="255f0-117">訊息</span><span class="sxs-lookup"><span data-stu-id="255f0-117">Message</span></span>  

 <span data-ttu-id="255f0-118">傳輸傳送了訊息至 '%1'。</span><span class="sxs-lookup"><span data-stu-id="255f0-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="255f0-119">詳細資料</span><span class="sxs-lookup"><span data-stu-id="255f0-119">Details</span></span>  
  
|<span data-ttu-id="255f0-120">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="255f0-120">Data Item Name</span></span>|<span data-ttu-id="255f0-121">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="255f0-121">Data Item Type</span></span>|<span data-ttu-id="255f0-122">描述</span><span class="sxs-lookup"><span data-stu-id="255f0-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="255f0-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="255f0-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="255f0-124">要求訊息傳送至的位址。</span><span class="sxs-lookup"><span data-stu-id="255f0-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="255f0-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="255f0-125">HostReference</span></span>|<span data-ttu-id="255f0-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="255f0-126">xs:string</span></span>|<span data-ttu-id="255f0-127">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="255f0-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="255f0-128">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="255f0-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="255f0-129">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="255f0-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="255f0-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="255f0-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="255f0-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="255f0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
