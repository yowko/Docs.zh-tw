---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511263"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="bae6e-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="bae6e-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="bae6e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="bae6e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bae6e-104">ID</span><span class="sxs-lookup"><span data-stu-id="bae6e-104">ID</span></span>|<span data-ttu-id="bae6e-105">4212</span><span class="sxs-lookup"><span data-stu-id="bae6e-105">4212</span></span>|  
|<span data-ttu-id="bae6e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bae6e-106">Keywords</span></span>|<span data-ttu-id="bae6e-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="bae6e-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="bae6e-108">層級</span><span class="sxs-lookup"><span data-stu-id="bae6e-108">Level</span></span>|<span data-ttu-id="bae6e-109">警告</span><span class="sxs-lookup"><span data-stu-id="bae6e-109">Warning</span></span>|  
|<span data-ttu-id="bae6e-110">通道</span><span class="sxs-lookup"><span data-stu-id="bae6e-110">Channel</span></span>|<span data-ttu-id="bae6e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bae6e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bae6e-112">描述</span><span class="sxs-lookup"><span data-stu-id="bae6e-112">Description</span></span>  
 <span data-ttu-id="bae6e-113">SQL 提供者嘗試擷取執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="bae6e-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bae6e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="bae6e-114">Message</span></span>  
 <span data-ttu-id="bae6e-115">嘗試取得執行個體鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="bae6e-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="bae6e-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="bae6e-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="bae6e-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="bae6e-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bae6e-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bae6e-118">Details</span></span>  
  
|<span data-ttu-id="bae6e-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="bae6e-119">Data Item Name</span></span>|<span data-ttu-id="bae6e-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="bae6e-120">Data Item Type</span></span>|<span data-ttu-id="bae6e-121">描述</span><span class="sxs-lookup"><span data-stu-id="bae6e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bae6e-122">延遲</span><span class="sxs-lookup"><span data-stu-id="bae6e-122">Delay</span></span>|<span data-ttu-id="bae6e-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="bae6e-123">xs:string</span></span>|<span data-ttu-id="bae6e-124">重試之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="bae6e-124">The delay between retries.</span></span>|  
|<span data-ttu-id="bae6e-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bae6e-125">AppDomain</span></span>|<span data-ttu-id="bae6e-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="bae6e-126">xs:string</span></span>|<span data-ttu-id="bae6e-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="bae6e-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
