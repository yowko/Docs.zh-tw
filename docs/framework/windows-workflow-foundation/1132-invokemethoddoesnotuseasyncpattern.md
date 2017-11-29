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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 300e843529bfc76df4193b46cd713ce0bd9cdbfd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="f3c7d-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="f3c7d-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="f3c7d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f3c7d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3c7d-104">ID</span><span class="sxs-lookup"><span data-stu-id="f3c7d-104">ID</span></span>|<span data-ttu-id="f3c7d-105">1132</span><span class="sxs-lookup"><span data-stu-id="f3c7d-105">1132</span></span>|  
|<span data-ttu-id="f3c7d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3c7d-106">Keywords</span></span>|<span data-ttu-id="f3c7d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f3c7d-107">WFRuntime</span></span>|  
|<span data-ttu-id="f3c7d-108">層級</span><span class="sxs-lookup"><span data-stu-id="f3c7d-108">Level</span></span>|<span data-ttu-id="f3c7d-109">資訊</span><span class="sxs-lookup"><span data-stu-id="f3c7d-109">Information</span></span>|  
|<span data-ttu-id="f3c7d-110">通道</span><span class="sxs-lookup"><span data-stu-id="f3c7d-110">Channel</span></span>|<span data-ttu-id="f3c7d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f3c7d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3c7d-112">描述</span><span class="sxs-lookup"><span data-stu-id="f3c7d-112">Description</span></span>  
 <span data-ttu-id="f3c7d-113">在 CacheMetadata 步驟期間，InvokeMethod 活動表示其於叫用方法時，未使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="f3c7d-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3c7d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f3c7d-114">Message</span></span>  
 <span data-ttu-id="f3c7d-115">InvokeMethod '%1' - 方法未使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="f3c7d-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3c7d-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f3c7d-116">Details</span></span>  
  
|<span data-ttu-id="f3c7d-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f3c7d-117">Data Item Name</span></span>|<span data-ttu-id="f3c7d-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f3c7d-118">Data Item Type</span></span>|<span data-ttu-id="f3c7d-119">描述</span><span class="sxs-lookup"><span data-stu-id="f3c7d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3c7d-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f3c7d-120">InvokeMethod</span></span>|<span data-ttu-id="f3c7d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f3c7d-121">xs:string</span></span>|<span data-ttu-id="f3c7d-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f3c7d-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f3c7d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3c7d-123">AppDomain</span></span>|<span data-ttu-id="f3c7d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f3c7d-124">xs:string</span></span>|<span data-ttu-id="f3c7d-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f3c7d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
