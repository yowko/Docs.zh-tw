---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48161ca9c9268fb52c8b8ab9f3fb6d6ce894efa4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="a0796-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="a0796-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a0796-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a0796-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0796-104">ID</span><span class="sxs-lookup"><span data-stu-id="a0796-104">ID</span></span>|<span data-ttu-id="a0796-105">1034</span><span class="sxs-lookup"><span data-stu-id="a0796-105">1034</span></span>|  
|<span data-ttu-id="a0796-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a0796-106">Keywords</span></span>|<span data-ttu-id="a0796-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a0796-107">WFRuntime</span></span>|  
|<span data-ttu-id="a0796-108">層級</span><span class="sxs-lookup"><span data-stu-id="a0796-108">Level</span></span>|<span data-ttu-id="a0796-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a0796-109">Verbose</span></span>|  
|<span data-ttu-id="a0796-110">通道</span><span class="sxs-lookup"><span data-stu-id="a0796-110">Channel</span></span>|<span data-ttu-id="a0796-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a0796-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a0796-112">描述</span><span class="sxs-lookup"><span data-stu-id="a0796-112">Description</span></span>  
 <span data-ttu-id="a0796-113">表示 RuntimeWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="a0796-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a0796-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a0796-114">Message</span></span>  
 <span data-ttu-id="a0796-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="a0796-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a0796-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0796-116">Details</span></span>  
  
|<span data-ttu-id="a0796-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a0796-117">Data Item Name</span></span>|<span data-ttu-id="a0796-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a0796-118">Data Item Type</span></span>|<span data-ttu-id="a0796-119">描述</span><span class="sxs-lookup"><span data-stu-id="a0796-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a0796-120">活動</span><span class="sxs-lookup"><span data-stu-id="a0796-120">Activity</span></span>|<span data-ttu-id="a0796-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a0796-121">xs:string</span></span>|<span data-ttu-id="a0796-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a0796-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a0796-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a0796-123">DisplayName</span></span>|<span data-ttu-id="a0796-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a0796-124">xs:string</span></span>|<span data-ttu-id="a0796-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a0796-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a0796-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a0796-126">InstanceId</span></span>|<span data-ttu-id="a0796-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a0796-127">xs:string</span></span>|<span data-ttu-id="a0796-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="a0796-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a0796-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a0796-129">AppDomain</span></span>|<span data-ttu-id="a0796-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a0796-130">xs:string</span></span>|<span data-ttu-id="a0796-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a0796-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
