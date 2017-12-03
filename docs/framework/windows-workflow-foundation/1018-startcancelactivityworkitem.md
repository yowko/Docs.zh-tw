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
ms.openlocfilehash: b64ea860e9881ed31aa0d8e78dec55f329cc6fad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="ef11a-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="ef11a-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ef11a-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ef11a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef11a-104">ID</span><span class="sxs-lookup"><span data-stu-id="ef11a-104">ID</span></span>|<span data-ttu-id="ef11a-105">1018</span><span class="sxs-lookup"><span data-stu-id="ef11a-105">1018</span></span>|  
|<span data-ttu-id="ef11a-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ef11a-106">Keywords</span></span>|<span data-ttu-id="ef11a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ef11a-107">WFRuntime</span></span>|  
|<span data-ttu-id="ef11a-108">層級</span><span class="sxs-lookup"><span data-stu-id="ef11a-108">Level</span></span>|<span data-ttu-id="ef11a-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ef11a-109">Verbose</span></span>|  
|<span data-ttu-id="ef11a-110">通道</span><span class="sxs-lookup"><span data-stu-id="ef11a-110">Channel</span></span>|<span data-ttu-id="ef11a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ef11a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef11a-112">描述</span><span class="sxs-lookup"><span data-stu-id="ef11a-112">Description</span></span>  
 <span data-ttu-id="ef11a-113">表示 CancelActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="ef11a-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef11a-114">訊息</span><span class="sxs-lookup"><span data-stu-id="ef11a-114">Message</span></span>  
 <span data-ttu-id="ef11a-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3'的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="ef11a-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef11a-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef11a-116">Details</span></span>  
  
|<span data-ttu-id="ef11a-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ef11a-117">Data Item Name</span></span>|<span data-ttu-id="ef11a-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ef11a-118">Data Item Type</span></span>|<span data-ttu-id="ef11a-119">描述</span><span class="sxs-lookup"><span data-stu-id="ef11a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef11a-120">活動</span><span class="sxs-lookup"><span data-stu-id="ef11a-120">Activity</span></span>|<span data-ttu-id="ef11a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef11a-121">xs:string</span></span>|<span data-ttu-id="ef11a-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ef11a-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ef11a-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ef11a-123">DisplayName</span></span>|<span data-ttu-id="ef11a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef11a-124">xs:string</span></span>|<span data-ttu-id="ef11a-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="ef11a-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ef11a-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ef11a-126">InstanceId</span></span>|<span data-ttu-id="ef11a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef11a-127">xs:string</span></span>|<span data-ttu-id="ef11a-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="ef11a-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ef11a-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef11a-129">AppDomain</span></span>|<span data-ttu-id="ef11a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef11a-130">xs:string</span></span>|<span data-ttu-id="ef11a-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ef11a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
