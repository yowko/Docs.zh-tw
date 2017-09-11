---
title: "delegate (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
dev_langs:
- CSharp
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: 24
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 402eedd0c59b5c95e1a9b44faca66ccb4d4e04e7
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="delegate-c-reference"></a><span data-ttu-id="79749-102">delegate (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="79749-102">delegate (C# Reference)</span></span>
<span data-ttu-id="79749-103">委派類型的宣告類似方法簽章。</span><span class="sxs-lookup"><span data-stu-id="79749-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="79749-104">它具有傳回值以及任意類型之任何數目的參數：</span><span class="sxs-lookup"><span data-stu-id="79749-104">It has a return value and any number of parameters of any type:</span></span>  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="79749-105">`delegate` 是可用來封裝具名或匿名方法的參考型別。</span><span class="sxs-lookup"><span data-stu-id="79749-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="79749-106">委派類似 C++ 中的函式指標，但委派是型別安全而且安全的。</span><span class="sxs-lookup"><span data-stu-id="79749-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="79749-107">如需委派的應用程式，請參閱[委派](../../../csharp/programming-guide/delegates/index.md)和[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="79749-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79749-108">備註</span><span class="sxs-lookup"><span data-stu-id="79749-108">Remarks</span></span>  
 <span data-ttu-id="79749-109">委派是[事件](../../../csharp/programming-guide/events/index.md)的基礎。</span><span class="sxs-lookup"><span data-stu-id="79749-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="79749-110">委派的具現化方式是將它與具名或匿名方法建立關聯。</span><span class="sxs-lookup"><span data-stu-id="79749-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="79749-111">如需詳細資訊，請參閱[具名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)和[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="79749-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="79749-112">委派必須使用具有相容傳回型別和輸入參數的方法或 Lambda 運算式進行具現化。</span><span class="sxs-lookup"><span data-stu-id="79749-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="79749-113">如需方法簽章中所允許變異程度的詳細資訊，請參閱 [Variance in Delegates](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) (委派中的變異數)。</span><span class="sxs-lookup"><span data-stu-id="79749-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca).</span></span> <span data-ttu-id="79749-114">若與匿名方法搭配使用，則會一起宣告要與它建立關聯的委派和程式碼。</span><span class="sxs-lookup"><span data-stu-id="79749-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="79749-115">本節討論兩種具現化委派的方式。</span><span class="sxs-lookup"><span data-stu-id="79749-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79749-116">範例</span><span class="sxs-lookup"><span data-stu-id="79749-116">Example</span></span>  
 <span data-ttu-id="79749-117">[!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="79749-117">[!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="79749-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="79749-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="79749-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79749-119">See Also</span></span>  
 <span data-ttu-id="79749-120">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="79749-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="79749-121">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="79749-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="79749-122">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="79749-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="79749-123">[參考型別](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="79749-123">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="79749-124">[委派](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="79749-124">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="79749-125">[事件](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="79749-125">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="79749-126">[具名方法委派與匿名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="79749-126">[Delegates with Named vs. Anonymous Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) </span></span>  
 [<span data-ttu-id="79749-127">匿名方法</span><span class="sxs-lookup"><span data-stu-id="79749-127">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)

