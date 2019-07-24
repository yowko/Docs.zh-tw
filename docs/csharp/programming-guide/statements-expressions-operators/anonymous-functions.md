---
title: 匿名函式 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 4d266584e1867a512e4b61e8839fe948aafb007f
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363923"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="13219-102">匿名函式 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="13219-102">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="13219-103">匿名函式是可用於任何需要委派類型之處的「內嵌」陳述式或運算式。</span><span class="sxs-lookup"><span data-stu-id="13219-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="13219-104">您可以使用它來初始化具名委派，或改將它傳遞給具名委派類型作為方法參數。</span><span class="sxs-lookup"><span data-stu-id="13219-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="13219-105">您可以使用 [Lambda 運算式](lambda-expressions.md)或[匿名方法](../../language-reference/operators/delegate-operator.md)來建立匿名函式。</span><span class="sxs-lookup"><span data-stu-id="13219-105">You can use a [lambda expression](lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="13219-106">我們建議使用 Lambda 運算式，因為它們提供更簡潔且更具表達性的方式來撰寫內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="13219-106">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="13219-107">不同於匿名方法，某些型別的 Lambda 運算式可以轉換成運算式樹狀架構型別。</span><span class="sxs-lookup"><span data-stu-id="13219-107">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="13219-108">C\# 中的委派演進</span><span class="sxs-lookup"><span data-stu-id="13219-108">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="13219-109">在 C# 1.0 中，您已使用該程式碼中其他地方所定義的方法明確初始化委派，來建立委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="13219-109">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="13219-110">C# 2.0 引進匿名方法概念，用來撰寫可在委派引動過程中執行的未命名內嵌陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="13219-110">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="13219-111">C# 3.0 引進 Lambda 運算式，這在概念上與匿名方法類似，但更易懂且更簡潔。</span><span class="sxs-lookup"><span data-stu-id="13219-111">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="13219-112">這兩個功能統稱為「匿名函式」  。</span><span class="sxs-lookup"><span data-stu-id="13219-112">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="13219-113">一般而言，以 .NET Framework 3.5 版和更新版本為目標的應用程式應該使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="13219-113">In general, applications that target version 3.5 and later of the .NET Framework should use lambda expressions.</span></span>  
  
 <span data-ttu-id="13219-114">下列範例示範從 C# 1.0 到 C# 3.0 的委派建立演進：</span><span class="sxs-lookup"><span data-stu-id="13219-114">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="13219-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="13219-115">C# language specification</span></span>

<span data-ttu-id="13219-116">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="13219-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13219-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13219-117">See also</span></span>

- [<span data-ttu-id="13219-118">陳述式、運算式和運算子</span><span class="sxs-lookup"><span data-stu-id="13219-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [<span data-ttu-id="13219-119">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="13219-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="13219-120">委派</span><span class="sxs-lookup"><span data-stu-id="13219-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="13219-121">運算式樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="13219-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
