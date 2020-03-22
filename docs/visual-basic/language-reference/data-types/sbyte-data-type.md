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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400789"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="c0dee-102">SByte 資料類型（可視基本）</span><span class="sxs-lookup"><span data-stu-id="c0dee-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="c0dee-103">保留在 -128 到 127 之間的值範圍的已簽名 8 位（1 位元組）整數。</span><span class="sxs-lookup"><span data-stu-id="c0dee-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0dee-104">備註</span><span class="sxs-lookup"><span data-stu-id="c0dee-104">Remarks</span></span>

<span data-ttu-id="c0dee-105">使用`SByte`資料類型包含不需要 的完整資料寬度`Integer`甚至一半資料寬度的`Short`整數值。</span><span class="sxs-lookup"><span data-stu-id="c0dee-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="c0dee-106">在某些情況下，通用語言運行時可能能夠將`SByte`變數緊密打包在一起並節省記憶體消耗。</span><span class="sxs-lookup"><span data-stu-id="c0dee-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="c0dee-107">`SByte` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="c0dee-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="c0dee-108">文本分配</span><span class="sxs-lookup"><span data-stu-id="c0dee-108">Literal assignments</span></span>

<span data-ttu-id="c0dee-109">您可以通過為其分配十進位文本、`SByte`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="c0dee-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="c0dee-110">在下面的示例中，等於 -102 的整數，表示為十進位、十六進位和二進位文本`SByte`。</span><span class="sxs-lookup"><span data-stu-id="c0dee-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="c0dee-111">此示例要求您使用`/removeintchecks`編譯器開關進行編譯。</span><span class="sxs-lookup"><span data-stu-id="c0dee-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="c0dee-112">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="c0dee-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="c0dee-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="c0dee-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c0dee-114">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="c0dee-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="c0dee-115">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c0dee-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c0dee-116">例如：</span><span class="sxs-lookup"><span data-stu-id="c0dee-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="c0dee-117">如果整數常值超出 `SByte` 的範圍 (亦即，如果小於 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.SByte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0dee-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="c0dee-118">當整數文本沒有尾碼時，將推斷出[整數](integer-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="c0dee-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="c0dee-119">如果整數文本超出`Integer`類型的範圍，則推斷為[Long。](long-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="c0dee-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="c0dee-120">這意味著，在前面的示例中，數位文本`0x9A`和`0b10011010`轉換為 32 位簽名整數，值為 156，超過<xref:System.SByte.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c0dee-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0dee-121">要成功編譯像這樣將非十進位整數分配給 的代碼`SByte`，可以執行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="c0dee-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="c0dee-122">通過編譯`/removeintchecks`編譯器開關禁用整數邊界檢查。</span><span class="sxs-lookup"><span data-stu-id="c0dee-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="c0dee-123">使用[類型字元](../../programming-guide/language-features/data-types/type-characters.md)顯式定義要分配給 的文本`SByte`值。</span><span class="sxs-lookup"><span data-stu-id="c0dee-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="c0dee-124">下面的示例將負文本`Short`值分配給 。 `SByte`</span><span class="sxs-lookup"><span data-stu-id="c0dee-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="c0dee-125">請注意，對於負數，必須設置數位文本的高階字的高階位。</span><span class="sxs-lookup"><span data-stu-id="c0dee-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="c0dee-126">在我們的示例中，這是文本`Short`值的第 15 位。</span><span class="sxs-lookup"><span data-stu-id="c0dee-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="c0dee-127">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="c0dee-127">Programming tips</span></span>

- <span data-ttu-id="c0dee-128">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="c0dee-128">**CLS Compliance.**</span></span> <span data-ttu-id="c0dee-129">資料類型`SByte`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="c0dee-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="c0dee-130">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="c0dee-130">**Widening.**</span></span> <span data-ttu-id="c0dee-131">資料類型`SByte`擴展到`Short`、、、、、、、`Integer``Long``Decimal``Single`和`Double`。</span><span class="sxs-lookup"><span data-stu-id="c0dee-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="c0dee-132">這意味著您可以轉換為`SByte`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0dee-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="c0dee-133">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="c0dee-133">**Type Characters.**</span></span> <span data-ttu-id="c0dee-134">`SByte`沒有常值型別字元或識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="c0dee-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="c0dee-135">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="c0dee-135">**Framework Type.**</span></span> <span data-ttu-id="c0dee-136">在 .NET Framework 中對應的類型為 <xref:System.SByte?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="c0dee-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0dee-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0dee-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="c0dee-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="c0dee-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c0dee-139">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="c0dee-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c0dee-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="c0dee-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="c0dee-141">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="c0dee-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="c0dee-142">整數資料類型</span><span class="sxs-lookup"><span data-stu-id="c0dee-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="c0dee-143">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="c0dee-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="c0dee-144">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="c0dee-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
