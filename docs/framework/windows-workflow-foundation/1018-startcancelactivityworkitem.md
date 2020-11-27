---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: c1558e19b0de2dc5d22d4356b0f80c35e5b4fbc1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275501"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="a9b30-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="a9b30-102">1018 - StartCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a9b30-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a9b30-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9b30-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="a9b30-104">ID</span></span>|<span data-ttu-id="a9b30-105">1018</span><span class="sxs-lookup"><span data-stu-id="a9b30-105">1018</span></span>|  
|<span data-ttu-id="a9b30-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a9b30-106">Keywords</span></span>|<span data-ttu-id="a9b30-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a9b30-107">WFRuntime</span></span>|  
|<span data-ttu-id="a9b30-108">層級</span><span class="sxs-lookup"><span data-stu-id="a9b30-108">Level</span></span>|<span data-ttu-id="a9b30-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="a9b30-109">Verbose</span></span>|  
|<span data-ttu-id="a9b30-110">通路</span><span class="sxs-lookup"><span data-stu-id="a9b30-110">Channel</span></span>|<span data-ttu-id="a9b30-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a9b30-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a9b30-112">描述</span><span class="sxs-lookup"><span data-stu-id="a9b30-112">Description</span></span>  

 <span data-ttu-id="a9b30-113">表示 CancelActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="a9b30-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a9b30-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a9b30-114">Message</span></span>  

 <span data-ttu-id="a9b30-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3'的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="a9b30-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a9b30-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a9b30-116">Details</span></span>  
  
|<span data-ttu-id="a9b30-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a9b30-117">Data Item Name</span></span>|<span data-ttu-id="a9b30-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a9b30-118">Data Item Type</span></span>|<span data-ttu-id="a9b30-119">描述</span><span class="sxs-lookup"><span data-stu-id="a9b30-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a9b30-120">活動</span><span class="sxs-lookup"><span data-stu-id="a9b30-120">Activity</span></span>|<span data-ttu-id="a9b30-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a9b30-121">xs:string</span></span>|<span data-ttu-id="a9b30-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a9b30-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a9b30-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a9b30-123">DisplayName</span></span>|<span data-ttu-id="a9b30-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a9b30-124">xs:string</span></span>|<span data-ttu-id="a9b30-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a9b30-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a9b30-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a9b30-126">InstanceId</span></span>|<span data-ttu-id="a9b30-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a9b30-127">xs:string</span></span>|<span data-ttu-id="a9b30-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="a9b30-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a9b30-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a9b30-129">AppDomain</span></span>|<span data-ttu-id="a9b30-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a9b30-130">xs:string</span></span>|<span data-ttu-id="a9b30-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a9b30-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
