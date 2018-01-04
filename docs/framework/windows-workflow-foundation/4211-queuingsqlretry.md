---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ffd44cf9d2333b22e3be809d05f2fa8c33d4cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="043c8-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="043c8-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="043c8-103">屬性</span><span class="sxs-lookup"><span data-stu-id="043c8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="043c8-104">ID</span><span class="sxs-lookup"><span data-stu-id="043c8-104">ID</span></span>|<span data-ttu-id="043c8-105">4211</span><span class="sxs-lookup"><span data-stu-id="043c8-105">4211</span></span>|  
|<span data-ttu-id="043c8-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="043c8-106">Keywords</span></span>|<span data-ttu-id="043c8-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="043c8-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="043c8-108">層級</span><span class="sxs-lookup"><span data-stu-id="043c8-108">Level</span></span>|<span data-ttu-id="043c8-109">警告</span><span class="sxs-lookup"><span data-stu-id="043c8-109">Warning</span></span>|  
|<span data-ttu-id="043c8-110">通道</span><span class="sxs-lookup"><span data-stu-id="043c8-110">Channel</span></span>|<span data-ttu-id="043c8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="043c8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="043c8-112">描述</span><span class="sxs-lookup"><span data-stu-id="043c8-112">Description</span></span>  
 <span data-ttu-id="043c8-113">表示佇列 SQL 重試。</span><span class="sxs-lookup"><span data-stu-id="043c8-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="043c8-114">訊息</span><span class="sxs-lookup"><span data-stu-id="043c8-114">Message</span></span>  
 <span data-ttu-id="043c8-115">佇列 SQL 重試，但延遲 %1 毫秒。</span><span class="sxs-lookup"><span data-stu-id="043c8-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="043c8-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="043c8-116">Details</span></span>  
  
|<span data-ttu-id="043c8-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="043c8-117">Data Item Name</span></span>|<span data-ttu-id="043c8-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="043c8-118">Data Item Type</span></span>|<span data-ttu-id="043c8-119">描述</span><span class="sxs-lookup"><span data-stu-id="043c8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="043c8-120">延遲</span><span class="sxs-lookup"><span data-stu-id="043c8-120">Delay</span></span>|<span data-ttu-id="043c8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="043c8-121">xs:string</span></span>|<span data-ttu-id="043c8-122">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="043c8-122">The delay between retries.</span></span>|  
|<span data-ttu-id="043c8-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="043c8-123">AppDomain</span></span>|<span data-ttu-id="043c8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="043c8-124">xs:string</span></span>|<span data-ttu-id="043c8-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="043c8-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
