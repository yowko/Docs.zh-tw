---
title: explicit 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 66d271fdac0bad356ee0bafc1732e2f410854da1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027937"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="10647-102">explicit (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="10647-102">explicit (C# Reference)</span></span>

<span data-ttu-id="10647-103">`explicit` 關鍵字會宣告必須使用轉換叫用的使用者定義型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="10647-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="10647-104">例如，此運算子會將稱為華氏的類別轉換成稱為攝氏的類別︰</span><span class="sxs-lookup"><span data-stu-id="10647-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="10647-105">此轉換運算子可以這樣叫用︰</span><span class="sxs-lookup"><span data-stu-id="10647-105">This conversion operator can be invoked like this:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="10647-106">轉換運算子會將來源類型轉換成目標型別。</span><span class="sxs-lookup"><span data-stu-id="10647-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="10647-107">來源類型提供轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="10647-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="10647-108">不同於隱含轉換，明確轉換運算子必須透過轉換來叫用。</span><span class="sxs-lookup"><span data-stu-id="10647-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="10647-109">如果轉換作業會造成例外狀況或遺失資訊，您應將其標記為 `explicit`。</span><span class="sxs-lookup"><span data-stu-id="10647-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="10647-110">如此可避免編譯器以無訊息方式叫用轉換作業，發生難以預料的後果。</span><span class="sxs-lookup"><span data-stu-id="10647-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="10647-111">省略轉換會導致編譯時期錯誤 CS0266。</span><span class="sxs-lookup"><span data-stu-id="10647-111">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="10647-112">如需詳細資訊，請參閱[使用轉換運算子](../../programming-guide/statements-expressions-operators/using-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="10647-112">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="10647-113">範例</span><span class="sxs-lookup"><span data-stu-id="10647-113">Example</span></span>

<span data-ttu-id="10647-114">下例提供 `Fahrenheit` 和 `Celsius` 類別，它們互相提供明確轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="10647-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="10647-115">範例</span><span class="sxs-lookup"><span data-stu-id="10647-115">Example</span></span>

<span data-ttu-id="10647-116">下例定義 `Digit` 結構，表示單一十進位數字。</span><span class="sxs-lookup"><span data-stu-id="10647-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="10647-117">已定義將 `byte` 轉換成 `Digit` 的運算子，但是因為並非所有位元組都可轉換成 `Digit`，所以是明確轉換。</span><span class="sxs-lookup"><span data-stu-id="10647-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="10647-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="10647-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10647-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10647-119">See also</span></span>

[<span data-ttu-id="10647-120">C# 參考</span><span class="sxs-lookup"><span data-stu-id="10647-120">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="10647-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="10647-121">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="10647-122">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="10647-122">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="10647-123">implicit</span><span class="sxs-lookup"><span data-stu-id="10647-123">implicit</span></span>](implicit.md)  
[<span data-ttu-id="10647-124">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="10647-124">operator (C# Reference)</span></span>](operator.md)  
[<span data-ttu-id="10647-125">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="10647-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
[<span data-ttu-id="10647-126">C# 中鏈結的使用者定義明確轉換</span><span class="sxs-lookup"><span data-stu-id="10647-126">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  