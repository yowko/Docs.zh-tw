---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514565"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="09b80-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="09b80-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="09b80-103">屬性</span><span class="sxs-lookup"><span data-stu-id="09b80-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09b80-104">ID</span><span class="sxs-lookup"><span data-stu-id="09b80-104">ID</span></span>|<span data-ttu-id="09b80-105">4211</span><span class="sxs-lookup"><span data-stu-id="09b80-105">4211</span></span>|  
|<span data-ttu-id="09b80-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="09b80-106">Keywords</span></span>|<span data-ttu-id="09b80-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="09b80-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="09b80-108">層級</span><span class="sxs-lookup"><span data-stu-id="09b80-108">Level</span></span>|<span data-ttu-id="09b80-109">警告</span><span class="sxs-lookup"><span data-stu-id="09b80-109">Warning</span></span>|  
|<span data-ttu-id="09b80-110">通道</span><span class="sxs-lookup"><span data-stu-id="09b80-110">Channel</span></span>|<span data-ttu-id="09b80-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="09b80-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="09b80-112">描述</span><span class="sxs-lookup"><span data-stu-id="09b80-112">Description</span></span>  
 <span data-ttu-id="09b80-113">表示佇列 SQL 重試。</span><span class="sxs-lookup"><span data-stu-id="09b80-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="09b80-114">訊息</span><span class="sxs-lookup"><span data-stu-id="09b80-114">Message</span></span>  
 <span data-ttu-id="09b80-115">佇列 SQL 重試，但延遲 %1 毫秒。</span><span class="sxs-lookup"><span data-stu-id="09b80-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="09b80-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="09b80-116">Details</span></span>  
  
|<span data-ttu-id="09b80-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="09b80-117">Data Item Name</span></span>|<span data-ttu-id="09b80-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="09b80-118">Data Item Type</span></span>|<span data-ttu-id="09b80-119">描述</span><span class="sxs-lookup"><span data-stu-id="09b80-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="09b80-120">延遲</span><span class="sxs-lookup"><span data-stu-id="09b80-120">Delay</span></span>|<span data-ttu-id="09b80-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="09b80-121">xs:string</span></span>|<span data-ttu-id="09b80-122">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="09b80-122">The delay between retries.</span></span>|  
|<span data-ttu-id="09b80-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="09b80-123">AppDomain</span></span>|<span data-ttu-id="09b80-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="09b80-124">xs:string</span></span>|<span data-ttu-id="09b80-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="09b80-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
