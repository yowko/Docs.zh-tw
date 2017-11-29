---
title: 205 - OperationInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b0a96f1e3ba72a226d9b1a871382a27db61c57e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="205---operationinvoked"></a><span data-ttu-id="44151-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="44151-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="44151-103">屬性</span><span class="sxs-lookup"><span data-stu-id="44151-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44151-104">ID</span><span class="sxs-lookup"><span data-stu-id="44151-104">ID</span></span>|<span data-ttu-id="44151-105">205</span><span class="sxs-lookup"><span data-stu-id="44151-105">205</span></span>|  
|<span data-ttu-id="44151-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="44151-106">Keywords</span></span>|<span data-ttu-id="44151-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="44151-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="44151-108">層級</span><span class="sxs-lookup"><span data-stu-id="44151-108">Level</span></span>|<span data-ttu-id="44151-109">資訊</span><span class="sxs-lookup"><span data-stu-id="44151-109">Information</span></span>|  
|<span data-ttu-id="44151-110">通道</span><span class="sxs-lookup"><span data-stu-id="44151-110">Channel</span></span>|<span data-ttu-id="44151-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="44151-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="44151-112">描述</span><span class="sxs-lookup"><span data-stu-id="44151-112">Description</span></span>  
 <span data-ttu-id="44151-113">此事件會在服務模型的預設 `OperationInvoker` 開始呼叫方法之前發出。</span><span class="sxs-lookup"><span data-stu-id="44151-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="44151-114">訊息</span><span class="sxs-lookup"><span data-stu-id="44151-114">Message</span></span>  
 <span data-ttu-id="44151-115">OperationInvoker 已叫用 '%1' 方法。</span><span class="sxs-lookup"><span data-stu-id="44151-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="44151-116">呼叫端資訊: '%2'。</span><span class="sxs-lookup"><span data-stu-id="44151-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="44151-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="44151-117">Details</span></span>  
  
|<span data-ttu-id="44151-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="44151-118">Data Item Name</span></span>|<span data-ttu-id="44151-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="44151-119">Data Item Type</span></span>|<span data-ttu-id="44151-120">描述</span><span class="sxs-lookup"><span data-stu-id="44151-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="44151-121">方法名稱</span><span class="sxs-lookup"><span data-stu-id="44151-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="44151-122">`OperationInvoker` 叫用之方法的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="44151-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="44151-123">呼叫端資訊</span><span class="sxs-lookup"><span data-stu-id="44151-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="44151-124">用戶端的 IP 位址和連接埠號碼，格式為 'IPAddress:PortNumber'。</span><span class="sxs-lookup"><span data-stu-id="44151-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="44151-125">這兩個值都是從作業內容內的 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' 訊息屬性擷取。</span><span class="sxs-lookup"><span data-stu-id="44151-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="44151-126">請注意，針對非 TCP 繫結，此值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="44151-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="44151-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="44151-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="44151-128">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="44151-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="44151-129">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="44151-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="44151-130">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="44151-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="44151-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="44151-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="44151-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="44151-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
