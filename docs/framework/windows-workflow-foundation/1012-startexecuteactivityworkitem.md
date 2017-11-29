---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc60af91088fd61910dc0301b93844f4771177af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="abfad-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="abfad-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="abfad-103">屬性</span><span class="sxs-lookup"><span data-stu-id="abfad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="abfad-104">ID</span><span class="sxs-lookup"><span data-stu-id="abfad-104">ID</span></span>|<span data-ttu-id="abfad-105">1012</span><span class="sxs-lookup"><span data-stu-id="abfad-105">1012</span></span>|  
|<span data-ttu-id="abfad-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="abfad-106">Keywords</span></span>|<span data-ttu-id="abfad-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="abfad-107">WFRuntime</span></span>|  
|<span data-ttu-id="abfad-108">層級</span><span class="sxs-lookup"><span data-stu-id="abfad-108">Level</span></span>|<span data-ttu-id="abfad-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="abfad-109">Verbose</span></span>|  
|<span data-ttu-id="abfad-110">通道</span><span class="sxs-lookup"><span data-stu-id="abfad-110">Channel</span></span>|<span data-ttu-id="abfad-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="abfad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="abfad-112">描述</span><span class="sxs-lookup"><span data-stu-id="abfad-112">Description</span></span>  
 <span data-ttu-id="abfad-113">表示 ExecuteActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="abfad-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="abfad-114">訊息</span><span class="sxs-lookup"><span data-stu-id="abfad-114">Message</span></span>  
 <span data-ttu-id="abfad-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="abfad-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="abfad-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="abfad-116">Details</span></span>  
  
|<span data-ttu-id="abfad-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="abfad-117">Data Item Name</span></span>|<span data-ttu-id="abfad-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="abfad-118">Data Item Type</span></span>|<span data-ttu-id="abfad-119">描述</span><span class="sxs-lookup"><span data-stu-id="abfad-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="abfad-120">活動</span><span class="sxs-lookup"><span data-stu-id="abfad-120">Activity</span></span>|<span data-ttu-id="abfad-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="abfad-121">xs:string</span></span>|<span data-ttu-id="abfad-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="abfad-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="abfad-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="abfad-123">DisplayName</span></span>|<span data-ttu-id="abfad-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="abfad-124">xs:string</span></span>|<span data-ttu-id="abfad-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="abfad-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="abfad-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="abfad-126">InstanceId</span></span>|<span data-ttu-id="abfad-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="abfad-127">xs:string</span></span>|<span data-ttu-id="abfad-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="abfad-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="abfad-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="abfad-129">AppDomain</span></span>|<span data-ttu-id="abfad-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="abfad-130">xs:string</span></span>|<span data-ttu-id="abfad-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="abfad-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
