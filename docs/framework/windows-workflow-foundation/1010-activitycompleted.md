---
title: 1010 - ActivityCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1378ddd1550db614c9eddc44f79b19ff94ed585c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="33d70-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="33d70-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="33d70-103">屬性</span><span class="sxs-lookup"><span data-stu-id="33d70-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33d70-104">ID</span><span class="sxs-lookup"><span data-stu-id="33d70-104">ID</span></span>|<span data-ttu-id="33d70-105">1010</span><span class="sxs-lookup"><span data-stu-id="33d70-105">1010</span></span>|  
|<span data-ttu-id="33d70-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="33d70-106">Keywords</span></span>|<span data-ttu-id="33d70-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="33d70-107">WFRuntime</span></span>|  
|<span data-ttu-id="33d70-108">層級</span><span class="sxs-lookup"><span data-stu-id="33d70-108">Level</span></span>|<span data-ttu-id="33d70-109">資訊</span><span class="sxs-lookup"><span data-stu-id="33d70-109">Information</span></span>|  
|<span data-ttu-id="33d70-110">通道</span><span class="sxs-lookup"><span data-stu-id="33d70-110">Channel</span></span>|<span data-ttu-id="33d70-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="33d70-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="33d70-112">描述</span><span class="sxs-lookup"><span data-stu-id="33d70-112">Description</span></span>  
 <span data-ttu-id="33d70-113">表示活動已完成執行。</span><span class="sxs-lookup"><span data-stu-id="33d70-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="33d70-114">訊息</span><span class="sxs-lookup"><span data-stu-id="33d70-114">Message</span></span>  
 <span data-ttu-id="33d70-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已經以 '%4' 狀態完成。</span><span class="sxs-lookup"><span data-stu-id="33d70-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="33d70-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="33d70-116">Details</span></span>  
  
|<span data-ttu-id="33d70-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="33d70-117">Data Item Name</span></span>|<span data-ttu-id="33d70-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="33d70-118">Data Item Type</span></span>|<span data-ttu-id="33d70-119">描述</span><span class="sxs-lookup"><span data-stu-id="33d70-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="33d70-120">活動</span><span class="sxs-lookup"><span data-stu-id="33d70-120">Activity</span></span>|<span data-ttu-id="33d70-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="33d70-121">xs:string</span></span>|<span data-ttu-id="33d70-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="33d70-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="33d70-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="33d70-123">DisplayName</span></span>|<span data-ttu-id="33d70-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="33d70-124">xs:string</span></span>|<span data-ttu-id="33d70-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="33d70-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="33d70-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="33d70-126">InstanceId</span></span>|<span data-ttu-id="33d70-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="33d70-127">xs:string</span></span>|<span data-ttu-id="33d70-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="33d70-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="33d70-129">狀態</span><span class="sxs-lookup"><span data-stu-id="33d70-129">State</span></span>|<span data-ttu-id="33d70-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="33d70-130">xs:string</span></span>|<span data-ttu-id="33d70-131">活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="33d70-131">The state of the activity.</span></span>|  
|<span data-ttu-id="33d70-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="33d70-132">AppDomain</span></span>|<span data-ttu-id="33d70-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="33d70-133">xs:string</span></span>|<span data-ttu-id="33d70-134">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="33d70-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
