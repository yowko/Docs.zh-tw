---
title: delegate 運算子 - C# 參考
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1fe281776bd75d8fa869065cd24e85f04fec849d
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331827"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="fcb75-102">delegate 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="fcb75-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="fcb75-103">`delegate` 運算子會建立可轉換成委派型別的匿名方法：</span><span class="sxs-lookup"><span data-stu-id="fcb75-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

<span data-ttu-id="fcb75-104">從 C# 3 開始，[Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)提供更精簡且更具表達性的方式來建立匿名函式。</span><span class="sxs-lookup"><span data-stu-id="fcb75-104">Beginning with C# 3, [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="fcb75-105">使用 [=> 運算子](lambda-operator.md)來建構 Lambda 運算式：</span><span class="sxs-lookup"><span data-stu-id="fcb75-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>

[!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]

<span data-ttu-id="fcb75-106">當您使用 `delegate` 運算子時，您可以省略參數清單。</span><span class="sxs-lookup"><span data-stu-id="fcb75-106">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="fcb75-107">如果您這樣做，則可以將建立的匿名方法轉換成含任何參數清單的委派型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fcb75-107">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="fcb75-108">那是 Lambda 運算式不支援的唯一匿名方法功能。</span><span class="sxs-lookup"><span data-stu-id="fcb75-108">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="fcb75-109">在所有其他情況下，建議您以 Lambda 運算式的方式來撰寫內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="fcb75-109">In all other cases, a lambda expression is a preferred way to write inline code.</span></span> <span data-ttu-id="fcb75-110">如需 Lambda 運算式功能的詳細資訊 (例如，捕捉外部變數)，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="fcb75-110">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="fcb75-111">您也可以使用 `delegate` 關鍵字來宣告[委派型別](../builtin-types/reference-types.md#the-delegate-type)。</span><span class="sxs-lookup"><span data-stu-id="fcb75-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fcb75-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="fcb75-112">C# language specification</span></span>

<span data-ttu-id="fcb75-113">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="fcb75-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcb75-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb75-114">See also</span></span>

- [<span data-ttu-id="fcb75-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="fcb75-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fcb75-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="fcb75-116">C# operators</span></span>](index.md)
