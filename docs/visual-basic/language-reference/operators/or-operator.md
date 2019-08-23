---
title: Or 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955845"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="80d32-102">Or 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80d32-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="80d32-103">在兩個`Boolean`運算式上執行邏輯分離, 或在兩個數值運算式上執行位析取。</span><span class="sxs-lookup"><span data-stu-id="80d32-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d32-104">語法</span><span class="sxs-lookup"><span data-stu-id="80d32-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="80d32-105">組件</span><span class="sxs-lookup"><span data-stu-id="80d32-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="80d32-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="80d32-106">Required.</span></span> <span data-ttu-id="80d32-107">Any `Boolean`或 numeric 運算式。</span><span class="sxs-lookup"><span data-stu-id="80d32-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="80d32-108">為了`Boolean`進行比較`result` , 是兩個`Boolean`值的內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="80d32-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="80d32-109">對於位運算而言`result` , 是代表兩個數值位模式之內含位分離的數值。</span><span class="sxs-lookup"><span data-stu-id="80d32-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="80d32-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="80d32-110">Required.</span></span> <span data-ttu-id="80d32-111">Any `Boolean`或 numeric 運算式。</span><span class="sxs-lookup"><span data-stu-id="80d32-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="80d32-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="80d32-112">Required.</span></span> <span data-ttu-id="80d32-113">Any `Boolean`或 numeric 運算式。</span><span class="sxs-lookup"><span data-stu-id="80d32-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80d32-114">備註</span><span class="sxs-lookup"><span data-stu-id="80d32-114">Remarks</span></span>  
 <span data-ttu-id="80d32-115">為了`Boolean`進行比較`result` `expression1` ,只有和`expression2`都評估為`False`時才為。 `False`</span><span class="sxs-lookup"><span data-stu-id="80d32-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="80d32-116">下表說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="80d32-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="80d32-117">如果`expression1`為</span><span class="sxs-lookup"><span data-stu-id="80d32-117">If `expression1` is</span></span>|<span data-ttu-id="80d32-118">和`expression2`為</span><span class="sxs-lookup"><span data-stu-id="80d32-118">And `expression2` is</span></span>|<span data-ttu-id="80d32-119">的值`result`為</span><span class="sxs-lookup"><span data-stu-id="80d32-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="80d32-120">在比較中`Or` , 運算子一律會評估兩個運算式, 這可能包括進行程序呼叫。 `Boolean`</span><span class="sxs-lookup"><span data-stu-id="80d32-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="80d32-121">[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)會執行最少運算, 這表示如果`expression1`為`True`, `expression2`則不會評估。</span><span class="sxs-lookup"><span data-stu-id="80d32-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="80d32-122">對於位運算, `Or`運算子會在兩個數值運算式中執行相同位置位的位比較, 並根據下表設定中`result`的對應位。</span><span class="sxs-lookup"><span data-stu-id="80d32-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="80d32-123">如果中的`expression1`位是</span><span class="sxs-lookup"><span data-stu-id="80d32-123">If bit in `expression1` is</span></span>|<span data-ttu-id="80d32-124">中的`expression2`和位為</span><span class="sxs-lookup"><span data-stu-id="80d32-124">And bit in `expression2` is</span></span>|<span data-ttu-id="80d32-125">中`result`的位是</span><span class="sxs-lookup"><span data-stu-id="80d32-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="80d32-126">1</span><span class="sxs-lookup"><span data-stu-id="80d32-126">1</span></span>|<span data-ttu-id="80d32-127">1</span><span class="sxs-lookup"><span data-stu-id="80d32-127">1</span></span>|<span data-ttu-id="80d32-128">1</span><span class="sxs-lookup"><span data-stu-id="80d32-128">1</span></span>|  
|<span data-ttu-id="80d32-129">1</span><span class="sxs-lookup"><span data-stu-id="80d32-129">1</span></span>|<span data-ttu-id="80d32-130">0</span><span class="sxs-lookup"><span data-stu-id="80d32-130">0</span></span>|<span data-ttu-id="80d32-131">1</span><span class="sxs-lookup"><span data-stu-id="80d32-131">1</span></span>|  
|<span data-ttu-id="80d32-132">0</span><span class="sxs-lookup"><span data-stu-id="80d32-132">0</span></span>|<span data-ttu-id="80d32-133">1</span><span class="sxs-lookup"><span data-stu-id="80d32-133">1</span></span>|<span data-ttu-id="80d32-134">1</span><span class="sxs-lookup"><span data-stu-id="80d32-134">1</span></span>|  
|<span data-ttu-id="80d32-135">0</span><span class="sxs-lookup"><span data-stu-id="80d32-135">0</span></span>|<span data-ttu-id="80d32-136">0</span><span class="sxs-lookup"><span data-stu-id="80d32-136">0</span></span>|<span data-ttu-id="80d32-137">0</span><span class="sxs-lookup"><span data-stu-id="80d32-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="80d32-138">由於邏輯和位運算子的優先順序比其他算術和關係運算子低, 因此應該將任何位運算括在括弧中, 以確保正確執行。</span><span class="sxs-lookup"><span data-stu-id="80d32-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="80d32-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="80d32-139">Data Types</span></span>  
 <span data-ttu-id="80d32-140">如果運算元是由`Boolean`一個運算式和一個數值運算式所組成, Visual Basic 會`Boolean`將運算式轉換為數值 (-1 代表`True` , 0 則代表`False`), 並執行位運算。</span><span class="sxs-lookup"><span data-stu-id="80d32-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="80d32-141">為了進行`Boolean`比較, 結果的資料類型是。 `Boolean`</span><span class="sxs-lookup"><span data-stu-id="80d32-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="80d32-142">針對位比較, 結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="80d32-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="80d32-143">請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。</span><span class="sxs-lookup"><span data-stu-id="80d32-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="80d32-144">多載化</span><span class="sxs-lookup"><span data-stu-id="80d32-144">Overloading</span></span>  
 <span data-ttu-id="80d32-145">運算子可以多載, 這表示當運算元具有該類別或結構的類型時, 類別或結構可以重新定義其行為。 `Or`</span><span class="sxs-lookup"><span data-stu-id="80d32-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="80d32-146">如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="80d32-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="80d32-147">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="80d32-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80d32-148">範例</span><span class="sxs-lookup"><span data-stu-id="80d32-148">Example</span></span>  
 <span data-ttu-id="80d32-149">下列範例會使用`Or`運算子, 在兩個運算式上執行內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="80d32-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="80d32-150">結果是`Boolean`值, 表示兩個運算式的其中一個是否為`True`。</span><span class="sxs-lookup"><span data-stu-id="80d32-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="80d32-151">上述範例會分別產生、 `True` `True`和`False`的結果。</span><span class="sxs-lookup"><span data-stu-id="80d32-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80d32-152">範例</span><span class="sxs-lookup"><span data-stu-id="80d32-152">Example</span></span>  
 <span data-ttu-id="80d32-153">下列範例會使用`Or`運算子, 在兩個數值運算式的個別位上執行內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="80d32-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="80d32-154">如果運算元中的其中一個對應位設為 1, 則結果模式中的位會設定為。</span><span class="sxs-lookup"><span data-stu-id="80d32-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="80d32-155">上述範例會分別產生10、14和14的結果。</span><span class="sxs-lookup"><span data-stu-id="80d32-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d32-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80d32-156">See also</span></span>

- [<span data-ttu-id="80d32-157">邏輯/位運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80d32-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="80d32-158">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="80d32-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="80d32-159">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="80d32-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="80d32-160">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="80d32-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="80d32-161">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="80d32-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
