---
title: 1124 - InvokeMethodIsStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8db91ad18548ac67a1ad2942fb7f57048e272df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="31d20-102">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="31d20-102">1124 - InvokeMethodIsStatic</span></span>
## <a name="properties"></a><span data-ttu-id="31d20-103">屬性</span><span class="sxs-lookup"><span data-stu-id="31d20-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31d20-104">ID</span><span class="sxs-lookup"><span data-stu-id="31d20-104">ID</span></span>|<span data-ttu-id="31d20-105">1124</span><span class="sxs-lookup"><span data-stu-id="31d20-105">1124</span></span>|  
|<span data-ttu-id="31d20-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="31d20-106">Keywords</span></span>|<span data-ttu-id="31d20-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="31d20-107">WFRuntime</span></span>|  
|<span data-ttu-id="31d20-108">層級</span><span class="sxs-lookup"><span data-stu-id="31d20-108">Level</span></span>|<span data-ttu-id="31d20-109">資訊</span><span class="sxs-lookup"><span data-stu-id="31d20-109">Information</span></span>|  
|<span data-ttu-id="31d20-110">通道</span><span class="sxs-lookup"><span data-stu-id="31d20-110">Channel</span></span>|<span data-ttu-id="31d20-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="31d20-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31d20-112">描述</span><span class="sxs-lookup"><span data-stu-id="31d20-112">Description</span></span>  
 <span data-ttu-id="31d20-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出要叫用的方法是靜態的。</span><span class="sxs-lookup"><span data-stu-id="31d20-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31d20-114">訊息</span><span class="sxs-lookup"><span data-stu-id="31d20-114">Message</span></span>  
 <span data-ttu-id="31d20-115">InvokeMethod '%1' - 方法是靜態方法。</span><span class="sxs-lookup"><span data-stu-id="31d20-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31d20-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="31d20-116">Details</span></span>  
  
|<span data-ttu-id="31d20-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="31d20-117">Data Item Name</span></span>|<span data-ttu-id="31d20-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="31d20-118">Data Item Type</span></span>|<span data-ttu-id="31d20-119">描述</span><span class="sxs-lookup"><span data-stu-id="31d20-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31d20-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="31d20-120">InvokeMethod</span></span>|<span data-ttu-id="31d20-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="31d20-121">xs:string</span></span>|<span data-ttu-id="31d20-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="31d20-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="31d20-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="31d20-123">AppDomain</span></span>|<span data-ttu-id="31d20-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="31d20-124">xs:string</span></span>|<span data-ttu-id="31d20-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="31d20-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
