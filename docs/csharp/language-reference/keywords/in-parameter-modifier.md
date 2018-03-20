---
title: "in 參數修飾詞 (C# 參考)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 035aac3e6b902f607e533b709713eb1d07c9774a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="19661-102">in 參數修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="19661-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="19661-103">`in` 關鍵字會導致引數由參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="19661-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="19661-104">這和 [ref](ref.md) 或 [out](out-parameter-modifier.md) 關鍵字類似同，但 `in` 引數無法由呼叫的方法加以修改，而是可以修改 `ref` 引數。`out` 引數必須由呼叫端修改，而這些修改內容可於呼叫內容中查看。</span><span class="sxs-lookup"><span data-stu-id="19661-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="19661-105">上述範例示範了 `in` 修飾詞在呼叫位置並非必要，</span><span class="sxs-lookup"><span data-stu-id="19661-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="19661-106">而只有在宣告方法時才會需要該項目。</span><span class="sxs-lookup"><span data-stu-id="19661-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="19661-107">`in` 關鍵字也可與泛型型別搭配使用，來指定類型參數是否為 Contravariant、屬於 `foreach` 陳述式的一部分，或是屬於 LINQ 查詢中的 `join` 子句。</span><span class="sxs-lookup"><span data-stu-id="19661-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="19661-108">如需如何在這些內容中使用 `in` 關鍵字的詳細資訊，請參閱 [in](in.md)，其提供所有這些使用的連結。</span><span class="sxs-lookup"><span data-stu-id="19661-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="19661-109">傳遞為 `in` 引數的變數，必須先經過初始化，才能在方法呼叫中傳遞。</span><span class="sxs-lookup"><span data-stu-id="19661-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="19661-110">但是，呼叫方法可能不會指派值或修改引數。</span><span class="sxs-lookup"><span data-stu-id="19661-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="19661-111">雖然 `in`、`ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯期間，不會將其視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="19661-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="19661-112">因此，如果唯一的差別是一種方法採用 `ref` 或 `in` 引數，而另一種方法採用 `out` 引數，則無法對方法進行多載。</span><span class="sxs-lookup"><span data-stu-id="19661-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="19661-113">例如，將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="19661-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="19661-114">若有 `in`，可以進行多載，但會產生編譯器警告：</span><span class="sxs-lookup"><span data-stu-id="19661-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="19661-115">因為呼叫方法並不會修改屬性與常數的值，所以這兩者皆會以 `in` 參數方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="19661-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="19661-116">您不可為下列幾種方法使用 `in`、`ref` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="19661-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="19661-117">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="19661-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="19661-118">迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="19661-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="19661-119">一般來說，您宣告 `in` 引數，以避免出現依值傳遞引數時所需進行的複製作業。</span><span class="sxs-lookup"><span data-stu-id="19661-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="19661-120">當引數為結構或結構的陣列時，此方法相當實用。</span><span class="sxs-lookup"><span data-stu-id="19661-120">This is most useful when arguments are structures or arrays of structures.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="19661-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="19661-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19661-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="19661-122">See Also</span></span>  
 [<span data-ttu-id="19661-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="19661-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="19661-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="19661-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="19661-125">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="19661-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="19661-126">方法參數</span><span class="sxs-lookup"><span data-stu-id="19661-126">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
