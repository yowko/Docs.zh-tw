---
title: SByte 資料類型 (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ab72b2ac2678640697e3cfab426e5a7d6d889a
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257392"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="26e7b-102">SByte 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26e7b-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="26e7b-103">保存帶正負號 8 位元 （1 個位元組） 整數，範圍介於-128 到 127。</span><span class="sxs-lookup"><span data-stu-id="26e7b-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26e7b-104">備註</span><span class="sxs-lookup"><span data-stu-id="26e7b-104">Remarks</span></span>

<span data-ttu-id="26e7b-105">使用`SByte`包含不需要完整的資料寬度的整數值的資料型別`Integer`或甚至是一半的資料寬度`Short`。</span><span class="sxs-lookup"><span data-stu-id="26e7b-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="26e7b-106">在某些情況下，common language runtime 可以封裝程式`SByte`緊密合作，並將記憶體耗用量儲存的變數。</span><span class="sxs-lookup"><span data-stu-id="26e7b-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="26e7b-107">`SByte` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="26e7b-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="26e7b-108">常值的指派</span><span class="sxs-lookup"><span data-stu-id="26e7b-108">Literal assignments</span></span>
  
<span data-ttu-id="26e7b-109">您可以宣告並初始化`SByte`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="26e7b-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="26e7b-110">在下列範例中，以十進位、 十六進位表示的-102 和二進位常值指派給`SByte`值。</span><span class="sxs-lookup"><span data-stu-id="26e7b-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="26e7b-111">這個範例需要您使用編譯`/removeintchecks`編譯器參數。</span><span class="sxs-lookup"><span data-stu-id="26e7b-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="26e7b-112">使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。</span><span class="sxs-lookup"><span data-stu-id="26e7b-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="26e7b-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="26e7b-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="26e7b-114">從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="26e7b-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="26e7b-115">從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。</span><span class="sxs-lookup"><span data-stu-id="26e7b-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="26e7b-116">例如: </span><span class="sxs-lookup"><span data-stu-id="26e7b-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="26e7b-117">如果整數常值超出 `SByte` 的範圍 (亦即，如果小於 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.SByte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="26e7b-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="26e7b-118">當整數常值沒有後置詞時，[整數](integer-data-type.md)推斷而來。</span><span class="sxs-lookup"><span data-stu-id="26e7b-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="26e7b-119">如果整數常值超出範圍`Integer`型別[長](long-data-type.md)推斷而來。</span><span class="sxs-lookup"><span data-stu-id="26e7b-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="26e7b-120">這表示，在上一個範例中，將數值常值`0x9A`並`0b10011010`會解譯為 32 位元帶正負號整數值 156，而超過<xref:System.SByte.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="26e7b-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26e7b-121">若要成功編譯會將指派從非十進位整數到如下的程式碼`SByte`，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="26e7b-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="26e7b-122">停用整數範圍檢查，藉由使用編譯`/removeintchecks`編譯器參數。</span><span class="sxs-lookup"><span data-stu-id="26e7b-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="26e7b-123">使用[型別字元](../../programming-guide\language-features\data-types/type-characters.md)明確地定義您想要指派給常值`SByte`。</span><span class="sxs-lookup"><span data-stu-id="26e7b-123">Use a [type character](../../programming-guide\language-features\data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="26e7b-124">下列範例會指派為負的常值`Short`值`SByte`。</span><span class="sxs-lookup"><span data-stu-id="26e7b-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="26e7b-125">請注意，對於負數的數字，高序位位元的數值常值的高序位文字必須設定。</span><span class="sxs-lookup"><span data-stu-id="26e7b-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="26e7b-126">在我們的範例中，這位元的常值 15`Short`值。</span><span class="sxs-lookup"><span data-stu-id="26e7b-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="26e7b-127">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="26e7b-127">Programming tips</span></span>
  
-   <span data-ttu-id="26e7b-128">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="26e7b-128">**CLS Compliance.**</span></span> <span data-ttu-id="26e7b-129">`SByte`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法取用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="26e7b-129">The `SByte` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="26e7b-130">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="26e7b-130">**Widening.**</span></span> <span data-ttu-id="26e7b-131">`SByte`資料類型可擴展為`Short`， `Integer`， `Long`， `Decimal`， `Single`，和`Double`。</span><span class="sxs-lookup"><span data-stu-id="26e7b-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="26e7b-132">這表示您可以將轉換`SByte`任何一種類型，而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="26e7b-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="26e7b-133">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="26e7b-133">**Type Characters.**</span></span> <span data-ttu-id="26e7b-134">`SByte` 沒有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="26e7b-134">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="26e7b-135">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="26e7b-135">**Framework Type.**</span></span> <span data-ttu-id="26e7b-136">在 .NET Framework 中對應的類型為 <xref:System.SByte?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="26e7b-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="26e7b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26e7b-137">See also</span></span>

 <xref:System.SByte?displayProperty=nameWithType>  
 [<span data-ttu-id="26e7b-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="26e7b-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="26e7b-139">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="26e7b-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="26e7b-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="26e7b-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="26e7b-141">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="26e7b-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="26e7b-142">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="26e7b-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="26e7b-143">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="26e7b-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="26e7b-144">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="26e7b-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
