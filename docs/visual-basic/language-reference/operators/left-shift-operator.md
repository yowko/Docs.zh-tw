---
title: "&lt;&lt;運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56cfb227f7e5c68de802c1f2cfb842a770f65ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="6b0e1-102">&lt;&lt;運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b0e1-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="6b0e1-103">位元模式上執行算術左的移位。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b0e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b0e1-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="6b0e1-105">組件</span><span class="sxs-lookup"><span data-stu-id="6b0e1-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6b0e1-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-106">Required.</span></span> <span data-ttu-id="6b0e1-107">整數值。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-107">Integral numeric value.</span></span> <span data-ttu-id="6b0e1-108">移位的位元模式的結果。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="6b0e1-109">資料類型是屬於相同`pattern`。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="6b0e1-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-110">Required.</span></span> <span data-ttu-id="6b0e1-111">整數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-111">Integral numeric expression.</span></span> <span data-ttu-id="6b0e1-112">要移位的位元模式。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="6b0e1-113">資料型別必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="6b0e1-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-114">Required.</span></span> <span data-ttu-id="6b0e1-115">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-115">Numeric expression.</span></span> <span data-ttu-id="6b0e1-116">要移位的位元模式的位元數。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="6b0e1-117">資料類型必須是`Integer`或擴展為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b0e1-118">備註</span><span class="sxs-lookup"><span data-stu-id="6b0e1-118">Remarks</span></span>  
 <span data-ttu-id="6b0e1-119">算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="6b0e1-120">在算術左移位，移位超出結果資料類型之範圍的位元會捨棄，而且右方空出的位元位置會設定為零。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="6b0e1-121">若要避免多於結果所能容納更多的位元位移，Visual Basic 遮罩的值`amount`與對應的資料類型的大小遮罩`pattern`。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="6b0e1-122">這些值的二進位 AND 用於移位量。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="6b0e1-123">遮罩的大小如下所示：</span><span class="sxs-lookup"><span data-stu-id="6b0e1-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="6b0e1-124">資料型別`pattern`</span><span class="sxs-lookup"><span data-stu-id="6b0e1-124">Data type of `pattern`</span></span>|<span data-ttu-id="6b0e1-125">大小遮罩 （十進位）</span><span class="sxs-lookup"><span data-stu-id="6b0e1-125">Size mask (decimal)</span></span>|<span data-ttu-id="6b0e1-126">大小遮罩 （十六進位）</span><span class="sxs-lookup"><span data-stu-id="6b0e1-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="6b0e1-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="6b0e1-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="6b0e1-128">7</span><span class="sxs-lookup"><span data-stu-id="6b0e1-128">7</span></span>|<span data-ttu-id="6b0e1-129">（& S) H00000007</span><span class="sxs-lookup"><span data-stu-id="6b0e1-129">&H00000007</span></span>|  
|<span data-ttu-id="6b0e1-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="6b0e1-130">`Short`, `UShort`</span></span>|<span data-ttu-id="6b0e1-131">15</span><span class="sxs-lookup"><span data-stu-id="6b0e1-131">15</span></span>|<span data-ttu-id="6b0e1-132">（& S) H0000000F</span><span class="sxs-lookup"><span data-stu-id="6b0e1-132">&H0000000F</span></span>|  
|<span data-ttu-id="6b0e1-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="6b0e1-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="6b0e1-134">31</span><span class="sxs-lookup"><span data-stu-id="6b0e1-134">31</span></span>|<span data-ttu-id="6b0e1-135">（& S) H0000001F</span><span class="sxs-lookup"><span data-stu-id="6b0e1-135">&H0000001F</span></span>|  
|<span data-ttu-id="6b0e1-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="6b0e1-136">`Long`, `ULong`</span></span>|<span data-ttu-id="6b0e1-137">63</span><span class="sxs-lookup"><span data-stu-id="6b0e1-137">63</span></span>|<span data-ttu-id="6b0e1-138">（& S) H0000003F</span><span class="sxs-lookup"><span data-stu-id="6b0e1-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="6b0e1-139">如果`amount`是零，值`result`等同於值`pattern`。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="6b0e1-140">如果`amount`是負數，它是被視為不帶正負號的值，加上適當的大小遮罩。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="6b0e1-141">算術移位不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b0e1-142">`<<`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6b0e1-143">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="6b0e1-144">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b0e1-145">範例</span><span class="sxs-lookup"><span data-stu-id="6b0e1-145">Example</span></span>  
 <span data-ttu-id="6b0e1-146">下列範例會使用`<<`運算子來執行算術左移位整數值。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="6b0e1-147">結果會有相同的資料類型已移位之運算式。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="6b0e1-148">前一個範例的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="6b0e1-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="6b0e1-149">`result1`為 192 (0000 0000 1100年 0000)。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="6b0e1-150">`result2`會 3072 (0000 1100年 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="6b0e1-151">`result3`是介於-32768 (1000年 0000 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="6b0e1-152">`result4`為 384 (0000 0001 1000年 0000)。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="6b0e1-153">`result5`為 0 （左邊的移位 15 位數）。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="6b0e1-154">移位量的`result4`的計算方式為 17 和 15，等於 1。</span><span class="sxs-lookup"><span data-stu-id="6b0e1-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b0e1-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b0e1-155">See Also</span></span>  
 [<span data-ttu-id="6b0e1-156">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="6b0e1-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="6b0e1-157">指派運算子</span><span class="sxs-lookup"><span data-stu-id="6b0e1-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="6b0e1-158"><<= 運算子</span><span class="sxs-lookup"><span data-stu-id="6b0e1-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [<span data-ttu-id="6b0e1-159">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="6b0e1-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="6b0e1-160">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="6b0e1-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="6b0e1-161">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="6b0e1-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
