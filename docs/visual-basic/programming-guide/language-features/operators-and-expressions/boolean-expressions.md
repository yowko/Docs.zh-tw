---
title: "布林運算式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 48071c6833f9841fa42311dda59d6959c0645ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="f5c4a-102">布林運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5c4a-102">Boolean Expressions (Visual Basic)</span></span>
<span data-ttu-id="f5c4a-103">A*布林運算式*是評估為值的運算式[布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md):`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="f5c4a-104">`Boolean`運算式可以採用數種格式。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="f5c4a-105">最簡單的是直接比較值的`Boolean`變數設為`Boolean`常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="f5c4a-106">兩個意義的 = 運算子</span><span class="sxs-lookup"><span data-stu-id="f5c4a-106">Two Meanings of the = Operator</span></span>  
 <span data-ttu-id="f5c4a-107">請注意，指派陳述式`newCustomer = True`與相同的運算式，在上述範例中，但是它會執行不同的函式，並使用方式。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-107">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="f5c4a-108">在上述範例中，運算式`newCustomer = True`代表布林值，而`=`號會解譯為比較運算子。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-108">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="f5c4a-109">在獨立的陳述式，`=`符號會解譯為指派運算子和指派左邊變數 右邊的值。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-109">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="f5c4a-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 <span data-ttu-id="f5c4a-111">如需詳細資訊，請參閱[值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)和[陳述式](../../../../visual-basic/language-reference/statements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-111">For further information, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) and [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="f5c4a-112">比較運算子</span><span class="sxs-lookup"><span data-stu-id="f5c4a-112">Comparison Operators</span></span>  
 <span data-ttu-id="f5c4a-113">比較運算子，例如`=`， `<`， `>`， `<>`， `<=`，和`>=`比較運算子右邊的運算式的左邊的運算式所產生的布林運算式運算子和評估結果為`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-113">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="f5c4a-114">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-114">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="f5c4a-115">由於 42 小於 81，上述範例中的布林運算式會評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-115">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="f5c4a-116">如需這類運算式的詳細資訊，請參閱[值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-116">For more information on this kind of expression, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="f5c4a-117">結合邏輯運算子的比較運算子</span><span class="sxs-lookup"><span data-stu-id="f5c4a-117">Comparison Operators Combined with Logical Operators</span></span>  
 <span data-ttu-id="f5c4a-118">比較運算式可產生更複雜的布林運算式中使用邏輯運算子結合。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-118">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="f5c4a-119">下列範例示範如何搭配使用邏輯運算子的比較運算子的使用。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-119">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="f5c4a-120">在上述範例中，整個運算式的值取決於每一邊的運算式值`And`運算子。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-120">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="f5c4a-121">如果這兩個運算式都是`True`，則整體的運算式會評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-121">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="f5c4a-122">如果任一個運算式是`False`，則整個運算式會評估為`False`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-122">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="f5c4a-123">最少運算運算子</span><span class="sxs-lookup"><span data-stu-id="f5c4a-123">Short-Circuiting Operators</span></span>  
 <span data-ttu-id="f5c4a-124">邏輯運算子`AndAlso`和`OrElse`表現所謂*最少運算*。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-124">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="f5c4a-125">最少運算運算子會先評估的左的運算元。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-125">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="f5c4a-126">如果左的運算元判斷整個運算式的值，程式執行程序而不需要評估右運算式。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-126">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="f5c4a-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-127">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 <span data-ttu-id="f5c4a-128">在上述範例中，運算子會評估左邊的運算式， `45 < 12`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-128">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="f5c4a-129">因為左邊的運算式會評估為`False`，整個邏輯運算式必須評估為`False`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-129">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="f5c4a-130">程式執行，因此略過內的程式碼執行`If`區塊，而不需要評估右運算式， `testFunction(3)`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-130">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="f5c4a-131">此範例不會呼叫`testFunction()`因為左邊的運算式證明整個運算式。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-131">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="f5c4a-132">同樣地，如果左邊的運算式中使用邏輯運算式`OrElse`評估為`True`，繼續執行至下一行程式碼而不需要評估右運算式，因為左邊的運算式已經驗證整個運算式。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-132">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="f5c4a-133">具有非最少運算運算子的比較</span><span class="sxs-lookup"><span data-stu-id="f5c4a-133">Comparison with Non-Short-Circuiting Operators</span></span>  
 <span data-ttu-id="f5c4a-134">相反地，會評估邏輯運算子的兩側時邏輯運算子`And`和`Or`可用。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-134">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="f5c4a-135">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 <span data-ttu-id="f5c4a-136">上述範例會呼叫`testFunction()`即使左邊的運算式評估為`False`。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-136">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="f5c4a-137">括號運算式</span><span class="sxs-lookup"><span data-stu-id="f5c4a-137">Parenthetical Expressions</span></span>  
 <span data-ttu-id="f5c4a-138">您可以使用括號控制的布林運算式的評估順序。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-138">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="f5c4a-139">先評估括號括住的運算式。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-139">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="f5c4a-140">多個巢狀層級，優先順序會授與給巢狀最深處的運算式。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-140">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="f5c4a-141">括號內評估會繼續根據運算子優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-141">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="f5c4a-142">如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c4a-142">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c4a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5c4a-143">See Also</span></span>  
 [<span data-ttu-id="f5c4a-144">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="f5c4a-144">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="f5c4a-145">數值比較</span><span class="sxs-lookup"><span data-stu-id="f5c4a-145">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="f5c4a-146">陳述式</span><span class="sxs-lookup"><span data-stu-id="f5c4a-146">Statements</span></span>](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="f5c4a-147">比較運算子</span><span class="sxs-lookup"><span data-stu-id="f5c4a-147">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="f5c4a-148">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="f5c4a-148">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [<span data-ttu-id="f5c4a-149">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="f5c4a-149">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="f5c4a-150">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="f5c4a-150">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
