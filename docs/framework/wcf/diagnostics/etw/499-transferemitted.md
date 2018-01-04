---
title: 499 - TransferEmitted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1034ae6bd6072a3849d72fafcad55c61e500439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="0d63b-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="0d63b-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="0d63b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0d63b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d63b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="0d63b-104">ID</span></span>|<span data-ttu-id="0d63b-105">499</span><span class="sxs-lookup"><span data-stu-id="0d63b-105">499</span></span>|  
|<span data-ttu-id="0d63b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0d63b-106">Keywords</span></span>|<span data-ttu-id="0d63b-107">Troubleshooting，UserEvents，EndToEndMonitoring，ServiceModel，WFTracking，ServiceHost，WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="0d63b-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="0d63b-108">層級</span><span class="sxs-lookup"><span data-stu-id="0d63b-108">Level</span></span>|<span data-ttu-id="0d63b-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="0d63b-109">LogAlways</span></span>|  
|<span data-ttu-id="0d63b-110">通道</span><span class="sxs-lookup"><span data-stu-id="0d63b-110">Channel</span></span>|<span data-ttu-id="0d63b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0d63b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0d63b-112">描述</span><span class="sxs-lookup"><span data-stu-id="0d63b-112">Description</span></span>  
 <span data-ttu-id="0d63b-113">當傳輸事件發生時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="0d63b-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0d63b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0d63b-114">Message</span></span>  
 <span data-ttu-id="0d63b-115">已發出傳輸事件。</span><span class="sxs-lookup"><span data-stu-id="0d63b-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0d63b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0d63b-116">Details</span></span>  
  
|<span data-ttu-id="0d63b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0d63b-117">Data Item Name</span></span>|<span data-ttu-id="0d63b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0d63b-118">Data Item Type</span></span>|<span data-ttu-id="0d63b-119">描述</span><span class="sxs-lookup"><span data-stu-id="0d63b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0d63b-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="0d63b-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="0d63b-121">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="0d63b-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0d63b-122">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="0d63b-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0d63b-123">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="0d63b-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0d63b-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0d63b-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0d63b-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0d63b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
