---
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 903b497fb3f244fd40c6888829ef71dddd455251
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275475"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="9d99c-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="9d99c-102">1019 - CompleteCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="9d99c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9d99c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d99c-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="9d99c-104">ID</span></span>|<span data-ttu-id="9d99c-105">1019</span><span class="sxs-lookup"><span data-stu-id="9d99c-105">1019</span></span>|  
|<span data-ttu-id="9d99c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9d99c-106">Keywords</span></span>|<span data-ttu-id="9d99c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9d99c-107">WFRuntime</span></span>|  
|<span data-ttu-id="9d99c-108">層級</span><span class="sxs-lookup"><span data-stu-id="9d99c-108">Level</span></span>|<span data-ttu-id="9d99c-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="9d99c-109">Verbose</span></span>|  
|<span data-ttu-id="9d99c-110">通路</span><span class="sxs-lookup"><span data-stu-id="9d99c-110">Channel</span></span>|<span data-ttu-id="9d99c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9d99c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9d99c-112">描述</span><span class="sxs-lookup"><span data-stu-id="9d99c-112">Description</span></span>  

 <span data-ttu-id="9d99c-113">表示 CancelActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="9d99c-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9d99c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9d99c-114">Message</span></span>  

 <span data-ttu-id="9d99c-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="9d99c-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9d99c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9d99c-116">Details</span></span>  
  
|<span data-ttu-id="9d99c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9d99c-117">Data Item Name</span></span>|<span data-ttu-id="9d99c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9d99c-118">Data Item Type</span></span>|<span data-ttu-id="9d99c-119">描述</span><span class="sxs-lookup"><span data-stu-id="9d99c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9d99c-120">活動</span><span class="sxs-lookup"><span data-stu-id="9d99c-120">Activity</span></span>|<span data-ttu-id="9d99c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d99c-121">xs:string</span></span>|<span data-ttu-id="9d99c-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9d99c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9d99c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9d99c-123">DisplayName</span></span>|<span data-ttu-id="9d99c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d99c-124">xs:string</span></span>|<span data-ttu-id="9d99c-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9d99c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9d99c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9d99c-126">InstanceId</span></span>|<span data-ttu-id="9d99c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d99c-127">xs:string</span></span>|<span data-ttu-id="9d99c-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9d99c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9d99c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9d99c-129">AppDomain</span></span>|<span data-ttu-id="9d99c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d99c-130">xs:string</span></span>|<span data-ttu-id="9d99c-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9d99c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
