---
title: 'nameof 運算式-c # 參考'
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: b00c5f6f97d27290fb3773dcbb422bf9fb4c425b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916781"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="dad4b-102">nameof expression (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="dad4b-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="dad4b-103">`nameof`運算式會產生變數、類型或成員的名稱做為字串常數：</span><span class="sxs-lookup"><span data-stu-id="dad4b-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

<span data-ttu-id="dad4b-104">如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。</span><span class="sxs-lookup"><span data-stu-id="dad4b-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="dad4b-105">在[逐字識別碼](../tokens/verbatim.md)的情況下， `@` 字元不是名稱的一部分，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="dad4b-105">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="dad4b-106">`nameof`運算式會在編譯時期評估，而且在執行時間不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="dad4b-106">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="dad4b-107">您可以使用 `nameof` 運算式，讓引數檢查程式碼更容易維護：</span><span class="sxs-lookup"><span data-stu-id="dad4b-107">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="dad4b-108">`nameof`運算式適用于 c # 6 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="dad4b-108">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dad4b-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="dad4b-109">C# language specification</span></span>

<span data-ttu-id="dad4b-110">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="dad4b-110">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dad4b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dad4b-111">See also</span></span>

- [<span data-ttu-id="dad4b-112">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="dad4b-112">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dad4b-113">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="dad4b-113">C# operators and expressions</span></span>](index.md)
