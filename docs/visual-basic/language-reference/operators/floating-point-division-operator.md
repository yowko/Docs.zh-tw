---
title: "/ 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 82255339c3bdab7f6e760de9bef073f463260877
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="eb390-102">/ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb390-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="eb390-103">將兩個數值相除，傳回浮點結果。</span><span class="sxs-lookup"><span data-stu-id="eb390-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb390-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb390-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="eb390-105">組件</span><span class="sxs-lookup"><span data-stu-id="eb390-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="eb390-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="eb390-106">Required.</span></span> <span data-ttu-id="eb390-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="eb390-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="eb390-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="eb390-108">Required.</span></span> <span data-ttu-id="eb390-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="eb390-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="eb390-110">支援的型別</span><span class="sxs-lookup"><span data-stu-id="eb390-110">Supported Types</span></span>  
 <span data-ttu-id="eb390-111">所有的數字類型，包括不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="eb390-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="eb390-112">結果</span><span class="sxs-lookup"><span data-stu-id="eb390-112">Result</span></span>  
 <span data-ttu-id="eb390-113">結果是完整的商數`expression1`除以`expression2`，包括任何其餘部分。</span><span class="sxs-lookup"><span data-stu-id="eb390-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="eb390-114">[\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回整數商數，這會卸除其餘部分。</span><span class="sxs-lookup"><span data-stu-id="eb390-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb390-115">備註</span><span class="sxs-lookup"><span data-stu-id="eb390-115">Remarks</span></span>  
 <span data-ttu-id="eb390-116">結果的資料類型取決於運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="eb390-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="eb390-117">下表顯示如何決定結果的資料型別。</span><span class="sxs-lookup"><span data-stu-id="eb390-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="eb390-118">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="eb390-118">Operand data types</span></span>|<span data-ttu-id="eb390-119">結果資料類型</span><span class="sxs-lookup"><span data-stu-id="eb390-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="eb390-120">這兩個運算式都是整數類資料類型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)， [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="eb390-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="eb390-121">一個運算式[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)資料類型和其他不是[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="eb390-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="eb390-122">一個運算式[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)資料類型和其他不是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="eb390-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="eb390-123">任何一個運算式[雙](../../../visual-basic/language-reference/data-types/double-data-type.md)資料類型</span><span class="sxs-lookup"><span data-stu-id="eb390-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="eb390-124">任何整數的數值運算式執行除法之前，會擴展為`Double`。</span><span class="sxs-lookup"><span data-stu-id="eb390-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="eb390-125">如果結果為整數類資料型別時，Visual Basic 會嘗試將轉換的結果`Double`為該型別。</span><span class="sxs-lookup"><span data-stu-id="eb390-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="eb390-126">如果結果不符合該類型，這可以擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eb390-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="eb390-127">這個說明網頁，特別是，請參閱 」 嘗試以零為除數 」。</span><span class="sxs-lookup"><span data-stu-id="eb390-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="eb390-128">如果`expression1`或`expression2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。</span><span class="sxs-lookup"><span data-stu-id="eb390-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="eb390-129">嘗試的除以零</span><span class="sxs-lookup"><span data-stu-id="eb390-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="eb390-130">如果`expression2`判斷值為零，`/`運算子具有不同行為不同的運算元資料類型。</span><span class="sxs-lookup"><span data-stu-id="eb390-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="eb390-131">下表顯示可能的行為。</span><span class="sxs-lookup"><span data-stu-id="eb390-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="eb390-132">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="eb390-132">Operand data types</span></span>|<span data-ttu-id="eb390-133">行為如果`expression2`為零</span><span class="sxs-lookup"><span data-stu-id="eb390-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="eb390-134">浮點數 (`Single`或`Double`)</span><span class="sxs-lookup"><span data-stu-id="eb390-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="eb390-135">傳回無限大 (<xref:System.Double.PositiveInfinity>或<xref:System.Double.NegativeInfinity>)，或<xref:System.Double.NaN>（不是數字） 如果`expression1`也是零</xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity></span><span class="sxs-lookup"><span data-stu-id="eb390-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="eb390-136">擲回<xref:System.DivideByZeroException></xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="eb390-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="eb390-137">整數 （帶正負號或不帶正負號）</span><span class="sxs-lookup"><span data-stu-id="eb390-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="eb390-138">嘗試轉換回整數類資料類型會擲回<xref:System.OverflowException>無法接受整數類資料類型，所以<xref:System.Double.PositiveInfinity>， <xref:System.Double.NegativeInfinity>，或<xref:System.Double.NaN></xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity></xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="eb390-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="eb390-139">`/`運算子可以*多載*，也就是說，類別或結構可以重新定義它的行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="eb390-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="eb390-140">如果您的程式碼會使用此運算子在這種類別或結構，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="eb390-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="eb390-141">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="eb390-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb390-142">範例</span><span class="sxs-lookup"><span data-stu-id="eb390-142">Example</span></span>  
 <span data-ttu-id="eb390-143">這個範例會使用`/`來執行浮點除法運算子。</span><span class="sxs-lookup"><span data-stu-id="eb390-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="eb390-144">結果是兩個運算元的商。</span><span class="sxs-lookup"><span data-stu-id="eb390-144">The result is the quotient of the two operands.</span></span>  
  
 <span data-ttu-id="eb390-145">[!code-vb[VbVbalrOperators #&16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="eb390-145">[!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="eb390-146">在上述範例中的運算式會傳回 2.5 和 3.333333 的值。</span><span class="sxs-lookup"><span data-stu-id="eb390-146">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="eb390-147">請注意結果一定是浮點 (`Double`)，即使這兩個運算元都是整數常數。</span><span class="sxs-lookup"><span data-stu-id="eb390-147">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb390-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb390-148">See Also</span></span>  
 <span data-ttu-id="eb390-149">[/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="eb390-149">[/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span></span>  
<span data-ttu-id="eb390-150"> [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="eb390-150"> [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span></span>  
<span data-ttu-id="eb390-151"> [運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span><span class="sxs-lookup"><span data-stu-id="eb390-151"> [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span></span>  
<span data-ttu-id="eb390-152"> [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="eb390-152"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="eb390-153"> [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="eb390-153"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="eb390-154"> [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="eb390-154"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="eb390-155"> [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="eb390-155"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

