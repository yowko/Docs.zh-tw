---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f74a133a685699bcefc014269a9ecb3ebea4e505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="5ebcf-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="5ebcf-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5ebcf-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5ebcf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ebcf-104">ID</span><span class="sxs-lookup"><span data-stu-id="5ebcf-104">ID</span></span>|<span data-ttu-id="5ebcf-105">1018</span><span class="sxs-lookup"><span data-stu-id="5ebcf-105">1018</span></span>|  
|<span data-ttu-id="5ebcf-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5ebcf-106">Keywords</span></span>|<span data-ttu-id="5ebcf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5ebcf-107">WFRuntime</span></span>|  
|<span data-ttu-id="5ebcf-108">層級</span><span class="sxs-lookup"><span data-stu-id="5ebcf-108">Level</span></span>|<span data-ttu-id="5ebcf-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5ebcf-109">Verbose</span></span>|  
|<span data-ttu-id="5ebcf-110">通道</span><span class="sxs-lookup"><span data-stu-id="5ebcf-110">Channel</span></span>|<span data-ttu-id="5ebcf-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5ebcf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5ebcf-112">描述</span><span class="sxs-lookup"><span data-stu-id="5ebcf-112">Description</span></span>  
 <span data-ttu-id="5ebcf-113">表示 CancelActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="5ebcf-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5ebcf-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5ebcf-114">Message</span></span>  
 <span data-ttu-id="5ebcf-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3'的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="5ebcf-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5ebcf-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5ebcf-116">Details</span></span>  
  
|<span data-ttu-id="5ebcf-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5ebcf-117">Data Item Name</span></span>|<span data-ttu-id="5ebcf-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5ebcf-118">Data Item Type</span></span>|<span data-ttu-id="5ebcf-119">描述</span><span class="sxs-lookup"><span data-stu-id="5ebcf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5ebcf-120">活動</span><span class="sxs-lookup"><span data-stu-id="5ebcf-120">Activity</span></span>|<span data-ttu-id="5ebcf-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ebcf-121">xs:string</span></span>|<span data-ttu-id="5ebcf-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="5ebcf-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="5ebcf-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5ebcf-123">DisplayName</span></span>|<span data-ttu-id="5ebcf-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ebcf-124">xs:string</span></span>|<span data-ttu-id="5ebcf-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5ebcf-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="5ebcf-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5ebcf-126">InstanceId</span></span>|<span data-ttu-id="5ebcf-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ebcf-127">xs:string</span></span>|<span data-ttu-id="5ebcf-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="5ebcf-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5ebcf-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5ebcf-129">AppDomain</span></span>|<span data-ttu-id="5ebcf-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ebcf-130">xs:string</span></span>|<span data-ttu-id="5ebcf-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5ebcf-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
