---
title: 類型系統 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0afeffd3ad180d6cc6175010140754e279988b38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034098"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="edf98-102">類型系統 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="edf98-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="edf98-103">支援數種類型：</span><span class="sxs-lookup"><span data-stu-id="edf98-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="edf98-104">基本 (簡單) 型別，例如 `Int32` 和 `String.`。</span><span class="sxs-lookup"><span data-stu-id="edf98-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="edf98-105">結構描述中定義的名義型別，例如 <xref:System.Data.Metadata.Edm.EntityType>、<xref:System.Data.Metadata.Edm.ComplexType> 和 <xref:System.Data.Metadata.Edm.RelationshipType>。</span><span class="sxs-lookup"><span data-stu-id="edf98-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="edf98-106">沒有在結構描述中明確定義的匿名型別：<xref:System.Data.Metadata.Edm.CollectionType>、<xref:System.Data.Metadata.Edm.RowType> 和 <xref:System.Data.Metadata.Edm.RefType>。</span><span class="sxs-lookup"><span data-stu-id="edf98-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="edf98-107">本節將討論沒有結構描述中明確定義，但支援 Entity SQL 所支援的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="edf98-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="edf98-108">如需基本和名義型別資訊，請參閱[概念模型型別 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)。</span><span class="sxs-lookup"><span data-stu-id="edf98-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="edf98-109">列</span><span class="sxs-lookup"><span data-stu-id="edf98-109">Rows</span></span>  
 <span data-ttu-id="edf98-110">資料列的結構取決於此資料列所包含之具型別和具名成員的序列。</span><span class="sxs-lookup"><span data-stu-id="edf98-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="edf98-111">資料列型別沒有任何識別 (Identity)，而且無法從中繼承。</span><span class="sxs-lookup"><span data-stu-id="edf98-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="edf98-112">如果這些成員分別對等，相同資料列型別的執行個體 (Instance) 就會對等。</span><span class="sxs-lookup"><span data-stu-id="edf98-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="edf98-113">除了結構化對等以外，資料列沒有任何行為，而且在 Common Language Runtime 中沒有對等項目。</span><span class="sxs-lookup"><span data-stu-id="edf98-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="edf98-114">查詢可能會產生包含資料列或資料列集合的結構。</span><span class="sxs-lookup"><span data-stu-id="edf98-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="edf98-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢與主應用程式 (Host) 語言之間的 API 繫結會定義如何在產生結果的查詢中實現資料列。</span><span class="sxs-lookup"><span data-stu-id="edf98-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="edf98-116">如需如何建構資料列執行個體的資訊，請參閱[建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="edf98-116">For information on how to construct a row instance, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="edf98-117">集合</span><span class="sxs-lookup"><span data-stu-id="edf98-117">Collections</span></span>  
 <span data-ttu-id="edf98-118">集合型別代表零個或多個其他物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="edf98-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="edf98-119">如需如何建構集合的詳細資訊，請參閱[建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="edf98-119">For information on how to construct collection, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="edf98-120">參考</span><span class="sxs-lookup"><span data-stu-id="edf98-120">References</span></span>  
 <span data-ttu-id="edf98-121">參考是指向特定實體集中特定實體的邏輯指標。</span><span class="sxs-lookup"><span data-stu-id="edf98-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="edf98-122">支援下列用來建構、解構及巡覽參考的運算子：</span><span class="sxs-lookup"><span data-stu-id="edf98-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="edf98-123">REF</span><span class="sxs-lookup"><span data-stu-id="edf98-123">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
- [<span data-ttu-id="edf98-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="edf98-124">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
- [<span data-ttu-id="edf98-125">KEY</span><span class="sxs-lookup"><span data-stu-id="edf98-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
- [<span data-ttu-id="edf98-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="edf98-126">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 <span data-ttu-id="edf98-127">您可以使用成員存取 (點) 運算子 (`.`) 來巡覽參考。</span><span class="sxs-lookup"><span data-stu-id="edf98-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="edf98-128">下列程式碼片段會透過巡覽 r (參考) 屬性，擷取 (訂單的) Id 屬性。</span><span class="sxs-lookup"><span data-stu-id="edf98-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="edf98-129">如果此參數值為 null，或者參考的目標不存在，結果就是 null。</span><span class="sxs-lookup"><span data-stu-id="edf98-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf98-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edf98-130">See also</span></span>

- [<span data-ttu-id="edf98-131">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="edf98-131">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="edf98-132">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="edf98-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="edf98-133">CAST</span><span class="sxs-lookup"><span data-stu-id="edf98-133">CAST</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)
- [<span data-ttu-id="edf98-134">CSDL、SSDL 和 MSL 規格</span><span class="sxs-lookup"><span data-stu-id="edf98-134">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
