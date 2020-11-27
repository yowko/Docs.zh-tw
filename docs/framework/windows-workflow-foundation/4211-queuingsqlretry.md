---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ff8a1e099934f5bf71fef0afbb7e54c0d1851fae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267178"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="4821d-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="4821d-102">4211 - QueuingSqlRetry</span></span>

## <a name="properties"></a><span data-ttu-id="4821d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="4821d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4821d-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="4821d-104">ID</span></span>|<span data-ttu-id="4821d-105">4211</span><span class="sxs-lookup"><span data-stu-id="4821d-105">4211</span></span>|  
|<span data-ttu-id="4821d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="4821d-106">Keywords</span></span>|<span data-ttu-id="4821d-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="4821d-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="4821d-108">層級</span><span class="sxs-lookup"><span data-stu-id="4821d-108">Level</span></span>|<span data-ttu-id="4821d-109">警告</span><span class="sxs-lookup"><span data-stu-id="4821d-109">Warning</span></span>|  
|<span data-ttu-id="4821d-110">通路</span><span class="sxs-lookup"><span data-stu-id="4821d-110">Channel</span></span>|<span data-ttu-id="4821d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4821d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4821d-112">描述</span><span class="sxs-lookup"><span data-stu-id="4821d-112">Description</span></span>  

 <span data-ttu-id="4821d-113">表示佇列 SQL 重試。</span><span class="sxs-lookup"><span data-stu-id="4821d-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4821d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="4821d-114">Message</span></span>  

 <span data-ttu-id="4821d-115">佇列 SQL 重試，但延遲 %1 毫秒。</span><span class="sxs-lookup"><span data-stu-id="4821d-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4821d-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4821d-116">Details</span></span>  
  
|<span data-ttu-id="4821d-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="4821d-117">Data Item Name</span></span>|<span data-ttu-id="4821d-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="4821d-118">Data Item Type</span></span>|<span data-ttu-id="4821d-119">描述</span><span class="sxs-lookup"><span data-stu-id="4821d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4821d-120">延遲</span><span class="sxs-lookup"><span data-stu-id="4821d-120">Delay</span></span>|<span data-ttu-id="4821d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4821d-121">xs:string</span></span>|<span data-ttu-id="4821d-122">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="4821d-122">The delay between retries.</span></span>|  
|<span data-ttu-id="4821d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4821d-123">AppDomain</span></span>|<span data-ttu-id="4821d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4821d-124">xs:string</span></span>|<span data-ttu-id="4821d-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="4821d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
