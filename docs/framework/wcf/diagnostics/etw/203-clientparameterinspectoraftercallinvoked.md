---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1173aaa4bf01b324c8cd6088cd5646bc67f08c72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="f1457-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="f1457-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="f1457-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f1457-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1457-104">ID</span><span class="sxs-lookup"><span data-stu-id="f1457-104">ID</span></span>|<span data-ttu-id="f1457-105">203</span><span class="sxs-lookup"><span data-stu-id="f1457-105">203</span></span>|  
|<span data-ttu-id="f1457-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f1457-106">Keywords</span></span>|<span data-ttu-id="f1457-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f1457-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f1457-108">層級</span><span class="sxs-lookup"><span data-stu-id="f1457-108">Level</span></span>|<span data-ttu-id="f1457-109">資訊</span><span class="sxs-lookup"><span data-stu-id="f1457-109">Information</span></span>|  
|<span data-ttu-id="f1457-110">通道</span><span class="sxs-lookup"><span data-stu-id="f1457-110">Channel</span></span>|<span data-ttu-id="f1457-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f1457-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f1457-112">描述</span><span class="sxs-lookup"><span data-stu-id="f1457-112">Description</span></span>  
 <span data-ttu-id="f1457-113">此事件是在服務模型已在用戶端參數偵測器上叫用 `AfterCall` 方法之後發出。</span><span class="sxs-lookup"><span data-stu-id="f1457-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f1457-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f1457-114">Message</span></span>  
 <span data-ttu-id="f1457-115">發送器已在型別為 '%1' 的 ClientParameterInspector 上叫用 'AfterCall'。</span><span class="sxs-lookup"><span data-stu-id="f1457-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f1457-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f1457-116">Details</span></span>  
  
|<span data-ttu-id="f1457-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f1457-117">Data Item Name</span></span>|<span data-ttu-id="f1457-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f1457-118">Data Item Type</span></span>|<span data-ttu-id="f1457-119">描述</span><span class="sxs-lookup"><span data-stu-id="f1457-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f1457-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="f1457-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="f1457-121">叫用之偵測器型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="f1457-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="f1457-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f1457-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f1457-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="f1457-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f1457-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="f1457-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f1457-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="f1457-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f1457-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f1457-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f1457-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f1457-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
