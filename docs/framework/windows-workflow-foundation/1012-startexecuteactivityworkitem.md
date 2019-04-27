---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: d6b330bc454c39584e5027f757fd9d9d3434d941
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924575"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="78be8-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="78be8-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="78be8-103">屬性</span><span class="sxs-lookup"><span data-stu-id="78be8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78be8-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="78be8-104">ID</span></span>|<span data-ttu-id="78be8-105">1012</span><span class="sxs-lookup"><span data-stu-id="78be8-105">1012</span></span>|  
|<span data-ttu-id="78be8-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="78be8-106">Keywords</span></span>|<span data-ttu-id="78be8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="78be8-107">WFRuntime</span></span>|  
|<span data-ttu-id="78be8-108">層級</span><span class="sxs-lookup"><span data-stu-id="78be8-108">Level</span></span>|<span data-ttu-id="78be8-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="78be8-109">Verbose</span></span>|  
|<span data-ttu-id="78be8-110">通道</span><span class="sxs-lookup"><span data-stu-id="78be8-110">Channel</span></span>|<span data-ttu-id="78be8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="78be8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="78be8-112">描述</span><span class="sxs-lookup"><span data-stu-id="78be8-112">Description</span></span>  
 <span data-ttu-id="78be8-113">表示 ExecuteActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="78be8-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="78be8-114">訊息</span><span class="sxs-lookup"><span data-stu-id="78be8-114">Message</span></span>  
 <span data-ttu-id="78be8-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="78be8-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="78be8-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="78be8-116">Details</span></span>  
  
|<span data-ttu-id="78be8-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="78be8-117">Data Item Name</span></span>|<span data-ttu-id="78be8-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="78be8-118">Data Item Type</span></span>|<span data-ttu-id="78be8-119">描述</span><span class="sxs-lookup"><span data-stu-id="78be8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="78be8-120">活動</span><span class="sxs-lookup"><span data-stu-id="78be8-120">Activity</span></span>|<span data-ttu-id="78be8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="78be8-121">xs:string</span></span>|<span data-ttu-id="78be8-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="78be8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="78be8-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="78be8-123">DisplayName</span></span>|<span data-ttu-id="78be8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="78be8-124">xs:string</span></span>|<span data-ttu-id="78be8-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="78be8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="78be8-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="78be8-126">InstanceId</span></span>|<span data-ttu-id="78be8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="78be8-127">xs:string</span></span>|<span data-ttu-id="78be8-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="78be8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="78be8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="78be8-129">AppDomain</span></span>|<span data-ttu-id="78be8-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="78be8-130">xs:string</span></span>|<span data-ttu-id="78be8-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="78be8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
