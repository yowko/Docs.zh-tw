---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510062"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="9d1aa-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="9d1aa-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9d1aa-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9d1aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d1aa-104">ID</span><span class="sxs-lookup"><span data-stu-id="9d1aa-104">ID</span></span>|<span data-ttu-id="9d1aa-105">1033</span><span class="sxs-lookup"><span data-stu-id="9d1aa-105">1033</span></span>|  
|<span data-ttu-id="9d1aa-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9d1aa-106">Keywords</span></span>|<span data-ttu-id="9d1aa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9d1aa-107">WFRuntime</span></span>|  
|<span data-ttu-id="9d1aa-108">層級</span><span class="sxs-lookup"><span data-stu-id="9d1aa-108">Level</span></span>|<span data-ttu-id="9d1aa-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9d1aa-109">Verbose</span></span>|  
|<span data-ttu-id="9d1aa-110">通道</span><span class="sxs-lookup"><span data-stu-id="9d1aa-110">Channel</span></span>|<span data-ttu-id="9d1aa-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9d1aa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9d1aa-112">描述</span><span class="sxs-lookup"><span data-stu-id="9d1aa-112">Description</span></span>  
 <span data-ttu-id="9d1aa-113">表示 RuntimeWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="9d1aa-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9d1aa-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9d1aa-114">Message</span></span>  
 <span data-ttu-id="9d1aa-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。</span><span class="sxs-lookup"><span data-stu-id="9d1aa-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9d1aa-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9d1aa-116">Details</span></span>  
  
|<span data-ttu-id="9d1aa-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9d1aa-117">Data Item Name</span></span>|<span data-ttu-id="9d1aa-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9d1aa-118">Data Item Type</span></span>|<span data-ttu-id="9d1aa-119">描述</span><span class="sxs-lookup"><span data-stu-id="9d1aa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9d1aa-120">活動</span><span class="sxs-lookup"><span data-stu-id="9d1aa-120">Activity</span></span>|<span data-ttu-id="9d1aa-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d1aa-121">xs:string</span></span>|<span data-ttu-id="9d1aa-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9d1aa-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9d1aa-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9d1aa-123">DisplayName</span></span>|<span data-ttu-id="9d1aa-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d1aa-124">xs:string</span></span>|<span data-ttu-id="9d1aa-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9d1aa-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9d1aa-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9d1aa-126">InstanceId</span></span>|<span data-ttu-id="9d1aa-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d1aa-127">xs:string</span></span>|<span data-ttu-id="9d1aa-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9d1aa-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9d1aa-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9d1aa-129">AppDomain</span></span>|<span data-ttu-id="9d1aa-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="9d1aa-130">xs:string</span></span>|<span data-ttu-id="9d1aa-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9d1aa-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
