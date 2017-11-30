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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0de8e45a592cae49060f976b28a7a7bcf8781265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="87d7d-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="87d7d-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="87d7d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="87d7d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87d7d-104">ID</span><span class="sxs-lookup"><span data-stu-id="87d7d-104">ID</span></span>|<span data-ttu-id="87d7d-105">1033</span><span class="sxs-lookup"><span data-stu-id="87d7d-105">1033</span></span>|  
|<span data-ttu-id="87d7d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="87d7d-106">Keywords</span></span>|<span data-ttu-id="87d7d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="87d7d-107">WFRuntime</span></span>|  
|<span data-ttu-id="87d7d-108">層級</span><span class="sxs-lookup"><span data-stu-id="87d7d-108">Level</span></span>|<span data-ttu-id="87d7d-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="87d7d-109">Verbose</span></span>|  
|<span data-ttu-id="87d7d-110">通道</span><span class="sxs-lookup"><span data-stu-id="87d7d-110">Channel</span></span>|<span data-ttu-id="87d7d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="87d7d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="87d7d-112">描述</span><span class="sxs-lookup"><span data-stu-id="87d7d-112">Description</span></span>  
 <span data-ttu-id="87d7d-113">表示 RuntimeWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="87d7d-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="87d7d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="87d7d-114">Message</span></span>  
 <span data-ttu-id="87d7d-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="87d7d-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="87d7d-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="87d7d-116">Details</span></span>  
  
|<span data-ttu-id="87d7d-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="87d7d-117">Data Item Name</span></span>|<span data-ttu-id="87d7d-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="87d7d-118">Data Item Type</span></span>|<span data-ttu-id="87d7d-119">描述</span><span class="sxs-lookup"><span data-stu-id="87d7d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="87d7d-120">活動</span><span class="sxs-lookup"><span data-stu-id="87d7d-120">Activity</span></span>|<span data-ttu-id="87d7d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="87d7d-121">xs:string</span></span>|<span data-ttu-id="87d7d-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="87d7d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="87d7d-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="87d7d-123">DisplayName</span></span>|<span data-ttu-id="87d7d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="87d7d-124">xs:string</span></span>|<span data-ttu-id="87d7d-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="87d7d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="87d7d-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="87d7d-126">InstanceId</span></span>|<span data-ttu-id="87d7d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="87d7d-127">xs:string</span></span>|<span data-ttu-id="87d7d-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="87d7d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="87d7d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="87d7d-129">AppDomain</span></span>|<span data-ttu-id="87d7d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="87d7d-130">xs:string</span></span>|<span data-ttu-id="87d7d-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="87d7d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
