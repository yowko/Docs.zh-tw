---
title: 委派 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 3924d070ea012faf33f1d808b92b1328626ef567
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43805451"
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="bf06d-102">委派 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bf06d-102">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="bf06d-103">[委派](../../../csharp/language-reference/keywords/delegate.md)是一種類型，代表具有特定參數清單及傳回型別的方法參考。</span><span class="sxs-lookup"><span data-stu-id="bf06d-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="bf06d-104">當您具現化委派時，可以將其執行個體與任何具有相容簽章和傳回型別的方法產生關聯。</span><span class="sxs-lookup"><span data-stu-id="bf06d-104">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="bf06d-105">您可以透過委派執行個體叫用 (或呼叫) 方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-105">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="bf06d-106">委派可以用來將方法當做引數傳遞給其他方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-106">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="bf06d-107">事件處理常式就是透過委派叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-107">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="bf06d-108">建立自訂方法後，像是 Windows 控制項這樣的類別就會在特定事件發生時呼叫您的方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-108">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="bf06d-109">下列範例將示範委派宣告：</span><span class="sxs-lookup"><span data-stu-id="bf06d-109">The following example shows a delegate declaration:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="bf06d-110">來自符合委派類型之任何可存取類別或結構的任何方法都可以指派給委派。</span><span class="sxs-lookup"><span data-stu-id="bf06d-110">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="bf06d-111">方法可以是靜態或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-111">The method can be either static or an instance method.</span></span> <span data-ttu-id="bf06d-112">如此即可用程式設計的方式變更方法呼叫，也可將新的程式碼插入現有的類別中。</span><span class="sxs-lookup"><span data-stu-id="bf06d-112">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf06d-113">在方法多載的內容中，方法的簽章並不包括傳回值。</span><span class="sxs-lookup"><span data-stu-id="bf06d-113">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="bf06d-114">不過在委派的內容中，簽章卻包含傳回值。</span><span class="sxs-lookup"><span data-stu-id="bf06d-114">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="bf06d-115">換句話說，方法必須與委派擁有相同的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="bf06d-115">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="bf06d-116">由於委派能夠將方法當做參數來參考，因此很適合用來定義回呼方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-116">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="bf06d-117">例如，可以將比較兩個物件的方法參考當成引數傳遞至排序演算法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-117">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="bf06d-118">因為比較程式碼是在獨立的程序中，因此排序演算法可以用較普通的方式撰寫。</span><span class="sxs-lookup"><span data-stu-id="bf06d-118">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="bf06d-119">委派概觀</span><span class="sxs-lookup"><span data-stu-id="bf06d-119">Delegates Overview</span></span>  
 <span data-ttu-id="bf06d-120">委派包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="bf06d-120">Delegates have the following properties:</span></span>  
  
-   <span data-ttu-id="bf06d-121">委派與 C++ 函式指標類似，但為類型安全。</span><span class="sxs-lookup"><span data-stu-id="bf06d-121">Delegates are like C++ function pointers but are type safe.</span></span>  
  
-   <span data-ttu-id="bf06d-122">委派允許將方法當做參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="bf06d-122">Delegates allow methods to be passed as parameters.</span></span>  
  
-   <span data-ttu-id="bf06d-123">委派可用於定義回呼方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-123">Delegates can be used to define callback methods.</span></span>  
  
-   <span data-ttu-id="bf06d-124">您可將委派鏈結在一起，例如，可在單一事件上呼叫多個方法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-124">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
-   <span data-ttu-id="bf06d-125">方法不需要完全符合委派類型。</span><span class="sxs-lookup"><span data-stu-id="bf06d-125">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="bf06d-126">如需詳細資訊，請參閱[在委派中使用差異](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="bf06d-126">For more information, see [Using Variance in Delegates](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
-   <span data-ttu-id="bf06d-127">C# 2.0 版開始引進[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)的概念。此方法能夠以參數的方式傳遞程式碼區塊，取代了個別定義方法的作法。</span><span class="sxs-lookup"><span data-stu-id="bf06d-127">C# version 2.0 introduced the concept of [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="bf06d-128">C# 3.0 引進了 Lambda 運算式，做為更簡潔的內嵌 (Inline) 程式碼區塊撰寫方式。</span><span class="sxs-lookup"><span data-stu-id="bf06d-128">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="bf06d-129">匿名方法與 Lambda 運算式 (在特定內容中) 都會編譯為委派類型。</span><span class="sxs-lookup"><span data-stu-id="bf06d-129">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="bf06d-130">現在，這些功能合稱為「匿名函式」(Anonymous Function)。</span><span class="sxs-lookup"><span data-stu-id="bf06d-130">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="bf06d-131">如需 Lambda 運算式的詳細資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="bf06d-131">For more information about lambda expressions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf06d-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="bf06d-132">In This Section</span></span>  
  
-   [<span data-ttu-id="bf06d-133">使用委派</span><span class="sxs-lookup"><span data-stu-id="bf06d-133">Using Delegates</span></span>](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [<span data-ttu-id="bf06d-134">何時應使用委派，而不使用介面 （C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="bf06d-134">When to Use Delegates Instead of Interfaces (C# Programming Guide)</span></span>](https://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [<span data-ttu-id="bf06d-135">具名方法委派與匿名方法委派</span><span class="sxs-lookup"><span data-stu-id="bf06d-135">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [<span data-ttu-id="bf06d-136">匿名方法</span><span class="sxs-lookup"><span data-stu-id="bf06d-136">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [<span data-ttu-id="bf06d-137">在委派中使用變異數</span><span class="sxs-lookup"><span data-stu-id="bf06d-137">Using Variance in Delegates</span></span>](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [<span data-ttu-id="bf06d-138">如何：組合委派 (多點傳送委派)</span><span class="sxs-lookup"><span data-stu-id="bf06d-138">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [<span data-ttu-id="bf06d-139">如何：宣告和使用委派及將其具現化</span><span class="sxs-lookup"><span data-stu-id="bf06d-139">How to: Declare, Instantiate, and Use a Delegate</span></span>](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="bf06d-140">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bf06d-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="bf06d-141">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="bf06d-141">Featured Book Chapters</span></span>  
 <span data-ttu-id="bf06d-142">[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) (C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案) 中的 [Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="bf06d-142">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="bf06d-143">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="bf06d-143">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf06d-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf06d-144">See Also</span></span>

- <xref:System.Delegate>  
- [<span data-ttu-id="bf06d-145">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bf06d-145">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bf06d-146">事件</span><span class="sxs-lookup"><span data-stu-id="bf06d-146">Events</span></span>](../../../csharp/programming-guide/events/index.md)
