---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982250"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="f0b17-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="f0b17-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f0b17-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f0b17-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0b17-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f0b17-104">ID</span></span>|<span data-ttu-id="f0b17-105">1011</span><span class="sxs-lookup"><span data-stu-id="f0b17-105">1011</span></span>|  
|<span data-ttu-id="f0b17-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f0b17-106">Keywords</span></span>|<span data-ttu-id="f0b17-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f0b17-107">WFRuntime</span></span>|  
|<span data-ttu-id="f0b17-108">層級</span><span class="sxs-lookup"><span data-stu-id="f0b17-108">Level</span></span>|<span data-ttu-id="f0b17-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f0b17-109">Verbose</span></span>|  
|<span data-ttu-id="f0b17-110">通道</span><span class="sxs-lookup"><span data-stu-id="f0b17-110">Channel</span></span>|<span data-ttu-id="f0b17-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f0b17-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f0b17-112">描述</span><span class="sxs-lookup"><span data-stu-id="f0b17-112">Description</span></span>  
 <span data-ttu-id="f0b17-113">表示 ExecuteActivityWorkItem 已排程。</span><span class="sxs-lookup"><span data-stu-id="f0b17-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f0b17-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f0b17-114">Message</span></span>  
 <span data-ttu-id="f0b17-115">已經為活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 排程 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="f0b17-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f0b17-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0b17-116">Details</span></span>  
  
|<span data-ttu-id="f0b17-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f0b17-117">Data Item Name</span></span>|<span data-ttu-id="f0b17-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f0b17-118">Data Item Type</span></span>|<span data-ttu-id="f0b17-119">描述</span><span class="sxs-lookup"><span data-stu-id="f0b17-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f0b17-120">活動</span><span class="sxs-lookup"><span data-stu-id="f0b17-120">Activity</span></span>|<span data-ttu-id="f0b17-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0b17-121">xs:string</span></span>|<span data-ttu-id="f0b17-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f0b17-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f0b17-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f0b17-123">DisplayName</span></span>|<span data-ttu-id="f0b17-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0b17-124">xs:string</span></span>|<span data-ttu-id="f0b17-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f0b17-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f0b17-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f0b17-126">InstanceId</span></span>|<span data-ttu-id="f0b17-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0b17-127">xs:string</span></span>|<span data-ttu-id="f0b17-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f0b17-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f0b17-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f0b17-129">AppDomain</span></span>|<span data-ttu-id="f0b17-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0b17-130">xs:string</span></span>|<span data-ttu-id="f0b17-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f0b17-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
