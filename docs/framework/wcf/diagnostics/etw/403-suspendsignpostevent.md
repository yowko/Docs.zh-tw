---
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 727d164b9cd47657af0d7810103a766f33cb35de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33467203"
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="c3e5a-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="c3e5a-102">403 - SuspendSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="c3e5a-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c3e5a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3e5a-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3e5a-104">ID</span></span>|<span data-ttu-id="c3e5a-105">403</span><span class="sxs-lookup"><span data-stu-id="c3e5a-105">403</span></span>|  
|<span data-ttu-id="c3e5a-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c3e5a-106">Keywords</span></span>|<span data-ttu-id="c3e5a-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="c3e5a-107">Troubleshooting</span></span>|  
|<span data-ttu-id="c3e5a-108">層級</span><span class="sxs-lookup"><span data-stu-id="c3e5a-108">Level</span></span>|<span data-ttu-id="c3e5a-109">資訊</span><span class="sxs-lookup"><span data-stu-id="c3e5a-109">Information</span></span>|  
|<span data-ttu-id="c3e5a-110">通道</span><span class="sxs-lookup"><span data-stu-id="c3e5a-110">Channel</span></span>|<span data-ttu-id="c3e5a-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c3e5a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3e5a-112">描述</span><span class="sxs-lookup"><span data-stu-id="c3e5a-112">Description</span></span>  
 <span data-ttu-id="c3e5a-113">此活動會標記端對端活動的暫停。</span><span class="sxs-lookup"><span data-stu-id="c3e5a-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="c3e5a-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e5a-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3e5a-115">訊息</span><span class="sxs-lookup"><span data-stu-id="c3e5a-115">Message</span></span>  
 <span data-ttu-id="c3e5a-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="c3e5a-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3e5a-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c3e5a-117">Details</span></span>  
  
|<span data-ttu-id="c3e5a-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c3e5a-118">Data Item Name</span></span>|<span data-ttu-id="c3e5a-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c3e5a-119">Data Item Type</span></span>|<span data-ttu-id="c3e5a-120">描述</span><span class="sxs-lookup"><span data-stu-id="c3e5a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3e5a-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="c3e5a-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="c3e5a-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e5a-122">The name of the activity.</span></span>|  
|<span data-ttu-id="c3e5a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c3e5a-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c3e5a-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c3e5a-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
