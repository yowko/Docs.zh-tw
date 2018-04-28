---
title: Mod 運算子 (Visual Basic)
ms.date: 04/24/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf0889cbea609b4555581fbf67cd0cba1ea889d0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="bb36f-102">Mod 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb36f-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="bb36f-103">兩數相除並只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb36f-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb36f-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="bb36f-105">組件</span><span class="sxs-lookup"><span data-stu-id="bb36f-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="bb36f-106">必要。</span><span class="sxs-lookup"><span data-stu-id="bb36f-106">Required.</span></span> <span data-ttu-id="bb36f-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="bb36f-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="bb36f-108">必要。</span><span class="sxs-lookup"><span data-stu-id="bb36f-108">Required.</span></span> <span data-ttu-id="bb36f-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="bb36f-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="bb36f-110">支援的型別</span><span class="sxs-lookup"><span data-stu-id="bb36f-110">Supported types</span></span>  
 <span data-ttu-id="bb36f-111">所有數字類型。</span><span class="sxs-lookup"><span data-stu-id="bb36f-111">All numeric types.</span></span> <span data-ttu-id="bb36f-112">這包括不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="bb36f-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="bb36f-113">結果</span><span class="sxs-lookup"><span data-stu-id="bb36f-113">Result</span></span>

<span data-ttu-id="bb36f-114">結果是後的餘數`number1`除以`number2`。</span><span class="sxs-lookup"><span data-stu-id="bb36f-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="bb36f-115">例如，運算式`14 Mod 4`評估為 2。</span><span class="sxs-lookup"><span data-stu-id="bb36f-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  

> [!NOTE]
> <span data-ttu-id="bb36f-116">之間的差異*餘數*和*模數*在數學上，使用不同的結果為負數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-116">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="bb36f-117">`Mod`運算子在 Visual Basic 中，.NET Framework`op_Modulus`運算子，以及基礎 [rem]<xref:System.Reflection.Emit.OpCodes.Rem> IL 指令的所有執行其餘作業。</span><span class="sxs-lookup"><span data-stu-id="bb36f-117">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem]<xref:System.Reflection.Emit.OpCodes.Rem> IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="bb36f-118">結果`Mod`作業會保留除數的正負號`number1`，因此它可能是正數或負數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-118">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="bb36f-119">結果一定是範圍 (-`number2`， `number2`)、 獨佔。</span><span class="sxs-lookup"><span data-stu-id="bb36f-119">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="bb36f-120">例如: </span><span class="sxs-lookup"><span data-stu-id="bb36f-120">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="bb36f-121">備註</span><span class="sxs-lookup"><span data-stu-id="bb36f-121">Remarks</span></span>  
 <span data-ttu-id="bb36f-122">如果有任一個`number1`或`number2`是浮點數的值，會傳回浮點除法的餘數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-122">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="bb36f-123">結果的資料類型是最小的資料型別，可以產生除法運算的資料類型的所有可能值`number1`和`number2`。</span><span class="sxs-lookup"><span data-stu-id="bb36f-123">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="bb36f-124">如果`number1`或`number2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。</span><span class="sxs-lookup"><span data-stu-id="bb36f-124">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="bb36f-125">相關的運算子包括：</span><span class="sxs-lookup"><span data-stu-id="bb36f-125">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="bb36f-126">[\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回除法的整數商數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-126">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="bb36f-127">例如，運算式`14 \ 4`評估結果為 3。</span><span class="sxs-lookup"><span data-stu-id="bb36f-127">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="bb36f-128">[/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整的商數，包括其餘部分，做為浮點數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-128">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="bb36f-129">例如，運算式`14 / 4`會評估為 3.5。</span><span class="sxs-lookup"><span data-stu-id="bb36f-129">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="bb36f-130">嘗試的除以零</span><span class="sxs-lookup"><span data-stu-id="bb36f-130">Attempted division by zero</span></span>  
 <span data-ttu-id="bb36f-131">如果`number2`評估為零，行為`Mod`運算子的運算元資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="bb36f-131">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="bb36f-132">發生整數除以擲回<xref:System.DivideByZeroException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bb36f-132">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="bb36f-133">傳回浮點除法<xref:System.Double.NaN>。</span><span class="sxs-lookup"><span data-stu-id="bb36f-133">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="bb36f-134">對等的公式</span><span class="sxs-lookup"><span data-stu-id="bb36f-134">Equivalent formula</span></span>  
 <span data-ttu-id="bb36f-135">運算式`a Mod b`相當於下列公式：</span><span class="sxs-lookup"><span data-stu-id="bb36f-135">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="bb36f-136">浮點不精確而受到</span><span class="sxs-lookup"><span data-stu-id="bb36f-136">Floating-point imprecision</span></span>  
 <span data-ttu-id="bb36f-137">當您使用浮點數時，請記得它們在記憶體中不一定有的精確的十進位表示法。</span><span class="sxs-lookup"><span data-stu-id="bb36f-137">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="bb36f-138">這可能會導致非預期的結果從某些作業，例如值比較而`Mod`運算子。</span><span class="sxs-lookup"><span data-stu-id="bb36f-138">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="bb36f-139">如需詳細資訊，請參閱[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bb36f-139">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bb36f-140">多載化</span><span class="sxs-lookup"><span data-stu-id="bb36f-140">Overloading</span></span>  
 <span data-ttu-id="bb36f-141">`Mod`運算子可以是*多載*，這表示類別或結構可以重新定義它的行為。</span><span class="sxs-lookup"><span data-stu-id="bb36f-141">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="bb36f-142">如果您的程式碼適用於`Mod`至類別或結構，其中包含這類多載，這個執行個體，請務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="bb36f-142">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bb36f-143">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="bb36f-143">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb36f-144">範例</span><span class="sxs-lookup"><span data-stu-id="bb36f-144">Example</span></span>  
 <span data-ttu-id="bb36f-145">下列範例會使用`Mod`運算子將兩數相除並只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-145">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="bb36f-146">如果任一個數字是浮點數，結果會是代表餘數的浮點數。</span><span class="sxs-lookup"><span data-stu-id="bb36f-146">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="bb36f-147">範例</span><span class="sxs-lookup"><span data-stu-id="bb36f-147">Example</span></span>  
 <span data-ttu-id="bb36f-148">下列範例示範可能會不精確而受到浮點數運算元。</span><span class="sxs-lookup"><span data-stu-id="bb36f-148">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="bb36f-149">在第一個陳述式中，運算元都是`Double`，而且 0.2 無限重複的二進位小數 0.20000000000000001 預存值。</span><span class="sxs-lookup"><span data-stu-id="bb36f-149">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="bb36f-150">在第二個陳述式中，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確地表示法。</span><span class="sxs-lookup"><span data-stu-id="bb36f-150">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bb36f-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb36f-151">See also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="bb36f-152">算術運算子</span><span class="sxs-lookup"><span data-stu-id="bb36f-152">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="bb36f-153">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="bb36f-153">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="bb36f-154">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="bb36f-154">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="bb36f-155">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="bb36f-155">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="bb36f-156">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="bb36f-156">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="bb36f-157">\ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb36f-157">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
