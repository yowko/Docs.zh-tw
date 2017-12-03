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
ms.openlocfilehash: 346cb98b1285883a9a85f2c7abb6147f42734395
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="9c10e-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="9c10e-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="9c10e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9c10e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c10e-104">ID</span><span class="sxs-lookup"><span data-stu-id="9c10e-104">ID</span></span>|<span data-ttu-id="9c10e-105">3508</span><span class="sxs-lookup"><span data-stu-id="9c10e-105">3508</span></span>|  
|<span data-ttu-id="9c10e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9c10e-106">Keywords</span></span>|<span data-ttu-id="9c10e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="9c10e-107">WFServices</span></span>|  
|<span data-ttu-id="9c10e-108">層級</span><span class="sxs-lookup"><span data-stu-id="9c10e-108">Level</span></span>|<span data-ttu-id="9c10e-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9c10e-109">Verbose</span></span>|  
|<span data-ttu-id="9c10e-110">通道</span><span class="sxs-lookup"><span data-stu-id="9c10e-110">Channel</span></span>|<span data-ttu-id="9c10e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9c10e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9c10e-112">描述</span><span class="sxs-lookup"><span data-stu-id="9c10e-112">Description</span></span>  
 <span data-ttu-id="9c10e-113">表示在組態檔中找不到 TrackingProfile，或是 ActivityDefinitionId 不符合設定檔。</span><span class="sxs-lookup"><span data-stu-id="9c10e-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9c10e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9c10e-114">Message</span></span>  
 <span data-ttu-id="9c10e-115">找不到 ActivityDefinitionId '%2' 的 TrackingProfile '%1'。</span><span class="sxs-lookup"><span data-stu-id="9c10e-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="9c10e-116">在組態檔中找不到 TrackingProfile，或者 ActivityDefinitionId 不相符。</span><span class="sxs-lookup"><span data-stu-id="9c10e-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9c10e-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9c10e-117">Details</span></span>  
  
|<span data-ttu-id="9c10e-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9c10e-118">Data Item Name</span></span>|<span data-ttu-id="9c10e-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9c10e-119">Data Item Type</span></span>|<span data-ttu-id="9c10e-120">描述</span><span class="sxs-lookup"><span data-stu-id="9c10e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9c10e-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="9c10e-121">TrackingProfile</span></span>|<span data-ttu-id="9c10e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c10e-122">xs:string</span></span>|<span data-ttu-id="9c10e-123">追蹤設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c10e-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="9c10e-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="9c10e-124">ActivityDefinitionId</span></span>|<span data-ttu-id="9c10e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c10e-125">xs:string</span></span>|<span data-ttu-id="9c10e-126">活動定義 ID。</span><span class="sxs-lookup"><span data-stu-id="9c10e-126">The activity definition id.</span></span>|  
|<span data-ttu-id="9c10e-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9c10e-127">AppDomain</span></span>|<span data-ttu-id="9c10e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c10e-128">xs:string</span></span>|<span data-ttu-id="9c10e-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9c10e-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
