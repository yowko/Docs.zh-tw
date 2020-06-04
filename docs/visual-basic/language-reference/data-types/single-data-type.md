---
title: Single 資料類型
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
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415527"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="60470-102">字串資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60470-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="60470-103">保存已簽署的 IEEE 32 位（4個位元組）單精確度浮點數，範圍介於-3.4028235 E + 38 到-1.401298 E-45 的值中，負值和從 1.401298 E-45 到 3.4028235 E + 38 的正值。</span><span class="sxs-lookup"><span data-stu-id="60470-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="60470-104">單精確度浮點數會儲存實數的近似值。</span><span class="sxs-lookup"><span data-stu-id="60470-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60470-105">備註</span><span class="sxs-lookup"><span data-stu-id="60470-105">Remarks</span></span>  

 <span data-ttu-id="60470-106">使用 `Single` 資料類型來包含不需要完整資料寬度的浮點值 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="60470-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="60470-107">在某些情況下，通用語言執行時間可能可以將您的 `Single` 變數緊密地結合在一起，並節省記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="60470-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="60470-108">`Single` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="60470-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="60470-109">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="60470-109">Programming Tips</span></span>  
  
- <span data-ttu-id="60470-110">**精密.**</span><span class="sxs-lookup"><span data-stu-id="60470-110">**Precision.**</span></span> <span data-ttu-id="60470-111">當您使用浮點數時，請記住它們不一定會在記憶體中有精確的標記法。</span><span class="sxs-lookup"><span data-stu-id="60470-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="60470-112">這可能會導致某些作業產生非預期的結果，例如值比較和 `Mod` 運算子。</span><span class="sxs-lookup"><span data-stu-id="60470-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="60470-113">如需詳細資訊，請參閱針對[資料類型進行疑難排解](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="60470-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="60470-114">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="60470-114">**Widening.**</span></span> <span data-ttu-id="60470-115">`Single`資料類型會擴大為 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="60470-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="60470-116">這表示您可以將轉換 `Single` 成， `Double` 而不會 <xref:System.OverflowException?displayProperty=nameWithType> 發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="60470-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="60470-117">**尾端零。**</span><span class="sxs-lookup"><span data-stu-id="60470-117">**Trailing Zeros.**</span></span> <span data-ttu-id="60470-118">浮點資料類型沒有尾端0字元的任何內部標記法。</span><span class="sxs-lookup"><span data-stu-id="60470-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="60470-119">例如，它們不會區分4.2000 和4.2。</span><span class="sxs-lookup"><span data-stu-id="60470-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="60470-120">因此，當您顯示或列印浮點值時，不會顯示尾端的0個字元。</span><span class="sxs-lookup"><span data-stu-id="60470-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="60470-121">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="60470-121">**Type Characters.**</span></span> <span data-ttu-id="60470-122">將常值類型字元 `F` 附加到常值，會強制其成為 `Single` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="60470-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="60470-123">將識別項類型字元 `!` 附加到任何識別項，會強制其成為 `Single`。</span><span class="sxs-lookup"><span data-stu-id="60470-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="60470-124">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="60470-124">**Framework Type.**</span></span> <span data-ttu-id="60470-125">在 .NET Framework 中對應的類型為 <xref:System.Single?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="60470-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60470-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60470-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="60470-127">資料類型</span><span class="sxs-lookup"><span data-stu-id="60470-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="60470-128">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="60470-128">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="60470-129">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="60470-129">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="60470-130">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="60470-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="60470-131">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="60470-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="60470-132">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="60470-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="60470-133">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="60470-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
