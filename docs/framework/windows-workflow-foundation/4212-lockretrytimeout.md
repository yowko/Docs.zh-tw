---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f47b383547da5145c5307670fee2eda10fcab402
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="5f1a0-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="5f1a0-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="5f1a0-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5f1a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f1a0-104">ID</span><span class="sxs-lookup"><span data-stu-id="5f1a0-104">ID</span></span>|<span data-ttu-id="5f1a0-105">4212</span><span class="sxs-lookup"><span data-stu-id="5f1a0-105">4212</span></span>|  
|<span data-ttu-id="5f1a0-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f1a0-106">Keywords</span></span>|<span data-ttu-id="5f1a0-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5f1a0-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5f1a0-108">層級</span><span class="sxs-lookup"><span data-stu-id="5f1a0-108">Level</span></span>|<span data-ttu-id="5f1a0-109">警告</span><span class="sxs-lookup"><span data-stu-id="5f1a0-109">Warning</span></span>|  
|<span data-ttu-id="5f1a0-110">通道</span><span class="sxs-lookup"><span data-stu-id="5f1a0-110">Channel</span></span>|<span data-ttu-id="5f1a0-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5f1a0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5f1a0-112">描述</span><span class="sxs-lookup"><span data-stu-id="5f1a0-112">Description</span></span>  
 <span data-ttu-id="5f1a0-113">SQL 提供者嘗試擷取執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="5f1a0-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5f1a0-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5f1a0-114">Message</span></span>  
 <span data-ttu-id="5f1a0-115">嘗試取得執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="5f1a0-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="5f1a0-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="5f1a0-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="5f1a0-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="5f1a0-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5f1a0-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5f1a0-118">Details</span></span>  
  
|<span data-ttu-id="5f1a0-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5f1a0-119">Data Item Name</span></span>|<span data-ttu-id="5f1a0-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5f1a0-120">Data Item Type</span></span>|<span data-ttu-id="5f1a0-121">描述</span><span class="sxs-lookup"><span data-stu-id="5f1a0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5f1a0-122">延遲</span><span class="sxs-lookup"><span data-stu-id="5f1a0-122">Delay</span></span>|<span data-ttu-id="5f1a0-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f1a0-123">xs:string</span></span>|<span data-ttu-id="5f1a0-124">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="5f1a0-124">The delay between retries.</span></span>|  
|<span data-ttu-id="5f1a0-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5f1a0-125">AppDomain</span></span>|<span data-ttu-id="5f1a0-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f1a0-126">xs:string</span></span>|<span data-ttu-id="5f1a0-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5f1a0-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
