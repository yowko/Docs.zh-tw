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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="fecfb-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="fecfb-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="fecfb-103">屬性</span><span class="sxs-lookup"><span data-stu-id="fecfb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fecfb-104">ID</span><span class="sxs-lookup"><span data-stu-id="fecfb-104">ID</span></span>|<span data-ttu-id="fecfb-105">1035</span><span class="sxs-lookup"><span data-stu-id="fecfb-105">1035</span></span>|  
|<span data-ttu-id="fecfb-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="fecfb-106">Keywords</span></span>|<span data-ttu-id="fecfb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fecfb-107">WFRuntime</span></span>|  
|<span data-ttu-id="fecfb-108">層級</span><span class="sxs-lookup"><span data-stu-id="fecfb-108">Level</span></span>|<span data-ttu-id="fecfb-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="fecfb-109">Verbose</span></span>|  
|<span data-ttu-id="fecfb-110">通道</span><span class="sxs-lookup"><span data-stu-id="fecfb-110">Channel</span></span>|<span data-ttu-id="fecfb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fecfb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fecfb-112">描述</span><span class="sxs-lookup"><span data-stu-id="fecfb-112">Description</span></span>  
 <span data-ttu-id="fecfb-113">表示活動已設定執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="fecfb-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fecfb-114">訊息</span><span class="sxs-lookup"><span data-stu-id="fecfb-114">Message</span></span>  
 <span data-ttu-id="fecfb-115">執行階段交易已預先設定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="fecfb-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="fecfb-116">執行已隔離到活動 '%4'、 DisplayName: '%5'、 InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="fecfb-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fecfb-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fecfb-117">Details</span></span>  
  
|<span data-ttu-id="fecfb-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="fecfb-118">Data Item Name</span></span>|<span data-ttu-id="fecfb-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="fecfb-119">Data Item Type</span></span>|<span data-ttu-id="fecfb-120">描述</span><span class="sxs-lookup"><span data-stu-id="fecfb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fecfb-121">活動</span><span class="sxs-lookup"><span data-stu-id="fecfb-121">Activity</span></span>|<span data-ttu-id="fecfb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fecfb-122">xs:string</span></span>|<span data-ttu-id="fecfb-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="fecfb-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="fecfb-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fecfb-124">DisplayName</span></span>|<span data-ttu-id="fecfb-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fecfb-125">xs:string</span></span>|<span data-ttu-id="fecfb-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="fecfb-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="fecfb-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="fecfb-127">InstanceId</span></span>|<span data-ttu-id="fecfb-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="fecfb-128">xs:string</span></span>|<span data-ttu-id="fecfb-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="fecfb-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="fecfb-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="fecfb-130">IsolatedActivity</span></span>|<span data-ttu-id="fecfb-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="fecfb-131">xs:string</span></span>|<span data-ttu-id="fecfb-132">隔離交易之目標活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="fecfb-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="fecfb-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fecfb-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="fecfb-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="fecfb-134">xs:string</span></span>|<span data-ttu-id="fecfb-135">隔離交易之目標活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="fecfb-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="fecfb-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fecfb-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="fecfb-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="fecfb-137">xs:string</span></span>|<span data-ttu-id="fecfb-138">隔離交易之目標活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="fecfb-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="fecfb-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fecfb-139">AppDomain</span></span>|<span data-ttu-id="fecfb-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="fecfb-140">xs:string</span></span>|<span data-ttu-id="fecfb-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="fecfb-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
