---
title: 1150 - CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 2adb317521b8659c2419e4c04aabf4cf4499b36f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285105"
---
# <a name="1150---compensationstate"></a><span data-ttu-id="cc57d-102">1150 - CompensationState</span><span class="sxs-lookup"><span data-stu-id="cc57d-102">1150 - CompensationState</span></span>

## <a name="properties"></a><span data-ttu-id="cc57d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="cc57d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc57d-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="cc57d-104">ID</span></span>|<span data-ttu-id="cc57d-105">1150</span><span class="sxs-lookup"><span data-stu-id="cc57d-105">1150</span></span>|  
|<span data-ttu-id="cc57d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="cc57d-106">Keywords</span></span>|<span data-ttu-id="cc57d-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="cc57d-107">WFActivities</span></span>|  
|<span data-ttu-id="cc57d-108">層級</span><span class="sxs-lookup"><span data-stu-id="cc57d-108">Level</span></span>|<span data-ttu-id="cc57d-109">資訊</span><span class="sxs-lookup"><span data-stu-id="cc57d-109">Information</span></span>|  
|<span data-ttu-id="cc57d-110">通路</span><span class="sxs-lookup"><span data-stu-id="cc57d-110">Channel</span></span>|<span data-ttu-id="cc57d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cc57d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cc57d-112">描述</span><span class="sxs-lookup"><span data-stu-id="cc57d-112">Description</span></span>  

 <span data-ttu-id="cc57d-113">表示 CompensableActivity 中的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="cc57d-113">Indicates a change of state in a CompensableActivity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cc57d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="cc57d-114">Message</span></span>  

 <span data-ttu-id="cc57d-115">CompensableActivity '%1' 處於 '%2' 狀態。</span><span class="sxs-lookup"><span data-stu-id="cc57d-115">CompensableActivity '%1' is in the '%2' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cc57d-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cc57d-116">Details</span></span>  
  
|<span data-ttu-id="cc57d-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="cc57d-117">Data Item Name</span></span>|<span data-ttu-id="cc57d-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="cc57d-118">Data Item Type</span></span>|<span data-ttu-id="cc57d-119">描述</span><span class="sxs-lookup"><span data-stu-id="cc57d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cc57d-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="cc57d-120">DisplayName</span></span>|<span data-ttu-id="cc57d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc57d-121">xs:string</span></span>|<span data-ttu-id="cc57d-122">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="cc57d-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="cc57d-123">州</span><span class="sxs-lookup"><span data-stu-id="cc57d-123">State</span></span>|<span data-ttu-id="cc57d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc57d-124">xs:string</span></span>|<span data-ttu-id="cc57d-125">補償狀態。</span><span class="sxs-lookup"><span data-stu-id="cc57d-125">The compensation state.</span></span>|  
|<span data-ttu-id="cc57d-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cc57d-126">AppDomain</span></span>|<span data-ttu-id="cc57d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc57d-127">xs:string</span></span>|<span data-ttu-id="cc57d-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="cc57d-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
