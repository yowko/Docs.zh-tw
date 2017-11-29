---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f430e7b58d5aba277b0a35a20f1f5fdb707bce9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="8fee1-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="8fee1-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8fee1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8fee1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8fee1-104">ID</span><span class="sxs-lookup"><span data-stu-id="8fee1-104">ID</span></span>|<span data-ttu-id="8fee1-105">1013</span><span class="sxs-lookup"><span data-stu-id="8fee1-105">1013</span></span>|  
|<span data-ttu-id="8fee1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8fee1-106">Keywords</span></span>|<span data-ttu-id="8fee1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8fee1-107">WFRuntime</span></span>|  
|<span data-ttu-id="8fee1-108">層級</span><span class="sxs-lookup"><span data-stu-id="8fee1-108">Level</span></span>|<span data-ttu-id="8fee1-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="8fee1-109">Verbose</span></span>|  
|<span data-ttu-id="8fee1-110">通道</span><span class="sxs-lookup"><span data-stu-id="8fee1-110">Channel</span></span>|<span data-ttu-id="8fee1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8fee1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8fee1-112">描述</span><span class="sxs-lookup"><span data-stu-id="8fee1-112">Description</span></span>  
 <span data-ttu-id="8fee1-113">表示 ExecuteActivityWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="8fee1-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="8fee1-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8fee1-114">Message</span></span>  
 <span data-ttu-id="8fee1-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="8fee1-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8fee1-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8fee1-116">Details</span></span>  
  
|<span data-ttu-id="8fee1-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8fee1-117">Data Item Name</span></span>|<span data-ttu-id="8fee1-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8fee1-118">Data Item Type</span></span>|<span data-ttu-id="8fee1-119">描述</span><span class="sxs-lookup"><span data-stu-id="8fee1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8fee1-120">活動</span><span class="sxs-lookup"><span data-stu-id="8fee1-120">Activity</span></span>|<span data-ttu-id="8fee1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8fee1-121">xs:string</span></span>|<span data-ttu-id="8fee1-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8fee1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8fee1-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8fee1-123">DisplayName</span></span>|<span data-ttu-id="8fee1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8fee1-124">xs:string</span></span>|<span data-ttu-id="8fee1-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8fee1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8fee1-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8fee1-126">InstanceId</span></span>|<span data-ttu-id="8fee1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8fee1-127">xs:string</span></span>|<span data-ttu-id="8fee1-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="8fee1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8fee1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8fee1-129">AppDomain</span></span>|<span data-ttu-id="8fee1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8fee1-130">xs:string</span></span>|<span data-ttu-id="8fee1-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8fee1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
