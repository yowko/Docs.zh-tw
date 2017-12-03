---
title: 1019 - CompleteCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cf96d665bcd5ff703f54d2f15d1912ad0b9573c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="f7889-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="f7889-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f7889-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f7889-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7889-104">ID</span><span class="sxs-lookup"><span data-stu-id="f7889-104">ID</span></span>|<span data-ttu-id="f7889-105">1019</span><span class="sxs-lookup"><span data-stu-id="f7889-105">1019</span></span>|  
|<span data-ttu-id="f7889-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f7889-106">Keywords</span></span>|<span data-ttu-id="f7889-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f7889-107">WFRuntime</span></span>|  
|<span data-ttu-id="f7889-108">層級</span><span class="sxs-lookup"><span data-stu-id="f7889-108">Level</span></span>|<span data-ttu-id="f7889-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f7889-109">Verbose</span></span>|  
|<span data-ttu-id="f7889-110">通道</span><span class="sxs-lookup"><span data-stu-id="f7889-110">Channel</span></span>|<span data-ttu-id="f7889-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f7889-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f7889-112">描述</span><span class="sxs-lookup"><span data-stu-id="f7889-112">Description</span></span>  
 <span data-ttu-id="f7889-113">表示 CancelActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="f7889-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f7889-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f7889-114">Message</span></span>  
 <span data-ttu-id="f7889-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="f7889-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f7889-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f7889-116">Details</span></span>  
  
|<span data-ttu-id="f7889-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f7889-117">Data Item Name</span></span>|<span data-ttu-id="f7889-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f7889-118">Data Item Type</span></span>|<span data-ttu-id="f7889-119">描述</span><span class="sxs-lookup"><span data-stu-id="f7889-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f7889-120">活動</span><span class="sxs-lookup"><span data-stu-id="f7889-120">Activity</span></span>|<span data-ttu-id="f7889-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f7889-121">xs:string</span></span>|<span data-ttu-id="f7889-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f7889-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f7889-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f7889-123">DisplayName</span></span>|<span data-ttu-id="f7889-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f7889-124">xs:string</span></span>|<span data-ttu-id="f7889-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f7889-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f7889-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f7889-126">InstanceId</span></span>|<span data-ttu-id="f7889-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f7889-127">xs:string</span></span>|<span data-ttu-id="f7889-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f7889-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f7889-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f7889-129">AppDomain</span></span>|<span data-ttu-id="f7889-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f7889-130">xs:string</span></span>|<span data-ttu-id="f7889-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f7889-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
