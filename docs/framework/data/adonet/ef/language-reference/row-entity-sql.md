---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 9515d972addc3dd10a27ffbe7776f77d097a30d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074257"
---
# <a name="row-entity-sql"></a><span data-ttu-id="9a74e-102">ROW (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a74e-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="9a74e-103">從一個或多個值建構匿名、結構式型別的記錄。</span><span class="sxs-lookup"><span data-stu-id="9a74e-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a74e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a74e-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a74e-105">引數</span><span class="sxs-lookup"><span data-stu-id="9a74e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9a74e-106">資料列型別中任何傳回值到結構的有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="9a74e-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="9a74e-107">為資料列型別中指定的值指定別名。</span><span class="sxs-lookup"><span data-stu-id="9a74e-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="9a74e-108">如果未提供別名， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試依據 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 別名產生規則產生別名。</span><span class="sxs-lookup"><span data-stu-id="9a74e-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a74e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9a74e-109">Return Value</span></span>  
 <span data-ttu-id="9a74e-110">資料列型別。</span><span class="sxs-lookup"><span data-stu-id="9a74e-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a74e-111">備註</span><span class="sxs-lookup"><span data-stu-id="9a74e-111">Remarks</span></span>  
 <span data-ttu-id="9a74e-112">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中必須使用資料列建構函式從一或多個值建構匿名、結構式型別的記錄。</span><span class="sxs-lookup"><span data-stu-id="9a74e-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="9a74e-113">資料列建構函式的結果型別是資料列型別，而且它的欄位型別對應到用於建立此資料列的值的型別。</span><span class="sxs-lookup"><span data-stu-id="9a74e-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="9a74e-114">例如，下列運算式會建構 `Record(a int, b string, c int)`型別的值。</span><span class="sxs-lookup"><span data-stu-id="9a74e-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="9a74e-115">如果您沒有提供資料列建構函式中運算式的別名，Entity Framework 將會嘗試產生一個別名。</span><span class="sxs-lookup"><span data-stu-id="9a74e-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="9a74e-116">如需詳細資訊，請參閱 [識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) 主題中的＜別名規則＞章節。</span><span class="sxs-lookup"><span data-stu-id="9a74e-116">For more information, see the "Aliasing Rules" section of the [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="9a74e-117">下列規則適用於資料列建構函式中的運算式別名：</span><span class="sxs-lookup"><span data-stu-id="9a74e-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="9a74e-118">資料列建構函式中的運算式不可參考同一個建構函式中的其他別名。</span><span class="sxs-lookup"><span data-stu-id="9a74e-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="9a74e-119">同一個資料列建構函式中的兩個運算式不能有相同的別名。</span><span class="sxs-lookup"><span data-stu-id="9a74e-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="9a74e-120">如需有關查詢建構函式的詳細資訊，請參閱 <<c0> [ 建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9a74e-120">For more information about query constructors, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a74e-121">範例</span><span class="sxs-lookup"><span data-stu-id="9a74e-121">Example</span></span>  
 <span data-ttu-id="9a74e-122">下列 Entity SQL 查詢使用 ROW 運算子來建構匿名、結構式型別的記錄。</span><span class="sxs-lookup"><span data-stu-id="9a74e-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="9a74e-123">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="9a74e-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9a74e-124">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="9a74e-124">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9a74e-125">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="9a74e-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="9a74e-126">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="9a74e-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="9a74e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a74e-127">See also</span></span>

- [<span data-ttu-id="9a74e-128">建構類型</span><span class="sxs-lookup"><span data-stu-id="9a74e-128">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="9a74e-129">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9a74e-129">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="9a74e-130">類型定義</span><span class="sxs-lookup"><span data-stu-id="9a74e-130">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
