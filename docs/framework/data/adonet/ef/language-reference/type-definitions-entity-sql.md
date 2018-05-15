---
title: 類型定義 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7abbe5dfed005a10955a385cadf12725a9450512
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="cbd51-102">類型定義 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cbd51-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="cbd51-103">型別定義用於 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 內嵌函式中的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="cbd51-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd51-104">備註</span><span class="sxs-lookup"><span data-stu-id="cbd51-104">Remarks</span></span>  
 <span data-ttu-id="cbd51-105">內嵌函式的宣告陳述式組成[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)關鍵字後面接著表示函式名稱 (例如，"MyAvg")，後面接著以括號 （適用於在參數定義清單的識別項例如"dues Collection(Decimal)")。</span><span class="sxs-lookup"><span data-stu-id="cbd51-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="cbd51-106">參數定義清單包括零或多個參數定義。</span><span class="sxs-lookup"><span data-stu-id="cbd51-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="cbd51-107">每個參數定義包括一個識別項 (函式參數的名稱，例如 "dues")，後面接型別定義 (例如 "Collection(Decimal)")。</span><span class="sxs-lookup"><span data-stu-id="cbd51-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="cbd51-108">型別定義可以是下面其中一項：</span><span class="sxs-lookup"><span data-stu-id="cbd51-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="cbd51-109">識別項的型別 (例如 "Int32" 或 "AdventureWorks.Order")。</span><span class="sxs-lookup"><span data-stu-id="cbd51-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="cbd51-110">關鍵字 `COLLECTION` 後面接以括號括住的其他型別定義 (例如 "Collection(AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="cbd51-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="cbd51-111">關鍵字 ROW 後面接以括號括住的屬性定義清單 (例如 "Row(x AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="cbd51-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="cbd51-112">屬性定義具有格式，例如"`identifier type_definition`， `identifier type_definition`，..."。</span><span class="sxs-lookup"><span data-stu-id="cbd51-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="cbd51-113">關鍵字 REF 後面接以括號括住的識別項型別 (例如 "Ref(AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="cbd51-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="cbd51-114">REF 型別定義運算子需要實體類型做為引數。</span><span class="sxs-lookup"><span data-stu-id="cbd51-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="cbd51-115">您不能指定基本型別做為引數。</span><span class="sxs-lookup"><span data-stu-id="cbd51-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="cbd51-116">您也可以巢狀化型別定義 (例如 "Collection(Row(x Ref(AdventureWorks.Order)))")。</span><span class="sxs-lookup"><span data-stu-id="cbd51-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="cbd51-117">型別定義的選項是：</span><span class="sxs-lookup"><span data-stu-id="cbd51-117">The type definition options are:</span></span>  
  
-   <span data-ttu-id="cbd51-118">`IdentifierName supported_type` 或</span><span class="sxs-lookup"><span data-stu-id="cbd51-118">`IdentifierName supported_type`, or</span></span>  
  
-   <span data-ttu-id="cbd51-119">`IdentifierName` COLLECTION(`type_definition`)，或</span><span class="sxs-lookup"><span data-stu-id="cbd51-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
-   <span data-ttu-id="cbd51-120">`IdentifierName` ROW(`property_definition`)，或</span><span class="sxs-lookup"><span data-stu-id="cbd51-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
-   <span data-ttu-id="cbd51-121">`IdentifierName` REF(`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="cbd51-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="cbd51-122">屬性定義的選項是 `IdentifierName type_definition`。</span><span class="sxs-lookup"><span data-stu-id="cbd51-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="cbd51-123">支援的型別是目前命名空間中的任何型別。</span><span class="sxs-lookup"><span data-stu-id="cbd51-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="cbd51-124">這些包括基本型別和實體類型兩者。</span><span class="sxs-lookup"><span data-stu-id="cbd51-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="cbd51-125">支援的實體類型只會參考目前命名空間中的實體類型。</span><span class="sxs-lookup"><span data-stu-id="cbd51-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="cbd51-126">不包括基本型別。</span><span class="sxs-lookup"><span data-stu-id="cbd51-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cbd51-127">範例</span><span class="sxs-lookup"><span data-stu-id="cbd51-127">Examples</span></span>  
 <span data-ttu-id="cbd51-128">下面是一個簡單的型別定義範例：</span><span class="sxs-lookup"><span data-stu-id="cbd51-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="cbd51-129">下面是一個 COLLECTION 型別定義的範例：</span><span class="sxs-lookup"><span data-stu-id="cbd51-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="cbd51-130">下面是一個 ROW 型別定義的範例：</span><span class="sxs-lookup"><span data-stu-id="cbd51-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="cbd51-131">下面是一個 REF 型別定義的範例。</span><span class="sxs-lookup"><span data-stu-id="cbd51-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbd51-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbd51-132">See Also</span></span>  
 [<span data-ttu-id="cbd51-133">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="cbd51-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="cbd51-134">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="cbd51-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
