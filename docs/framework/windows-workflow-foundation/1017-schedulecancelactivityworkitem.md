---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b524f083c49f517c21c77da4f1d1488625a575b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="7b1c3-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7b1c3-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7b1c3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="7b1c3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b1c3-104">ID</span><span class="sxs-lookup"><span data-stu-id="7b1c3-104">ID</span></span>|<span data-ttu-id="7b1c3-105">1017</span><span class="sxs-lookup"><span data-stu-id="7b1c3-105">1017</span></span>|  
|<span data-ttu-id="7b1c3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7b1c3-106">Keywords</span></span>|<span data-ttu-id="7b1c3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7b1c3-107">WFRuntime</span></span>|  
|<span data-ttu-id="7b1c3-108">層級</span><span class="sxs-lookup"><span data-stu-id="7b1c3-108">Level</span></span>|<span data-ttu-id="7b1c3-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="7b1c3-109">Verbose</span></span>|  
|<span data-ttu-id="7b1c3-110">通道</span><span class="sxs-lookup"><span data-stu-id="7b1c3-110">Channel</span></span>|<span data-ttu-id="7b1c3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7b1c3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7b1c3-112">描述</span><span class="sxs-lookup"><span data-stu-id="7b1c3-112">Description</span></span>  
 <span data-ttu-id="7b1c3-113">表示已排定 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="7b1c3-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7b1c3-114">訊息</span><span class="sxs-lookup"><span data-stu-id="7b1c3-114">Message</span></span>  
 <span data-ttu-id="7b1c3-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="7b1c3-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7b1c3-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b1c3-116">Details</span></span>  
  
|<span data-ttu-id="7b1c3-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="7b1c3-117">Data Item Name</span></span>|<span data-ttu-id="7b1c3-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="7b1c3-118">Data Item Type</span></span>|<span data-ttu-id="7b1c3-119">描述</span><span class="sxs-lookup"><span data-stu-id="7b1c3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7b1c3-120">活動</span><span class="sxs-lookup"><span data-stu-id="7b1c3-120">Activity</span></span>|<span data-ttu-id="7b1c3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b1c3-121">xs:string</span></span>|<span data-ttu-id="7b1c3-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7b1c3-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7b1c3-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7b1c3-123">DisplayName</span></span>|<span data-ttu-id="7b1c3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b1c3-124">xs:string</span></span>|<span data-ttu-id="7b1c3-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7b1c3-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7b1c3-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7b1c3-126">InstanceId</span></span>|<span data-ttu-id="7b1c3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b1c3-127">xs:string</span></span>|<span data-ttu-id="7b1c3-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="7b1c3-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7b1c3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7b1c3-129">AppDomain</span></span>|<span data-ttu-id="7b1c3-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b1c3-130">xs:string</span></span>|<span data-ttu-id="7b1c3-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7b1c3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
