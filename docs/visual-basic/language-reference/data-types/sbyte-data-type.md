---
title: SByte 資料類型
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415566"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="4d407-102">SByte 資料類型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4d407-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="4d407-103">保存帶正負號的8位（1個位元組）整數，其範圍介於-128 到127之間。</span><span class="sxs-lookup"><span data-stu-id="4d407-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d407-104">備註</span><span class="sxs-lookup"><span data-stu-id="4d407-104">Remarks</span></span>

<span data-ttu-id="4d407-105">使用 `SByte` 資料類型來包含不需要完整資料寬度 `Integer` 或甚至是一半資料寬度的整數值 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="4d407-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="4d407-106">在某些情況下，通用語言執行時間可能可以將您的 `SByte` 變數緊密地封裝在一起，並節省記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="4d407-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="4d407-107">`SByte` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="4d407-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="4d407-108">常值指派</span><span class="sxs-lookup"><span data-stu-id="4d407-108">Literal assignments</span></span>

<span data-ttu-id="4d407-109">您可以藉 `SByte` 由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="4d407-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="4d407-110">在下列範例中，以十進位、十六進位和二進位常值表示的整數等於-102，會指派給 `SByte` 值。</span><span class="sxs-lookup"><span data-stu-id="4d407-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="4d407-111">這個範例需要您使用編譯器參數編譯 `/removeintchecks` 。</span><span class="sxs-lookup"><span data-stu-id="4d407-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="4d407-112">您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或表示 `&B` 二進位常值，以及前置詞 `&o` 或 `&O` 來表示八進位常值。</span><span class="sxs-lookup"><span data-stu-id="4d407-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4d407-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="4d407-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4d407-114">從 Visual Basic 2017 開始，您也可以使用底線字元 `_` 做為數位分隔符號來增強可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4d407-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="4d407-115">從 Visual Basic 15.5 開始，您也可以使用底線字元（ `_` ）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="4d407-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4d407-116">例如：</span><span class="sxs-lookup"><span data-stu-id="4d407-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4d407-117">如果整數常值超出 `SByte` 的範圍 (亦即，如果小於 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.SByte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d407-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="4d407-118">當整數常值沒有後置詞時，就會推斷[整數](integer-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="4d407-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="4d407-119">如果整數常值超出類型的範圍，則 `Integer` 會推斷出[Long](long-data-type.md) 。</span><span class="sxs-lookup"><span data-stu-id="4d407-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="4d407-120">這表示在先前的範例中，數值常 `0x9A` `0b10011010` 值和會被視為32位帶正負號的整數，其值為156，這會超過 <xref:System.SByte.MaxValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4d407-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4d407-121">若要成功編譯這類程式碼，將非十進位整數指派給 `SByte` ，您可以執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="4d407-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="4d407-122">使用編譯器參數編譯來停用整數界限檢查 `/removeintchecks` 。</span><span class="sxs-lookup"><span data-stu-id="4d407-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="4d407-123">使用[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來明確定義您想要指派給的常值 `SByte` 。</span><span class="sxs-lookup"><span data-stu-id="4d407-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="4d407-124">下列範例會將負常 `Short` 值指派給 `SByte` 。</span><span class="sxs-lookup"><span data-stu-id="4d407-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="4d407-125">請注意，若為負數，必須設定數值常值之高序位單字的高序位位。</span><span class="sxs-lookup"><span data-stu-id="4d407-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="4d407-126">在我們的範例中，這是常值的 bit 15 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="4d407-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="4d407-127">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="4d407-127">Programming tips</span></span>

- <span data-ttu-id="4d407-128">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="4d407-128">**CLS Compliance.**</span></span> <span data-ttu-id="4d407-129">`SByte`資料類型不是[Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) （CLS）的一部分，因此符合 cls 標準的程式碼無法使用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="4d407-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="4d407-130">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="4d407-130">**Widening.**</span></span> <span data-ttu-id="4d407-131">`SByte`資料類型會擴大為 `Short` 、 `Integer` 、 `Long` 、 `Decimal` 、 `Single` 和 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="4d407-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="4d407-132">這表示您可以轉換 `SByte` 成這些類型的任何一種，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d407-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="4d407-133">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="4d407-133">**Type Characters.**</span></span> <span data-ttu-id="4d407-134">`SByte`沒有常數值型別字元或識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="4d407-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="4d407-135">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="4d407-135">**Framework Type.**</span></span> <span data-ttu-id="4d407-136">在 .NET Framework 中對應的類型為 <xref:System.SByte?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="4d407-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d407-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d407-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="4d407-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="4d407-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="4d407-139">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="4d407-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="4d407-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="4d407-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="4d407-141">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="4d407-141">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="4d407-142">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="4d407-142">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="4d407-143">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="4d407-143">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="4d407-144">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="4d407-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
