---
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 1776252c362feb3c3ebc04651603944040ceee7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999748"
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="5b72b-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="5b72b-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="5b72b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5b72b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b72b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="5b72b-104">ID</span></span>|<span data-ttu-id="5b72b-105">401</span><span class="sxs-lookup"><span data-stu-id="5b72b-105">401</span></span>|  
|<span data-ttu-id="5b72b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5b72b-106">Keywords</span></span>|<span data-ttu-id="5b72b-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="5b72b-107">Troubleshooting</span></span>|  
|<span data-ttu-id="5b72b-108">層級</span><span class="sxs-lookup"><span data-stu-id="5b72b-108">Level</span></span>|<span data-ttu-id="5b72b-109">資訊</span><span class="sxs-lookup"><span data-stu-id="5b72b-109">Information</span></span>|  
|<span data-ttu-id="5b72b-110">通道</span><span class="sxs-lookup"><span data-stu-id="5b72b-110">Channel</span></span>|<span data-ttu-id="5b72b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5b72b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5b72b-112">描述</span><span class="sxs-lookup"><span data-stu-id="5b72b-112">Description</span></span>  
 <span data-ttu-id="5b72b-113">此事件會標記端對端活動的結束。</span><span class="sxs-lookup"><span data-stu-id="5b72b-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="5b72b-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b72b-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5b72b-115">訊息</span><span class="sxs-lookup"><span data-stu-id="5b72b-115">Message</span></span>  
 <span data-ttu-id="5b72b-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="5b72b-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5b72b-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5b72b-117">Details</span></span>  
  
|<span data-ttu-id="5b72b-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5b72b-118">Data Item Name</span></span>|<span data-ttu-id="5b72b-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5b72b-119">Data Item Type</span></span>|<span data-ttu-id="5b72b-120">描述</span><span class="sxs-lookup"><span data-stu-id="5b72b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5b72b-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="5b72b-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="5b72b-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="5b72b-122">The name of the activity.</span></span>|  
|<span data-ttu-id="5b72b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5b72b-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5b72b-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5b72b-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
