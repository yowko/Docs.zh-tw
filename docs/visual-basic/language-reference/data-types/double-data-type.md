---
title: Double 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 92adb26702d94dee08e51decd845d019c797e195
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630092"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="27eb7-102">Double 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27eb7-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="27eb7-103">保存已簽署的 IEEE 64 位 (8 位元組) 雙精確度浮點數, 範圍介於-1.79769313486231570 E + 308 到-4.94065645841246544 E-324 中的負值, 以及從 4.94065645841246544 E-324 到 1.79769313486231570 E + 308 的值正數值。</span><span class="sxs-lookup"><span data-stu-id="27eb7-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="27eb7-104">雙精度浮點數會儲存實數的近似值。</span><span class="sxs-lookup"><span data-stu-id="27eb7-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="27eb7-105">備註</span><span class="sxs-lookup"><span data-stu-id="27eb7-105">Remarks</span></span>

<span data-ttu-id="27eb7-106">`Double`資料類型會針對某個數位提供最大和最小的可能巨量。</span><span class="sxs-lookup"><span data-stu-id="27eb7-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="27eb7-107">`Double` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="27eb7-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="27eb7-108">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="27eb7-108">Programming Tips</span></span>

- <span data-ttu-id="27eb7-109">**精密.**</span><span class="sxs-lookup"><span data-stu-id="27eb7-109">**Precision.**</span></span> <span data-ttu-id="27eb7-110">當您使用浮點數時, 請記住它們不一定會在記憶體中有精確的標記法。</span><span class="sxs-lookup"><span data-stu-id="27eb7-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="27eb7-111">這可能會導致某些作業產生非預期的結果, 例如值比較和`Mod`運算子。</span><span class="sxs-lookup"><span data-stu-id="27eb7-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="27eb7-112">如需詳細資訊, 請參閱針對[資料類型進行疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="27eb7-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="27eb7-113">**尾端零。**</span><span class="sxs-lookup"><span data-stu-id="27eb7-113">**Trailing Zeros.**</span></span> <span data-ttu-id="27eb7-114">浮點資料類型沒有尾端零字元的任何內部表示。</span><span class="sxs-lookup"><span data-stu-id="27eb7-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="27eb7-115">例如, 它們不會區分4.2000 和4.2。</span><span class="sxs-lookup"><span data-stu-id="27eb7-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="27eb7-116">因此, 當您顯示或列印浮點值時, 不會出現尾端的零字元。</span><span class="sxs-lookup"><span data-stu-id="27eb7-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="27eb7-117">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="27eb7-117">**Type Characters.**</span></span> <span data-ttu-id="27eb7-118">將常值類型字元 `R` 附加到常值，會強制其成為 `Double` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="27eb7-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="27eb7-119">例如, 如果整數值後面接著`R`, 則值會變更`Double`為。</span><span class="sxs-lookup"><span data-stu-id="27eb7-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="27eb7-120">將識別項類型字元 `#` 附加到任何識別項，會強制其成為 `Double`。</span><span class="sxs-lookup"><span data-stu-id="27eb7-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="27eb7-121">在下列範例中, 變數`num`的類型`Double`為:</span><span class="sxs-lookup"><span data-stu-id="27eb7-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="27eb7-122">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="27eb7-122">**Framework Type.**</span></span> <span data-ttu-id="27eb7-123">在 .NET Framework 中對應的類型為 <xref:System.Double?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="27eb7-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="27eb7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27eb7-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="27eb7-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="27eb7-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="27eb7-126">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="27eb7-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="27eb7-127">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="27eb7-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="27eb7-128">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="27eb7-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="27eb7-129">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="27eb7-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="27eb7-130">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="27eb7-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="27eb7-131">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="27eb7-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="27eb7-132">類型字元</span><span class="sxs-lookup"><span data-stu-id="27eb7-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
