---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 349a91f5b4708d829aee8d7f055871ac7dcc8914
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="40b98-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="40b98-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="40b98-103">屬性</span><span class="sxs-lookup"><span data-stu-id="40b98-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40b98-104">ID</span><span class="sxs-lookup"><span data-stu-id="40b98-104">ID</span></span>|<span data-ttu-id="40b98-105">4211</span><span class="sxs-lookup"><span data-stu-id="40b98-105">4211</span></span>|  
|<span data-ttu-id="40b98-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="40b98-106">Keywords</span></span>|<span data-ttu-id="40b98-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="40b98-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="40b98-108">層級</span><span class="sxs-lookup"><span data-stu-id="40b98-108">Level</span></span>|<span data-ttu-id="40b98-109">警告</span><span class="sxs-lookup"><span data-stu-id="40b98-109">Warning</span></span>|  
|<span data-ttu-id="40b98-110">通道</span><span class="sxs-lookup"><span data-stu-id="40b98-110">Channel</span></span>|<span data-ttu-id="40b98-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="40b98-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="40b98-112">描述</span><span class="sxs-lookup"><span data-stu-id="40b98-112">Description</span></span>  
 <span data-ttu-id="40b98-113">表示佇列 SQL 重試。</span><span class="sxs-lookup"><span data-stu-id="40b98-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="40b98-114">訊息</span><span class="sxs-lookup"><span data-stu-id="40b98-114">Message</span></span>  
 <span data-ttu-id="40b98-115">佇列 SQL 重試，但延遲 %1 毫秒。</span><span class="sxs-lookup"><span data-stu-id="40b98-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="40b98-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="40b98-116">Details</span></span>  
  
|<span data-ttu-id="40b98-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="40b98-117">Data Item Name</span></span>|<span data-ttu-id="40b98-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="40b98-118">Data Item Type</span></span>|<span data-ttu-id="40b98-119">描述</span><span class="sxs-lookup"><span data-stu-id="40b98-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="40b98-120">延遲</span><span class="sxs-lookup"><span data-stu-id="40b98-120">Delay</span></span>|<span data-ttu-id="40b98-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="40b98-121">xs:string</span></span>|<span data-ttu-id="40b98-122">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="40b98-122">The delay between retries.</span></span>|  
|<span data-ttu-id="40b98-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="40b98-123">AppDomain</span></span>|<span data-ttu-id="40b98-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="40b98-124">xs:string</span></span>|<span data-ttu-id="40b98-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="40b98-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
