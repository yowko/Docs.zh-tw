---
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: ff32c900f4e357b7f1eca669a0ea60f80ea24b19
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258318"
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="4f6e6-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="4f6e6-102">402 - StartSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="4f6e6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="4f6e6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f6e6-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="4f6e6-104">ID</span></span>|<span data-ttu-id="4f6e6-105">402</span><span class="sxs-lookup"><span data-stu-id="4f6e6-105">402</span></span>|  
|<span data-ttu-id="4f6e6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="4f6e6-106">Keywords</span></span>|<span data-ttu-id="4f6e6-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4f6e6-107">Troubleshooting</span></span>|  
|<span data-ttu-id="4f6e6-108">層級</span><span class="sxs-lookup"><span data-stu-id="4f6e6-108">Level</span></span>|<span data-ttu-id="4f6e6-109">資訊</span><span class="sxs-lookup"><span data-stu-id="4f6e6-109">Information</span></span>|  
|<span data-ttu-id="4f6e6-110">通路</span><span class="sxs-lookup"><span data-stu-id="4f6e6-110">Channel</span></span>|<span data-ttu-id="4f6e6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4f6e6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4f6e6-112">描述</span><span class="sxs-lookup"><span data-stu-id="4f6e6-112">Description</span></span>  

 <span data-ttu-id="4f6e6-113">此活動會標記端對端活動的開始。</span><span class="sxs-lookup"><span data-stu-id="4f6e6-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="4f6e6-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f6e6-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4f6e6-115">訊息</span><span class="sxs-lookup"><span data-stu-id="4f6e6-115">Message</span></span>  

 <span data-ttu-id="4f6e6-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="4f6e6-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4f6e6-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4f6e6-117">Details</span></span>  
  
|<span data-ttu-id="4f6e6-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="4f6e6-118">Data Item Name</span></span>|<span data-ttu-id="4f6e6-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="4f6e6-119">Data Item Type</span></span>|<span data-ttu-id="4f6e6-120">描述</span><span class="sxs-lookup"><span data-stu-id="4f6e6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4f6e6-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="4f6e6-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="4f6e6-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="4f6e6-122">The name of the activity.</span></span>|  
|<span data-ttu-id="4f6e6-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4f6e6-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4f6e6-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="4f6e6-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
