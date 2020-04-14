---
title: Decimal 資料類型
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243319"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="3f68a-102">Decimal 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f68a-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="3f68a-103">保存帶正負號的 128 位元 (16 位元組) 值，代表可變倍率 10 倍的 96 位元 (12 位元組) 整數。</span><span class="sxs-lookup"><span data-stu-id="3f68a-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="3f68a-104">縮放因數指定小數點右側的數字數;範圍從 0 到 28。</span><span class="sxs-lookup"><span data-stu-id="3f68a-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="3f68a-105">其刻度為 0(無小數位數),最大可能值為 +/-79,228,162,514,264,337,593,543,950,335 (+/-7.922816251423355353535535553355+28)。</span><span class="sxs-lookup"><span data-stu-id="3f68a-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="3f68a-106">對於 28 位小數,最大值為 +//922816251426433759355439555555555555303335,最小非零值為 +//000000000000000000000000001(+//-1E-28)。</span><span class="sxs-lookup"><span data-stu-id="3f68a-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="3f68a-107">備註</span><span class="sxs-lookup"><span data-stu-id="3f68a-107">Remarks</span></span>

<span data-ttu-id="3f68a-108">數據類型`Decimal`為數位提供最多數量的重要數位。</span><span class="sxs-lookup"><span data-stu-id="3f68a-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="3f68a-109">它最多支援 29 位有效數位,可以表示大於 7.9228 x 10^28 的值。</span><span class="sxs-lookup"><span data-stu-id="3f68a-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="3f68a-110">它特別適用於需要大量數位但不能容忍捨入錯誤的計算(如財務)。</span><span class="sxs-lookup"><span data-stu-id="3f68a-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="3f68a-111">`Decimal` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="3f68a-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="3f68a-112">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="3f68a-112">Programming Tips</span></span>

- <span data-ttu-id="3f68a-113">**精度。**</span><span class="sxs-lookup"><span data-stu-id="3f68a-113">**Precision.**</span></span> <span data-ttu-id="3f68a-114">`Decimal`不是浮點數據類型。</span><span class="sxs-lookup"><span data-stu-id="3f68a-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="3f68a-115">結構`Decimal`包含二進位整數值,以及符號位和整數縮放因數,指定值的哪一部分是十進位數。</span><span class="sxs-lookup"><span data-stu-id="3f68a-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="3f68a-116">因此,與浮`Decimal`點類型`Single``Double`(和 ) 相比,數位在記憶體中的表示法更精確。</span><span class="sxs-lookup"><span data-stu-id="3f68a-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="3f68a-117">**效能。**</span><span class="sxs-lookup"><span data-stu-id="3f68a-117">**Performance.**</span></span> <span data-ttu-id="3f68a-118">數據類型`Decimal`是所有數值類型中最慢的。</span><span class="sxs-lookup"><span data-stu-id="3f68a-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="3f68a-119">在選擇數據類型之前,應權衡精度與性能的重要性。</span><span class="sxs-lookup"><span data-stu-id="3f68a-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="3f68a-120">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="3f68a-120">**Widening.**</span></span> <span data-ttu-id="3f68a-121">資料型`Decimal`態延伸`Single`到`Double`或 。</span><span class="sxs-lookup"><span data-stu-id="3f68a-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="3f68a-122">這意味著您可以轉換為`Decimal`其中任<xref:System.OverflowException?displayProperty=nameWithType>一類型,而不會遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f68a-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="3f68a-123">**尾隨零。**</span><span class="sxs-lookup"><span data-stu-id="3f68a-123">**Trailing Zeros.**</span></span> <span data-ttu-id="3f68a-124">視覺基礎不會在`Decimal`文本中存儲尾隨零。</span><span class="sxs-lookup"><span data-stu-id="3f68a-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="3f68a-125">但是,`Decimal`變數保留在計算中獲取的任何尾隨零。</span><span class="sxs-lookup"><span data-stu-id="3f68a-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="3f68a-126">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="3f68a-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="3f68a-127">上`MsgBox`例中的輸出如下:</span><span class="sxs-lookup"><span data-stu-id="3f68a-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="3f68a-128">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="3f68a-128">**Type Characters.**</span></span> <span data-ttu-id="3f68a-129">將常值類型字元 `D` 附加到常值，會強制其成為 `Decimal` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="3f68a-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="3f68a-130">將識別項類型字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="3f68a-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="3f68a-131">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="3f68a-131">**Framework Type.**</span></span> <span data-ttu-id="3f68a-132">在 .NET Framework 中對應的類型為 <xref:System.Decimal?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="3f68a-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="3f68a-133">範圍</span><span class="sxs-lookup"><span data-stu-id="3f68a-133">Range</span></span>

 <span data-ttu-id="3f68a-134">您可能需要使用`D`類型字元將大值分配給`Decimal`變數或常量。</span><span class="sxs-lookup"><span data-stu-id="3f68a-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="3f68a-135">此要求是因為編譯器將文本解釋為`Long`除非文本類型字元遵循文本,如下例所示。</span><span class="sxs-lookup"><span data-stu-id="3f68a-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="3f68a-136">的聲明`bigDec1`不會生成溢出,因為分配給它的值`Long`在</span><span class="sxs-lookup"><span data-stu-id="3f68a-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="3f68a-137">可以將`Long`該值分配`Decimal`給 變數。</span><span class="sxs-lookup"><span data-stu-id="3f68a-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="3f68a-138">的聲明`bigDec2`生成溢出錯誤,因為分配給它的值`Long`對於 來說太大。</span><span class="sxs-lookup"><span data-stu-id="3f68a-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="3f68a-139">由於數位文字不能首先解釋為`Long`, 無法將其`Decimal`分配給 變數。</span><span class="sxs-lookup"><span data-stu-id="3f68a-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="3f68a-140">對於`bigDec3`,文本類型字`D`元 通過強制編譯器將文本`Decimal`解釋為 而不是解說,從而解決`Long`了問題。</span><span class="sxs-lookup"><span data-stu-id="3f68a-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f68a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f68a-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3f68a-142">資料類型</span><span class="sxs-lookup"><span data-stu-id="3f68a-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="3f68a-143">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="3f68a-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="3f68a-144">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="3f68a-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="3f68a-145">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="3f68a-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="3f68a-146">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="3f68a-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="3f68a-147">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="3f68a-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
