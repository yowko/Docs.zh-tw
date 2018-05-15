---
title: 具名類型建構函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 9ffaf55ed54e8479a56e6f9fc4d7a5efe47f8e2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="44cb9-102">具名類型建構函式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="44cb9-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="44cb9-103">用於建立概念模型名義型別 (例如實體類型或複雜類型) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="44cb9-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44cb9-104">語法</span><span class="sxs-lookup"><span data-stu-id="44cb9-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="44cb9-105">引數</span><span class="sxs-lookup"><span data-stu-id="44cb9-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="44cb9-106">為簡單或引號識別項的值。</span><span class="sxs-lookup"><span data-stu-id="44cb9-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="44cb9-107">如需詳細資訊，請參閱[識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="44cb9-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="44cb9-108">型別的屬性，假設與它們出現在型別宣告中的順序相同。</span><span class="sxs-lookup"><span data-stu-id="44cb9-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44cb9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="44cb9-109">Return Value</span></span>  
 <span data-ttu-id="44cb9-110">具名複雜類型和實體類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="44cb9-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44cb9-111">備註</span><span class="sxs-lookup"><span data-stu-id="44cb9-111">Remarks</span></span>  
 <span data-ttu-id="44cb9-112">以下範例示範如何建構名義和複雜類型。</span><span class="sxs-lookup"><span data-stu-id="44cb9-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="44cb9-113">下面的運算式會建立 `Person` 型別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="44cb9-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="44cb9-114">下面的運算式會建立複雜類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="44cb9-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="44cb9-115">下面的運算式會建立巢狀複雜類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="44cb9-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="44cb9-116">下面的運算式會建立具有巢狀複雜類型之實體的執行個體：</span><span class="sxs-lookup"><span data-stu-id="44cb9-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="44cb9-117">以下範例示範如何將複雜類型的屬性初始化為：`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="44cb9-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="44cb9-118">範例</span><span class="sxs-lookup"><span data-stu-id="44cb9-118">Example</span></span>  
 <span data-ttu-id="44cb9-119">以下 Entity SQL 查詢使用具名型別建構函式來建立概念模型型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="44cb9-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="44cb9-120">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="44cb9-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="44cb9-121">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="44cb9-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="44cb9-122">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="44cb9-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="44cb9-123">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="44cb9-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="44cb9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44cb9-124">See Also</span></span>  
 [<span data-ttu-id="44cb9-125">建構類型</span><span class="sxs-lookup"><span data-stu-id="44cb9-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="44cb9-126">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="44cb9-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
