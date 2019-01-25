---
title: Decimal 資料類型 (Visual Basic)
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
ms.openlocfilehash: 7a04f0a9862927f8588a895c7f0f099509aa4d8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512888"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="a4783-102">Decimal 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4783-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="a4783-103">保存帶正負號的 128 位元 （16 個位元組） 值，表示調整變數的 10 乘冪的 96 位元 （12 個位元組） 整數數字。</span><span class="sxs-lookup"><span data-stu-id="a4783-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="a4783-104">縮放比例指定小數點; 右邊的數字的數目其範圍從 0 到 28。</span><span class="sxs-lookup"><span data-stu-id="a4783-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="a4783-105">數位數為 0 （沒有小數位數），最大的可能值是 + /-79228162514264337593543950335 (+ /-7.9228162514264337593543950335E + 28)。</span><span class="sxs-lookup"><span data-stu-id="a4783-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="a4783-106">28 的小數位數，最大值是 + /--7.9228162514264337593543950335，與最小的非零值是 + /-0.0000000000000000000000000001 （+ /-1E-28)。</span><span class="sxs-lookup"><span data-stu-id="a4783-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4783-107">備註</span><span class="sxs-lookup"><span data-stu-id="a4783-107">Remarks</span></span>  
 <span data-ttu-id="a4783-108">`Decimal`資料類型提供許多有效位數的最大數目。</span><span class="sxs-lookup"><span data-stu-id="a4783-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="a4783-109">它支援多達 29 個有效位數，而且可以代表值超出 7.9228 x 10 ^28。</span><span class="sxs-lookup"><span data-stu-id="a4783-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="a4783-110">它是特別適合用來計算，例如財務、，需要大量的數字，但無法容忍捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4783-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="a4783-111">`Decimal` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="a4783-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="a4783-112">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="a4783-112">Programming Tips</span></span>  
  
-   <span data-ttu-id="a4783-113">**有效位數。**</span><span class="sxs-lookup"><span data-stu-id="a4783-113">**Precision.**</span></span> <span data-ttu-id="a4783-114">`Decimal` 不是浮點資料類型。</span><span class="sxs-lookup"><span data-stu-id="a4783-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="a4783-115">`Decimal`結構包含二進位整數值，以及正負號位元和縮放比例，指定哪些部分的值為十進位小數的整數。</span><span class="sxs-lookup"><span data-stu-id="a4783-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="a4783-116">基於這個原因，`Decimal`數字中的記憶體比浮點數類型有更精確的表示法 (`Single`和`Double`)。</span><span class="sxs-lookup"><span data-stu-id="a4783-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
-   <span data-ttu-id="a4783-117">**效能。**</span><span class="sxs-lookup"><span data-stu-id="a4783-117">**Performance.**</span></span> <span data-ttu-id="a4783-118">`Decimal`資料類型是最慢的所有數字的類型。</span><span class="sxs-lookup"><span data-stu-id="a4783-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="a4783-119">您應該衡量精確度和效能，再選擇的資料類型的重要性。</span><span class="sxs-lookup"><span data-stu-id="a4783-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
-   <span data-ttu-id="a4783-120">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="a4783-120">**Widening.**</span></span> <span data-ttu-id="a4783-121">`Decimal`資料類型可擴展為`Single`或`Double`。</span><span class="sxs-lookup"><span data-stu-id="a4783-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="a4783-122">這表示您可以將轉換`Decimal`而不會發生這些類型的任何一個<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4783-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="a4783-123">**尾端零。**</span><span class="sxs-lookup"><span data-stu-id="a4783-123">**Trailing Zeros.**</span></span> <span data-ttu-id="a4783-124">Visual Basic 不會儲存的尾端零`Decimal`常值。</span><span class="sxs-lookup"><span data-stu-id="a4783-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="a4783-125">不過，`Decimal`變數會保留運算資源取得任何尾端零。</span><span class="sxs-lookup"><span data-stu-id="a4783-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="a4783-126">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="a4783-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="a4783-127">輸出`MsgBox`前一個範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="a4783-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="a4783-128">d1 = 2.375，d2 = 1.625，d3 = 4.000，d4 = 4</span><span class="sxs-lookup"><span data-stu-id="a4783-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
-   <span data-ttu-id="a4783-129">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="a4783-129">**Type Characters.**</span></span> <span data-ttu-id="a4783-130">將常值類型字元 `D` 附加到常值，會強制其成為 `Decimal` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="a4783-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="a4783-131">將識別項類型字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a4783-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
-   <span data-ttu-id="a4783-132">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="a4783-132">**Framework Type.**</span></span> <span data-ttu-id="a4783-133">在 .NET Framework 中對應的類型為 <xref:System.Decimal?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="a4783-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="a4783-134">範圍</span><span class="sxs-lookup"><span data-stu-id="a4783-134">Range</span></span>  
 <span data-ttu-id="a4783-135">您可能需要使用`D`型別字元，將大型值指派給`Decimal`變數或常數。</span><span class="sxs-lookup"><span data-stu-id="a4783-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="a4783-136">此需求是因為編譯器會解譯為常值`Long`除非常值類型字元會遵循常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a4783-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="a4783-137">宣告`bigDec1`不會產生溢位，因為指派給它的值落在範圍內`Long`。</span><span class="sxs-lookup"><span data-stu-id="a4783-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="a4783-138">`Long`可以將值指派給`Decimal`變數。</span><span class="sxs-lookup"><span data-stu-id="a4783-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="a4783-139">宣告`bigDec2`指派給它的值太大，所以會產生溢位錯誤`Long`。</span><span class="sxs-lookup"><span data-stu-id="a4783-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="a4783-140">因為數值常值第一次無法解譯為`Long`，不能將它指派給`Decimal`變數。</span><span class="sxs-lookup"><span data-stu-id="a4783-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="a4783-141">針對`bigDec3`，常值類型字元`D`解決問題，強制編譯器將解譯為常值`Decimal`而不是做為`Long`。</span><span class="sxs-lookup"><span data-stu-id="a4783-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4783-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4783-142">See also</span></span>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a4783-143">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4783-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a4783-144">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="a4783-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="a4783-145">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="a4783-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="a4783-146">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="a4783-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a4783-147">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="a4783-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a4783-148">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="a4783-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
