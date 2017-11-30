---
title: "SByte 資料類型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.sbyte
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bcd00665ec5b8651089811a61212bfa302fe95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="2ae81-102">SByte 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ae81-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="2ae81-103">保存帶正負號 8 位元 （1 個位元組） 整數，範圍從-128 到 127。</span><span class="sxs-lookup"><span data-stu-id="2ae81-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ae81-104">備註</span><span class="sxs-lookup"><span data-stu-id="2ae81-104">Remarks</span></span>

<span data-ttu-id="2ae81-105">使用`SByte`資料類型可包含不需要完整的資料寬度的整數值`Integer`或甚至一半的資料寬度的`Short`。</span><span class="sxs-lookup"><span data-stu-id="2ae81-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="2ae81-106">在某些情況下，通用語言執行平台可能可以 pack 您`SByte`緊密，並將記憶體耗用量儲存變數。</span><span class="sxs-lookup"><span data-stu-id="2ae81-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="2ae81-107">`SByte` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="2ae81-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="2ae81-108">常值的指派</span><span class="sxs-lookup"><span data-stu-id="2ae81-108">Literal assignments</span></span>
  
<span data-ttu-id="2ae81-109">您可以宣告和初始化`SByte`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="2ae81-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="2ae81-110">在下列範例中，整數等於-102 以十進位、 十六進位表示，而二進位常值指派給`SByte`值。</span><span class="sxs-lookup"><span data-stu-id="2ae81-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="2ae81-111">這個範例需要您使用編譯`/removeintchecks`編譯器參數。</span><span class="sxs-lookup"><span data-stu-id="2ae81-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="2ae81-112">使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。</span><span class="sxs-lookup"><span data-stu-id="2ae81-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2ae81-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="2ae81-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2ae81-114">從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2ae81-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="2ae81-115">如果整數常值超出 `SByte` 的範圍 (亦即，如果小於 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.SByte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ae81-115">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="2ae81-116">當整數常值有沒有後置詞，[整數](integer-data-type.md)會推斷而來。</span><span class="sxs-lookup"><span data-stu-id="2ae81-116">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="2ae81-117">如果整數常值超出範圍`Integer`型別，[長](long-data-type.md)會推斷而來。</span><span class="sxs-lookup"><span data-stu-id="2ae81-117">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="2ae81-118">這表示，在上一個範例中，數值常值`0x9A`和`0b10011010`會解譯為 32 位元帶正負號的整數值為 156，但這超過<xref:System.SByte.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2ae81-118">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2ae81-119">若要成功編譯程式碼如下指派至非十進位整數`SByte`，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2ae81-119">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="2ae81-120">停用整數範圍檢查，藉由編譯與`/removeintchecks`編譯器參數。</span><span class="sxs-lookup"><span data-stu-id="2ae81-120">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="2ae81-121">使用[類型字元](../../programming-guide\language-features\data-types/type-characters.md)明確地定義您想要指派給常值`SByte`。</span><span class="sxs-lookup"><span data-stu-id="2ae81-121">Use a [type character](../../programming-guide\language-features\data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="2ae81-122">下列範例指定負數的常值`Short`值設定為`SByte`。</span><span class="sxs-lookup"><span data-stu-id="2ae81-122">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="2ae81-123">請注意，負數，高序位位元的數值常值的高序位文字必須設定。</span><span class="sxs-lookup"><span data-stu-id="2ae81-123">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="2ae81-124">在我們的範例，這位元的常值 15`Short`值。</span><span class="sxs-lookup"><span data-stu-id="2ae81-124">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="2ae81-125">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="2ae81-125">Programming tips</span></span>
  
-   <span data-ttu-id="2ae81-126">**Cls 符合性。**</span><span class="sxs-lookup"><span data-stu-id="2ae81-126">**CLS Compliance.**</span></span> <span data-ttu-id="2ae81-127">`SByte`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法使用所使用的元件。</span><span class="sxs-lookup"><span data-stu-id="2ae81-127">The `SByte` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="2ae81-128">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="2ae81-128">**Widening.**</span></span> <span data-ttu-id="2ae81-129">`SByte`資料類型可擴展成`Short`， `Integer`， `Long`， `Decimal`， `Single`，和`Double`。</span><span class="sxs-lookup"><span data-stu-id="2ae81-129">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="2ae81-130">這表示您可以將轉換`SByte`而不會發生這些類型的任何<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ae81-130">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="2ae81-131">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="2ae81-131">**Type Characters.**</span></span> <span data-ttu-id="2ae81-132">`SByte`沒有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="2ae81-132">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="2ae81-133">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="2ae81-133">**Framework Type.**</span></span> <span data-ttu-id="2ae81-134">在 .NET Framework 中對應的類型為 <xref:System.SByte?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="2ae81-134">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2ae81-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ae81-135">See also</span></span>

 <xref:System.SByte?displayProperty=nameWithType>  
 [<span data-ttu-id="2ae81-136">資料類型</span><span class="sxs-lookup"><span data-stu-id="2ae81-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="2ae81-137">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="2ae81-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2ae81-138">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="2ae81-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="2ae81-139">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="2ae81-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="2ae81-140">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="2ae81-140">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="2ae81-141">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="2ae81-141">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="2ae81-142">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="2ae81-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
