---
title: 219 - ServiceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fceff5c748076c75c942f515e2621edff5106f4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="219---serviceexception"></a><span data-ttu-id="fe0fe-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="fe0fe-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="fe0fe-103">屬性</span><span class="sxs-lookup"><span data-stu-id="fe0fe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe0fe-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="fe0fe-104">ID</span></span>|<span data-ttu-id="fe0fe-105">219</span><span class="sxs-lookup"><span data-stu-id="fe0fe-105">219</span></span>|  
|<span data-ttu-id="fe0fe-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="fe0fe-106">Keywords</span></span>|<span data-ttu-id="fe0fe-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe0fe-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fe0fe-108">層級</span><span class="sxs-lookup"><span data-stu-id="fe0fe-108">Level</span></span>|<span data-ttu-id="fe0fe-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="fe0fe-109">Error</span></span>|  
|<span data-ttu-id="fe0fe-110">通道</span><span class="sxs-lookup"><span data-stu-id="fe0fe-110">Channel</span></span>|<span data-ttu-id="fe0fe-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fe0fe-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fe0fe-112">描述</span><span class="sxs-lookup"><span data-stu-id="fe0fe-112">Description</span></span>  
 <span data-ttu-id="fe0fe-113">當 WCF 服務遇到未處理的例外狀況時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="fe0fe-114">這包含啟動期間、訊息處理期間和使用者程式碼中的未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fe0fe-115">訊息</span><span class="sxs-lookup"><span data-stu-id="fe0fe-115">Message</span></span>  
 <span data-ttu-id="fe0fe-116">訊息處理期間發生了未處理的例外狀況 (型別為 '%2')。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="fe0fe-117">完整例外狀況 ToString: %1。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fe0fe-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fe0fe-118">Details</span></span>  
  
|<span data-ttu-id="fe0fe-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="fe0fe-119">Data Item Name</span></span>|<span data-ttu-id="fe0fe-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="fe0fe-120">Data Item Type</span></span>|<span data-ttu-id="fe0fe-121">描述</span><span class="sxs-lookup"><span data-stu-id="fe0fe-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fe0fe-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="fe0fe-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="fe0fe-123">在 CLR 例外狀況上呼叫 `ToString`() 的結果。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="fe0fe-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="fe0fe-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="fe0fe-125">例外狀況型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="fe0fe-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="fe0fe-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="fe0fe-127">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fe0fe-128">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fe0fe-129">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fe0fe-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fe0fe-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fe0fe-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="fe0fe-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
