---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008367"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="f780d-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="f780d-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="f780d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f780d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f780d-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f780d-104">ID</span></span>|<span data-ttu-id="f780d-105">1010</span><span class="sxs-lookup"><span data-stu-id="f780d-105">1010</span></span>|  
|<span data-ttu-id="f780d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f780d-106">Keywords</span></span>|<span data-ttu-id="f780d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f780d-107">WFRuntime</span></span>|  
|<span data-ttu-id="f780d-108">層級</span><span class="sxs-lookup"><span data-stu-id="f780d-108">Level</span></span>|<span data-ttu-id="f780d-109">資訊</span><span class="sxs-lookup"><span data-stu-id="f780d-109">Information</span></span>|  
|<span data-ttu-id="f780d-110">通道</span><span class="sxs-lookup"><span data-stu-id="f780d-110">Channel</span></span>|<span data-ttu-id="f780d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f780d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f780d-112">描述</span><span class="sxs-lookup"><span data-stu-id="f780d-112">Description</span></span>  
 <span data-ttu-id="f780d-113">表示活動已完成執行。</span><span class="sxs-lookup"><span data-stu-id="f780d-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f780d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f780d-114">Message</span></span>  
 <span data-ttu-id="f780d-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已經以 '%4' 狀態完成。</span><span class="sxs-lookup"><span data-stu-id="f780d-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f780d-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f780d-116">Details</span></span>  
  
|<span data-ttu-id="f780d-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f780d-117">Data Item Name</span></span>|<span data-ttu-id="f780d-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f780d-118">Data Item Type</span></span>|<span data-ttu-id="f780d-119">描述</span><span class="sxs-lookup"><span data-stu-id="f780d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f780d-120">活動</span><span class="sxs-lookup"><span data-stu-id="f780d-120">Activity</span></span>|<span data-ttu-id="f780d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f780d-121">xs:string</span></span>|<span data-ttu-id="f780d-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f780d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f780d-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f780d-123">DisplayName</span></span>|<span data-ttu-id="f780d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f780d-124">xs:string</span></span>|<span data-ttu-id="f780d-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f780d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f780d-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f780d-126">InstanceId</span></span>|<span data-ttu-id="f780d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f780d-127">xs:string</span></span>|<span data-ttu-id="f780d-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f780d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f780d-129">狀況</span><span class="sxs-lookup"><span data-stu-id="f780d-129">State</span></span>|<span data-ttu-id="f780d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f780d-130">xs:string</span></span>|<span data-ttu-id="f780d-131">活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="f780d-131">The state of the activity.</span></span>|  
|<span data-ttu-id="f780d-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f780d-132">AppDomain</span></span>|<span data-ttu-id="f780d-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="f780d-133">xs:string</span></span>|<span data-ttu-id="f780d-134">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f780d-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
