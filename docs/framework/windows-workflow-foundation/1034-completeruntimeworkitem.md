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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63ab145b8a0688a7f7bbf7dbcbe8dfe612eab294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="e606c-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="e606c-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e606c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e606c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e606c-104">ID</span><span class="sxs-lookup"><span data-stu-id="e606c-104">ID</span></span>|<span data-ttu-id="e606c-105">1034</span><span class="sxs-lookup"><span data-stu-id="e606c-105">1034</span></span>|  
|<span data-ttu-id="e606c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e606c-106">Keywords</span></span>|<span data-ttu-id="e606c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e606c-107">WFRuntime</span></span>|  
|<span data-ttu-id="e606c-108">層級</span><span class="sxs-lookup"><span data-stu-id="e606c-108">Level</span></span>|<span data-ttu-id="e606c-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="e606c-109">Verbose</span></span>|  
|<span data-ttu-id="e606c-110">通道</span><span class="sxs-lookup"><span data-stu-id="e606c-110">Channel</span></span>|<span data-ttu-id="e606c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e606c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e606c-112">描述</span><span class="sxs-lookup"><span data-stu-id="e606c-112">Description</span></span>  
 <span data-ttu-id="e606c-113">表示 RuntimeWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="e606c-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e606c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e606c-114">Message</span></span>  
 <span data-ttu-id="e606c-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="e606c-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e606c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e606c-116">Details</span></span>  
  
|<span data-ttu-id="e606c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e606c-117">Data Item Name</span></span>|<span data-ttu-id="e606c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e606c-118">Data Item Type</span></span>|<span data-ttu-id="e606c-119">描述</span><span class="sxs-lookup"><span data-stu-id="e606c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e606c-120">活動</span><span class="sxs-lookup"><span data-stu-id="e606c-120">Activity</span></span>|<span data-ttu-id="e606c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e606c-121">xs:string</span></span>|<span data-ttu-id="e606c-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e606c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e606c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e606c-123">DisplayName</span></span>|<span data-ttu-id="e606c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e606c-124">xs:string</span></span>|<span data-ttu-id="e606c-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e606c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e606c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e606c-126">InstanceId</span></span>|<span data-ttu-id="e606c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e606c-127">xs:string</span></span>|<span data-ttu-id="e606c-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="e606c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e606c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e606c-129">AppDomain</span></span>|<span data-ttu-id="e606c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e606c-130">xs:string</span></span>|<span data-ttu-id="e606c-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e606c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
