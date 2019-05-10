---
title: 字串資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: af75f5eb5a4281f6efae8ec3c9442ce2b28f595e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646989"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="95abf-102">字串資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95abf-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="95abf-103">保存帶正負號的 IEEE 32 位元 （4 個位元組） 單精確度浮點數，值範圍從-3.4028235E + 38 到-1.401298E-45 負值，以及從 1.401298E-45 到 3.4028235E + 38 的正數值。</span><span class="sxs-lookup"><span data-stu-id="95abf-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="95abf-104">單精確度數字儲存的是實數的近似值。</span><span class="sxs-lookup"><span data-stu-id="95abf-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95abf-105">備註</span><span class="sxs-lookup"><span data-stu-id="95abf-105">Remarks</span></span>  
 <span data-ttu-id="95abf-106">使用`Single`資料類型可包含不需要完整的資料寬度的浮點值`Double`。</span><span class="sxs-lookup"><span data-stu-id="95abf-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="95abf-107">在某些情況下的 common language runtime 可能可以將封裝您`Single`緊密合作，並將記憶體耗用量儲存的變數。</span><span class="sxs-lookup"><span data-stu-id="95abf-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="95abf-108">`Single` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="95abf-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="95abf-109">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="95abf-109">Programming Tips</span></span>  
  
- <span data-ttu-id="95abf-110">**有效位數。**</span><span class="sxs-lookup"><span data-stu-id="95abf-110">**Precision.**</span></span> <span data-ttu-id="95abf-111">當您使用浮點數時，記住其在記憶體中不一定有精確的表示法。</span><span class="sxs-lookup"><span data-stu-id="95abf-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="95abf-112">這可能會導致非預期的結果從某些作業，例如要做數值比較，`Mod`運算子。</span><span class="sxs-lookup"><span data-stu-id="95abf-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="95abf-113">如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="95abf-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="95abf-114">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="95abf-114">**Widening.**</span></span> <span data-ttu-id="95abf-115">`Single`資料類型可擴展為`Double`。</span><span class="sxs-lookup"><span data-stu-id="95abf-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="95abf-116">這表示您可以將轉換`Single`要`Double`而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="95abf-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="95abf-117">**尾端零。**</span><span class="sxs-lookup"><span data-stu-id="95abf-117">**Trailing Zeros.**</span></span> <span data-ttu-id="95abf-118">浮點資料類型沒有任何結尾 0 字元的內部表示法。</span><span class="sxs-lookup"><span data-stu-id="95abf-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="95abf-119">比方說，它們無法區分 4.2000 與 4.2。</span><span class="sxs-lookup"><span data-stu-id="95abf-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="95abf-120">因此，結尾 0 字元時，沒有出現在顯示或列印浮點數的值。</span><span class="sxs-lookup"><span data-stu-id="95abf-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="95abf-121">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="95abf-121">**Type Characters.**</span></span> <span data-ttu-id="95abf-122">將常值類型字元 `F` 附加到常值，會強制其成為 `Single` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="95abf-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="95abf-123">將識別項類型字元 `!` 附加到任何識別項，會強制其成為 `Single`。</span><span class="sxs-lookup"><span data-stu-id="95abf-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="95abf-124">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="95abf-124">**Framework Type.**</span></span> <span data-ttu-id="95abf-125">在 .NET Framework 中對應的類型為 <xref:System.Single?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="95abf-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95abf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95abf-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="95abf-127">資料類型</span><span class="sxs-lookup"><span data-stu-id="95abf-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="95abf-128">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="95abf-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="95abf-129">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="95abf-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="95abf-130">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="95abf-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="95abf-131">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="95abf-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="95abf-132">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="95abf-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="95abf-133">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="95abf-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
