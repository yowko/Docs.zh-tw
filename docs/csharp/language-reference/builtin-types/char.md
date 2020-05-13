---
title: 'char 類型-c # 參考'
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: f771626e9777deab30e798559d847615d6124e6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205784"
---
# <a name="char-c-reference"></a><span data-ttu-id="97935-102">char （c # 參考）</span><span class="sxs-lookup"><span data-stu-id="97935-102">char (C# reference)</span></span>

<span data-ttu-id="97935-103">`char`Type 關鍵字是 <xref:System.Char?displayProperty=nameWithType> 代表 Unicode utf-16 字元之 .net 結構類型的別名。</span><span class="sxs-lookup"><span data-stu-id="97935-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="97935-104">類型</span><span class="sxs-lookup"><span data-stu-id="97935-104">Type</span></span>|<span data-ttu-id="97935-105">範圍</span><span class="sxs-lookup"><span data-stu-id="97935-105">Range</span></span>|<span data-ttu-id="97935-106">大小</span><span class="sxs-lookup"><span data-stu-id="97935-106">Size</span></span>|<span data-ttu-id="97935-107">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="97935-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="97935-108">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="97935-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="97935-109">16位</span><span class="sxs-lookup"><span data-stu-id="97935-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="97935-110">類型的預設值 `char` 是 `\0` ，也就是 U + 0000。</span><span class="sxs-lookup"><span data-stu-id="97935-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="97935-111">`char`型別支援[比較](../operators/comparison-operators.md)、[相等](../operators/equality-operators.md)、[遞增](../operators/arithmetic-operators.md#increment-operator-)和[遞減](../operators/arithmetic-operators.md#decrement-operator---)運算子。</span><span class="sxs-lookup"><span data-stu-id="97935-111">The `char` type supports [comparison](../operators/comparison-operators.md), [equality](../operators/equality-operators.md), [increment](../operators/arithmetic-operators.md#increment-operator-), and [decrement](../operators/arithmetic-operators.md#decrement-operator---) operators.</span></span> <span data-ttu-id="97935-112">此外，對於 `char` 運算元，[算術](../operators/arithmetic-operators.md)和[位邏輯](../operators/bitwise-and-shift-operators.md)運算子會對對應的字元碼執行運算，並產生類型的結果 `int` 。</span><span class="sxs-lookup"><span data-stu-id="97935-112">Moreover, for `char` operands, [arithmetic](../operators/arithmetic-operators.md) and [bitwise logical](../operators/bitwise-and-shift-operators.md) operators perform an operation on the corresponding character codes and produce the result of the `int` type.</span></span>

<span data-ttu-id="97935-113">[字串](reference-types.md#the-string-type)類型以一系列的值表示文字 `char` 。</span><span class="sxs-lookup"><span data-stu-id="97935-113">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="97935-114">常值</span><span class="sxs-lookup"><span data-stu-id="97935-114">Literals</span></span>

<span data-ttu-id="97935-115">您可以使用來指定 `char` 值：</span><span class="sxs-lookup"><span data-stu-id="97935-115">You can specify a `char` value with:</span></span>

- <span data-ttu-id="97935-116">字元常值。</span><span class="sxs-lookup"><span data-stu-id="97935-116">a character literal.</span></span>
- <span data-ttu-id="97935-117">Unicode 逸出序列， `\u` 後面接著字元碼的四符號十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="97935-117">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="97935-118">十六進位的逸出序列， `\x` 後面接著字元碼的十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="97935-118">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="97935-119">如上述範例所示，您也可以將字元碼的值轉換成對應的 `char` 值。</span><span class="sxs-lookup"><span data-stu-id="97935-119">As the preceding example shows, you can also cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="97935-120">在 Unicode 逸出序列的情況下，您必須指定全部四個十六進位數位。</span><span class="sxs-lookup"><span data-stu-id="97935-120">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="97935-121">也就是說， `\u006A` 是有效的逸出序列，而 `\u06A` 和則無效 `\u6A` 。</span><span class="sxs-lookup"><span data-stu-id="97935-121">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="97935-122">在十六進位 escape 序列的情況下，您可以省略前置的零。</span><span class="sxs-lookup"><span data-stu-id="97935-122">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="97935-123">也就是說，、和 `\x006A` `\x06A` `\x6A` escape 序列都是有效的，而且會對應至相同的字元。</span><span class="sxs-lookup"><span data-stu-id="97935-123">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="97935-124">轉換</span><span class="sxs-lookup"><span data-stu-id="97935-124">Conversions</span></span>

<span data-ttu-id="97935-125">`char`類型可以隱含地轉換成下列[整數](integral-numeric-types.md)類資料類型： `ushort` 、 `int` 、 `uint` 、 `long` 和 `ulong` 。</span><span class="sxs-lookup"><span data-stu-id="97935-125">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="97935-126">它也可以隱含地轉換成內建的[浮點](floating-point-numeric-types.md)數數值型別： `float` 、 `double` 和 `decimal` 。</span><span class="sxs-lookup"><span data-stu-id="97935-126">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="97935-127">它可以明確轉換成 `sbyte` 、 `byte` 和 `short` 整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="97935-127">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="97935-128">沒有從其他類型到類型的隱含轉換 `char` 。</span><span class="sxs-lookup"><span data-stu-id="97935-128">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="97935-129">不過，任何[整數](integral-numeric-types.md)或[浮點數](floating-point-numeric-types.md)型別都可以明確地轉換成 `char` 。</span><span class="sxs-lookup"><span data-stu-id="97935-129">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="97935-130">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="97935-130">C# language specification</span></span>

<span data-ttu-id="97935-131">如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[整數類資料類型](~/_csharplang/spec/types.md#integral-types)一節。</span><span class="sxs-lookup"><span data-stu-id="97935-131">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97935-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="97935-132">See also</span></span>

- [<span data-ttu-id="97935-133">C# 參考</span><span class="sxs-lookup"><span data-stu-id="97935-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="97935-134">值類型</span><span class="sxs-lookup"><span data-stu-id="97935-134">Value types</span></span>](value-types.md)
- [<span data-ttu-id="97935-135">字串</span><span class="sxs-lookup"><span data-stu-id="97935-135">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="97935-136">.NET 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="97935-136">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
