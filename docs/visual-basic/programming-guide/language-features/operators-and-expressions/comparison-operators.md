---
title: "在 Visual Basic 中的比較運算子 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- comparison operators, comparing strings
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a958481fa04cb1a9abde69c5215dccd6dbbe4a14
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="56504-102">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56504-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="56504-103">比較運算子比較兩個運算式，並傳回`Boolean`值，表示其值的關聯性。</span><span class="sxs-lookup"><span data-stu-id="56504-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="56504-104">有運算子來比較數值、 運算子來比較字串和比較物件的運算子。</span><span class="sxs-lookup"><span data-stu-id="56504-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="56504-105">本文將討論這三種運算子。</span><span class="sxs-lookup"><span data-stu-id="56504-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="56504-106">比較數值</span><span class="sxs-lookup"><span data-stu-id="56504-106">Comparing Numeric Values</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="56504-107">比較數值資料，請使用六個數值的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="56504-107"> compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="56504-108">每個運算子會使用兩個運算式評估為數值，做為運算元。</span><span class="sxs-lookup"><span data-stu-id="56504-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="56504-109">下表列出的運算子，並顯示每個範例。</span><span class="sxs-lookup"><span data-stu-id="56504-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="56504-110">運算子</span><span class="sxs-lookup"><span data-stu-id="56504-110">Operator</span></span>|<span data-ttu-id="56504-111">測試的條件</span><span class="sxs-lookup"><span data-stu-id="56504-111">Condition tested</span></span>|<span data-ttu-id="56504-112">範例</span><span class="sxs-lookup"><span data-stu-id="56504-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="56504-113">`=`（相等）</span><span class="sxs-lookup"><span data-stu-id="56504-113">`=` (Equality)</span></span>|<span data-ttu-id="56504-114">第二個值是第一個運算式相等的值？</span><span class="sxs-lookup"><span data-stu-id="56504-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="56504-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="56504-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="56504-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="56504-118">`<>`（不等）</span><span class="sxs-lookup"><span data-stu-id="56504-118">`<>` (Inequality)</span></span>|<span data-ttu-id="56504-119">是第一個運算式的值等於第二個值？</span><span class="sxs-lookup"><span data-stu-id="56504-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="56504-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="56504-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="56504-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="56504-123">`<`（小於）</span><span class="sxs-lookup"><span data-stu-id="56504-123">`<` (Less than)</span></span>|<span data-ttu-id="56504-124">是第一個運算式的值大於或等於第二個值？</span><span class="sxs-lookup"><span data-stu-id="56504-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="56504-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="56504-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="56504-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="56504-128">`>`（大於）</span><span class="sxs-lookup"><span data-stu-id="56504-128">`>` (Greater than)</span></span>|<span data-ttu-id="56504-129">是第一個運算式的值大於第二個值？</span><span class="sxs-lookup"><span data-stu-id="56504-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="56504-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="56504-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="56504-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="56504-133">`<=`（小於或等於）</span><span class="sxs-lookup"><span data-stu-id="56504-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="56504-134">小於或等於第二個值是第一個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="56504-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="56504-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="56504-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="56504-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="56504-138">`>=`（大於或等於）</span><span class="sxs-lookup"><span data-stu-id="56504-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="56504-139">大於或等於第二個值是第一個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="56504-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="56504-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="56504-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="56504-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="56504-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="56504-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="56504-143">比較字串</span><span class="sxs-lookup"><span data-stu-id="56504-143">Comparing Strings</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="56504-144">比較字串使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)以及數值比較運算子。</span><span class="sxs-lookup"><span data-stu-id="56504-144"> compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="56504-145">`Like`運算子可讓您指定的模式。</span><span class="sxs-lookup"><span data-stu-id="56504-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="56504-146">字串比較是模式，以及如果相符，則結果是`True`。</span><span class="sxs-lookup"><span data-stu-id="56504-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="56504-147">否則，結果就是`False`。</span><span class="sxs-lookup"><span data-stu-id="56504-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="56504-148">數值運算子可讓您比較`String`值根據其排序次序，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="56504-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="56504-149">在上述範例中的結果是`True`因為第一個字串的第一個字元順序是排在第二個字串的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="56504-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="56504-150">如果第一個字元相同，比較會繼續進行下一個字元，在這兩個字串，依此類推。</span><span class="sxs-lookup"><span data-stu-id="56504-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="56504-151">您也可以測試使用等號比較運算子，如下列範例所示的字串相等。</span><span class="sxs-lookup"><span data-stu-id="56504-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="56504-152">如果某字串是另一個前置詞，例如"aa"和"aaa"，較長的字串視為大於較短的字串。</span><span class="sxs-lookup"><span data-stu-id="56504-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="56504-153">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="56504-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="56504-154">排序順序根據二進位比較或設定而定的文字比較`Option Compare`。</span><span class="sxs-lookup"><span data-stu-id="56504-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="56504-155">如需詳細資訊，請參閱[選項比較陳述式](../../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="56504-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="56504-156">比較物件</span><span class="sxs-lookup"><span data-stu-id="56504-156">Comparing Objects</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="56504-157">比較兩個物件參考變數[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)和[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="56504-157"> compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="56504-158">您可以使用這些運算子來判斷兩個參考變數參考相同的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="56504-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="56504-159">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="56504-159">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="56504-160">[!code-vb[VbVbalrOperators #&65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="56504-160">[!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="56504-161">在上述範例中，`x Is y`評估為`True`，因為這兩個變數參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56504-161">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="56504-162">對照此結果與以下的範例。</span><span class="sxs-lookup"><span data-stu-id="56504-162">Contrast this result with the following example.</span></span>  
  
 <span data-ttu-id="56504-163">[!code-vb[VbVbalrOperators #&66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="56504-163">[!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="56504-164">在上述範例中，`x Is y`評估為`False`，因為它們雖然變數參考相同類型的物件，參考該類型的不同執行個體。</span><span class="sxs-lookup"><span data-stu-id="56504-164">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="56504-165">當您想要測試兩個物件未指向相同的執行個體，`IsNot`運算子可讓您避免文法笨拙的組合`Not`和`Is`。</span><span class="sxs-lookup"><span data-stu-id="56504-165">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="56504-166">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="56504-166">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="56504-167">[!code-vb[VbVbalrOperators #&67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="56504-167">[!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span></span>  
  
 <span data-ttu-id="56504-168">在上述範例中，`If a IsNot b`相當於`If Not a Is b`。</span><span class="sxs-lookup"><span data-stu-id="56504-168">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="56504-169">比較物件型別</span><span class="sxs-lookup"><span data-stu-id="56504-169">Comparing Object Type</span></span>  
 <span data-ttu-id="56504-170">您可以測試物件是否屬於特定型別與`TypeOf`...`Is`運算式。</span><span class="sxs-lookup"><span data-stu-id="56504-170">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="56504-171">語法如下：</span><span class="sxs-lookup"><span data-stu-id="56504-171">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="56504-172">當`typename`指定介面型別，則`TypeOf`...`Is`運算式傳回`True`如果物件實作的介面型別。</span><span class="sxs-lookup"><span data-stu-id="56504-172">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="56504-173">當`typename`是類別型別，則運算式會傳回`True`的物件是否屬於指定的類別或衍生自指定類別的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="56504-173">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="56504-174">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="56504-174">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="56504-175">[!code-vb[VbVbalrOperators #&68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="56504-175">[!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span></span>  
  
 <span data-ttu-id="56504-176">在上述範例中，`TypeOf x Is Control`運算式評估為`True`因為的型別`x`是`Button`，繼承自`Control`。</span><span class="sxs-lookup"><span data-stu-id="56504-176">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="56504-177">如需詳細資訊，請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="56504-177">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56504-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56504-178">See Also</span></span>  
 <span data-ttu-id="56504-179">[值的比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="56504-179">[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="56504-180"> [比較運算子](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="56504-180"> [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="56504-181"> [運算子](../../../../visual-basic/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="56504-181"> [Operators](../../../../visual-basic/language-reference/operators/index.md) </span></span>  
<span data-ttu-id="56504-182"> [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="56504-182"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="56504-183"> [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="56504-183"> [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span></span>  
<span data-ttu-id="56504-184"> [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="56504-184"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
