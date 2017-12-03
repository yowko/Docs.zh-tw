---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b31bb8db8252474d20f7523e08cadf35bfcc84a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="91a27-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="91a27-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="91a27-103">屬性</span><span class="sxs-lookup"><span data-stu-id="91a27-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91a27-104">ID</span><span class="sxs-lookup"><span data-stu-id="91a27-104">ID</span></span>|<span data-ttu-id="91a27-105">1125</span><span class="sxs-lookup"><span data-stu-id="91a27-105">1125</span></span>|  
|<span data-ttu-id="91a27-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="91a27-106">Keywords</span></span>|<span data-ttu-id="91a27-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="91a27-107">WFRuntime</span></span>|  
|<span data-ttu-id="91a27-108">層級</span><span class="sxs-lookup"><span data-stu-id="91a27-108">Level</span></span>|<span data-ttu-id="91a27-109">資訊</span><span class="sxs-lookup"><span data-stu-id="91a27-109">Information</span></span>|  
|<span data-ttu-id="91a27-110">通道</span><span class="sxs-lookup"><span data-stu-id="91a27-110">Channel</span></span>|<span data-ttu-id="91a27-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="91a27-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91a27-112">描述</span><span class="sxs-lookup"><span data-stu-id="91a27-112">Description</span></span>  
 <span data-ttu-id="91a27-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出要叫用的方法不是靜態的。</span><span class="sxs-lookup"><span data-stu-id="91a27-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91a27-114">訊息</span><span class="sxs-lookup"><span data-stu-id="91a27-114">Message</span></span>  
 <span data-ttu-id="91a27-115">InvokeMethod '%1' - 方法不是靜態方法。</span><span class="sxs-lookup"><span data-stu-id="91a27-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91a27-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="91a27-116">Details</span></span>  
  
|<span data-ttu-id="91a27-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="91a27-117">Data Item Name</span></span>|<span data-ttu-id="91a27-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="91a27-118">Data Item Type</span></span>|<span data-ttu-id="91a27-119">描述</span><span class="sxs-lookup"><span data-stu-id="91a27-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91a27-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="91a27-120">InvokeMethod</span></span>|<span data-ttu-id="91a27-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="91a27-121">xs:string</span></span>|<span data-ttu-id="91a27-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="91a27-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="91a27-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="91a27-123">AppDomain</span></span>|<span data-ttu-id="91a27-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="91a27-124">xs:string</span></span>|<span data-ttu-id="91a27-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="91a27-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
