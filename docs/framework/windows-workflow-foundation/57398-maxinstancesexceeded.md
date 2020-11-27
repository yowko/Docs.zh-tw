---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: bd490aad24fba4550bc778799cd6f836dcfd466c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289174"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="33eda-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="33eda-102">57398 - MaxInstancesExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="33eda-103">屬性</span><span class="sxs-lookup"><span data-stu-id="33eda-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33eda-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="33eda-104">ID</span></span>|<span data-ttu-id="33eda-105">57398</span><span class="sxs-lookup"><span data-stu-id="33eda-105">57398</span></span>|  
|<span data-ttu-id="33eda-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="33eda-106">Keywords</span></span>|<span data-ttu-id="33eda-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="33eda-107">WFServices</span></span>|  
|<span data-ttu-id="33eda-108">層級</span><span class="sxs-lookup"><span data-stu-id="33eda-108">Level</span></span>|<span data-ttu-id="33eda-109">警告</span><span class="sxs-lookup"><span data-stu-id="33eda-109">Warning</span></span>|  
|<span data-ttu-id="33eda-110">通路</span><span class="sxs-lookup"><span data-stu-id="33eda-110">Channel</span></span>|<span data-ttu-id="33eda-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="33eda-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="33eda-112">描述</span><span class="sxs-lookup"><span data-stu-id="33eda-112">Description</span></span>  

 <span data-ttu-id="33eda-113">表示系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="33eda-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="33eda-114">訊息</span><span class="sxs-lookup"><span data-stu-id="33eda-114">Message</span></span>  

 <span data-ttu-id="33eda-115">系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="33eda-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="33eda-116">此節流的限制設為 %1。</span><span class="sxs-lookup"><span data-stu-id="33eda-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="33eda-117">若要變更節流值，請修改 serviceThrottle 元素中的屬性 'maxConcurrentInstances'，或修改行為 ServiceThrottlingBehavior 的 'MaxConcurrentInstances' 屬性。</span><span class="sxs-lookup"><span data-stu-id="33eda-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="33eda-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="33eda-118">Details</span></span>  
  
|<span data-ttu-id="33eda-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="33eda-119">Data Item Name</span></span>|<span data-ttu-id="33eda-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="33eda-120">Data Item Type</span></span>|<span data-ttu-id="33eda-121">描述</span><span class="sxs-lookup"><span data-stu-id="33eda-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="33eda-122">Name</span><span class="sxs-lookup"><span data-stu-id="33eda-122">Name</span></span>|<span data-ttu-id="33eda-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="33eda-123">xs:string</span></span>|<span data-ttu-id="33eda-124">項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="33eda-124">The name of the item.</span></span>|  
|<span data-ttu-id="33eda-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="33eda-125">AppDomain</span></span>|<span data-ttu-id="33eda-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="33eda-126">xs:string</span></span>|<span data-ttu-id="33eda-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="33eda-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
