---
title: ^ 運算子 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 2fb52a57a9d96f93c31ab1419e81e7f05967f831
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659701"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="764e8-102">^ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="764e8-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="764e8-103">引發到另一個數字乘冪的數字。</span><span class="sxs-lookup"><span data-stu-id="764e8-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="764e8-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="764e8-105">組件</span><span class="sxs-lookup"><span data-stu-id="764e8-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="764e8-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="764e8-106">Required.</span></span> <span data-ttu-id="764e8-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="764e8-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="764e8-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="764e8-108">Required.</span></span> <span data-ttu-id="764e8-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="764e8-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="764e8-110">結果</span><span class="sxs-lookup"><span data-stu-id="764e8-110">Result</span></span>  
 <span data-ttu-id="764e8-111">結果是`number`的乘冪`exponent`，一律為`Double`值。</span><span class="sxs-lookup"><span data-stu-id="764e8-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="764e8-112">支援的型別</span><span class="sxs-lookup"><span data-stu-id="764e8-112">Supported Types</span></span>  
 <span data-ttu-id="764e8-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="764e8-113">`Double`.</span></span> <span data-ttu-id="764e8-114">任何不同類型的運算元會轉換成`Double`。</span><span class="sxs-lookup"><span data-stu-id="764e8-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="764e8-115">備註</span><span class="sxs-lookup"><span data-stu-id="764e8-115">Remarks</span></span>  
 <span data-ttu-id="764e8-116">Visual Basic 一律會執行中的乘冪[Double 資料型別](../../../visual-basic/language-reference/data-types/double-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="764e8-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="764e8-117">值`exponent`可以是小數、 負數，或兩者。</span><span class="sxs-lookup"><span data-stu-id="764e8-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="764e8-118">在單一運算式中，執行一個以上的乘冪時`^`時發現從左到右評估運算子。</span><span class="sxs-lookup"><span data-stu-id="764e8-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="764e8-119">`^`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="764e8-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="764e8-120">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="764e8-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="764e8-121">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="764e8-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="764e8-122">範例</span><span class="sxs-lookup"><span data-stu-id="764e8-122">Example</span></span>  
 <span data-ttu-id="764e8-123">下列範例會使用`^`運算子引發的指數乘冪數字。</span><span class="sxs-lookup"><span data-stu-id="764e8-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="764e8-124">結果會是第一個運算元具有乘冪數的第二個。</span><span class="sxs-lookup"><span data-stu-id="764e8-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="764e8-125">上述範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="764e8-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="764e8-126">`exp1` 設為 4 (平方 2)。</span><span class="sxs-lookup"><span data-stu-id="764e8-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="764e8-127">`exp2` 設定為 19683 (3 立方，然後該值立方)。</span><span class="sxs-lookup"><span data-stu-id="764e8-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="764e8-128">`exp3` 設定為-125 (-5 立方)。</span><span class="sxs-lookup"><span data-stu-id="764e8-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="764e8-129">`exp4` 設定為 625 (第四個的乘冪的-5)。</span><span class="sxs-lookup"><span data-stu-id="764e8-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="764e8-130">`exp5` 設定為 2 （8 個的立方根）。</span><span class="sxs-lookup"><span data-stu-id="764e8-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="764e8-131">`exp6` 設定為 0.5 (除以 8 的立方根 1.0)。</span><span class="sxs-lookup"><span data-stu-id="764e8-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="764e8-132">請注意在上述範例中的運算式中的括號的重要性。</span><span class="sxs-lookup"><span data-stu-id="764e8-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="764e8-133">由於*運算子優先順序*，通常會先執行 Visual Basic`^`運算子，再執行其他的甚至是一元`–`運算子。</span><span class="sxs-lookup"><span data-stu-id="764e8-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="764e8-134">如果`exp4`和`exp6`已計算沒有括號，則可能產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="764e8-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="764e8-135">`exp4 = -5 ^ 4` 會計算為 (第四個的乘冪 5)，這會導致-625。</span><span class="sxs-lookup"><span data-stu-id="764e8-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="764e8-136">`exp6 = 8 ^ -1.0 / 3.0` 會計算為 (-1 的電力或 0.125 8) 除以可得到 0.041666666666666666666666666666667 3.0。</span><span class="sxs-lookup"><span data-stu-id="764e8-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764e8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="764e8-137">See also</span></span>
- [<span data-ttu-id="764e8-138">^= 運算子</span><span class="sxs-lookup"><span data-stu-id="764e8-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="764e8-139">算術運算子</span><span class="sxs-lookup"><span data-stu-id="764e8-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="764e8-140">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="764e8-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="764e8-141">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="764e8-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="764e8-142">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="764e8-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
