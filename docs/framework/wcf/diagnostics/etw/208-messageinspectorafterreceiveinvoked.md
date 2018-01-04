---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 253daea49ed36e27a23c55f3baf252344c0a34f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="51ee8-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="51ee8-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="51ee8-103">屬性</span><span class="sxs-lookup"><span data-stu-id="51ee8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51ee8-104">ID</span><span class="sxs-lookup"><span data-stu-id="51ee8-104">ID</span></span>|<span data-ttu-id="51ee8-105">208</span><span class="sxs-lookup"><span data-stu-id="51ee8-105">208</span></span>|  
|<span data-ttu-id="51ee8-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="51ee8-106">Keywords</span></span>|<span data-ttu-id="51ee8-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="51ee8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="51ee8-108">層級</span><span class="sxs-lookup"><span data-stu-id="51ee8-108">Level</span></span>|<span data-ttu-id="51ee8-109">資訊</span><span class="sxs-lookup"><span data-stu-id="51ee8-109">Information</span></span>|  
|<span data-ttu-id="51ee8-110">通道</span><span class="sxs-lookup"><span data-stu-id="51ee8-110">Channel</span></span>|<span data-ttu-id="51ee8-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="51ee8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="51ee8-112">描述</span><span class="sxs-lookup"><span data-stu-id="51ee8-112">Description</span></span>  
 <span data-ttu-id="51ee8-113">服務模型在訊息偵測器上叫用 `AfterReceive` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="51ee8-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="51ee8-114">訊息</span><span class="sxs-lookup"><span data-stu-id="51ee8-114">Message</span></span>  
 <span data-ttu-id="51ee8-115">發送器在型別 '%1' 的 MessageInspector 上叫用了 'AfterReceiveReply'。</span><span class="sxs-lookup"><span data-stu-id="51ee8-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="51ee8-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="51ee8-116">Details</span></span>  
  
|<span data-ttu-id="51ee8-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="51ee8-117">Data Item Name</span></span>|<span data-ttu-id="51ee8-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="51ee8-118">Data Item Type</span></span>|<span data-ttu-id="51ee8-119">描述</span><span class="sxs-lookup"><span data-stu-id="51ee8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="51ee8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="51ee8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="51ee8-121">已叫用 `MessageInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="51ee8-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="51ee8-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="51ee8-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="51ee8-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="51ee8-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="51ee8-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="51ee8-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="51ee8-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="51ee8-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="51ee8-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="51ee8-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="51ee8-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="51ee8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
