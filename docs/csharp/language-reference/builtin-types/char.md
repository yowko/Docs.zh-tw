---
title: 字元類型 - C# 引用
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 8727e47e13082e8550fb174c92139dfd5c17ec36
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134332"
---
# <a name="char-c-reference"></a><span data-ttu-id="0875d-102">字元（C# 參考）</span><span class="sxs-lookup"><span data-stu-id="0875d-102">char (C# reference)</span></span>

<span data-ttu-id="0875d-103">類型`char`關鍵字是表示 Unicode UTF-16 字元的 .NET<xref:System.Char?displayProperty=nameWithType>結構類型的別名。</span><span class="sxs-lookup"><span data-stu-id="0875d-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="0875d-104">類型</span><span class="sxs-lookup"><span data-stu-id="0875d-104">Type</span></span>|<span data-ttu-id="0875d-105">範圍</span><span class="sxs-lookup"><span data-stu-id="0875d-105">Range</span></span>|<span data-ttu-id="0875d-106">大小</span><span class="sxs-lookup"><span data-stu-id="0875d-106">Size</span></span>|<span data-ttu-id="0875d-107">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="0875d-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="0875d-108">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="0875d-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="0875d-109">16 位</span><span class="sxs-lookup"><span data-stu-id="0875d-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="0875d-110">`char`類型的預設值為`\0`，即 U+0000。</span><span class="sxs-lookup"><span data-stu-id="0875d-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="0875d-111">[字串](reference-types.md#the-string-type)類型將文本表示為值序列`char`。</span><span class="sxs-lookup"><span data-stu-id="0875d-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="0875d-112">常值</span><span class="sxs-lookup"><span data-stu-id="0875d-112">Literals</span></span>

<span data-ttu-id="0875d-113">可以使用以下條件指定`char`值：</span><span class="sxs-lookup"><span data-stu-id="0875d-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="0875d-114">字元文本。</span><span class="sxs-lookup"><span data-stu-id="0875d-114">a character literal.</span></span>
- <span data-ttu-id="0875d-115">Unicode 逸出序列，後面`\u`跟著字元代碼的四符號十六進位表示形式。</span><span class="sxs-lookup"><span data-stu-id="0875d-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="0875d-116">十六進位逸出序列，`\x`後跟字元代碼的十六進位表示形式。</span><span class="sxs-lookup"><span data-stu-id="0875d-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="0875d-117">如前面的示例所示，您還可以將字元代碼的值轉換為相應的`char`值。</span><span class="sxs-lookup"><span data-stu-id="0875d-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="0875d-118">在 Unicode 逸出序列中，必須指定所有四個十六進位數位。</span><span class="sxs-lookup"><span data-stu-id="0875d-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="0875d-119">也就是說，`\u006A`是有效的逸出序列，而`\u06A`和`\u6A`無效。</span><span class="sxs-lookup"><span data-stu-id="0875d-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="0875d-120">在十六進位逸出序列的情況下，可以省略前置字元為零。</span><span class="sxs-lookup"><span data-stu-id="0875d-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="0875d-121">也就是說，`\x006A`和`\x06A``\x6A`逸出序列是有效的，並且對應于同一個字元。</span><span class="sxs-lookup"><span data-stu-id="0875d-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="0875d-122">轉換</span><span class="sxs-lookup"><span data-stu-id="0875d-122">Conversions</span></span>

<span data-ttu-id="0875d-123">類型`char`隱式可轉換為以下[積分](integral-numeric-types.md)`ushort`類型： 、 `int`、 `uint` `long`、`ulong`和 。</span><span class="sxs-lookup"><span data-stu-id="0875d-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="0875d-124">它還隱式可轉換為內置[浮點](floating-point-numeric-types.md)數數值型別：`float`和`double`。 `decimal`</span><span class="sxs-lookup"><span data-stu-id="0875d-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="0875d-125">它顯式可轉換為`sbyte`、`byte`和`short`積分類型。</span><span class="sxs-lookup"><span data-stu-id="0875d-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="0875d-126">沒有從其他類型的隱式轉換到類型`char`。</span><span class="sxs-lookup"><span data-stu-id="0875d-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="0875d-127">但是，任何[積分](integral-numeric-types.md)或[浮點](floating-point-numeric-types.md)數位類型都顯式轉換為`char`。</span><span class="sxs-lookup"><span data-stu-id="0875d-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0875d-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0875d-128">C# language specification</span></span>

<span data-ttu-id="0875d-129">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的["積分類型"](~/_csharplang/spec/types.md#integral-types)部分。</span><span class="sxs-lookup"><span data-stu-id="0875d-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0875d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0875d-130">See also</span></span>

- [<span data-ttu-id="0875d-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0875d-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0875d-132">實值型別</span><span class="sxs-lookup"><span data-stu-id="0875d-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="0875d-133">字串</span><span class="sxs-lookup"><span data-stu-id="0875d-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="0875d-134">在 .NET 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="0875d-134">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
