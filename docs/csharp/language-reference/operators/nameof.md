---
title: nameof 運算子 - C# 參考
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846268"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="904b0-102">nameof 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="904b0-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="904b0-103">`nameof` 運算子會以字串常值格式取得變數、型別或成員的名稱：</span><span class="sxs-lookup"><span data-stu-id="904b0-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="904b0-104">如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。</span><span class="sxs-lookup"><span data-stu-id="904b0-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="904b0-105">運算子`nameof`在編譯時計算，在運行時無效。</span><span class="sxs-lookup"><span data-stu-id="904b0-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="904b0-106">您可以使用 `nameof` 運算子，讓檢查引數的程式碼更容易維護：</span><span class="sxs-lookup"><span data-stu-id="904b0-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="904b0-107">C# 6 與更新版本提供 `nameof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="904b0-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="904b0-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="904b0-108">C# language specification</span></span>

<span data-ttu-id="904b0-109">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="904b0-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="904b0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="904b0-110">See also</span></span>

- [<span data-ttu-id="904b0-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="904b0-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="904b0-112">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="904b0-112">C# operators</span></span>](index.md)
