---
title: goto 陳述式 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: d4fd9f1f26b82b409d704c45e4bcf18cceef8282
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507519"
---
# <a name="goto-c-reference"></a><span data-ttu-id="e0ad3-102">goto (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e0ad3-102">goto (C# Reference)</span></span>

<span data-ttu-id="e0ad3-103">`goto` 陳述式會將程式控制權直接轉移到標記陳述式。</span><span class="sxs-lookup"><span data-stu-id="e0ad3-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="e0ad3-104">`goto` 的一個常見用法是將控制權轉移到特定的切換案例標籤，或 `switch` 陳述式中的預設標籤。</span><span class="sxs-lookup"><span data-stu-id="e0ad3-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="e0ad3-105">`goto` 陳述式也適用於跳出深度巢狀的迴圈。</span><span class="sxs-lookup"><span data-stu-id="e0ad3-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="e0ad3-106">範例</span><span class="sxs-lookup"><span data-stu-id="e0ad3-106">Example</span></span>

<span data-ttu-id="e0ad3-107">下列範例示範如何在 [switch](switch.md) 陳述式中使用 `goto`。</span><span class="sxs-lookup"><span data-stu-id="e0ad3-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="e0ad3-108">範例</span><span class="sxs-lookup"><span data-stu-id="e0ad3-108">Example</span></span>

<span data-ttu-id="e0ad3-109">下列範例示範如何使用 `goto` 跳出巢狀迴圈。</span><span class="sxs-lookup"><span data-stu-id="e0ad3-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="e0ad3-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e0ad3-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e0ad3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0ad3-111">See also</span></span>

- [<span data-ttu-id="e0ad3-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e0ad3-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="e0ad3-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e0ad3-113">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="e0ad3-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e0ad3-114">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="e0ad3-115">goto 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="e0ad3-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)  
- [<span data-ttu-id="e0ad3-116">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="e0ad3-116">Jump Statements</span></span>](jump-statements.md)  
