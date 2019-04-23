---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 51de041a4b06d5da31071ea2b3cb31c86feff137
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294441"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="84268-102">CAST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="84268-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="84268-103">將一種資料類型的運算式轉換成另一種。</span><span class="sxs-lookup"><span data-stu-id="84268-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84268-104">語法</span><span class="sxs-lookup"><span data-stu-id="84268-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="84268-105">引數</span><span class="sxs-lookup"><span data-stu-id="84268-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="84268-106">可以轉換為 `data_type`的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="84268-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="84268-107">目標系統提供的資料型別。</span><span class="sxs-lookup"><span data-stu-id="84268-107">The target system-supplied data type.</span></span> <span data-ttu-id="84268-108">它必須是基本 (純量) 型別。</span><span class="sxs-lookup"><span data-stu-id="84268-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="84268-109">使用的 `data_type` 視查詢空間而定。</span><span class="sxs-lookup"><span data-stu-id="84268-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="84268-110">如果查詢是以 <xref:System.Data.EntityClient.EntityCommand>執行的，資料型別會是在概念模型中定義的型別。</span><span class="sxs-lookup"><span data-stu-id="84268-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="84268-111">如需詳細資訊，請參閱 [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="84268-111">For more information, see [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span> <span data-ttu-id="84268-112">如果查詢是以 <xref:System.Data.Objects.ObjectQuery%601>執行的，則資料型別為 Common Language Runtime (CLR) 型別。</span><span class="sxs-lookup"><span data-stu-id="84268-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84268-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="84268-113">Return Value</span></span>  
 <span data-ttu-id="84268-114">傳回 `data_type`的相同值。</span><span class="sxs-lookup"><span data-stu-id="84268-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84268-115">備註</span><span class="sxs-lookup"><span data-stu-id="84268-115">Remarks</span></span>  
 <span data-ttu-id="84268-116">轉型運算式的語意很類似 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT 運算式。</span><span class="sxs-lookup"><span data-stu-id="84268-116">The cast expression has similar semantics to the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT expression.</span></span> <span data-ttu-id="84268-117">轉型運算式是用來將某個型別的值轉換成另一個型別的值。</span><span class="sxs-lookup"><span data-stu-id="84268-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="84268-118">如果 e 為 S 型別，且 S 可轉換成 T，則上述運算式便是有效的轉型運算式。</span><span class="sxs-lookup"><span data-stu-id="84268-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="84268-119">T 必須是基本 (純量) 型別。</span><span class="sxs-lookup"><span data-stu-id="84268-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="84268-120">轉型為 `Edm.Decimal`時可選擇性提供有效位數和小數位數 Facet 的值。</span><span class="sxs-lookup"><span data-stu-id="84268-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="84268-121">如果沒有明確提供，則有效位數和小數位數的預設值將分別為 18 和 0。</span><span class="sxs-lookup"><span data-stu-id="84268-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="84268-122">更明確地講，下列多載支援 `Decimal`：</span><span class="sxs-lookup"><span data-stu-id="84268-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="84268-123">使用轉型運算式會視為明確轉換。</span><span class="sxs-lookup"><span data-stu-id="84268-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="84268-124">而明確轉換可能會截斷資料或遺失有效位數。</span><span class="sxs-lookup"><span data-stu-id="84268-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84268-125">只有在基本型別和列舉成員型別上能支援 CAST。</span><span class="sxs-lookup"><span data-stu-id="84268-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84268-126">範例</span><span class="sxs-lookup"><span data-stu-id="84268-126">Example</span></span>  
 <span data-ttu-id="84268-127">下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 CAST 運算子將某個資料型別的運算式轉型為另一個資料型別。</span><span class="sxs-lookup"><span data-stu-id="84268-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="84268-128">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="84268-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="84268-129">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="84268-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="84268-130">請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="84268-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="84268-131">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="84268-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="84268-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84268-132">See also</span></span>

- [<span data-ttu-id="84268-133">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="84268-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
