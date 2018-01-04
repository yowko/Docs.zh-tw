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
ms.workload: dotnet
ms.openlocfilehash: c8b5e255e9a753c6476a070609b0cbda189d37a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="e58a3-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="e58a3-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="e58a3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e58a3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e58a3-104">ID</span><span class="sxs-lookup"><span data-stu-id="e58a3-104">ID</span></span>|<span data-ttu-id="e58a3-105">1125</span><span class="sxs-lookup"><span data-stu-id="e58a3-105">1125</span></span>|  
|<span data-ttu-id="e58a3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e58a3-106">Keywords</span></span>|<span data-ttu-id="e58a3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e58a3-107">WFRuntime</span></span>|  
|<span data-ttu-id="e58a3-108">層級</span><span class="sxs-lookup"><span data-stu-id="e58a3-108">Level</span></span>|<span data-ttu-id="e58a3-109">資訊</span><span class="sxs-lookup"><span data-stu-id="e58a3-109">Information</span></span>|  
|<span data-ttu-id="e58a3-110">通道</span><span class="sxs-lookup"><span data-stu-id="e58a3-110">Channel</span></span>|<span data-ttu-id="e58a3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e58a3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e58a3-112">描述</span><span class="sxs-lookup"><span data-stu-id="e58a3-112">Description</span></span>  
 <span data-ttu-id="e58a3-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出要叫用的方法不是靜態的。</span><span class="sxs-lookup"><span data-stu-id="e58a3-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e58a3-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e58a3-114">Message</span></span>  
 <span data-ttu-id="e58a3-115">InvokeMethod '%1' - 方法不是靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e58a3-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e58a3-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e58a3-116">Details</span></span>  
  
|<span data-ttu-id="e58a3-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e58a3-117">Data Item Name</span></span>|<span data-ttu-id="e58a3-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e58a3-118">Data Item Type</span></span>|<span data-ttu-id="e58a3-119">描述</span><span class="sxs-lookup"><span data-stu-id="e58a3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e58a3-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e58a3-120">InvokeMethod</span></span>|<span data-ttu-id="e58a3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e58a3-121">xs:string</span></span>|<span data-ttu-id="e58a3-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e58a3-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="e58a3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e58a3-123">AppDomain</span></span>|<span data-ttu-id="e58a3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e58a3-124">xs:string</span></span>|<span data-ttu-id="e58a3-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e58a3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
