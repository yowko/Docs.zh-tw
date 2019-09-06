---
title: 標準函式
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 8949735ba4712b721460335b4579f0a268c91aea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251281"
---
# <a name="canonical-functions"></a><span data-ttu-id="4a6ef-102">標準函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-102">Canonical Functions</span></span>
<span data-ttu-id="4a6ef-103">本節討論所有資料提供者都支援，而且可由所有查詢技術使用的標準函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="4a6ef-104">標準函式無法由提供者擴允。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="4a6ef-105">這些標準函式將會轉譯成提供者的對應資料來源功能，</span><span class="sxs-lookup"><span data-stu-id="4a6ef-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="4a6ef-106">這樣一來就能以跨資料來源的通用形式表示函式引動過程。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="4a6ef-107">由於這些標準函式與資料來源無關，所以標準函式的引數和傳回型別是以概念模型中的型別定義。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="4a6ef-108">不過，某些資料來源可能無法支援概念模型中的所有型別。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="4a6ef-109">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢中使用標準函式時，會在資料來源中呼叫適當的函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="4a6ef-110">所有標準函式都必須明確指定 null 輸入行為和錯誤條件。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="4a6ef-111">存放區提供者應遵守該行為，但 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 並不強制執行此行為。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="4a6ef-112">針對 LINQ 案例，針對的[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]查詢牽涉到將 CLR 方法對應到基礎資料來源中的方法。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="4a6ef-113">CLR 方法會對應到標準函式，這樣一來便會正確對應一組特定的方法，而不用顧慮資料來源為何。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="4a6ef-114">標準函式命名空間</span><span class="sxs-lookup"><span data-stu-id="4a6ef-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="4a6ef-115">標準函式的命名空間為 <xref:System.Data.Metadata.Edm>。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="4a6ef-116"><xref:System.Data.Metadata.Edm> 命名空間會自動包含在所有查詢中。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="4a6ef-117">但是，如果匯入了另一個命名空間，包含與標準函式同名的函式 (在 <xref:System.Data.Metadata.Edm> 命名空間中)，您就必須指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a6ef-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="4a6ef-118">In This Section</span></span>  
 [<span data-ttu-id="4a6ef-119">彙總標準函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-119">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="4a6ef-120">討論彙總 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4a6ef-121">數學標準函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-121">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="4a6ef-122">討論數學 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4a6ef-123">字串標準函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-123">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="4a6ef-124">討論字串 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4a6ef-125">日期和時間標準函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-125">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="4a6ef-126">討論日期和時間 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4a6ef-127">位元標準函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-127">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="4a6ef-128">討論位元運算 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4a6ef-129">空間函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-129">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="4a6ef-130">討論空間 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4a6ef-131">其他標準函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-131">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="4a6ef-132">討論未分類為位元運算、日期/時間、字串、數學或彙總的函式。</span><span class="sxs-lookup"><span data-stu-id="4a6ef-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a6ef-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a6ef-133">See also</span></span>

- [<span data-ttu-id="4a6ef-134">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="4a6ef-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="4a6ef-135">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="4a6ef-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="4a6ef-136">概念模型標準與 SQL Server 函式的對應</span><span class="sxs-lookup"><span data-stu-id="4a6ef-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="4a6ef-137">使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="4a6ef-137">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
