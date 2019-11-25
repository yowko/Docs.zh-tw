---
title: + 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 12c14b3be0562a31470ddbd2d5489ccdbdf3b62b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350297"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8b15f-102">+ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b15f-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="8b15f-103">Adds two numbers or returns the positive value of a numeric expression.</span><span class="sxs-lookup"><span data-stu-id="8b15f-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="8b15f-104">Can also be used to concatenate two string expressions.</span><span class="sxs-lookup"><span data-stu-id="8b15f-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b15f-105">語法</span><span class="sxs-lookup"><span data-stu-id="8b15f-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="8b15f-106">或</span><span class="sxs-lookup"><span data-stu-id="8b15f-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="8b15f-107">組件</span><span class="sxs-lookup"><span data-stu-id="8b15f-107">Parts</span></span>  
  
|<span data-ttu-id="8b15f-108">詞彙</span><span class="sxs-lookup"><span data-stu-id="8b15f-108">Term</span></span>|<span data-ttu-id="8b15f-109">定義</span><span class="sxs-lookup"><span data-stu-id="8b15f-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="8b15f-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="8b15f-110">Required.</span></span> <span data-ttu-id="8b15f-111">Any numeric or string expression.</span><span class="sxs-lookup"><span data-stu-id="8b15f-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="8b15f-112">Required unless the `+` operator is calculating a negative value.</span><span class="sxs-lookup"><span data-stu-id="8b15f-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="8b15f-113">Any numeric or string expression.</span><span class="sxs-lookup"><span data-stu-id="8b15f-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="8b15f-114">結果</span><span class="sxs-lookup"><span data-stu-id="8b15f-114">Result</span></span>  
 <span data-ttu-id="8b15f-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span><span class="sxs-lookup"><span data-stu-id="8b15f-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="8b15f-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span><span class="sxs-lookup"><span data-stu-id="8b15f-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="8b15f-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span><span class="sxs-lookup"><span data-stu-id="8b15f-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="8b15f-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span><span class="sxs-lookup"><span data-stu-id="8b15f-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="8b15f-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8b15f-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="8b15f-120">For more information, see the tables in "Remarks."</span><span class="sxs-lookup"><span data-stu-id="8b15f-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="8b15f-121">支援的型別</span><span class="sxs-lookup"><span data-stu-id="8b15f-121">Supported Types</span></span>  
 <span data-ttu-id="8b15f-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span><span class="sxs-lookup"><span data-stu-id="8b15f-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b15f-123">備註</span><span class="sxs-lookup"><span data-stu-id="8b15f-123">Remarks</span></span>  
 <span data-ttu-id="8b15f-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span><span class="sxs-lookup"><span data-stu-id="8b15f-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="8b15f-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span><span class="sxs-lookup"><span data-stu-id="8b15f-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="8b15f-126">Data types of expressions</span><span class="sxs-lookup"><span data-stu-id="8b15f-126">Data types of expressions</span></span>|<span data-ttu-id="8b15f-127">Action by compiler</span><span class="sxs-lookup"><span data-stu-id="8b15f-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="8b15f-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span><span class="sxs-lookup"><span data-stu-id="8b15f-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="8b15f-129">Add.</span><span class="sxs-lookup"><span data-stu-id="8b15f-129">Add.</span></span> <span data-ttu-id="8b15f-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span><span class="sxs-lookup"><span data-stu-id="8b15f-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="8b15f-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="8b15f-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="8b15f-132">Both expressions are of type `String`</span><span class="sxs-lookup"><span data-stu-id="8b15f-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="8b15f-133">Concatenate.</span><span class="sxs-lookup"><span data-stu-id="8b15f-133">Concatenate.</span></span>|  
|<span data-ttu-id="8b15f-134">One expression is a numeric data type and the other is a string</span><span class="sxs-lookup"><span data-stu-id="8b15f-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="8b15f-135">If `Option Strict` is `On`, then generate a compiler error.</span><span class="sxs-lookup"><span data-stu-id="8b15f-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="8b15f-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span><span class="sxs-lookup"><span data-stu-id="8b15f-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="8b15f-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span><span class="sxs-lookup"><span data-stu-id="8b15f-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="8b15f-138">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="8b15f-138">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="8b15f-139">Add, with `Nothing` valued as zero.</span><span class="sxs-lookup"><span data-stu-id="8b15f-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="8b15f-140">One expression is a string, and the other is `Nothing`</span><span class="sxs-lookup"><span data-stu-id="8b15f-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="8b15f-141">Concatenate, with `Nothing` valued as "".</span><span class="sxs-lookup"><span data-stu-id="8b15f-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="8b15f-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span><span class="sxs-lookup"><span data-stu-id="8b15f-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="8b15f-143">Data types of expressions</span><span class="sxs-lookup"><span data-stu-id="8b15f-143">Data types of expressions</span></span>|<span data-ttu-id="8b15f-144">Action by compiler</span><span class="sxs-lookup"><span data-stu-id="8b15f-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="8b15f-145">`Object` expression holds a numeric value and the other is a numeric data type</span><span class="sxs-lookup"><span data-stu-id="8b15f-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="8b15f-146">If `Option Strict` is `On`, then generate a compiler error.</span><span class="sxs-lookup"><span data-stu-id="8b15f-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="8b15f-147">If `Option Strict` is `Off`, then add.</span><span class="sxs-lookup"><span data-stu-id="8b15f-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="8b15f-148">`Object` expression holds a numeric value and the other is of type `String`</span><span class="sxs-lookup"><span data-stu-id="8b15f-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="8b15f-149">If `Option Strict` is `On`, then generate a compiler error.</span><span class="sxs-lookup"><span data-stu-id="8b15f-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="8b15f-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span><span class="sxs-lookup"><span data-stu-id="8b15f-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="8b15f-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span><span class="sxs-lookup"><span data-stu-id="8b15f-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="8b15f-152">`Object` expression holds a string and the other is a numeric data type</span><span class="sxs-lookup"><span data-stu-id="8b15f-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="8b15f-153">If `Option Strict` is `On`, then generate a compiler error.</span><span class="sxs-lookup"><span data-stu-id="8b15f-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="8b15f-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span><span class="sxs-lookup"><span data-stu-id="8b15f-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="8b15f-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span><span class="sxs-lookup"><span data-stu-id="8b15f-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="8b15f-156">`Object` expression holds a string and the other is of type `String`</span><span class="sxs-lookup"><span data-stu-id="8b15f-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="8b15f-157">If `Option Strict` is `On`, then generate a compiler error.</span><span class="sxs-lookup"><span data-stu-id="8b15f-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="8b15f-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span><span class="sxs-lookup"><span data-stu-id="8b15f-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="8b15f-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span><span class="sxs-lookup"><span data-stu-id="8b15f-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="8b15f-160">Data types of expressions</span><span class="sxs-lookup"><span data-stu-id="8b15f-160">Data types of expressions</span></span>|<span data-ttu-id="8b15f-161">Action by compiler</span><span class="sxs-lookup"><span data-stu-id="8b15f-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="8b15f-162">Both `Object` expressions hold numeric values</span><span class="sxs-lookup"><span data-stu-id="8b15f-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="8b15f-163">Add.</span><span class="sxs-lookup"><span data-stu-id="8b15f-163">Add.</span></span>|  
|<span data-ttu-id="8b15f-164">Both `Object` expressions are of type `String`</span><span class="sxs-lookup"><span data-stu-id="8b15f-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="8b15f-165">Concatenate.</span><span class="sxs-lookup"><span data-stu-id="8b15f-165">Concatenate.</span></span>|  
|<span data-ttu-id="8b15f-166">One `Object` expression holds a numeric value and the other holds a string</span><span class="sxs-lookup"><span data-stu-id="8b15f-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="8b15f-167">Implicitly convert the string `Object` to `Double` and add.</span><span class="sxs-lookup"><span data-stu-id="8b15f-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="8b15f-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span><span class="sxs-lookup"><span data-stu-id="8b15f-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="8b15f-169">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span><span class="sxs-lookup"><span data-stu-id="8b15f-169">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b15f-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span><span class="sxs-lookup"><span data-stu-id="8b15f-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="8b15f-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span><span class="sxs-lookup"><span data-stu-id="8b15f-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8b15f-172">多載化</span><span class="sxs-lookup"><span data-stu-id="8b15f-172">Overloading</span></span>  
 <span data-ttu-id="8b15f-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="8b15f-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8b15f-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="8b15f-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8b15f-175">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="8b15f-175">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b15f-176">範例</span><span class="sxs-lookup"><span data-stu-id="8b15f-176">Example</span></span>  
 <span data-ttu-id="8b15f-177">The following example uses the `+` operator to add numbers.</span><span class="sxs-lookup"><span data-stu-id="8b15f-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="8b15f-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span><span class="sxs-lookup"><span data-stu-id="8b15f-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="8b15f-179">The arithmetic result represents the sum of the two operands.</span><span class="sxs-lookup"><span data-stu-id="8b15f-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="8b15f-180">You can also use the `+` operator to concatenate strings.</span><span class="sxs-lookup"><span data-stu-id="8b15f-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="8b15f-181">If the operands are both strings, Visual Basic concatenates them.</span><span class="sxs-lookup"><span data-stu-id="8b15f-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="8b15f-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span><span class="sxs-lookup"><span data-stu-id="8b15f-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="8b15f-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8b15f-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="8b15f-184">The following example illustrates the result when `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="8b15f-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="8b15f-185">The following example illustrates the result when `Option Strict` is `Off`.</span><span class="sxs-lookup"><span data-stu-id="8b15f-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="8b15f-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span><span class="sxs-lookup"><span data-stu-id="8b15f-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b15f-187">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b15f-187">See also</span></span>

- [<span data-ttu-id="8b15f-188">& 運算子</span><span class="sxs-lookup"><span data-stu-id="8b15f-188">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="8b15f-189">串連運算子</span><span class="sxs-lookup"><span data-stu-id="8b15f-189">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="8b15f-190">算術運算子</span><span class="sxs-lookup"><span data-stu-id="8b15f-190">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="8b15f-191">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="8b15f-191">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8b15f-192">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="8b15f-192">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8b15f-193">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b15f-193">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="8b15f-194">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="8b15f-194">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
