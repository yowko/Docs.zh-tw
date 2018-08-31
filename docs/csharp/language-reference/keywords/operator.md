---
title: operator 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929868"
---
# <a name="operator-c-reference"></a><span data-ttu-id="bf58c-102">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bf58c-102">operator (C# Reference)</span></span>

<span data-ttu-id="bf58c-103">使用 `operator` 關鍵字多載內建運算子，或在類別或結構宣告中提供使用者定義的轉換。</span><span class="sxs-lookup"><span data-stu-id="bf58c-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

## <a name="example"></a><span data-ttu-id="bf58c-104">範例</span><span class="sxs-lookup"><span data-stu-id="bf58c-104">Example</span></span>

<span data-ttu-id="bf58c-105">以下是極簡化的分數類別。</span><span class="sxs-lookup"><span data-stu-id="bf58c-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="bf58c-106">它會多載 `+` 和 `*` 運算子，以執行分數的加法和乘法，也提供將 `Fraction` 類型轉換成 `double` 類型的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="bf58c-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="bf58c-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bf58c-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bf58c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf58c-108">See also</span></span>

- [<span data-ttu-id="bf58c-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bf58c-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bf58c-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bf58c-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bf58c-111">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bf58c-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bf58c-112">implicit</span><span class="sxs-lookup"><span data-stu-id="bf58c-112">implicit</span></span>](implicit.md)
- [<span data-ttu-id="bf58c-113">explicit</span><span class="sxs-lookup"><span data-stu-id="bf58c-113">explicit</span></span>](explicit.md)
- [<span data-ttu-id="bf58c-114">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="bf58c-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
