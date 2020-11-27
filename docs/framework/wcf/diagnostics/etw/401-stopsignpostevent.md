---
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: e549a8aabd0a54022000515050cde19dc4f20dd3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294062"
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="21e52-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="21e52-102">401- StopSignPostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="21e52-103">屬性</span><span class="sxs-lookup"><span data-stu-id="21e52-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21e52-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="21e52-104">ID</span></span>|<span data-ttu-id="21e52-105">401</span><span class="sxs-lookup"><span data-stu-id="21e52-105">401</span></span>|  
|<span data-ttu-id="21e52-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="21e52-106">Keywords</span></span>|<span data-ttu-id="21e52-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="21e52-107">Troubleshooting</span></span>|  
|<span data-ttu-id="21e52-108">層級</span><span class="sxs-lookup"><span data-stu-id="21e52-108">Level</span></span>|<span data-ttu-id="21e52-109">資訊</span><span class="sxs-lookup"><span data-stu-id="21e52-109">Information</span></span>|  
|<span data-ttu-id="21e52-110">通路</span><span class="sxs-lookup"><span data-stu-id="21e52-110">Channel</span></span>|<span data-ttu-id="21e52-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="21e52-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21e52-112">描述</span><span class="sxs-lookup"><span data-stu-id="21e52-112">Description</span></span>  

 <span data-ttu-id="21e52-113">此事件會標記端對端活動的結束。</span><span class="sxs-lookup"><span data-stu-id="21e52-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="21e52-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="21e52-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21e52-115">訊息</span><span class="sxs-lookup"><span data-stu-id="21e52-115">Message</span></span>  

 <span data-ttu-id="21e52-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="21e52-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21e52-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="21e52-117">Details</span></span>  
  
|<span data-ttu-id="21e52-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="21e52-118">Data Item Name</span></span>|<span data-ttu-id="21e52-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="21e52-119">Data Item Type</span></span>|<span data-ttu-id="21e52-120">描述</span><span class="sxs-lookup"><span data-stu-id="21e52-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21e52-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="21e52-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="21e52-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="21e52-122">The name of the activity.</span></span>|  
|<span data-ttu-id="21e52-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="21e52-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="21e52-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="21e52-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
