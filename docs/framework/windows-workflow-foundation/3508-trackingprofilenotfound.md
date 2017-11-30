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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb5636057193fcfb59e5062f6f3833a62b4f3027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="799f9-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="799f9-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="799f9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="799f9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="799f9-104">ID</span><span class="sxs-lookup"><span data-stu-id="799f9-104">ID</span></span>|<span data-ttu-id="799f9-105">3508</span><span class="sxs-lookup"><span data-stu-id="799f9-105">3508</span></span>|  
|<span data-ttu-id="799f9-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="799f9-106">Keywords</span></span>|<span data-ttu-id="799f9-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="799f9-107">WFServices</span></span>|  
|<span data-ttu-id="799f9-108">層級</span><span class="sxs-lookup"><span data-stu-id="799f9-108">Level</span></span>|<span data-ttu-id="799f9-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="799f9-109">Verbose</span></span>|  
|<span data-ttu-id="799f9-110">通道</span><span class="sxs-lookup"><span data-stu-id="799f9-110">Channel</span></span>|<span data-ttu-id="799f9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="799f9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="799f9-112">描述</span><span class="sxs-lookup"><span data-stu-id="799f9-112">Description</span></span>  
 <span data-ttu-id="799f9-113">表示在組態檔中找不到 TrackingProfile，或是 ActivityDefinitionId 不符合設定檔。</span><span class="sxs-lookup"><span data-stu-id="799f9-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="799f9-114">訊息</span><span class="sxs-lookup"><span data-stu-id="799f9-114">Message</span></span>  
 <span data-ttu-id="799f9-115">找不到 ActivityDefinitionId '%2' 的 TrackingProfile '%1'。</span><span class="sxs-lookup"><span data-stu-id="799f9-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="799f9-116">在組態檔中找不到 TrackingProfile，或者 ActivityDefinitionId 不相符。</span><span class="sxs-lookup"><span data-stu-id="799f9-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="799f9-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="799f9-117">Details</span></span>  
  
|<span data-ttu-id="799f9-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="799f9-118">Data Item Name</span></span>|<span data-ttu-id="799f9-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="799f9-119">Data Item Type</span></span>|<span data-ttu-id="799f9-120">描述</span><span class="sxs-lookup"><span data-stu-id="799f9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="799f9-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="799f9-121">TrackingProfile</span></span>|<span data-ttu-id="799f9-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="799f9-122">xs:string</span></span>|<span data-ttu-id="799f9-123">追蹤設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="799f9-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="799f9-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="799f9-124">ActivityDefinitionId</span></span>|<span data-ttu-id="799f9-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="799f9-125">xs:string</span></span>|<span data-ttu-id="799f9-126">活動定義 ID。</span><span class="sxs-lookup"><span data-stu-id="799f9-126">The activity definition id.</span></span>|  
|<span data-ttu-id="799f9-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="799f9-127">AppDomain</span></span>|<span data-ttu-id="799f9-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="799f9-128">xs:string</span></span>|<span data-ttu-id="799f9-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="799f9-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
