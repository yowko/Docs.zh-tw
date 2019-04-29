---
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: 6dfb3b187f58de2c9573c2d2f6d579e3557c3de8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774949"
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="c7133-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="c7133-102">402 - StartSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="c7133-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c7133-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7133-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c7133-104">ID</span></span>|<span data-ttu-id="c7133-105">402</span><span class="sxs-lookup"><span data-stu-id="c7133-105">402</span></span>|  
|<span data-ttu-id="c7133-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c7133-106">Keywords</span></span>|<span data-ttu-id="c7133-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="c7133-107">Troubleshooting</span></span>|  
|<span data-ttu-id="c7133-108">層級</span><span class="sxs-lookup"><span data-stu-id="c7133-108">Level</span></span>|<span data-ttu-id="c7133-109">資訊</span><span class="sxs-lookup"><span data-stu-id="c7133-109">Information</span></span>|  
|<span data-ttu-id="c7133-110">通道</span><span class="sxs-lookup"><span data-stu-id="c7133-110">Channel</span></span>|<span data-ttu-id="c7133-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c7133-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7133-112">描述</span><span class="sxs-lookup"><span data-stu-id="c7133-112">Description</span></span>  
 <span data-ttu-id="c7133-113">此活動會標記端對端活動的開始。</span><span class="sxs-lookup"><span data-stu-id="c7133-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="c7133-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7133-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7133-115">訊息</span><span class="sxs-lookup"><span data-stu-id="c7133-115">Message</span></span>  
 <span data-ttu-id="c7133-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="c7133-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7133-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7133-117">Details</span></span>  
  
|<span data-ttu-id="c7133-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c7133-118">Data Item Name</span></span>|<span data-ttu-id="c7133-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c7133-119">Data Item Type</span></span>|<span data-ttu-id="c7133-120">描述</span><span class="sxs-lookup"><span data-stu-id="c7133-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7133-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="c7133-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="c7133-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="c7133-122">The name of the activity.</span></span>|  
|<span data-ttu-id="c7133-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c7133-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c7133-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c7133-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
