---
title: 比較運算子
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
ms.openlocfilehash: ea7604626ede66da818e4bc22fe4922bc752dc2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336076"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="d56d5-102">比較運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56d5-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="d56d5-103">以下是在 Visual Basic 中定義的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="d56d5-103">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="d56d5-104">`<` 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-104">`<` operator</span></span>

 <span data-ttu-id="d56d5-105">`<=` 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-105">`<=` operator</span></span>

 <span data-ttu-id="d56d5-106">`>` 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-106">`>` operator</span></span>

 <span data-ttu-id="d56d5-107">`>=` 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-107">`>=` operator</span></span>

 <span data-ttu-id="d56d5-108">`=` 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-108">`=` operator</span></span>

 <span data-ttu-id="d56d5-109">`<>` 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-109">`<>` operator</span></span>

 [<span data-ttu-id="d56d5-110">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)

 [<span data-ttu-id="d56d5-111">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [<span data-ttu-id="d56d5-112">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)

 <span data-ttu-id="d56d5-113">這些運算子會比較兩個運算式，以判斷它們是否相等，如果不是，則會有何差異。</span><span class="sxs-lookup"><span data-stu-id="d56d5-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="d56d5-114">`Is`、`IsNot`和 `Like` 會在個別的 [說明] 頁面中詳細討論。</span><span class="sxs-lookup"><span data-stu-id="d56d5-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="d56d5-115">本頁面會詳細討論關聯式比較運算子。</span><span class="sxs-lookup"><span data-stu-id="d56d5-115">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="d56d5-116">語法</span><span class="sxs-lookup"><span data-stu-id="d56d5-116">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="d56d5-117">組件</span><span class="sxs-lookup"><span data-stu-id="d56d5-117">Parts</span></span>
 `result`  
 <span data-ttu-id="d56d5-118">必要。</span><span class="sxs-lookup"><span data-stu-id="d56d5-118">Required.</span></span> <span data-ttu-id="d56d5-119">`Boolean` 值，表示比較的結果。</span><span class="sxs-lookup"><span data-stu-id="d56d5-119">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="d56d5-120">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="d56d5-120">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="d56d5-121">必要。</span><span class="sxs-lookup"><span data-stu-id="d56d5-121">Required.</span></span> <span data-ttu-id="d56d5-122">任何運算式。</span><span class="sxs-lookup"><span data-stu-id="d56d5-122">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="d56d5-123">必要。</span><span class="sxs-lookup"><span data-stu-id="d56d5-123">Required.</span></span> <span data-ttu-id="d56d5-124">任何關聯式比較運算子。</span><span class="sxs-lookup"><span data-stu-id="d56d5-124">Any relational comparison operator.</span></span>

 <span data-ttu-id="d56d5-125">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="d56d5-125">`object1`, `object2`</span></span>  
 <span data-ttu-id="d56d5-126">必要。</span><span class="sxs-lookup"><span data-stu-id="d56d5-126">Required.</span></span> <span data-ttu-id="d56d5-127">任何參考物件名稱。</span><span class="sxs-lookup"><span data-stu-id="d56d5-127">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="d56d5-128">必要。</span><span class="sxs-lookup"><span data-stu-id="d56d5-128">Required.</span></span> <span data-ttu-id="d56d5-129">任何 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d56d5-129">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="d56d5-130">必要。</span><span class="sxs-lookup"><span data-stu-id="d56d5-130">Required.</span></span> <span data-ttu-id="d56d5-131">任何 `String` 的運算式或字元範圍。</span><span class="sxs-lookup"><span data-stu-id="d56d5-131">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="d56d5-132">備註</span><span class="sxs-lookup"><span data-stu-id="d56d5-132">Remarks</span></span>
 <span data-ttu-id="d56d5-133">下表包含關聯式比較運算子的清單，以及判斷 `result` `True` 或 `False`的條件。</span><span class="sxs-lookup"><span data-stu-id="d56d5-133">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="d56d5-134">運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-134">Operator</span></span>|<span data-ttu-id="d56d5-135">`True` -</span><span class="sxs-lookup"><span data-stu-id="d56d5-135">`True` if</span></span>|<span data-ttu-id="d56d5-136">`False` -</span><span class="sxs-lookup"><span data-stu-id="d56d5-136">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="d56d5-137">`<` （小於）</span><span class="sxs-lookup"><span data-stu-id="d56d5-137">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="d56d5-138">`<=` （小於或等於）</span><span class="sxs-lookup"><span data-stu-id="d56d5-138">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="d56d5-139">`>` （大於）</span><span class="sxs-lookup"><span data-stu-id="d56d5-139">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="d56d5-140">`>=` （大於或等於）</span><span class="sxs-lookup"><span data-stu-id="d56d5-140">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="d56d5-141">`=` （等於）</span><span class="sxs-lookup"><span data-stu-id="d56d5-141">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="d56d5-142">`<>` （不等於）</span><span class="sxs-lookup"><span data-stu-id="d56d5-142">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="d56d5-143">[= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)也會用來做為指派運算子。</span><span class="sxs-lookup"><span data-stu-id="d56d5-143">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="d56d5-144">`Is` 運算子、`IsNot` 運算子和 `Like` 運算子具有與上表中運算子不同的特定比較功能。</span><span class="sxs-lookup"><span data-stu-id="d56d5-144">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="d56d5-145">比較數位</span><span class="sxs-lookup"><span data-stu-id="d56d5-145">Comparing Numbers</span></span>
 <span data-ttu-id="d56d5-146">當您比較類型 `Single` 的運算式與 `Double`類型之一時，`Single` 運算式會轉換成 `Double`。</span><span class="sxs-lookup"><span data-stu-id="d56d5-146">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="d56d5-147">這種行為與 Visual Basic 6 中找到的行為相反。</span><span class="sxs-lookup"><span data-stu-id="d56d5-147">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="d56d5-148">同樣地，當您將類型 `Decimal` 的運算式與 `Single` 或 `Double`類型的運算式進行比較時，`Decimal` 運算式會轉換成 `Single` 或 `Double`。</span><span class="sxs-lookup"><span data-stu-id="d56d5-148">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="d56d5-149">對於 `Decimal` 運算式，小於 1E-28 的任何小數值可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="d56d5-149">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="d56d5-150">這類小數值遺失可能會導致兩個值在不相等時進行比較。</span><span class="sxs-lookup"><span data-stu-id="d56d5-150">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="d56d5-151">基於這個理由，您應該在使用相等（`=`）來比較兩個浮點變數時特別小心。</span><span class="sxs-lookup"><span data-stu-id="d56d5-151">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="d56d5-152">測試兩個數字之間的差值絕對值是否小於較小的可接受容錯，是比較安全的作法。</span><span class="sxs-lookup"><span data-stu-id="d56d5-152">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="d56d5-153">浮點不精確</span><span class="sxs-lookup"><span data-stu-id="d56d5-153">Floating-point Imprecision</span></span>
 <span data-ttu-id="d56d5-154">當您使用浮點數時，請記住它們不一定會在記憶體中有精確的標記法。</span><span class="sxs-lookup"><span data-stu-id="d56d5-154">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="d56d5-155">這可能會導致某些作業產生非預期的結果，例如值比較和[Mod 運算子](../../../visual-basic/language-reference/operators/mod-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="d56d5-155">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="d56d5-156">如需詳細資訊，請參閱針對[資料類型進行疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d56d5-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="d56d5-157">比較字串</span><span class="sxs-lookup"><span data-stu-id="d56d5-157">Comparing Strings</span></span>
 <span data-ttu-id="d56d5-158">當您比較字串時，字串運算式會根據其順序排序次序進行評估，這取決於 `Option Compare` 設定。</span><span class="sxs-lookup"><span data-stu-id="d56d5-158">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="d56d5-159">`Option Compare Binary` 根據從字元的內部二進位標記法衍生的排序次序來進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="d56d5-159">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="d56d5-160">排序次序是由字碼頁所決定。</span><span class="sxs-lookup"><span data-stu-id="d56d5-160">The sort order is determined by the code page.</span></span> <span data-ttu-id="d56d5-161">下列範例顯示典型的二進位排序次序。</span><span class="sxs-lookup"><span data-stu-id="d56d5-161">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="d56d5-162">`Option Compare Text` 根據您應用程式的地區設定所決定的區分大小寫、文字排序次序來進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="d56d5-162">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="d56d5-163">當您設定 `Option Compare Text` 並排序上述範例中的字元時，會套用下列文字排序次序：</span><span class="sxs-lookup"><span data-stu-id="d56d5-163">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="d56d5-164">地區設定相關性</span><span class="sxs-lookup"><span data-stu-id="d56d5-164">Locale Dependence</span></span>
 <span data-ttu-id="d56d5-165">當您設定 `Option Compare Text`時，字串比較的結果可能取決於應用程式執行所在的地區設定。</span><span class="sxs-lookup"><span data-stu-id="d56d5-165">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="d56d5-166">在一個地區設定中，兩個字元可能會比較成相等，但另一個則不會。</span><span class="sxs-lookup"><span data-stu-id="d56d5-166">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="d56d5-167">如果您使用字串比較來做出重要決策，例如是否要接受登入的嘗試，您應該會在區分地區設定的情況下發出警示。</span><span class="sxs-lookup"><span data-stu-id="d56d5-167">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="d56d5-168">請考慮設定 `Option Compare Binary` 或呼叫 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>，這會將地區設定納入考慮。</span><span class="sxs-lookup"><span data-stu-id="d56d5-168">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="d56d5-169">使用關聯式比較運算子進行無程式設計</span><span class="sxs-lookup"><span data-stu-id="d56d5-169">Typeless Programming with Relational Comparison Operators</span></span>
 <span data-ttu-id="d56d5-170">在 `Option Strict On`下，不允許使用具有 `Object` 運算式的關聯式比較運算子。</span><span class="sxs-lookup"><span data-stu-id="d56d5-170">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="d56d5-171">當 `Option Strict` `Off`，且 `expression1` 或 `expression2` 是 `Object` 運算式時，執行時間類型會決定它們的比較方式。</span><span class="sxs-lookup"><span data-stu-id="d56d5-171">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="d56d5-172">下表顯示如何比較運算式和比較的結果，端視運算元的執行時間類型而定。</span><span class="sxs-lookup"><span data-stu-id="d56d5-172">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="d56d5-173">如果運算元為</span><span class="sxs-lookup"><span data-stu-id="d56d5-173">If operands are</span></span>|<span data-ttu-id="d56d5-174">比較</span><span class="sxs-lookup"><span data-stu-id="d56d5-174">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="d56d5-175">兩者 `String`</span><span class="sxs-lookup"><span data-stu-id="d56d5-175">Both `String`</span></span>|<span data-ttu-id="d56d5-176">根據字串排序特性排序比較。</span><span class="sxs-lookup"><span data-stu-id="d56d5-176">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="d56d5-177">兩者都是數值</span><span class="sxs-lookup"><span data-stu-id="d56d5-177">Both numeric</span></span>|<span data-ttu-id="d56d5-178">轉換成 `Double`，數值比較的物件。</span><span class="sxs-lookup"><span data-stu-id="d56d5-178">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="d56d5-179">一個數位和一個 `String`</span><span class="sxs-lookup"><span data-stu-id="d56d5-179">One numeric and one `String`</span></span>|<span data-ttu-id="d56d5-180">`String` 會轉換成 `Double` 並執行數值比較。</span><span class="sxs-lookup"><span data-stu-id="d56d5-180">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="d56d5-181">如果 `String` 無法轉換成 `Double`，則會擲回 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="d56d5-181">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="d56d5-182">或兩者都是以外的參考型別 `String`</span><span class="sxs-lookup"><span data-stu-id="d56d5-182">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="d56d5-183">擲回 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="d56d5-183">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="d56d5-184">數值比較會將 `Nothing` 視為0。</span><span class="sxs-lookup"><span data-stu-id="d56d5-184">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="d56d5-185">字串比較會將 `Nothing` 視為 `""` （空字串）。</span><span class="sxs-lookup"><span data-stu-id="d56d5-185">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="d56d5-186">多載化</span><span class="sxs-lookup"><span data-stu-id="d56d5-186">Overloading</span></span>
 <span data-ttu-id="d56d5-187">關聯式比較運算子（`<`。</span><span class="sxs-lookup"><span data-stu-id="d56d5-187">The relational comparison operators (`<`.</span></span> <span data-ttu-id="d56d5-188">`<=`、`>`、`>=`、`=`、`<>`）可以多*載，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="d56d5-188">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d56d5-189">如果您的程式碼在這類類別或結構上使用上述任何運算子，請務必瞭解已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="d56d5-189">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="d56d5-190">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d56d5-190">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="d56d5-191">請注意， [= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)只能多載為關聯式比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="d56d5-191">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="d56d5-192">範例</span><span class="sxs-lookup"><span data-stu-id="d56d5-192">Example</span></span>
 <span data-ttu-id="d56d5-193">下列範例顯示關聯式比較運算子的各種用法，您可以用來比較運算式。</span><span class="sxs-lookup"><span data-stu-id="d56d5-193">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="d56d5-194">關聯式比較運算子會傳回 `Boolean` 的結果，表示指定的運算式是否評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="d56d5-194">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="d56d5-195">當您將 `>` 和 `<` 運算子套用至字串時，會使用字串的一般字母順序排序來進行比較。</span><span class="sxs-lookup"><span data-stu-id="d56d5-195">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="d56d5-196">此順序可能取決於您的地區設定。</span><span class="sxs-lookup"><span data-stu-id="d56d5-196">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="d56d5-197">排序是否區分大小寫，或不取決於 [[選項比較](../../../visual-basic/language-reference/statements/option-compare-statement.md)] 設定。</span><span class="sxs-lookup"><span data-stu-id="d56d5-197">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="d56d5-198">在上述範例中，第一個比較會傳回 `False`，而其餘的比較會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="d56d5-198">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d56d5-199">請參閱</span><span class="sxs-lookup"><span data-stu-id="d56d5-199">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="d56d5-200">= 運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-200">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="d56d5-201">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="d56d5-201">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d56d5-202">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="d56d5-202">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d56d5-203">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="d56d5-203">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="d56d5-204">Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="d56d5-204">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
