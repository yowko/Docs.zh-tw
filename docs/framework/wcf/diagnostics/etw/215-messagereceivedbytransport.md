---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460899"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="29eb3-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="29eb3-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="29eb3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="29eb3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29eb3-104">ID</span><span class="sxs-lookup"><span data-stu-id="29eb3-104">ID</span></span>|<span data-ttu-id="29eb3-105">215</span><span class="sxs-lookup"><span data-stu-id="29eb3-105">215</span></span>|  
|<span data-ttu-id="29eb3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="29eb3-106">Keywords</span></span>|<span data-ttu-id="29eb3-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29eb3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="29eb3-108">層級</span><span class="sxs-lookup"><span data-stu-id="29eb3-108">Level</span></span>|<span data-ttu-id="29eb3-109">資訊</span><span class="sxs-lookup"><span data-stu-id="29eb3-109">Information</span></span>|  
|<span data-ttu-id="29eb3-110">通道</span><span class="sxs-lookup"><span data-stu-id="29eb3-110">Channel</span></span>|<span data-ttu-id="29eb3-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="29eb3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="29eb3-112">描述</span><span class="sxs-lookup"><span data-stu-id="29eb3-112">Description</span></span>  
 <span data-ttu-id="29eb3-113">此事件會在 TCP 傳輸接收訊息時發生。</span><span class="sxs-lookup"><span data-stu-id="29eb3-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="29eb3-114">請注意，在傳輸層級，用戶端與服務之間可以針對單一作業交換多個訊息。</span><span class="sxs-lookup"><span data-stu-id="29eb3-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="29eb3-115">這可能是由於基礎結構行為所致，安全性就是一個很好的例子。</span><span class="sxs-lookup"><span data-stu-id="29eb3-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="29eb3-116">因此，發出的 `MessageReceivedByTransport` 事件數目會根據服務的繫結及其組態而有所不同。</span><span class="sxs-lookup"><span data-stu-id="29eb3-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29eb3-117">單向傳輸不會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="29eb3-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="29eb3-118">訊息</span><span class="sxs-lookup"><span data-stu-id="29eb3-118">Message</span></span>  
 <span data-ttu-id="29eb3-119">傳輸收到來自 '%1' 的訊息。</span><span class="sxs-lookup"><span data-stu-id="29eb3-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="29eb3-120">詳細資料</span><span class="sxs-lookup"><span data-stu-id="29eb3-120">Details</span></span>  
  
|<span data-ttu-id="29eb3-121">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="29eb3-121">Data Item Name</span></span>|<span data-ttu-id="29eb3-122">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="29eb3-122">Data Item Type</span></span>|<span data-ttu-id="29eb3-123">描述</span><span class="sxs-lookup"><span data-stu-id="29eb3-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="29eb3-124">ListenAddress</span><span class="sxs-lookup"><span data-stu-id="29eb3-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="29eb3-125">收到訊息的位址。</span><span class="sxs-lookup"><span data-stu-id="29eb3-125">The address that received the message.</span></span>|  
|<span data-ttu-id="29eb3-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="29eb3-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="29eb3-127">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="29eb3-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="29eb3-128">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="29eb3-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="29eb3-129">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="29eb3-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="29eb3-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="29eb3-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="29eb3-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="29eb3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
