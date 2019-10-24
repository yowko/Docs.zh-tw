---
title: char 關鍵字- C#參考
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771793"
---
# <a name="char-c-reference"></a><span data-ttu-id="4b125-102">char （C#參考）</span><span class="sxs-lookup"><span data-stu-id="4b125-102">char (C# reference)</span></span>

<span data-ttu-id="4b125-103">@No__t_0 類型關鍵字是代表 Unicode UTF-16 字元之 .NET <xref:System.Char?displayProperty=nameWithType> 結構類型的別名：</span><span class="sxs-lookup"><span data-stu-id="4b125-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character:</span></span>

|<span data-ttu-id="4b125-104">輸入</span><span class="sxs-lookup"><span data-stu-id="4b125-104">Type</span></span>|<span data-ttu-id="4b125-105">Range</span><span class="sxs-lookup"><span data-stu-id="4b125-105">Range</span></span>|<span data-ttu-id="4b125-106">大小</span><span class="sxs-lookup"><span data-stu-id="4b125-106">Size</span></span>|<span data-ttu-id="4b125-107">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="4b125-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="4b125-108">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="4b125-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="4b125-109">16位</span><span class="sxs-lookup"><span data-stu-id="4b125-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="4b125-110">常值</span><span class="sxs-lookup"><span data-stu-id="4b125-110">Literals</span></span>

<span data-ttu-id="4b125-111">`char` 類型的常數可以撰寫為字元常值、十六進位逸出序列或 Unicode 表示法。</span><span class="sxs-lookup"><span data-stu-id="4b125-111">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="4b125-112">您也可以將整數位符程式碼轉換成對應的 `char` 值。</span><span class="sxs-lookup"><span data-stu-id="4b125-112">You can also cast an integral character code into the corresponding `char` value.</span></span> <span data-ttu-id="4b125-113">在下列範例中，`char` 陣列的四個元素會使用相同的字元 `X` 進行初始化：</span><span class="sxs-lookup"><span data-stu-id="4b125-113">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="4b125-114">轉換</span><span class="sxs-lookup"><span data-stu-id="4b125-114">Conversions</span></span>

<span data-ttu-id="4b125-115">@No__t_0 類型可以隱含地轉換成下列[整數](../builtin-types/integral-numeric-types.md)類資料類型： `ushort`、`int`、`uint`、`long` 和 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="4b125-115">The `char` type is implicitly convertible to the following [integral](../builtin-types/integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="4b125-116">它也可以隱含地轉換成內建的[浮點](../builtin-types/floating-point-numeric-types.md)數數值型別： `float`、`double` 和 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="4b125-116">It's also implicitly convertible to the built-in [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="4b125-117">它可以明確轉換成 `sbyte`、`byte` 和 `short` 整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="4b125-117">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="4b125-118">沒有從其他類型到 `char` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="4b125-118">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="4b125-119">不過，任何[整數](../builtin-types/integral-numeric-types.md)或[浮點數](../builtin-types/floating-point-numeric-types.md)類型都可以明確地轉換成 `char`。</span><span class="sxs-lookup"><span data-stu-id="4b125-119">However, any [integral](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4b125-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4b125-120">C# language specification</span></span>

<span data-ttu-id="4b125-121">如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[整數類資料類型](~/_csharplang/spec/types.md#integral-types)一節。</span><span class="sxs-lookup"><span data-stu-id="4b125-121">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b125-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b125-122">See also</span></span>

- [<span data-ttu-id="4b125-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4b125-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4b125-124">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4b125-124">C# keywords</span></span>](./index.md)
- [<span data-ttu-id="4b125-125">內建型別表</span><span class="sxs-lookup"><span data-stu-id="4b125-125">Built-in types table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="4b125-126">字串</span><span class="sxs-lookup"><span data-stu-id="4b125-126">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
