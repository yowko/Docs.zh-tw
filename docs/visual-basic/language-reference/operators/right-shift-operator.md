---
title: '&gt;&gt;運算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4eb0ed817c95905a679de5026bf6494eb72df078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="3ca74-102">&gt;&gt;運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ca74-102">&gt;&gt; Operator (Visual Basic)</span></span>
<span data-ttu-id="3ca74-103">位元模式上執行算術右移位。</span><span class="sxs-lookup"><span data-stu-id="3ca74-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca74-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ca74-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="3ca74-105">組件</span><span class="sxs-lookup"><span data-stu-id="3ca74-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="3ca74-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="3ca74-106">Required.</span></span> <span data-ttu-id="3ca74-107">整數值。</span><span class="sxs-lookup"><span data-stu-id="3ca74-107">Integral numeric value.</span></span> <span data-ttu-id="3ca74-108">移位的位元模式的結果。</span><span class="sxs-lookup"><span data-stu-id="3ca74-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="3ca74-109">資料類型是屬於相同`pattern`。</span><span class="sxs-lookup"><span data-stu-id="3ca74-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="3ca74-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="3ca74-110">Required.</span></span> <span data-ttu-id="3ca74-111">整數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="3ca74-111">Integral numeric expression.</span></span> <span data-ttu-id="3ca74-112">要移位的位元模式。</span><span class="sxs-lookup"><span data-stu-id="3ca74-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="3ca74-113">資料型別必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="3ca74-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="3ca74-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="3ca74-114">Required.</span></span> <span data-ttu-id="3ca74-115">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="3ca74-115">Numeric expression.</span></span> <span data-ttu-id="3ca74-116">要移位的位元模式的位元數。</span><span class="sxs-lookup"><span data-stu-id="3ca74-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="3ca74-117">資料類型必須是`Integer`或擴展為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="3ca74-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ca74-118">備註</span><span class="sxs-lookup"><span data-stu-id="3ca74-118">Remarks</span></span>  
 <span data-ttu-id="3ca74-119">算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。</span><span class="sxs-lookup"><span data-stu-id="3ca74-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="3ca74-120">在算術右移位，移位超過右邊的位元位置的位元會捨棄，而且最左邊 （符號） 位元會傳播到左邊空出的位元位置。</span><span class="sxs-lookup"><span data-stu-id="3ca74-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="3ca74-121">這表示如果`pattern`負值，空出的位置會設為其中一個; 否則設定為零。</span><span class="sxs-lookup"><span data-stu-id="3ca74-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="3ca74-122">請注意，資料型別`Byte`， `UShort`， `UInteger`，和`ULong`是不帶正負號，所以傳播的無正負號位元。</span><span class="sxs-lookup"><span data-stu-id="3ca74-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="3ca74-123">如果`pattern`的任何不帶正負號型別、 空出的位置永遠會設定為零。</span><span class="sxs-lookup"><span data-stu-id="3ca74-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="3ca74-124">若要避免由多於結果所能容納更多的位元移位，Visual Basic 遮罩的值`amount`大小遮罩的資料類型對應`pattern`。</span><span class="sxs-lookup"><span data-stu-id="3ca74-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="3ca74-125">這些值的二進位 AND 用於移位量。</span><span class="sxs-lookup"><span data-stu-id="3ca74-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="3ca74-126">遮罩的大小如下所示：</span><span class="sxs-lookup"><span data-stu-id="3ca74-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="3ca74-127">資料型別`pattern`</span><span class="sxs-lookup"><span data-stu-id="3ca74-127">Data type of `pattern`</span></span>|<span data-ttu-id="3ca74-128">大小遮罩 （十進位）</span><span class="sxs-lookup"><span data-stu-id="3ca74-128">Size mask (decimal)</span></span>|<span data-ttu-id="3ca74-129">大小遮罩 （十六進位）</span><span class="sxs-lookup"><span data-stu-id="3ca74-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="3ca74-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="3ca74-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="3ca74-131">7</span><span class="sxs-lookup"><span data-stu-id="3ca74-131">7</span></span>|<span data-ttu-id="3ca74-132">（& S) H00000007</span><span class="sxs-lookup"><span data-stu-id="3ca74-132">&H00000007</span></span>|  
|<span data-ttu-id="3ca74-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="3ca74-133">`Short`, `UShort`</span></span>|<span data-ttu-id="3ca74-134">15</span><span class="sxs-lookup"><span data-stu-id="3ca74-134">15</span></span>|<span data-ttu-id="3ca74-135">（& S) H0000000F</span><span class="sxs-lookup"><span data-stu-id="3ca74-135">&H0000000F</span></span>|  
|<span data-ttu-id="3ca74-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="3ca74-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="3ca74-137">31</span><span class="sxs-lookup"><span data-stu-id="3ca74-137">31</span></span>|<span data-ttu-id="3ca74-138">（& S) H0000001F</span><span class="sxs-lookup"><span data-stu-id="3ca74-138">&H0000001F</span></span>|  
|<span data-ttu-id="3ca74-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="3ca74-139">`Long`, `ULong`</span></span>|<span data-ttu-id="3ca74-140">63</span><span class="sxs-lookup"><span data-stu-id="3ca74-140">63</span></span>|<span data-ttu-id="3ca74-141">（& S) H0000003F</span><span class="sxs-lookup"><span data-stu-id="3ca74-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="3ca74-142">如果`amount`是零，值`result`等同於值`pattern`。</span><span class="sxs-lookup"><span data-stu-id="3ca74-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="3ca74-143">如果`amount`是負數，它是被視為不帶正負號的值，加上適當的大小遮罩。</span><span class="sxs-lookup"><span data-stu-id="3ca74-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="3ca74-144">算術移位不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3ca74-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3ca74-145">多載化</span><span class="sxs-lookup"><span data-stu-id="3ca74-145">Overloading</span></span>  
 <span data-ttu-id="3ca74-146">`>>`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="3ca74-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3ca74-147">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="3ca74-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3ca74-148">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="3ca74-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ca74-149">範例</span><span class="sxs-lookup"><span data-stu-id="3ca74-149">Example</span></span>  
 <span data-ttu-id="3ca74-150">下列範例會使用`>>`整數值上執行算術右移位運算子。</span><span class="sxs-lookup"><span data-stu-id="3ca74-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="3ca74-151">結果會有相同的資料類型已移位之運算式。</span><span class="sxs-lookup"><span data-stu-id="3ca74-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 <span data-ttu-id="3ca74-152">前述範例中的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="3ca74-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="3ca74-153">`result1`是 2560 (0000 1010年 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="3ca74-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="3ca74-154">`result2`為 160 (0000 0000 1010年 0000)。</span><span class="sxs-lookup"><span data-stu-id="3ca74-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="3ca74-155">`result3`為 2 (0000 0000 0000 0010)。</span><span class="sxs-lookup"><span data-stu-id="3ca74-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="3ca74-156">`result4`為 640 (0000 0010 1000年 0000)。</span><span class="sxs-lookup"><span data-stu-id="3ca74-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="3ca74-157">`result5`為 0 （右邊的移位 15 位數）。</span><span class="sxs-lookup"><span data-stu-id="3ca74-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="3ca74-158">移位量的`result4`的計算方式為 18 和 15，等於 2。</span><span class="sxs-lookup"><span data-stu-id="3ca74-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="3ca74-159">下列範例顯示上一個負數值的算術移位。</span><span class="sxs-lookup"><span data-stu-id="3ca74-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 <span data-ttu-id="3ca74-160">前述範例中的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="3ca74-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="3ca74-161">`negresult1`是-512 (1111年 1110年 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="3ca74-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="3ca74-162">`negresult2`為-1 （傳播正負號位元）。</span><span class="sxs-lookup"><span data-stu-id="3ca74-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca74-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ca74-163">See Also</span></span>  
 [<span data-ttu-id="3ca74-164">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="3ca74-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="3ca74-165">指派運算子</span><span class="sxs-lookup"><span data-stu-id="3ca74-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="3ca74-166">>>= 運算子</span><span class="sxs-lookup"><span data-stu-id="3ca74-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [<span data-ttu-id="3ca74-167">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="3ca74-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="3ca74-168">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="3ca74-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="3ca74-169">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="3ca74-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
