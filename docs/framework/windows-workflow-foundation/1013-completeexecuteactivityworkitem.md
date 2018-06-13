---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509570"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="c6ae7-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="c6ae7-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c6ae7-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c6ae7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6ae7-104">ID</span><span class="sxs-lookup"><span data-stu-id="c6ae7-104">ID</span></span>|<span data-ttu-id="c6ae7-105">1013</span><span class="sxs-lookup"><span data-stu-id="c6ae7-105">1013</span></span>|  
|<span data-ttu-id="c6ae7-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c6ae7-106">Keywords</span></span>|<span data-ttu-id="c6ae7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c6ae7-107">WFRuntime</span></span>|  
|<span data-ttu-id="c6ae7-108">層級</span><span class="sxs-lookup"><span data-stu-id="c6ae7-108">Level</span></span>|<span data-ttu-id="c6ae7-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c6ae7-109">Verbose</span></span>|  
|<span data-ttu-id="c6ae7-110">通道</span><span class="sxs-lookup"><span data-stu-id="c6ae7-110">Channel</span></span>|<span data-ttu-id="c6ae7-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c6ae7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c6ae7-112">描述</span><span class="sxs-lookup"><span data-stu-id="c6ae7-112">Description</span></span>  
 <span data-ttu-id="c6ae7-113">表示 ExecuteActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="c6ae7-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c6ae7-114">Message</span></span>  
 <span data-ttu-id="c6ae7-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c6ae7-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6ae7-116">Details</span></span>  
  
|<span data-ttu-id="c6ae7-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c6ae7-117">Data Item Name</span></span>|<span data-ttu-id="c6ae7-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c6ae7-118">Data Item Type</span></span>|<span data-ttu-id="c6ae7-119">描述</span><span class="sxs-lookup"><span data-stu-id="c6ae7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c6ae7-120">活動</span><span class="sxs-lookup"><span data-stu-id="c6ae7-120">Activity</span></span>|<span data-ttu-id="c6ae7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6ae7-121">xs:string</span></span>|<span data-ttu-id="c6ae7-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c6ae7-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c6ae7-123">DisplayName</span></span>|<span data-ttu-id="c6ae7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6ae7-124">xs:string</span></span>|<span data-ttu-id="c6ae7-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c6ae7-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c6ae7-126">InstanceId</span></span>|<span data-ttu-id="c6ae7-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6ae7-127">xs:string</span></span>|<span data-ttu-id="c6ae7-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c6ae7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c6ae7-129">AppDomain</span></span>|<span data-ttu-id="c6ae7-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6ae7-130">xs:string</span></span>|<span data-ttu-id="c6ae7-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
