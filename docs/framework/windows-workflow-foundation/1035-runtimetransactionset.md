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
ms.openlocfilehash: 0fcd6662c0f8899b6830dc8e06cee4f56b5ff906
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="0db18-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="0db18-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="0db18-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0db18-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0db18-104">ID</span><span class="sxs-lookup"><span data-stu-id="0db18-104">ID</span></span>|<span data-ttu-id="0db18-105">1035</span><span class="sxs-lookup"><span data-stu-id="0db18-105">1035</span></span>|  
|<span data-ttu-id="0db18-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0db18-106">Keywords</span></span>|<span data-ttu-id="0db18-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0db18-107">WFRuntime</span></span>|  
|<span data-ttu-id="0db18-108">層級</span><span class="sxs-lookup"><span data-stu-id="0db18-108">Level</span></span>|<span data-ttu-id="0db18-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0db18-109">Verbose</span></span>|  
|<span data-ttu-id="0db18-110">通道</span><span class="sxs-lookup"><span data-stu-id="0db18-110">Channel</span></span>|<span data-ttu-id="0db18-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0db18-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0db18-112">描述</span><span class="sxs-lookup"><span data-stu-id="0db18-112">Description</span></span>  
 <span data-ttu-id="0db18-113">表示活動已設定執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="0db18-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0db18-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0db18-114">Message</span></span>  
 <span data-ttu-id="0db18-115">執行階段交易已預先設定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="0db18-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="0db18-116">執行已隔離到活動 '%4'、 DisplayName: '%5'、 InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="0db18-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0db18-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0db18-117">Details</span></span>  
  
|<span data-ttu-id="0db18-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0db18-118">Data Item Name</span></span>|<span data-ttu-id="0db18-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0db18-119">Data Item Type</span></span>|<span data-ttu-id="0db18-120">描述</span><span class="sxs-lookup"><span data-stu-id="0db18-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0db18-121">活動</span><span class="sxs-lookup"><span data-stu-id="0db18-121">Activity</span></span>|<span data-ttu-id="0db18-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0db18-122">xs:string</span></span>|<span data-ttu-id="0db18-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0db18-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="0db18-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0db18-124">DisplayName</span></span>|<span data-ttu-id="0db18-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0db18-125">xs:string</span></span>|<span data-ttu-id="0db18-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0db18-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="0db18-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0db18-127">InstanceId</span></span>|<span data-ttu-id="0db18-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="0db18-128">xs:string</span></span>|<span data-ttu-id="0db18-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="0db18-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0db18-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="0db18-130">IsolatedActivity</span></span>|<span data-ttu-id="0db18-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="0db18-131">xs:string</span></span>|<span data-ttu-id="0db18-132">隔離交易之目標活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0db18-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="0db18-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0db18-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="0db18-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="0db18-134">xs:string</span></span>|<span data-ttu-id="0db18-135">隔離交易之目標活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0db18-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="0db18-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0db18-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="0db18-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="0db18-137">xs:string</span></span>|<span data-ttu-id="0db18-138">隔離交易之目標活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="0db18-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="0db18-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0db18-139">AppDomain</span></span>|<span data-ttu-id="0db18-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="0db18-140">xs:string</span></span>|<span data-ttu-id="0db18-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0db18-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
