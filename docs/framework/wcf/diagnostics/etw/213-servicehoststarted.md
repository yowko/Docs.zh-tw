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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61d79adce71be9ef93e9232e01a8cba5f5319f79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="352db-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="352db-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="352db-103">屬性</span><span class="sxs-lookup"><span data-stu-id="352db-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="352db-104">ID</span><span class="sxs-lookup"><span data-stu-id="352db-104">ID</span></span>|<span data-ttu-id="352db-105">213</span><span class="sxs-lookup"><span data-stu-id="352db-105">213</span></span>|  
|<span data-ttu-id="352db-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="352db-106">Keywords</span></span>|<span data-ttu-id="352db-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceHost</span><span class="sxs-lookup"><span data-stu-id="352db-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="352db-108">層級</span><span class="sxs-lookup"><span data-stu-id="352db-108">Level</span></span>|<span data-ttu-id="352db-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="352db-109">LogAlways</span></span>|  
|<span data-ttu-id="352db-110">通道</span><span class="sxs-lookup"><span data-stu-id="352db-110">Channel</span></span>|<span data-ttu-id="352db-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="352db-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="352db-112">描述</span><span class="sxs-lookup"><span data-stu-id="352db-112">Description</span></span>  
 <span data-ttu-id="352db-113">此事件是在 Web 裝載服務主機啟動時發出。</span><span class="sxs-lookup"><span data-stu-id="352db-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="352db-114">這種情況通常是在訊息啟動服務時發生。</span><span class="sxs-lookup"><span data-stu-id="352db-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="352db-115">此外也可能在服務設定為自動啟動時發生。</span><span class="sxs-lookup"><span data-stu-id="352db-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="352db-116">訊息</span><span class="sxs-lookup"><span data-stu-id="352db-116">Message</span></span>  
 <span data-ttu-id="352db-117">ServiceHost 已啟動: '%1'。</span><span class="sxs-lookup"><span data-stu-id="352db-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="352db-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="352db-118">Details</span></span>  
  
|<span data-ttu-id="352db-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="352db-119">Data Item Name</span></span>|<span data-ttu-id="352db-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="352db-120">Data Item Type</span></span>|<span data-ttu-id="352db-121">描述</span><span class="sxs-lookup"><span data-stu-id="352db-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="352db-122">服務型別名稱</span><span class="sxs-lookup"><span data-stu-id="352db-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="352db-123">服務實作之型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="352db-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="352db-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="352db-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="352db-125">若是 Web 裝載的服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="352db-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="352db-126">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="352db-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="352db-127">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="352db-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="352db-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="352db-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="352db-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="352db-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
