---
title: 類型系統 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149827"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="bdf7a-102">類型系統 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bdf7a-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bdf7a-103">支援多種類型：</span><span class="sxs-lookup"><span data-stu-id="bdf7a-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="bdf7a-104">基本 (簡單) 型別，例如 `Int32` 和 `String.`。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="bdf7a-105">結構描述中定義的名義型別，例如 <xref:System.Data.Metadata.Edm.EntityType>、<xref:System.Data.Metadata.Edm.ComplexType> 和 <xref:System.Data.Metadata.Edm.RelationshipType>。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="bdf7a-106">沒有在結構描述中明確定義的匿名型別：<xref:System.Data.Metadata.Edm.CollectionType>、<xref:System.Data.Metadata.Edm.RowType> 和 <xref:System.Data.Metadata.Edm.RefType>。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="bdf7a-107">本節討論未在架構中顯式定義但實體 SQL 支援的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="bdf7a-108">有關基元和標稱類型的資訊，請參閱[概念模型類型 （CSDL）。](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)</span><span class="sxs-lookup"><span data-stu-id="bdf7a-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="bdf7a-109">資料列</span><span class="sxs-lookup"><span data-stu-id="bdf7a-109">Rows</span></span>  
 <span data-ttu-id="bdf7a-110">資料列的結構取決於此資料列所包含之具型別和具名成員的序列。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="bdf7a-111">資料列型別沒有任何識別 (Identity)，而且無法從中繼承。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="bdf7a-112">如果這些成員分別對等，相同資料列型別的執行個體 (Instance) 就會對等。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="bdf7a-113">除了結構化對等以外，資料列沒有任何行為，而且在 Common Language Runtime 中沒有對等項目。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="bdf7a-114">查詢可能會產生包含資料列或資料列集合的結構。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="bdf7a-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢與主應用程式 (Host) 語言之間的 API 繫結會定義如何在產生結果的查詢中實現資料列。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="bdf7a-116">有關如何構造行實例的資訊，請參閱[構造類型](constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="bdf7a-117">集合</span><span class="sxs-lookup"><span data-stu-id="bdf7a-117">Collections</span></span>  
 <span data-ttu-id="bdf7a-118">集合型別代表零個或多個其他物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="bdf7a-119">有關如何構造集合的資訊，請參閱[構造類型](constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="bdf7a-120">參考</span><span class="sxs-lookup"><span data-stu-id="bdf7a-120">References</span></span>  
 <span data-ttu-id="bdf7a-121">參考是指向特定實體集中特定實體的邏輯指標。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="bdf7a-122">支援下列用來建構、解構及巡覽參考的運算子：</span><span class="sxs-lookup"><span data-stu-id="bdf7a-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="bdf7a-123">裁判</span><span class="sxs-lookup"><span data-stu-id="bdf7a-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="bdf7a-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="bdf7a-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="bdf7a-125">關鍵</span><span class="sxs-lookup"><span data-stu-id="bdf7a-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="bdf7a-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="bdf7a-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="bdf7a-127">您可以使用成員存取 (點) 運算子 (`.`) 來巡覽參考。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="bdf7a-128">下列程式碼片段會透過巡覽 r (參考) 屬性，擷取 (訂單的) Id 屬性。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 <span data-ttu-id="bdf7a-129">如果此參數值為 null，或者參考的目標不存在，結果就是 null。</span><span class="sxs-lookup"><span data-stu-id="bdf7a-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf7a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdf7a-130">See also</span></span>

- [<span data-ttu-id="bdf7a-131">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="bdf7a-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="bdf7a-132">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="bdf7a-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="bdf7a-133">CAST</span><span class="sxs-lookup"><span data-stu-id="bdf7a-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="bdf7a-134">CSDL、SSDL 和 MSL 規格</span><span class="sxs-lookup"><span data-stu-id="bdf7a-134">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
