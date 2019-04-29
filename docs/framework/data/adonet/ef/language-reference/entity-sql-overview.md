---
title: Entity SQL 概觀
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 100d616462cd76e1dde8fc855787ec3118842fc8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606173"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="5b318-102">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="5b318-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5b318-103">是類似 SQL 的語言，可讓您在 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 中查詢概念模型。</span><span class="sxs-lookup"><span data-stu-id="5b318-103">is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="5b318-104">概念模型實體和關聯性，以代表資料和[!INCLUDE[esql](../../../../../../includes/esql-md.md)]可讓您查詢這些實體和關聯性中使用 SQL 使用者很熟悉的格式。</span><span class="sxs-lookup"><span data-stu-id="5b318-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="5b318-105">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 會與儲存區特定的資料提供者一起運作，將泛型 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 轉譯成儲存區特定的查詢。</span><span class="sxs-lookup"><span data-stu-id="5b318-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="5b318-106">EntityClient 提供者會提供一個方式來針對實體模型執行 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 命令，並傳回豐富的資料型別，包括純量結果、結果集和物件圖形。</span><span class="sxs-lookup"><span data-stu-id="5b318-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="5b318-107">當您建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢的文字，其方式是將 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢字串指派給它的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="5b318-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5b318-108"><xref:System.Data.EntityClient.EntityDataReader> 會公開針對 EDM 執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。</span><span class="sxs-lookup"><span data-stu-id="5b318-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="5b318-109">若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。</span><span class="sxs-lookup"><span data-stu-id="5b318-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="5b318-110">除了 EntityClient 提供者外，[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 也能讓您使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 針對概念模型執行查詢，並將資料當做強型別 CLR 物件 (實體類型的執行個體) 傳回。</span><span class="sxs-lookup"><span data-stu-id="5b318-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="5b318-111">如需詳細資訊，請參閱 <<c0> [ 使用物件](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="5b318-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="5b318-112">本章節提供有關 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的概念資訊。</span><span class="sxs-lookup"><span data-stu-id="5b318-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b318-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="5b318-113">In This Section</span></span>  
 [<span data-ttu-id="5b318-114">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="5b318-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="5b318-115">Entity SQL 快速參考</span><span class="sxs-lookup"><span data-stu-id="5b318-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="5b318-116">類型系統</span><span class="sxs-lookup"><span data-stu-id="5b318-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="5b318-117">型別定義</span><span class="sxs-lookup"><span data-stu-id="5b318-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="5b318-118">建構類型</span><span class="sxs-lookup"><span data-stu-id="5b318-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="5b318-119">查詢計劃快取</span><span class="sxs-lookup"><span data-stu-id="5b318-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="5b318-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="5b318-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="5b318-121">識別項</span><span class="sxs-lookup"><span data-stu-id="5b318-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="5b318-122">參數</span><span class="sxs-lookup"><span data-stu-id="5b318-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="5b318-123">變數</span><span class="sxs-lookup"><span data-stu-id="5b318-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="5b318-124">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="5b318-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="5b318-125">常值</span><span class="sxs-lookup"><span data-stu-id="5b318-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="5b318-126">Null 常值和型別推斷</span><span class="sxs-lookup"><span data-stu-id="5b318-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="5b318-127">輸入字元集</span><span class="sxs-lookup"><span data-stu-id="5b318-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="5b318-128">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="5b318-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="5b318-129">函式</span><span class="sxs-lookup"><span data-stu-id="5b318-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="5b318-130">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="5b318-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="5b318-131">分頁</span><span class="sxs-lookup"><span data-stu-id="5b318-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="5b318-132">比較語意</span><span class="sxs-lookup"><span data-stu-id="5b318-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="5b318-133">撰寫巢狀 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="5b318-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="5b318-134">可為 Null 的結構類型</span><span class="sxs-lookup"><span data-stu-id="5b318-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b318-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b318-135">See also</span></span>

- [<span data-ttu-id="5b318-136">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="5b318-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="5b318-137">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="5b318-137">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="5b318-138">CSDL、SSDL 和 MSL 規格</span><span class="sxs-lookup"><span data-stu-id="5b318-138">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
