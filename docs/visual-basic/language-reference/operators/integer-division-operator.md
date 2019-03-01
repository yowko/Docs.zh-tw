---
title: '\ 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 7ce7bdaa2bcbf2ba67f24c7e129f8f9a03a28c52
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201907"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9ecf2-102">\ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ecf2-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="9ecf2-103">兩數相除並傳回整數結果。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ecf2-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ecf2-104">Syntax</span></span>  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9ecf2-105">組件</span><span class="sxs-lookup"><span data-stu-id="9ecf2-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="9ecf2-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-106">Required.</span></span> <span data-ttu-id="9ecf2-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9ecf2-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-108">Required.</span></span> <span data-ttu-id="9ecf2-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="9ecf2-110">支援的型別</span><span class="sxs-lookup"><span data-stu-id="9ecf2-110">Supported Types</span></span>  
 <span data-ttu-id="9ecf2-111">所有的數字類型，包括不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="9ecf2-112">結果</span><span class="sxs-lookup"><span data-stu-id="9ecf2-112">Result</span></span>  
 <span data-ttu-id="9ecf2-113">結果是整數商數`expression1`除以`expression2`，它會捨棄任何餘數，並保留只有整數部分。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="9ecf2-114">這就所謂*截斷*。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="9ecf2-115">將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9ecf2-116">請參閱中的 「 整數算術 」 表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="9ecf2-117">[/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整商數，仍會保留其餘部分中的小數部分。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ecf2-118">備註</span><span class="sxs-lookup"><span data-stu-id="9ecf2-118">Remarks</span></span>  
 <span data-ttu-id="9ecf2-119">然後再執行除法運算，Visual Basic 會嘗試轉換到任何浮點數值運算式`Long`。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="9ecf2-120">如果`Option Strict`是`On`，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="9ecf2-121">如果`Option Strict`是`Off`，則<xref:System.OverflowException>如果值超出範圍，就可能[Long 資料型別](../../../visual-basic/language-reference/data-types/long-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="9ecf2-122">轉換成`Long`也受限於*銀行進位*。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="9ecf2-123">如需詳細資訊，請參閱 「 小數點後的組件 」 中[類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="9ecf2-124">如果`expression1`或是`expression2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="9ecf2-125">嘗試的除以零</span><span class="sxs-lookup"><span data-stu-id="9ecf2-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="9ecf2-126">如果`expression2`評估為零，`\`運算子則會擲回<xref:System.DivideByZeroException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="9ecf2-127">這是所有的數值資料類型的運算元，則為 true。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ecf2-128">`\`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9ecf2-129">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9ecf2-130">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ecf2-131">範例</span><span class="sxs-lookup"><span data-stu-id="9ecf2-131">Example</span></span>  
 <span data-ttu-id="9ecf2-132">下列範例會使用`\`執行整數除法運算子。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="9ecf2-133">結果是一個整數，表示兩個運算元的整數商數，捨棄餘數。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="9ecf2-134">在上述範例中的運算式會分別傳回值 2、 3、 33 與-22。</span><span class="sxs-lookup"><span data-stu-id="9ecf2-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecf2-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecf2-135">See also</span></span>
- [<span data-ttu-id="9ecf2-136">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="9ecf2-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="9ecf2-137">/ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ecf2-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="9ecf2-138">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ecf2-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="9ecf2-139">算術運算子</span><span class="sxs-lookup"><span data-stu-id="9ecf2-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="9ecf2-140">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="9ecf2-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9ecf2-141">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="9ecf2-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9ecf2-142">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="9ecf2-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
