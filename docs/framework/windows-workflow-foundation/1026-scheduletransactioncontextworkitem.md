---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 7ba2ada1fbd5217592b4e4e3cffd813ffbe978ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275241"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="4cbb6-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="4cbb6-102">1026 - ScheduleTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="4cbb6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="4cbb6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4cbb6-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="4cbb6-104">ID</span></span>|<span data-ttu-id="4cbb6-105">1026</span><span class="sxs-lookup"><span data-stu-id="4cbb6-105">1026</span></span>|  
|<span data-ttu-id="4cbb6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="4cbb6-106">Keywords</span></span>|<span data-ttu-id="4cbb6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4cbb6-107">WFRuntime</span></span>|  
|<span data-ttu-id="4cbb6-108">層級</span><span class="sxs-lookup"><span data-stu-id="4cbb6-108">Level</span></span>|<span data-ttu-id="4cbb6-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="4cbb6-109">Verbose</span></span>|  
|<span data-ttu-id="4cbb6-110">通路</span><span class="sxs-lookup"><span data-stu-id="4cbb6-110">Channel</span></span>|<span data-ttu-id="4cbb6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4cbb6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4cbb6-112">描述</span><span class="sxs-lookup"><span data-stu-id="4cbb6-112">Description</span></span>  

 <span data-ttu-id="4cbb6-113">表示已排定 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="4cbb6-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4cbb6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="4cbb6-114">Message</span></span>  

 <span data-ttu-id="4cbb6-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="4cbb6-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4cbb6-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4cbb6-116">Details</span></span>  
  
|<span data-ttu-id="4cbb6-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="4cbb6-117">Data Item Name</span></span>|<span data-ttu-id="4cbb6-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="4cbb6-118">Data Item Type</span></span>|<span data-ttu-id="4cbb6-119">描述</span><span class="sxs-lookup"><span data-stu-id="4cbb6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4cbb6-120">活動</span><span class="sxs-lookup"><span data-stu-id="4cbb6-120">Activity</span></span>|<span data-ttu-id="4cbb6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cbb6-121">xs:string</span></span>|<span data-ttu-id="4cbb6-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="4cbb6-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4cbb6-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4cbb6-123">DisplayName</span></span>|<span data-ttu-id="4cbb6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cbb6-124">xs:string</span></span>|<span data-ttu-id="4cbb6-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4cbb6-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4cbb6-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4cbb6-126">InstanceId</span></span>|<span data-ttu-id="4cbb6-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cbb6-127">xs:string</span></span>|<span data-ttu-id="4cbb6-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="4cbb6-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4cbb6-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4cbb6-129">AppDomain</span></span>|<span data-ttu-id="4cbb6-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cbb6-130">xs:string</span></span>|<span data-ttu-id="4cbb6-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="4cbb6-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
