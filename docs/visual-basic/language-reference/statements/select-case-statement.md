---
title: Select...Case 陳述式 (Visual Basic)
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
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957650"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="5edb0-102">Select...Case 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5edb0-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="5edb0-103">視運算式的值而定, 執行數個語句群組的其中一個。</span><span class="sxs-lookup"><span data-stu-id="5edb0-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5edb0-104">語法</span><span class="sxs-lookup"><span data-stu-id="5edb0-104">Syntax</span></span>  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="5edb0-105">組件</span><span class="sxs-lookup"><span data-stu-id="5edb0-105">Parts</span></span>  
  
|<span data-ttu-id="5edb0-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="5edb0-106">Term</span></span>|<span data-ttu-id="5edb0-107">定義</span><span class="sxs-lookup"><span data-stu-id="5edb0-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="5edb0-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="5edb0-108">Required.</span></span> <span data-ttu-id="5edb0-109">運算式.</span><span class="sxs-lookup"><span data-stu-id="5edb0-109">Expression.</span></span> <span data-ttu-id="5edb0-110">必須評估為`Boolean`其中一個基本資料類型 (、 `Decimal` `Double` `Date` `Byte` `Char` 、、、`Long`、 、、`SByte`、、、、 、、、、、、、、、`Short` `Integer` `Object``Single`、 、`String` 、`ULong`和)。 `UInteger` `UShort`</span><span class="sxs-lookup"><span data-stu-id="5edb0-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="5edb0-111">語句中的`Case`必要項。</span><span class="sxs-lookup"><span data-stu-id="5edb0-111">Required in a `Case` statement.</span></span> <span data-ttu-id="5edb0-112">表示之符合值的`testexpression`運算式子句清單。</span><span class="sxs-lookup"><span data-stu-id="5edb0-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="5edb0-113">多個運算式子句會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="5edb0-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="5edb0-114">每個子句都可以採用下列其中一種形式:</span><span class="sxs-lookup"><span data-stu-id="5edb0-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="5edb0-115">-   *expression1* `To` *expression2*</span><span class="sxs-lookup"><span data-stu-id="5edb0-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="5edb0-116">-   [ `Is` ] *comparisonoperator* *expression*</span><span class="sxs-lookup"><span data-stu-id="5edb0-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="5edb0-117">-   *運算式*</span><span class="sxs-lookup"><span data-stu-id="5edb0-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="5edb0-118">使用關鍵字來指定的相符`testexpression`值範圍的界限。 `To`</span><span class="sxs-lookup"><span data-stu-id="5edb0-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="5edb0-119">的值`expression1`必須小於或等於的`expression2`值。</span><span class="sxs-lookup"><span data-stu-id="5edb0-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="5edb0-120">`<` `<>` `<=`使用關鍵字搭配`>=`比較`=`運算子 (、、 `testexpression`、 、或)來指定的比對值限制。`>` `Is`</span><span class="sxs-lookup"><span data-stu-id="5edb0-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="5edb0-121">如果未提供關鍵字,則會在comparisonoperator之前自動`Is`插入。</span><span class="sxs-lookup"><span data-stu-id="5edb0-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="5edb0-122">僅`expression`指定的表單會被視為`Is`表單的特殊案例, 其中*comparisonoperator*是等號 (`=`)。</span><span class="sxs-lookup"><span data-stu-id="5edb0-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="5edb0-123">這個表單會評估`testexpression`為 =  `expression`。</span><span class="sxs-lookup"><span data-stu-id="5edb0-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="5edb0-124">中`expressionlist`的運算式可以是任何資料類型, 前提是它們會隱含地轉換成的`testexpression`類型, 而適當`comparisonoperator`的適用于搭配使用的兩個類型。</span><span class="sxs-lookup"><span data-stu-id="5edb0-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="5edb0-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5edb0-125">Optional.</span></span> <span data-ttu-id="5edb0-126">如果符合中`Case` `testexpression` 的任何`expressionlist`子句, 則在之後執行的一個或多個語句。</span><span class="sxs-lookup"><span data-stu-id="5edb0-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="5edb0-127">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5edb0-127">Optional.</span></span> <span data-ttu-id="5edb0-128">如果`Case Else` 不`testexpression` 符合任何`Case`語句之中的任何子句, 則會在執行之後的一或多個語句。`expressionlist`</span><span class="sxs-lookup"><span data-stu-id="5edb0-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="5edb0-129">結束的定義`Select`.。。`Case`結構。</span><span class="sxs-lookup"><span data-stu-id="5edb0-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5edb0-130">備註</span><span class="sxs-lookup"><span data-stu-id="5edb0-130">Remarks</span></span>  
 <span data-ttu-id="5edb0-131">如果`testexpression`符合 any `Case` `End Select` `Case` `Case Else` `Case`子句, 則語句後面的語句會執行到下一個、或語句。 `expressionlist`</span><span class="sxs-lookup"><span data-stu-id="5edb0-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="5edb0-132">控制項接著會傳遞至後面`End Select`的語句。</span><span class="sxs-lookup"><span data-stu-id="5edb0-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="5edb0-133">如果`testexpression` 符合一個以上`Case`子句中的子句,則只會執行第一個相符專案之後的語句。`expressionlist`</span><span class="sxs-lookup"><span data-stu-id="5edb0-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="5edb0-134">如果`Case Else`在任何其他`elsestatements` `testexpression`語句的和`expressionlist`子句之間找不到相符項, 則會使用語句來導入要執行的。 `Case`</span><span class="sxs-lookup"><span data-stu-id="5edb0-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="5edb0-135">雖然並非必要, 但在您`Case Else` `Select Case`的結構中有語句來處理`testexpression`未預期的值是個不錯的主意。</span><span class="sxs-lookup"><span data-stu-id="5edb0-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="5edb0-136">如果沒有`Case` `expressionlist` `End Select`符合的子句,而且沒有語句,則控制權會傳遞至下列語句。`testexpression` `Case Else`</span><span class="sxs-lookup"><span data-stu-id="5edb0-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="5edb0-137">您可以在每個`Case`子句中使用多個運算式或範圍。</span><span class="sxs-lookup"><span data-stu-id="5edb0-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="5edb0-138">例如, 下列程式程式碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="5edb0-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> <span data-ttu-id="5edb0-139">和`Case` `Is` 語句`Case Else`中所使用的關鍵字與[is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)不同, 後者是用於物件參考比較。</span><span class="sxs-lookup"><span data-stu-id="5edb0-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="5edb0-140">您可以為字元字串指定範圍和多個運算式。</span><span class="sxs-lookup"><span data-stu-id="5edb0-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="5edb0-141">在下列範例中, `Case`會比對完全等於「蘋果」的任何字串、以字母順序表示「螺母」和「湯品」之間的值, 或包含與目前值完全相同的`testItem`值。</span><span class="sxs-lookup"><span data-stu-id="5edb0-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="5edb0-142">的設定`Option Compare`可能會影響字串比較。</span><span class="sxs-lookup"><span data-stu-id="5edb0-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="5edb0-143">在`Option Compare Text`下, 字串 "蘋果" 和 "蘋果" 比較為相等, 但在`Option Compare Binary`之下則不會。</span><span class="sxs-lookup"><span data-stu-id="5edb0-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5edb0-144">具有`Case`多個子句的語句可以呈現稱為「最少運算」的行為。</span><span class="sxs-lookup"><span data-stu-id="5edb0-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="5edb0-145">Visual Basic 會從左至右評估子句, 而且如果其中一個會產生符合`testexpression`的, 則不會評估其餘的子句。</span><span class="sxs-lookup"><span data-stu-id="5edb0-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="5edb0-146">最短運算可以改善效能, 但如果您預期要評估中的`expressionlist`每個運算式, 可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="5edb0-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="5edb0-147">如需有關簡短運算的詳細資訊, 請參閱[布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="5edb0-147">For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="5edb0-148">如果`Case` `Exit Select`或`Case Else`語句區塊內的程式碼不需要執行區塊中的任何其他語句, 它可以使用語句來結束區塊。</span><span class="sxs-lookup"><span data-stu-id="5edb0-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="5edb0-149">這會立即將控制權轉移給後面`End Select`的語句。</span><span class="sxs-lookup"><span data-stu-id="5edb0-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="5edb0-150">`Select Case`可以嵌套結構。</span><span class="sxs-lookup"><span data-stu-id="5edb0-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="5edb0-151">每個`Select Case`嵌套的結構都必須`End Select`有相符的語句, 而且必須完全包含`Case`在其所用之外部`Select Case`結構的單一或`Case Else`語句區塊內。</span><span class="sxs-lookup"><span data-stu-id="5edb0-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5edb0-152">範例</span><span class="sxs-lookup"><span data-stu-id="5edb0-152">Example</span></span>  
 <span data-ttu-id="5edb0-153">下列範例會使用`Select Case`結構來撰寫對應至變數`number`值的線條。</span><span class="sxs-lookup"><span data-stu-id="5edb0-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="5edb0-154">第二`Case`個語句包含符合目前`number`值的值, 因此會執行寫入「介於6和 8 (含)」的語句。</span><span class="sxs-lookup"><span data-stu-id="5edb0-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a><span data-ttu-id="5edb0-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5edb0-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [<span data-ttu-id="5edb0-156">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="5edb0-156">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
- [<span data-ttu-id="5edb0-157">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="5edb0-157">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="5edb0-158">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="5edb0-158">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="5edb0-159">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="5edb0-159">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
