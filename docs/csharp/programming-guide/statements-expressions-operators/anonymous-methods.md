---
title: "匿名方法 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d942e0f3245f6404c896173b2c7ca6f1090a8c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="bdd45-102">匿名方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bdd45-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="bdd45-103">在 C# 2.0 版之前，宣告[委派](../../../csharp/language-reference/keywords/delegate.md)的唯一方式是使用[具名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="bdd45-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="bdd45-104">C# 2.0 引入了匿名方法，而在 C# 3.0 和更新版本中，則是以 lambda 運算式取代匿名方法，成為撰寫程式碼內嵌的慣用方式。</span><span class="sxs-lookup"><span data-stu-id="bdd45-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="bdd45-105">不過，本主題中的匿名方法相關資訊也適用於 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="bdd45-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="bdd45-106">有一種情況，是匿名方法提供了 lambda 運算式沒有的功能。</span><span class="sxs-lookup"><span data-stu-id="bdd45-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="bdd45-107">匿名方法能讓您省略參數清單。</span><span class="sxs-lookup"><span data-stu-id="bdd45-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="bdd45-108">這表示，匿名方法可以轉換成有各種不同簽章的委派。</span><span class="sxs-lookup"><span data-stu-id="bdd45-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="bdd45-109">這在 lambda 運算式是不可能的。</span><span class="sxs-lookup"><span data-stu-id="bdd45-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="bdd45-110">如需專門針對 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="bdd45-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="bdd45-111">建立匿名方法，其實是將程式碼區塊當成委派參數傳遞的方法。</span><span class="sxs-lookup"><span data-stu-id="bdd45-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="bdd45-112">以下是兩個範例：</span><span class="sxs-lookup"><span data-stu-id="bdd45-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 <span data-ttu-id="bdd45-113">使用匿名方法，您可以減少在具現化委派中撰寫程式碼的額外負荷，因為您不必另外建立一個方法。</span><span class="sxs-lookup"><span data-stu-id="bdd45-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="bdd45-114">例如，在必須建立某方法的情況下，而此方法可能不是那麼有必要的額外負荷時，指定程式碼區塊而不指定委派會很有用。</span><span class="sxs-lookup"><span data-stu-id="bdd45-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="bdd45-115">啟動新的執行緒時即是很好的範例。</span><span class="sxs-lookup"><span data-stu-id="bdd45-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="bdd45-116">這個類別會建立執行緒，而且也包含執行緒執行的程式碼，不需要為委派建立額外的方法。</span><span class="sxs-lookup"><span data-stu-id="bdd45-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="bdd45-117">備註</span><span class="sxs-lookup"><span data-stu-id="bdd45-117">Remarks</span></span>  
 <span data-ttu-id="bdd45-118">匿名方法的參數範圍是「匿名方法區塊」。</span><span class="sxs-lookup"><span data-stu-id="bdd45-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="bdd45-119">如果目標在區塊外，它是在匿名方法區塊內有跳躍陳述式的錯誤，例如 [goto](../../../csharp/language-reference/keywords/goto.md)、[break](../../../csharp/language-reference/keywords/break.md) 或 [continue](../../../csharp/language-reference/keywords/continue.md)。</span><span class="sxs-lookup"><span data-stu-id="bdd45-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="bdd45-120">如果目標在區塊內，它也是在匿名方法區塊外有跳躍陳述式的錯誤，例如 `goto`、`break` 或 `continue`。</span><span class="sxs-lookup"><span data-stu-id="bdd45-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="bdd45-121">範圍包含匿名方法宣告的本機變數和參數，稱為匿名方法的「外部」變數。</span><span class="sxs-lookup"><span data-stu-id="bdd45-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="bdd45-122">例如，在下列程式碼片段中，`n` 即為外部變數：</span><span class="sxs-lookup"><span data-stu-id="bdd45-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 <span data-ttu-id="bdd45-123">外部變數 `n` 的參考會在建立委派時「擷取」。</span><span class="sxs-lookup"><span data-stu-id="bdd45-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="bdd45-124">不同於本機變數，已擷取變數的存留期會延伸至參考匿名方法的委派符合記憶體回收資格。</span><span class="sxs-lookup"><span data-stu-id="bdd45-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="bdd45-125">匿名方法無法存取外部範圍的 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="bdd45-125">An anonymous method cannot access the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="bdd45-126">無法存取「匿名方法區塊」內的任何不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdd45-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="bdd45-127">匿名方法不可出現在 [is](../../../csharp/language-reference/keywords/is.md) 運算子的左邊。</span><span class="sxs-lookup"><span data-stu-id="bdd45-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd45-128">範例</span><span class="sxs-lookup"><span data-stu-id="bdd45-128">Example</span></span>  
 <span data-ttu-id="bdd45-129">下例示範兩種具現化委派的方式：</span><span class="sxs-lookup"><span data-stu-id="bdd45-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="bdd45-130">建立委派與匿名方法的關聯。</span><span class="sxs-lookup"><span data-stu-id="bdd45-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="bdd45-131">建立委派與具名方法 (`DoWork`) 的關聯。</span><span class="sxs-lookup"><span data-stu-id="bdd45-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="bdd45-132">在每個案例中，叫用委派時即會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="bdd45-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bdd45-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdd45-133">See Also</span></span>  
 [<span data-ttu-id="bdd45-134">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bdd45-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bdd45-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bdd45-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bdd45-136">委派</span><span class="sxs-lookup"><span data-stu-id="bdd45-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="bdd45-137">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="bdd45-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="bdd45-138">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="bdd45-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="bdd45-139">方法</span><span class="sxs-lookup"><span data-stu-id="bdd45-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="bdd45-140">具名方法委派與匿名方法委派</span><span class="sxs-lookup"><span data-stu-id="bdd45-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
