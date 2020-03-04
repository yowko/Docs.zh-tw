---
title: char 類型- C#參考
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a5aca12e4037d517c3bcfb403c990605a052d48f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239842"
---
# <a name="char-c-reference"></a><span data-ttu-id="00779-102">char （C#參考）</span><span class="sxs-lookup"><span data-stu-id="00779-102">char (C# reference)</span></span>

<span data-ttu-id="00779-103">`char` 類型關鍵字是代表 Unicode UTF-16 字元之 .NET <xref:System.Char?displayProperty=nameWithType> 結構類型的別名。</span><span class="sxs-lookup"><span data-stu-id="00779-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="00779-104">類型</span><span class="sxs-lookup"><span data-stu-id="00779-104">Type</span></span>|<span data-ttu-id="00779-105">範圍</span><span class="sxs-lookup"><span data-stu-id="00779-105">Range</span></span>|<span data-ttu-id="00779-106">大小</span><span class="sxs-lookup"><span data-stu-id="00779-106">Size</span></span>|<span data-ttu-id="00779-107">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="00779-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="00779-108">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="00779-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="00779-109">16位</span><span class="sxs-lookup"><span data-stu-id="00779-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="00779-110">`char` 類型的預設值為 `\0`，也就是 U + 0000。</span><span class="sxs-lookup"><span data-stu-id="00779-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="00779-111">[字串](reference-types.md#the-string-type)類型以 `char` 值序列的形式來表示文字。</span><span class="sxs-lookup"><span data-stu-id="00779-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="00779-112">常值</span><span class="sxs-lookup"><span data-stu-id="00779-112">Literals</span></span>

<span data-ttu-id="00779-113">您可以使用指定 `char` 值：</span><span class="sxs-lookup"><span data-stu-id="00779-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="00779-114">字元常值。</span><span class="sxs-lookup"><span data-stu-id="00779-114">a character literal.</span></span>
- <span data-ttu-id="00779-115">Unicode 逸出序列，`\u` 後面接著字元碼的四符號十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="00779-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="00779-116">十六進位的逸出序列，`\x` 後面接著字元碼的十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="00779-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/snippets/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="00779-117">如上述範例所示，您也可以將字元碼的值轉換成對應的 `char` 值。</span><span class="sxs-lookup"><span data-stu-id="00779-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="00779-118">在 Unicode 逸出序列的情況下，您必須指定全部四個十六進位數位。</span><span class="sxs-lookup"><span data-stu-id="00779-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="00779-119">也就是說，`\u006A` 是有效的逸出序列，而 `\u06A` 和 `\u6A` 則無效。</span><span class="sxs-lookup"><span data-stu-id="00779-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="00779-120">在十六進位 escape 序列的情況下，您可以省略前置的零。</span><span class="sxs-lookup"><span data-stu-id="00779-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="00779-121">也就是說，`\x006A`、`\x06A`和 `\x6A` 的逸出序列都是有效的，而且會對應至相同的字元。</span><span class="sxs-lookup"><span data-stu-id="00779-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="00779-122">轉換</span><span class="sxs-lookup"><span data-stu-id="00779-122">Conversions</span></span>

<span data-ttu-id="00779-123">`char` 類型可以隱含地轉換成下列[整數](integral-numeric-types.md)類資料類型： `ushort`、`int`、`uint`、`long`和 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="00779-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="00779-124">它也可以隱含地轉換成內建的[浮點](floating-point-numeric-types.md)數數值型別： `float`、`double`和 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="00779-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="00779-125">它可以明確轉換成 `sbyte`、`byte`和 `short` 整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="00779-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="00779-126">沒有從其他類型到 `char` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="00779-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="00779-127">不過，任何[整數](integral-numeric-types.md)或[浮點數](floating-point-numeric-types.md)類型都可以明確地轉換成 `char`。</span><span class="sxs-lookup"><span data-stu-id="00779-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="00779-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="00779-128">C# language specification</span></span>

<span data-ttu-id="00779-129">如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[整數類資料類型](~/_csharplang/spec/types.md#integral-types)一節。</span><span class="sxs-lookup"><span data-stu-id="00779-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00779-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00779-130">See also</span></span>

- [<span data-ttu-id="00779-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="00779-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="00779-132">值類型</span><span class="sxs-lookup"><span data-stu-id="00779-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="00779-133">字串</span><span class="sxs-lookup"><span data-stu-id="00779-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
