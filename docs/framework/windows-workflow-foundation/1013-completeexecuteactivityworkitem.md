---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dc72081d2e9b89a9979651bb02b6c06448e30e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="7b507-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7b507-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7b507-103">屬性</span><span class="sxs-lookup"><span data-stu-id="7b507-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b507-104">ID</span><span class="sxs-lookup"><span data-stu-id="7b507-104">ID</span></span>|<span data-ttu-id="7b507-105">1013</span><span class="sxs-lookup"><span data-stu-id="7b507-105">1013</span></span>|  
|<span data-ttu-id="7b507-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7b507-106">Keywords</span></span>|<span data-ttu-id="7b507-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7b507-107">WFRuntime</span></span>|  
|<span data-ttu-id="7b507-108">層級</span><span class="sxs-lookup"><span data-stu-id="7b507-108">Level</span></span>|<span data-ttu-id="7b507-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="7b507-109">Verbose</span></span>|  
|<span data-ttu-id="7b507-110">通道</span><span class="sxs-lookup"><span data-stu-id="7b507-110">Channel</span></span>|<span data-ttu-id="7b507-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7b507-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7b507-112">描述</span><span class="sxs-lookup"><span data-stu-id="7b507-112">Description</span></span>  
 <span data-ttu-id="7b507-113">表示 ExecuteActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="7b507-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="7b507-114">訊息</span><span class="sxs-lookup"><span data-stu-id="7b507-114">Message</span></span>  
 <span data-ttu-id="7b507-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="7b507-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7b507-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b507-116">Details</span></span>  
  
|<span data-ttu-id="7b507-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="7b507-117">Data Item Name</span></span>|<span data-ttu-id="7b507-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="7b507-118">Data Item Type</span></span>|<span data-ttu-id="7b507-119">描述</span><span class="sxs-lookup"><span data-stu-id="7b507-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7b507-120">活動</span><span class="sxs-lookup"><span data-stu-id="7b507-120">Activity</span></span>|<span data-ttu-id="7b507-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b507-121">xs:string</span></span>|<span data-ttu-id="7b507-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7b507-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7b507-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7b507-123">DisplayName</span></span>|<span data-ttu-id="7b507-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b507-124">xs:string</span></span>|<span data-ttu-id="7b507-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7b507-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7b507-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7b507-126">InstanceId</span></span>|<span data-ttu-id="7b507-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b507-127">xs:string</span></span>|<span data-ttu-id="7b507-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="7b507-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7b507-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7b507-129">AppDomain</span></span>|<span data-ttu-id="7b507-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b507-130">xs:string</span></span>|<span data-ttu-id="7b507-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7b507-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
