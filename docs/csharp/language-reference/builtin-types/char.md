---
title: 字元類型 - C# 引用
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846518"
---
# <a name="char-c-reference"></a><span data-ttu-id="5aeb3-102">字元（C# 參考）</span><span class="sxs-lookup"><span data-stu-id="5aeb3-102">char (C# reference)</span></span>

<span data-ttu-id="5aeb3-103">類型`char`關鍵字是表示 Unicode UTF-16 字元的 .NET<xref:System.Char?displayProperty=nameWithType>結構類型的別名。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="5aeb3-104">類型</span><span class="sxs-lookup"><span data-stu-id="5aeb3-104">Type</span></span>|<span data-ttu-id="5aeb3-105">範圍</span><span class="sxs-lookup"><span data-stu-id="5aeb3-105">Range</span></span>|<span data-ttu-id="5aeb3-106">大小</span><span class="sxs-lookup"><span data-stu-id="5aeb3-106">Size</span></span>|<span data-ttu-id="5aeb3-107">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="5aeb3-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="5aeb3-108">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="5aeb3-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="5aeb3-109">16 位</span><span class="sxs-lookup"><span data-stu-id="5aeb3-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="5aeb3-110">`char`類型的預設值為`\0`，即 U+0000。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="5aeb3-111">[字串](reference-types.md#the-string-type)類型將文本表示為值序列`char`。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="5aeb3-112">常值</span><span class="sxs-lookup"><span data-stu-id="5aeb3-112">Literals</span></span>

<span data-ttu-id="5aeb3-113">可以使用以下條件指定`char`值：</span><span class="sxs-lookup"><span data-stu-id="5aeb3-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="5aeb3-114">字元文本。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-114">a character literal.</span></span>
- <span data-ttu-id="5aeb3-115">Unicode 逸出序列，後面`\u`跟著字元代碼的四符號十六進位表示形式。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="5aeb3-116">十六進位逸出序列，`\x`後跟字元代碼的十六進位表示形式。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="5aeb3-117">如前面的示例所示，您還可以將字元代碼的值轉換為相應的`char`值。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="5aeb3-118">在 Unicode 逸出序列中，必須指定所有四個十六進位數位。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="5aeb3-119">也就是說，`\u006A`是有效的逸出序列，而`\u06A`和`\u6A`無效。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="5aeb3-120">在十六進位逸出序列的情況下，可以省略前置字元為零。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="5aeb3-121">也就是說，`\x006A`和`\x06A``\x6A`逸出序列是有效的，並且對應于同一個字元。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="5aeb3-122">轉換</span><span class="sxs-lookup"><span data-stu-id="5aeb3-122">Conversions</span></span>

<span data-ttu-id="5aeb3-123">類型`char`隱式可轉換為以下[積分](integral-numeric-types.md)`ushort`類型： 、 `int`、 `uint` `long`、`ulong`和 。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="5aeb3-124">它還隱式可轉換為內置[浮點](floating-point-numeric-types.md)數數值型別：`float`和`double`。 `decimal`</span><span class="sxs-lookup"><span data-stu-id="5aeb3-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="5aeb3-125">它顯式可轉換為`sbyte`、`byte`和`short`積分類型。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="5aeb3-126">沒有從其他類型的隱式轉換到類型`char`。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="5aeb3-127">但是，任何[積分](integral-numeric-types.md)或[浮點](floating-point-numeric-types.md)數位類型都顯式轉換為`char`。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5aeb3-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5aeb3-128">C# language specification</span></span>

<span data-ttu-id="5aeb3-129">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的["積分類型"](~/_csharplang/spec/types.md#integral-types)部分。</span><span class="sxs-lookup"><span data-stu-id="5aeb3-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5aeb3-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aeb3-130">See also</span></span>

- [<span data-ttu-id="5aeb3-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5aeb3-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5aeb3-132">實值型別</span><span class="sxs-lookup"><span data-stu-id="5aeb3-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="5aeb3-133">字串</span><span class="sxs-lookup"><span data-stu-id="5aeb3-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
