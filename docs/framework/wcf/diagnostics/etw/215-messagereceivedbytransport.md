---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781832"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="e4bea-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="e4bea-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="e4bea-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e4bea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4bea-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="e4bea-104">ID</span></span>|<span data-ttu-id="e4bea-105">215</span><span class="sxs-lookup"><span data-stu-id="e4bea-105">215</span></span>|  
|<span data-ttu-id="e4bea-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e4bea-106">Keywords</span></span>|<span data-ttu-id="e4bea-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e4bea-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e4bea-108">層級</span><span class="sxs-lookup"><span data-stu-id="e4bea-108">Level</span></span>|<span data-ttu-id="e4bea-109">資訊</span><span class="sxs-lookup"><span data-stu-id="e4bea-109">Information</span></span>|  
|<span data-ttu-id="e4bea-110">通道</span><span class="sxs-lookup"><span data-stu-id="e4bea-110">Channel</span></span>|<span data-ttu-id="e4bea-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e4bea-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e4bea-112">描述</span><span class="sxs-lookup"><span data-stu-id="e4bea-112">Description</span></span>  
 <span data-ttu-id="e4bea-113">此事件會在 TCP 傳輸接收訊息時發生。</span><span class="sxs-lookup"><span data-stu-id="e4bea-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="e4bea-114">請注意，在傳輸層級，用戶端與服務之間可以針對單一作業交換多個訊息。</span><span class="sxs-lookup"><span data-stu-id="e4bea-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="e4bea-115">這可能是由於基礎結構行為所致，安全性就是一個很好的例子。</span><span class="sxs-lookup"><span data-stu-id="e4bea-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="e4bea-116">因此，發出的 `MessageReceivedByTransport` 事件數目會根據服務的繫結及其組態而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e4bea-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4bea-117">單向傳輸不會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="e4bea-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e4bea-118">訊息</span><span class="sxs-lookup"><span data-stu-id="e4bea-118">Message</span></span>  
 <span data-ttu-id="e4bea-119">傳輸收到來自 '%1' 的訊息。</span><span class="sxs-lookup"><span data-stu-id="e4bea-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e4bea-120">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e4bea-120">Details</span></span>  
  
|<span data-ttu-id="e4bea-121">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e4bea-121">Data Item Name</span></span>|<span data-ttu-id="e4bea-122">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e4bea-122">Data Item Type</span></span>|<span data-ttu-id="e4bea-123">描述</span><span class="sxs-lookup"><span data-stu-id="e4bea-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e4bea-124">ListenAddress</span><span class="sxs-lookup"><span data-stu-id="e4bea-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="e4bea-125">收到訊息的位址。</span><span class="sxs-lookup"><span data-stu-id="e4bea-125">The address that received the message.</span></span>|  
|<span data-ttu-id="e4bea-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="e4bea-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="e4bea-127">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="e4bea-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e4bea-128">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="e4bea-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e4bea-129">範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="e4bea-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e4bea-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e4bea-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e4bea-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e4bea-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
