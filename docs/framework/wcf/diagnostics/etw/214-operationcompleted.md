---
title: 214 - OperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6ef1eb398a0146e619cbcb85fe2761306aba4fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="92be3-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="92be3-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="92be3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="92be3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92be3-104">ID</span><span class="sxs-lookup"><span data-stu-id="92be3-104">ID</span></span>|<span data-ttu-id="92be3-105">214</span><span class="sxs-lookup"><span data-stu-id="92be3-105">214</span></span>|  
|<span data-ttu-id="92be3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="92be3-106">Keywords</span></span>|<span data-ttu-id="92be3-107">HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="92be3-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="92be3-108">層級</span><span class="sxs-lookup"><span data-stu-id="92be3-108">Level</span></span>|<span data-ttu-id="92be3-109">資訊</span><span class="sxs-lookup"><span data-stu-id="92be3-109">Information</span></span>|  
|<span data-ttu-id="92be3-110">通道</span><span class="sxs-lookup"><span data-stu-id="92be3-110">Channel</span></span>|<span data-ttu-id="92be3-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="92be3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="92be3-112">描述</span><span class="sxs-lookup"><span data-stu-id="92be3-112">Description</span></span>  
 <span data-ttu-id="92be3-113">此事件是在服務模型的預設 `OperationInvoker` 完成呼叫方法，且該方法未擲回例外狀況時發出。</span><span class="sxs-lookup"><span data-stu-id="92be3-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="92be3-114">訊息</span><span class="sxs-lookup"><span data-stu-id="92be3-114">Message</span></span>  
 <span data-ttu-id="92be3-115">OperationInvoker 完成了對 '%1' 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="92be3-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="92be3-116">此方法的呼叫持續時間為 '%2' 毫秒。</span><span class="sxs-lookup"><span data-stu-id="92be3-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="92be3-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="92be3-117">Details</span></span>  
  
|<span data-ttu-id="92be3-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="92be3-118">Data Item Name</span></span>|<span data-ttu-id="92be3-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="92be3-119">Data Item Type</span></span>|<span data-ttu-id="92be3-120">描述</span><span class="sxs-lookup"><span data-stu-id="92be3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="92be3-121">方法名稱</span><span class="sxs-lookup"><span data-stu-id="92be3-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="92be3-122">`OperationInvoker` 叫用之方法的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="92be3-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="92be3-123">持續期間</span><span class="sxs-lookup"><span data-stu-id="92be3-123">Duration</span></span>|`xs:long`|<span data-ttu-id="92be3-124">`OperationInvoker` 叫用方法所花費的時間，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="92be3-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="92be3-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="92be3-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="92be3-126">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="92be3-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="92be3-127">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="92be3-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="92be3-128">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="92be3-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="92be3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="92be3-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="92be3-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="92be3-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
