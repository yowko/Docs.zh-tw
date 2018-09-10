---
title: 具名方法委派與匿名方法 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 6d7dcb3c7c6fa8f1d55237504c23cf468aa0e79d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194214"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="66ca0-102">具名方法委派與匿名方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="66ca0-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="66ca0-103">[delegate](../../../csharp/language-reference/keywords/delegate.md) 可以與具名方法產生關聯。</span><span class="sxs-lookup"><span data-stu-id="66ca0-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="66ca0-104">當您使用具名方法具現化委派時，方法會當做參數傳遞，例如：</span><span class="sxs-lookup"><span data-stu-id="66ca0-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="66ca0-105">這會使用具名方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="66ca0-105">This is called using a named method.</span></span> <span data-ttu-id="66ca0-106">使用具名方法建構的委派可封裝[靜態](../../../csharp/language-reference/keywords/static.md)方法或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="66ca0-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="66ca0-107">在舊版 C# 中，要具現化委派只能使用具名方法。</span><span class="sxs-lookup"><span data-stu-id="66ca0-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="66ca0-108">不過，如果建立新方法會產生額外不必要的負荷，C# 可讓您具現化委派，並立即指定呼叫委派時會處理的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="66ca0-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="66ca0-109">區塊可以包含 Lambda 運算式或匿名方法。</span><span class="sxs-lookup"><span data-stu-id="66ca0-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="66ca0-110">如需詳細資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="66ca0-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66ca0-111">備註</span><span class="sxs-lookup"><span data-stu-id="66ca0-111">Remarks</span></span>  
 <span data-ttu-id="66ca0-112">當做委派參數傳遞的方法必須擁有與委派宣告相同的簽章。</span><span class="sxs-lookup"><span data-stu-id="66ca0-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="66ca0-113">委派執行個體可封裝靜態或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="66ca0-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="66ca0-114">即使委派可使用 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數，但仍不建議您用於多點傳送事件委派，因為無從得知將呼叫哪一個委派。</span><span class="sxs-lookup"><span data-stu-id="66ca0-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="66ca0-115">範例 1</span><span class="sxs-lookup"><span data-stu-id="66ca0-115">Example 1</span></span>  
 <span data-ttu-id="66ca0-116">以下是宣告和使用委派的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="66ca0-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="66ca0-117">請注意，委派 `Del` 和相關聯的方法 `MultiplyNumbers` 必須擁有相同的簽章</span><span class="sxs-lookup"><span data-stu-id="66ca0-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="66ca0-118">範例 2</span><span class="sxs-lookup"><span data-stu-id="66ca0-118">Example 2</span></span>  
 <span data-ttu-id="66ca0-119">在下列範例中，一個委派會同時對應到靜態和執行個體方法，並傳回每個方法的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="66ca0-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="66ca0-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="66ca0-120">See Also</span></span>

- [<span data-ttu-id="66ca0-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="66ca0-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="66ca0-122">委派</span><span class="sxs-lookup"><span data-stu-id="66ca0-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="66ca0-123">匿名方法</span><span class="sxs-lookup"><span data-stu-id="66ca0-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="66ca0-124">如何：組合委派 (多點傳送委派)</span><span class="sxs-lookup"><span data-stu-id="66ca0-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
- [<span data-ttu-id="66ca0-125">事件</span><span class="sxs-lookup"><span data-stu-id="66ca0-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)
