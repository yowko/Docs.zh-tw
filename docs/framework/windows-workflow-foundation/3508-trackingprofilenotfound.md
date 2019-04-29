---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755567"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="c7b0d-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="c7b0d-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="c7b0d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c7b0d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7b0d-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c7b0d-104">ID</span></span>|<span data-ttu-id="c7b0d-105">3508</span><span class="sxs-lookup"><span data-stu-id="c7b0d-105">3508</span></span>|  
|<span data-ttu-id="c7b0d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c7b0d-106">Keywords</span></span>|<span data-ttu-id="c7b0d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="c7b0d-107">WFServices</span></span>|  
|<span data-ttu-id="c7b0d-108">層級</span><span class="sxs-lookup"><span data-stu-id="c7b0d-108">Level</span></span>|<span data-ttu-id="c7b0d-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c7b0d-109">Verbose</span></span>|  
|<span data-ttu-id="c7b0d-110">通道</span><span class="sxs-lookup"><span data-stu-id="c7b0d-110">Channel</span></span>|<span data-ttu-id="c7b0d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c7b0d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7b0d-112">描述</span><span class="sxs-lookup"><span data-stu-id="c7b0d-112">Description</span></span>  
 <span data-ttu-id="c7b0d-113">表示在組態檔中找不到 TrackingProfile，或是 ActivityDefinitionId 不符合設定檔。</span><span class="sxs-lookup"><span data-stu-id="c7b0d-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7b0d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c7b0d-114">Message</span></span>  
 <span data-ttu-id="c7b0d-115">找不到 ActivityDefinitionId '%2' 的 TrackingProfile '%1'。</span><span class="sxs-lookup"><span data-stu-id="c7b0d-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="c7b0d-116">在組態檔中找不到 TrackingProfile，或者 ActivityDefinitionId 不相符。</span><span class="sxs-lookup"><span data-stu-id="c7b0d-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7b0d-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7b0d-117">Details</span></span>  
  
|<span data-ttu-id="c7b0d-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c7b0d-118">Data Item Name</span></span>|<span data-ttu-id="c7b0d-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c7b0d-119">Data Item Type</span></span>|<span data-ttu-id="c7b0d-120">描述</span><span class="sxs-lookup"><span data-stu-id="c7b0d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7b0d-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="c7b0d-121">TrackingProfile</span></span>|<span data-ttu-id="c7b0d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b0d-122">xs:string</span></span>|<span data-ttu-id="c7b0d-123">追蹤設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7b0d-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="c7b0d-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="c7b0d-124">ActivityDefinitionId</span></span>|<span data-ttu-id="c7b0d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b0d-125">xs:string</span></span>|<span data-ttu-id="c7b0d-126">活動定義 ID。</span><span class="sxs-lookup"><span data-stu-id="c7b0d-126">The activity definition id.</span></span>|  
|<span data-ttu-id="c7b0d-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c7b0d-127">AppDomain</span></span>|<span data-ttu-id="c7b0d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b0d-128">xs:string</span></span>|<span data-ttu-id="c7b0d-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c7b0d-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
