---
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 66251141cdf66c18ad0c1334f6f3e6c0629b4b33
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241053"
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="5a3e5-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="5a3e5-102">403 - SuspendSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="5a3e5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5a3e5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a3e5-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="5a3e5-104">ID</span></span>|<span data-ttu-id="5a3e5-105">403</span><span class="sxs-lookup"><span data-stu-id="5a3e5-105">403</span></span>|  
|<span data-ttu-id="5a3e5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5a3e5-106">Keywords</span></span>|<span data-ttu-id="5a3e5-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="5a3e5-107">Troubleshooting</span></span>|  
|<span data-ttu-id="5a3e5-108">層級</span><span class="sxs-lookup"><span data-stu-id="5a3e5-108">Level</span></span>|<span data-ttu-id="5a3e5-109">資訊</span><span class="sxs-lookup"><span data-stu-id="5a3e5-109">Information</span></span>|  
|<span data-ttu-id="5a3e5-110">通路</span><span class="sxs-lookup"><span data-stu-id="5a3e5-110">Channel</span></span>|<span data-ttu-id="5a3e5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5a3e5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5a3e5-112">描述</span><span class="sxs-lookup"><span data-stu-id="5a3e5-112">Description</span></span>  

 <span data-ttu-id="5a3e5-113">此活動會標記端對端活動的暫停。</span><span class="sxs-lookup"><span data-stu-id="5a3e5-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="5a3e5-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a3e5-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5a3e5-115">訊息</span><span class="sxs-lookup"><span data-stu-id="5a3e5-115">Message</span></span>  

 <span data-ttu-id="5a3e5-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="5a3e5-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5a3e5-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5a3e5-117">Details</span></span>  
  
|<span data-ttu-id="5a3e5-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5a3e5-118">Data Item Name</span></span>|<span data-ttu-id="5a3e5-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5a3e5-119">Data Item Type</span></span>|<span data-ttu-id="5a3e5-120">描述</span><span class="sxs-lookup"><span data-stu-id="5a3e5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5a3e5-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="5a3e5-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="5a3e5-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="5a3e5-122">The name of the activity.</span></span>|  
|<span data-ttu-id="5a3e5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5a3e5-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5a3e5-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5a3e5-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
