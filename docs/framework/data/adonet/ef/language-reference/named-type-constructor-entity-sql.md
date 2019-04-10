---
title: 具名類型建構函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f95f0dcb92068675b2efff0af7e97b349976bf42
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329462"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="da65b-102">具名類型建構函式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="da65b-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="da65b-103">用於建立概念模型名義型別 (例如實體類型或複雜類型) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="da65b-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da65b-104">語法</span><span class="sxs-lookup"><span data-stu-id="da65b-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="da65b-105">引數</span><span class="sxs-lookup"><span data-stu-id="da65b-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="da65b-106">為簡單或引號識別項的值。</span><span class="sxs-lookup"><span data-stu-id="da65b-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="da65b-107">如需詳細資訊，請參閱[識別碼](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="da65b-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="da65b-108">型別的屬性，假設與它們出現在型別宣告中的順序相同。</span><span class="sxs-lookup"><span data-stu-id="da65b-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da65b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="da65b-109">Return Value</span></span>  
 <span data-ttu-id="da65b-110">具名複雜類型和實體類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="da65b-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da65b-111">備註</span><span class="sxs-lookup"><span data-stu-id="da65b-111">Remarks</span></span>  
 <span data-ttu-id="da65b-112">以下範例示範如何建構名義和複雜類型。</span><span class="sxs-lookup"><span data-stu-id="da65b-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="da65b-113">下面的運算式會建立 `Person` 型別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="da65b-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="da65b-114">下面的運算式會建立複雜類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="da65b-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="da65b-115">下面的運算式會建立巢狀複雜類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="da65b-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="da65b-116">下面的運算式會建立具有巢狀複雜類型之實體的執行個體：</span><span class="sxs-lookup"><span data-stu-id="da65b-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="da65b-117">下列範例示範如何初始化為 null 的複雜類型的屬性：</span><span class="sxs-lookup"><span data-stu-id="da65b-117">The following example shows how to initialize a property of a complex type to null:</span></span>`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a><span data-ttu-id="da65b-118">範例</span><span class="sxs-lookup"><span data-stu-id="da65b-118">Example</span></span>  
 <span data-ttu-id="da65b-119">以下 Entity SQL 查詢使用具名型別建構函式來建立概念模型型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="da65b-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="da65b-120">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="da65b-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="da65b-121">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="da65b-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="da65b-122">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="da65b-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="da65b-123">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="da65b-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="da65b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da65b-124">See also</span></span>

- [<span data-ttu-id="da65b-125">建構類型</span><span class="sxs-lookup"><span data-stu-id="da65b-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="da65b-126">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="da65b-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
