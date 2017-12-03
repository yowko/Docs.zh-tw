---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0428d90135823761e7b8a12f560786e34e12734
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="d64a0-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="d64a0-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="d64a0-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d64a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d64a0-104">ID</span><span class="sxs-lookup"><span data-stu-id="d64a0-104">ID</span></span>|<span data-ttu-id="d64a0-105">223</span><span class="sxs-lookup"><span data-stu-id="d64a0-105">223</span></span>|  
|<span data-ttu-id="d64a0-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d64a0-106">Keywords</span></span>|<span data-ttu-id="d64a0-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d64a0-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d64a0-108">層級</span><span class="sxs-lookup"><span data-stu-id="d64a0-108">Level</span></span>|<span data-ttu-id="d64a0-109">警告</span><span class="sxs-lookup"><span data-stu-id="d64a0-109">Warning</span></span>|  
|<span data-ttu-id="d64a0-110">通道</span><span class="sxs-lookup"><span data-stu-id="d64a0-110">Channel</span></span>|<span data-ttu-id="d64a0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d64a0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d64a0-112">描述</span><span class="sxs-lookup"><span data-stu-id="d64a0-112">Description</span></span>  
 <span data-ttu-id="d64a0-113">當服務模型的預設 `OperationInvoker` 在叫用其方法而遭遇衍生自 `FaultException` 的例外狀況時，便會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="d64a0-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d64a0-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d64a0-114">Message</span></span>  
 <span data-ttu-id="d64a0-115">由 OperationInvoker 叫用時，'%1' 方法擲回 FaultException。</span><span class="sxs-lookup"><span data-stu-id="d64a0-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="d64a0-116">此方法的呼叫持續時間為 '%2' 毫秒。</span><span class="sxs-lookup"><span data-stu-id="d64a0-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d64a0-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d64a0-117">Details</span></span>  
  
|<span data-ttu-id="d64a0-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d64a0-118">Data Item Name</span></span>|<span data-ttu-id="d64a0-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d64a0-119">Data Item Type</span></span>|<span data-ttu-id="d64a0-120">描述</span><span class="sxs-lookup"><span data-stu-id="d64a0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d64a0-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="d64a0-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="d64a0-122">`OperationInvoker` 叫用之方法的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="d64a0-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="d64a0-123">持續期間</span><span class="sxs-lookup"><span data-stu-id="d64a0-123">Duration</span></span>|`xs:long`|<span data-ttu-id="d64a0-124">`OperationInvoker` 叫用方法所花費的時間，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="d64a0-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="d64a0-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="d64a0-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="d64a0-126">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="d64a0-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d64a0-127">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="d64a0-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d64a0-128">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="d64a0-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d64a0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d64a0-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d64a0-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d64a0-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
