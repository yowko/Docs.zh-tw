---
title: "out 參數修飾詞 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
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
ms.sourcegitcommit: 59e445ac27f07c85d9e98c5f595cf5f935f75443
ms.openlocfilehash: 9a0a488c6f444608a335cd990847774fb6fe9e3f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/31/2017

---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="ad8bc-102">out 參數修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ad8bc-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="ad8bc-103">`out` 關鍵字會導致引數以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="ad8bc-104">它類似於 [ref](../../../csharp/language-reference/keywords/ref.md) 關鍵字，只是 `ref` 要求必須在傳遞變數前先將它初始化。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="ad8bc-105">若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="ad8bc-106">例如: </span><span class="sxs-lookup"><span data-stu-id="ad8bc-106">For example:</span></span>  
  
 <span data-ttu-id="ad8bc-107">[!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad8bc-107">[!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="ad8bc-108">`out` 關鍵字也可以和泛型型別參數一起使用，指定型別參數為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="ad8bc-109">如需在此內容中使用 `out` 關鍵字的詳細資訊，請參閱 [out (泛型修飾詞)](../../../csharp/language-reference/keywords/out-generic-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="ad8bc-110">當作 `out` 引數傳遞的變數不必先初始化，就能在方法呼叫中傳遞。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="ad8bc-111">不過，需要先指派值給被呼叫的方法，方法才能傳回。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="ad8bc-112">雖然 `ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯階段，不會將其視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-112">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="ad8bc-113">因此，如果唯一的差別是一種方法採用 `ref` 引數，而另一種方法採用 `out` 引數，則不能多載方法。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="ad8bc-114">例如，將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ad8bc-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="ad8bc-115">不過，如果一種方法採用 `ref` 或 `out` 引數，而另一種方法都不採用，則可以完成多載，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ad8bc-115">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 <span data-ttu-id="ad8bc-116">[!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad8bc-116">[!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]</span></span>  
  
 <span data-ttu-id="ad8bc-117">屬性不是變數，因此無法作為 `out` 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="ad8bc-118">如需傳遞陣列的資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="ad8bc-119">您不能將 `ref` 和 `out` 關鍵字用於下列幾種方法：</span><span class="sxs-lookup"><span data-stu-id="ad8bc-119">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="ad8bc-120">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="ad8bc-121">迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="ad8bc-122">宣告 `out` 引數</span><span class="sxs-lookup"><span data-stu-id="ad8bc-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="ad8bc-123">當您想要方法傳回多個值時，使用 `out` 引數宣告方法很有用。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="ad8bc-124">下列範例使用 `out`，在單一方法呼叫中傳回三個變數。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="ad8bc-125">請注意，第三個引數指派為 Null。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="ad8bc-126">這可讓方法能選擇性地傳回值。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-126">This enables methods to return values optionally.</span></span>  
  
 <span data-ttu-id="ad8bc-127">[!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad8bc-127">[!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]</span></span>  

 <span data-ttu-id="ad8bc-128">[Try 模式](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) 牽涉到傳回 `bool` 以指出作業成功或失敗，並傳回作業在 `out` 引數中產生的值。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-128">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="ad8bc-129">有數種剖析方法 (例如 [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) 方法) 使用此模式。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-129">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="ad8bc-130">使用 `out` 引數呼叫方法</span><span class="sxs-lookup"><span data-stu-id="ad8bc-130">Calling a method with an `out` argument</span></span>

<span data-ttu-id="ad8bc-131">在 C# 6 和舊版中，您必須先在其他陳述式中宣告變數，才能以 `out` 引數方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-131">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="ad8bc-132">下列範例宣告名為 `number` 的變數，然後將它傳遞到 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法，此方法嘗試將字串轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-132">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 <span data-ttu-id="ad8bc-133">[!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad8bc-133">[!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]</span></span>  

<span data-ttu-id="ad8bc-134">從 C# 7 開始，您可以在方法呼叫的引數清單中宣告 `out` 變數，而非在個別變數中宣告。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-134">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="ad8bc-135">這會產生更精簡、更容易閱讀的程式碼，也可避免不小心在方法呼叫前先將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-135">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="ad8bc-136">下列範例與上一個範例類似，但下列範例會在對 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法的呼叫中定義 `number` 變數。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-136">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 <span data-ttu-id="ad8bc-137">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad8bc-137">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]</span></span>  
   
<span data-ttu-id="ad8bc-138">在上面的範例中中，`number` 變數是如同 `int` 的強型別。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-138">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="ad8bc-139">您也可以宣告隱含型別的區域變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ad8bc-139">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 <span data-ttu-id="ad8bc-140">[!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad8bc-140">[!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]</span></span>  
   
## <a name="c-language-specification"></a><span data-ttu-id="ad8bc-141">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ad8bc-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad8bc-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad8bc-142">See Also</span></span>  
 <span data-ttu-id="ad8bc-143">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad8bc-143">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ad8bc-144">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad8bc-144">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ad8bc-145">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad8bc-145">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="ad8bc-146">方法參數</span><span class="sxs-lookup"><span data-stu-id="ad8bc-146">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)

