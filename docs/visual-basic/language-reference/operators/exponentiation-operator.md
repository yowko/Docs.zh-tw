---
title: ^ 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="52488-102">^ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52488-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="52488-103">數目自乘至另一個數字乘冪。</span><span class="sxs-lookup"><span data-stu-id="52488-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52488-104">語法</span><span class="sxs-lookup"><span data-stu-id="52488-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="52488-105">組件</span><span class="sxs-lookup"><span data-stu-id="52488-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="52488-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="52488-106">Required.</span></span> <span data-ttu-id="52488-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="52488-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="52488-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="52488-108">Required.</span></span> <span data-ttu-id="52488-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="52488-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="52488-110">結果</span><span class="sxs-lookup"><span data-stu-id="52488-110">Result</span></span>  
 <span data-ttu-id="52488-111">結果是`number`乘冪`exponent`，一律為`Double`值。</span><span class="sxs-lookup"><span data-stu-id="52488-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="52488-112">支援的型別</span><span class="sxs-lookup"><span data-stu-id="52488-112">Supported Types</span></span>  
 <span data-ttu-id="52488-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="52488-113">`Double`.</span></span> <span data-ttu-id="52488-114">任何其他類型的運算元都轉換成`Double`。</span><span class="sxs-lookup"><span data-stu-id="52488-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52488-115">備註</span><span class="sxs-lookup"><span data-stu-id="52488-115">Remarks</span></span>  
 <span data-ttu-id="52488-116">Visual Basic 一律會執行中的乘冪[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="52488-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="52488-117">值`exponent`可以是分數，負數，或兩者。</span><span class="sxs-lookup"><span data-stu-id="52488-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="52488-118">在單一運算式中，執行一個以上的乘冪時`^`運算子時發現從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="52488-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52488-119">`^`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="52488-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="52488-120">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="52488-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="52488-121">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="52488-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52488-122">範例</span><span class="sxs-lookup"><span data-stu-id="52488-122">Example</span></span>  
 <span data-ttu-id="52488-123">下列範例會使用`^`運算子引發的數字的指數乘冪。</span><span class="sxs-lookup"><span data-stu-id="52488-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="52488-124">結果會是第一個運算元的乘冪的第二個。</span><span class="sxs-lookup"><span data-stu-id="52488-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="52488-125">上述範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="52488-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="52488-126">`exp1`設為 4 (平方 2)。</span><span class="sxs-lookup"><span data-stu-id="52488-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="52488-127">`exp2`設定為 19683 (3 立方，然後該值立方)。</span><span class="sxs-lookup"><span data-stu-id="52488-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="52488-128">`exp3`設定為-125 (立方-5)。</span><span class="sxs-lookup"><span data-stu-id="52488-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="52488-129">`exp4`設定為 625 (第四個的乘冪-5)。</span><span class="sxs-lookup"><span data-stu-id="52488-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="52488-130">`exp5`設定為 2 （8 個的立方根）。</span><span class="sxs-lookup"><span data-stu-id="52488-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="52488-131">`exp6`設定為 0.5 (除以 8 的立方根 1.0)。</span><span class="sxs-lookup"><span data-stu-id="52488-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="52488-132">請注意在上述範例中的運算式中的括弧的重要性。</span><span class="sxs-lookup"><span data-stu-id="52488-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="52488-133">因為*運算子優先順序*，通常會先執行 Visual Basic`^`運算子，再執行其他的即使是一元`–`運算子。</span><span class="sxs-lookup"><span data-stu-id="52488-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="52488-134">如果`exp4`和`exp6`已計算沒有括號，則可能產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="52488-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="52488-135">`exp4 = -5 ^ 4`會計算為 (第四個的乘冪 5)，這會導致-625。</span><span class="sxs-lookup"><span data-stu-id="52488-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="52488-136">`exp6 = 8 ^ -1.0 / 3.0`將計算成 (8 – 1 乘冪或 0.125) 除以可得到 0.041666666666666666666666666666667 3.0。</span><span class="sxs-lookup"><span data-stu-id="52488-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52488-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52488-137">See Also</span></span>  
 [<span data-ttu-id="52488-138">^= 運算子</span><span class="sxs-lookup"><span data-stu-id="52488-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="52488-139">算術運算子</span><span class="sxs-lookup"><span data-stu-id="52488-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="52488-140">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="52488-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="52488-141">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="52488-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="52488-142">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="52488-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
