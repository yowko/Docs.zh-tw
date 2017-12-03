---
title: 1131 - InvokeMethodUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db529ed413d70165c7813e23ce8f164262c8e16b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="a8cb9-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="a8cb9-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="a8cb9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a8cb9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8cb9-104">ID</span><span class="sxs-lookup"><span data-stu-id="a8cb9-104">ID</span></span>|<span data-ttu-id="a8cb9-105">1131</span><span class="sxs-lookup"><span data-stu-id="a8cb9-105">1131</span></span>|  
|<span data-ttu-id="a8cb9-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a8cb9-106">Keywords</span></span>|<span data-ttu-id="a8cb9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a8cb9-107">WFRuntime</span></span>|  
|<span data-ttu-id="a8cb9-108">層級</span><span class="sxs-lookup"><span data-stu-id="a8cb9-108">Level</span></span>|<span data-ttu-id="a8cb9-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a8cb9-109">Information</span></span>|  
|<span data-ttu-id="a8cb9-110">通道</span><span class="sxs-lookup"><span data-stu-id="a8cb9-110">Channel</span></span>|<span data-ttu-id="a8cb9-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a8cb9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a8cb9-112">描述</span><span class="sxs-lookup"><span data-stu-id="a8cb9-112">Description</span></span>  
 <span data-ttu-id="a8cb9-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出其於叫用方法時，使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="a8cb9-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a8cb9-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a8cb9-114">Message</span></span>  
 <span data-ttu-id="a8cb9-115">InvokeMethod '%1' - 方法使用 '%2' 和 '%3' 非同步模式。</span><span class="sxs-lookup"><span data-stu-id="a8cb9-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a8cb9-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a8cb9-116">Details</span></span>  
  
|<span data-ttu-id="a8cb9-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a8cb9-117">Data Item Name</span></span>|<span data-ttu-id="a8cb9-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a8cb9-118">Data Item Type</span></span>|<span data-ttu-id="a8cb9-119">描述</span><span class="sxs-lookup"><span data-stu-id="a8cb9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a8cb9-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="a8cb9-120">InvokeMethod</span></span>|<span data-ttu-id="a8cb9-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a8cb9-121">xs:string</span></span>|<span data-ttu-id="a8cb9-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a8cb9-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="a8cb9-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="a8cb9-123">BeginMethod</span></span>|<span data-ttu-id="a8cb9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a8cb9-124">xs:string</span></span>|<span data-ttu-id="a8cb9-125">Begin 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8cb9-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="a8cb9-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="a8cb9-126">EndMethod</span></span>|<span data-ttu-id="a8cb9-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a8cb9-127">xs:string</span></span>|<span data-ttu-id="a8cb9-128">End 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8cb9-128">The name of the end method.</span></span>|  
|<span data-ttu-id="a8cb9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a8cb9-129">AppDomain</span></span>|<span data-ttu-id="a8cb9-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a8cb9-130">xs:string</span></span>|<span data-ttu-id="a8cb9-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a8cb9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
