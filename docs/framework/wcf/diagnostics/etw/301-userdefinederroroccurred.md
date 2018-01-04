---
title: 301 - UserDefinedErrorOccurred
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b24d54930a29a24dab97ce403c2808fb74b8cbfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="9429b-102">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="9429b-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="9429b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9429b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9429b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="9429b-104">ID</span></span>|<span data-ttu-id="9429b-105">301</span><span class="sxs-lookup"><span data-stu-id="9429b-105">301</span></span>|  
|<span data-ttu-id="9429b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9429b-106">Keywords</span></span>|<span data-ttu-id="9429b-107">Troubleshooting，HealthMonitoring，UserEvents，ServiceModel，EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="9429b-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="9429b-108">層級</span><span class="sxs-lookup"><span data-stu-id="9429b-108">Level</span></span>|<span data-ttu-id="9429b-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="9429b-109">Error</span></span>|  
|<span data-ttu-id="9429b-110">通道</span><span class="sxs-lookup"><span data-stu-id="9429b-110">Channel</span></span>|<span data-ttu-id="9429b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9429b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9429b-112">描述</span><span class="sxs-lookup"><span data-stu-id="9429b-112">Description</span></span>  
 <span data-ttu-id="9429b-113">此事件是由使用者程式碼所發出。</span><span class="sxs-lookup"><span data-stu-id="9429b-113">This event is emitted from user code.</span></span> <span data-ttu-id="9429b-114">當開發人員的服務中發生自訂定義錯誤時，可能會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="9429b-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="9429b-115">這項操作可使用 <xref:System.Diagnostics.Eventing> API 達到目的。</span><span class="sxs-lookup"><span data-stu-id="9429b-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="9429b-116">另外還有 WCF 範例，可包裝該 API 並示範如何正確發出此事件。</span><span class="sxs-lookup"><span data-stu-id="9429b-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9429b-117">訊息</span><span class="sxs-lookup"><span data-stu-id="9429b-117">Message</span></span>  
 <span data-ttu-id="9429b-118">名稱:'%1'，參考:'%2'，承載:%3。</span><span class="sxs-lookup"><span data-stu-id="9429b-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="9429b-119">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9429b-119">Details</span></span>  
  
|<span data-ttu-id="9429b-120">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9429b-120">Data Item Name</span></span>|<span data-ttu-id="9429b-121">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9429b-121">Data Item Type</span></span>|<span data-ttu-id="9429b-122">描述</span><span class="sxs-lookup"><span data-stu-id="9429b-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9429b-123">名稱</span><span class="sxs-lookup"><span data-stu-id="9429b-123">Name</span></span>|`xs:string`|<span data-ttu-id="9429b-124">使用者定義的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="9429b-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="9429b-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="9429b-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="9429b-126">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="9429b-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9429b-127">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="9429b-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9429b-128">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="9429b-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9429b-129">承載</span><span class="sxs-lookup"><span data-stu-id="9429b-129">Payload</span></span>|`xs:string`|<span data-ttu-id="9429b-130">使用者定義的事件裝載。</span><span class="sxs-lookup"><span data-stu-id="9429b-130">The user-defined payload of the event.</span></span>|
