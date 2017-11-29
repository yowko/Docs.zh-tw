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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c318ee6509ce8b96a1e7e78a13f4aeb7c76dde6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="268da-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="268da-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="268da-103">屬性</span><span class="sxs-lookup"><span data-stu-id="268da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="268da-104">ID</span><span class="sxs-lookup"><span data-stu-id="268da-104">ID</span></span>|<span data-ttu-id="268da-105">4211</span><span class="sxs-lookup"><span data-stu-id="268da-105">4211</span></span>|  
|<span data-ttu-id="268da-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="268da-106">Keywords</span></span>|<span data-ttu-id="268da-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="268da-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="268da-108">層級</span><span class="sxs-lookup"><span data-stu-id="268da-108">Level</span></span>|<span data-ttu-id="268da-109">警告</span><span class="sxs-lookup"><span data-stu-id="268da-109">Warning</span></span>|  
|<span data-ttu-id="268da-110">通道</span><span class="sxs-lookup"><span data-stu-id="268da-110">Channel</span></span>|<span data-ttu-id="268da-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="268da-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="268da-112">描述</span><span class="sxs-lookup"><span data-stu-id="268da-112">Description</span></span>  
 <span data-ttu-id="268da-113">表示佇列 SQL 重試。</span><span class="sxs-lookup"><span data-stu-id="268da-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="268da-114">訊息</span><span class="sxs-lookup"><span data-stu-id="268da-114">Message</span></span>  
 <span data-ttu-id="268da-115">佇列 SQL 重試，但延遲 %1 毫秒。</span><span class="sxs-lookup"><span data-stu-id="268da-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="268da-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="268da-116">Details</span></span>  
  
|<span data-ttu-id="268da-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="268da-117">Data Item Name</span></span>|<span data-ttu-id="268da-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="268da-118">Data Item Type</span></span>|<span data-ttu-id="268da-119">描述</span><span class="sxs-lookup"><span data-stu-id="268da-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="268da-120">延遲</span><span class="sxs-lookup"><span data-stu-id="268da-120">Delay</span></span>|<span data-ttu-id="268da-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="268da-121">xs:string</span></span>|<span data-ttu-id="268da-122">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="268da-122">The delay between retries.</span></span>|  
|<span data-ttu-id="268da-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="268da-123">AppDomain</span></span>|<span data-ttu-id="268da-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="268da-124">xs:string</span></span>|<span data-ttu-id="268da-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="268da-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
