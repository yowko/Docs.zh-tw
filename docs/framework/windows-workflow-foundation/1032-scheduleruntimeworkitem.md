---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: da35201f2b3e3bc07e0b9139b0584ce37011e168
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294309"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="241cc-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="241cc-102">1032 - ScheduleRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="241cc-103">屬性</span><span class="sxs-lookup"><span data-stu-id="241cc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="241cc-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="241cc-104">ID</span></span>|<span data-ttu-id="241cc-105">1032</span><span class="sxs-lookup"><span data-stu-id="241cc-105">1032</span></span>|  
|<span data-ttu-id="241cc-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="241cc-106">Keywords</span></span>|<span data-ttu-id="241cc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="241cc-107">WFRuntime</span></span>|  
|<span data-ttu-id="241cc-108">層級</span><span class="sxs-lookup"><span data-stu-id="241cc-108">Level</span></span>|<span data-ttu-id="241cc-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="241cc-109">Verbose</span></span>|  
|<span data-ttu-id="241cc-110">通路</span><span class="sxs-lookup"><span data-stu-id="241cc-110">Channel</span></span>|<span data-ttu-id="241cc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="241cc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="241cc-112">描述</span><span class="sxs-lookup"><span data-stu-id="241cc-112">Description</span></span>  

 <span data-ttu-id="241cc-113">表示已排定 RuntimeWorkItem。</span><span class="sxs-lookup"><span data-stu-id="241cc-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="241cc-114">訊息</span><span class="sxs-lookup"><span data-stu-id="241cc-114">Message</span></span>  

 <span data-ttu-id="241cc-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="241cc-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="241cc-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="241cc-116">Details</span></span>  
  
|<span data-ttu-id="241cc-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="241cc-117">Data Item Name</span></span>|<span data-ttu-id="241cc-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="241cc-118">Data Item Type</span></span>|<span data-ttu-id="241cc-119">描述</span><span class="sxs-lookup"><span data-stu-id="241cc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="241cc-120">活動</span><span class="sxs-lookup"><span data-stu-id="241cc-120">Activity</span></span>|<span data-ttu-id="241cc-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="241cc-121">xs:string</span></span>|<span data-ttu-id="241cc-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="241cc-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="241cc-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="241cc-123">DisplayName</span></span>|<span data-ttu-id="241cc-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="241cc-124">xs:string</span></span>|<span data-ttu-id="241cc-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="241cc-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="241cc-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="241cc-126">InstanceId</span></span>|<span data-ttu-id="241cc-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="241cc-127">xs:string</span></span>|<span data-ttu-id="241cc-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="241cc-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="241cc-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="241cc-129">AppDomain</span></span>|<span data-ttu-id="241cc-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="241cc-130">xs:string</span></span>|<span data-ttu-id="241cc-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="241cc-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
