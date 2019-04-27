---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924484"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="7d7ab-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7d7ab-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7d7ab-103">屬性</span><span class="sxs-lookup"><span data-stu-id="7d7ab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d7ab-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="7d7ab-104">ID</span></span>|<span data-ttu-id="7d7ab-105">1017</span><span class="sxs-lookup"><span data-stu-id="7d7ab-105">1017</span></span>|  
|<span data-ttu-id="7d7ab-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7d7ab-106">Keywords</span></span>|<span data-ttu-id="7d7ab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7d7ab-107">WFRuntime</span></span>|  
|<span data-ttu-id="7d7ab-108">層級</span><span class="sxs-lookup"><span data-stu-id="7d7ab-108">Level</span></span>|<span data-ttu-id="7d7ab-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="7d7ab-109">Verbose</span></span>|  
|<span data-ttu-id="7d7ab-110">通道</span><span class="sxs-lookup"><span data-stu-id="7d7ab-110">Channel</span></span>|<span data-ttu-id="7d7ab-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7d7ab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7d7ab-112">描述</span><span class="sxs-lookup"><span data-stu-id="7d7ab-112">Description</span></span>  
 <span data-ttu-id="7d7ab-113">表示已排定 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="7d7ab-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7d7ab-114">訊息</span><span class="sxs-lookup"><span data-stu-id="7d7ab-114">Message</span></span>  
 <span data-ttu-id="7d7ab-115">已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="7d7ab-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7d7ab-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7d7ab-116">Details</span></span>  
  
|<span data-ttu-id="7d7ab-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="7d7ab-117">Data Item Name</span></span>|<span data-ttu-id="7d7ab-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="7d7ab-118">Data Item Type</span></span>|<span data-ttu-id="7d7ab-119">描述</span><span class="sxs-lookup"><span data-stu-id="7d7ab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7d7ab-120">活動</span><span class="sxs-lookup"><span data-stu-id="7d7ab-120">Activity</span></span>|<span data-ttu-id="7d7ab-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d7ab-121">xs:string</span></span>|<span data-ttu-id="7d7ab-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7d7ab-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7d7ab-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7d7ab-123">DisplayName</span></span>|<span data-ttu-id="7d7ab-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d7ab-124">xs:string</span></span>|<span data-ttu-id="7d7ab-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7d7ab-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7d7ab-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7d7ab-126">InstanceId</span></span>|<span data-ttu-id="7d7ab-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d7ab-127">xs:string</span></span>|<span data-ttu-id="7d7ab-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="7d7ab-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7d7ab-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7d7ab-129">AppDomain</span></span>|<span data-ttu-id="7d7ab-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d7ab-130">xs:string</span></span>|<span data-ttu-id="7d7ab-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7d7ab-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
