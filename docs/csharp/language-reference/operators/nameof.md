---
title: nameof 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 965b3e96a20906187df4c8693f050c550a747091
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331432"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="926e8-102">nameof 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="926e8-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="926e8-103">`nameof` 運算子會以字串常值格式取得變數、型別或成員的名稱：</span><span class="sxs-lookup"><span data-stu-id="926e8-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="926e8-104">如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。</span><span class="sxs-lookup"><span data-stu-id="926e8-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="926e8-105">`nameof` 運算子會在編譯時間評估，在執行階段則不會有作用。</span><span class="sxs-lookup"><span data-stu-id="926e8-105">The `nameof` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="926e8-106">您可以使用 `nameof` 運算子，讓檢查引數的程式碼更容易維護：</span><span class="sxs-lookup"><span data-stu-id="926e8-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="926e8-107">C# 6 與更新版本提供 `nameof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="926e8-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="926e8-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="926e8-108">C# language specification</span></span>

<span data-ttu-id="926e8-109">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="926e8-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="926e8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="926e8-110">See also</span></span>

- [<span data-ttu-id="926e8-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="926e8-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="926e8-112">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="926e8-112">C# operators</span></span>](index.md)
