---
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 28d19742055c51ca94c36ffddf15dced7dfc14cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924432"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="9256b-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="9256b-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9256b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9256b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9256b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="9256b-104">ID</span></span>|<span data-ttu-id="9256b-105">1019</span><span class="sxs-lookup"><span data-stu-id="9256b-105">1019</span></span>|  
|<span data-ttu-id="9256b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9256b-106">Keywords</span></span>|<span data-ttu-id="9256b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9256b-107">WFRuntime</span></span>|  
|<span data-ttu-id="9256b-108">層級</span><span class="sxs-lookup"><span data-stu-id="9256b-108">Level</span></span>|<span data-ttu-id="9256b-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9256b-109">Verbose</span></span>|  
|<span data-ttu-id="9256b-110">通道</span><span class="sxs-lookup"><span data-stu-id="9256b-110">Channel</span></span>|<span data-ttu-id="9256b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9256b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9256b-112">描述</span><span class="sxs-lookup"><span data-stu-id="9256b-112">Description</span></span>  
 <span data-ttu-id="9256b-113">表示 CancelActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="9256b-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9256b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9256b-114">Message</span></span>  
 <span data-ttu-id="9256b-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="9256b-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9256b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9256b-116">Details</span></span>  
  
|<span data-ttu-id="9256b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9256b-117">Data Item Name</span></span>|<span data-ttu-id="9256b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9256b-118">Data Item Type</span></span>|<span data-ttu-id="9256b-119">描述</span><span class="sxs-lookup"><span data-stu-id="9256b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9256b-120">活動</span><span class="sxs-lookup"><span data-stu-id="9256b-120">Activity</span></span>|<span data-ttu-id="9256b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9256b-121">xs:string</span></span>|<span data-ttu-id="9256b-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9256b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9256b-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9256b-123">DisplayName</span></span>|<span data-ttu-id="9256b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9256b-124">xs:string</span></span>|<span data-ttu-id="9256b-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9256b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9256b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9256b-126">InstanceId</span></span>|<span data-ttu-id="9256b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9256b-127">xs:string</span></span>|<span data-ttu-id="9256b-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9256b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9256b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9256b-129">AppDomain</span></span>|<span data-ttu-id="9256b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="9256b-130">xs:string</span></span>|<span data-ttu-id="9256b-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9256b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
