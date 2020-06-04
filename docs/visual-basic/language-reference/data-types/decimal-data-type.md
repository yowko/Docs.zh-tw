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
ms.openlocfilehash: 690c8061b6df1115aa24668520170b44edfa8287
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415643"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="af075-102">Decimal 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af075-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="af075-103">保存帶正負號的 128 位元 (16 位元組) 值，代表可變倍率 10 倍的 96 位元 (12 位元組) 整數。</span><span class="sxs-lookup"><span data-stu-id="af075-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="af075-104">縮放比例會指定小數點右邊的位數;其範圍從0到28。</span><span class="sxs-lookup"><span data-stu-id="af075-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="af075-105">若小數位數為0（不含小數點），則最大的可能值為 +/-79228162514264337593543950335 （+/-7.9228162514264337593543950335E + 28）。</span><span class="sxs-lookup"><span data-stu-id="af075-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="af075-106">若有28位小數位數，最大值為 +/-7.9228162514264337593543950335，而最小非零值為 +/-0.0000000000000000000000000001 （+/-1E-28）。</span><span class="sxs-lookup"><span data-stu-id="af075-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="af075-107">備註</span><span class="sxs-lookup"><span data-stu-id="af075-107">Remarks</span></span>

<span data-ttu-id="af075-108">`Decimal`資料類型會提供數位的最大有效位數。</span><span class="sxs-lookup"><span data-stu-id="af075-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="af075-109">最多可支援29個有效位數，而且可以代表超過 7.9228 x 10 ^ 28 的值。</span><span class="sxs-lookup"><span data-stu-id="af075-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="af075-110">它特別適合需要大量數位但無法容忍進位誤差的計算（例如財務）。</span><span class="sxs-lookup"><span data-stu-id="af075-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="af075-111">`Decimal` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="af075-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="af075-112">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="af075-112">Programming Tips</span></span>

- <span data-ttu-id="af075-113">**精密.**</span><span class="sxs-lookup"><span data-stu-id="af075-113">**Precision.**</span></span> <span data-ttu-id="af075-114">`Decimal`不是浮點資料類型。</span><span class="sxs-lookup"><span data-stu-id="af075-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="af075-115">`Decimal`結構會保存一個二進位整數值，加上一個正負號位和一個整數縮放因素，指定值的哪個部分是小數部分。</span><span class="sxs-lookup"><span data-stu-id="af075-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="af075-116">因此， `Decimal` 數位在記憶體中的表示方式比浮點類型（ `Single` 和）更精確 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="af075-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="af075-117">**效能。**</span><span class="sxs-lookup"><span data-stu-id="af075-117">**Performance.**</span></span> <span data-ttu-id="af075-118">`Decimal`資料類型是所有數數值型別的最慢。</span><span class="sxs-lookup"><span data-stu-id="af075-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="af075-119">在選擇資料類型之前，您應該先衡量精確度與效能的重要性。</span><span class="sxs-lookup"><span data-stu-id="af075-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="af075-120">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="af075-120">**Widening.**</span></span> <span data-ttu-id="af075-121">`Decimal`資料類型會擴大至 `Single` 或 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="af075-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="af075-122">這表示您可以在 `Decimal` 不發生錯誤的情況下，轉換成其中一種類型 <xref:System.OverflowException?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="af075-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="af075-123">**尾端零。**</span><span class="sxs-lookup"><span data-stu-id="af075-123">**Trailing Zeros.**</span></span> <span data-ttu-id="af075-124">Visual Basic 不會在常值中儲存尾端零 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="af075-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="af075-125">不過， `Decimal` 變數會保留任何尾端零的計算。</span><span class="sxs-lookup"><span data-stu-id="af075-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="af075-126">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="af075-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="af075-127">上述範例中的輸出如下所示 `MsgBox` ：</span><span class="sxs-lookup"><span data-stu-id="af075-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="af075-128">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="af075-128">**Type Characters.**</span></span> <span data-ttu-id="af075-129">將常值類型字元 `D` 附加到常值，會強制其成為 `Decimal` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="af075-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="af075-130">將識別項類型字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="af075-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="af075-131">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="af075-131">**Framework Type.**</span></span> <span data-ttu-id="af075-132">在 .NET Framework 中對應的類型為 <xref:System.Decimal?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="af075-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="af075-133">範圍</span><span class="sxs-lookup"><span data-stu-id="af075-133">Range</span></span>

 <span data-ttu-id="af075-134">您可能需要使用 `D` 類型字元，將大數值指派給 `Decimal` 變數或常數。</span><span class="sxs-lookup"><span data-stu-id="af075-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="af075-135">這項需求是因為編譯器會將常值解讀為 `Long` ，除非常數值型別字元遵循常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="af075-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="af075-136">的宣告 `bigDec1` 不會產生溢位，因為指派給它的值落在的範圍內 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="af075-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="af075-137">此 `Long` 值可指派給 `Decimal` 變數。</span><span class="sxs-lookup"><span data-stu-id="af075-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="af075-138">的宣告 `bigDec2` 會產生溢位錯誤，因為指派給它的值對而言太大 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="af075-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="af075-139">因為數值常值無法先解讀為 `Long` ，所以無法將它指派給 `Decimal` 變數。</span><span class="sxs-lookup"><span data-stu-id="af075-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="af075-140">對於 `bigDec3` ，常數值型別字元會 `D` 強制編譯器將常值解讀成， `Decimal` 而不是做為，藉此解決此問題 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="af075-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="af075-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af075-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="af075-142">資料類型</span><span class="sxs-lookup"><span data-stu-id="af075-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="af075-143">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="af075-143">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="af075-144">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="af075-144">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="af075-145">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="af075-145">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="af075-146">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="af075-146">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="af075-147">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="af075-147">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
