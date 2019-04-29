---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774240"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="6f5d5-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="6f5d5-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="6f5d5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="6f5d5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f5d5-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="6f5d5-104">ID</span></span>|<span data-ttu-id="6f5d5-105">4211</span><span class="sxs-lookup"><span data-stu-id="6f5d5-105">4211</span></span>|  
|<span data-ttu-id="6f5d5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="6f5d5-106">Keywords</span></span>|<span data-ttu-id="6f5d5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="6f5d5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="6f5d5-108">層級</span><span class="sxs-lookup"><span data-stu-id="6f5d5-108">Level</span></span>|<span data-ttu-id="6f5d5-109">警告</span><span class="sxs-lookup"><span data-stu-id="6f5d5-109">Warning</span></span>|  
|<span data-ttu-id="6f5d5-110">通道</span><span class="sxs-lookup"><span data-stu-id="6f5d5-110">Channel</span></span>|<span data-ttu-id="6f5d5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6f5d5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6f5d5-112">描述</span><span class="sxs-lookup"><span data-stu-id="6f5d5-112">Description</span></span>  
 <span data-ttu-id="6f5d5-113">表示佇列 SQL 重試。</span><span class="sxs-lookup"><span data-stu-id="6f5d5-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6f5d5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="6f5d5-114">Message</span></span>  
 <span data-ttu-id="6f5d5-115">佇列 SQL 重試，但延遲 %1 毫秒。</span><span class="sxs-lookup"><span data-stu-id="6f5d5-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6f5d5-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6f5d5-116">Details</span></span>  
  
|<span data-ttu-id="6f5d5-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="6f5d5-117">Data Item Name</span></span>|<span data-ttu-id="6f5d5-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="6f5d5-118">Data Item Type</span></span>|<span data-ttu-id="6f5d5-119">描述</span><span class="sxs-lookup"><span data-stu-id="6f5d5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6f5d5-120">延遲</span><span class="sxs-lookup"><span data-stu-id="6f5d5-120">Delay</span></span>|<span data-ttu-id="6f5d5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6f5d5-121">xs:string</span></span>|<span data-ttu-id="6f5d5-122">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="6f5d5-122">The delay between retries.</span></span>|  
|<span data-ttu-id="6f5d5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6f5d5-123">AppDomain</span></span>|<span data-ttu-id="6f5d5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6f5d5-124">xs:string</span></span>|<span data-ttu-id="6f5d5-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="6f5d5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
