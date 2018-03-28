---
title: in 參數修飾詞 (C# 參考)
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
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="9cd62-102">in 參數修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9cd62-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="9cd62-103">`in` 關鍵字會導致引數由參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="9cd62-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="9cd62-104">這和 [ref](ref.md) 或 [out](out-parameter-modifier.md) 關鍵字類似同，但 `in` 引數無法由呼叫的方法加以修改，而是可以修改 `ref` 引數。`out` 引數必須由呼叫端修改，而這些修改內容可於呼叫內容中查看。</span><span class="sxs-lookup"><span data-stu-id="9cd62-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="9cd62-105">上述範例示範了 `in` 修飾詞在呼叫位置並非必要，</span><span class="sxs-lookup"><span data-stu-id="9cd62-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="9cd62-106">而只有在宣告方法時才會需要該項目。</span><span class="sxs-lookup"><span data-stu-id="9cd62-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="9cd62-107">`in` 關鍵字也可與泛型型別搭配使用，來指定類型參數是否為 Contravariant、屬於 `foreach` 陳述式的一部分，或是屬於 LINQ 查詢中的 `join` 子句。</span><span class="sxs-lookup"><span data-stu-id="9cd62-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="9cd62-108">如需如何在這些內容中使用 `in` 關鍵字的詳細資訊，請參閱 [in](in.md)，其提供所有這些使用的連結。</span><span class="sxs-lookup"><span data-stu-id="9cd62-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="9cd62-109">傳遞為 `in` 引數的變數，必須先經過初始化，才能在方法呼叫中傳遞。</span><span class="sxs-lookup"><span data-stu-id="9cd62-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="9cd62-110">但是，呼叫方法可能不會指派值或修改引數。</span><span class="sxs-lookup"><span data-stu-id="9cd62-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="9cd62-111">雖然 `in`、`ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯期間，不會將其視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="9cd62-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="9cd62-112">因此，如果唯一的差別是一種方法採用 `ref` 或 `in` 引數，而另一種方法採用 `out` 引數，則無法對方法進行多載。</span><span class="sxs-lookup"><span data-stu-id="9cd62-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="9cd62-113">例如，將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9cd62-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="9cd62-114">若有 `in`，可以進行多載，但會產生編譯器警告：</span><span class="sxs-lookup"><span data-stu-id="9cd62-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="9cd62-115">因為呼叫方法並不會修改屬性與常數的值，所以這兩者皆會以 `in` 參數方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="9cd62-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="9cd62-116">您不可為下列幾種方法使用 `in`、`ref` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="9cd62-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="9cd62-117">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="9cd62-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="9cd62-118">迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9cd62-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="9cd62-119">一般來說，您宣告 `in` 引數，以避免出現依值傳遞引數時所需進行的複製作業。</span><span class="sxs-lookup"><span data-stu-id="9cd62-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="9cd62-120">當引數為實質型別 (例如複製作業所耗用資源較傳遞參考高的結構) 時，這相當實用。</span><span class="sxs-lookup"><span data-stu-id="9cd62-120">This is most useful when arguments are value types such as structures where copy operations are more expensive than passing by reference.</span></span>

> [!WARNING]
>  <span data-ttu-id="9cd62-121">若誤用，`in` 參數所耗費的資源可能更高。</span><span class="sxs-lookup"><span data-stu-id="9cd62-121">`in` parameters can be even more expensive if misused.</span></span> <span data-ttu-id="9cd62-122">編譯器無法得知成員方法是否會修改結構狀態。</span><span class="sxs-lookup"><span data-stu-id="9cd62-122">The compiler may not know if member methods modify the state of the struct.</span></span> <span data-ttu-id="9cd62-123">每當編譯器不確定物件是否未經過修改時，會為了防禦而建立複本，並使用該複本呼叫成員參考。</span><span class="sxs-lookup"><span data-stu-id="9cd62-123">Whenever the compiler cannot ensure that the object is not modified, it defensively creates a copy and calls member references using that copy.</span></span> <span data-ttu-id="9cd62-124">任何可能的修改皆僅會修改防禦複本。</span><span class="sxs-lookup"><span data-stu-id="9cd62-124">Any possible modifications are to that defensive copy.</span></span> <span data-ttu-id="9cd62-125">有兩種方式可避免這些複本，其一是將 `in` 參數作為 `in` 引數傳遞，其二是將結構定義為 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="9cd62-125">The two ways to avoid these copies are to pass `in` parameters as `in` arguments or to define structures as `readonly struct`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9cd62-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9cd62-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9cd62-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cd62-127">See Also</span></span>  
 [<span data-ttu-id="9cd62-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9cd62-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9cd62-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9cd62-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9cd62-130">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9cd62-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9cd62-131">方法參數</span><span class="sxs-lookup"><span data-stu-id="9cd62-131">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="9cd62-132">具備實值型別的參考語意</span><span class="sxs-lookup"><span data-stu-id="9cd62-132">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
