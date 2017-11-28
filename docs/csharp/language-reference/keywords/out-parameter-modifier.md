---
title: "out 參數修飾詞 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="c1ae4-102">out 參數修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c1ae4-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="c1ae4-103">`out` 關鍵字會導致引數由參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="c1ae4-104">它類似於 [ref](../../../csharp/language-reference/keywords/ref.md) 關鍵字，只是 `ref` 需要在傳遞之前，先初始化變數。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="c1ae4-105">若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="c1ae4-106">例如: </span><span class="sxs-lookup"><span data-stu-id="c1ae4-106">For example:</span></span>  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> <span data-ttu-id="c1ae4-107">`out` 關鍵字也可以和泛型型別參數一起使用，指定型別參數為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-107">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="c1ae4-108">如需在此內容中使用 `out` 關鍵字的詳細資訊，請參閱 [out (泛型修飾詞)](../../../csharp/language-reference/keywords/out-generic-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-108">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="c1ae4-109">當作 `out` 引數傳遞的變數不必先初始化，再於方法呼叫中傳遞。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-109">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="c1ae4-110">不過，需要先指派值給被呼叫的方法，方法才能傳回。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-110">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="c1ae4-111">雖然 `ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯階段，不會將其視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-111">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="c1ae4-112">因此，如果唯一的差別是一種方法採用 `ref` 引數，而另一種方法採用 `out` 引數，則不能多載方法。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="c1ae4-113">例如，將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c1ae4-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="c1ae4-114">不過，如果一種方法採用 `ref` 或 `out` 引數，而另一種方法都不採用，則可以完成多載，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c1ae4-114">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 <span data-ttu-id="c1ae4-115">屬性不是變數，因此無法做為 `out` 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-115">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="c1ae4-116">如需傳遞陣列的資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-116">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="c1ae4-117">您不能將 `ref` 和 `out` 關鍵字用於下列幾種方法：</span><span class="sxs-lookup"><span data-stu-id="c1ae4-117">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="c1ae4-118">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-118">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="c1ae4-119">迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-119">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="c1ae4-120">宣告 `out` 引數</span><span class="sxs-lookup"><span data-stu-id="c1ae4-120">Declaring `out` arguments</span></span>   

 <span data-ttu-id="c1ae4-121">當您想要方法傳回多個值時，宣告使用 `out` 引數的方法很有用。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-121">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="c1ae4-122">下列範例使用 `out`，在單一方法呼叫中，傳回三個變數。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-122">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="c1ae4-123">請注意，第三個引數指派為 null。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-123">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="c1ae4-124">這可讓方法能選擇性地傳回值。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-124">This enables methods to return values optionally.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 <span data-ttu-id="c1ae4-125">[Try 模式](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) 牽涉到傳回 `bool` 指出作業成功或失敗，並傳回作業在 `out` 引數中產生的值。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-125">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="c1ae4-126">有數種剖析方法 (例如 [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) 方法) 使用此模式。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-126">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="c1ae4-127">呼叫有 `out` 引數的方法</span><span class="sxs-lookup"><span data-stu-id="c1ae4-127">Calling a method with an `out` argument</span></span>

<span data-ttu-id="c1ae4-128">在 C# 6 和舊版中，您必須先在其他陳述式中宣告變數，再將它傳遞為 `out` 引數。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-128">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="c1ae4-129">下列範例宣告名為 `number` 的變數，然後將它傳遞到 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法，此方法嘗試將字串轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-129">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

<span data-ttu-id="c1ae4-130">從 C# 7 開始，您可以在方法呼叫的引數清單中宣告 `out` 變數，而非在其他的變數中宣告。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-130">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="c1ae4-131">這會產生更精簡、更容易閱讀的程式碼，也可避免不小心在方法呼叫前先將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-131">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="c1ae4-132">下列範例與上一個範例類似，但下列範例會在對 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法的呼叫中定義 `number` 變數。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-132">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
<span data-ttu-id="c1ae4-133">在上例中，`number` 變數是如同 `int` 的強型別。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-133">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="c1ae4-134">您也可以宣告隱含型別的區域變數，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="c1ae4-134">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="c1ae4-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c1ae4-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1ae4-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1ae4-136">See Also</span></span>  
 [<span data-ttu-id="c1ae4-137">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c1ae4-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c1ae4-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c1ae4-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c1ae4-139">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c1ae4-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c1ae4-140">方法參數</span><span class="sxs-lookup"><span data-stu-id="c1ae4-140">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
