---
title: Select...Case 陳述式
ms.date: 07/20/2015
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
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404235"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="546e2-102">Select...Case 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="546e2-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="546e2-103">視運算式的值而定，執行數個語句群組的其中一個。</span><span class="sxs-lookup"><span data-stu-id="546e2-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="546e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="546e2-104">Syntax</span></span>  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="546e2-105">組件</span><span class="sxs-lookup"><span data-stu-id="546e2-105">Parts</span></span>  
  
|<span data-ttu-id="546e2-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="546e2-106">Term</span></span>|<span data-ttu-id="546e2-107">定義</span><span class="sxs-lookup"><span data-stu-id="546e2-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="546e2-108">必要。</span><span class="sxs-lookup"><span data-stu-id="546e2-108">Required.</span></span> <span data-ttu-id="546e2-109">運算式。</span><span class="sxs-lookup"><span data-stu-id="546e2-109">Expression.</span></span> <span data-ttu-id="546e2-110">必須評估為其中一個基本資料類型（、、、、、、、、、、、、、、 `Boolean` `Byte` `Char` `Date` `Double` `Decimal` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` 和 `UShort` ）。</span><span class="sxs-lookup"><span data-stu-id="546e2-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="546e2-111">語句中的必要項 `Case` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-111">Required in a `Case` statement.</span></span> <span data-ttu-id="546e2-112">表示之符合值的運算式子句清單 `testexpression` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="546e2-113">多個運算式子句會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="546e2-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="546e2-114">每個子句都可以採用下列其中一種形式：</span><span class="sxs-lookup"><span data-stu-id="546e2-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="546e2-115">-   *運算式* `To`*運算式*2</span><span class="sxs-lookup"><span data-stu-id="546e2-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="546e2-116">-[ `Is` ] *comparisonoperator* *運算式*</span><span class="sxs-lookup"><span data-stu-id="546e2-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="546e2-117">-   *運算式*</span><span class="sxs-lookup"><span data-stu-id="546e2-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="546e2-118">使用 `To` 關鍵字來指定的相符值範圍的界限 `testexpression` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="546e2-119">的值 `expression1` 必須小於或等於的值 `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="546e2-120">使用 `Is` 關鍵字搭配比較運算子（ `=` 、 `<>` 、、、 `<` `<=` `>` 或 `>=` ）來指定的比對值限制 `testexpression` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="546e2-121">如果 `Is` 未提供關鍵字，則會在*comparisonoperator*之前自動插入。</span><span class="sxs-lookup"><span data-stu-id="546e2-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="546e2-122">僅指定的表單 `expression` 會被視為表單的特殊案例， `Is` 其中*comparisonoperator*是等號（ `=` ）。</span><span class="sxs-lookup"><span data-stu-id="546e2-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="546e2-123">這個表單會評估為 `testexpression`  =  `expression` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="546e2-124">中的運算式 `expressionlist` 可以是任何資料類型，前提是它們會隱含地轉換成的類型， `testexpression` 而適當的適用 `comparisonoperator` 于搭配使用的兩個類型。</span><span class="sxs-lookup"><span data-stu-id="546e2-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="546e2-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546e2-125">Optional.</span></span> <span data-ttu-id="546e2-126">`Case`如果 `testexpression` 符合中的任何子句，則在之後執行的一個或多個語句 `expressionlist` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="546e2-127">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546e2-127">Optional.</span></span> <span data-ttu-id="546e2-128">`Case Else`如果 `testexpression` 不符合任何語句之中的任何子句，則會在執行之後的一或多個語句 `expressionlist` `Case` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="546e2-129">終止 `Select` ... 結構的定義。 `Case`</span><span class="sxs-lookup"><span data-stu-id="546e2-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="546e2-130">備註</span><span class="sxs-lookup"><span data-stu-id="546e2-130">Remarks</span></span>  
 <span data-ttu-id="546e2-131">如果 `testexpression` 符合 any `Case` `expressionlist` 子句，則語句後面的語句會 `Case` 執行到下一個 `Case` 、 `Case Else` 或 `End Select` 語句。</span><span class="sxs-lookup"><span data-stu-id="546e2-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="546e2-132">控制項接著會傳遞至後面的語句 `End Select` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="546e2-133">如果 `testexpression` 符合一個 `expressionlist` 以上子句中的子句 `Case` ，則只會執行第一個相符專案之後的語句。</span><span class="sxs-lookup"><span data-stu-id="546e2-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="546e2-134">`Case Else` `elsestatements` 如果在 `testexpression` `expressionlist` 任何其他語句的和子句之間找不到相符項，則會使用語句來導入要執行的 `Case` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="546e2-135">雖然並非必要，但在 `Case Else` 您的結構中有語句來處理未預期的值是個不錯的主意 `Select Case` `testexpression` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="546e2-136">如果沒有 `Case` `expressionlist` 符合的子句 `testexpression` ，而且沒有 `Case Else` 語句，則控制權會傳遞至下列語句 `End Select` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="546e2-137">您可以在每個子句中使用多個運算式或範圍 `Case` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="546e2-138">例如，下列程式程式碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="546e2-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> <span data-ttu-id="546e2-139">`Is`和語句中所使用的關鍵字與 `Case` `Case Else` [is 運算子](../operators/is-operator.md)不同，後者是用於物件參考比較。</span><span class="sxs-lookup"><span data-stu-id="546e2-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="546e2-140">您可以為字元字串指定範圍和多個運算式。</span><span class="sxs-lookup"><span data-stu-id="546e2-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="546e2-141">在下列範例中， `Case` 會比對完全等於「蘋果」的任何字串、以字母順序表示「螺母」和「湯品」之間的值，或包含與目前值完全相同的值 `testItem` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="546e2-142">的設定 `Option Compare` 可能會影響字串比較。</span><span class="sxs-lookup"><span data-stu-id="546e2-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="546e2-143">在下 `Option Compare Text` ，字串 "蘋果" 和 "蘋果" 比較為相等，但在之下則 `Option Compare Binary` 不會。</span><span class="sxs-lookup"><span data-stu-id="546e2-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="546e2-144">`Case`具有多個子句的語句可以呈現稱為「最少運算 *」的*行為。</span><span class="sxs-lookup"><span data-stu-id="546e2-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="546e2-145">Visual Basic 會從左至右評估子句，而且如果其中一個會產生符合的 `testexpression` ，則不會評估其餘的子句。</span><span class="sxs-lookup"><span data-stu-id="546e2-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="546e2-146">最短運算可以改善效能，但如果您預期要評估中的每個運算式，可能會產生非預期的結果 `expressionlist` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="546e2-147">如需有關簡短運算的詳細資訊，請參閱[布林運算式](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="546e2-147">For more information on short-circuiting, see [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="546e2-148">如果或語句區塊內的程式碼 `Case` `Case Else` 不需要執行區塊中的任何其他語句，它可以使用語句來結束區塊 `Exit Select` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="546e2-149">這會立即將控制權轉移給後面的語句 `End Select` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="546e2-150">`Select Case`可以嵌套結構。</span><span class="sxs-lookup"><span data-stu-id="546e2-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="546e2-151">每個嵌套 `Select Case` 的結構都必須有相符的 `End Select` 語句，而且必須完全包含 `Case` 在 `Case Else` `Select Case` 其所用之外部結構的單一或語句區塊內。</span><span class="sxs-lookup"><span data-stu-id="546e2-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="546e2-152">範例</span><span class="sxs-lookup"><span data-stu-id="546e2-152">Example</span></span>  
 <span data-ttu-id="546e2-153">下列範例會使用 `Select Case` 結構來撰寫對應至變數值的線條 `number` 。</span><span class="sxs-lookup"><span data-stu-id="546e2-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="546e2-154">第二個 `Case` 語句包含符合目前值的值 `number` ，因此會執行寫入「介於6和8（含）」的語句。</span><span class="sxs-lookup"><span data-stu-id="546e2-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a><span data-ttu-id="546e2-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="546e2-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [<span data-ttu-id="546e2-156">End 語句</span><span class="sxs-lookup"><span data-stu-id="546e2-156">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="546e2-157">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="546e2-157">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="546e2-158">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="546e2-158">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="546e2-159">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="546e2-159">Exit Statement</span></span>](exit-statement.md)
