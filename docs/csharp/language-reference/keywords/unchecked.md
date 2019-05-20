---
title: unchecked 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 0d96b9af0eaee81da8532c1facbfa8b1d1a8128f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633502"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="a84d7-102">unchecked (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a84d7-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="a84d7-103">`unchecked` 關鍵字是用來抑制整數類型算術運算和轉換的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="a84d7-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="a84d7-104">在未檢查的內容中，如果運算式產生不在目的類型範圍內的值，則不會標示溢位。</span><span class="sxs-lookup"><span data-stu-id="a84d7-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="a84d7-105">例如，因為是在 `unchecked` 區塊或運算式中執行下列範例中的計算，所以會忽略整數結果太大的事實，而且 `int1` 會獲指派 -2,147,483,639 值。</span><span class="sxs-lookup"><span data-stu-id="a84d7-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="a84d7-106">如果移除 `unchecked` 環境，則會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="a84d7-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="a84d7-107">因為運算式的所有項目都是常數，所以會在編譯時期偵測到溢位。</span><span class="sxs-lookup"><span data-stu-id="a84d7-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="a84d7-108">預設不會在編譯時期和執行階段檢查包含非常數項目的運算式。</span><span class="sxs-lookup"><span data-stu-id="a84d7-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="a84d7-109">如需啟用已檢查環境的資訊，請參閱 [checked](checked.md)。</span><span class="sxs-lookup"><span data-stu-id="a84d7-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="a84d7-110">因為檢查溢位需要一些時間，所以在沒有溢位危險的情況下使用未檢查的程式碼可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="a84d7-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="a84d7-111">不過，如果可能會發生溢位，則應該使用已檢查過的環境。</span><span class="sxs-lookup"><span data-stu-id="a84d7-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="a84d7-112">範例</span><span class="sxs-lookup"><span data-stu-id="a84d7-112">Example</span></span>

<span data-ttu-id="a84d7-113">這個範例示範如何使用 `unchecked` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a84d7-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="a84d7-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a84d7-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a84d7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a84d7-115">See also</span></span>

- [<span data-ttu-id="a84d7-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a84d7-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="a84d7-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a84d7-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a84d7-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a84d7-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a84d7-119">Checked 與 Unchecked</span><span class="sxs-lookup"><span data-stu-id="a84d7-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="a84d7-120">checked</span><span class="sxs-lookup"><span data-stu-id="a84d7-120">checked</span></span>](checked.md)
