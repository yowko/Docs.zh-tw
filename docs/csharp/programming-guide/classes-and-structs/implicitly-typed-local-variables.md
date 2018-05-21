---
title: 隱含類型區域變數 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: c6c2bae39764e78fad2510bbc8937b0ac790bef5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="4e46a-102">隱含類型區域變數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4e46a-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="4e46a-103">您可以宣告區域變數而不提供明確類型。</span><span class="sxs-lookup"><span data-stu-id="4e46a-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="4e46a-104">`var` 關鍵字會指示編譯器從初始化陳述式右側的運算式推斷變數的類型。</span><span class="sxs-lookup"><span data-stu-id="4e46a-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="4e46a-105">推斷類型可能是內建類型、匿名型別、使用者定義型別，或 .NET Framework 類別庫中定義的類型。</span><span class="sxs-lookup"><span data-stu-id="4e46a-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="4e46a-106">如需如何使用 `var` 初始化陣列的詳細資訊，請參閱[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="4e46a-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="4e46a-107">下列範例顯示可以使用 `var` 宣告區域變數的各種方法：</span><span class="sxs-lookup"><span data-stu-id="4e46a-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="4e46a-108">請務必了解 `var` 關鍵字不代表 "variant"，也不代表變數是不嚴格規定類型或晚期繫結的。</span><span class="sxs-lookup"><span data-stu-id="4e46a-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="4e46a-109">只代表編譯器會判斷並指派最適當的類型。</span><span class="sxs-lookup"><span data-stu-id="4e46a-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="4e46a-110">`var` 關鍵字可在下列內容中使用：</span><span class="sxs-lookup"><span data-stu-id="4e46a-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="4e46a-111">在區域變數 (方法範圍中宣告的變數) 上，如前述範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e46a-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="4e46a-112">在 [for](../../../csharp/language-reference/keywords/for.md) 初始化陳述式中。</span><span class="sxs-lookup"><span data-stu-id="4e46a-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="4e46a-113">在 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 初始化陳述式中。</span><span class="sxs-lookup"><span data-stu-id="4e46a-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="4e46a-114">在 [using](../../../csharp/language-reference/keywords/using-statement.md) 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="4e46a-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="4e46a-115">如需詳細資訊，請參閱[如何：在查詢運算式中使用隱含型別區域變數和陣列](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="4e46a-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="4e46a-116">var 和匿名型別</span><span class="sxs-lookup"><span data-stu-id="4e46a-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="4e46a-117">在許多情況下，使用 `var` 是選擇性的，只是為了在語法上便於使用。</span><span class="sxs-lookup"><span data-stu-id="4e46a-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="4e46a-118">不過，當變數以匿名型別初始化時，如果您稍後需要存取物件的屬性，則必須宣告該變數為 `var`。</span><span class="sxs-lookup"><span data-stu-id="4e46a-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="4e46a-119">這是 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中的常見案例。</span><span class="sxs-lookup"><span data-stu-id="4e46a-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="4e46a-120">如需詳細資訊，請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4e46a-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="4e46a-121">從原始程式碼的觀點來看，匿名型別沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="4e46a-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="4e46a-122">因此，如果已使用 `var` 初始化查詢變數，則存取傳回的物件序列中屬性的唯一方法，就是使用 `var` 作為 `foreach` 陳述式中反覆運算變數的類型。</span><span class="sxs-lookup"><span data-stu-id="4e46a-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="4e46a-123">備註</span><span class="sxs-lookup"><span data-stu-id="4e46a-123">Remarks</span></span>  
 <span data-ttu-id="4e46a-124">下列限制適用於隱含型別變數宣告：</span><span class="sxs-lookup"><span data-stu-id="4e46a-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="4e46a-125">`var` 只能在區域變數於相同的陳述式中宣告和初始化時使用；此變數無法初始化為 null、方法群組或匿名函式。</span><span class="sxs-lookup"><span data-stu-id="4e46a-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="4e46a-126">`var` 無法在類別範圍的欄位中使用。</span><span class="sxs-lookup"><span data-stu-id="4e46a-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="4e46a-127">使用 `var` 宣告的變數無法在初始化運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="4e46a-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="4e46a-128">換句話說，此運算式是合法的 `: int i = (i = 20);`，但此運算式會產生編譯時期錯誤︰`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="4e46a-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="4e46a-129">無法在相同的陳述式中初始化多個隱含型別變數。</span><span class="sxs-lookup"><span data-stu-id="4e46a-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="4e46a-130">如果名為 `var` 的類型在範圍之內，則 `var` 關鍵字會解析成該類型名稱，而且不會視為隱含型別區域變數宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e46a-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="4e46a-131">您會發現在難以判斷查詢運算式中查詢變數的確切建構類型時，`var` 也相當有用。</span><span class="sxs-lookup"><span data-stu-id="4e46a-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="4e46a-132">這會在群組與排序作業時發生。</span><span class="sxs-lookup"><span data-stu-id="4e46a-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="4e46a-133">當您不想要老是在鍵盤上鍵入變數的特定類型，或是此特定類型很明顯或不會增加程式碼的可讀性時，`var` 關鍵字也相當有用。</span><span class="sxs-lookup"><span data-stu-id="4e46a-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="4e46a-134">`var` 有用的其中一個範例是用於巢狀泛型型別時，例如用於群組作業的類型。</span><span class="sxs-lookup"><span data-stu-id="4e46a-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="4e46a-135">在下列查詢中，查詢變數的類型是 `IEnumerable<IGrouping<string, Student>>`。</span><span class="sxs-lookup"><span data-stu-id="4e46a-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="4e46a-136">只要您及維護程式碼的其他使用者了解這點，為求便利和簡潔而使用隱含型別就不會有問題。</span><span class="sxs-lookup"><span data-stu-id="4e46a-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="4e46a-137">無論如何，使用 `var` 都可能會使您的程式碼對其他開發人員而言更難以了解。</span><span class="sxs-lookup"><span data-stu-id="4e46a-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="4e46a-138">基於這個理由，C# 文件通常只有在必要時才會使用 `var`。</span><span class="sxs-lookup"><span data-stu-id="4e46a-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e46a-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e46a-139">See Also</span></span>  
 [<span data-ttu-id="4e46a-140">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4e46a-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4e46a-141">隱含型別陣列</span><span class="sxs-lookup"><span data-stu-id="4e46a-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="4e46a-142">如何：在查詢運算式中使用隱含型別區域變數和陣列</span><span class="sxs-lookup"><span data-stu-id="4e46a-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="4e46a-143">匿名類型</span><span class="sxs-lookup"><span data-stu-id="4e46a-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="4e46a-144">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="4e46a-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="4e46a-145">var</span><span class="sxs-lookup"><span data-stu-id="4e46a-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="4e46a-146">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="4e46a-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="4e46a-147">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="4e46a-147">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="4e46a-148">for</span><span class="sxs-lookup"><span data-stu-id="4e46a-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="4e46a-149">foreach、in</span><span class="sxs-lookup"><span data-stu-id="4e46a-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="4e46a-150">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="4e46a-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
