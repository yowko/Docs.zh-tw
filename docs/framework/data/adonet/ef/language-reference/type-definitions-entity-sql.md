---
title: "類型定義 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 269d0b7942a949b899a445af0fc15502e0ae3f7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="d988e-102">類型定義 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d988e-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="d988e-103">型別定義用於 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 內嵌函式中的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="d988e-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d988e-104">備註</span><span class="sxs-lookup"><span data-stu-id="d988e-104">Remarks</span></span>  
 <span data-ttu-id="d988e-105">內嵌函式的宣告陳述式組成[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)關鍵字後面接著表示函式名稱 (例如，"MyAvg")，後面接著以括號 （適用於在參數定義清單的識別項例如"dues Collection(Decimal)")。</span><span class="sxs-lookup"><span data-stu-id="d988e-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="d988e-106">參數定義清單包括零或多個參數定義。</span><span class="sxs-lookup"><span data-stu-id="d988e-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="d988e-107">每個參數定義包括一個識別項 (函式參數的名稱，例如 "dues")，後面接型別定義 (例如 "Collection(Decimal)")。</span><span class="sxs-lookup"><span data-stu-id="d988e-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="d988e-108">型別定義可以是下面其中一項：</span><span class="sxs-lookup"><span data-stu-id="d988e-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="d988e-109">識別項的型別 (例如 "Int32" 或 "AdventureWorks.Order")。</span><span class="sxs-lookup"><span data-stu-id="d988e-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="d988e-110">關鍵字 `COLLECTION` 後面接以括號括住的其他型別定義 (例如 "Collection(AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="d988e-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="d988e-111">關鍵字 ROW 後面接以括號括住的屬性定義清單 (例如 "Row(x AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="d988e-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="d988e-112">屬性定義具有格式，例如"`identifier type_definition`， `identifier type_definition`，..."。</span><span class="sxs-lookup"><span data-stu-id="d988e-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="d988e-113">關鍵字 REF 後面接以括號括住的識別項型別 (例如 "Ref(AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="d988e-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="d988e-114">REF 型別定義運算子需要實體類型做為引數。</span><span class="sxs-lookup"><span data-stu-id="d988e-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="d988e-115">您不能指定基本型別做為引數。</span><span class="sxs-lookup"><span data-stu-id="d988e-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="d988e-116">您也可以巢狀化型別定義 (例如 "Collection(Row(x Ref(AdventureWorks.Order)))")。</span><span class="sxs-lookup"><span data-stu-id="d988e-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="d988e-117">型別定義的選項是：</span><span class="sxs-lookup"><span data-stu-id="d988e-117">The type definition options are:</span></span>  
  
-   <span data-ttu-id="d988e-118">`IdentifierName supported_type` 或</span><span class="sxs-lookup"><span data-stu-id="d988e-118">`IdentifierName supported_type`, or</span></span>  
  
-   <span data-ttu-id="d988e-119">`IdentifierName` COLLECTION(`type_definition`)，或</span><span class="sxs-lookup"><span data-stu-id="d988e-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
-   <span data-ttu-id="d988e-120">`IdentifierName` ROW(`property_definition`)，或</span><span class="sxs-lookup"><span data-stu-id="d988e-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
-   <span data-ttu-id="d988e-121">`IdentifierName` REF(`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="d988e-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="d988e-122">屬性定義的選項是 `IdentifierName type_definition`。</span><span class="sxs-lookup"><span data-stu-id="d988e-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="d988e-123">支援的型別是目前命名空間中的任何型別。</span><span class="sxs-lookup"><span data-stu-id="d988e-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="d988e-124">這些包括基本型別和實體類型兩者。</span><span class="sxs-lookup"><span data-stu-id="d988e-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="d988e-125">支援的實體類型只會參考目前命名空間中的實體類型。</span><span class="sxs-lookup"><span data-stu-id="d988e-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="d988e-126">不包括基本型別。</span><span class="sxs-lookup"><span data-stu-id="d988e-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d988e-127">範例</span><span class="sxs-lookup"><span data-stu-id="d988e-127">Examples</span></span>  
 <span data-ttu-id="d988e-128">下面是一個簡單的型別定義範例：</span><span class="sxs-lookup"><span data-stu-id="d988e-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="d988e-129">下面是一個 COLLECTION 型別定義的範例：</span><span class="sxs-lookup"><span data-stu-id="d988e-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="d988e-130">下面是一個 ROW 型別定義的範例：</span><span class="sxs-lookup"><span data-stu-id="d988e-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="d988e-131">下面是一個 REF 型別定義的範例。</span><span class="sxs-lookup"><span data-stu-id="d988e-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="d988e-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="d988e-132">See Also</span></span>  
 [<span data-ttu-id="d988e-133">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="d988e-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="d988e-134">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="d988e-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
