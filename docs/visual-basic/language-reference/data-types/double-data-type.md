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
ms.openlocfilehash: 6273f6c9e71f286bdbebc3fe1953988b43de3101
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663210"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="d2faf-102">Double 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2faf-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="d2faf-103">保存帶正負號的 IEEE 64 位元 （8 個位元組） 雙精確度浮點數，範圍從-1.79769313486231570 e + 308 到-4.94065645841246544-324 負值進出 4.94065645841246544-324 1.79769313486231570 e + 308 到正的數值。</span><span class="sxs-lookup"><span data-stu-id="d2faf-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="d2faf-104">雙精度數字儲存的是實數的近似值。</span><span class="sxs-lookup"><span data-stu-id="d2faf-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2faf-105">備註</span><span class="sxs-lookup"><span data-stu-id="d2faf-105">Remarks</span></span>  
 <span data-ttu-id="d2faf-106">`Double`資料類型提供許多最大和最小可能的範圍。</span><span class="sxs-lookup"><span data-stu-id="d2faf-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="d2faf-107">`Double` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="d2faf-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="d2faf-108">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="d2faf-108">Programming Tips</span></span>  
  
- <span data-ttu-id="d2faf-109">**有效位數。**</span><span class="sxs-lookup"><span data-stu-id="d2faf-109">**Precision.**</span></span> <span data-ttu-id="d2faf-110">當您使用浮點數時，請記得它們在記憶體中不一定有精確的表示法。</span><span class="sxs-lookup"><span data-stu-id="d2faf-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="d2faf-111">這可能會導致非預期的結果從某些作業，例如要做數值比較，`Mod`運算子。</span><span class="sxs-lookup"><span data-stu-id="d2faf-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="d2faf-112">如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d2faf-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="d2faf-113">**尾端零。**</span><span class="sxs-lookup"><span data-stu-id="d2faf-113">**Trailing Zeros.**</span></span> <span data-ttu-id="d2faf-114">浮點資料類型沒有任何的尾端零個字元的內部表示法。</span><span class="sxs-lookup"><span data-stu-id="d2faf-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="d2faf-115">比方說，它們無法區分 4.2000 與 4.2。</span><span class="sxs-lookup"><span data-stu-id="d2faf-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="d2faf-116">因此，尾端零字元不會出現在顯示或列印的浮點值。</span><span class="sxs-lookup"><span data-stu-id="d2faf-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="d2faf-117">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="d2faf-117">**Type Characters.**</span></span> <span data-ttu-id="d2faf-118">將常值類型字元 `R` 附加到常值，會強制其成為 `Double` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d2faf-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="d2faf-119">例如，如果整數值，後面跟著`R`的值變更為`Double`。</span><span class="sxs-lookup"><span data-stu-id="d2faf-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="d2faf-120">將識別項類型字元 `#` 附加到任何識別項，會強制其成為 `Double`。</span><span class="sxs-lookup"><span data-stu-id="d2faf-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="d2faf-121">在下列範例中，變數`num`型別為`Double`:</span><span class="sxs-lookup"><span data-stu-id="d2faf-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
- <span data-ttu-id="d2faf-122">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="d2faf-122">**Framework Type.**</span></span> <span data-ttu-id="d2faf-123">在 .NET Framework 中對應的類型為 <xref:System.Double?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="d2faf-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2faf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2faf-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="d2faf-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="d2faf-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d2faf-126">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="d2faf-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="d2faf-127">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="d2faf-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="d2faf-128">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="d2faf-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d2faf-129">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="d2faf-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="d2faf-130">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="d2faf-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="d2faf-131">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="d2faf-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="d2faf-132">類型字元</span><span class="sxs-lookup"><span data-stu-id="d2faf-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
