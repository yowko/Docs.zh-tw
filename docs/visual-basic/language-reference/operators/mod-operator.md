---
title: Mod 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
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
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="0ca05-102">Mod 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca05-102">Mod Operator (Visual Basic)</span></span>
<span data-ttu-id="0ca05-103">兩數相除並只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="0ca05-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca05-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ca05-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="0ca05-105">組件</span><span class="sxs-lookup"><span data-stu-id="0ca05-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="0ca05-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="0ca05-106">Required.</span></span> <span data-ttu-id="0ca05-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="0ca05-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="0ca05-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0ca05-108">Required.</span></span> <span data-ttu-id="0ca05-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="0ca05-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="0ca05-110">支援的型別</span><span class="sxs-lookup"><span data-stu-id="0ca05-110">Supported Types</span></span>  
 <span data-ttu-id="0ca05-111">所有數字類型。</span><span class="sxs-lookup"><span data-stu-id="0ca05-111">All numeric types.</span></span> <span data-ttu-id="0ca05-112">這包括不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="0ca05-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="0ca05-113">結果</span><span class="sxs-lookup"><span data-stu-id="0ca05-113">Result</span></span>  
 <span data-ttu-id="0ca05-114">結果是後的餘數`number1`除以`number2`。</span><span class="sxs-lookup"><span data-stu-id="0ca05-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="0ca05-115">例如，運算式`14 Mod 4`評估為 2。</span><span class="sxs-lookup"><span data-stu-id="0ca05-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ca05-116">備註</span><span class="sxs-lookup"><span data-stu-id="0ca05-116">Remarks</span></span>  
 <span data-ttu-id="0ca05-117">如果有任一個`number1`或`number2`是浮點數的值，會傳回浮點除法的餘數。</span><span class="sxs-lookup"><span data-stu-id="0ca05-117">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="0ca05-118">結果的資料類型是最小的資料型別，可以產生除法運算的資料類型的所有可能值`number1`和`number2`。</span><span class="sxs-lookup"><span data-stu-id="0ca05-118">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="0ca05-119">如果`number1`或`number2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。</span><span class="sxs-lookup"><span data-stu-id="0ca05-119">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="0ca05-120">相關的運算子包括：</span><span class="sxs-lookup"><span data-stu-id="0ca05-120">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="0ca05-121">[\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回除法的整數商數。</span><span class="sxs-lookup"><span data-stu-id="0ca05-121">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="0ca05-122">例如，運算式`14 \ 4`評估結果為 3。</span><span class="sxs-lookup"><span data-stu-id="0ca05-122">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="0ca05-123">[/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整的商數，包括其餘部分，做為浮點數。</span><span class="sxs-lookup"><span data-stu-id="0ca05-123">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="0ca05-124">例如，運算式`14 / 4`會評估為 3.5。</span><span class="sxs-lookup"><span data-stu-id="0ca05-124">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="0ca05-125">嘗試的除以零</span><span class="sxs-lookup"><span data-stu-id="0ca05-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="0ca05-126">如果`number2`評估為零，行為`Mod`運算子的運算元資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="0ca05-126">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="0ca05-127">發生整數除以擲回<xref:System.DivideByZeroException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0ca05-127">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="0ca05-128">傳回浮點除法<xref:System.Double.NaN>。</span><span class="sxs-lookup"><span data-stu-id="0ca05-128">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="0ca05-129">對等的公式</span><span class="sxs-lookup"><span data-stu-id="0ca05-129">Equivalent Formula</span></span>  
 <span data-ttu-id="0ca05-130">運算式`a Mod b`相當於下列公式：</span><span class="sxs-lookup"><span data-stu-id="0ca05-130">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="0ca05-131">浮點不精確而受到</span><span class="sxs-lookup"><span data-stu-id="0ca05-131">Floating-Point Imprecision</span></span>  
 <span data-ttu-id="0ca05-132">當您使用浮點數時，請記得它們在記憶體中不一定有精確的表示。</span><span class="sxs-lookup"><span data-stu-id="0ca05-132">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="0ca05-133">這可能會導致非預期的結果從某些作業，例如值比較而`Mod`運算子。</span><span class="sxs-lookup"><span data-stu-id="0ca05-133">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="0ca05-134">如需詳細資訊，請參閱[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca05-134">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0ca05-135">多載化</span><span class="sxs-lookup"><span data-stu-id="0ca05-135">Overloading</span></span>  
 <span data-ttu-id="0ca05-136">`Mod`運算子可以是*多載*，這表示類別或結構可以重新定義它的行為。</span><span class="sxs-lookup"><span data-stu-id="0ca05-136">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="0ca05-137">如果您的程式碼適用於`Mod`至類別或結構，其中包含這類多載，這個執行個體，請務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="0ca05-137">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0ca05-138">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca05-138">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ca05-139">範例</span><span class="sxs-lookup"><span data-stu-id="0ca05-139">Example</span></span>  
 <span data-ttu-id="0ca05-140">下列範例會使用`Mod`運算子將兩數相除並只傳回餘數。</span><span class="sxs-lookup"><span data-stu-id="0ca05-140">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="0ca05-141">如果任一個數字是浮點數，結果會是代表餘數的浮點數。</span><span class="sxs-lookup"><span data-stu-id="0ca05-141">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="0ca05-142">範例</span><span class="sxs-lookup"><span data-stu-id="0ca05-142">Example</span></span>  
 <span data-ttu-id="0ca05-143">下列範例示範可能會不精確而受到浮點數運算元。</span><span class="sxs-lookup"><span data-stu-id="0ca05-143">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="0ca05-144">在第一個陳述式中，運算元都是`Double`，而且 0.2 無限重複的二進位小數 0.20000000000000001 預存值。</span><span class="sxs-lookup"><span data-stu-id="0ca05-144">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="0ca05-145">在第二個陳述式中，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確地表示法。</span><span class="sxs-lookup"><span data-stu-id="0ca05-145">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0ca05-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca05-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="0ca05-147">算術運算子</span><span class="sxs-lookup"><span data-stu-id="0ca05-147">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="0ca05-148">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="0ca05-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="0ca05-149">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="0ca05-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="0ca05-150">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="0ca05-150">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="0ca05-151">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="0ca05-151">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="0ca05-152">\ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca05-152">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
