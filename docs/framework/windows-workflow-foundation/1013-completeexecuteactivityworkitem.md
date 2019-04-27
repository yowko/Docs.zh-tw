---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925186"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="438b5-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="438b5-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="438b5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="438b5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="438b5-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="438b5-104">ID</span></span>|<span data-ttu-id="438b5-105">1013</span><span class="sxs-lookup"><span data-stu-id="438b5-105">1013</span></span>|  
|<span data-ttu-id="438b5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="438b5-106">Keywords</span></span>|<span data-ttu-id="438b5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="438b5-107">WFRuntime</span></span>|  
|<span data-ttu-id="438b5-108">層級</span><span class="sxs-lookup"><span data-stu-id="438b5-108">Level</span></span>|<span data-ttu-id="438b5-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="438b5-109">Verbose</span></span>|  
|<span data-ttu-id="438b5-110">通道</span><span class="sxs-lookup"><span data-stu-id="438b5-110">Channel</span></span>|<span data-ttu-id="438b5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="438b5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="438b5-112">描述</span><span class="sxs-lookup"><span data-stu-id="438b5-112">Description</span></span>  
 <span data-ttu-id="438b5-113">表示 ExecuteActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="438b5-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="438b5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="438b5-114">Message</span></span>  
 <span data-ttu-id="438b5-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="438b5-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="438b5-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="438b5-116">Details</span></span>  
  
|<span data-ttu-id="438b5-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="438b5-117">Data Item Name</span></span>|<span data-ttu-id="438b5-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="438b5-118">Data Item Type</span></span>|<span data-ttu-id="438b5-119">描述</span><span class="sxs-lookup"><span data-stu-id="438b5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="438b5-120">活動</span><span class="sxs-lookup"><span data-stu-id="438b5-120">Activity</span></span>|<span data-ttu-id="438b5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="438b5-121">xs:string</span></span>|<span data-ttu-id="438b5-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="438b5-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="438b5-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="438b5-123">DisplayName</span></span>|<span data-ttu-id="438b5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="438b5-124">xs:string</span></span>|<span data-ttu-id="438b5-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="438b5-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="438b5-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="438b5-126">InstanceId</span></span>|<span data-ttu-id="438b5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="438b5-127">xs:string</span></span>|<span data-ttu-id="438b5-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="438b5-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="438b5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="438b5-129">AppDomain</span></span>|<span data-ttu-id="438b5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="438b5-130">xs:string</span></span>|<span data-ttu-id="438b5-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="438b5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
