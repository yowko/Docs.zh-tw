---
title: 207 - FaultProviderInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9035739f8625a07e8bf2b9bce2fe109880676405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="8cd99-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="8cd99-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="8cd99-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8cd99-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8cd99-104">ID</span><span class="sxs-lookup"><span data-stu-id="8cd99-104">ID</span></span>|<span data-ttu-id="8cd99-105">207</span><span class="sxs-lookup"><span data-stu-id="8cd99-105">207</span></span>|  
|<span data-ttu-id="8cd99-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8cd99-106">Keywords</span></span>|<span data-ttu-id="8cd99-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8cd99-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8cd99-108">層級</span><span class="sxs-lookup"><span data-stu-id="8cd99-108">Level</span></span>|<span data-ttu-id="8cd99-109">資訊</span><span class="sxs-lookup"><span data-stu-id="8cd99-109">Information</span></span>|  
|<span data-ttu-id="8cd99-110">通道</span><span class="sxs-lookup"><span data-stu-id="8cd99-110">Channel</span></span>|<span data-ttu-id="8cd99-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8cd99-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8cd99-112">描述</span><span class="sxs-lookup"><span data-stu-id="8cd99-112">Description</span></span>  
 <span data-ttu-id="8cd99-113">此事件是在已叫用 `FaultProvider` 之後發出。</span><span class="sxs-lookup"><span data-stu-id="8cd99-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8cd99-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8cd99-114">Message</span></span>  
 <span data-ttu-id="8cd99-115">發送器已叫用型別為 '%1' 的 FaultProvider，其例外狀況型別為 '%2'。</span><span class="sxs-lookup"><span data-stu-id="8cd99-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8cd99-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8cd99-116">Details</span></span>  
  
|<span data-ttu-id="8cd99-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8cd99-117">Data Item Name</span></span>|<span data-ttu-id="8cd99-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8cd99-118">Data Item Type</span></span>|<span data-ttu-id="8cd99-119">描述</span><span class="sxs-lookup"><span data-stu-id="8cd99-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8cd99-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="8cd99-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="8cd99-121">已叫用 `FaultProvider` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="8cd99-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="8cd99-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="8cd99-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="8cd99-123">`FaultProvider` 已處理之例外狀況的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="8cd99-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="8cd99-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="8cd99-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="8cd99-125">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="8cd99-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8cd99-126">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="8cd99-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8cd99-127">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="8cd99-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8cd99-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8cd99-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8cd99-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8cd99-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
