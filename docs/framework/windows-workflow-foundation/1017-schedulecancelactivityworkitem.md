---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510168"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="da9d5-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="da9d5-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="da9d5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="da9d5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da9d5-104">ID</span><span class="sxs-lookup"><span data-stu-id="da9d5-104">ID</span></span>|<span data-ttu-id="da9d5-105">1017</span><span class="sxs-lookup"><span data-stu-id="da9d5-105">1017</span></span>|  
|<span data-ttu-id="da9d5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="da9d5-106">Keywords</span></span>|<span data-ttu-id="da9d5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="da9d5-107">WFRuntime</span></span>|  
|<span data-ttu-id="da9d5-108">層級</span><span class="sxs-lookup"><span data-stu-id="da9d5-108">Level</span></span>|<span data-ttu-id="da9d5-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="da9d5-109">Verbose</span></span>|  
|<span data-ttu-id="da9d5-110">通道</span><span class="sxs-lookup"><span data-stu-id="da9d5-110">Channel</span></span>|<span data-ttu-id="da9d5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="da9d5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="da9d5-112">描述</span><span class="sxs-lookup"><span data-stu-id="da9d5-112">Description</span></span>  
 <span data-ttu-id="da9d5-113">表示已排定 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="da9d5-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="da9d5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="da9d5-114">Message</span></span>  
 <span data-ttu-id="da9d5-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="da9d5-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="da9d5-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="da9d5-116">Details</span></span>  
  
|<span data-ttu-id="da9d5-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="da9d5-117">Data Item Name</span></span>|<span data-ttu-id="da9d5-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="da9d5-118">Data Item Type</span></span>|<span data-ttu-id="da9d5-119">描述</span><span class="sxs-lookup"><span data-stu-id="da9d5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="da9d5-120">活動</span><span class="sxs-lookup"><span data-stu-id="da9d5-120">Activity</span></span>|<span data-ttu-id="da9d5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="da9d5-121">xs:string</span></span>|<span data-ttu-id="da9d5-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="da9d5-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="da9d5-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="da9d5-123">DisplayName</span></span>|<span data-ttu-id="da9d5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="da9d5-124">xs:string</span></span>|<span data-ttu-id="da9d5-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="da9d5-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="da9d5-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="da9d5-126">InstanceId</span></span>|<span data-ttu-id="da9d5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="da9d5-127">xs:string</span></span>|<span data-ttu-id="da9d5-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="da9d5-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="da9d5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="da9d5-129">AppDomain</span></span>|<span data-ttu-id="da9d5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="da9d5-130">xs:string</span></span>|<span data-ttu-id="da9d5-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="da9d5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
