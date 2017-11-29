---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4de69b1fc2647d7723db8aebb02942938db7478f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="0a695-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="0a695-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0a695-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0a695-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a695-104">ID</span><span class="sxs-lookup"><span data-stu-id="0a695-104">ID</span></span>|<span data-ttu-id="0a695-105">1032</span><span class="sxs-lookup"><span data-stu-id="0a695-105">1032</span></span>|  
|<span data-ttu-id="0a695-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0a695-106">Keywords</span></span>|<span data-ttu-id="0a695-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0a695-107">WFRuntime</span></span>|  
|<span data-ttu-id="0a695-108">層級</span><span class="sxs-lookup"><span data-stu-id="0a695-108">Level</span></span>|<span data-ttu-id="0a695-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0a695-109">Verbose</span></span>|  
|<span data-ttu-id="0a695-110">通道</span><span class="sxs-lookup"><span data-stu-id="0a695-110">Channel</span></span>|<span data-ttu-id="0a695-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0a695-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0a695-112">描述</span><span class="sxs-lookup"><span data-stu-id="0a695-112">Description</span></span>  
 <span data-ttu-id="0a695-113">表示已排定 RuntimeWorkItem。</span><span class="sxs-lookup"><span data-stu-id="0a695-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0a695-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0a695-114">Message</span></span>  
 <span data-ttu-id="0a695-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="0a695-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0a695-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0a695-116">Details</span></span>  
  
|<span data-ttu-id="0a695-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0a695-117">Data Item Name</span></span>|<span data-ttu-id="0a695-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0a695-118">Data Item Type</span></span>|<span data-ttu-id="0a695-119">描述</span><span class="sxs-lookup"><span data-stu-id="0a695-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0a695-120">活動</span><span class="sxs-lookup"><span data-stu-id="0a695-120">Activity</span></span>|<span data-ttu-id="0a695-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a695-121">xs:string</span></span>|<span data-ttu-id="0a695-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0a695-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0a695-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0a695-123">DisplayName</span></span>|<span data-ttu-id="0a695-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a695-124">xs:string</span></span>|<span data-ttu-id="0a695-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0a695-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0a695-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0a695-126">InstanceId</span></span>|<span data-ttu-id="0a695-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a695-127">xs:string</span></span>|<span data-ttu-id="0a695-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="0a695-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0a695-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0a695-129">AppDomain</span></span>|<span data-ttu-id="0a695-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a695-130">xs:string</span></span>|<span data-ttu-id="0a695-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0a695-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
