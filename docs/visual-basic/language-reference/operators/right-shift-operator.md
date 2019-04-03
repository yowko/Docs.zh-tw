---
title: '>> 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816963"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="02a36-102">>> 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02a36-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="02a36-103">位元模式中執行算術右移位。</span><span class="sxs-lookup"><span data-stu-id="02a36-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02a36-104">語法</span><span class="sxs-lookup"><span data-stu-id="02a36-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="02a36-105">組件</span><span class="sxs-lookup"><span data-stu-id="02a36-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="02a36-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="02a36-106">Required.</span></span> <span data-ttu-id="02a36-107">整數值。</span><span class="sxs-lookup"><span data-stu-id="02a36-107">Integral numeric value.</span></span> <span data-ttu-id="02a36-108">移位的位元模式的結果。</span><span class="sxs-lookup"><span data-stu-id="02a36-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="02a36-109">資料類型是屬於相同`pattern`。</span><span class="sxs-lookup"><span data-stu-id="02a36-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="02a36-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="02a36-110">Required.</span></span> <span data-ttu-id="02a36-111">整數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="02a36-111">Integral numeric expression.</span></span> <span data-ttu-id="02a36-112">要移位的位元模式。</span><span class="sxs-lookup"><span data-stu-id="02a36-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="02a36-113">資料類型必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="02a36-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="02a36-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="02a36-114">Required.</span></span> <span data-ttu-id="02a36-115">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="02a36-115">Numeric expression.</span></span> <span data-ttu-id="02a36-116">位元模式移位的位元數。</span><span class="sxs-lookup"><span data-stu-id="02a36-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="02a36-117">資料類型必須是`Integer`或擴展至`Integer`。</span><span class="sxs-lookup"><span data-stu-id="02a36-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02a36-118">備註</span><span class="sxs-lookup"><span data-stu-id="02a36-118">Remarks</span></span>  
 <span data-ttu-id="02a36-119">算術的排班不是循環，這表示移出結果的某一端的位元不會重新引入另一端。</span><span class="sxs-lookup"><span data-stu-id="02a36-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="02a36-120">在算術右移位，移位超過最右邊位元位置的位元會予以捨棄，並最左邊 （符號） 位元會傳播到左邊空出的位元位置。</span><span class="sxs-lookup"><span data-stu-id="02a36-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="02a36-121">這表示如果`pattern`的值是負數，空出的位置會設為其中一個; 否則設定為零。</span><span class="sxs-lookup"><span data-stu-id="02a36-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="02a36-122">請注意，資料類型`Byte`， `UShort`， `UInteger`，和`ULong`是不帶正負號，因此沒有傳播沒有正負號位元。</span><span class="sxs-lookup"><span data-stu-id="02a36-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="02a36-123">如果`pattern`的任何不帶正負號的類型、 空出的位置一律會設定為零。</span><span class="sxs-lookup"><span data-stu-id="02a36-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="02a36-124">若要避免超出結果所能持有更多的位元移位，Visual Basic 會遮罩的值`amount`具有對應的資料類型大小遮罩`pattern`。</span><span class="sxs-lookup"><span data-stu-id="02a36-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="02a36-125">這些值的二進位 AND 用於移位量。</span><span class="sxs-lookup"><span data-stu-id="02a36-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="02a36-126">遮罩的大小如下所示：</span><span class="sxs-lookup"><span data-stu-id="02a36-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="02a36-127">資料類型 `pattern`</span><span class="sxs-lookup"><span data-stu-id="02a36-127">Data type of `pattern`</span></span>|<span data-ttu-id="02a36-128">大小遮罩 （十進位）</span><span class="sxs-lookup"><span data-stu-id="02a36-128">Size mask (decimal)</span></span>|<span data-ttu-id="02a36-129">大小遮罩 （十六進位）</span><span class="sxs-lookup"><span data-stu-id="02a36-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="02a36-130">`SByte`、 `Byte`</span><span class="sxs-lookup"><span data-stu-id="02a36-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="02a36-131">7</span><span class="sxs-lookup"><span data-stu-id="02a36-131">7</span></span>|<span data-ttu-id="02a36-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="02a36-132">&H00000007</span></span>|  
|<span data-ttu-id="02a36-133">`Short`、 `UShort`</span><span class="sxs-lookup"><span data-stu-id="02a36-133">`Short`, `UShort`</span></span>|<span data-ttu-id="02a36-134">15</span><span class="sxs-lookup"><span data-stu-id="02a36-134">15</span></span>|<span data-ttu-id="02a36-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="02a36-135">&H0000000F</span></span>|  
|<span data-ttu-id="02a36-136">`Integer`、 `UInteger`</span><span class="sxs-lookup"><span data-stu-id="02a36-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="02a36-137">31</span><span class="sxs-lookup"><span data-stu-id="02a36-137">31</span></span>|<span data-ttu-id="02a36-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="02a36-138">&H0000001F</span></span>|  
|<span data-ttu-id="02a36-139">`Long`、 `ULong`</span><span class="sxs-lookup"><span data-stu-id="02a36-139">`Long`, `ULong`</span></span>|<span data-ttu-id="02a36-140">63</span><span class="sxs-lookup"><span data-stu-id="02a36-140">63</span></span>|<span data-ttu-id="02a36-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="02a36-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="02a36-142">如果`amount`為零，則值`result`的值一致`pattern`。</span><span class="sxs-lookup"><span data-stu-id="02a36-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="02a36-143">如果`amount`是負數，它是做為不帶正負號的值，加上適當的大小遮罩。</span><span class="sxs-lookup"><span data-stu-id="02a36-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="02a36-144">算術移位絕不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="02a36-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="02a36-145">多載化</span><span class="sxs-lookup"><span data-stu-id="02a36-145">Overloading</span></span>  
 <span data-ttu-id="02a36-146">`>>`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="02a36-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="02a36-147">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="02a36-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="02a36-148">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="02a36-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02a36-149">範例</span><span class="sxs-lookup"><span data-stu-id="02a36-149">Example</span></span>  
 <span data-ttu-id="02a36-150">下列範例會使用`>>`整數值上執行算術右移位運算子。</span><span class="sxs-lookup"><span data-stu-id="02a36-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="02a36-151">結果會有相同的資料類型的已移位的運算式。</span><span class="sxs-lookup"><span data-stu-id="02a36-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="02a36-152">上述範例的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="02a36-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="02a36-153">`result1` 是 2560 (0000 1010年 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="02a36-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="02a36-154">`result2` 是 160 (0000 0000 1010年 0000)。</span><span class="sxs-lookup"><span data-stu-id="02a36-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="02a36-155">`result3` 為 2 (0000 0000 0000 0010)。</span><span class="sxs-lookup"><span data-stu-id="02a36-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="02a36-156">`result4` 為 640 (0000 0010 1000年 0000)。</span><span class="sxs-lookup"><span data-stu-id="02a36-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="02a36-157">`result5` 為 0 （右邊的移位 15 位數）。</span><span class="sxs-lookup"><span data-stu-id="02a36-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="02a36-158">移位量的`result4`的計算方式為 18 和 15，等於 2。</span><span class="sxs-lookup"><span data-stu-id="02a36-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="02a36-159">下列範例會顯示在負值上算術移位。</span><span class="sxs-lookup"><span data-stu-id="02a36-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="02a36-160">上述範例的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="02a36-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="02a36-161">`negresult1` 是-512 (1111年 1110年 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="02a36-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="02a36-162">`negresult2` 為-1 （傳播正負號位元）。</span><span class="sxs-lookup"><span data-stu-id="02a36-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a36-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02a36-163">See also</span></span>

- [<span data-ttu-id="02a36-164">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="02a36-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="02a36-165">指派運算子</span><span class="sxs-lookup"><span data-stu-id="02a36-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="02a36-166">>>= 運算子</span><span class="sxs-lookup"><span data-stu-id="02a36-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="02a36-167">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="02a36-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="02a36-168">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="02a36-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="02a36-169">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="02a36-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
