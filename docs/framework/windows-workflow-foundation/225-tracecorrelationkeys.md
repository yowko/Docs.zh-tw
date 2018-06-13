---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512134"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="c7bad-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="c7bad-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="c7bad-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c7bad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7bad-104">ID</span><span class="sxs-lookup"><span data-stu-id="c7bad-104">ID</span></span>|<span data-ttu-id="c7bad-105">225</span><span class="sxs-lookup"><span data-stu-id="c7bad-105">225</span></span>|  
|<span data-ttu-id="c7bad-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c7bad-106">Keywords</span></span>|<span data-ttu-id="c7bad-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c7bad-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c7bad-108">層級</span><span class="sxs-lookup"><span data-stu-id="c7bad-108">Level</span></span>|<span data-ttu-id="c7bad-109">資訊</span><span class="sxs-lookup"><span data-stu-id="c7bad-109">Information</span></span>|  
|<span data-ttu-id="c7bad-110">通道</span><span class="sxs-lookup"><span data-stu-id="c7bad-110">Channel</span></span>|<span data-ttu-id="c7bad-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c7bad-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7bad-112">描述</span><span class="sxs-lookup"><span data-stu-id="c7bad-112">Description</span></span>  
 <span data-ttu-id="c7bad-113">此事件是在內容架構相互關聯用於工作流程服務時發出。</span><span class="sxs-lookup"><span data-stu-id="c7bad-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="c7bad-114">其中包含套用的相互關聯索引鍵，可用來讓訊息與執行個體相互關聯。</span><span class="sxs-lookup"><span data-stu-id="c7bad-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7bad-115">訊息</span><span class="sxs-lookup"><span data-stu-id="c7bad-115">Message</span></span>  
 <span data-ttu-id="c7bad-116">在父範圍 '%3' 中使用 '%2' 值計算的相互關聯索引鍵 '%1'。</span><span class="sxs-lookup"><span data-stu-id="c7bad-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7bad-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7bad-117">Details</span></span>  
  
|<span data-ttu-id="c7bad-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c7bad-118">Data Item Name</span></span>|<span data-ttu-id="c7bad-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c7bad-119">Data Item Type</span></span>|<span data-ttu-id="c7bad-120">描述</span><span class="sxs-lookup"><span data-stu-id="c7bad-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7bad-121">執行個體索引鍵</span><span class="sxs-lookup"><span data-stu-id="c7bad-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="c7bad-122">產生自相互關聯值的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c7bad-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="c7bad-123">值</span><span class="sxs-lookup"><span data-stu-id="c7bad-123">Values</span></span>|`xs:string`|<span data-ttu-id="c7bad-124">用來計算相互關聯執行個體索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="c7bad-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="c7bad-125">父範圍</span><span class="sxs-lookup"><span data-stu-id="c7bad-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="c7bad-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c7bad-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c7bad-127">若是 Web 裝載的服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="c7bad-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c7bad-128">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="c7bad-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c7bad-129">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="c7bad-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c7bad-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c7bad-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c7bad-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c7bad-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
