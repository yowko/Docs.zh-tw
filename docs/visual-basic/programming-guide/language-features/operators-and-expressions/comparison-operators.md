---
title: Comparison Operators in Visual Basic
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
ms.openlocfilehash: d08974a929a723d4037300f9d72ae03c072d47fa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826154"
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="eabab-102">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eabab-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="eabab-103">比較運算子比較兩個運算式，並傳回`Boolean`值，表示其值的關聯性。</span><span class="sxs-lookup"><span data-stu-id="eabab-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="eabab-104">有數字值、 運算子來比較字串和運算子來比較物件比較的運算子。</span><span class="sxs-lookup"><span data-stu-id="eabab-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="eabab-105">本文件討論所有的三種類型的運算子。</span><span class="sxs-lookup"><span data-stu-id="eabab-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="eabab-106">比較數值</span><span class="sxs-lookup"><span data-stu-id="eabab-106">Comparing Numeric Values</span></span>  
 <span data-ttu-id="eabab-107">Visual Basic 比較數值資料，請使用六個的數字的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="eabab-107">Visual Basic compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="eabab-108">每個運算子會使用兩個運算式，評估為數值的值做為運算元。</span><span class="sxs-lookup"><span data-stu-id="eabab-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="eabab-109">下表列出的運算子，並顯示每個範例。</span><span class="sxs-lookup"><span data-stu-id="eabab-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="eabab-110">運算子</span><span class="sxs-lookup"><span data-stu-id="eabab-110">Operator</span></span>|<span data-ttu-id="eabab-111">測試條件</span><span class="sxs-lookup"><span data-stu-id="eabab-111">Condition tested</span></span>|<span data-ttu-id="eabab-112">範例</span><span class="sxs-lookup"><span data-stu-id="eabab-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="eabab-113">`=` （相等）</span><span class="sxs-lookup"><span data-stu-id="eabab-113">`=` (Equality)</span></span>|<span data-ttu-id="eabab-114">第二個值是第一個運算式相等的值？</span><span class="sxs-lookup"><span data-stu-id="eabab-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="eabab-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="eabab-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="eabab-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="eabab-118">`<>` （不等）</span><span class="sxs-lookup"><span data-stu-id="eabab-118">`<>` (Inequality)</span></span>|<span data-ttu-id="eabab-119">第一個運算式的值是否不相等的第二個值？</span><span class="sxs-lookup"><span data-stu-id="eabab-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="eabab-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="eabab-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="eabab-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="eabab-123">`<` （小於）</span><span class="sxs-lookup"><span data-stu-id="eabab-123">`<` (Less than)</span></span>|<span data-ttu-id="eabab-124">在第一個運算式的值大於或等於第二個值是？</span><span class="sxs-lookup"><span data-stu-id="eabab-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="eabab-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="eabab-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="eabab-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="eabab-128">`>` （大於）</span><span class="sxs-lookup"><span data-stu-id="eabab-128">`>` (Greater than)</span></span>|<span data-ttu-id="eabab-129">第一個運算式的值是否大於第二個值？</span><span class="sxs-lookup"><span data-stu-id="eabab-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="eabab-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="eabab-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="eabab-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="eabab-133">`<=` （小於或等於）</span><span class="sxs-lookup"><span data-stu-id="eabab-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="eabab-134">小於或等於第二個值是第一個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="eabab-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="eabab-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="eabab-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="eabab-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="eabab-138">`>=` （大於或等於）</span><span class="sxs-lookup"><span data-stu-id="eabab-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="eabab-139">第一個運算式的值是否大於或等於第二個值？</span><span class="sxs-lookup"><span data-stu-id="eabab-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="eabab-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="eabab-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="eabab-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="eabab-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="eabab-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="eabab-143">比較字串</span><span class="sxs-lookup"><span data-stu-id="eabab-143">Comparing Strings</span></span>  
 <span data-ttu-id="eabab-144">Visual Basic 比較字串時，使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)以及數值比較運算子。</span><span class="sxs-lookup"><span data-stu-id="eabab-144">Visual Basic compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="eabab-145">`Like`運算子可讓您指定的模式。</span><span class="sxs-lookup"><span data-stu-id="eabab-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="eabab-146">字串接著會比較該模式，和如果相符，則結果是`True`。</span><span class="sxs-lookup"><span data-stu-id="eabab-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="eabab-147">否則，結果為 `False`。</span><span class="sxs-lookup"><span data-stu-id="eabab-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="eabab-148">數值運算子可讓您比較`String`值根據其排序次序，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="eabab-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="eabab-149">在上述範例中的結果是`True`因為第二個字串的第一個字元之前排序的第一個字串的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="eabab-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="eabab-150">如果第一個字元等於，比較將繼續進行下一個字元，在這兩個字串，等等。</span><span class="sxs-lookup"><span data-stu-id="eabab-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="eabab-151">您也可以測試使用等號比較運算子，如下列範例所示的字串相等。</span><span class="sxs-lookup"><span data-stu-id="eabab-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="eabab-152">如果一個字串是另一個前置詞，例如"aa"和"aaa"，較長的字串視為大於較短的字串。</span><span class="sxs-lookup"><span data-stu-id="eabab-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="eabab-153">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eabab-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="eabab-154">排序次序以二進位比較或根據設定的文字比較為基礎`Option Compare`。</span><span class="sxs-lookup"><span data-stu-id="eabab-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="eabab-155">如需詳細資訊，請參閱[Option 比較陳述式](../../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eabab-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="eabab-156">比較物件</span><span class="sxs-lookup"><span data-stu-id="eabab-156">Comparing Objects</span></span>  
 <span data-ttu-id="eabab-157">Visual Basic 比較兩個物件參考變數[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)並[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="eabab-157">Visual Basic compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="eabab-158">您可以使用這些運算子來判斷兩個參考變數參考相同的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="eabab-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="eabab-159">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eabab-159">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 <span data-ttu-id="eabab-160">在上述範例中，`x Is y`評估為`True`，因為這兩個變數都參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eabab-160">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="eabab-161">比較這個結果與以下的範例。</span><span class="sxs-lookup"><span data-stu-id="eabab-161">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 <span data-ttu-id="eabab-162">在上述範例中，`x Is y`評估為`False`，因為它們雖然變數都參考相同類型的物件，參考該類型的不同執行個體。</span><span class="sxs-lookup"><span data-stu-id="eabab-162">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="eabab-163">當您想要測試兩個物件未指向相同的執行個體，`IsNot`運算子可讓您避免文法笨拙的組合`Not`和`Is`。</span><span class="sxs-lookup"><span data-stu-id="eabab-163">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="eabab-164">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eabab-164">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 <span data-ttu-id="eabab-165">在上述範例中，`If a IsNot b`相當於`If Not a Is b`。</span><span class="sxs-lookup"><span data-stu-id="eabab-165">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="eabab-166">比較的物件類型</span><span class="sxs-lookup"><span data-stu-id="eabab-166">Comparing Object Type</span></span>  
 <span data-ttu-id="eabab-167">您可以測試使用特定類型的物件是否`TypeOf`...`Is`運算式。</span><span class="sxs-lookup"><span data-stu-id="eabab-167">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="eabab-168">語法如下：</span><span class="sxs-lookup"><span data-stu-id="eabab-168">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="eabab-169">當`typename`指定介面型別，則`TypeOf`...`Is`運算式傳回`True`如果物件實作的介面型別。</span><span class="sxs-lookup"><span data-stu-id="eabab-169">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="eabab-170">當`typename`是類別類型，則運算式會傳回`True`的物件是否為指定的類別或衍生自指定類別的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="eabab-170">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="eabab-171">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eabab-171">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 <span data-ttu-id="eabab-172">在上述範例中，`TypeOf x Is Control`運算式會評估`True`因為的型別`x`是`Button`，該項則繼承自`Control`。</span><span class="sxs-lookup"><span data-stu-id="eabab-172">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="eabab-173">如需詳細資訊，請參閱 < [TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="eabab-173">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabab-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eabab-174">See also</span></span>

- [<span data-ttu-id="eabab-175">數值比較</span><span class="sxs-lookup"><span data-stu-id="eabab-175">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="eabab-176">比較運算子</span><span class="sxs-lookup"><span data-stu-id="eabab-176">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="eabab-177">運算子</span><span class="sxs-lookup"><span data-stu-id="eabab-177">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="eabab-178">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="eabab-178">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="eabab-179">在 Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="eabab-179">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [<span data-ttu-id="eabab-180">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="eabab-180">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
