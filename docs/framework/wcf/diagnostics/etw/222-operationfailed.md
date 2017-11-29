---
title: 222 - OperationFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c76b502c9c1a767898b1e857c2e943c26fad5c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="222---operationfailed"></a><span data-ttu-id="3ec41-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="3ec41-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="3ec41-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3ec41-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ec41-104">ID</span><span class="sxs-lookup"><span data-stu-id="3ec41-104">ID</span></span>|<span data-ttu-id="3ec41-105">222</span><span class="sxs-lookup"><span data-stu-id="3ec41-105">222</span></span>|  
|<span data-ttu-id="3ec41-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3ec41-106">Keywords</span></span>|<span data-ttu-id="3ec41-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3ec41-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3ec41-108">層級</span><span class="sxs-lookup"><span data-stu-id="3ec41-108">Level</span></span>|<span data-ttu-id="3ec41-109">警告</span><span class="sxs-lookup"><span data-stu-id="3ec41-109">Warning</span></span>|  
|<span data-ttu-id="3ec41-110">通道</span><span class="sxs-lookup"><span data-stu-id="3ec41-110">Channel</span></span>|<span data-ttu-id="3ec41-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="3ec41-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3ec41-112">描述</span><span class="sxs-lookup"><span data-stu-id="3ec41-112">Description</span></span>  
 <span data-ttu-id="3ec41-113">當服務模型的預設 `OperationInvoker` 在呼叫其方法發生例外時，便會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="3ec41-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="3ec41-114">請注意，衍生自 `FaultException` 的例外會導致不發出此事件。</span><span class="sxs-lookup"><span data-stu-id="3ec41-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3ec41-115">訊息</span><span class="sxs-lookup"><span data-stu-id="3ec41-115">Message</span></span>  
 <span data-ttu-id="3ec41-116">由 OperationInvoker 叫用時，'%1' 方法擲回無法處理的例外。</span><span class="sxs-lookup"><span data-stu-id="3ec41-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="3ec41-117">此方法的呼叫持續時間為 '%2' 毫秒。</span><span class="sxs-lookup"><span data-stu-id="3ec41-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3ec41-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3ec41-118">Details</span></span>  
  
|<span data-ttu-id="3ec41-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3ec41-119">Data Item Name</span></span>|<span data-ttu-id="3ec41-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3ec41-120">Data Item Type</span></span>|<span data-ttu-id="3ec41-121">描述</span><span class="sxs-lookup"><span data-stu-id="3ec41-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3ec41-122">方法名稱</span><span class="sxs-lookup"><span data-stu-id="3ec41-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="3ec41-123">`OperationInvoker` 叫用之方法的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="3ec41-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="3ec41-124">持續期間</span><span class="sxs-lookup"><span data-stu-id="3ec41-124">Duration</span></span>|`xs:long`|<span data-ttu-id="3ec41-125">`OperationInvoker` 叫用方法所花費的時間，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="3ec41-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="3ec41-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="3ec41-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="3ec41-127">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="3ec41-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3ec41-128">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="3ec41-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3ec41-129">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="3ec41-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3ec41-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3ec41-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3ec41-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3ec41-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
