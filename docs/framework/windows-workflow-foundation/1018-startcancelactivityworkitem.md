---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d64d18474ff867ee5679e07c18a288f07185f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="4c793-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4c793-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4c793-103">屬性</span><span class="sxs-lookup"><span data-stu-id="4c793-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c793-104">ID</span><span class="sxs-lookup"><span data-stu-id="4c793-104">ID</span></span>|<span data-ttu-id="4c793-105">1018</span><span class="sxs-lookup"><span data-stu-id="4c793-105">1018</span></span>|  
|<span data-ttu-id="4c793-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="4c793-106">Keywords</span></span>|<span data-ttu-id="4c793-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4c793-107">WFRuntime</span></span>|  
|<span data-ttu-id="4c793-108">層級</span><span class="sxs-lookup"><span data-stu-id="4c793-108">Level</span></span>|<span data-ttu-id="4c793-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="4c793-109">Verbose</span></span>|  
|<span data-ttu-id="4c793-110">通道</span><span class="sxs-lookup"><span data-stu-id="4c793-110">Channel</span></span>|<span data-ttu-id="4c793-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4c793-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4c793-112">描述</span><span class="sxs-lookup"><span data-stu-id="4c793-112">Description</span></span>  
 <span data-ttu-id="4c793-113">表示 CancelActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="4c793-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4c793-114">訊息</span><span class="sxs-lookup"><span data-stu-id="4c793-114">Message</span></span>  
 <span data-ttu-id="4c793-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3'的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="4c793-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4c793-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4c793-116">Details</span></span>  
  
|<span data-ttu-id="4c793-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="4c793-117">Data Item Name</span></span>|<span data-ttu-id="4c793-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="4c793-118">Data Item Type</span></span>|<span data-ttu-id="4c793-119">描述</span><span class="sxs-lookup"><span data-stu-id="4c793-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4c793-120">活動</span><span class="sxs-lookup"><span data-stu-id="4c793-120">Activity</span></span>|<span data-ttu-id="4c793-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c793-121">xs:string</span></span>|<span data-ttu-id="4c793-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="4c793-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4c793-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4c793-123">DisplayName</span></span>|<span data-ttu-id="4c793-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c793-124">xs:string</span></span>|<span data-ttu-id="4c793-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4c793-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4c793-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4c793-126">InstanceId</span></span>|<span data-ttu-id="4c793-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c793-127">xs:string</span></span>|<span data-ttu-id="4c793-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="4c793-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4c793-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4c793-129">AppDomain</span></span>|<span data-ttu-id="4c793-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c793-130">xs:string</span></span>|<span data-ttu-id="4c793-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="4c793-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
