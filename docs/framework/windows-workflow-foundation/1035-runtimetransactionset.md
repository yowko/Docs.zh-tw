---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a8a4ab6212a5e83b59fd7523df9cd875e7b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="3968f-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="3968f-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="3968f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3968f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3968f-104">ID</span><span class="sxs-lookup"><span data-stu-id="3968f-104">ID</span></span>|<span data-ttu-id="3968f-105">1035</span><span class="sxs-lookup"><span data-stu-id="3968f-105">1035</span></span>|  
|<span data-ttu-id="3968f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3968f-106">Keywords</span></span>|<span data-ttu-id="3968f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3968f-107">WFRuntime</span></span>|  
|<span data-ttu-id="3968f-108">層級</span><span class="sxs-lookup"><span data-stu-id="3968f-108">Level</span></span>|<span data-ttu-id="3968f-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="3968f-109">Verbose</span></span>|  
|<span data-ttu-id="3968f-110">通道</span><span class="sxs-lookup"><span data-stu-id="3968f-110">Channel</span></span>|<span data-ttu-id="3968f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3968f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3968f-112">描述</span><span class="sxs-lookup"><span data-stu-id="3968f-112">Description</span></span>  
 <span data-ttu-id="3968f-113">表示活動已設定執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="3968f-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3968f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3968f-114">Message</span></span>  
 <span data-ttu-id="3968f-115">執行階段交易已預先設定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="3968f-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="3968f-116">執行已隔離到活動 '%4'、 DisplayName: '%5'、 InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="3968f-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3968f-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3968f-117">Details</span></span>  
  
|<span data-ttu-id="3968f-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3968f-118">Data Item Name</span></span>|<span data-ttu-id="3968f-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3968f-119">Data Item Type</span></span>|<span data-ttu-id="3968f-120">描述</span><span class="sxs-lookup"><span data-stu-id="3968f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3968f-121">活動</span><span class="sxs-lookup"><span data-stu-id="3968f-121">Activity</span></span>|<span data-ttu-id="3968f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="3968f-122">xs:string</span></span>|<span data-ttu-id="3968f-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="3968f-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="3968f-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3968f-124">DisplayName</span></span>|<span data-ttu-id="3968f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="3968f-125">xs:string</span></span>|<span data-ttu-id="3968f-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3968f-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="3968f-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3968f-127">InstanceId</span></span>|<span data-ttu-id="3968f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="3968f-128">xs:string</span></span>|<span data-ttu-id="3968f-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="3968f-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3968f-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="3968f-130">IsolatedActivity</span></span>|<span data-ttu-id="3968f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="3968f-131">xs:string</span></span>|<span data-ttu-id="3968f-132">隔離交易之目標活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="3968f-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="3968f-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3968f-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="3968f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="3968f-134">xs:string</span></span>|<span data-ttu-id="3968f-135">隔離交易之目標活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3968f-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="3968f-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3968f-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="3968f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="3968f-137">xs:string</span></span>|<span data-ttu-id="3968f-138">隔離交易之目標活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="3968f-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="3968f-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3968f-139">AppDomain</span></span>|<span data-ttu-id="3968f-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="3968f-140">xs:string</span></span>|<span data-ttu-id="3968f-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3968f-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
