---
description: out 參數修飾詞 - C# 參考
title: out 參數修飾詞 - C# 參考
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 23bf841c002f9be5fdd4e8d8da48e68e9f6e5fcc
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122416"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="1e824-103">out 參數修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1e824-103">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="1e824-104">`out` 關鍵字會導致引數由參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="1e824-104">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="1e824-105">它會使形式參數成為引數的別名，其必須為變數。</span><span class="sxs-lookup"><span data-stu-id="1e824-105">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="1e824-106">換句話說，參數上的任何作業都會在引數上進行。</span><span class="sxs-lookup"><span data-stu-id="1e824-106">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="1e824-107">它類似於 [ref](ref.md) 關鍵字，只是 `ref` 需要在傳遞之前，先初始化變數。</span><span class="sxs-lookup"><span data-stu-id="1e824-107">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="1e824-108">其類似於 [in](in-parameter-modifier.md) 關鍵字，但不同處在於 `in` 不允許呼叫的方法來修改引數的值。</span><span class="sxs-lookup"><span data-stu-id="1e824-108">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="1e824-109">若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1e824-109">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="1e824-110">例如：</span><span class="sxs-lookup"><span data-stu-id="1e824-110">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="1e824-111">`out` 關鍵字也可以和泛型型別參數一起使用，指定型別參數為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="1e824-111">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="1e824-112">如需在此內容中使用 `out` 關鍵字的詳細資訊，請參閱 [out (泛型修飾詞)](out-generic-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="1e824-112">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="1e824-113">當作 `out` 引數傳遞的變數不必先初始化，再於方法呼叫中傳遞。</span><span class="sxs-lookup"><span data-stu-id="1e824-113">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="1e824-114">不過，需要先指派值給被呼叫的方法，方法才能傳回。</span><span class="sxs-lookup"><span data-stu-id="1e824-114">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="1e824-115">針對多載解析的目的，`in`、`ref` 和 `out` 關鍵字不被視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="1e824-115">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="1e824-116">因此，如果唯一的差別是一種方法採用 `ref` 或 `in` 引數，而另一種方法採用 `out` 引數，則無法對方法進行多載。</span><span class="sxs-lookup"><span data-stu-id="1e824-116">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="1e824-117">例如，將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="1e824-117">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="1e824-118">但如果有一種方法採用 `ref`、`in` 或 `out` 引數，而另一種方法完全沒有這些修飾詞，則類似於：</span><span class="sxs-lookup"><span data-stu-id="1e824-118">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="1e824-119">編譯器會選擇最佳的多載，方法是比對呼叫位置的參數修飾詞，與方法呼叫中所使用的參數修飾詞。</span><span class="sxs-lookup"><span data-stu-id="1e824-119">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="1e824-120">屬性不是變數，因此無法做為 `out` 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="1e824-120">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="1e824-121">您不可為下列幾種方法使用 `in`、`ref` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="1e824-121">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="1e824-122">使用 [async](./async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="1e824-122">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="1e824-123">迭代器方法，其包括 [yield return](./yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1e824-123">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="1e824-124">此外， [擴充方法](../../programming-guide/classes-and-structs/extension-methods.md) 具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="1e824-124">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="1e824-125">`out`關鍵字不能用在擴充方法的第一個引數上。</span><span class="sxs-lookup"><span data-stu-id="1e824-125">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="1e824-126">`ref`當引數不是結構，或是不受限於不是結構的泛型型別時，無法在擴充方法的第一個引數上使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1e824-126">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="1e824-127">`in`除非第一個引數是結構，否則無法使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1e824-127">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="1e824-128">`in`關鍵字不能用於任何泛型型別，即使當條件約束為結構時也一樣。</span><span class="sxs-lookup"><span data-stu-id="1e824-128">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="1e824-129">宣告 `out` 參數</span><span class="sxs-lookup"><span data-stu-id="1e824-129">Declaring `out` parameters</span></span>

<span data-ttu-id="1e824-130">使用 `out` 引數來宣告方法是傳回多個值的傳統因應措施。</span><span class="sxs-lookup"><span data-stu-id="1e824-130">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="1e824-131">從 c # 7.0 開始，請考慮類似案例的 [值元組](../builtin-types/value-tuples.md) 。</span><span class="sxs-lookup"><span data-stu-id="1e824-131">Beginning with C# 7.0, consider [value tuples](../builtin-types/value-tuples.md) for similar scenarios.</span></span> <span data-ttu-id="1e824-132">下列範例使用 `out`，在單一方法呼叫中，傳回三個變數。</span><span class="sxs-lookup"><span data-stu-id="1e824-132">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="1e824-133">第三個引數會指派給 null。</span><span class="sxs-lookup"><span data-stu-id="1e824-133">The third argument is assigned to null.</span></span> <span data-ttu-id="1e824-134">這可讓方法能選擇性地傳回值。</span><span class="sxs-lookup"><span data-stu-id="1e824-134">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="1e824-135">呼叫有 `out` 引數的方法</span><span class="sxs-lookup"><span data-stu-id="1e824-135">Calling a method with an `out` argument</span></span>

<span data-ttu-id="1e824-136">在 C# 6 和舊版中，您必須先在其他陳述式中宣告變數，再將它傳遞為 `out` 引數。</span><span class="sxs-lookup"><span data-stu-id="1e824-136">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="1e824-137">下列範例宣告名為 `number` 的變數，然後將它傳遞到 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法，此方法嘗試將字串轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="1e824-137">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="1e824-138">從 C# 7.0 開始，您可以在方法呼叫的引數清單中宣告 `out` 變數，而非在其他的變數中宣告。</span><span class="sxs-lookup"><span data-stu-id="1e824-138">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="1e824-139">這會產生更精簡、更容易閱讀的程式碼，也可避免不小心在方法呼叫前先將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="1e824-139">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="1e824-140">下列範例與上一個範例類似，但下列範例會在對 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法的呼叫中定義 `number` 變數。</span><span class="sxs-lookup"><span data-stu-id="1e824-140">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="1e824-141">在上例中，`number` 變數是如同 `int` 的強型別。</span><span class="sxs-lookup"><span data-stu-id="1e824-141">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="1e824-142">您也可以宣告隱含型別的區域變數，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="1e824-142">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="1e824-143">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1e824-143">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1e824-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e824-144">See also</span></span>

- [<span data-ttu-id="1e824-145">C # 參考</span><span class="sxs-lookup"><span data-stu-id="1e824-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1e824-146">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1e824-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1e824-147">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1e824-147">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="1e824-148">方法參數</span><span class="sxs-lookup"><span data-stu-id="1e824-148">Method Parameters</span></span>](./method-parameters.md)
