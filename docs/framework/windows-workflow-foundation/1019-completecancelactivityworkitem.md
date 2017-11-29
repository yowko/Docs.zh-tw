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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f8af4486d4659afd4c98016a6f88719271f1a1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="8b034-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="8b034-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8b034-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8b034-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b034-104">ID</span><span class="sxs-lookup"><span data-stu-id="8b034-104">ID</span></span>|<span data-ttu-id="8b034-105">1019</span><span class="sxs-lookup"><span data-stu-id="8b034-105">1019</span></span>|  
|<span data-ttu-id="8b034-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8b034-106">Keywords</span></span>|<span data-ttu-id="8b034-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8b034-107">WFRuntime</span></span>|  
|<span data-ttu-id="8b034-108">層級</span><span class="sxs-lookup"><span data-stu-id="8b034-108">Level</span></span>|<span data-ttu-id="8b034-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="8b034-109">Verbose</span></span>|  
|<span data-ttu-id="8b034-110">通道</span><span class="sxs-lookup"><span data-stu-id="8b034-110">Channel</span></span>|<span data-ttu-id="8b034-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8b034-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8b034-112">描述</span><span class="sxs-lookup"><span data-stu-id="8b034-112">Description</span></span>  
 <span data-ttu-id="8b034-113">表示 CancelActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="8b034-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8b034-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8b034-114">Message</span></span>  
 <span data-ttu-id="8b034-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="8b034-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8b034-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8b034-116">Details</span></span>  
  
|<span data-ttu-id="8b034-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8b034-117">Data Item Name</span></span>|<span data-ttu-id="8b034-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8b034-118">Data Item Type</span></span>|<span data-ttu-id="8b034-119">描述</span><span class="sxs-lookup"><span data-stu-id="8b034-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8b034-120">活動</span><span class="sxs-lookup"><span data-stu-id="8b034-120">Activity</span></span>|<span data-ttu-id="8b034-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b034-121">xs:string</span></span>|<span data-ttu-id="8b034-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8b034-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8b034-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8b034-123">DisplayName</span></span>|<span data-ttu-id="8b034-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b034-124">xs:string</span></span>|<span data-ttu-id="8b034-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8b034-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8b034-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8b034-126">InstanceId</span></span>|<span data-ttu-id="8b034-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b034-127">xs:string</span></span>|<span data-ttu-id="8b034-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="8b034-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8b034-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8b034-129">AppDomain</span></span>|<span data-ttu-id="8b034-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b034-130">xs:string</span></span>|<span data-ttu-id="8b034-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8b034-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
