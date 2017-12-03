---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 321d8c6185c8d24b7a3b6e255e235c36c119ff21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="eddbd-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="eddbd-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="eddbd-103">屬性</span><span class="sxs-lookup"><span data-stu-id="eddbd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eddbd-104">ID</span><span class="sxs-lookup"><span data-stu-id="eddbd-104">ID</span></span>|<span data-ttu-id="eddbd-105">1132</span><span class="sxs-lookup"><span data-stu-id="eddbd-105">1132</span></span>|  
|<span data-ttu-id="eddbd-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="eddbd-106">Keywords</span></span>|<span data-ttu-id="eddbd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="eddbd-107">WFRuntime</span></span>|  
|<span data-ttu-id="eddbd-108">層級</span><span class="sxs-lookup"><span data-stu-id="eddbd-108">Level</span></span>|<span data-ttu-id="eddbd-109">資訊</span><span class="sxs-lookup"><span data-stu-id="eddbd-109">Information</span></span>|  
|<span data-ttu-id="eddbd-110">通道</span><span class="sxs-lookup"><span data-stu-id="eddbd-110">Channel</span></span>|<span data-ttu-id="eddbd-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="eddbd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eddbd-112">描述</span><span class="sxs-lookup"><span data-stu-id="eddbd-112">Description</span></span>  
 <span data-ttu-id="eddbd-113">在 CacheMetadata 步驟期間，InvokeMethod 活動表示其於叫用方法時，未使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="eddbd-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eddbd-114">訊息</span><span class="sxs-lookup"><span data-stu-id="eddbd-114">Message</span></span>  
 <span data-ttu-id="eddbd-115">InvokeMethod '%1' - 方法未使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="eddbd-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eddbd-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="eddbd-116">Details</span></span>  
  
|<span data-ttu-id="eddbd-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="eddbd-117">Data Item Name</span></span>|<span data-ttu-id="eddbd-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="eddbd-118">Data Item Type</span></span>|<span data-ttu-id="eddbd-119">描述</span><span class="sxs-lookup"><span data-stu-id="eddbd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eddbd-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="eddbd-120">InvokeMethod</span></span>|<span data-ttu-id="eddbd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="eddbd-121">xs:string</span></span>|<span data-ttu-id="eddbd-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="eddbd-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="eddbd-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eddbd-123">AppDomain</span></span>|<span data-ttu-id="eddbd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="eddbd-124">xs:string</span></span>|<span data-ttu-id="eddbd-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="eddbd-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
