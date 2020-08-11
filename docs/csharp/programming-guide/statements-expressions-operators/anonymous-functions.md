---
title: 匿名函式 - C# 程式設計指南
description: 瞭解匿名函式。 您可以使用 lambda 運算式或匿名方法來建立匿名函式。
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 1fde7d535054f09d55018a010468776622ebfba7
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063259"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="5264d-104">匿名函式 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="5264d-104">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="5264d-105">匿名函式是可用於任何需要委派類型之處的「內嵌」陳述式或運算式。</span><span class="sxs-lookup"><span data-stu-id="5264d-105">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="5264d-106">您可以使用它來初始化具名委派，或改將它傳遞給具名委派類型作為方法參數。</span><span class="sxs-lookup"><span data-stu-id="5264d-106">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="5264d-107">您可以使用 [Lambda 運算式](../../language-reference/operators/lambda-expressions.md)或[匿名方法](../../language-reference/operators/delegate-operator.md)來建立匿名函式。</span><span class="sxs-lookup"><span data-stu-id="5264d-107">You can use a [lambda expression](../../language-reference/operators/lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="5264d-108">我們建議使用 Lambda 運算式，因為它們提供更簡潔且更具表達性的方式來撰寫內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="5264d-108">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="5264d-109">不同於匿名方法，某些型別的 Lambda 運算式可以轉換成運算式樹狀架構型別。</span><span class="sxs-lookup"><span data-stu-id="5264d-109">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="5264d-110">C\# 中的委派演進</span><span class="sxs-lookup"><span data-stu-id="5264d-110">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="5264d-111">在 C# 1.0 中，您已使用該程式碼中其他地方所定義的方法明確初始化委派，來建立委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="5264d-111">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="5264d-112">C# 2.0 引進匿名方法概念，用來撰寫可在委派引動過程中執行的未命名內嵌陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="5264d-112">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="5264d-113">C# 3.0 引進 Lambda 運算式，這在概念上與匿名方法類似，但更易懂且更簡潔。</span><span class="sxs-lookup"><span data-stu-id="5264d-113">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="5264d-114">這兩個功能統稱為「匿名函式」\*\*。</span><span class="sxs-lookup"><span data-stu-id="5264d-114">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="5264d-115">一般來說，以 .NET Framework 3.5 或更新版本為目標的應用程式應該使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="5264d-115">In general, applications that target .NET Framework 3.5 or later should use lambda expressions.</span></span>  
  
 <span data-ttu-id="5264d-116">下列範例示範從 C# 1.0 到 C# 3.0 的委派建立演進：</span><span class="sxs-lookup"><span data-stu-id="5264d-116">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5264d-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5264d-117">C# language specification</span></span>

<span data-ttu-id="5264d-118">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="5264d-118">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5264d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5264d-119">See also</span></span>

- [<span data-ttu-id="5264d-120">語句、運算式和運算子</span><span class="sxs-lookup"><span data-stu-id="5264d-120">Statements, Expressions, and Operators</span></span>](./index.md)
- [<span data-ttu-id="5264d-121">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="5264d-121">Lambda Expressions</span></span>](../../language-reference/operators/lambda-expressions.md)
- [<span data-ttu-id="5264d-122">委派</span><span class="sxs-lookup"><span data-stu-id="5264d-122">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="5264d-123">運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="5264d-123">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
