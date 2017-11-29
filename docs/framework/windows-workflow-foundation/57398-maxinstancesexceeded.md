---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="2b900-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="2b900-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="2b900-103">屬性</span><span class="sxs-lookup"><span data-stu-id="2b900-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b900-104">ID</span><span class="sxs-lookup"><span data-stu-id="2b900-104">ID</span></span>|<span data-ttu-id="2b900-105">57398</span><span class="sxs-lookup"><span data-stu-id="2b900-105">57398</span></span>|  
|<span data-ttu-id="2b900-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="2b900-106">Keywords</span></span>|<span data-ttu-id="2b900-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="2b900-107">WFServices</span></span>|  
|<span data-ttu-id="2b900-108">層級</span><span class="sxs-lookup"><span data-stu-id="2b900-108">Level</span></span>|<span data-ttu-id="2b900-109">警告</span><span class="sxs-lookup"><span data-stu-id="2b900-109">Warning</span></span>|  
|<span data-ttu-id="2b900-110">通道</span><span class="sxs-lookup"><span data-stu-id="2b900-110">Channel</span></span>|<span data-ttu-id="2b900-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2b900-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b900-112">描述</span><span class="sxs-lookup"><span data-stu-id="2b900-112">Description</span></span>  
 <span data-ttu-id="2b900-113">表示系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="2b900-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b900-114">訊息</span><span class="sxs-lookup"><span data-stu-id="2b900-114">Message</span></span>  
 <span data-ttu-id="2b900-115">系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="2b900-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="2b900-116">此節流的限制設為 %1。</span><span class="sxs-lookup"><span data-stu-id="2b900-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="2b900-117">若要變更節流值，請修改 serviceThrottle 元素中的屬性 'maxConcurrentInstances'，或修改行為 ServiceThrottlingBehavior 的 'MaxConcurrentInstances' 屬性。</span><span class="sxs-lookup"><span data-stu-id="2b900-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b900-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2b900-118">Details</span></span>  
  
|<span data-ttu-id="2b900-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="2b900-119">Data Item Name</span></span>|<span data-ttu-id="2b900-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="2b900-120">Data Item Type</span></span>|<span data-ttu-id="2b900-121">描述</span><span class="sxs-lookup"><span data-stu-id="2b900-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b900-122">名稱</span><span class="sxs-lookup"><span data-stu-id="2b900-122">Name</span></span>|<span data-ttu-id="2b900-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b900-123">xs:string</span></span>|<span data-ttu-id="2b900-124">項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b900-124">The name of the item.</span></span>|  
|<span data-ttu-id="2b900-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b900-125">AppDomain</span></span>|<span data-ttu-id="2b900-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b900-126">xs:string</span></span>|<span data-ttu-id="2b900-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="2b900-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
