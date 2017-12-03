---
title: 211 - ParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78424b8057518f5d9f201ead33b2784ffeeb7e58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="339bf-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="339bf-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="339bf-103">屬性</span><span class="sxs-lookup"><span data-stu-id="339bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="339bf-104">ID</span><span class="sxs-lookup"><span data-stu-id="339bf-104">ID</span></span>|<span data-ttu-id="339bf-105">211</span><span class="sxs-lookup"><span data-stu-id="339bf-105">211</span></span>|  
|<span data-ttu-id="339bf-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="339bf-106">Keywords</span></span>|<span data-ttu-id="339bf-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="339bf-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="339bf-108">層級</span><span class="sxs-lookup"><span data-stu-id="339bf-108">Level</span></span>|<span data-ttu-id="339bf-109">資訊</span><span class="sxs-lookup"><span data-stu-id="339bf-109">Information</span></span>|  
|<span data-ttu-id="339bf-110">通道</span><span class="sxs-lookup"><span data-stu-id="339bf-110">Channel</span></span>|<span data-ttu-id="339bf-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="339bf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="339bf-112">描述</span><span class="sxs-lookup"><span data-stu-id="339bf-112">Description</span></span>  
 <span data-ttu-id="339bf-113">服務模型已在 `AfterCall` 上叫用 `ParameterInspector` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="339bf-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="339bf-114">訊息</span><span class="sxs-lookup"><span data-stu-id="339bf-114">Message</span></span>  
 <span data-ttu-id="339bf-115">發送器在型別 '%1' 的 ParameterInspector 上叫用 'AfterCall'。</span><span class="sxs-lookup"><span data-stu-id="339bf-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="339bf-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="339bf-116">Details</span></span>  
  
|<span data-ttu-id="339bf-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="339bf-117">Data Item Name</span></span>|<span data-ttu-id="339bf-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="339bf-118">Data Item Type</span></span>|<span data-ttu-id="339bf-119">描述</span><span class="sxs-lookup"><span data-stu-id="339bf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="339bf-120">類型名稱</span><span class="sxs-lookup"><span data-stu-id="339bf-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="339bf-121">已叫用 `ParameterInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="339bf-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="339bf-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="339bf-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="339bf-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="339bf-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="339bf-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="339bf-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="339bf-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="339bf-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="339bf-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="339bf-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="339bf-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="339bf-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
