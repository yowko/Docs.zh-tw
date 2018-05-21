---
title: delegate (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: 4eafd0ffb6da191db80fd69f1980a167dbfc742b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="delegate-c-reference"></a><span data-ttu-id="6216f-102">delegate (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6216f-102">delegate (C# Reference)</span></span>
<span data-ttu-id="6216f-103">委派類型的宣告類似方法簽章。</span><span class="sxs-lookup"><span data-stu-id="6216f-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="6216f-104">它具有傳回值以及任意類型之任何數目的參數：</span><span class="sxs-lookup"><span data-stu-id="6216f-104">It has a return value and any number of parameters of any type:</span></span>  
  
```csharp  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="6216f-105">`delegate` 是可用來封裝具名或匿名方法的參考型別。</span><span class="sxs-lookup"><span data-stu-id="6216f-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="6216f-106">委派類似 C++ 中的函式指標，但委派是型別安全而且安全的。</span><span class="sxs-lookup"><span data-stu-id="6216f-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="6216f-107">如需委派的應用程式，請參閱[委派](../../../csharp/programming-guide/delegates/index.md)和[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="6216f-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6216f-108">備註</span><span class="sxs-lookup"><span data-stu-id="6216f-108">Remarks</span></span>  
 <span data-ttu-id="6216f-109">委派是[事件](../../../csharp/programming-guide/events/index.md)的基礎。</span><span class="sxs-lookup"><span data-stu-id="6216f-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="6216f-110">委派的具現化方式是將它與具名或匿名方法建立關聯。</span><span class="sxs-lookup"><span data-stu-id="6216f-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="6216f-111">如需詳細資訊，請參閱[具名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)和[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="6216f-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="6216f-112">委派必須使用具有相容傳回型別和輸入參數的方法或 Lambda 運算式進行具現化。</span><span class="sxs-lookup"><span data-stu-id="6216f-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="6216f-113">如需方法簽章中所允許變異程度的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) (委派中的變異數)。</span><span class="sxs-lookup"><span data-stu-id="6216f-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="6216f-114">若與匿名方法搭配使用，則會一起宣告要與它建立關聯的委派和程式碼。</span><span class="sxs-lookup"><span data-stu-id="6216f-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="6216f-115">本節討論兩種具現化委派的方式。</span><span class="sxs-lookup"><span data-stu-id="6216f-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6216f-116">範例</span><span class="sxs-lookup"><span data-stu-id="6216f-116">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6216f-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6216f-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6216f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="6216f-118">See Also</span></span>  
 [<span data-ttu-id="6216f-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6216f-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6216f-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6216f-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6216f-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="6216f-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6216f-122">參考型別</span><span class="sxs-lookup"><span data-stu-id="6216f-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="6216f-123">委派</span><span class="sxs-lookup"><span data-stu-id="6216f-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="6216f-124">事件</span><span class="sxs-lookup"><span data-stu-id="6216f-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="6216f-125">具名方法委派與匿名方法委派</span><span class="sxs-lookup"><span data-stu-id="6216f-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [<span data-ttu-id="6216f-126">匿名方法</span><span class="sxs-lookup"><span data-stu-id="6216f-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
