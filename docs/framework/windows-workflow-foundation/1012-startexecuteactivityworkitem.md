---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a3b03e8ac24bc1652b88b71e8c25862a07c194f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="c3cb2-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="c3cb2-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c3cb2-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c3cb2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3cb2-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3cb2-104">ID</span></span>|<span data-ttu-id="c3cb2-105">1012</span><span class="sxs-lookup"><span data-stu-id="c3cb2-105">1012</span></span>|  
|<span data-ttu-id="c3cb2-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c3cb2-106">Keywords</span></span>|<span data-ttu-id="c3cb2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c3cb2-107">WFRuntime</span></span>|  
|<span data-ttu-id="c3cb2-108">層級</span><span class="sxs-lookup"><span data-stu-id="c3cb2-108">Level</span></span>|<span data-ttu-id="c3cb2-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c3cb2-109">Verbose</span></span>|  
|<span data-ttu-id="c3cb2-110">通道</span><span class="sxs-lookup"><span data-stu-id="c3cb2-110">Channel</span></span>|<span data-ttu-id="c3cb2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c3cb2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3cb2-112">描述</span><span class="sxs-lookup"><span data-stu-id="c3cb2-112">Description</span></span>  
 <span data-ttu-id="c3cb2-113">表示 ExecuteActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="c3cb2-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3cb2-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c3cb2-114">Message</span></span>  
 <span data-ttu-id="c3cb2-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="c3cb2-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3cb2-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c3cb2-116">Details</span></span>  
  
|<span data-ttu-id="c3cb2-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c3cb2-117">Data Item Name</span></span>|<span data-ttu-id="c3cb2-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c3cb2-118">Data Item Type</span></span>|<span data-ttu-id="c3cb2-119">描述</span><span class="sxs-lookup"><span data-stu-id="c3cb2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3cb2-120">活動</span><span class="sxs-lookup"><span data-stu-id="c3cb2-120">Activity</span></span>|<span data-ttu-id="c3cb2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3cb2-121">xs:string</span></span>|<span data-ttu-id="c3cb2-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c3cb2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c3cb2-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c3cb2-123">DisplayName</span></span>|<span data-ttu-id="c3cb2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3cb2-124">xs:string</span></span>|<span data-ttu-id="c3cb2-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c3cb2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c3cb2-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c3cb2-126">InstanceId</span></span>|<span data-ttu-id="c3cb2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3cb2-127">xs:string</span></span>|<span data-ttu-id="c3cb2-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c3cb2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c3cb2-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c3cb2-129">AppDomain</span></span>|<span data-ttu-id="c3cb2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3cb2-130">xs:string</span></span>|<span data-ttu-id="c3cb2-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c3cb2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
