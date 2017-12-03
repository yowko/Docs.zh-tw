---
title: 403 - SuspendSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9259ca71a21e36eaae06d33920adec538e36d98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="3f05d-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="3f05d-102">403 - SuspendSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="3f05d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3f05d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f05d-104">ID</span><span class="sxs-lookup"><span data-stu-id="3f05d-104">ID</span></span>|<span data-ttu-id="3f05d-105">403</span><span class="sxs-lookup"><span data-stu-id="3f05d-105">403</span></span>|  
|<span data-ttu-id="3f05d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3f05d-106">Keywords</span></span>|<span data-ttu-id="3f05d-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="3f05d-107">Troubleshooting</span></span>|  
|<span data-ttu-id="3f05d-108">層級</span><span class="sxs-lookup"><span data-stu-id="3f05d-108">Level</span></span>|<span data-ttu-id="3f05d-109">資訊</span><span class="sxs-lookup"><span data-stu-id="3f05d-109">Information</span></span>|  
|<span data-ttu-id="3f05d-110">通道</span><span class="sxs-lookup"><span data-stu-id="3f05d-110">Channel</span></span>|<span data-ttu-id="3f05d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="3f05d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3f05d-112">描述</span><span class="sxs-lookup"><span data-stu-id="3f05d-112">Description</span></span>  
 <span data-ttu-id="3f05d-113">此活動會標記端對端活動的暫停。</span><span class="sxs-lookup"><span data-stu-id="3f05d-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="3f05d-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f05d-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3f05d-115">訊息</span><span class="sxs-lookup"><span data-stu-id="3f05d-115">Message</span></span>  
 <span data-ttu-id="3f05d-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="3f05d-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3f05d-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3f05d-117">Details</span></span>  
  
|<span data-ttu-id="3f05d-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3f05d-118">Data Item Name</span></span>|<span data-ttu-id="3f05d-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3f05d-119">Data Item Type</span></span>|<span data-ttu-id="3f05d-120">描述</span><span class="sxs-lookup"><span data-stu-id="3f05d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3f05d-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="3f05d-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="3f05d-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="3f05d-122">The name of the activity.</span></span>|  
|<span data-ttu-id="3f05d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3f05d-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3f05d-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3f05d-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
