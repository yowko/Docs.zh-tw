---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924861"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="c3794-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="c3794-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c3794-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c3794-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3794-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c3794-104">ID</span></span>|<span data-ttu-id="c3794-105">1032</span><span class="sxs-lookup"><span data-stu-id="c3794-105">1032</span></span>|  
|<span data-ttu-id="c3794-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c3794-106">Keywords</span></span>|<span data-ttu-id="c3794-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c3794-107">WFRuntime</span></span>|  
|<span data-ttu-id="c3794-108">層級</span><span class="sxs-lookup"><span data-stu-id="c3794-108">Level</span></span>|<span data-ttu-id="c3794-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c3794-109">Verbose</span></span>|  
|<span data-ttu-id="c3794-110">通道</span><span class="sxs-lookup"><span data-stu-id="c3794-110">Channel</span></span>|<span data-ttu-id="c3794-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c3794-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3794-112">描述</span><span class="sxs-lookup"><span data-stu-id="c3794-112">Description</span></span>  
 <span data-ttu-id="c3794-113">表示已排定 RuntimeWorkItem。</span><span class="sxs-lookup"><span data-stu-id="c3794-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3794-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c3794-114">Message</span></span>  
 <span data-ttu-id="c3794-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="c3794-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3794-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c3794-116">Details</span></span>  
  
|<span data-ttu-id="c3794-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c3794-117">Data Item Name</span></span>|<span data-ttu-id="c3794-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c3794-118">Data Item Type</span></span>|<span data-ttu-id="c3794-119">描述</span><span class="sxs-lookup"><span data-stu-id="c3794-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3794-120">活動</span><span class="sxs-lookup"><span data-stu-id="c3794-120">Activity</span></span>|<span data-ttu-id="c3794-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3794-121">xs:string</span></span>|<span data-ttu-id="c3794-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c3794-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c3794-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c3794-123">DisplayName</span></span>|<span data-ttu-id="c3794-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3794-124">xs:string</span></span>|<span data-ttu-id="c3794-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c3794-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c3794-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c3794-126">InstanceId</span></span>|<span data-ttu-id="c3794-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3794-127">xs:string</span></span>|<span data-ttu-id="c3794-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c3794-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c3794-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c3794-129">AppDomain</span></span>|<span data-ttu-id="c3794-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3794-130">xs:string</span></span>|<span data-ttu-id="c3794-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c3794-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
