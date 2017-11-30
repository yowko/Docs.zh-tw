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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 897e6ef8b739654a61058106966c870c47f8129a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="2d806-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="2d806-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="2d806-103">屬性</span><span class="sxs-lookup"><span data-stu-id="2d806-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d806-104">ID</span><span class="sxs-lookup"><span data-stu-id="2d806-104">ID</span></span>|<span data-ttu-id="2d806-105">4212</span><span class="sxs-lookup"><span data-stu-id="2d806-105">4212</span></span>|  
|<span data-ttu-id="2d806-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="2d806-106">Keywords</span></span>|<span data-ttu-id="2d806-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="2d806-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="2d806-108">層級</span><span class="sxs-lookup"><span data-stu-id="2d806-108">Level</span></span>|<span data-ttu-id="2d806-109">警告</span><span class="sxs-lookup"><span data-stu-id="2d806-109">Warning</span></span>|  
|<span data-ttu-id="2d806-110">通道</span><span class="sxs-lookup"><span data-stu-id="2d806-110">Channel</span></span>|<span data-ttu-id="2d806-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2d806-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2d806-112">描述</span><span class="sxs-lookup"><span data-stu-id="2d806-112">Description</span></span>  
 <span data-ttu-id="2d806-113">SQL 提供者嘗試擷取執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="2d806-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2d806-114">訊息</span><span class="sxs-lookup"><span data-stu-id="2d806-114">Message</span></span>  
 <span data-ttu-id="2d806-115">嘗試取得執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="2d806-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="2d806-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="2d806-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="2d806-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="2d806-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2d806-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2d806-118">Details</span></span>  
  
|<span data-ttu-id="2d806-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="2d806-119">Data Item Name</span></span>|<span data-ttu-id="2d806-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="2d806-120">Data Item Type</span></span>|<span data-ttu-id="2d806-121">描述</span><span class="sxs-lookup"><span data-stu-id="2d806-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2d806-122">延遲</span><span class="sxs-lookup"><span data-stu-id="2d806-122">Delay</span></span>|<span data-ttu-id="2d806-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="2d806-123">xs:string</span></span>|<span data-ttu-id="2d806-124">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="2d806-124">The delay between retries.</span></span>|  
|<span data-ttu-id="2d806-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2d806-125">AppDomain</span></span>|<span data-ttu-id="2d806-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2d806-126">xs:string</span></span>|<span data-ttu-id="2d806-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="2d806-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
