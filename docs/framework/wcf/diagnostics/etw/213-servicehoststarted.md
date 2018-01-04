---
title: 213 - ServiceHostStarted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a83cb1cfb87b562add1a791de5a651b563d63d4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="4b496-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="4b496-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="4b496-103">屬性</span><span class="sxs-lookup"><span data-stu-id="4b496-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b496-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="4b496-104">ID</span></span>|<span data-ttu-id="4b496-105">213</span><span class="sxs-lookup"><span data-stu-id="4b496-105">213</span></span>|  
|<span data-ttu-id="4b496-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="4b496-106">Keywords</span></span>|<span data-ttu-id="4b496-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceHost</span><span class="sxs-lookup"><span data-stu-id="4b496-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="4b496-108">層級</span><span class="sxs-lookup"><span data-stu-id="4b496-108">Level</span></span>|<span data-ttu-id="4b496-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="4b496-109">LogAlways</span></span>|  
|<span data-ttu-id="4b496-110">通道</span><span class="sxs-lookup"><span data-stu-id="4b496-110">Channel</span></span>|<span data-ttu-id="4b496-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4b496-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4b496-112">描述</span><span class="sxs-lookup"><span data-stu-id="4b496-112">Description</span></span>  
 <span data-ttu-id="4b496-113">此事件是在 Web 裝載服務主機啟動時發出。</span><span class="sxs-lookup"><span data-stu-id="4b496-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="4b496-114">這種情況通常是在訊息啟動服務時發生。</span><span class="sxs-lookup"><span data-stu-id="4b496-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="4b496-115">此外也可能在服務設定為自動啟動時發生。</span><span class="sxs-lookup"><span data-stu-id="4b496-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4b496-116">訊息</span><span class="sxs-lookup"><span data-stu-id="4b496-116">Message</span></span>  
 <span data-ttu-id="4b496-117">ServiceHost 已啟動: '%1'。</span><span class="sxs-lookup"><span data-stu-id="4b496-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4b496-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4b496-118">Details</span></span>  
  
|<span data-ttu-id="4b496-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="4b496-119">Data Item Name</span></span>|<span data-ttu-id="4b496-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="4b496-120">Data Item Type</span></span>|<span data-ttu-id="4b496-121">描述</span><span class="sxs-lookup"><span data-stu-id="4b496-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4b496-122">服務型別名稱</span><span class="sxs-lookup"><span data-stu-id="4b496-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="4b496-123">服務實作之型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="4b496-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="4b496-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="4b496-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="4b496-125">若是 Web 裝載的服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="4b496-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4b496-126">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="4b496-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4b496-127">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="4b496-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4b496-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4b496-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4b496-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="4b496-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
