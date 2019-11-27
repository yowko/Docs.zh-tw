---
title: 比較運算子
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: e1feb08539e47ec6fda64aa1a1f8ec2cc19f7b62
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346072"
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="df3b4-102">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="df3b4-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="df3b4-103">比較運算子會比較兩個運算式，並傳回代表其值之關聯性的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="df3b4-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="df3b4-104">有運算子可比較數值、比較字串的運算子，以及比較物件的運算子。</span><span class="sxs-lookup"><span data-stu-id="df3b4-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="df3b4-105">這裡將討論這三種類型的運算子。</span><span class="sxs-lookup"><span data-stu-id="df3b4-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="df3b4-106">比較數值</span><span class="sxs-lookup"><span data-stu-id="df3b4-106">Comparing Numeric Values</span></span>  
 <span data-ttu-id="df3b4-107">Visual Basic 使用六個數值比較運算子來比較數值。</span><span class="sxs-lookup"><span data-stu-id="df3b4-107">Visual Basic compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="df3b4-108">每個運算子都會接受兩個評估為數值之運算式的運算元。</span><span class="sxs-lookup"><span data-stu-id="df3b4-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="df3b4-109">下表列出運算子，並顯示各項的範例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="df3b4-110">運算子</span><span class="sxs-lookup"><span data-stu-id="df3b4-110">Operator</span></span>|<span data-ttu-id="df3b4-111">測試的條件</span><span class="sxs-lookup"><span data-stu-id="df3b4-111">Condition tested</span></span>|<span data-ttu-id="df3b4-112">範例</span><span class="sxs-lookup"><span data-stu-id="df3b4-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="df3b4-113">`=` （相等）</span><span class="sxs-lookup"><span data-stu-id="df3b4-113">`=` (Equality)</span></span>|<span data-ttu-id="df3b4-114">第一個運算式的值是否等於秒的值？</span><span class="sxs-lookup"><span data-stu-id="df3b4-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="df3b4-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="df3b4-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="df3b4-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="df3b4-118">`<>` （不等）</span><span class="sxs-lookup"><span data-stu-id="df3b4-118">`<>` (Inequality)</span></span>|<span data-ttu-id="df3b4-119">第一個運算式的值是否與第二個運算式的值不相等？</span><span class="sxs-lookup"><span data-stu-id="df3b4-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="df3b4-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="df3b4-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="df3b4-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="df3b4-123">`<` （小於）</span><span class="sxs-lookup"><span data-stu-id="df3b4-123">`<` (Less than)</span></span>|<span data-ttu-id="df3b4-124">第一個運算式的值是否小於第二個的值？</span><span class="sxs-lookup"><span data-stu-id="df3b4-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="df3b4-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="df3b4-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="df3b4-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="df3b4-128">`>` （大於）</span><span class="sxs-lookup"><span data-stu-id="df3b4-128">`>` (Greater than)</span></span>|<span data-ttu-id="df3b4-129">第一個運算式的值是否大於第二個的值？</span><span class="sxs-lookup"><span data-stu-id="df3b4-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="df3b4-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="df3b4-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="df3b4-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="df3b4-133">`<=` （小於或等於）</span><span class="sxs-lookup"><span data-stu-id="df3b4-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="df3b4-134">第一個運算式的值是否小於或等於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="df3b4-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="df3b4-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="df3b4-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="df3b4-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="df3b4-138">`>=` （大於或等於）</span><span class="sxs-lookup"><span data-stu-id="df3b4-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="df3b4-139">第一個運算式的值是否大於或等於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="df3b4-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="df3b4-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="df3b4-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="df3b4-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="df3b4-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="df3b4-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="df3b4-143">比較字串</span><span class="sxs-lookup"><span data-stu-id="df3b4-143">Comparing Strings</span></span>  
 <span data-ttu-id="df3b4-144">Visual Basic 使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)和數值比較運算子來比較字串。</span><span class="sxs-lookup"><span data-stu-id="df3b4-144">Visual Basic compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="df3b4-145">`Like` 運算子可讓您指定模式。</span><span class="sxs-lookup"><span data-stu-id="df3b4-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="df3b4-146">然後，字串會與模式進行比較，如果相符，則會 `True`結果。</span><span class="sxs-lookup"><span data-stu-id="df3b4-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="df3b4-147">否則，結果為 `False`。</span><span class="sxs-lookup"><span data-stu-id="df3b4-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="df3b4-148">數值運算子可讓您根據排序次序來比較 `String` 值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="df3b4-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="df3b4-149">前一個範例中的結果是 `True` 的，因為第一個字串中的第一個字元會在第二個字串的第一個字元之前排序。</span><span class="sxs-lookup"><span data-stu-id="df3b4-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="df3b4-150">如果第一個字元相等，則比較會繼續在兩個字串中的下一個字元，依此類推。</span><span class="sxs-lookup"><span data-stu-id="df3b4-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="df3b4-151">您也可以使用等號比較運算子來測試字串是否相等，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="df3b4-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="df3b4-152">如果一個字串是另一個的前置詞，例如 "aa" 和 "aaa"，則較長的字串會被視為大於較短的字串。</span><span class="sxs-lookup"><span data-stu-id="df3b4-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="df3b4-153">說明如下例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="df3b4-154">排序次序是根據 `Option Compare`的設定，以二進位比較或文字比較為基礎。</span><span class="sxs-lookup"><span data-stu-id="df3b4-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="df3b4-155">如需詳細資訊，請參閱[Option Compare 語句](../../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="df3b4-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="df3b4-156">比較物件</span><span class="sxs-lookup"><span data-stu-id="df3b4-156">Comparing Objects</span></span>  
 <span data-ttu-id="df3b4-157">Visual Basic 會比較兩個物件參考變數與[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)和[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="df3b4-157">Visual Basic compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="df3b4-158">您可以使用其中一個運算子來判斷兩個參考變數是否參考相同的物件實例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="df3b4-159">說明如下例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-159">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 <span data-ttu-id="df3b4-160">在上述範例中，`x Is y` 會評估為 `True`，因為這兩個變數都參考相同的實例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-160">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="df3b4-161">請使用下列範例來對比此結果。</span><span class="sxs-lookup"><span data-stu-id="df3b4-161">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 <span data-ttu-id="df3b4-162">在上述範例中，`x Is y` 會評估為 `False`，因為雖然變數會參考相同類型的物件，但它們會參考該類型的不同實例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-162">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="df3b4-163">當您想要測試兩個未指向相同實例的物件時，`IsNot` 運算子可讓您避免 `Not` 和 `Is`的文法笨拙組合。</span><span class="sxs-lookup"><span data-stu-id="df3b4-163">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="df3b4-164">說明如下例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-164">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 <span data-ttu-id="df3b4-165">在上述範例中，`If a IsNot b` 相當於 `If Not a Is b`。</span><span class="sxs-lookup"><span data-stu-id="df3b4-165">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="df3b4-166">比較物件類型</span><span class="sxs-lookup"><span data-stu-id="df3b4-166">Comparing Object Type</span></span>  
 <span data-ttu-id="df3b4-167">您可以使用 `TypeOf`...`Is` 運算式，測試物件是否為特定類型。</span><span class="sxs-lookup"><span data-stu-id="df3b4-167">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="df3b4-168">語法如下：</span><span class="sxs-lookup"><span data-stu-id="df3b4-168">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="df3b4-169">當 `typename` 指定介面類別型時，如果物件會執行介面類別型，則 `TypeOf`...`Is` 運算式會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="df3b4-169">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="df3b4-170">當 `typename` 是類別類型時，如果物件是所指定類別的實例或衍生自指定類別的類別，則運算式會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="df3b4-170">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="df3b4-171">說明如下例。</span><span class="sxs-lookup"><span data-stu-id="df3b4-171">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 <span data-ttu-id="df3b4-172">在上述範例中，`TypeOf x Is Control` 運算式會評估為 `True`，因為 `x` 的類型是 `Button`，這會繼承自 `Control`。</span><span class="sxs-lookup"><span data-stu-id="df3b4-172">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="df3b4-173">如需詳細資訊，請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="df3b4-173">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df3b4-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df3b4-174">See also</span></span>

- [<span data-ttu-id="df3b4-175">數值比較</span><span class="sxs-lookup"><span data-stu-id="df3b4-175">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="df3b4-176">比較運算子</span><span class="sxs-lookup"><span data-stu-id="df3b4-176">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="df3b4-177">運算子</span><span class="sxs-lookup"><span data-stu-id="df3b4-177">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="df3b4-178">Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="df3b4-178">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="df3b4-179">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="df3b4-179">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [<span data-ttu-id="df3b4-180">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="df3b4-180">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
