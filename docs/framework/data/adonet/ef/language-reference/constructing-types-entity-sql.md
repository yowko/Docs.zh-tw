---
title: "建構類型 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a10ac4f8b89259c7d5ff46ad99ad6c8a925726d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="ecaa0-102">建構類型 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ecaa0-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ecaa0-103">提供三種建構函式： 資料列建構函式、 具名型別建構函式和集合建構函式。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-103"> provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="ecaa0-104">資料列建構函式</span><span class="sxs-lookup"><span data-stu-id="ecaa0-104">Row Constructors</span></span>  
 <span data-ttu-id="ecaa0-105">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中使用資料列建構函式，可以從一個或多個值建構匿名、結構式具型別的記錄。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="ecaa0-106">資料列建構函式的結果型別是資料列型別，而且它的欄位型別會對應到用於建構資料列的值的型別。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="ecaa0-107">例如，下列運算式會建構類型的值`Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="ecaa0-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="ecaa0-108">如果您沒有提供資料列建構函式中運算式的別名，Entity Framework 將會嘗試產生一個別名。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="ecaa0-109">如需詳細資訊，請參閱中的 < 別名規則 > 一節[識別碼](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ecaa0-110">下列規則適用於資料列建構函式中的運算式別名：</span><span class="sxs-lookup"><span data-stu-id="ecaa0-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="ecaa0-111">資料列建構函式中的運算式不可參考同一個建構函式中的其他別名。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="ecaa0-112">同一個資料列建構函式中的兩個運算式不能有相同的別名。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="ecaa0-113">如需資料列建構函式的詳細資訊，請參閱[列](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="ecaa0-114">集合建構函式</span><span class="sxs-lookup"><span data-stu-id="ecaa0-114">Collection Constructors</span></span>  
 <span data-ttu-id="ecaa0-115">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中使用集合建構函式，可以從值清單建立多重集 (Multiset) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="ecaa0-116">建構函式中的所有值都必須是相容的型別 `T`，而且建構函式會產生型別 `Multiset<T>` 的集合。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="ecaa0-117">例如，下列運算式會建立整數的集合：</span><span class="sxs-lookup"><span data-stu-id="ecaa0-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="ecaa0-118">空白的多重集建構函式是不被允許的，因為這樣無法判斷項目的型別。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="ecaa0-119">以下程式碼行是無效的：</span><span class="sxs-lookup"><span data-stu-id="ecaa0-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="ecaa0-120">如需詳細資訊，請參閱[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="ecaa0-121">具名型別建構函式 (NamedType 初始設定式)</span><span class="sxs-lookup"><span data-stu-id="ecaa0-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ecaa0-122"> 可以讓型別建構函式 (初始設定式) 建立具名複雜類型和實體類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-122"> allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="ecaa0-123">例如，下列運算式會建立 `Person` 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="ecaa0-124">下列運算式會建立複雜類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="ecaa0-125">下列運算式會建立巢狀複雜類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="ecaa0-126">下列運算式會建立具有巢狀複雜類型之實體的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="ecaa0-127">下列範例顯示如何將複雜類型的屬性 (Property) 初始化為 null。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="ecaa0-128">建構函式的引數順序，會假設與型別屬性 (Attribute) 宣告中的順序相同。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="ecaa0-129">如需詳細資訊，請參閱[具名類型建構函式](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ecaa0-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecaa0-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecaa0-130">See Also</span></span>  
 [<span data-ttu-id="ecaa0-131">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="ecaa0-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="ecaa0-132">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="ecaa0-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="ecaa0-133">類型系統</span><span class="sxs-lookup"><span data-stu-id="ecaa0-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
