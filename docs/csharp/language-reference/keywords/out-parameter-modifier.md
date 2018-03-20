---
title: "out 參數修飾詞 (C# 參考)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0686d8bb0dec2a5ea6dd92491e58c93b7ee53a8
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="8f646-102">out 參數修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8f646-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="8f646-103">`out` 關鍵字會導致引數由參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="8f646-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="8f646-104">它類似於 [ref](ref.md) 關鍵字，只是 `ref` 需要在傳遞之前，先初始化變數。</span><span class="sxs-lookup"><span data-stu-id="8f646-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="8f646-105">其類似於 [in](in-parameter-modifier.md) 關鍵字，但不同處在於 `in` 不允許呼叫的方法來修改引數的值。</span><span class="sxs-lookup"><span data-stu-id="8f646-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="8f646-106">若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8f646-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="8f646-107">例如: </span><span class="sxs-lookup"><span data-stu-id="8f646-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="8f646-108">`out` 關鍵字也可以和泛型型別參數一起使用，指定型別參數為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="8f646-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="8f646-109">如需在此內容中使用 `out` 關鍵字的詳細資訊，請參閱 [out (泛型修飾詞)](out-generic-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="8f646-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="8f646-110">當作 `out` 引數傳遞的變數不必先初始化，再於方法呼叫中傳遞。</span><span class="sxs-lookup"><span data-stu-id="8f646-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="8f646-111">不過，需要先指派值給被呼叫的方法，方法才能傳回。</span><span class="sxs-lookup"><span data-stu-id="8f646-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="8f646-112">雖然 `in`、`ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯期間，不會將其視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="8f646-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="8f646-113">因此，如果唯一的差別是一種方法採用 `ref` 或 `in` 引數，而另一種方法採用 `out` 引數，則無法對方法進行多載。</span><span class="sxs-lookup"><span data-stu-id="8f646-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="8f646-114">例如，將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8f646-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="8f646-115">但如果有一種方法採用 `ref`、`in` 或 `out` 引數，而另一種方法完全沒有這些修飾詞，則類似於：</span><span class="sxs-lookup"><span data-stu-id="8f646-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="8f646-116">編譯器會選擇最佳的多載，方法是比對呼叫位置的參數修飾詞，與方法呼叫中所使用的參數修飾詞。</span><span class="sxs-lookup"><span data-stu-id="8f646-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="8f646-117">屬性不是變數，因此無法做為 `out` 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="8f646-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
 <span data-ttu-id="8f646-118">如需傳遞陣列的資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="8f646-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="8f646-119">您不可為下列幾種方法使用 `in`、`ref` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="8f646-119">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="8f646-120">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="8f646-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="8f646-121">迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8f646-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="8f646-122">宣告 `out` 引數</span><span class="sxs-lookup"><span data-stu-id="8f646-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="8f646-123">當您想要方法傳回多個值時，宣告使用 `out` 引數的方法很有用。</span><span class="sxs-lookup"><span data-stu-id="8f646-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="8f646-124">下列範例使用 `out`，在單一方法呼叫中，傳回三個變數。</span><span class="sxs-lookup"><span data-stu-id="8f646-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="8f646-125">請注意，第三個引數指派為 null。</span><span class="sxs-lookup"><span data-stu-id="8f646-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="8f646-126">這可讓方法能選擇性地傳回值。</span><span class="sxs-lookup"><span data-stu-id="8f646-126">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="8f646-127">[Try 模式](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) 牽涉到傳回 `bool` 指出作業成功或失敗，並傳回作業在 `out` 引數中產生的值。</span><span class="sxs-lookup"><span data-stu-id="8f646-127">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="8f646-128">有數種剖析方法 (例如 [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) 方法) 使用此模式。</span><span class="sxs-lookup"><span data-stu-id="8f646-128">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="8f646-129">呼叫有 `out` 引數的方法</span><span class="sxs-lookup"><span data-stu-id="8f646-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="8f646-130">在 C# 6 和舊版中，您必須先在其他陳述式中宣告變數，再將它傳遞為 `out` 引數。</span><span class="sxs-lookup"><span data-stu-id="8f646-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="8f646-131">下列範例宣告名為 `number` 的變數，然後將它傳遞到 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法，此方法嘗試將字串轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="8f646-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="8f646-132">從 C# 7 開始，您可以在方法呼叫的引數清單中宣告 `out` 變數，而非在其他的變數中宣告。</span><span class="sxs-lookup"><span data-stu-id="8f646-132">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="8f646-133">這會產生更精簡、更容易閱讀的程式碼，也可避免不小心在方法呼叫前先將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="8f646-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="8f646-134">下列範例與上一個範例類似，但下列範例會在對 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法的呼叫中定義 `number` 變數。</span><span class="sxs-lookup"><span data-stu-id="8f646-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="8f646-135">在上例中，`number` 變數是如同 `int` 的強型別。</span><span class="sxs-lookup"><span data-stu-id="8f646-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="8f646-136">您也可以宣告隱含型別的區域變數，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="8f646-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="8f646-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8f646-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f646-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f646-138">See Also</span></span>  
 [<span data-ttu-id="8f646-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8f646-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8f646-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8f646-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8f646-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8f646-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8f646-142">方法參數</span><span class="sxs-lookup"><span data-stu-id="8f646-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
