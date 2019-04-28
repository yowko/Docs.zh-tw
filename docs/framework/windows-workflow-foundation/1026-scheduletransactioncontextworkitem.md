---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924627"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="afb57-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="afb57-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="afb57-103">屬性</span><span class="sxs-lookup"><span data-stu-id="afb57-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="afb57-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="afb57-104">ID</span></span>|<span data-ttu-id="afb57-105">1026</span><span class="sxs-lookup"><span data-stu-id="afb57-105">1026</span></span>|  
|<span data-ttu-id="afb57-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="afb57-106">Keywords</span></span>|<span data-ttu-id="afb57-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="afb57-107">WFRuntime</span></span>|  
|<span data-ttu-id="afb57-108">層級</span><span class="sxs-lookup"><span data-stu-id="afb57-108">Level</span></span>|<span data-ttu-id="afb57-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="afb57-109">Verbose</span></span>|  
|<span data-ttu-id="afb57-110">通道</span><span class="sxs-lookup"><span data-stu-id="afb57-110">Channel</span></span>|<span data-ttu-id="afb57-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="afb57-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="afb57-112">描述</span><span class="sxs-lookup"><span data-stu-id="afb57-112">Description</span></span>  
 <span data-ttu-id="afb57-113">表示已排定 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="afb57-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="afb57-114">訊息</span><span class="sxs-lookup"><span data-stu-id="afb57-114">Message</span></span>  
 <span data-ttu-id="afb57-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="afb57-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="afb57-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="afb57-116">Details</span></span>  
  
|<span data-ttu-id="afb57-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="afb57-117">Data Item Name</span></span>|<span data-ttu-id="afb57-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="afb57-118">Data Item Type</span></span>|<span data-ttu-id="afb57-119">描述</span><span class="sxs-lookup"><span data-stu-id="afb57-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="afb57-120">活動</span><span class="sxs-lookup"><span data-stu-id="afb57-120">Activity</span></span>|<span data-ttu-id="afb57-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="afb57-121">xs:string</span></span>|<span data-ttu-id="afb57-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="afb57-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="afb57-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="afb57-123">DisplayName</span></span>|<span data-ttu-id="afb57-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="afb57-124">xs:string</span></span>|<span data-ttu-id="afb57-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="afb57-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="afb57-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="afb57-126">InstanceId</span></span>|<span data-ttu-id="afb57-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="afb57-127">xs:string</span></span>|<span data-ttu-id="afb57-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="afb57-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="afb57-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="afb57-129">AppDomain</span></span>|<span data-ttu-id="afb57-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="afb57-130">xs:string</span></span>|<span data-ttu-id="afb57-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="afb57-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
