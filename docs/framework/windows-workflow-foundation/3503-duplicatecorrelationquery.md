---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: e1e64824ee9a95757ed7c00aa17fa80898219401
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270324"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="03f57-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="03f57-102">3503 - DuplicateCorrelationQuery</span></span>

## <a name="properties"></a><span data-ttu-id="03f57-103">屬性</span><span class="sxs-lookup"><span data-stu-id="03f57-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03f57-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="03f57-104">ID</span></span>|<span data-ttu-id="03f57-105">3503</span><span class="sxs-lookup"><span data-stu-id="03f57-105">3503</span></span>|  
|<span data-ttu-id="03f57-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="03f57-106">Keywords</span></span>|<span data-ttu-id="03f57-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="03f57-107">WFServices</span></span>|  
|<span data-ttu-id="03f57-108">層級</span><span class="sxs-lookup"><span data-stu-id="03f57-108">Level</span></span>|<span data-ttu-id="03f57-109">警告</span><span class="sxs-lookup"><span data-stu-id="03f57-109">Warning</span></span>|  
|<span data-ttu-id="03f57-110">通路</span><span class="sxs-lookup"><span data-stu-id="03f57-110">Channel</span></span>|<span data-ttu-id="03f57-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="03f57-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03f57-112">描述</span><span class="sxs-lookup"><span data-stu-id="03f57-112">Description</span></span>  

 <span data-ttu-id="03f57-113">表示發現重複的 CorrelationQuery。</span><span class="sxs-lookup"><span data-stu-id="03f57-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="03f57-114">在計算相互關聯時，不會使用重複的查詢。</span><span class="sxs-lookup"><span data-stu-id="03f57-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03f57-115">訊息</span><span class="sxs-lookup"><span data-stu-id="03f57-115">Message</span></span>  

 <span data-ttu-id="03f57-116">發現 Where='%1' 的重複 CorrelationQuery。</span><span class="sxs-lookup"><span data-stu-id="03f57-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="03f57-117">計算相互關聯時不會使用這個重複的查詢。</span><span class="sxs-lookup"><span data-stu-id="03f57-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03f57-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="03f57-118">Details</span></span>  
  
|<span data-ttu-id="03f57-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="03f57-119">Data Item Name</span></span>|<span data-ttu-id="03f57-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="03f57-120">Data Item Type</span></span>|<span data-ttu-id="03f57-121">描述</span><span class="sxs-lookup"><span data-stu-id="03f57-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03f57-122">Where</span><span class="sxs-lookup"><span data-stu-id="03f57-122">Where</span></span>|<span data-ttu-id="03f57-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="03f57-123">xs:string</span></span>|<span data-ttu-id="03f57-124">相互關聯查詢的 Where 部分。</span><span class="sxs-lookup"><span data-stu-id="03f57-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="03f57-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="03f57-125">AppDomain</span></span>|<span data-ttu-id="03f57-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="03f57-126">xs:string</span></span>|<span data-ttu-id="03f57-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="03f57-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
