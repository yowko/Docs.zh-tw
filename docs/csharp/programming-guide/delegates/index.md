---
title: 委派 - C# 程式設計手冊
description: 'C # 中的委派是一種類型，它會參考具有參數清單和傳回類型的方法。 委派可以用來將方法當做引數傳遞給其他方法。'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 2c1be56b67528c17a6cf1d8d8517817ff93b2aa5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063634"
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="dcefe-104">委派 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="dcefe-104">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="dcefe-105">[委派](../../language-reference/builtin-types/reference-types.md)是一種類型，代表具有特定參數清單及傳回型別的方法參考。</span><span class="sxs-lookup"><span data-stu-id="dcefe-105">A [delegate](../../language-reference/builtin-types/reference-types.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="dcefe-106">當您具現化委派時，可以將其執行個體與任何具有相容簽章和傳回型別的方法產生關聯。</span><span class="sxs-lookup"><span data-stu-id="dcefe-106">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="dcefe-107">您可以透過委派執行個體叫用 (或呼叫) 方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-107">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="dcefe-108">委派可以用來將方法當做引數傳遞給其他方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-108">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="dcefe-109">事件處理常式就是透過委派叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-109">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="dcefe-110">建立自訂方法後，像是 Windows 控制項這樣的類別就會在特定事件發生時呼叫您的方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-110">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="dcefe-111">下列範例將示範委派宣告：</span><span class="sxs-lookup"><span data-stu-id="dcefe-111">The following example shows a delegate declaration:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 <span data-ttu-id="dcefe-112">來自符合委派類型之任何可存取類別或結構的任何方法都可以指派給委派。</span><span class="sxs-lookup"><span data-stu-id="dcefe-112">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="dcefe-113">方法可以是靜態或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-113">The method can be either static or an instance method.</span></span> <span data-ttu-id="dcefe-114">如此即可用程式設計的方式變更方法呼叫，也可將新的程式碼插入現有的類別中。</span><span class="sxs-lookup"><span data-stu-id="dcefe-114">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcefe-115">在方法多載的內容中，方法的簽章並不包括傳回值。</span><span class="sxs-lookup"><span data-stu-id="dcefe-115">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="dcefe-116">不過在委派的內容中，簽章卻包含傳回值。</span><span class="sxs-lookup"><span data-stu-id="dcefe-116">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="dcefe-117">換句話說，方法必須與委派擁有相同的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="dcefe-117">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="dcefe-118">由於委派能夠將方法當做參數來參考，因此很適合用來定義回呼方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-118">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="dcefe-119">例如，可以將比較兩個物件的方法參考當成引數傳遞至排序演算法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-119">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="dcefe-120">因為比較程式碼是在獨立的程序中，因此排序演算法可以用較普通的方式撰寫。</span><span class="sxs-lookup"><span data-stu-id="dcefe-120">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="dcefe-121">委派概觀</span><span class="sxs-lookup"><span data-stu-id="dcefe-121">Delegates Overview</span></span>  
 <span data-ttu-id="dcefe-122">委派包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="dcefe-122">Delegates have the following properties:</span></span>  
  
- <span data-ttu-id="dcefe-123">委派與 C++ 函式指標相似，但委派完全為物件導向，而且不像 C++ 指標之於成員函式，會同時委派封裝物件執行個體與方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-123">Delegates are similar to C++ function pointers, but delegates are fully object-oriented, and unlike C++ pointers to member functions, delegates encapsulate both an object instance and a method.</span></span>
  
- <span data-ttu-id="dcefe-124">委派允許將方法當做參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="dcefe-124">Delegates allow methods to be passed as parameters.</span></span>  
  
- <span data-ttu-id="dcefe-125">委派可用於定義回呼方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-125">Delegates can be used to define callback methods.</span></span>  
  
- <span data-ttu-id="dcefe-126">您可將委派鏈結在一起，例如，可在單一事件上呼叫多個方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-126">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
- <span data-ttu-id="dcefe-127">方法不需要完全符合委派類型。</span><span class="sxs-lookup"><span data-stu-id="dcefe-127">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="dcefe-128">如需詳細資訊，請參閱[在委派中使用差異](../concepts/covariance-contravariance/using-variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="dcefe-128">For more information, see [Using Variance in Delegates](../concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
- <span data-ttu-id="dcefe-129">C # 版本2.0 引進了[匿名方法](../../language-reference/operators/delegate-operator.md)的概念，可讓程式碼區塊當做參數傳遞，以取代個別定義的方法。</span><span class="sxs-lookup"><span data-stu-id="dcefe-129">C# version 2.0 introduced the concept of [anonymous methods](../../language-reference/operators/delegate-operator.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="dcefe-130">C# 3.0 引進了 Lambda 運算式，做為更簡潔的內嵌 (Inline) 程式碼區塊撰寫方式。</span><span class="sxs-lookup"><span data-stu-id="dcefe-130">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="dcefe-131">匿名方法與 Lambda 運算式 (在特定內容中) 都會編譯為委派類型。</span><span class="sxs-lookup"><span data-stu-id="dcefe-131">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="dcefe-132">現在，這些功能合稱為「匿名函式」(Anonymous Function)。</span><span class="sxs-lookup"><span data-stu-id="dcefe-132">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="dcefe-133">如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../language-reference/operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="dcefe-133">For more information about lambda expressions, see [Lambda expressions](../../language-reference/operators/lambda-expressions.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="dcefe-134">本節內容</span><span class="sxs-lookup"><span data-stu-id="dcefe-134">In This Section</span></span>  
  
- [<span data-ttu-id="dcefe-135">使用委派</span><span class="sxs-lookup"><span data-stu-id="dcefe-135">Using Delegates</span></span>](./using-delegates.md)  
  
- <span data-ttu-id="dcefe-136">[何時應使用委派，而不使用介面 (C# 程式設計指南)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dcefe-136">[When to Use Delegates Instead of Interfaces (C# Programming Guide)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span></span>  
  
- [<span data-ttu-id="dcefe-137">具名方法委派與匿名方法</span><span class="sxs-lookup"><span data-stu-id="dcefe-137">Delegates with Named vs. Anonymous Methods</span></span>](./delegates-with-named-vs-anonymous-methods.md)  
  
- [<span data-ttu-id="dcefe-138">在委派中使用變異數</span><span class="sxs-lookup"><span data-stu-id="dcefe-138">Using Variance in Delegates</span></span>](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [<span data-ttu-id="dcefe-139">如何將委派結合 (多播委派) </span><span class="sxs-lookup"><span data-stu-id="dcefe-139">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)  
  
- [<span data-ttu-id="dcefe-140">如何宣告、具現化和使用委派</span><span class="sxs-lookup"><span data-stu-id="dcefe-140">How to declare, instantiate, and use a delegate</span></span>](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a><span data-ttu-id="dcefe-141">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="dcefe-141">C# Language Specification</span></span>  

<span data-ttu-id="dcefe-142">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的[委派](~/_csharplang/spec/delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="dcefe-142">For more information, see [Delegates](~/_csharplang/spec/delegates.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="dcefe-143">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="dcefe-143">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="dcefe-144">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="dcefe-144">Featured Book Chapters</span></span>  
 <span data-ttu-id="dcefe-145">[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案) 中的 [Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="dcefe-145">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="dcefe-146">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="dcefe-146">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcefe-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcefe-147">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="dcefe-148">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dcefe-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dcefe-149">事件</span><span class="sxs-lookup"><span data-stu-id="dcefe-149">Events</span></span>](../events/index.md)
