---
title: char 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605957"
---
# <a name="char-c-reference"></a><span data-ttu-id="c8de0-102">char (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c8de0-102">char (C# Reference)</span></span>

<span data-ttu-id="c8de0-103">`char` 關鍵字是用來宣告 .NET Framework 用來代表 Unicode 字元的 <xref:System.Char?displayProperty=nameWithType> 結構執行個體。</span><span class="sxs-lookup"><span data-stu-id="c8de0-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="c8de0-104">`Char` 物件的值是 16 位元數字 (序數) 值。</span><span class="sxs-lookup"><span data-stu-id="c8de0-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="c8de0-105">Unicode 字元是用來代表世界各地的大部分書寫語言。</span><span class="sxs-lookup"><span data-stu-id="c8de0-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="c8de0-106">類型</span><span class="sxs-lookup"><span data-stu-id="c8de0-106">Type</span></span>|<span data-ttu-id="c8de0-107">Range</span><span class="sxs-lookup"><span data-stu-id="c8de0-107">Range</span></span>|<span data-ttu-id="c8de0-108">大小</span><span class="sxs-lookup"><span data-stu-id="c8de0-108">Size</span></span>|<span data-ttu-id="c8de0-109">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="c8de0-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="c8de0-110">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="c8de0-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="c8de0-111">Unicode 16 位元字元</span><span class="sxs-lookup"><span data-stu-id="c8de0-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="c8de0-112">常值</span><span class="sxs-lookup"><span data-stu-id="c8de0-112">Literals</span></span>

<span data-ttu-id="c8de0-113">`char` 類型的常數可以撰寫為字元常值、十六進位逸出序列或 Unicode 表示法。</span><span class="sxs-lookup"><span data-stu-id="c8de0-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="c8de0-114">您也可以轉型整數字元碼。</span><span class="sxs-lookup"><span data-stu-id="c8de0-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="c8de0-115">在下列範例中，四個 `char` 變數都會初始化成相同的字元 `X`：</span><span class="sxs-lookup"><span data-stu-id="c8de0-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="c8de0-116">轉換</span><span class="sxs-lookup"><span data-stu-id="c8de0-116">Conversions</span></span>

<span data-ttu-id="c8de0-117">`char` 可以隱含轉換為 [ushort](../builtin-types/integral-numeric-types.md)、[int](../builtin-types/integral-numeric-types.md)、[uint](../builtin-types/integral-numeric-types.md)、[double](../builtin-types/floating-point-numeric-types.md) 或 [decimal](../builtin-types/floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c8de0-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="c8de0-118">不過，沒有從其他類型到 `char` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c8de0-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="c8de0-119"><xref:System.Char?displayProperty=nameWithType> 型別提供數種使用 `char` 值的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c8de0-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c8de0-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c8de0-120">C# language specification</span></span>  

<span data-ttu-id="c8de0-121">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。</span><span class="sxs-lookup"><span data-stu-id="c8de0-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="c8de0-122">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="c8de0-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8de0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8de0-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="c8de0-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c8de0-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c8de0-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c8de0-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c8de0-126">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c8de0-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c8de0-127">整數型別</span><span class="sxs-lookup"><span data-stu-id="c8de0-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="c8de0-128">內建型別表</span><span class="sxs-lookup"><span data-stu-id="c8de0-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="c8de0-129">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="c8de0-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="c8de0-130">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="c8de0-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="c8de0-131">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="c8de0-131">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="c8de0-132">字串</span><span class="sxs-lookup"><span data-stu-id="c8de0-132">Strings</span></span>](../../programming-guide/strings/index.md)
