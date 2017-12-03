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
ms.openlocfilehash: abe1f560cc984551f069a75873a7e5545aec03cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="58830-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="58830-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="58830-103">屬性</span><span class="sxs-lookup"><span data-stu-id="58830-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58830-104">ID</span><span class="sxs-lookup"><span data-stu-id="58830-104">ID</span></span>|<span data-ttu-id="58830-105">4212</span><span class="sxs-lookup"><span data-stu-id="58830-105">4212</span></span>|  
|<span data-ttu-id="58830-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="58830-106">Keywords</span></span>|<span data-ttu-id="58830-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="58830-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="58830-108">層級</span><span class="sxs-lookup"><span data-stu-id="58830-108">Level</span></span>|<span data-ttu-id="58830-109">警告</span><span class="sxs-lookup"><span data-stu-id="58830-109">Warning</span></span>|  
|<span data-ttu-id="58830-110">通道</span><span class="sxs-lookup"><span data-stu-id="58830-110">Channel</span></span>|<span data-ttu-id="58830-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="58830-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58830-112">描述</span><span class="sxs-lookup"><span data-stu-id="58830-112">Description</span></span>  
 <span data-ttu-id="58830-113">SQL 提供者嘗試擷取執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="58830-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58830-114">訊息</span><span class="sxs-lookup"><span data-stu-id="58830-114">Message</span></span>  
 <span data-ttu-id="58830-115">嘗試取得執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="58830-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="58830-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="58830-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="58830-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="58830-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58830-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58830-118">Details</span></span>  
  
|<span data-ttu-id="58830-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="58830-119">Data Item Name</span></span>|<span data-ttu-id="58830-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="58830-120">Data Item Type</span></span>|<span data-ttu-id="58830-121">描述</span><span class="sxs-lookup"><span data-stu-id="58830-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58830-122">延遲</span><span class="sxs-lookup"><span data-stu-id="58830-122">Delay</span></span>|<span data-ttu-id="58830-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="58830-123">xs:string</span></span>|<span data-ttu-id="58830-124">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="58830-124">The delay between retries.</span></span>|  
|<span data-ttu-id="58830-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="58830-125">AppDomain</span></span>|<span data-ttu-id="58830-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="58830-126">xs:string</span></span>|<span data-ttu-id="58830-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="58830-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
