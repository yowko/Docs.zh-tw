---
title: "yield (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 46
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
ms.openlocfilehash: eb55fd5b1ade48316516cda83633935abbf8dcf9
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="yield-c-reference"></a><span data-ttu-id="3f6e2-102">yield (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3f6e2-102">yield (C# Reference)</span></span>
<span data-ttu-id="3f6e2-103">在陳述式中使用 `yield` 關鍵字時，您會表示關鍵字所在的方法、運算子或 `get` 存取子是迭代器。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-103">When you use the `yield` keyword in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="3f6e2-104">如果使用 `yield` 定義迭代器，當您為自訂集合類型實作 <xref:System.Collections.Generic.IEnumerator%601> 和 <xref:System.Collections.IEnumerable> 模式時，就不需要明確的額外類別 (保存列舉之狀態的類別，請參閱 <xref:System.Collections.IEnumerator> 中的範例)。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="3f6e2-105">下列範例將示範兩種形式的 `yield` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f6e2-106">備註</span><span class="sxs-lookup"><span data-stu-id="3f6e2-106">Remarks</span></span>  
 <span data-ttu-id="3f6e2-107">您可以使用 `yield return` 陳述式一次傳回一個元素。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="3f6e2-108">使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式或 LINQ 查詢，即可使用 iterator 方法。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="3f6e2-109">`foreach` 迴圈的每個反覆項目都會呼叫 Iterator 方法。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="3f6e2-110">當 Iterator 方法中到達 `yield return` 陳述式時，就會傳回 `expression` 並保留程式碼中目前的位置。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="3f6e2-111">下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="3f6e2-112">您可以使用 `yield break` 陳述式結束反覆項目。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="3f6e2-113">如需迭代器的詳細資訊，請參閱 [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) (迭代器)。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-113">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="3f6e2-114">Iterator 方法和 get 存取子</span><span class="sxs-lookup"><span data-stu-id="3f6e2-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="3f6e2-115">迭代器的宣告必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="3f6e2-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="3f6e2-116">傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="3f6e2-117">宣告不可包含任何 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-117">The declaration can't have any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters.</span></span>  
  
 <span data-ttu-id="3f6e2-118">傳回 `yield` 或 <xref:System.Collections.IEnumerable> 的 <xref:System.Collections.IEnumerator> 類型迭代器為 `object`。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="3f6e2-119">如果迭代器傳回 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.Generic.IEnumerator%601>，則 `yield return` 陳述式中必須進行從運算式類型轉換成泛型類型參數的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="3f6e2-120">具有下列特性的方法中不可包含 `yield return` 或 `yield break` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="3f6e2-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="3f6e2-121">匿名方法。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-121">Anonymous methods.</span></span> <span data-ttu-id="3f6e2-122">如需詳細資訊，請參閱[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="3f6e2-123">包含不安全區塊的方法。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="3f6e2-124">如需詳細資訊，請參閱 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="3f6e2-125">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="3f6e2-125">Exception Handling</span></span>  
 <span data-ttu-id="3f6e2-126">`yield return` 陳述式不能位於 try-catch 區塊內。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="3f6e2-127">`yield return` 陳述式可以位於 try-finally 陳述式的 try 區塊內。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="3f6e2-128">`yield break` 陳述式可以位於 try 區塊或 catch 區塊中，但是不可位於 finally 區塊中。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="3f6e2-129">如果 `foreach` 主體 (在 Iterator 方法之外) 擲回例外狀況，則會執行 Iterator 方法中的 `finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="3f6e2-130">技術實作</span><span class="sxs-lookup"><span data-stu-id="3f6e2-130">Technical Implementation</span></span>  
 <span data-ttu-id="3f6e2-131">下列程式碼會從 Iterator 方法傳回 `IEnumerable<string>`，然後逐一查看其元素。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="3f6e2-132">對 `MyIteratorMethod` 的呼叫不會執行方法的主體。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="3f6e2-133">呼叫會改為將 `IEnumerable<string>` 傳回至 `elements` 變數中。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="3f6e2-134">在 `foreach` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="3f6e2-135">這個呼叫會執行 `MyIteratorMethod` 的主體，直到下一個 `yield return` 陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="3f6e2-136">`yield return` 陳述式所傳回的運算式不僅會判斷迴圈主體所使用之 `element` 變數的值，也會判斷元素的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性，該屬性會是 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="3f6e2-137">在 `foreach` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `yield return` 陳述式時再次停止。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="3f6e2-138">當 Iterator 方法結束或到達 `foreach` 陳述式時，`yield break` 迴圈便完成。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f6e2-139">範例</span><span class="sxs-lookup"><span data-stu-id="3f6e2-139">Example</span></span>  
 <span data-ttu-id="3f6e2-140">下列範例中的陳述式 `yield return` 位於 `for` 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="3f6e2-141">`foreach` 中 `Process` 陳述式主體的每個反覆項目都會建立對 `Power` Iterator 函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-141">Each iteration of the `foreach` statement body in `Process` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="3f6e2-142">每次呼叫 Iterator 函式都會執行下一個 `yield return` 陳述式，這會在 `for` 迴圈的下一個反覆項目期間發生。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="3f6e2-143">Iterator 方法的傳回類型是 <xref:System.Collections.IEnumerable>，其為 Iterator 介面類型。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="3f6e2-144">呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 <span data-ttu-id="3f6e2-145">[!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f6e2-145">[!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f6e2-146">範例</span><span class="sxs-lookup"><span data-stu-id="3f6e2-146">Example</span></span>  
 <span data-ttu-id="3f6e2-147">下列範例將示範本身為迭代器的 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-147">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="3f6e2-148">在這個範例中，每個 `yield return` 陳述式都會傳回使用者定義類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-148">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 <span data-ttu-id="3f6e2-149">[!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f6e2-149">[!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f6e2-150">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3f6e2-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f6e2-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f6e2-151">See Also</span></span>  
 <span data-ttu-id="3f6e2-152">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f6e2-152">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3f6e2-153">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f6e2-153">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3f6e2-154">[foreach、in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="3f6e2-154">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
 [<span data-ttu-id="3f6e2-155">迭代器</span><span class="sxs-lookup"><span data-stu-id="3f6e2-155">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)

