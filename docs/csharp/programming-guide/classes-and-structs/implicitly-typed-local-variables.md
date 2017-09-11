---
title: "隱含類型區域變數 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cc02c0f7ef5fbbbf3c60188426a8027f6a60fb89
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="2828f-102">隱含類型區域變數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2828f-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="2828f-103">您可以宣告區域變數而不提供明確類型。</span><span class="sxs-lookup"><span data-stu-id="2828f-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="2828f-104">`var` 關鍵字會指示編譯器從初始化陳述式右側的運算式推斷變數的類型。</span><span class="sxs-lookup"><span data-stu-id="2828f-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="2828f-105">推斷類型可能是內建類型、匿名型別、使用者定義型別，或 .NET Framework 類別庫中定義的類型。</span><span class="sxs-lookup"><span data-stu-id="2828f-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="2828f-106">如需如何使用 `var` 初始化陣列的詳細資訊，請參閱[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="2828f-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="2828f-107">下列範例顯示可以使用 `var` 宣告區域變數的各種方法：</span><span class="sxs-lookup"><span data-stu-id="2828f-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 <span data-ttu-id="2828f-108">[!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2828f-108">[!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]</span></span>  
  
 <span data-ttu-id="2828f-109">請務必了解 `var` 關鍵字不代表 "variant"，也不代表變數是不嚴格規定類型或晚期繫結的。</span><span class="sxs-lookup"><span data-stu-id="2828f-109">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="2828f-110">只代表編譯器會判斷並指派最適當的類型。</span><span class="sxs-lookup"><span data-stu-id="2828f-110">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="2828f-111">`var` 關鍵字可在下列內容中使用：</span><span class="sxs-lookup"><span data-stu-id="2828f-111">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="2828f-112">在區域變數 (方法範圍中宣告的變數) 上，如前述範例所示。</span><span class="sxs-lookup"><span data-stu-id="2828f-112">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="2828f-113">在 [for](../../../csharp/language-reference/keywords/for.md) 初始化陳述式中。</span><span class="sxs-lookup"><span data-stu-id="2828f-113">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="2828f-114">在 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 初始化陳述式中。</span><span class="sxs-lookup"><span data-stu-id="2828f-114">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="2828f-115">在 [using](../../../csharp/language-reference/keywords/using-statement.md) 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="2828f-115">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="2828f-116">如需詳細資訊，請參閱[如何：在查詢運算式中使用隱含型別區域變數和陣列](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="2828f-116">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="2828f-117">var 和匿名型別</span><span class="sxs-lookup"><span data-stu-id="2828f-117">var and Anonymous Types</span></span>  
 <span data-ttu-id="2828f-118">在許多情況下，使用 `var` 是選擇性的，只是為了在語法上便於使用。</span><span class="sxs-lookup"><span data-stu-id="2828f-118">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="2828f-119">不過，當變數以匿名型別初始化時，如果您稍後需要存取物件的屬性，則必須宣告該變數為 `var`。</span><span class="sxs-lookup"><span data-stu-id="2828f-119">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="2828f-120">這是 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中的常見案例。</span><span class="sxs-lookup"><span data-stu-id="2828f-120">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="2828f-121">如需詳細資訊，請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2828f-121">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="2828f-122">從原始程式碼的觀點來看，匿名型別沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="2828f-122">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="2828f-123">因此，如果已使用 `var` 初始化查詢變數，則存取傳回的物件序列中屬性的唯一方法，就是使用 `var` 作為 `foreach` 陳述式中反覆運算變數的類型。</span><span class="sxs-lookup"><span data-stu-id="2828f-123">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 <span data-ttu-id="2828f-124">[!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2828f-124">[!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2828f-125">備註</span><span class="sxs-lookup"><span data-stu-id="2828f-125">Remarks</span></span>  
 <span data-ttu-id="2828f-126">下列限制適用於隱含型別變數宣告：</span><span class="sxs-lookup"><span data-stu-id="2828f-126">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="2828f-127">`var` 只能在區域變數於相同的陳述式中宣告和初始化時使用；此變數無法初始化為 null、方法群組或匿名函式。</span><span class="sxs-lookup"><span data-stu-id="2828f-127">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="2828f-128">`var` 無法在類別範圍的欄位中使用。</span><span class="sxs-lookup"><span data-stu-id="2828f-128">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="2828f-129">使用 `var` 宣告的變數無法在初始化運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="2828f-129">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="2828f-130">換句話說，此運算式是合法的 `: int i = (i = 20);`，但此運算式會產生編譯時期錯誤︰`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="2828f-130">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="2828f-131">無法在相同的陳述式中初始化多個隱含型別變數。</span><span class="sxs-lookup"><span data-stu-id="2828f-131">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="2828f-132">如果名為 `var` 的類型在範圍之內，則 `var` 關鍵字會解析成該類型名稱，而且不會視為隱含型別區域變數宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="2828f-132">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="2828f-133">您會發現在難以判斷查詢運算式中查詢變數的確切建構類型時，`var` 也相當有用。</span><span class="sxs-lookup"><span data-stu-id="2828f-133">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="2828f-134">這會在群組與排序作業時發生。</span><span class="sxs-lookup"><span data-stu-id="2828f-134">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="2828f-135">當您不想要老是在鍵盤上鍵入變數的特定類型，或是此特定類型很明顯或不會增加程式碼的可讀性時，`var` 關鍵字也相當有用。</span><span class="sxs-lookup"><span data-stu-id="2828f-135">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="2828f-136">`var` 有用的其中一個範例是用於巢狀泛型型別時，例如用於群組作業的類型。</span><span class="sxs-lookup"><span data-stu-id="2828f-136">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="2828f-137">在下列查詢中，查詢變數的類型是 `IEnumerable<IGrouping<string, Student>>`。</span><span class="sxs-lookup"><span data-stu-id="2828f-137">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="2828f-138">只要您及維護程式碼的其他使用者了解這點，為求便利和簡潔而使用隱含型別就不會有問題。</span><span class="sxs-lookup"><span data-stu-id="2828f-138">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 <span data-ttu-id="2828f-139">[!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2828f-139">[!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]</span></span>  
  
 <span data-ttu-id="2828f-140">無論如何，使用 `var` 都可能會使您的程式碼對其他開發人員而言更難以了解。</span><span class="sxs-lookup"><span data-stu-id="2828f-140">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="2828f-141">基於這個理由，C# 文件通常只有在必要時才會使用 `var`。</span><span class="sxs-lookup"><span data-stu-id="2828f-141">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2828f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2828f-142">See Also</span></span>  
 <span data-ttu-id="2828f-143">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-143">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2828f-144">[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-144">[Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md) </span></span>  
 <span data-ttu-id="2828f-145">[如何：在查詢運算式中使用隱含型別區域變數和陣列](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-145">[How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md) </span></span>  
 <span data-ttu-id="2828f-146">[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-146">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="2828f-147">[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-147">[Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span></span>  
 <span data-ttu-id="2828f-148">[var](../../../csharp/language-reference/keywords/var.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-148">[var](../../../csharp/language-reference/keywords/var.md) </span></span>  
 <span data-ttu-id="2828f-149">[LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-149">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="2828f-150">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="2828f-150">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="2828f-151">[for](../../../csharp/language-reference/keywords/for.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-151">[for](../../../csharp/language-reference/keywords/for.md) </span></span>  
 <span data-ttu-id="2828f-152">[foreach、in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="2828f-152">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
 [<span data-ttu-id="2828f-153">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="2828f-153">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)

