---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: 46a3dc8d313ec72ac90abc2e2e333b274dad2e4c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294296"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="ce262-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="ce262-102">1033 - StartRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="ce262-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ce262-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce262-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="ce262-104">ID</span></span>|<span data-ttu-id="ce262-105">1033</span><span class="sxs-lookup"><span data-stu-id="ce262-105">1033</span></span>|  
|<span data-ttu-id="ce262-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ce262-106">Keywords</span></span>|<span data-ttu-id="ce262-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ce262-107">WFRuntime</span></span>|  
|<span data-ttu-id="ce262-108">層級</span><span class="sxs-lookup"><span data-stu-id="ce262-108">Level</span></span>|<span data-ttu-id="ce262-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="ce262-109">Verbose</span></span>|  
|<span data-ttu-id="ce262-110">通路</span><span class="sxs-lookup"><span data-stu-id="ce262-110">Channel</span></span>|<span data-ttu-id="ce262-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ce262-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce262-112">描述</span><span class="sxs-lookup"><span data-stu-id="ce262-112">Description</span></span>  

 <span data-ttu-id="ce262-113">表示 RuntimeWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="ce262-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ce262-114">訊息</span><span class="sxs-lookup"><span data-stu-id="ce262-114">Message</span></span>  

 <span data-ttu-id="ce262-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="ce262-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ce262-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ce262-116">Details</span></span>  
  
|<span data-ttu-id="ce262-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ce262-117">Data Item Name</span></span>|<span data-ttu-id="ce262-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ce262-118">Data Item Type</span></span>|<span data-ttu-id="ce262-119">描述</span><span class="sxs-lookup"><span data-stu-id="ce262-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ce262-120">活動</span><span class="sxs-lookup"><span data-stu-id="ce262-120">Activity</span></span>|<span data-ttu-id="ce262-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce262-121">xs:string</span></span>|<span data-ttu-id="ce262-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ce262-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ce262-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ce262-123">DisplayName</span></span>|<span data-ttu-id="ce262-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce262-124">xs:string</span></span>|<span data-ttu-id="ce262-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="ce262-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ce262-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ce262-126">InstanceId</span></span>|<span data-ttu-id="ce262-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce262-127">xs:string</span></span>|<span data-ttu-id="ce262-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="ce262-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ce262-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ce262-129">AppDomain</span></span>|<span data-ttu-id="ce262-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce262-130">xs:string</span></span>|<span data-ttu-id="ce262-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ce262-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
