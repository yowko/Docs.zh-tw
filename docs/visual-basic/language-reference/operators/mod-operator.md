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
ms.openlocfilehash: dc1e866836bb7420ffe17210b5be7a5e1d4048d0
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374495"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="33e20-102">Mod 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="33e20-102">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="33e20-103">將兩個數字相除，然後只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="33e20-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="33e20-104">語法</span><span class="sxs-lookup"><span data-stu-id="33e20-104">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="33e20-105">組件</span><span class="sxs-lookup"><span data-stu-id="33e20-105">Parts</span></span>

`result` \
<span data-ttu-id="33e20-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="33e20-106">Required.</span></span> <span data-ttu-id="33e20-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="33e20-107">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="33e20-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="33e20-108">Required.</span></span> <span data-ttu-id="33e20-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="33e20-109">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="33e20-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="33e20-110">Required.</span></span> <span data-ttu-id="33e20-111">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="33e20-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="33e20-112">支援的類型</span><span class="sxs-lookup"><span data-stu-id="33e20-112">Supported types</span></span>

<span data-ttu-id="33e20-113">所有數值類型。</span><span class="sxs-lookup"><span data-stu-id="33e20-113">All numeric types.</span></span> <span data-ttu-id="33e20-114">這包括不帶正負號的和浮點類型`Decimal`，以及。</span><span class="sxs-lookup"><span data-stu-id="33e20-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="33e20-115">結果</span><span class="sxs-lookup"><span data-stu-id="33e20-115">Result</span></span>

<span data-ttu-id="33e20-116">結果是`number1` `number2`除以之後的餘數。</span><span class="sxs-lookup"><span data-stu-id="33e20-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="33e20-117">例如，運算式`14 Mod 4`會評估為2。</span><span class="sxs-lookup"><span data-stu-id="33e20-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="33e20-118">在數學中，*餘數*與*模數*之間會有不同的結果，而負數的結果則有所不同。</span><span class="sxs-lookup"><span data-stu-id="33e20-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="33e20-119">Visual Basic `Mod` 、.NET Framework `op_Modulus`運算子和基礎[rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 指令中的運算子都會執行餘數運算。</span><span class="sxs-lookup"><span data-stu-id="33e20-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="33e20-120">作業的結果`Mod`會保留被除數、 `number1`和的正負號，因此它可以是正數或負數。</span><span class="sxs-lookup"><span data-stu-id="33e20-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="33e20-121">結果一律在範圍（-`number2`、 `number2`）、獨佔。</span><span class="sxs-lookup"><span data-stu-id="33e20-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="33e20-122">例如：</span><span class="sxs-lookup"><span data-stu-id="33e20-122">For example:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="33e20-123">備註</span><span class="sxs-lookup"><span data-stu-id="33e20-123">Remarks</span></span>

<span data-ttu-id="33e20-124">`number1`如果或`number2`是浮點值，則會傳回除法的浮點餘數。</span><span class="sxs-lookup"><span data-stu-id="33e20-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="33e20-125">結果的資料類型是最小的資料類型，可以保存與`number1`和`number2`資料類型相除所產生的所有可能值。</span><span class="sxs-lookup"><span data-stu-id="33e20-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="33e20-126">如果`number1` 或`number2`評估為[沒有任何](../../../visual-basic/language-reference/nothing.md)值，則會將它視為零。</span><span class="sxs-lookup"><span data-stu-id="33e20-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="33e20-127">相關的運算子包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="33e20-127">Related operators include the following:</span></span>

- <span data-ttu-id="33e20-128">[\ 運算子（Visual Basic）](../../../visual-basic/language-reference/operators/integer-division-operator.md)會傳回除法的整數商。</span><span class="sxs-lookup"><span data-stu-id="33e20-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="33e20-129">例如，運算式`14 \ 4`會評估為3。</span><span class="sxs-lookup"><span data-stu-id="33e20-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="33e20-130">[/運算子（Visual Basic）](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)會傳回完整的商，包括餘數，做為浮點數。</span><span class="sxs-lookup"><span data-stu-id="33e20-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="33e20-131">例如，運算式`14 / 4`會評估為3.5。</span><span class="sxs-lookup"><span data-stu-id="33e20-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="33e20-132">嘗試除數為零</span><span class="sxs-lookup"><span data-stu-id="33e20-132">Attempted division by zero</span></span>

<span data-ttu-id="33e20-133">如果`number2`評估為零，則`Mod`運算子的行為取決於運算元的資料類型：</span><span class="sxs-lookup"><span data-stu-id="33e20-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>
- <span data-ttu-id="33e20-134">如果<xref:System.DivideByZeroException> `BC30542 Division by zero occurred while evaluating this expression` `number2`無法在編譯時期判斷，則整數除法會擲回例外狀況，如果在編譯時期評估為零，則會產生編譯時期錯誤。 `number2`</span><span class="sxs-lookup"><span data-stu-id="33e20-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="33e20-135">浮點除法<xref:System.Double.NaN?displayProperty=nameWithType>會傳回。</span><span class="sxs-lookup"><span data-stu-id="33e20-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="33e20-136">對等公式</span><span class="sxs-lookup"><span data-stu-id="33e20-136">Equivalent formula</span></span>

<span data-ttu-id="33e20-137">運算式`a Mod b`相當於下列其中一個公式：</span><span class="sxs-lookup"><span data-stu-id="33e20-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="33e20-138">浮點不精確</span><span class="sxs-lookup"><span data-stu-id="33e20-138">Floating-point imprecision</span></span>

<span data-ttu-id="33e20-139">當您使用浮點數時，請記住，記憶體中不一定有精確的十進位標記法。</span><span class="sxs-lookup"><span data-stu-id="33e20-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="33e20-140">這可能會導致某些作業產生非預期的結果，例如值比較和`Mod`運算子。</span><span class="sxs-lookup"><span data-stu-id="33e20-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="33e20-141">如需詳細資訊，請參閱針對[資料類型進行疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="33e20-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="33e20-142">多載化</span><span class="sxs-lookup"><span data-stu-id="33e20-142">Overloading</span></span>

<span data-ttu-id="33e20-143">運算子可以多載 *，這*表示類別或結構可以重新定義其行為。 `Mod`</span><span class="sxs-lookup"><span data-stu-id="33e20-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="33e20-144">如果您的程式`Mod`代碼適用于包含這類多載的類別或結構實例，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="33e20-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="33e20-145">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="33e20-145">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="33e20-146">範例</span><span class="sxs-lookup"><span data-stu-id="33e20-146">Example</span></span>

<span data-ttu-id="33e20-147">下列範例會使用`Mod`運算子來將兩個數字相除，然後只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="33e20-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="33e20-148">如果任一個數位是浮點數，則結果會是代表餘數的浮點數。</span><span class="sxs-lookup"><span data-stu-id="33e20-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="33e20-149">範例</span><span class="sxs-lookup"><span data-stu-id="33e20-149">Example</span></span>

<span data-ttu-id="33e20-150">下列範例示範浮點運算元的潛在不精確。</span><span class="sxs-lookup"><span data-stu-id="33e20-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="33e20-151">在第一個語句中，運算元是`Double`，而0.2 是具有儲存值0.20000000000000001 的無限重複二進位分數。</span><span class="sxs-lookup"><span data-stu-id="33e20-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="33e20-152">在第二個語句中，常值`D`類型字元會強制`Decimal`執行這兩個運算元，而0.2 具有精確的標記法。</span><span class="sxs-lookup"><span data-stu-id="33e20-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="33e20-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33e20-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="33e20-154">算術運算子</span><span class="sxs-lookup"><span data-stu-id="33e20-154">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="33e20-155">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="33e20-155">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="33e20-156">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="33e20-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="33e20-157">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="33e20-157">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="33e20-158">Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="33e20-158">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="33e20-159">\ 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="33e20-159">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
