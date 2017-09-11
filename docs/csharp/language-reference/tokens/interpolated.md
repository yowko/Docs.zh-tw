---
title: "$ (C# 參考)"
ms.date: 2017-02-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
dev_langs:
- CSharp
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 65dfc7b28059c4d41dd9113fd60c6a64987bfc2b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-c-reference"></a><span data-ttu-id="a65df-102">$ (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a65df-102">$ (C# Reference)</span></span>

<span data-ttu-id="a65df-103">將字串常值識別為[字串插值](../keywords/interpolated-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="a65df-103">Identifies a string literal as an [interpolated string](../keywords/interpolated-strings.md).</span></span> <span data-ttu-id="a65df-104">字串插值是類似範本的字串，其中包含常值文字及「插入運算式」。</span><span class="sxs-lookup"><span data-stu-id="a65df-104">An interpolated string is a template-like string that contains literal text along with *interpolated expressions*.</span></span> <span data-ttu-id="a65df-105">解析字串插值時 (例如在指派陳述式或方法呼叫中)，其插入運算式會以運算式在結果字串中的字串表示取代。</span><span class="sxs-lookup"><span data-stu-id="a65df-105">When the interpolated string is resolved, for example in an assignment statement or a method call, its interpolated expressions are replaced by their string representations in the result string.</span></span> <span data-ttu-id="a65df-106">字串插值會以 .NET Framework 支援的[複合格式字串](../../../standard/base-types/composite-format.md)取代。</span><span class="sxs-lookup"><span data-stu-id="a65df-106">Interpolated strings are replacements for the [composite format strings](../../../standard/base-types/composite-format.md) supported by the .NET Framework.</span></span>

<span data-ttu-id="a65df-107">下列範例使用 `$` 字元來定義字串插值。</span><span class="sxs-lookup"><span data-stu-id="a65df-107">The following example uses the `$` character to define an interpolated string.</span></span>

<span data-ttu-id="a65df-108">[!CODE-cs[字串插值符號](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="a65df-108">[!CODE-cs[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]</span></span>

<span data-ttu-id="a65df-109">如需字串插值的詳細資訊，請參閱[字串插值](../keywords/interpolated-strings.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a65df-109">For more information on interpolated strings, see the [Interpolated Strings](../keywords/interpolated-strings.md) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="a65df-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a65df-110">See Also</span></span>  
 <span data-ttu-id="a65df-111">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a65df-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="a65df-112">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a65df-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="a65df-113">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="a65df-113">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)

