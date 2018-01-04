---
title: 1028 - CompleteTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cd2ee443d6c521f168a170a1079eb4e9657e2dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="aaa97-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="aaa97-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="aaa97-103">屬性</span><span class="sxs-lookup"><span data-stu-id="aaa97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aaa97-104">ID</span><span class="sxs-lookup"><span data-stu-id="aaa97-104">ID</span></span>|<span data-ttu-id="aaa97-105">1028</span><span class="sxs-lookup"><span data-stu-id="aaa97-105">1028</span></span>|  
|<span data-ttu-id="aaa97-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="aaa97-106">Keywords</span></span>|<span data-ttu-id="aaa97-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aaa97-107">WFRuntime</span></span>|  
|<span data-ttu-id="aaa97-108">層級</span><span class="sxs-lookup"><span data-stu-id="aaa97-108">Level</span></span>|<span data-ttu-id="aaa97-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="aaa97-109">Verbose</span></span>|  
|<span data-ttu-id="aaa97-110">通道</span><span class="sxs-lookup"><span data-stu-id="aaa97-110">Channel</span></span>|<span data-ttu-id="aaa97-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="aaa97-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aaa97-112">描述</span><span class="sxs-lookup"><span data-stu-id="aaa97-112">Description</span></span>  
 <span data-ttu-id="aaa97-113">表示 TransactionContextWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="aaa97-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aaa97-114">訊息</span><span class="sxs-lookup"><span data-stu-id="aaa97-114">Message</span></span>  
 <span data-ttu-id="aaa97-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="aaa97-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aaa97-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aaa97-116">Details</span></span>  
  
|<span data-ttu-id="aaa97-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="aaa97-117">Data Item Name</span></span>|<span data-ttu-id="aaa97-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="aaa97-118">Data Item Type</span></span>|<span data-ttu-id="aaa97-119">描述</span><span class="sxs-lookup"><span data-stu-id="aaa97-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aaa97-120">活動</span><span class="sxs-lookup"><span data-stu-id="aaa97-120">Activity</span></span>|<span data-ttu-id="aaa97-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="aaa97-121">xs:string</span></span>|<span data-ttu-id="aaa97-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="aaa97-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="aaa97-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="aaa97-123">DisplayName</span></span>|<span data-ttu-id="aaa97-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="aaa97-124">xs:string</span></span>|<span data-ttu-id="aaa97-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="aaa97-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="aaa97-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="aaa97-126">InstanceId</span></span>|<span data-ttu-id="aaa97-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="aaa97-127">xs:string</span></span>|<span data-ttu-id="aaa97-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="aaa97-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="aaa97-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aaa97-129">AppDomain</span></span>|<span data-ttu-id="aaa97-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="aaa97-130">xs:string</span></span>|<span data-ttu-id="aaa97-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="aaa97-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
