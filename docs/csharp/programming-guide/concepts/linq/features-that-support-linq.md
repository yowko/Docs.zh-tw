---
title: 支援 LINQ 的 C# 功能
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f1c045ffe311dfad851c7cace37966d8d42a22cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325204"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="c3b54-102">支援 LINQ 的 C# 功能</span><span class="sxs-lookup"><span data-stu-id="c3b54-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="c3b54-103">下節將介紹 C# 3.0 中引進的新語言建構。</span><span class="sxs-lookup"><span data-stu-id="c3b54-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="c3b54-104">雖然這些新功能或多或少都會用於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢，但不限於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，還可用於任何您認為實用的內容中。</span><span class="sxs-lookup"><span data-stu-id="c3b54-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="c3b54-105">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="c3b54-105">Query Expressions</span></span>  
 <span data-ttu-id="c3b54-106">查詢運算式使用類似於 SQL 或 XQuery 的宣告式語法來查詢 IEnumerable 集合。</span><span class="sxs-lookup"><span data-stu-id="c3b54-106">Queries expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="c3b54-107">在編譯時期，查詢語法會轉換成對 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者實作的標準查詢運算子擴充方法進行的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c3b54-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="c3b54-108">應用程式使用 `using` 指示詞來指定適當的命名空間，藉此控制範圍內的標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="c3b54-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="c3b54-109">下列查詢運算式會擷取字串的陣列，然後根據字串的第一個字元分組字串，再排序這些群組。</span><span class="sxs-lookup"><span data-stu-id="c3b54-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="c3b54-110">如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b54-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="c3b54-111">隱含型別變數 (var)</span><span class="sxs-lookup"><span data-stu-id="c3b54-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="c3b54-112">除了在宣告和初始化變數時明確指定類型，您還可以使用 [var](../../../../csharp/language-reference/keywords/var.md) 修飾詞，指示編譯器推斷並指派類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3b54-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="c3b54-113">宣告為 `var` 的變數和明確指定類型的變數一樣具有強型別。</span><span class="sxs-lookup"><span data-stu-id="c3b54-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="c3b54-114">`var` 可用來建立匿名型別，但也可用於任何區域變數。</span><span class="sxs-lookup"><span data-stu-id="c3b54-114">The use of `var` makes it possible to create anonymous types, but it can be used for any local variable.</span></span> <span data-ttu-id="c3b54-115">陣列也可以使用隱含型別進行宣告。</span><span class="sxs-lookup"><span data-stu-id="c3b54-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="c3b54-116">如需詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b54-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="c3b54-117">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="c3b54-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="c3b54-118">物件和集合初始設定式可以初始化物件，而不需要明確呼叫物件的建構函式。</span><span class="sxs-lookup"><span data-stu-id="c3b54-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="c3b54-119">初始設定式通常會用於將來源資料投影為新資料類型的查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="c3b54-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="c3b54-120">假設有個名為 `Customer` 的類別具有公用的 `Name` 和 `Phone` 屬性，則可如下列程式碼所示使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="c3b54-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="c3b54-121">如需詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b54-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="c3b54-122">匿名類型</span><span class="sxs-lookup"><span data-stu-id="c3b54-122">Anonymous Types</span></span>  
 <span data-ttu-id="c3b54-123">匿名型別是由編譯器所建構，只有編譯器才知道類型名稱。</span><span class="sxs-lookup"><span data-stu-id="c3b54-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="c3b54-124">匿名型別提供了一個便利的方法，暫時將查詢結果中的一組屬性分組，而不需要另外定義具名類型。</span><span class="sxs-lookup"><span data-stu-id="c3b54-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="c3b54-125">匿名型別是以新的運算式和物件初始設定式進行初始化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3b54-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="c3b54-126">如需詳細資訊，請參閱[匿名型別](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b54-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="c3b54-127">擴充方法</span><span class="sxs-lookup"><span data-stu-id="c3b54-127">Extension Methods</span></span>  
 <span data-ttu-id="c3b54-128">擴充方法是一種可以與類型相關聯的靜態方法，因此可以像呼叫類型上的執行個體方法一樣呼叫它。</span><span class="sxs-lookup"><span data-stu-id="c3b54-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="c3b54-129">這項功能實際上可讓您「新增」方法至現有的類型，而不需要實際修改這些類型。</span><span class="sxs-lookup"><span data-stu-id="c3b54-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="c3b54-130">標準查詢運算子是一組擴充方法，可為實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何類型提供 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢功能。</span><span class="sxs-lookup"><span data-stu-id="c3b54-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="c3b54-131">如需詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b54-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="c3b54-132">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="c3b54-132">Lambda Expressions</span></span>  
 <span data-ttu-id="c3b54-133">Lambda 運算式是一種內嵌函式，其使用 => 運算子分隔輸入參數與函式主體，而且可以在編譯期間轉換成委派或運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c3b54-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="c3b54-134">在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 程式設計中，當您直接對標準查詢運算子進行方法呼叫時，就會遇到 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c3b54-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="c3b54-135">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="c3b54-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c3b54-136">匿名函式</span><span class="sxs-lookup"><span data-stu-id="c3b54-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="c3b54-137">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="c3b54-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="c3b54-138">運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="c3b54-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="c3b54-139">自動實作的屬性</span><span class="sxs-lookup"><span data-stu-id="c3b54-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="c3b54-140">自動實作的屬性讓屬性宣告更簡潔。</span><span class="sxs-lookup"><span data-stu-id="c3b54-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="c3b54-141">當您如下列範例所示宣告屬性時，編譯器會建立私用、匿名的支援欄位，只能透過 getter 和 setter 屬性進行存取。</span><span class="sxs-lookup"><span data-stu-id="c3b54-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="c3b54-142">如需詳細資訊，請參閱[自動實作的屬性](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b54-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b54-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3b54-143">See Also</span></span>  
 [<span data-ttu-id="c3b54-144">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c3b54-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
