---
title: "Select...Case 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7527763a05ec32af88c6ba66ef717d839c33154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="0f036-102">Select...Case 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f036-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="0f036-103">執行其中一個陳述式中，運算式的值而定的數個群組。</span><span class="sxs-lookup"><span data-stu-id="0f036-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f036-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f036-104">Syntax</span></span>  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="0f036-105">組件</span><span class="sxs-lookup"><span data-stu-id="0f036-105">Parts</span></span>  
  
|<span data-ttu-id="0f036-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0f036-106">Term</span></span>|<span data-ttu-id="0f036-107">定義</span><span class="sxs-lookup"><span data-stu-id="0f036-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="0f036-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0f036-108">Required.</span></span> <span data-ttu-id="0f036-109">運算式。</span><span class="sxs-lookup"><span data-stu-id="0f036-109">Expression.</span></span> <span data-ttu-id="0f036-110">必須評估為其中一種基本資料類型 (`Boolean`， `Byte`， `Char`， `Date`， `Double`， `Decimal`， `Integer`， `Long`， `Object`， `SByte`， `Short`，`Single`， `String`， `UInteger`， `ULong`，和`UShort`)。</span><span class="sxs-lookup"><span data-stu-id="0f036-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="0f036-111">中需要`Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0f036-111">Required in a `Case` statement.</span></span> <span data-ttu-id="0f036-112">代表比對值運算式子句的清單`testexpression`。</span><span class="sxs-lookup"><span data-stu-id="0f036-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="0f036-113">多個運算式子句會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="0f036-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="0f036-114">每個子句可以採用下列格式之一：</span><span class="sxs-lookup"><span data-stu-id="0f036-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="0f036-115">-   *expression1* `To` *expression2*</span><span class="sxs-lookup"><span data-stu-id="0f036-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="0f036-116">-[ `Is` ]*關係運算子**運算式*</span><span class="sxs-lookup"><span data-stu-id="0f036-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="0f036-117">-   *運算式*</span><span class="sxs-lookup"><span data-stu-id="0f036-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="0f036-118">使用`To`關鍵字來指定比對的範圍界限值`testexpression`。</span><span class="sxs-lookup"><span data-stu-id="0f036-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="0f036-119">值`expression1`必須小於或等於值`expression2`。</span><span class="sxs-lookup"><span data-stu-id="0f036-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="0f036-120">使用`Is`關鍵字搭配比較運算子 (`=`， `<>`， `<`， `<=`， `>`，或`>=`) 來比對值的指定限制`testexpression`。</span><span class="sxs-lookup"><span data-stu-id="0f036-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="0f036-121">如果`Is`關鍵字未提供，它會自動插入之前*關係運算子*。</span><span class="sxs-lookup"><span data-stu-id="0f036-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="0f036-122">只指定表單`expression`的特殊案例會被視為`Is`形成 where*關係運算子*為等號 (`=`)。</span><span class="sxs-lookup"><span data-stu-id="0f036-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="0f036-123">此表單會評估為`testexpression`  =  `expression`。</span><span class="sxs-lookup"><span data-stu-id="0f036-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="0f036-124">中的運算式`expressionlist`可以是任何資料類型，提供可以隱含地轉換成的型別`testexpression`和適當`comparisonoperator`適用於兩種類型與正在使用它。</span><span class="sxs-lookup"><span data-stu-id="0f036-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="0f036-125">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0f036-125">Optional.</span></span> <span data-ttu-id="0f036-126">一或多個陳述式下列`Case`，執行的如果`testexpression`符合中的任何子句`expressionlist`。</span><span class="sxs-lookup"><span data-stu-id="0f036-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="0f036-127">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0f036-127">Optional.</span></span> <span data-ttu-id="0f036-128">一或多個陳述式下列`Case Else`，執行的如果`testexpression`不相符在任何子句`expressionlist`其中任一`Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0f036-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="0f036-129">結束的定義`Select`...`Case`建構。</span><span class="sxs-lookup"><span data-stu-id="0f036-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f036-130">備註</span><span class="sxs-lookup"><span data-stu-id="0f036-130">Remarks</span></span>  
 <span data-ttu-id="0f036-131">如果`testexpression`符合任何`Case``expressionlist`子句，陳述式，`Case`陳述式執行到下`Case`， `Case Else`，或`End Select`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0f036-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="0f036-132">然後會將控制權傳遞給之後的陳述式`End Select`。</span><span class="sxs-lookup"><span data-stu-id="0f036-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="0f036-133">如果`testexpression`符合`expressionlist`中多個子句`Case`子句之後的第一個符合的陳述式執行。</span><span class="sxs-lookup"><span data-stu-id="0f036-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="0f036-134">`Case Else`陳述式用於介紹`elsestatements`執行，如果沒有找到符合的之間`testexpression`和`expressionlist`中任何其他子句`Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0f036-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="0f036-135">雖然並非必要，最好在其中具有`Case Else`陳述式中的您`Select Case`建構來處理無法預料`testexpression`值。</span><span class="sxs-lookup"><span data-stu-id="0f036-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="0f036-136">如果沒有`Case``expressionlist`子句符合`testexpression`，而且沒有任何`Case Else`陳述式之後的陳述式來控制傳遞`End Select`。</span><span class="sxs-lookup"><span data-stu-id="0f036-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="0f036-137">您可以使用多個運算式或範圍中每個`Case`子句。</span><span class="sxs-lookup"><span data-stu-id="0f036-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="0f036-138">例如下, 面是有效的。</span><span class="sxs-lookup"><span data-stu-id="0f036-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  <span data-ttu-id="0f036-139">`Is`關鍵字用於`Case`和`Case Else`陳述式不是相同[Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)，用於物件參考比較。</span><span class="sxs-lookup"><span data-stu-id="0f036-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="0f036-140">您可以指定範圍和多個運算式的字元字串。</span><span class="sxs-lookup"><span data-stu-id="0f036-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="0f036-141">在下列範例中，`Case`比對任何字串完全等於 「 蘋果 」、 「 nuts"和"soup 」 之間的值依字母順序，或包含目前的值完全相同的值`testItem`。</span><span class="sxs-lookup"><span data-stu-id="0f036-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="0f036-142">設定`Option Compare`可能會影響字串比較。</span><span class="sxs-lookup"><span data-stu-id="0f036-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="0f036-143">在下`Option Compare Text`，「 蘋果 」 和 「 蘋果 」 的字串比較結果為相等，但在`Option Compare Binary`，不相符。</span><span class="sxs-lookup"><span data-stu-id="0f036-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f036-144">A`Case`展現具有多個子句的陳述式的行為稱為*最少運算*。</span><span class="sxs-lookup"><span data-stu-id="0f036-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="0f036-145">Visual Basic 評估從左到右的子句，和如果有一個會產生相符`testexpression`，不會評估其餘的子句。</span><span class="sxs-lookup"><span data-stu-id="0f036-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="0f036-146">最少運算可改善效能，但它可以產生非預期的結果，如果您預期會在每個運算式`expressionlist`進行評估。</span><span class="sxs-lookup"><span data-stu-id="0f036-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="0f036-147">如需最少運算的詳細資訊，請參閱[布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0f036-147">For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="0f036-148">如果中的程式碼`Case`或`Case Else`陳述式區塊就不需要執行更多的陳述式區塊中，它可以使用結束區塊`Exit Select`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0f036-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="0f036-149">這將控制項傳送立即之後的陳述式`End Select`。</span><span class="sxs-lookup"><span data-stu-id="0f036-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="0f036-150">`Select Case`語法結構，可以是巢狀。</span><span class="sxs-lookup"><span data-stu-id="0f036-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="0f036-151">每個巢狀`Select Case`建構必須具有相符`End Select`陳述式，而且必須完全包含在單一`Case`或`Case Else`陳述式區塊外部`Select Case`建構巢狀內。</span><span class="sxs-lookup"><span data-stu-id="0f036-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f036-152">範例</span><span class="sxs-lookup"><span data-stu-id="0f036-152">Example</span></span>  
 <span data-ttu-id="0f036-153">下列範例會使用`Select Case`建構來寫入變數的值對應的行`number`。</span><span class="sxs-lookup"><span data-stu-id="0f036-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="0f036-154">第二個`Case`陳述式包含的值符合目前的值， `number`，因此陳述式會將寫入 「 介於 6 和 8 （含) 」 執行。</span><span class="sxs-lookup"><span data-stu-id="0f036-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0f036-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f036-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [<span data-ttu-id="0f036-156">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f036-156">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="0f036-157">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f036-157">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="0f036-158">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f036-158">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="0f036-159">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f036-159">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
