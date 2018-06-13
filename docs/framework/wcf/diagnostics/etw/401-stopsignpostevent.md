---
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 1776252c362feb3c3ebc04651603944040ceee7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474164"
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="ef714-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="ef714-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="ef714-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ef714-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef714-104">ID</span><span class="sxs-lookup"><span data-stu-id="ef714-104">ID</span></span>|<span data-ttu-id="ef714-105">401</span><span class="sxs-lookup"><span data-stu-id="ef714-105">401</span></span>|  
|<span data-ttu-id="ef714-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ef714-106">Keywords</span></span>|<span data-ttu-id="ef714-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="ef714-107">Troubleshooting</span></span>|  
|<span data-ttu-id="ef714-108">層級</span><span class="sxs-lookup"><span data-stu-id="ef714-108">Level</span></span>|<span data-ttu-id="ef714-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ef714-109">Information</span></span>|  
|<span data-ttu-id="ef714-110">通道</span><span class="sxs-lookup"><span data-stu-id="ef714-110">Channel</span></span>|<span data-ttu-id="ef714-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ef714-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef714-112">描述</span><span class="sxs-lookup"><span data-stu-id="ef714-112">Description</span></span>  
 <span data-ttu-id="ef714-113">此事件會標記端對端活動的結束。</span><span class="sxs-lookup"><span data-stu-id="ef714-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="ef714-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef714-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef714-115">訊息</span><span class="sxs-lookup"><span data-stu-id="ef714-115">Message</span></span>  
 <span data-ttu-id="ef714-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="ef714-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef714-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef714-117">Details</span></span>  
  
|<span data-ttu-id="ef714-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ef714-118">Data Item Name</span></span>|<span data-ttu-id="ef714-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ef714-119">Data Item Type</span></span>|<span data-ttu-id="ef714-120">描述</span><span class="sxs-lookup"><span data-stu-id="ef714-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef714-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="ef714-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="ef714-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="ef714-122">The name of the activity.</span></span>|  
|<span data-ttu-id="ef714-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef714-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ef714-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ef714-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
