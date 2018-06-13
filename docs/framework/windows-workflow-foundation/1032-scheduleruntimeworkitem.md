---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510243"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="1433f-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="1433f-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1433f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1433f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1433f-104">ID</span><span class="sxs-lookup"><span data-stu-id="1433f-104">ID</span></span>|<span data-ttu-id="1433f-105">1032</span><span class="sxs-lookup"><span data-stu-id="1433f-105">1032</span></span>|  
|<span data-ttu-id="1433f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1433f-106">Keywords</span></span>|<span data-ttu-id="1433f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1433f-107">WFRuntime</span></span>|  
|<span data-ttu-id="1433f-108">層級</span><span class="sxs-lookup"><span data-stu-id="1433f-108">Level</span></span>|<span data-ttu-id="1433f-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="1433f-109">Verbose</span></span>|  
|<span data-ttu-id="1433f-110">通道</span><span class="sxs-lookup"><span data-stu-id="1433f-110">Channel</span></span>|<span data-ttu-id="1433f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1433f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1433f-112">描述</span><span class="sxs-lookup"><span data-stu-id="1433f-112">Description</span></span>  
 <span data-ttu-id="1433f-113">表示已排定 RuntimeWorkItem。</span><span class="sxs-lookup"><span data-stu-id="1433f-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1433f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1433f-114">Message</span></span>  
 <span data-ttu-id="1433f-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="1433f-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1433f-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1433f-116">Details</span></span>  
  
|<span data-ttu-id="1433f-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1433f-117">Data Item Name</span></span>|<span data-ttu-id="1433f-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1433f-118">Data Item Type</span></span>|<span data-ttu-id="1433f-119">描述</span><span class="sxs-lookup"><span data-stu-id="1433f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1433f-120">活動</span><span class="sxs-lookup"><span data-stu-id="1433f-120">Activity</span></span>|<span data-ttu-id="1433f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1433f-121">xs:string</span></span>|<span data-ttu-id="1433f-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1433f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1433f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1433f-123">DisplayName</span></span>|<span data-ttu-id="1433f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1433f-124">xs:string</span></span>|<span data-ttu-id="1433f-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1433f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1433f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1433f-126">InstanceId</span></span>|<span data-ttu-id="1433f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1433f-127">xs:string</span></span>|<span data-ttu-id="1433f-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1433f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1433f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1433f-129">AppDomain</span></span>|<span data-ttu-id="1433f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1433f-130">xs:string</span></span>|<span data-ttu-id="1433f-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1433f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
