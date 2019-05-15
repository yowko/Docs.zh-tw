---
title: out 參數修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 704b66e6cdec5caa47f85ed8e3acbd2a6a73b730
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598233"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="787d6-102">out 參數修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="787d6-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="787d6-103">`out` 關鍵字會導致引數由參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="787d6-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="787d6-104">它會使形式參數成為引數的別名，其必須為變數。</span><span class="sxs-lookup"><span data-stu-id="787d6-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="787d6-105">換句話說，參數上的任何作業都會在引數上進行。</span><span class="sxs-lookup"><span data-stu-id="787d6-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="787d6-106">它類似於 [ref](ref.md) 關鍵字，只是 `ref` 需要在傳遞之前，先初始化變數。</span><span class="sxs-lookup"><span data-stu-id="787d6-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="787d6-107">其類似於 [in](in-parameter-modifier.md) 關鍵字，但不同處在於 `in` 不允許呼叫的方法來修改引數的值。</span><span class="sxs-lookup"><span data-stu-id="787d6-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="787d6-108">若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="787d6-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="787d6-109">例如：</span><span class="sxs-lookup"><span data-stu-id="787d6-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="787d6-110">`out` 關鍵字也可以和泛型型別參數一起使用，指定型別參數為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="787d6-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="787d6-111">如需在此內容中使用 `out` 關鍵字的詳細資訊，請參閱 [out (泛型修飾詞)](out-generic-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="787d6-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="787d6-112">當作 `out` 引數傳遞的變數不必先初始化，再於方法呼叫中傳遞。</span><span class="sxs-lookup"><span data-stu-id="787d6-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="787d6-113">不過，需要先指派值給被呼叫的方法，方法才能傳回。</span><span class="sxs-lookup"><span data-stu-id="787d6-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="787d6-114">針對多載解析的目的，`in`、`ref` 和 `out` 關鍵字不被視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="787d6-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="787d6-115">因此，如果唯一的差別是一種方法採用 `ref` 或 `in` 引數，而另一種方法採用 `out` 引數，則無法對方法進行多載。</span><span class="sxs-lookup"><span data-stu-id="787d6-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="787d6-116">例如，將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="787d6-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="787d6-117">但如果有一種方法採用 `ref`、`in` 或 `out` 引數，而另一種方法完全沒有這些修飾詞，則類似於：</span><span class="sxs-lookup"><span data-stu-id="787d6-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="787d6-118">編譯器會選擇最佳的多載，方法是比對呼叫位置的參數修飾詞，與方法呼叫中所使用的參數修飾詞。</span><span class="sxs-lookup"><span data-stu-id="787d6-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="787d6-119">屬性不是變數，因此無法做為 `out` 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="787d6-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="787d6-120">您不可為下列幾種方法使用 `in`、`ref` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="787d6-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="787d6-121">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="787d6-121">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="787d6-122">迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="787d6-122">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="787d6-123">宣告 `out` 參數</span><span class="sxs-lookup"><span data-stu-id="787d6-123">Declaring `out` parameters</span></span>   

<span data-ttu-id="787d6-124">使用 `out` 引數來宣告方法是傳回多個值的傳統因應措施。</span><span class="sxs-lookup"><span data-stu-id="787d6-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="787d6-125">從 C# 7.0 開始，針對類似案例請考慮使用 [tuple](../../tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="787d6-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="787d6-126">下列範例使用 `out`，在單一方法呼叫中，傳回三個變數。</span><span class="sxs-lookup"><span data-stu-id="787d6-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="787d6-127">請注意，第三個引數指派為 null。</span><span class="sxs-lookup"><span data-stu-id="787d6-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="787d6-128">這可讓方法能選擇性地傳回值。</span><span class="sxs-lookup"><span data-stu-id="787d6-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="787d6-129">呼叫有 `out` 引數的方法</span><span class="sxs-lookup"><span data-stu-id="787d6-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="787d6-130">在 C# 6 和舊版中，您必須先在其他陳述式中宣告變數，再將它傳遞為 `out` 引數。</span><span class="sxs-lookup"><span data-stu-id="787d6-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="787d6-131">下列範例宣告名為 `number` 的變數，然後將它傳遞到 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法，此方法嘗試將字串轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="787d6-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="787d6-132">從 C# 7.0 開始，您可以在方法呼叫的引數清單中宣告 `out` 變數，而非在其他的變數中宣告。</span><span class="sxs-lookup"><span data-stu-id="787d6-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="787d6-133">這會產生更精簡、更容易閱讀的程式碼，也可避免不小心在方法呼叫前先將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="787d6-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="787d6-134">下列範例與上一個範例類似，但下列範例會在對 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法的呼叫中定義 `number` 變數。</span><span class="sxs-lookup"><span data-stu-id="787d6-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="787d6-135">在上例中，`number` 變數是如同 `int` 的強型別。</span><span class="sxs-lookup"><span data-stu-id="787d6-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="787d6-136">您也可以宣告隱含型別的區域變數，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="787d6-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="787d6-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="787d6-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="787d6-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="787d6-138">See also</span></span>

- [<span data-ttu-id="787d6-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="787d6-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="787d6-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="787d6-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="787d6-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="787d6-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="787d6-142">方法參數</span><span class="sxs-lookup"><span data-stu-id="787d6-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
