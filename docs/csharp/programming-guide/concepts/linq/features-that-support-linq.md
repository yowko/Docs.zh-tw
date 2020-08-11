---
title: 支援 LINQ 的 C# 功能
description: '瞭解搭配 LINQ 查詢和其他內容使用的 c # 功能。 這些語言結構是在 c # 3.0 中引進。'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 13254c69193e04ffcf11e3e23f1deb460063a6c1
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063688"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="c489c-104">支援 LINQ 的 C# 功能</span><span class="sxs-lookup"><span data-stu-id="c489c-104">C# Features That Support LINQ</span></span>

<span data-ttu-id="c489c-105">下節將介紹 C# 3.0 中引進的新語言建構。</span><span class="sxs-lookup"><span data-stu-id="c489c-105">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="c489c-106">雖然這些新功能全都適用于 LINQ 查詢的程度，但它們並不限於 LINQ，而且可以在任何您覺得有用的內容中使用。</span><span class="sxs-lookup"><span data-stu-id="c489c-106">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="c489c-107">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="c489c-107">Query Expressions</span></span>

<span data-ttu-id="c489c-108">查詢運算式使用類似 SQL 或 XQuery 的宣告式語法來查詢 IEnumerable 集合。</span><span class="sxs-lookup"><span data-stu-id="c489c-108">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="c489c-109">在編譯時期，查詢語法會轉換成 LINQ 提供者的標準查詢運算子擴充方法的實作為方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c489c-109">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="c489c-110">應用程式使用 `using` 指示詞來指定適當的命名空間，藉此控制範圍內的標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="c489c-110">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="c489c-111">下列查詢運算式會擷取字串的陣列，然後根據字串的第一個字元分組字串，再排序這些群組。</span><span class="sxs-lookup"><span data-stu-id="c489c-111">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="c489c-112">如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c489c-112">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="c489c-113">隱含型別變數 (var)</span><span class="sxs-lookup"><span data-stu-id="c489c-113">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="c489c-114">除了在宣告和初始化變數時明確指定類型，您還可以使用 [var](../../../language-reference/keywords/var.md) 修飾詞，指示編譯器推斷並指派類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c489c-114">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="c489c-115">宣告為的變數，與 `var` 您明確指定類型的變數一樣強型別。</span><span class="sxs-lookup"><span data-stu-id="c489c-115">Variables declared as `var` are just as strongly typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="c489c-116">`var` 可用來建立匿名型別，但僅可用於區域變數。</span><span class="sxs-lookup"><span data-stu-id="c489c-116">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="c489c-117">陣列也可以使用隱含型別進行宣告。</span><span class="sxs-lookup"><span data-stu-id="c489c-117">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="c489c-118">如需詳細資訊，請參閱[隱含型別區域變數](../../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c489c-118">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="c489c-119">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="c489c-119">Object and Collection Initializers</span></span>

<span data-ttu-id="c489c-120">物件和集合初始設定式可以初始化物件，而不需要明確呼叫物件的建構函式。</span><span class="sxs-lookup"><span data-stu-id="c489c-120">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="c489c-121">初始設定式通常會用於將來源資料投影為新資料類型的查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="c489c-121">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="c489c-122">假設有個名為 `Customer` 的類別具有公用的 `Name` 和 `Phone` 屬性，則可如下列程式碼所示使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="c489c-122">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="c489c-123">延續我們的 `Customer` 類別，假設有一個稱為 `IncomingOrders` 的資料來源，而其每個訂單都有大型的 `OrderSize`，我們想要根據該訂單建立新的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="c489c-123">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="c489c-124">您可以針對此資料來源執行 LINQ 查詢，並使用物件初始化來填滿集合：</span><span class="sxs-lookup"><span data-stu-id="c489c-124">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="c489c-125">資料來源底下可能有比 `Customer` 類別更多的屬性 (例如 `OrderSize`)，但使用物件初始化時，從查詢傳回的資料會塑造為我們想要的資料型別；我們選擇與我們的類別相關的資料。</span><span class="sxs-lookup"><span data-stu-id="c489c-125">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="c489c-126">因此，我們現在有使用新的 `Customer` 填滿的 `IEnumerable`，這正是我們所需要的。</span><span class="sxs-lookup"><span data-stu-id="c489c-126">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="c489c-127">上述內容也可以使用 LINQ 的方法語法撰寫：</span><span class="sxs-lookup"><span data-stu-id="c489c-127">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="c489c-128">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="c489c-128">For more information, see:</span></span>

- [<span data-ttu-id="c489c-129">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="c489c-129">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="c489c-130">標準查詢運算子的查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="c489c-130">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="c489c-131">匿名類型</span><span class="sxs-lookup"><span data-stu-id="c489c-131">Anonymous Types</span></span>

<span data-ttu-id="c489c-132">匿名型別是由編譯器所建構，只有編譯器才知道類型名稱。</span><span class="sxs-lookup"><span data-stu-id="c489c-132">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="c489c-133">匿名型別提供了一個便利的方法，暫時將查詢結果中的一組屬性分組，而不需要另外定義具名類型。</span><span class="sxs-lookup"><span data-stu-id="c489c-133">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="c489c-134">匿名型別是以新的運算式和物件初始設定式進行初始化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c489c-134">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="c489c-135">如需詳細資訊，請參閱[匿名](../../classes-and-structs/anonymous-types.md)型別。</span><span class="sxs-lookup"><span data-stu-id="c489c-135">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="c489c-136">擴充方法</span><span class="sxs-lookup"><span data-stu-id="c489c-136">Extension Methods</span></span>

<span data-ttu-id="c489c-137">擴充方法是一種可以與類型相關聯的靜態方法，因此可以像呼叫類型上的執行個體方法一樣呼叫它。</span><span class="sxs-lookup"><span data-stu-id="c489c-137">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="c489c-138">這項功能實際上可讓您「新增」方法至現有的類型，而不需要實際修改這些類型。</span><span class="sxs-lookup"><span data-stu-id="c489c-138">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="c489c-139">標準查詢運算子是一組擴充方法，可為任何可執行檔型別提供 LINQ 查詢功能 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="c489c-139">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="c489c-140">如需詳細資訊，請參閱[擴充方法](../../classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c489c-140">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="c489c-141">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="c489c-141">Lambda Expressions</span></span>

<span data-ttu-id="c489c-142">Lambda 運算式是一種內嵌函式，其使用 => 運算子分隔輸入參數與函式主體，而且可以在編譯期間轉換成委派或運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c489c-142">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="c489c-143">在 LINQ 程式設計中，當您對標準查詢運算子進行直接方法呼叫時，將會遇到 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c489c-143">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="c489c-144">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="c489c-144">For more information, see:</span></span>

- [<span data-ttu-id="c489c-145">匿名函式</span><span class="sxs-lookup"><span data-stu-id="c489c-145">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="c489c-146">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="c489c-146">Lambda Expressions</span></span>](../../../language-reference/operators/lambda-expressions.md)

- [<span data-ttu-id="c489c-147">運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="c489c-147">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="c489c-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c489c-148">See also</span></span>

- [<span data-ttu-id="c489c-149">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c489c-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
