---
title: 1033 - StartRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5502c3d2cb1e9ec9454ed43c3a468a27307d07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="c4981-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="c4981-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c4981-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c4981-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4981-104">ID</span><span class="sxs-lookup"><span data-stu-id="c4981-104">ID</span></span>|<span data-ttu-id="c4981-105">1033</span><span class="sxs-lookup"><span data-stu-id="c4981-105">1033</span></span>|  
|<span data-ttu-id="c4981-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c4981-106">Keywords</span></span>|<span data-ttu-id="c4981-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c4981-107">WFRuntime</span></span>|  
|<span data-ttu-id="c4981-108">層級</span><span class="sxs-lookup"><span data-stu-id="c4981-108">Level</span></span>|<span data-ttu-id="c4981-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c4981-109">Verbose</span></span>|  
|<span data-ttu-id="c4981-110">通道</span><span class="sxs-lookup"><span data-stu-id="c4981-110">Channel</span></span>|<span data-ttu-id="c4981-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c4981-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c4981-112">描述</span><span class="sxs-lookup"><span data-stu-id="c4981-112">Description</span></span>  
 <span data-ttu-id="c4981-113">表示 RuntimeWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="c4981-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c4981-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c4981-114">Message</span></span>  
 <span data-ttu-id="c4981-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="c4981-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c4981-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c4981-116">Details</span></span>  
  
|<span data-ttu-id="c4981-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c4981-117">Data Item Name</span></span>|<span data-ttu-id="c4981-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c4981-118">Data Item Type</span></span>|<span data-ttu-id="c4981-119">描述</span><span class="sxs-lookup"><span data-stu-id="c4981-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c4981-120">活動</span><span class="sxs-lookup"><span data-stu-id="c4981-120">Activity</span></span>|<span data-ttu-id="c4981-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4981-121">xs:string</span></span>|<span data-ttu-id="c4981-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c4981-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c4981-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c4981-123">DisplayName</span></span>|<span data-ttu-id="c4981-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4981-124">xs:string</span></span>|<span data-ttu-id="c4981-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c4981-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c4981-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c4981-126">InstanceId</span></span>|<span data-ttu-id="c4981-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4981-127">xs:string</span></span>|<span data-ttu-id="c4981-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c4981-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c4981-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c4981-129">AppDomain</span></span>|<span data-ttu-id="c4981-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4981-130">xs:string</span></span>|<span data-ttu-id="c4981-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c4981-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
