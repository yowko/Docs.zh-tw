---
title: Mod 運算子 (Visual Basic)
ms.date: 04/24/2018
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
ms.openlocfilehash: b127c50f3319d4fe7c4890fc3bffb295baa37466
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936665"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="32bf6-102">Mod 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32bf6-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="32bf6-103">兩個數目相除，然後只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bf6-104">語法</span><span class="sxs-lookup"><span data-stu-id="32bf6-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="32bf6-105">組件</span><span class="sxs-lookup"><span data-stu-id="32bf6-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="32bf6-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="32bf6-106">Required.</span></span> <span data-ttu-id="32bf6-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="32bf6-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="32bf6-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="32bf6-108">Required.</span></span> <span data-ttu-id="32bf6-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="32bf6-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="32bf6-110">支援的類型</span><span class="sxs-lookup"><span data-stu-id="32bf6-110">Supported types</span></span>  
 <span data-ttu-id="32bf6-111">所有數值類型。</span><span class="sxs-lookup"><span data-stu-id="32bf6-111">All numeric types.</span></span> <span data-ttu-id="32bf6-112">這包括的不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="32bf6-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="32bf6-113">結果</span><span class="sxs-lookup"><span data-stu-id="32bf6-113">Result</span></span>

<span data-ttu-id="32bf6-114">結果就是後的餘數`number1`除以`number2`。</span><span class="sxs-lookup"><span data-stu-id="32bf6-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="32bf6-115">例如，運算式`14 Mod 4`評估結果為 2。</span><span class="sxs-lookup"><span data-stu-id="32bf6-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  

> [!NOTE]
> <span data-ttu-id="32bf6-116">之間的差異*餘數*並*模數*數學，使用不同的結果為負數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-116">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="32bf6-117">`Mod`運算子，在 Visual Basic 中，.NET Framework`op_Modulus`運算子，以及基礎[rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 指令的所有執行其餘作業。</span><span class="sxs-lookup"><span data-stu-id="32bf6-117">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="32bf6-118">結果`Mod`作業會保留被除數的正負號`number1`，因此它可能是正數或負數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-118">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="32bf6-119">結果一律是在範圍 (-`number2`， `number2`)、 獨佔。</span><span class="sxs-lookup"><span data-stu-id="32bf6-119">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="32bf6-120">例如: </span><span class="sxs-lookup"><span data-stu-id="32bf6-120">For example:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="32bf6-121">備註</span><span class="sxs-lookup"><span data-stu-id="32bf6-121">Remarks</span></span>  
 <span data-ttu-id="32bf6-122">如果有任一`number1`或`number2`是浮點數的值，則會傳回浮點除法的餘數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-122">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="32bf6-123">結果的資料類型是最小的資料類型，可保存所有可能的值所產生的資料類型的除法`number1`和`number2`。</span><span class="sxs-lookup"><span data-stu-id="32bf6-123">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="32bf6-124">如果`number1`或是`number2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。</span><span class="sxs-lookup"><span data-stu-id="32bf6-124">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="32bf6-125">相關的運算子包括：</span><span class="sxs-lookup"><span data-stu-id="32bf6-125">Related operators include the following:</span></span>  
  
- <span data-ttu-id="32bf6-126">[\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回除法的整數商數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-126">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="32bf6-127">例如，運算式`14 \ 4`評估結果為 3。</span><span class="sxs-lookup"><span data-stu-id="32bf6-127">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
- <span data-ttu-id="32bf6-128">[/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整商數，包括其餘部分，做為浮點數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-128">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="32bf6-129">例如，運算式`14 / 4`會評估為 3.5。</span><span class="sxs-lookup"><span data-stu-id="32bf6-129">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="32bf6-130">嘗試的除以零</span><span class="sxs-lookup"><span data-stu-id="32bf6-130">Attempted division by zero</span></span>  
 <span data-ttu-id="32bf6-131">如果`number2`評估為零，就會有的行為`Mod`運算子的運算元資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="32bf6-131">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="32bf6-132">整數的除法就會擲回<xref:System.DivideByZeroException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="32bf6-132">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="32bf6-133">傳回浮點除法<xref:System.Double.NaN>。</span><span class="sxs-lookup"><span data-stu-id="32bf6-133">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="32bf6-134">對等的公式</span><span class="sxs-lookup"><span data-stu-id="32bf6-134">Equivalent formula</span></span>  
 <span data-ttu-id="32bf6-135">運算式`a Mod b`相當於下列公式：</span><span class="sxs-lookup"><span data-stu-id="32bf6-135">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="32bf6-136">浮點數不精確</span><span class="sxs-lookup"><span data-stu-id="32bf6-136">Floating-point imprecision</span></span>  
 <span data-ttu-id="32bf6-137">當您使用浮點數時，請記得它們在記憶體中不一定有精確的十進位表示法。</span><span class="sxs-lookup"><span data-stu-id="32bf6-137">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="32bf6-138">這可能會導致非預期的結果從某些作業，例如要做數值比較，`Mod`運算子。</span><span class="sxs-lookup"><span data-stu-id="32bf6-138">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="32bf6-139">如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="32bf6-139">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="32bf6-140">多載化</span><span class="sxs-lookup"><span data-stu-id="32bf6-140">Overloading</span></span>  
 <span data-ttu-id="32bf6-141">`Mod`運算子只能*多載*，這表示類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="32bf6-141">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="32bf6-142">如果您的程式碼適用於`Mod`類別或結構，其中包含這類多載的執行個體，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="32bf6-142">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="32bf6-143">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="32bf6-143">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32bf6-144">範例</span><span class="sxs-lookup"><span data-stu-id="32bf6-144">Example</span></span>  
 <span data-ttu-id="32bf6-145">下列範例會使用`Mod`運算子將兩個數字，並只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-145">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="32bf6-146">如果任一個數字是浮點數，結果會是浮點數表示餘數。</span><span class="sxs-lookup"><span data-stu-id="32bf6-146">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="32bf6-147">範例</span><span class="sxs-lookup"><span data-stu-id="32bf6-147">Example</span></span>  
 <span data-ttu-id="32bf6-148">下列範例示範可能會不精確的浮點運算元。</span><span class="sxs-lookup"><span data-stu-id="32bf6-148">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="32bf6-149">第一個陳述式中，運算元都是`Double`，0.2，無限地重複的二進位分數 0.20000000000000001 預存值。</span><span class="sxs-lookup"><span data-stu-id="32bf6-149">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="32bf6-150">在第二個陳述式中，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確的表示法。</span><span class="sxs-lookup"><span data-stu-id="32bf6-150">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="32bf6-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32bf6-151">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="32bf6-152">算術運算子</span><span class="sxs-lookup"><span data-stu-id="32bf6-152">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="32bf6-153">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="32bf6-153">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="32bf6-154">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="32bf6-154">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="32bf6-155">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="32bf6-155">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="32bf6-156">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="32bf6-156">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="32bf6-157">\ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32bf6-157">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
