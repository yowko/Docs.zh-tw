---
title: 布林運算式
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 1000ec6e4b35d0cb2c6232b50f9a9551cb0dfdcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350816"
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="f4756-102">布林運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4756-102">Boolean Expressions (Visual Basic)</span></span>
<span data-ttu-id="f4756-103">*布林運算式*是評估為[布林資料類型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)值的運算式： `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="f4756-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="f4756-104">`Boolean` 運算式可以採用數種形式。</span><span class="sxs-lookup"><span data-stu-id="f4756-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="f4756-105">最簡單的方式是將 `Boolean` 變數的值直接比較成 `Boolean` 常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f4756-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="f4756-106">= 運算子的兩個意義</span><span class="sxs-lookup"><span data-stu-id="f4756-106">Two Meanings of the = Operator</span></span>  
 <span data-ttu-id="f4756-107">請注意，指派語句 `newCustomer = True` 看起來與上述範例中的運算式相同，但它會執行不同的函式，並以不同的方式使用。</span><span class="sxs-lookup"><span data-stu-id="f4756-107">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="f4756-108">在上述範例中，運算式 `newCustomer = True` 代表布林值，而 `=` 符號則會解讀為比較運算子。</span><span class="sxs-lookup"><span data-stu-id="f4756-108">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="f4756-109">在獨立語句中，`=` 符號會被視為指派運算子，並將右邊的值指派給左邊的變數。</span><span class="sxs-lookup"><span data-stu-id="f4756-109">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="f4756-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f4756-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 <span data-ttu-id="f4756-111">如需進一步資訊，請參閱[值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)和[語句](../../../../visual-basic/language-reference/statements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f4756-111">For further information, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) and [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="f4756-112">比較運算子</span><span class="sxs-lookup"><span data-stu-id="f4756-112">Comparison Operators</span></span>  
 <span data-ttu-id="f4756-113">比較運算子（例如 `=`、`<`、`>`、`<>`、`<=`和 `>=`）會比較運算子左邊的運算式與運算子右邊的運算式，並將結果評估為 `True` 或 `False`，藉此產生布林運算式。</span><span class="sxs-lookup"><span data-stu-id="f4756-113">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="f4756-114">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f4756-114">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="f4756-115">因為42小於81，所以上述範例中的布林運算式會評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="f4756-115">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="f4756-116">如需這類運算式的詳細資訊，請參閱[值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)。</span><span class="sxs-lookup"><span data-stu-id="f4756-116">For more information on this kind of expression, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="f4756-117">與邏輯運算子結合的比較運算子</span><span class="sxs-lookup"><span data-stu-id="f4756-117">Comparison Operators Combined with Logical Operators</span></span>  
 <span data-ttu-id="f4756-118">比較運算式可以使用邏輯運算子結合，以產生更複雜的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="f4756-118">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="f4756-119">下列範例示範如何搭配使用比較運算子與邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="f4756-119">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="f4756-120">在上述範例中，整體運算式的值取決於 `And` 運算子的每一端上的運算式值。</span><span class="sxs-lookup"><span data-stu-id="f4756-120">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="f4756-121">如果兩個運算式都 `True`，則整體運算式會評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="f4756-121">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="f4756-122">如果 `False`任一運算式，則整個運算式會評估為 `False`。</span><span class="sxs-lookup"><span data-stu-id="f4756-122">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="f4756-123">短路運算子</span><span class="sxs-lookup"><span data-stu-id="f4756-123">Short-Circuiting Operators</span></span>  
 <span data-ttu-id="f4756-124">邏輯運算子 `AndAlso` 和 `OrElse` 展示稱為「最少運算 *」的行為。*</span><span class="sxs-lookup"><span data-stu-id="f4756-124">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="f4756-125">「短路」運算子會先評估左運算元。</span><span class="sxs-lookup"><span data-stu-id="f4756-125">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="f4756-126">如果左運算元決定整個運算式的值，則會繼續執行程式，而不會評估右運算式。</span><span class="sxs-lookup"><span data-stu-id="f4756-126">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="f4756-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f4756-127">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 <span data-ttu-id="f4756-128">在上述範例中，運算子會評估左邊的運算式，`45 < 12`。</span><span class="sxs-lookup"><span data-stu-id="f4756-128">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="f4756-129">因為左邊運算式會評估為 `False`，所以整個邏輯運算式必須評估為 `False`。</span><span class="sxs-lookup"><span data-stu-id="f4756-129">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="f4756-130">因此，程式執行會略過在 `If` 區塊內執行程式碼，而不會評估右運算式，`testFunction(3)`。</span><span class="sxs-lookup"><span data-stu-id="f4756-130">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="f4756-131">這個範例不會呼叫 `testFunction()`，因為左邊的運算式會 falsifies 整個運算式。</span><span class="sxs-lookup"><span data-stu-id="f4756-131">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="f4756-132">同樣地，如果使用 `OrElse` 的邏輯運算式中的左運算式評估為 `True`，則執行會繼續到下一行程式碼，而不會評估右運算式，因為左運算式已經驗證整個運算式。</span><span class="sxs-lookup"><span data-stu-id="f4756-132">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="f4756-133">與非短路運算子的比較</span><span class="sxs-lookup"><span data-stu-id="f4756-133">Comparison with Non-Short-Circuiting Operators</span></span>  
 <span data-ttu-id="f4756-134">相反地，當使用邏輯運算子 `And` 和 `Or` 時，就會評估邏輯運算子的兩端。</span><span class="sxs-lookup"><span data-stu-id="f4756-134">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="f4756-135">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f4756-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 <span data-ttu-id="f4756-136">先前的範例會呼叫 `testFunction()`，即使左運算式評估為 `False`也一樣。</span><span class="sxs-lookup"><span data-stu-id="f4756-136">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="f4756-137">括號運算式</span><span class="sxs-lookup"><span data-stu-id="f4756-137">Parenthetical Expressions</span></span>  
 <span data-ttu-id="f4756-138">您可以使用括弧來控制布林運算式的評估順序。</span><span class="sxs-lookup"><span data-stu-id="f4756-138">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="f4756-139">以括弧括住的運算式會先評估。</span><span class="sxs-lookup"><span data-stu-id="f4756-139">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="f4756-140">針對多個嵌套層級，優先順序會授與最深的嵌套運算式。</span><span class="sxs-lookup"><span data-stu-id="f4756-140">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="f4756-141">在括弧內，評估會根據運算子優先順序的規則繼續進行。</span><span class="sxs-lookup"><span data-stu-id="f4756-141">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="f4756-142">如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="f4756-142">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4756-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4756-143">See also</span></span>

- [<span data-ttu-id="f4756-144">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="f4756-144">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="f4756-145">數值比較</span><span class="sxs-lookup"><span data-stu-id="f4756-145">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="f4756-146">陳述式</span><span class="sxs-lookup"><span data-stu-id="f4756-146">Statements</span></span>](../../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="f4756-147">比較運算子</span><span class="sxs-lookup"><span data-stu-id="f4756-147">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="f4756-148">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="f4756-148">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="f4756-149">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="f4756-149">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f4756-150">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="f4756-150">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
