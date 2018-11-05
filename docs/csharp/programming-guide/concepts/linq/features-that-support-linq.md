---
title: 支援 LINQ 的 C# 功能
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 51cc24fd8054b87b6c92a02450420a9c4abef525
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50191086"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="7fcd4-102">支援 LINQ 的 C# 功能</span><span class="sxs-lookup"><span data-stu-id="7fcd4-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="7fcd4-103">下節將介紹 C# 3.0 中引進的新語言建構。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="7fcd4-104">雖然這些新功能或多或少都會用於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢，但不限於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，還可用於任何您認為實用的內容中。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="7fcd4-105">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="7fcd4-105">Query Expressions</span></span>  
 <span data-ttu-id="7fcd4-106">查詢運算式使用類似 SQL 或 XQuery 的宣告式語法來查詢 IEnumerable 集合。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="7fcd4-107">在編譯時期，查詢語法會轉換成對 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者實作的標準查詢運算子擴充方法進行的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="7fcd4-108">應用程式使用 `using` 指示詞來指定適當的命名空間，藉此控制範圍內的標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="7fcd4-109">下列查詢運算式會擷取字串的陣列，然後根據字串的第一個字元分組字串，再排序這些群組。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```csharp  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="7fcd4-110">如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="7fcd4-111">隱含型別變數 (var)</span><span class="sxs-lookup"><span data-stu-id="7fcd4-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="7fcd4-112">除了在宣告和初始化變數時明確指定類型，您還可以使用 [var](../../../../csharp/language-reference/keywords/var.md) 修飾詞，指示編譯器推斷並指派類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7fcd4-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```csharp  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="7fcd4-113">宣告為 `var` 的變數和明確指定類型的變數一樣具有強型別。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="7fcd4-114">`var` 可用來建立匿名型別，但僅可用於區域變數。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="7fcd4-115">陣列也可以使用隱含型別進行宣告。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="7fcd4-116">如需詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="7fcd4-117">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="7fcd4-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="7fcd4-118">物件和集合初始設定式可以初始化物件，而不需要明確呼叫物件的建構函式。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="7fcd4-119">初始設定式通常會用於將來源資料投影為新資料類型的查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="7fcd4-120">假設有個名為 `Customer` 的類別具有公用的 `Name` 和 `Phone` 屬性，則可如下列程式碼所示使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="7fcd4-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```csharp  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
<span data-ttu-id="7fcd4-121">延續我們的 `Customer` 類別，假設有一個稱為 `IncomingOrders` 的資料來源，而其每個訂單都有大型的 `OrderSize`，我們想要根據該訂單建立新的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="7fcd4-122">您可以針對此資料來源執行 LINQ 查詢，並使用物件初始化來填滿集合：</span><span class="sxs-lookup"><span data-stu-id="7fcd4-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>
```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```
<span data-ttu-id="7fcd4-123">資料來源底下可能有比 `Customer` 類別更多的屬性 (例如 `OrderSize`)，但使用物件初始化時，從查詢傳回的資料會塑造為我們想要的資料型別；我們選擇與我們的類別相關的資料。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="7fcd4-124">因此，我們現在有使用新的 `Customer` 填滿的 `IEnumerable`，這正是我們所需要的。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="7fcd4-125">上述內容也可以使用 LINQ 的方法語法撰寫：</span><span class="sxs-lookup"><span data-stu-id="7fcd4-125">The above can also be written in LINQ's method syntax:</span></span>
```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```
 <span data-ttu-id="7fcd4-126">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="7fcd4-126">For more information, see:</span></span>
 
 - [<span data-ttu-id="7fcd4-127">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="7fcd4-127">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

 - [<span data-ttu-id="7fcd4-128">標準查詢運算子的查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="7fcd4-128">Query Expression Syntax for Standard Query Operators</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="7fcd4-129">匿名類型</span><span class="sxs-lookup"><span data-stu-id="7fcd4-129">Anonymous Types</span></span>  
 <span data-ttu-id="7fcd4-130">匿名型別是由編譯器所建構，只有編譯器才知道類型名稱。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="7fcd4-131">匿名型別提供了一個便利的方法，暫時將查詢結果中的一組屬性分組，而不需要另外定義具名類型。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="7fcd4-132">匿名型別是以新的運算式和物件初始設定式進行初始化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7fcd4-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```csharp
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="7fcd4-133">如需詳細資訊，請參閱[匿名型別](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-133">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="7fcd4-134">擴充方法</span><span class="sxs-lookup"><span data-stu-id="7fcd4-134">Extension Methods</span></span>  
 <span data-ttu-id="7fcd4-135">擴充方法是一種可以與類型相關聯的靜態方法，因此可以像呼叫類型上的執行個體方法一樣呼叫它。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="7fcd4-136">此功能實際上可讓您「新增」方法至現有的類型，而不需要實際修改這些類型。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="7fcd4-137">標準查詢運算子是一組擴充方法，可為實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何類型提供 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢功能。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-137">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="7fcd4-138">如需詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-138">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="7fcd4-139">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="7fcd4-139">Lambda Expressions</span></span>  
 <span data-ttu-id="7fcd4-140">Lambda 運算式是一種內嵌函式，其使用 => 運算子分隔輸入參數與函式主體，而且可以在編譯期間轉換成委派或運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="7fcd4-141">在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 程式設計中，當您直接對標準查詢運算子進行方法呼叫時，就會遇到 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="7fcd4-141">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="7fcd4-142">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="7fcd4-142">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcd4-143">匿名函式</span><span class="sxs-lookup"><span data-stu-id="7fcd4-143">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="7fcd4-144">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="7fcd4-144">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="7fcd4-145">運算式樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="7fcd4-145">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
   
## <a name="see-also"></a><span data-ttu-id="7fcd4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fcd4-146">See Also</span></span>

- [<span data-ttu-id="7fcd4-147">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7fcd4-147">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
