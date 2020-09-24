---
title: Entity SQL 概觀
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e9a5117984380938e48e0cd1113107c74389480f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148123"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="3bc46-102">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="3bc46-102">Entity SQL Overview</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3bc46-103">是一種類似 SQL 的語言，可讓您查詢 Entity Framework 中的概念模型。</span><span class="sxs-lookup"><span data-stu-id="3bc46-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="3bc46-104">概念模型將資料表示為實體和關聯性，並可 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 讓您以熟悉 SQL 的格式來查詢這些實體和關聯性。</span><span class="sxs-lookup"><span data-stu-id="3bc46-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="3bc46-105">Entity Framework 適用于儲存體專屬的資料提供者，可將泛型轉譯為 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 儲存體專屬的查詢。</span><span class="sxs-lookup"><span data-stu-id="3bc46-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="3bc46-106">EntityClient 提供者會提供一個方式來針對實體模型執行 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 命令，並傳回豐富的資料型別，包括純量結果、結果集和物件圖形。</span><span class="sxs-lookup"><span data-stu-id="3bc46-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="3bc46-107">當您建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢的文字，其方式是將 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢字串指派給它的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="3bc46-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3bc46-108"><xref:System.Data.EntityClient.EntityDataReader> 會公開針對 EDM 執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。</span><span class="sxs-lookup"><span data-stu-id="3bc46-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="3bc46-109">若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。</span><span class="sxs-lookup"><span data-stu-id="3bc46-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="3bc46-110">除了 EntityClient 提供者之外，Entity Framework 還可讓您用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 來針對概念模型執行查詢，並將資料以強型別 CLR 物件（實體類型的實例）傳回。</span><span class="sxs-lookup"><span data-stu-id="3bc46-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="3bc46-111">如需詳細資訊，請參閱 [使用物件](../working-with-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="3bc46-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="3bc46-112">本章節提供有關 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的概念資訊。</span><span class="sxs-lookup"><span data-stu-id="3bc46-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bc46-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="3bc46-113">In This Section</span></span>  

 [<span data-ttu-id="3bc46-114">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="3bc46-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="3bc46-115">Entity SQL 快速參考</span><span class="sxs-lookup"><span data-stu-id="3bc46-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="3bc46-116">型別系統</span><span class="sxs-lookup"><span data-stu-id="3bc46-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-117">類型定義</span><span class="sxs-lookup"><span data-stu-id="3bc46-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-118">建構類型</span><span class="sxs-lookup"><span data-stu-id="3bc46-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-119">查詢計劃快取</span><span class="sxs-lookup"><span data-stu-id="3bc46-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="3bc46-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-121">識別碼</span><span class="sxs-lookup"><span data-stu-id="3bc46-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-122">參數</span><span class="sxs-lookup"><span data-stu-id="3bc46-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-123">變數</span><span class="sxs-lookup"><span data-stu-id="3bc46-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-124">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="3bc46-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-125">文字</span><span class="sxs-lookup"><span data-stu-id="3bc46-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-126">Null 常值和型別推斷</span><span class="sxs-lookup"><span data-stu-id="3bc46-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-127">輸入字元集</span><span class="sxs-lookup"><span data-stu-id="3bc46-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-128">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="3bc46-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-129">函式</span><span class="sxs-lookup"><span data-stu-id="3bc46-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-130">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="3bc46-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-131">Paging</span><span class="sxs-lookup"><span data-stu-id="3bc46-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-132">比較語意</span><span class="sxs-lookup"><span data-stu-id="3bc46-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="3bc46-133">撰寫巢狀 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="3bc46-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="3bc46-134">可為 Null 的結構類型</span><span class="sxs-lookup"><span data-stu-id="3bc46-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="3bc46-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bc46-135">See also</span></span>

- [<span data-ttu-id="3bc46-136">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="3bc46-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3bc46-137">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="3bc46-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="3bc46-138">CSDL、SSDL 和 MSL 規格</span><span class="sxs-lookup"><span data-stu-id="3bc46-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
