---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: 654f961088c371ab53e4a81f40e3c63335efb1a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239584"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="0ce12-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="0ce12-102">1013 - CompleteExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="0ce12-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0ce12-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0ce12-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="0ce12-104">ID</span></span>|<span data-ttu-id="0ce12-105">1013</span><span class="sxs-lookup"><span data-stu-id="0ce12-105">1013</span></span>|  
|<span data-ttu-id="0ce12-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0ce12-106">Keywords</span></span>|<span data-ttu-id="0ce12-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0ce12-107">WFRuntime</span></span>|  
|<span data-ttu-id="0ce12-108">層級</span><span class="sxs-lookup"><span data-stu-id="0ce12-108">Level</span></span>|<span data-ttu-id="0ce12-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="0ce12-109">Verbose</span></span>|  
|<span data-ttu-id="0ce12-110">通路</span><span class="sxs-lookup"><span data-stu-id="0ce12-110">Channel</span></span>|<span data-ttu-id="0ce12-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0ce12-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0ce12-112">描述</span><span class="sxs-lookup"><span data-stu-id="0ce12-112">Description</span></span>  

 <span data-ttu-id="0ce12-113">表示 ExecuteActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="0ce12-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="0ce12-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0ce12-114">Message</span></span>  

 <span data-ttu-id="0ce12-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="0ce12-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0ce12-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0ce12-116">Details</span></span>  
  
|<span data-ttu-id="0ce12-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0ce12-117">Data Item Name</span></span>|<span data-ttu-id="0ce12-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0ce12-118">Data Item Type</span></span>|<span data-ttu-id="0ce12-119">描述</span><span class="sxs-lookup"><span data-stu-id="0ce12-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0ce12-120">活動</span><span class="sxs-lookup"><span data-stu-id="0ce12-120">Activity</span></span>|<span data-ttu-id="0ce12-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ce12-121">xs:string</span></span>|<span data-ttu-id="0ce12-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce12-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0ce12-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0ce12-123">DisplayName</span></span>|<span data-ttu-id="0ce12-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ce12-124">xs:string</span></span>|<span data-ttu-id="0ce12-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce12-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0ce12-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0ce12-126">InstanceId</span></span>|<span data-ttu-id="0ce12-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ce12-127">xs:string</span></span>|<span data-ttu-id="0ce12-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="0ce12-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0ce12-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0ce12-129">AppDomain</span></span>|<span data-ttu-id="0ce12-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ce12-130">xs:string</span></span>|<span data-ttu-id="0ce12-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0ce12-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
