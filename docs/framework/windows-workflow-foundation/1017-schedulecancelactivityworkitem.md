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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d348ec18b4d5eff7156d1e9809eb793ac1681d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="2fa66-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="2fa66-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2fa66-103">屬性</span><span class="sxs-lookup"><span data-stu-id="2fa66-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2fa66-104">ID</span><span class="sxs-lookup"><span data-stu-id="2fa66-104">ID</span></span>|<span data-ttu-id="2fa66-105">1017</span><span class="sxs-lookup"><span data-stu-id="2fa66-105">1017</span></span>|  
|<span data-ttu-id="2fa66-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="2fa66-106">Keywords</span></span>|<span data-ttu-id="2fa66-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2fa66-107">WFRuntime</span></span>|  
|<span data-ttu-id="2fa66-108">層級</span><span class="sxs-lookup"><span data-stu-id="2fa66-108">Level</span></span>|<span data-ttu-id="2fa66-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="2fa66-109">Verbose</span></span>|  
|<span data-ttu-id="2fa66-110">通道</span><span class="sxs-lookup"><span data-stu-id="2fa66-110">Channel</span></span>|<span data-ttu-id="2fa66-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2fa66-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2fa66-112">描述</span><span class="sxs-lookup"><span data-stu-id="2fa66-112">Description</span></span>  
 <span data-ttu-id="2fa66-113">表示已排定 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="2fa66-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2fa66-114">訊息</span><span class="sxs-lookup"><span data-stu-id="2fa66-114">Message</span></span>  
 <span data-ttu-id="2fa66-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="2fa66-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2fa66-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2fa66-116">Details</span></span>  
  
|<span data-ttu-id="2fa66-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="2fa66-117">Data Item Name</span></span>|<span data-ttu-id="2fa66-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="2fa66-118">Data Item Type</span></span>|<span data-ttu-id="2fa66-119">描述</span><span class="sxs-lookup"><span data-stu-id="2fa66-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2fa66-120">活動</span><span class="sxs-lookup"><span data-stu-id="2fa66-120">Activity</span></span>|<span data-ttu-id="2fa66-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2fa66-121">xs:string</span></span>|<span data-ttu-id="2fa66-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="2fa66-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2fa66-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2fa66-123">DisplayName</span></span>|<span data-ttu-id="2fa66-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2fa66-124">xs:string</span></span>|<span data-ttu-id="2fa66-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="2fa66-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2fa66-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2fa66-126">InstanceId</span></span>|<span data-ttu-id="2fa66-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2fa66-127">xs:string</span></span>|<span data-ttu-id="2fa66-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="2fa66-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2fa66-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2fa66-129">AppDomain</span></span>|<span data-ttu-id="2fa66-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2fa66-130">xs:string</span></span>|<span data-ttu-id="2fa66-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="2fa66-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
