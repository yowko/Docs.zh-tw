---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec89acb9d83a28ac280db7c3d536bfe63669fa97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="ce16a-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="ce16a-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ce16a-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ce16a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce16a-104">ID</span><span class="sxs-lookup"><span data-stu-id="ce16a-104">ID</span></span>|<span data-ttu-id="ce16a-105">1011</span><span class="sxs-lookup"><span data-stu-id="ce16a-105">1011</span></span>|  
|<span data-ttu-id="ce16a-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ce16a-106">Keywords</span></span>|<span data-ttu-id="ce16a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ce16a-107">WFRuntime</span></span>|  
|<span data-ttu-id="ce16a-108">層級</span><span class="sxs-lookup"><span data-stu-id="ce16a-108">Level</span></span>|<span data-ttu-id="ce16a-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ce16a-109">Verbose</span></span>|  
|<span data-ttu-id="ce16a-110">通道</span><span class="sxs-lookup"><span data-stu-id="ce16a-110">Channel</span></span>|<span data-ttu-id="ce16a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ce16a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce16a-112">描述</span><span class="sxs-lookup"><span data-stu-id="ce16a-112">Description</span></span>  
 <span data-ttu-id="ce16a-113">表示 ExecuteActivityWorkItem 已排程。</span><span class="sxs-lookup"><span data-stu-id="ce16a-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ce16a-114">訊息</span><span class="sxs-lookup"><span data-stu-id="ce16a-114">Message</span></span>  
 <span data-ttu-id="ce16a-115">已經為活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 排程 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="ce16a-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ce16a-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ce16a-116">Details</span></span>  
  
|<span data-ttu-id="ce16a-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ce16a-117">Data Item Name</span></span>|<span data-ttu-id="ce16a-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ce16a-118">Data Item Type</span></span>|<span data-ttu-id="ce16a-119">描述</span><span class="sxs-lookup"><span data-stu-id="ce16a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ce16a-120">活動</span><span class="sxs-lookup"><span data-stu-id="ce16a-120">Activity</span></span>|<span data-ttu-id="ce16a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce16a-121">xs:string</span></span>|<span data-ttu-id="ce16a-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ce16a-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ce16a-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ce16a-123">DisplayName</span></span>|<span data-ttu-id="ce16a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce16a-124">xs:string</span></span>|<span data-ttu-id="ce16a-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="ce16a-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ce16a-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ce16a-126">InstanceId</span></span>|<span data-ttu-id="ce16a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce16a-127">xs:string</span></span>|<span data-ttu-id="ce16a-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="ce16a-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ce16a-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ce16a-129">AppDomain</span></span>|<span data-ttu-id="ce16a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce16a-130">xs:string</span></span>|<span data-ttu-id="ce16a-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ce16a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
