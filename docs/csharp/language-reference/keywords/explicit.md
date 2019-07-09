---
title: explicit 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: a260c6f1ccac6e09770f1cb8f43d5d872b4b2650
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610106"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="7b873-102">explicit (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7b873-102">explicit (C# Reference)</span></span>

<span data-ttu-id="7b873-103">`explicit` 關鍵字會宣告必須使用轉換叫用的使用者定義型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="7b873-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span>

<span data-ttu-id="7b873-104">下列範例會定義從 `Fahrenheit` 類別轉換成 `Celsius` 類別的運算子。</span><span class="sxs-lookup"><span data-stu-id="7b873-104">The following example defines the operator that converts from a `Fahrenheit` class to a `Celsius` class.</span></span> <span data-ttu-id="7b873-105">該運算子必須在 `Fahrenheit` 類別或 `Celsius` 類別中定義：</span><span class="sxs-lookup"><span data-stu-id="7b873-105">The operator must be defined either inside a `Fahrenheit` class or a `Celsius` class:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="7b873-106">您會透過轉換來叫用已定義的轉換運算子，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7b873-106">You invoke the defined conversion operator with a cast, as the following example shows:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="7b873-107">轉換運算子會將來源類型轉換成目標型別。</span><span class="sxs-lookup"><span data-stu-id="7b873-107">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="7b873-108">來源類型提供轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="7b873-108">The source type provides the conversion operator.</span></span> <span data-ttu-id="7b873-109">不同於隱含轉換，明確轉換運算子必須透過轉換來叫用。</span><span class="sxs-lookup"><span data-stu-id="7b873-109">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="7b873-110">如果轉換作業會造成例外狀況或遺失資訊，您應將其標記為 `explicit`。</span><span class="sxs-lookup"><span data-stu-id="7b873-110">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="7b873-111">如此可避免編譯器以無訊息方式叫用轉換作業，發生難以預料的後果。</span><span class="sxs-lookup"><span data-stu-id="7b873-111">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="7b873-112">省略轉換會導致編譯時期錯誤 CS0266。</span><span class="sxs-lookup"><span data-stu-id="7b873-112">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="7b873-113">如需詳細資訊，請參閱[使用轉換運算子](../../programming-guide/statements-expressions-operators/using-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="7b873-113">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="7b873-114">範例</span><span class="sxs-lookup"><span data-stu-id="7b873-114">Example</span></span>

<span data-ttu-id="7b873-115">下例提供 `Fahrenheit` 和 `Celsius` 類別，它們互相提供明確轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="7b873-115">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="7b873-116">範例</span><span class="sxs-lookup"><span data-stu-id="7b873-116">Example</span></span>

<span data-ttu-id="7b873-117">下例定義 `Digit` 結構，表示單一十進位數字。</span><span class="sxs-lookup"><span data-stu-id="7b873-117">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="7b873-118">已定義將 `byte` 轉換成 `Digit` 的運算子，但是因為並非所有位元組都可轉換成 `Digit`，所以是明確轉換。</span><span class="sxs-lookup"><span data-stu-id="7b873-118">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="7b873-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="7b873-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b873-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b873-120">See also</span></span>

- [<span data-ttu-id="7b873-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7b873-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b873-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7b873-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b873-123">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="7b873-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7b873-124">implicit</span><span class="sxs-lookup"><span data-stu-id="7b873-124">implicit</span></span>](implicit.md)
- [<span data-ttu-id="7b873-125">運算子多載</span><span class="sxs-lookup"><span data-stu-id="7b873-125">Operator overloading</span></span>](../operators/operator-overloading.md)
- [<span data-ttu-id="7b873-126">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="7b873-126">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
- [<span data-ttu-id="7b873-127">C# 中鏈結的使用者定義明確轉換</span><span class="sxs-lookup"><span data-stu-id="7b873-127">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
