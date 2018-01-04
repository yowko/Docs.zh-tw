---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="67c41-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="67c41-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="67c41-103">屬性</span><span class="sxs-lookup"><span data-stu-id="67c41-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67c41-104">ID</span><span class="sxs-lookup"><span data-stu-id="67c41-104">ID</span></span>|<span data-ttu-id="67c41-105">3508</span><span class="sxs-lookup"><span data-stu-id="67c41-105">3508</span></span>|  
|<span data-ttu-id="67c41-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="67c41-106">Keywords</span></span>|<span data-ttu-id="67c41-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="67c41-107">WFServices</span></span>|  
|<span data-ttu-id="67c41-108">層級</span><span class="sxs-lookup"><span data-stu-id="67c41-108">Level</span></span>|<span data-ttu-id="67c41-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="67c41-109">Verbose</span></span>|  
|<span data-ttu-id="67c41-110">通道</span><span class="sxs-lookup"><span data-stu-id="67c41-110">Channel</span></span>|<span data-ttu-id="67c41-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="67c41-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="67c41-112">描述</span><span class="sxs-lookup"><span data-stu-id="67c41-112">Description</span></span>  
 <span data-ttu-id="67c41-113">表示在組態檔中找不到 TrackingProfile，或是 ActivityDefinitionId 不符合設定檔。</span><span class="sxs-lookup"><span data-stu-id="67c41-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="67c41-114">訊息</span><span class="sxs-lookup"><span data-stu-id="67c41-114">Message</span></span>  
 <span data-ttu-id="67c41-115">找不到 ActivityDefinitionId '%2' 的 TrackingProfile '%1'。</span><span class="sxs-lookup"><span data-stu-id="67c41-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="67c41-116">在組態檔中找不到 TrackingProfile，或者 ActivityDefinitionId 不相符。</span><span class="sxs-lookup"><span data-stu-id="67c41-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="67c41-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="67c41-117">Details</span></span>  
  
|<span data-ttu-id="67c41-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="67c41-118">Data Item Name</span></span>|<span data-ttu-id="67c41-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="67c41-119">Data Item Type</span></span>|<span data-ttu-id="67c41-120">描述</span><span class="sxs-lookup"><span data-stu-id="67c41-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="67c41-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="67c41-121">TrackingProfile</span></span>|<span data-ttu-id="67c41-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="67c41-122">xs:string</span></span>|<span data-ttu-id="67c41-123">追蹤設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="67c41-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="67c41-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="67c41-124">ActivityDefinitionId</span></span>|<span data-ttu-id="67c41-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="67c41-125">xs:string</span></span>|<span data-ttu-id="67c41-126">活動定義 ID。</span><span class="sxs-lookup"><span data-stu-id="67c41-126">The activity definition id.</span></span>|  
|<span data-ttu-id="67c41-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="67c41-127">AppDomain</span></span>|<span data-ttu-id="67c41-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="67c41-128">xs:string</span></span>|<span data-ttu-id="67c41-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="67c41-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
