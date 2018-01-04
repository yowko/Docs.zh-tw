---
title: 401- StopSignPostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 058cae31c70e2c415e27870af1a0064b84a70b12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="a8def-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="a8def-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="a8def-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a8def-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8def-104">ID</span><span class="sxs-lookup"><span data-stu-id="a8def-104">ID</span></span>|<span data-ttu-id="a8def-105">401</span><span class="sxs-lookup"><span data-stu-id="a8def-105">401</span></span>|  
|<span data-ttu-id="a8def-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a8def-106">Keywords</span></span>|<span data-ttu-id="a8def-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="a8def-107">Troubleshooting</span></span>|  
|<span data-ttu-id="a8def-108">層級</span><span class="sxs-lookup"><span data-stu-id="a8def-108">Level</span></span>|<span data-ttu-id="a8def-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a8def-109">Information</span></span>|  
|<span data-ttu-id="a8def-110">通道</span><span class="sxs-lookup"><span data-stu-id="a8def-110">Channel</span></span>|<span data-ttu-id="a8def-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a8def-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a8def-112">描述</span><span class="sxs-lookup"><span data-stu-id="a8def-112">Description</span></span>  
 <span data-ttu-id="a8def-113">此事件會標記端對端活動的結束。</span><span class="sxs-lookup"><span data-stu-id="a8def-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="a8def-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8def-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a8def-115">訊息</span><span class="sxs-lookup"><span data-stu-id="a8def-115">Message</span></span>  
 <span data-ttu-id="a8def-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="a8def-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a8def-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a8def-117">Details</span></span>  
  
|<span data-ttu-id="a8def-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a8def-118">Data Item Name</span></span>|<span data-ttu-id="a8def-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a8def-119">Data Item Type</span></span>|<span data-ttu-id="a8def-120">描述</span><span class="sxs-lookup"><span data-stu-id="a8def-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a8def-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="a8def-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="a8def-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="a8def-122">The name of the activity.</span></span>|  
|<span data-ttu-id="a8def-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a8def-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a8def-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a8def-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
