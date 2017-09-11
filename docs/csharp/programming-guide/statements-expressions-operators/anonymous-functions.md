---
title: "匿名函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: 14
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 465097f9e7024ecfa96ecacb3f4377f3e6a44d13
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="4a42c-102">匿名函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4a42c-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="4a42c-103">匿名函式是可用於任何需要委派類型之處的「內嵌」陳述式或運算式。</span><span class="sxs-lookup"><span data-stu-id="4a42c-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="4a42c-104">您可以使用它來初始化具名委派，或改將它傳遞給具名委派類型作為方法參數。</span><span class="sxs-lookup"><span data-stu-id="4a42c-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="4a42c-105">有兩種類型的匿名函式，將在下列主題中個別進行討論︰</span><span class="sxs-lookup"><span data-stu-id="4a42c-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="4a42c-106">[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4a42c-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="4a42c-107">匿名方法</span><span class="sxs-lookup"><span data-stu-id="4a42c-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="4a42c-108">Lambda 運算式可以繫結至運算式樹狀結構，也可以繫結至委派。</span><span class="sxs-lookup"><span data-stu-id="4a42c-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="4a42c-109">C 中的委派演進</span><span class="sxs-lookup"><span data-stu-id="4a42c-109">The Evolution of Delegates in C</span></span>#  
 <span data-ttu-id="4a42c-110">在 C# 1.0 中，您已使用該程式碼中其他地方所定義的方法明確初始化委派，來建立委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a42c-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="4a42c-111">C# 2.0 引進匿名方法概念，用來撰寫可在委派引動過程中執行的未命名內嵌陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="4a42c-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="4a42c-112">C# 3.0 引進 Lambda 運算式，這在概念上與匿名方法類似，但更易懂且更簡潔。</span><span class="sxs-lookup"><span data-stu-id="4a42c-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="4a42c-113">這兩個功能統稱為「匿名函式」**。</span><span class="sxs-lookup"><span data-stu-id="4a42c-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="4a42c-114">一般而言，以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 版和更新版本為目標的應用程式應該使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="4a42c-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="4a42c-115">下列範例示範從 C# 1.0 到 C# 3.0 的委派建立演進：</span><span class="sxs-lookup"><span data-stu-id="4a42c-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 <span data-ttu-id="4a42c-116">[!code-cs[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a42c-116">[!code-cs[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4a42c-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4a42c-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4a42c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a42c-118">See Also</span></span>  
 <span data-ttu-id="4a42c-119">[陳述式、運算式和運算子](../../../csharp/programming-guide/statements-expressions-operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="4a42c-119">[Statements, Expressions, and Operators](../../../csharp/programming-guide/statements-expressions-operators/index.md) </span></span>  
<span data-ttu-id="4a42c-120"> [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="4a42c-120"> [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="4a42c-121"> [委派](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="4a42c-121"> [Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
<span data-ttu-id="4a42c-122"> [運算式樹狀結構](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)</span><span class="sxs-lookup"><span data-stu-id="4a42c-122"> [Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)</span></span>
