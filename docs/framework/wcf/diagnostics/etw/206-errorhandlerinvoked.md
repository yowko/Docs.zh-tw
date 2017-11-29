---
title: 206 - ErrorHandlerInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84470cbaf7ba7951ef59b130c696462079216cde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="f371d-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="f371d-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="f371d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f371d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f371d-104">ID</span><span class="sxs-lookup"><span data-stu-id="f371d-104">ID</span></span>|<span data-ttu-id="f371d-105">206</span><span class="sxs-lookup"><span data-stu-id="f371d-105">206</span></span>|  
|<span data-ttu-id="f371d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f371d-106">Keywords</span></span>|<span data-ttu-id="f371d-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f371d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f371d-108">層級</span><span class="sxs-lookup"><span data-stu-id="f371d-108">Level</span></span>|<span data-ttu-id="f371d-109">資訊</span><span class="sxs-lookup"><span data-stu-id="f371d-109">Information</span></span>|  
|<span data-ttu-id="f371d-110">通道</span><span class="sxs-lookup"><span data-stu-id="f371d-110">Channel</span></span>|<span data-ttu-id="f371d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f371d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f371d-112">描述</span><span class="sxs-lookup"><span data-stu-id="f371d-112">Description</span></span>  
 <span data-ttu-id="f371d-113">這個事件是在 `ErrorHandler` 有機會處理服務作業中發生的例外狀況之後發出。</span><span class="sxs-lookup"><span data-stu-id="f371d-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f371d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f371d-114">Message</span></span>  
 <span data-ttu-id="f371d-115">發送器叫用類型 '%1' 的 ErrorHandler 與類型 '%3' 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f371d-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="f371d-116">ErrorHandled == '%2'。</span><span class="sxs-lookup"><span data-stu-id="f371d-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f371d-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f371d-117">Details</span></span>  
  
|<span data-ttu-id="f371d-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f371d-118">Data Item Name</span></span>|<span data-ttu-id="f371d-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f371d-119">Data Item Type</span></span>|<span data-ttu-id="f371d-120">描述</span><span class="sxs-lookup"><span data-stu-id="f371d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f371d-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="f371d-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="f371d-122">已叫用 `ErrorHandler` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="f371d-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="f371d-123">Handled</span><span class="sxs-lookup"><span data-stu-id="f371d-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="f371d-124">如果錯誤處理常式已處理錯誤，則為 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="f371d-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="f371d-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="f371d-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="f371d-126">已處理之例外狀況的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="f371d-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="f371d-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="f371d-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="f371d-128">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="f371d-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f371d-129">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="f371d-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f371d-130">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="f371d-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f371d-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f371d-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f371d-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f371d-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
