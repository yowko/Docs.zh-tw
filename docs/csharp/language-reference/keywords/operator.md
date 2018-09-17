---
title: operator 關鍵字 (C# 參考)
description: 了解如何多載內建 C# 運算子
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 1e11d7767b61becc39b1158fae9cb2abe997e4bd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560158"
---
# <a name="operator-c-reference"></a><span data-ttu-id="cdd39-103">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cdd39-103">operator (C# Reference)</span></span>

<span data-ttu-id="cdd39-104">使用 `operator` 關鍵字多載內建運算子，或在類別或結構宣告中提供使用者定義的轉換。</span><span class="sxs-lookup"><span data-stu-id="cdd39-104">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

<span data-ttu-id="cdd39-105">若要在自訂類別或結構上多載運算子，您可以在對應類型中建立運算子宣告。</span><span class="sxs-lookup"><span data-stu-id="cdd39-105">To overload an operator on a custom class or struct, you create an operator declaration in the corresponding type.</span></span> <span data-ttu-id="cdd39-106">多載內建 C# 運算子的運算子宣告必須滿足下列規則：</span><span class="sxs-lookup"><span data-stu-id="cdd39-106">The operator declaration that overloads a built-in C# operator must satisfy the following rules:</span></span>

- <span data-ttu-id="cdd39-107">它包含 `public` 和 `static` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="cdd39-107">It includes both a `public` and a `static` modifier.</span></span>
- <span data-ttu-id="cdd39-108">它包含 `operator X`，其中 `X` 是所要多載之運算子的名稱或符號。</span><span class="sxs-lookup"><span data-stu-id="cdd39-108">It includes `operator X` where `X` is the name or symbol of the operator being overloaded.</span></span>
- <span data-ttu-id="cdd39-109">一元運算子有一個參數，而二元運算子有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="cdd39-109">Unary operators have one parameter, and binary operators have two parameters.</span></span> <span data-ttu-id="cdd39-110">在各案例中，至少一個參數必須與宣告運算子的類別或結構擁有相同的類型。</span><span class="sxs-lookup"><span data-stu-id="cdd39-110">In each case, at least one parameter must be the same type as the class or struct that declares the operator.</span></span>

<span data-ttu-id="cdd39-111">如需如何定義轉換運算子的資訊，請參閱 [explicit](explicit.md) 和 [implicit](implicit.md) 關鍵字文章。</span><span class="sxs-lookup"><span data-stu-id="cdd39-111">For information about how to define conversion operators, see the [explicit](explicit.md) and [implicit](implicit.md) keyword articles.</span></span>

<span data-ttu-id="cdd39-112">如需可多載的 C# 運算子概觀，請參閱[可多載的運算子](../../programming-guide/statements-expressions-operators/overloadable-operators.md)一文。</span><span class="sxs-lookup"><span data-stu-id="cdd39-112">For an overview of the C# operators that can be overloaded, see the [Overloadable operators](../../programming-guide/statements-expressions-operators/overloadable-operators.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="cdd39-113">範例</span><span class="sxs-lookup"><span data-stu-id="cdd39-113">Example</span></span>

<span data-ttu-id="cdd39-114">下列範例定義 `Fraction` 類型，表示分數。</span><span class="sxs-lookup"><span data-stu-id="cdd39-114">The following example defines a `Fraction` type that represents fractional numbers.</span></span> <span data-ttu-id="cdd39-115">它會多載 `+` 和 `*` 運算子，以執行分數的加法和乘法，也提供將 `Fraction` 類型轉換成 `double` 類型的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cdd39-115">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="cdd39-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="cdd39-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cdd39-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdd39-117">See also</span></span>

- [<span data-ttu-id="cdd39-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cdd39-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cdd39-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cdd39-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cdd39-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="cdd39-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cdd39-121">implicit</span><span class="sxs-lookup"><span data-stu-id="cdd39-121">implicit</span></span>](implicit.md)
- [<span data-ttu-id="cdd39-122">explicit</span><span class="sxs-lookup"><span data-stu-id="cdd39-122">explicit</span></span>](explicit.md)
- [<span data-ttu-id="cdd39-123">多載運算子</span><span class="sxs-lookup"><span data-stu-id="cdd39-123">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="cdd39-124">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="cdd39-124">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
