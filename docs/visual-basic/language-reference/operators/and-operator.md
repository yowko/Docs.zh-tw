---
title: And 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: e14dfd8ba200598084cad04d1faa05f3561f8dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604636"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="09e70-102">And 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09e70-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="09e70-103">在兩個執行邏輯結合`Boolean`運算式或兩個數值運算式的位元結合。</span><span class="sxs-lookup"><span data-stu-id="09e70-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e70-104">語法</span><span class="sxs-lookup"><span data-stu-id="09e70-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="09e70-105">組件</span><span class="sxs-lookup"><span data-stu-id="09e70-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="09e70-106">必要。</span><span class="sxs-lookup"><span data-stu-id="09e70-106">Required.</span></span> <span data-ttu-id="09e70-107">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="09e70-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="09e70-108">布林比較，`result`是邏輯結合兩個`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="09e70-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="09e70-109">位元運算，如`result`是數字的值，表示兩個數值的位元模式位元結合。</span><span class="sxs-lookup"><span data-stu-id="09e70-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="09e70-110">必要。</span><span class="sxs-lookup"><span data-stu-id="09e70-110">Required.</span></span> <span data-ttu-id="09e70-111">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="09e70-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="09e70-112">必要。</span><span class="sxs-lookup"><span data-stu-id="09e70-112">Required.</span></span> <span data-ttu-id="09e70-113">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="09e70-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09e70-114">備註</span><span class="sxs-lookup"><span data-stu-id="09e70-114">Remarks</span></span>  
 <span data-ttu-id="09e70-115">布林比較，`result`是`True`並僅有兩個`expression1`和`expression2`評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="09e70-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="09e70-116">下表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="09e70-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="09e70-117">如果`expression1`是</span><span class="sxs-lookup"><span data-stu-id="09e70-117">If `expression1` is</span></span>|<span data-ttu-id="09e70-118">和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="09e70-118">And `expression2` is</span></span>|<span data-ttu-id="09e70-119">值`result`是</span><span class="sxs-lookup"><span data-stu-id="09e70-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="09e70-120">布林值相較之下，`And`運算子一律會評估這兩個運算式，可能會使程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="09e70-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="09e70-121">[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)執行*最少運算*，這表示如果`expression1`是`False`，然後`expression2`則不會評估。</span><span class="sxs-lookup"><span data-stu-id="09e70-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="09e70-122">當套用至數值，`And`運算子中兩個數值運算式執行位元的比較相同位置的位元並對應中位元設`result`根據下表。</span><span class="sxs-lookup"><span data-stu-id="09e70-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="09e70-123">如果位元`expression1`是</span><span class="sxs-lookup"><span data-stu-id="09e70-123">If bit in `expression1` is</span></span>|<span data-ttu-id="09e70-124">在位元和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="09e70-124">And bit in `expression2` is</span></span>|<span data-ttu-id="09e70-125">中的位元`result`是</span><span class="sxs-lookup"><span data-stu-id="09e70-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="09e70-126">1</span><span class="sxs-lookup"><span data-stu-id="09e70-126">1</span></span>|<span data-ttu-id="09e70-127">1</span><span class="sxs-lookup"><span data-stu-id="09e70-127">1</span></span>|<span data-ttu-id="09e70-128">1</span><span class="sxs-lookup"><span data-stu-id="09e70-128">1</span></span>|  
|<span data-ttu-id="09e70-129">1</span><span class="sxs-lookup"><span data-stu-id="09e70-129">1</span></span>|<span data-ttu-id="09e70-130">0</span><span class="sxs-lookup"><span data-stu-id="09e70-130">0</span></span>|<span data-ttu-id="09e70-131">0</span><span class="sxs-lookup"><span data-stu-id="09e70-131">0</span></span>|  
|<span data-ttu-id="09e70-132">0</span><span class="sxs-lookup"><span data-stu-id="09e70-132">0</span></span>|<span data-ttu-id="09e70-133">1</span><span class="sxs-lookup"><span data-stu-id="09e70-133">1</span></span>|<span data-ttu-id="09e70-134">0</span><span class="sxs-lookup"><span data-stu-id="09e70-134">0</span></span>|  
|<span data-ttu-id="09e70-135">0</span><span class="sxs-lookup"><span data-stu-id="09e70-135">0</span></span>|<span data-ttu-id="09e70-136">0</span><span class="sxs-lookup"><span data-stu-id="09e70-136">0</span></span>|<span data-ttu-id="09e70-137">0</span><span class="sxs-lookup"><span data-stu-id="09e70-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="09e70-138">因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元運算應該用括號，以確保精確的結果。</span><span class="sxs-lookup"><span data-stu-id="09e70-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="09e70-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="09e70-139">Data Types</span></span>  
 <span data-ttu-id="09e70-140">如果運算元組成一個`Boolean`Visual Basic 運算式和一個數值運算式，將轉換`Boolean`為數值運算式 (如 – 1`True`以 0 代表`False`) 和執行位元運算。</span><span class="sxs-lookup"><span data-stu-id="09e70-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="09e70-141">結果的資料型別是布林值的比較， `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="09e70-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="09e70-142">位元的比較，將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="09e70-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="09e70-143">請參閱 「 關聯式和位元比較 」 的表格[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="09e70-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09e70-144">`And`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="09e70-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="09e70-145">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="09e70-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="09e70-146">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="09e70-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e70-147">範例</span><span class="sxs-lookup"><span data-stu-id="09e70-147">Example</span></span>  
 <span data-ttu-id="09e70-148">下列範例會使用`And`運算子執行邏輯結合兩個運算式上。</span><span class="sxs-lookup"><span data-stu-id="09e70-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="09e70-149">結果是`Boolean`值，表示兩個運算式是否`True`。</span><span class="sxs-lookup"><span data-stu-id="09e70-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 <span data-ttu-id="09e70-150">上述範例產生的結果`True`和`False`分別。</span><span class="sxs-lookup"><span data-stu-id="09e70-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e70-151">範例</span><span class="sxs-lookup"><span data-stu-id="09e70-151">Example</span></span>  
 <span data-ttu-id="09e70-152">下列範例會使用`And`運算子執行邏輯結合兩個數值運算式的個別位元。</span><span class="sxs-lookup"><span data-stu-id="09e70-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="09e70-153">如果運算元的對應位元均設定為 1，會設定結果模式中的位元。</span><span class="sxs-lookup"><span data-stu-id="09e70-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 <span data-ttu-id="09e70-154">上述範例中會分別產生 8，2，0，的結果。</span><span class="sxs-lookup"><span data-stu-id="09e70-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e70-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09e70-155">See Also</span></span>  
 [<span data-ttu-id="09e70-156">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09e70-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="09e70-157">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="09e70-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="09e70-158">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="09e70-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="09e70-159">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="09e70-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [<span data-ttu-id="09e70-160">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="09e70-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
