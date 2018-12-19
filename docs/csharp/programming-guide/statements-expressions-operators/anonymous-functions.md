---
title: 匿名函式 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 9e0225960f16756820cdc095668cf7acfd4395cb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242863"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="f4734-102">匿名函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f4734-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="f4734-103">匿名函式是可用於任何需要委派類型之處的「內嵌」陳述式或運算式。</span><span class="sxs-lookup"><span data-stu-id="f4734-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="f4734-104">您可以使用它來初始化具名委派，或改將它傳遞給具名委派類型作為方法參數。</span><span class="sxs-lookup"><span data-stu-id="f4734-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="f4734-105">有兩種類型的匿名函式，將在下列主題中個別進行討論︰</span><span class="sxs-lookup"><span data-stu-id="f4734-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="f4734-106">[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f4734-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="f4734-107">匿名方法</span><span class="sxs-lookup"><span data-stu-id="f4734-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="f4734-108">Lambda 運算式可以繫結至運算式樹狀結構，也可以繫結至委派。</span><span class="sxs-lookup"><span data-stu-id="f4734-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="f4734-109">C# 中的委派演進</span><span class="sxs-lookup"><span data-stu-id="f4734-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="f4734-110">在 C# 1.0 中，您已使用該程式碼中其他地方所定義的方法明確初始化委派，來建立委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="f4734-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="f4734-111">C# 2.0 引進匿名方法概念，用來撰寫可在委派引動過程中執行的未命名內嵌陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="f4734-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="f4734-112">C# 3.0 引進 Lambda 運算式，這在概念上與匿名方法類似，但更易懂且更簡潔。</span><span class="sxs-lookup"><span data-stu-id="f4734-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="f4734-113">這兩個功能統稱為「匿名函式」。</span><span class="sxs-lookup"><span data-stu-id="f4734-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="f4734-114">一般而言，以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版和更新版本為目標的應用程式應該使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="f4734-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="f4734-115">下列範例示範從 C# 1.0 到 C# 3.0 的委派建立演進：</span><span class="sxs-lookup"><span data-stu-id="f4734-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f4734-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f4734-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4734-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4734-117">See Also</span></span>

- [<span data-ttu-id="f4734-118">陳述式、運算式和運算子</span><span class="sxs-lookup"><span data-stu-id="f4734-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
- [<span data-ttu-id="f4734-119">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="f4734-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [<span data-ttu-id="f4734-120">委派</span><span class="sxs-lookup"><span data-stu-id="f4734-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="f4734-121">運算式樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="f4734-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)  
