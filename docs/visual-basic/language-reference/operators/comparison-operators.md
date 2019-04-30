---
title: 比較運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 9014cac5e2f3933b27411dfe5681fc16f4cdde30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013578"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="09e65-102">比較運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09e65-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="09e65-103">以下是定義在 Visual Basic 中的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="09e65-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="09e65-104">`<` 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-104">`<` operator</span></span>  
  
 <span data-ttu-id="09e65-105">`<=` 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-105">`<=` operator</span></span>  
  
 <span data-ttu-id="09e65-106">`>` 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-106">`>` operator</span></span>  
  
 <span data-ttu-id="09e65-107">`>=` 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-107">`>=` operator</span></span>  
  
 <span data-ttu-id="09e65-108">`=` 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-108">`=` operator</span></span>  
  
 <span data-ttu-id="09e65-109">`<>` 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="09e65-110">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="09e65-111">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="09e65-112">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="09e65-113">這些運算子比較兩個運算式，以判斷相等，以及如果不是，它們之間的差異。</span><span class="sxs-lookup"><span data-stu-id="09e65-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="09e65-114">`Is``IsNot`，和`Like`會詳細討論個別的 [說明] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="09e65-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="09e65-115">關係比較運算子會詳細討論此頁面上。</span><span class="sxs-lookup"><span data-stu-id="09e65-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e65-116">語法</span><span class="sxs-lookup"><span data-stu-id="09e65-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="09e65-117">組件</span><span class="sxs-lookup"><span data-stu-id="09e65-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="09e65-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="09e65-118">Required.</span></span> <span data-ttu-id="09e65-119">A`Boolean`值，代表比較的結果。</span><span class="sxs-lookup"><span data-stu-id="09e65-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="09e65-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="09e65-120">Required.</span></span> <span data-ttu-id="09e65-121">任何運算式。</span><span class="sxs-lookup"><span data-stu-id="09e65-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="09e65-122">必要項。</span><span class="sxs-lookup"><span data-stu-id="09e65-122">Required.</span></span> <span data-ttu-id="09e65-123">任何關係比較運算子。</span><span class="sxs-lookup"><span data-stu-id="09e65-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="09e65-124">`object1`、 `object2`</span><span class="sxs-lookup"><span data-stu-id="09e65-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="09e65-125">必要項。</span><span class="sxs-lookup"><span data-stu-id="09e65-125">Required.</span></span> <span data-ttu-id="09e65-126">任何參考的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="09e65-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="09e65-127">必要項。</span><span class="sxs-lookup"><span data-stu-id="09e65-127">Required.</span></span> <span data-ttu-id="09e65-128">任何 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="09e65-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="09e65-129">必要項。</span><span class="sxs-lookup"><span data-stu-id="09e65-129">Required.</span></span> <span data-ttu-id="09e65-130">任何`String`運算式或字元範圍。</span><span class="sxs-lookup"><span data-stu-id="09e65-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09e65-131">備註</span><span class="sxs-lookup"><span data-stu-id="09e65-131">Remarks</span></span>  
 <span data-ttu-id="09e65-132">下表包含一份關係比較運算子和條件，以便判斷是否`result`已`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="09e65-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="09e65-133">運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-133">Operator</span></span>|<span data-ttu-id="09e65-134">`True` - </span><span class="sxs-lookup"><span data-stu-id="09e65-134">`True` if</span></span>|<span data-ttu-id="09e65-135">`False` - </span><span class="sxs-lookup"><span data-stu-id="09e65-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="09e65-136">`<` （小於）</span><span class="sxs-lookup"><span data-stu-id="09e65-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="09e65-137">`<=` （小於或等於）</span><span class="sxs-lookup"><span data-stu-id="09e65-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="09e65-138">`>` （大於）</span><span class="sxs-lookup"><span data-stu-id="09e65-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="09e65-139">`>=` （大於或等於）</span><span class="sxs-lookup"><span data-stu-id="09e65-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="09e65-140">`=` （等於）</span><span class="sxs-lookup"><span data-stu-id="09e65-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="09e65-141">`<>` （不等於）</span><span class="sxs-lookup"><span data-stu-id="09e65-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="09e65-142">[= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)也會為指派運算子。</span><span class="sxs-lookup"><span data-stu-id="09e65-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="09e65-143">`Is`運算子`IsNot`運算子，而`Like`運算子有特定的比較功能不同於上表中的運算子。</span><span class="sxs-lookup"><span data-stu-id="09e65-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="09e65-144">比較數字</span><span class="sxs-lookup"><span data-stu-id="09e65-144">Comparing Numbers</span></span>  
 <span data-ttu-id="09e65-145">當您比較類型的運算式`Single`類型的其中一個`Double`，則`Single`運算式轉換成`Double`。</span><span class="sxs-lookup"><span data-stu-id="09e65-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="09e65-146">此行為是相對於容量中 Visual Basic 6 的行為。</span><span class="sxs-lookup"><span data-stu-id="09e65-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="09e65-147">同樣地，當您比較類型的運算式`Decimal`類型的運算式來`Single`或`Double`，則`Decimal`運算式轉換成`Single`或`Double`。</span><span class="sxs-lookup"><span data-stu-id="09e65-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="09e65-148">針對`Decimal`運算式中，任何小數的值小於 1E 28 可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="09e65-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="09e65-149">這類分數值遺失可能會導致兩個值以比較為相等，前提是它們並非。</span><span class="sxs-lookup"><span data-stu-id="09e65-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="09e65-150">基於這個理由，您應謹慎使用等號比較時 (`=`) 比較兩個浮點變數。</span><span class="sxs-lookup"><span data-stu-id="09e65-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="09e65-151">它會比較安全來測試是否兩個數字之間差異的絕對值小於小型的可接受容錯。</span><span class="sxs-lookup"><span data-stu-id="09e65-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="09e65-152">浮點數不精確</span><span class="sxs-lookup"><span data-stu-id="09e65-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="09e65-153">當您使用浮點數時，記住其在記憶體中不一定有精確的表示法。</span><span class="sxs-lookup"><span data-stu-id="09e65-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="09e65-154">這可能會導致非預期的結果從某些作業，例如要做數值比較， [Mod 運算子](../../../visual-basic/language-reference/operators/mod-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="09e65-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="09e65-155">如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="09e65-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="09e65-156">比較字串</span><span class="sxs-lookup"><span data-stu-id="09e65-156">Comparing Strings</span></span>  
 <span data-ttu-id="09e65-157">當您比較字串時，字串運算式評估是根據其依字母順序排列的排序順序，這取決於`Option Compare`設定。</span><span class="sxs-lookup"><span data-stu-id="09e65-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="09e65-158">`Option Compare Binary` 基底的字串比較，在排序次序，衍生自內部的二進位表示的字元。</span><span class="sxs-lookup"><span data-stu-id="09e65-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="09e65-159">排序次序取決於字碼頁。</span><span class="sxs-lookup"><span data-stu-id="09e65-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="09e65-160">下列範例會示範一般的二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="09e65-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="09e65-161">`Option Compare Text` 基底的字串比較不區分大小寫、 文字排序順序取決於您的應用程式地區設定。</span><span class="sxs-lookup"><span data-stu-id="09e65-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="09e65-162">當您將設定`Option Compare Text`和排序在上述範例中的字元，請套用下列的文字排序順序：</span><span class="sxs-lookup"><span data-stu-id="09e65-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="09e65-163">地區設定相依性</span><span class="sxs-lookup"><span data-stu-id="09e65-163">Locale Dependence</span></span>  
 <span data-ttu-id="09e65-164">當您將設定`Option Compare Text`，則字串比較的結果可能取決於應用程式執行所在的地區設定。</span><span class="sxs-lookup"><span data-stu-id="09e65-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="09e65-165">兩個字元可能會比較為相等，在一個地區設定，但不是在另一個。</span><span class="sxs-lookup"><span data-stu-id="09e65-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="09e65-166">如果您使用的字串比較做出重要決定，例如是否將接受嘗試登入，您應該要區分地區設定的警示。</span><span class="sxs-lookup"><span data-stu-id="09e65-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="09e65-167">其中一個設定，請考慮`Option Compare Binary`或呼叫<xref:Microsoft.VisualBasic.Strings.StrComp%2A>，它接受地區設定列入考量。</span><span class="sxs-lookup"><span data-stu-id="09e65-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="09e65-168">關係比較運算子的無類型程式設計</span><span class="sxs-lookup"><span data-stu-id="09e65-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="09e65-169">關係比較運算子的用法`Object`下，不允許運算式`Option Strict On`。</span><span class="sxs-lookup"><span data-stu-id="09e65-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="09e65-170">當`Option Strict`是`Off`，以及`expression1`或`expression2`是`Object`運算式中，執行階段類型可讓您決定如何比較。</span><span class="sxs-lookup"><span data-stu-id="09e65-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="09e65-171">下表顯示如何比較運算式和相較之下，根據執行階段類型的運算元的結果。</span><span class="sxs-lookup"><span data-stu-id="09e65-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="09e65-172">如果運算元都是</span><span class="sxs-lookup"><span data-stu-id="09e65-172">If operands are</span></span>|<span data-ttu-id="09e65-173">比較</span><span class="sxs-lookup"><span data-stu-id="09e65-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="09e65-174">兩者 `String`</span><span class="sxs-lookup"><span data-stu-id="09e65-174">Both `String`</span></span>|<span data-ttu-id="09e65-175">排序依據排序特性的字串比較。</span><span class="sxs-lookup"><span data-stu-id="09e65-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="09e65-176">這兩個數值</span><span class="sxs-lookup"><span data-stu-id="09e65-176">Both numeric</span></span>|<span data-ttu-id="09e65-177">物件轉換成`Double`，數值比較。</span><span class="sxs-lookup"><span data-stu-id="09e65-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="09e65-178">一個數值，另一個 `String`</span><span class="sxs-lookup"><span data-stu-id="09e65-178">One numeric and one `String`</span></span>|<span data-ttu-id="09e65-179">`String`轉換成`Double`而且會執行數值的比較。</span><span class="sxs-lookup"><span data-stu-id="09e65-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="09e65-180">如果`String`無法轉換成`Double`、<xref:System.InvalidCastException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="09e65-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="09e65-181">其中之一或兩者是以外的參考型別 `String`</span><span class="sxs-lookup"><span data-stu-id="09e65-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="09e65-182">擲回 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="09e65-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="09e65-183">將數字比較`Nothing`為 0。</span><span class="sxs-lookup"><span data-stu-id="09e65-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="09e65-184">字串比較視為`Nothing`做為`""`（空字串）。</span><span class="sxs-lookup"><span data-stu-id="09e65-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="09e65-185">多載化</span><span class="sxs-lookup"><span data-stu-id="09e65-185">Overloading</span></span>  
 <span data-ttu-id="09e65-186">關係比較運算子 (`<`。</span><span class="sxs-lookup"><span data-stu-id="09e65-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="09e65-187">`<=``>`， `>=`， `=`， `<>`) 可以*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="09e65-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="09e65-188">如果您的程式碼會使用這些運算子的任何這類類別或結構上，請確定您了解重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="09e65-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="09e65-189">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="09e65-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="09e65-190">請注意， [= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)僅做為關係比較運算子，而非指派運算子可以多載。</span><span class="sxs-lookup"><span data-stu-id="09e65-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e65-191">範例</span><span class="sxs-lookup"><span data-stu-id="09e65-191">Example</span></span>  
 <span data-ttu-id="09e65-192">下列範例顯示各種關係比較運算子，用來比較運算式的用法。</span><span class="sxs-lookup"><span data-stu-id="09e65-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="09e65-193">關係比較運算子會傳回`Boolean`結果，表示是否在指定的運算式評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="09e65-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="09e65-194">當您套用`>`和`<`運算子為字串，則會進行比較之字串的一般依字母順序排序的順序，使用。</span><span class="sxs-lookup"><span data-stu-id="09e65-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="09e65-195">此順序可能會取決於您的地區設定的。</span><span class="sxs-lookup"><span data-stu-id="09e65-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="09e65-196">排序是否會區分大小寫取決於[Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)設定。</span><span class="sxs-lookup"><span data-stu-id="09e65-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 <span data-ttu-id="09e65-197">在上述範例中，第一個比較會傳回`False`以及剩餘的比較都會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="09e65-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e65-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09e65-198">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="09e65-199">= 運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="09e65-200">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="09e65-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="09e65-201">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="09e65-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="09e65-202">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="09e65-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="09e65-203">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="09e65-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
