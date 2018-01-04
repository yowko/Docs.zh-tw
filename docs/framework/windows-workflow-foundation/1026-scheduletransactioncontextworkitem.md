---
title: 1026 - ScheduleTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c99ddf9c5d4a8fa468303fb198abc349ace6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="16a30-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="16a30-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="16a30-103">屬性</span><span class="sxs-lookup"><span data-stu-id="16a30-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16a30-104">ID</span><span class="sxs-lookup"><span data-stu-id="16a30-104">ID</span></span>|<span data-ttu-id="16a30-105">1026</span><span class="sxs-lookup"><span data-stu-id="16a30-105">1026</span></span>|  
|<span data-ttu-id="16a30-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="16a30-106">Keywords</span></span>|<span data-ttu-id="16a30-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="16a30-107">WFRuntime</span></span>|  
|<span data-ttu-id="16a30-108">層級</span><span class="sxs-lookup"><span data-stu-id="16a30-108">Level</span></span>|<span data-ttu-id="16a30-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="16a30-109">Verbose</span></span>|  
|<span data-ttu-id="16a30-110">通道</span><span class="sxs-lookup"><span data-stu-id="16a30-110">Channel</span></span>|<span data-ttu-id="16a30-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="16a30-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16a30-112">描述</span><span class="sxs-lookup"><span data-stu-id="16a30-112">Description</span></span>  
 <span data-ttu-id="16a30-113">表示已排定 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="16a30-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16a30-114">訊息</span><span class="sxs-lookup"><span data-stu-id="16a30-114">Message</span></span>  
 <span data-ttu-id="16a30-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="16a30-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16a30-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="16a30-116">Details</span></span>  
  
|<span data-ttu-id="16a30-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="16a30-117">Data Item Name</span></span>|<span data-ttu-id="16a30-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="16a30-118">Data Item Type</span></span>|<span data-ttu-id="16a30-119">描述</span><span class="sxs-lookup"><span data-stu-id="16a30-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16a30-120">活動</span><span class="sxs-lookup"><span data-stu-id="16a30-120">Activity</span></span>|<span data-ttu-id="16a30-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="16a30-121">xs:string</span></span>|<span data-ttu-id="16a30-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="16a30-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="16a30-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="16a30-123">DisplayName</span></span>|<span data-ttu-id="16a30-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="16a30-124">xs:string</span></span>|<span data-ttu-id="16a30-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="16a30-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="16a30-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="16a30-126">InstanceId</span></span>|<span data-ttu-id="16a30-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="16a30-127">xs:string</span></span>|<span data-ttu-id="16a30-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="16a30-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="16a30-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="16a30-129">AppDomain</span></span>|<span data-ttu-id="16a30-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="16a30-130">xs:string</span></span>|<span data-ttu-id="16a30-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="16a30-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
