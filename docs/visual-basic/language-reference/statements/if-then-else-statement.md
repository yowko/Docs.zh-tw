---
title: If...Then...Else 陳述式 (Visual Basic)
ms.date: 04/16/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: conceptual
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
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1080a17cfcc493175c1e2f3527837030b4254bc2
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="acac1-102">If...Then...Else 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acac1-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="acac1-103">根據運算式的值而定，有條件地執行陳述式群組。</span><span class="sxs-lookup"><span data-stu-id="acac1-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acac1-104">語法</span><span class="sxs-lookup"><span data-stu-id="acac1-104">Syntax</span></span>  
  
```  
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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="acac1-105">範例程式碼的快速連結</span><span class="sxs-lookup"><span data-stu-id="acac1-105">Quick links to example code</span></span>

<span data-ttu-id="acac1-106">本文包含數個範例說明使用`If`...`Then`...`Else`陳述式：</span><span class="sxs-lookup"><span data-stu-id="acac1-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

* [<span data-ttu-id="acac1-107">多行的語法範例</span><span class="sxs-lookup"><span data-stu-id="acac1-107">Multiline syntax example</span></span>](#multi-line)
* [<span data-ttu-id="acac1-108">巢狀的語法範例</span><span class="sxs-lookup"><span data-stu-id="acac1-108">Nested syntax example</span></span>](#nested)
* [<span data-ttu-id="acac1-109">單行語法範例</span><span class="sxs-lookup"><span data-stu-id="acac1-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="acac1-110">組件</span><span class="sxs-lookup"><span data-stu-id="acac1-110">Parts</span></span>  
 `condition`  
 <span data-ttu-id="acac1-111">必要。</span><span class="sxs-lookup"><span data-stu-id="acac1-111">Required.</span></span> <span data-ttu-id="acac1-112">運算式。</span><span class="sxs-lookup"><span data-stu-id="acac1-112">Expression.</span></span> <span data-ttu-id="acac1-113">必須評估為`True`或`False`，或可以隱含轉換成資料型別`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="acac1-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="acac1-114">如果運算式是[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`變數評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，條件是運算式會視為`False`和`Else`執行區塊。</span><span class="sxs-lookup"><span data-stu-id="acac1-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False` and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="acac1-115">在單行語法; 所需選擇性參數的多行的語法。</span><span class="sxs-lookup"><span data-stu-id="acac1-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="acac1-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="acac1-116">Optional.</span></span> <span data-ttu-id="acac1-117">一或多個陳述式下列`If`...`Then`時，會執行`condition`評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="acac1-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="acac1-118">若`ElseIf`存在。</span><span class="sxs-lookup"><span data-stu-id="acac1-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="acac1-119">運算式。</span><span class="sxs-lookup"><span data-stu-id="acac1-119">Expression.</span></span> <span data-ttu-id="acac1-120">必須評估為`True`或`False`，或可以隱含轉換成資料型別`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="acac1-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="acac1-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="acac1-121">Optional.</span></span> <span data-ttu-id="acac1-122">一或多個陳述式下列`ElseIf`...`Then`時，會執行`elseifcondition`評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="acac1-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="acac1-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="acac1-123">Optional.</span></span> <span data-ttu-id="acac1-124">如果沒有先前執行的一或多個陳述式`condition`或`elseifcondition`運算式評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="acac1-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="acac1-125">終止的多行新版`If`...`Then`...`Else`區塊。</span><span class="sxs-lookup"><span data-stu-id="acac1-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acac1-126">備註</span><span class="sxs-lookup"><span data-stu-id="acac1-126">Remarks</span></span>  
  
### <a name="multiline-syntax"></a><span data-ttu-id="acac1-127">多行的語法</span><span class="sxs-lookup"><span data-stu-id="acac1-127">Multiline syntax</span></span>  
 <span data-ttu-id="acac1-128">當`If`...`Then`...`Else`遇到陳述式時，`condition`進行測試。</span><span class="sxs-lookup"><span data-stu-id="acac1-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="acac1-129">如果`condition`是`True`、 陳述式`Then`會執行。</span><span class="sxs-lookup"><span data-stu-id="acac1-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="acac1-130">如果`condition`是`False`，每個`ElseIf`陳述式 （如果有的話） 會評估順序。</span><span class="sxs-lookup"><span data-stu-id="acac1-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="acac1-131">當`True``elseifcondition`找到，緊接相關聯的陳述式`ElseIf`會執行。</span><span class="sxs-lookup"><span data-stu-id="acac1-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="acac1-132">如果沒有`elseifcondition`評估為`True`，或者如果有任何`ElseIf`陳述式、 陳述式`Else`會執行。</span><span class="sxs-lookup"><span data-stu-id="acac1-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="acac1-133">在執行下列陳述式之後`Then`， `ElseIf`，或`Else`，之後的陳述式會繼續執行`End If`。</span><span class="sxs-lookup"><span data-stu-id="acac1-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="acac1-134">`ElseIf`和`Else`子句是選擇性。</span><span class="sxs-lookup"><span data-stu-id="acac1-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="acac1-135">您可以擁有許多`ElseIf`子句做為您想要`If`...`Then`...`Else`陳述式，但不是`ElseIf`子句可以出現在之後`Else`子句。</span><span class="sxs-lookup"><span data-stu-id="acac1-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="acac1-136">`If`...`Then`...`Else`可以彼此嵌入陳述式。</span><span class="sxs-lookup"><span data-stu-id="acac1-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="acac1-137">在多行的語法中，`If`陳述式必須是唯一的陳述式的第一行。</span><span class="sxs-lookup"><span data-stu-id="acac1-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="acac1-138">`ElseIf`， `Else`，和`End If`陳述式前面可以有只有行標籤。</span><span class="sxs-lookup"><span data-stu-id="acac1-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="acac1-139">`If`...`Then`...`Else`區塊的結尾必須`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="acac1-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="acac1-140">[選取...陳述式的大小寫](../../../visual-basic/language-reference/statements/select-case-statement.md)評估單一運算式，有幾個可能的值時，可能會更有用。</span><span class="sxs-lookup"><span data-stu-id="acac1-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
### <a name="single-line-syntax"></a><span data-ttu-id="acac1-141">單行語法</span><span class="sxs-lookup"><span data-stu-id="acac1-141">Single-Line syntax</span></span>  
 <span data-ttu-id="acac1-142">您可以使用單一條件與程式碼的單行語法來執行，如果是 true。</span><span class="sxs-lookup"><span data-stu-id="acac1-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="acac1-143">不過，多行語法可提供更多的結構和彈性，而且易於讀取、 維護及偵錯。</span><span class="sxs-lookup"><span data-stu-id="acac1-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="acac1-144">下面這樣`Then`關鍵字會檢查以判斷在陳述式是否為單行`If`。</span><span class="sxs-lookup"><span data-stu-id="acac1-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="acac1-145">如果不是註解後面出現`Then`同一行中，陳述式會被視為單一線條`If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="acac1-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="acac1-146">如果`Then`不存在，它必須是多行開頭`If`...`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="acac1-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="acac1-147">在單行語法中，您可以有多個陳述式的結果執行`If`...`Then`決策。</span><span class="sxs-lookup"><span data-stu-id="acac1-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="acac1-148">所有陳述式必須在同一行，並以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="acac1-148">All statements must be on the same line and be separated by colons.</span></span>  

## <a name="multiline-syntax-example"></a><span data-ttu-id="acac1-149">多行的語法範例</span><span class="sxs-lookup"><span data-stu-id="acac1-149">Multiline syntax example</span></span>

<a name="multi-line"></a>
 
 <span data-ttu-id="acac1-150">下列範例說明使用的多行的語法`If`...`Then`...`Else`陳述式。</span><span class="sxs-lookup"><span data-stu-id="acac1-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb?highlight=11,14,17,19)]

## <a name="nested-syntax-example"></a><span data-ttu-id="acac1-151">巢狀的語法範例</span><span class="sxs-lookup"><span data-stu-id="acac1-151">Nested syntax example</span></span>

<a name="nested"></a>

 <span data-ttu-id="acac1-152">下列範例包含巢狀`If`...`Then`...`Else`陳述式。</span><span class="sxs-lookup"><span data-stu-id="acac1-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb?highlight=14,15,17,19,20,21,23,25,26,28)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="acac1-153">單行語法範例</span><span class="sxs-lookup"><span data-stu-id="acac1-153">Single-Line syntax example</span></span>
  
<a name="single-line"></a> <span data-ttu-id="acac1-154">下列範例說明使用單行語法。</span><span class="sxs-lookup"><span data-stu-id="acac1-154">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb?highlight=18)]
  
## <a name="see-also"></a><span data-ttu-id="acac1-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acac1-155">See also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [<span data-ttu-id="acac1-156">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="acac1-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="acac1-157">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="acac1-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="acac1-158">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="acac1-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="acac1-159">決策結構</span><span class="sxs-lookup"><span data-stu-id="acac1-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="acac1-160">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="acac1-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="acac1-161">If 運算子</span><span class="sxs-lookup"><span data-stu-id="acac1-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
