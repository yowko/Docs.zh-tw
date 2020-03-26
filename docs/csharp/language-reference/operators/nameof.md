---
title: 運算式的名稱 - C# 引用
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507135"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="6f6b7-102">運算式的名稱（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="6f6b7-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="6f6b7-103">運算式`nameof`生成變數、類型或成員的名稱作為字串常量：</span><span class="sxs-lookup"><span data-stu-id="6f6b7-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="6f6b7-104">如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。</span><span class="sxs-lookup"><span data-stu-id="6f6b7-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="6f6b7-105">運算式`nameof`在編譯時計算，在運行時不起作用。</span><span class="sxs-lookup"><span data-stu-id="6f6b7-105">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="6f6b7-106">可以使用運算式`nameof`使參數檢查代碼更可維護：</span><span class="sxs-lookup"><span data-stu-id="6f6b7-106">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="6f6b7-107">`nameof`運算式在 C# 6 及更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="6f6b7-107">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6f6b7-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6f6b7-108">C# language specification</span></span>

<span data-ttu-id="6f6b7-109">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="6f6b7-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f6b7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f6b7-110">See also</span></span>

- [<span data-ttu-id="6f6b7-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6f6b7-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6f6b7-112">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6f6b7-112">C# operators</span></span>](index.md)
