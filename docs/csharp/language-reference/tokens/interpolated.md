---
title: "$ (C# 參考)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d245bab063721abdb930aae113aab2094553b9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a><span data-ttu-id="5d9df-102">$ (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5d9df-102">$ (C# Reference)</span></span>

<span data-ttu-id="5d9df-103">將字串常值識別為[字串插值](../keywords/interpolated-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="5d9df-103">Identifies a string literal as an [interpolated string](../keywords/interpolated-strings.md).</span></span> <span data-ttu-id="5d9df-104">字串插值是類似範本的字串，其中包含常值文字及「插入運算式」。</span><span class="sxs-lookup"><span data-stu-id="5d9df-104">An interpolated string is a template-like string that contains literal text along with *interpolated expressions*.</span></span> <span data-ttu-id="5d9df-105">解析字串插值時 (例如在指派陳述式或方法呼叫中)，其插入運算式會以運算式在結果字串中的字串表示取代。</span><span class="sxs-lookup"><span data-stu-id="5d9df-105">When the interpolated string is resolved, for example in an assignment statement or a method call, its interpolated expressions are replaced by their string representations in the result string.</span></span> <span data-ttu-id="5d9df-106">字串插值會以 .NET Framework 支援的[複合格式字串](../../../standard/base-types/composite-format.md)取代。</span><span class="sxs-lookup"><span data-stu-id="5d9df-106">Interpolated strings are replacements for the [composite format strings](../../../standard/base-types/composite-format.md) supported by the .NET Framework.</span></span>

<span data-ttu-id="5d9df-107">下列範例使用 `$` 字元來定義字串插值。</span><span class="sxs-lookup"><span data-stu-id="5d9df-107">The following example uses the `$` character to define an interpolated string.</span></span>

[!code-csharp[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]

<span data-ttu-id="5d9df-108">如需字串插值的詳細資訊，請參閱[字串插值](../keywords/interpolated-strings.md)主題。</span><span class="sxs-lookup"><span data-stu-id="5d9df-108">For more information on interpolated strings, see the [Interpolated Strings](../keywords/interpolated-strings.md) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d9df-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d9df-109">See Also</span></span>  
 [<span data-ttu-id="5d9df-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5d9df-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5d9df-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5d9df-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d9df-112">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="5d9df-112">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
