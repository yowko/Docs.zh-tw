---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511396"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="ee7aa-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="ee7aa-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="ee7aa-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ee7aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee7aa-104">ID</span><span class="sxs-lookup"><span data-stu-id="ee7aa-104">ID</span></span>|<span data-ttu-id="ee7aa-105">3503</span><span class="sxs-lookup"><span data-stu-id="ee7aa-105">3503</span></span>|  
|<span data-ttu-id="ee7aa-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ee7aa-106">Keywords</span></span>|<span data-ttu-id="ee7aa-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ee7aa-107">WFServices</span></span>|  
|<span data-ttu-id="ee7aa-108">層級</span><span class="sxs-lookup"><span data-stu-id="ee7aa-108">Level</span></span>|<span data-ttu-id="ee7aa-109">警告</span><span class="sxs-lookup"><span data-stu-id="ee7aa-109">Warning</span></span>|  
|<span data-ttu-id="ee7aa-110">通道</span><span class="sxs-lookup"><span data-stu-id="ee7aa-110">Channel</span></span>|<span data-ttu-id="ee7aa-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ee7aa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ee7aa-112">描述</span><span class="sxs-lookup"><span data-stu-id="ee7aa-112">Description</span></span>  
 <span data-ttu-id="ee7aa-113">表示發現重複的 CorrelationQuery。</span><span class="sxs-lookup"><span data-stu-id="ee7aa-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="ee7aa-114">在計算相互關聯時，不會使用重複的查詢。</span><span class="sxs-lookup"><span data-stu-id="ee7aa-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ee7aa-115">訊息</span><span class="sxs-lookup"><span data-stu-id="ee7aa-115">Message</span></span>  
 <span data-ttu-id="ee7aa-116">發現 Where='%1' 的重複 CorrelationQuery。</span><span class="sxs-lookup"><span data-stu-id="ee7aa-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="ee7aa-117">計算相互關聯時不會使用這個重複的查詢。</span><span class="sxs-lookup"><span data-stu-id="ee7aa-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ee7aa-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee7aa-118">Details</span></span>  
  
|<span data-ttu-id="ee7aa-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ee7aa-119">Data Item Name</span></span>|<span data-ttu-id="ee7aa-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ee7aa-120">Data Item Type</span></span>|<span data-ttu-id="ee7aa-121">描述</span><span class="sxs-lookup"><span data-stu-id="ee7aa-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ee7aa-122">位置</span><span class="sxs-lookup"><span data-stu-id="ee7aa-122">Where</span></span>|<span data-ttu-id="ee7aa-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee7aa-123">xs:string</span></span>|<span data-ttu-id="ee7aa-124">相互關聯查詢的 Where 部分。</span><span class="sxs-lookup"><span data-stu-id="ee7aa-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="ee7aa-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ee7aa-125">AppDomain</span></span>|<span data-ttu-id="ee7aa-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee7aa-126">xs:string</span></span>|<span data-ttu-id="ee7aa-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ee7aa-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
