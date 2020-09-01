---
description: goto 陳述式 - C# 參考
title: goto 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128422"
---
# <a name="goto-c-reference"></a><span data-ttu-id="c1822-103">goto (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c1822-103">goto (C# Reference)</span></span>

<span data-ttu-id="c1822-104">`goto` 陳述式會將程式控制權直接轉移到標記陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1822-104">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="c1822-105">`goto` 的一個常見用法是將控制權轉移到特定的切換案例標籤，或 `switch` 陳述式中的預設標籤。</span><span class="sxs-lookup"><span data-stu-id="c1822-105">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="c1822-106">`goto` 陳述式也適用於跳出深度巢狀的迴圈。</span><span class="sxs-lookup"><span data-stu-id="c1822-106">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="c1822-107">範例</span><span class="sxs-lookup"><span data-stu-id="c1822-107">Example</span></span>

<span data-ttu-id="c1822-108">下列範例示範如何在 [switch](switch.md) 陳述式中使用 `goto`。</span><span class="sxs-lookup"><span data-stu-id="c1822-108">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="c1822-109">範例</span><span class="sxs-lookup"><span data-stu-id="c1822-109">Example</span></span>

<span data-ttu-id="c1822-110">下列範例示範如何使用 `goto` 跳出巢狀迴圈。</span><span class="sxs-lookup"><span data-stu-id="c1822-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="c1822-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c1822-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c1822-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1822-112">See also</span></span>

- [<span data-ttu-id="c1822-113">C # 參考</span><span class="sxs-lookup"><span data-stu-id="c1822-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c1822-114">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c1822-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c1822-115">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c1822-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c1822-116">goto 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="c1822-116">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
