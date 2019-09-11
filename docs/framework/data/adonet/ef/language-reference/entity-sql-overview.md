---
title: Entity SQL 概觀
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 8f40a34f361669d2b8d89b63b3187cae6bf705d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854492"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="8b0dc-102">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="8b0dc-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8b0dc-103">是一種類似 SQL 的語言，可讓您查詢 Entity Framework 中的概念模型。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="8b0dc-104">概念模型會將資料表示為實體和關聯[!INCLUDE[esql](../../../../../../includes/esql-md.md)]性，並可讓您以熟悉使用 SQL 之物件的格式來查詢這些實體和關聯性。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
      
 <span data-ttu-id="8b0dc-105">此 Entity Framework 可與儲存體特定的資料提供者搭配使用[!INCLUDE[esql](../../../../../../includes/esql-md.md)] ，以將泛型轉譯成特定儲存體的查詢。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="8b0dc-106">EntityClient 提供者會提供一個方式來針對實體模型執行 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 命令，並傳回豐富的資料型別，包括純量結果、結果集和物件圖形。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="8b0dc-107">當您建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢的文字，其方式是將 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢字串指派給它的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8b0dc-108"><xref:System.Data.EntityClient.EntityDataReader> 會公開針對 EDM 執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="8b0dc-109">若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="8b0dc-110">除了 EntityClient 提供者之外，Entity Framework 可讓您使用[!INCLUDE[esql](../../../../../../includes/esql-md.md)]針對概念模型執行查詢，並傳回資料做為實體類型實例的強型別 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="8b0dc-111">如需詳細資訊，請參閱[使用物件](../working-with-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="8b0dc-112">本章節提供有關 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的概念資訊。</span><span class="sxs-lookup"><span data-stu-id="8b0dc-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b0dc-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b0dc-113">In This Section</span></span>  
 [<span data-ttu-id="8b0dc-114">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="8b0dc-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="8b0dc-115">Entity SQL 快速參考</span><span class="sxs-lookup"><span data-stu-id="8b0dc-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="8b0dc-116">類型系統</span><span class="sxs-lookup"><span data-stu-id="8b0dc-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-117">型別定義</span><span class="sxs-lookup"><span data-stu-id="8b0dc-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-118">建構類型</span><span class="sxs-lookup"><span data-stu-id="8b0dc-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-119">查詢計劃快取</span><span class="sxs-lookup"><span data-stu-id="8b0dc-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="8b0dc-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-121">識別項</span><span class="sxs-lookup"><span data-stu-id="8b0dc-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-122">參數</span><span class="sxs-lookup"><span data-stu-id="8b0dc-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-123">變數</span><span class="sxs-lookup"><span data-stu-id="8b0dc-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-124">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="8b0dc-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-125">常值</span><span class="sxs-lookup"><span data-stu-id="8b0dc-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-126">Null 常值和型別推斷</span><span class="sxs-lookup"><span data-stu-id="8b0dc-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-127">輸入字元集</span><span class="sxs-lookup"><span data-stu-id="8b0dc-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-128">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="8b0dc-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-129">函式</span><span class="sxs-lookup"><span data-stu-id="8b0dc-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-130">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="8b0dc-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-131">分頁</span><span class="sxs-lookup"><span data-stu-id="8b0dc-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-132">比較語意</span><span class="sxs-lookup"><span data-stu-id="8b0dc-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="8b0dc-133">撰寫巢狀 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="8b0dc-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="8b0dc-134">可為 Null 的結構類型</span><span class="sxs-lookup"><span data-stu-id="8b0dc-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b0dc-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b0dc-135">See also</span></span>

- [<span data-ttu-id="8b0dc-136">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="8b0dc-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8b0dc-137">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="8b0dc-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="8b0dc-138">CSDL、SSDL 和 MSL 規格</span><span class="sxs-lookup"><span data-stu-id="8b0dc-138">CSDL, SSDL, and MSL Specifications</span></span>](csdl-ssdl-and-msl-specifications.md)
