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
ms.openlocfilehash: fbe81532bb435e54e694f9b5fe9dd497392f31e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071764"
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="eff03-102">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eff03-102">Comparison Operators in Visual Basic</span></span>

<span data-ttu-id="eff03-103">比較運算子會比較兩個運算式，並傳回 `Boolean` 值，表示其值的關聯性。</span><span class="sxs-lookup"><span data-stu-id="eff03-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="eff03-104">有一些運算子可比較數值、比較字串的運算子，以及比較物件的運算子。</span><span class="sxs-lookup"><span data-stu-id="eff03-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="eff03-105">本文將討論這三種運算子類型。</span><span class="sxs-lookup"><span data-stu-id="eff03-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="eff03-106">比較數值</span><span class="sxs-lookup"><span data-stu-id="eff03-106">Comparing Numeric Values</span></span>  

 <span data-ttu-id="eff03-107">Visual Basic 使用六個數值比較運算子來比較數值。</span><span class="sxs-lookup"><span data-stu-id="eff03-107">Visual Basic compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="eff03-108">每個運算子都採用兩個評估為數值的運算式做為運算元。</span><span class="sxs-lookup"><span data-stu-id="eff03-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="eff03-109">下表列出這些運算子，並顯示每個運算子的範例。</span><span class="sxs-lookup"><span data-stu-id="eff03-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="eff03-110">運算子</span><span class="sxs-lookup"><span data-stu-id="eff03-110">Operator</span></span>|<span data-ttu-id="eff03-111">測試的條件</span><span class="sxs-lookup"><span data-stu-id="eff03-111">Condition tested</span></span>|<span data-ttu-id="eff03-112">範例</span><span class="sxs-lookup"><span data-stu-id="eff03-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="eff03-113">`=` (相等) </span><span class="sxs-lookup"><span data-stu-id="eff03-113">`=` (Equality)</span></span>|<span data-ttu-id="eff03-114">第一個運算式的值是否等於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="eff03-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="eff03-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="eff03-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="eff03-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="eff03-118">`<>` (不相等) </span><span class="sxs-lookup"><span data-stu-id="eff03-118">`<>` (Inequality)</span></span>|<span data-ttu-id="eff03-119">第一個運算式的值是否不等於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="eff03-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="eff03-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="eff03-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="eff03-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="eff03-123">`<` (小於) </span><span class="sxs-lookup"><span data-stu-id="eff03-123">`<` (Less than)</span></span>|<span data-ttu-id="eff03-124">第一個運算式的值是否小於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="eff03-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="eff03-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="eff03-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="eff03-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="eff03-128">`>` (大於) </span><span class="sxs-lookup"><span data-stu-id="eff03-128">`>` (Greater than)</span></span>|<span data-ttu-id="eff03-129">第一個運算式的值是否大於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="eff03-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="eff03-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="eff03-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="eff03-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="eff03-133">`<=` (小於或等於) </span><span class="sxs-lookup"><span data-stu-id="eff03-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="eff03-134">第一個運算式的值是否小於或等於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="eff03-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="eff03-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="eff03-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="eff03-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="eff03-138">`>=` (大於或等於) </span><span class="sxs-lookup"><span data-stu-id="eff03-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="eff03-139">第一個運算式的值是否大於或等於第二個運算式的值？</span><span class="sxs-lookup"><span data-stu-id="eff03-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="eff03-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="eff03-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="eff03-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="eff03-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="eff03-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="eff03-143">比較字串</span><span class="sxs-lookup"><span data-stu-id="eff03-143">Comparing Strings</span></span>  

 <span data-ttu-id="eff03-144">Visual Basic 使用 [Like 運算子](../../../language-reference/operators/like-operator.md) 以及數值比較運算子來比較字串。</span><span class="sxs-lookup"><span data-stu-id="eff03-144">Visual Basic compares strings using the [Like Operator](../../../language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="eff03-145">`Like`運算子可讓您指定模式。</span><span class="sxs-lookup"><span data-stu-id="eff03-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="eff03-146">然後，此字串會與模式進行比較，如果相符，則結果為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="eff03-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="eff03-147">否則，結果為 `False`。</span><span class="sxs-lookup"><span data-stu-id="eff03-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="eff03-148">數值運算子可讓您 `String` 根據值的排序次序來比較值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="eff03-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="eff03-149">上述範例中的結果是 `True` 因為第一個字串中的第一個字元會在第二個字串的第一個字元之前排序。</span><span class="sxs-lookup"><span data-stu-id="eff03-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="eff03-150">如果第一個字元相等，則比較會繼續進行兩個字串中的下一個字元，依此類推。</span><span class="sxs-lookup"><span data-stu-id="eff03-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="eff03-151">您也可以使用等號比較運算子來測試字串是否相等，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="eff03-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="eff03-152">如果有一個字串是另一個字串的前置詞，例如 "aa" 和 "aaa"，則較長的字串會被視為大於較短的字串。</span><span class="sxs-lookup"><span data-stu-id="eff03-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="eff03-153">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eff03-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="eff03-154">排序次序是根據的設定，以二進位比較或文字比較為基礎 `Option Compare` 。</span><span class="sxs-lookup"><span data-stu-id="eff03-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="eff03-155">如需詳細資訊，請參閱 [Option Compare 語句](../../../language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eff03-155">For more information see [Option Compare Statement](../../../language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="eff03-156">比較物件</span><span class="sxs-lookup"><span data-stu-id="eff03-156">Comparing Objects</span></span>  

 <span data-ttu-id="eff03-157">Visual Basic 會比較兩個物件參考變數與「 [是」運算子](../../../language-reference/operators/is-operator.md) 和 [IsNot 運算子](../../../language-reference/operators/isnot-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="eff03-157">Visual Basic compares two object reference variables with the [Is Operator](../../../language-reference/operators/is-operator.md) and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="eff03-158">您可以使用其中一個運算子來判斷兩個參考變數是否參考相同的物件實例。</span><span class="sxs-lookup"><span data-stu-id="eff03-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="eff03-159">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eff03-159">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 <span data-ttu-id="eff03-160">在上述範例中，會 `x Is y` 評估為 `True` ，因為這兩個變數都參考相同的實例。</span><span class="sxs-lookup"><span data-stu-id="eff03-160">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="eff03-161">將此結果與下列範例做比較。</span><span class="sxs-lookup"><span data-stu-id="eff03-161">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 <span data-ttu-id="eff03-162">在上述範例中， `x Is y` 會評估為 `False` ，因為雖然變數參考相同類型的物件，但它們參考該類型的不同實例。</span><span class="sxs-lookup"><span data-stu-id="eff03-162">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="eff03-163">當您想要測試兩個未指向相同實例的物件時， `IsNot` 運算子可讓您避免和的文法笨拙組合 `Not` `Is` 。</span><span class="sxs-lookup"><span data-stu-id="eff03-163">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="eff03-164">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eff03-164">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 <span data-ttu-id="eff03-165">在上述範例中， `If a IsNot b` 相當於 `If Not a Is b` 。</span><span class="sxs-lookup"><span data-stu-id="eff03-165">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="eff03-166">比較物件類型</span><span class="sxs-lookup"><span data-stu-id="eff03-166">Comparing Object Type</span></span>  

 <span data-ttu-id="eff03-167">您可以使用 `TypeOf` ... 運算式測試物件是否為特定類型。 `Is`</span><span class="sxs-lookup"><span data-stu-id="eff03-167">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="eff03-168">語法如下：</span><span class="sxs-lookup"><span data-stu-id="eff03-168">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="eff03-169">當 `typename` 指定介面類別型時，如果物件會執行介面型別，則會傳回 `TypeOf` ... `Is` 運算式。 `True`</span><span class="sxs-lookup"><span data-stu-id="eff03-169">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="eff03-170">當 `typename` 是類別型別時， `True` 如果物件是指定類別的實例或衍生自指定類別的類別，則運算式會傳回。</span><span class="sxs-lookup"><span data-stu-id="eff03-170">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="eff03-171">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eff03-171">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 <span data-ttu-id="eff03-172">在上述範例中， `TypeOf x Is Control` 運算式會評估為 `True` ，因為的型別 `x` 是 `Button` ，它會繼承自 `Control` 。</span><span class="sxs-lookup"><span data-stu-id="eff03-172">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="eff03-173">如需詳細資訊，請參閱 [TypeOf 運算子](../../../language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="eff03-173">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff03-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eff03-174">See also</span></span>

- [<span data-ttu-id="eff03-175">數值比較</span><span class="sxs-lookup"><span data-stu-id="eff03-175">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="eff03-176">比較運算子</span><span class="sxs-lookup"><span data-stu-id="eff03-176">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="eff03-177">運算子</span><span class="sxs-lookup"><span data-stu-id="eff03-177">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="eff03-178">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="eff03-178">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="eff03-179">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="eff03-179">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="eff03-180">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="eff03-180">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
