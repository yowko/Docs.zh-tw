---
title: If...Then...Else 陳述式
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351167"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="260c6-102">If...Then...Else 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="260c6-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="260c6-103">根據運算式的值而定，有條件地執行陳述式群組。</span><span class="sxs-lookup"><span data-stu-id="260c6-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="260c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="260c6-104">Syntax</span></span>

```vb
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a><span data-ttu-id="260c6-105">Quick links to example code</span><span class="sxs-lookup"><span data-stu-id="260c6-105">Quick links to example code</span></span>

<span data-ttu-id="260c6-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span><span class="sxs-lookup"><span data-stu-id="260c6-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="260c6-107">Multiline syntax example</span><span class="sxs-lookup"><span data-stu-id="260c6-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="260c6-108">Nested syntax example</span><span class="sxs-lookup"><span data-stu-id="260c6-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="260c6-109">Single-line syntax example</span><span class="sxs-lookup"><span data-stu-id="260c6-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="260c6-110">組件</span><span class="sxs-lookup"><span data-stu-id="260c6-110">Parts</span></span>

`condition` \
<span data-ttu-id="260c6-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="260c6-111">Required.</span></span> <span data-ttu-id="260c6-112">Expression.</span><span class="sxs-lookup"><span data-stu-id="260c6-112">Expression.</span></span> <span data-ttu-id="260c6-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="260c6-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="260c6-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span><span class="sxs-lookup"><span data-stu-id="260c6-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="260c6-115">Required in the single-line syntax; optional in the multiline syntax.</span><span class="sxs-lookup"><span data-stu-id="260c6-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="260c6-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="260c6-116">Optional.</span></span> <span data-ttu-id="260c6-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span><span class="sxs-lookup"><span data-stu-id="260c6-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="260c6-118">Required if `ElseIf` is present.</span><span class="sxs-lookup"><span data-stu-id="260c6-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="260c6-119">Expression.</span><span class="sxs-lookup"><span data-stu-id="260c6-119">Expression.</span></span> <span data-ttu-id="260c6-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="260c6-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="260c6-121">選擇項。</span><span class="sxs-lookup"><span data-stu-id="260c6-121">Optional.</span></span> <span data-ttu-id="260c6-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span><span class="sxs-lookup"><span data-stu-id="260c6-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="260c6-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="260c6-123">Optional.</span></span> <span data-ttu-id="260c6-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span><span class="sxs-lookup"><span data-stu-id="260c6-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="260c6-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span><span class="sxs-lookup"><span data-stu-id="260c6-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="260c6-126">備註</span><span class="sxs-lookup"><span data-stu-id="260c6-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="260c6-127">Multiline syntax</span><span class="sxs-lookup"><span data-stu-id="260c6-127">Multiline syntax</span></span>

<span data-ttu-id="260c6-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span><span class="sxs-lookup"><span data-stu-id="260c6-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="260c6-129">If `condition` is `True`, the statements following `Then` are executed.</span><span class="sxs-lookup"><span data-stu-id="260c6-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="260c6-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span><span class="sxs-lookup"><span data-stu-id="260c6-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="260c6-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span><span class="sxs-lookup"><span data-stu-id="260c6-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="260c6-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span><span class="sxs-lookup"><span data-stu-id="260c6-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="260c6-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span><span class="sxs-lookup"><span data-stu-id="260c6-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="260c6-134">The `ElseIf` and `Else` clauses are both optional.</span><span class="sxs-lookup"><span data-stu-id="260c6-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="260c6-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span><span class="sxs-lookup"><span data-stu-id="260c6-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="260c6-136">`If`...`Then`...`Else` statements can be nested within each other.</span><span class="sxs-lookup"><span data-stu-id="260c6-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="260c6-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span><span class="sxs-lookup"><span data-stu-id="260c6-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="260c6-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span><span class="sxs-lookup"><span data-stu-id="260c6-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="260c6-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span><span class="sxs-lookup"><span data-stu-id="260c6-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="260c6-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span><span class="sxs-lookup"><span data-stu-id="260c6-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="260c6-141">Single-Line syntax</span><span class="sxs-lookup"><span data-stu-id="260c6-141">Single-Line syntax</span></span>

<span data-ttu-id="260c6-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span><span class="sxs-lookup"><span data-stu-id="260c6-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="260c6-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span><span class="sxs-lookup"><span data-stu-id="260c6-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="260c6-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span><span class="sxs-lookup"><span data-stu-id="260c6-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="260c6-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span><span class="sxs-lookup"><span data-stu-id="260c6-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="260c6-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="260c6-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="260c6-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span><span class="sxs-lookup"><span data-stu-id="260c6-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="260c6-148">All statements must be on the same line and be separated by colons.</span><span class="sxs-lookup"><span data-stu-id="260c6-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="260c6-149">Multiline syntax example</span><span class="sxs-lookup"><span data-stu-id="260c6-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="260c6-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span><span class="sxs-lookup"><span data-stu-id="260c6-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="260c6-151">Nested syntax example</span><span class="sxs-lookup"><span data-stu-id="260c6-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="260c6-152">The following example contains nested `If`...`Then`...`Else` statements.</span><span class="sxs-lookup"><span data-stu-id="260c6-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="260c6-153">Single-Line syntax example</span><span class="sxs-lookup"><span data-stu-id="260c6-153">Single-Line syntax example</span></span>

<a name="single-line"></a> <span data-ttu-id="260c6-154">The following example illustrates the use of the single-line syntax.</span><span class="sxs-lookup"><span data-stu-id="260c6-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="260c6-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="260c6-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="260c6-156">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="260c6-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="260c6-157">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="260c6-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="260c6-158">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="260c6-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="260c6-159">決策結構</span><span class="sxs-lookup"><span data-stu-id="260c6-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="260c6-160">Logical and Bitwise Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="260c6-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="260c6-161">If 運算子</span><span class="sxs-lookup"><span data-stu-id="260c6-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
