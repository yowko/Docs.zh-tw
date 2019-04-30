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
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013513"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="f92dc-102">Or 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f92dc-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="f92dc-103">對兩個執行邏輯分離`Boolean`運算式或兩個數值運算式的位元分離。</span><span class="sxs-lookup"><span data-stu-id="f92dc-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f92dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="f92dc-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f92dc-105">組件</span><span class="sxs-lookup"><span data-stu-id="f92dc-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f92dc-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="f92dc-106">Required.</span></span> <span data-ttu-id="f92dc-107">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f92dc-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="f92dc-108">針對`Boolean`相較之下，`result`是兩個內含邏輯分離`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="f92dc-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="f92dc-109">對於位元運算，`result`是數值，代表兩個數值位元模式 （含） 的位元分離。</span><span class="sxs-lookup"><span data-stu-id="f92dc-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f92dc-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="f92dc-110">Required.</span></span> <span data-ttu-id="f92dc-111">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f92dc-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f92dc-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="f92dc-112">Required.</span></span> <span data-ttu-id="f92dc-113">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f92dc-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f92dc-114">備註</span><span class="sxs-lookup"><span data-stu-id="f92dc-114">Remarks</span></span>  
 <span data-ttu-id="f92dc-115">針對`Boolean`相較之下，`result`是`False`並僅有兩個`expression1`並`expression2`評估為`False`。</span><span class="sxs-lookup"><span data-stu-id="f92dc-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="f92dc-116">下表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="f92dc-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f92dc-117">如果`expression1`是</span><span class="sxs-lookup"><span data-stu-id="f92dc-117">If `expression1` is</span></span>|<span data-ttu-id="f92dc-118">和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="f92dc-118">And `expression2` is</span></span>|<span data-ttu-id="f92dc-119">值`result`是</span><span class="sxs-lookup"><span data-stu-id="f92dc-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="f92dc-120">在 `Boolean`相較之下，`Or`運算子一律會評估這兩個運算式，這可能包括程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="f92dc-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="f92dc-121">[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)會執行*最少運算*，這表示如果`expression1`是`True`，然後`expression2`不會評估。</span><span class="sxs-lookup"><span data-stu-id="f92dc-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="f92dc-122">位元運算，如`Or`運算子會在兩個數值運算式之間執行位元比較相同位置的位元，並對應中位元設`result`根據下表。</span><span class="sxs-lookup"><span data-stu-id="f92dc-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="f92dc-123">如果位元`expression1`是</span><span class="sxs-lookup"><span data-stu-id="f92dc-123">If bit in `expression1` is</span></span>|<span data-ttu-id="f92dc-124">在位元和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="f92dc-124">And bit in `expression2` is</span></span>|<span data-ttu-id="f92dc-125">中的位元`result`是</span><span class="sxs-lookup"><span data-stu-id="f92dc-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="f92dc-126">1</span><span class="sxs-lookup"><span data-stu-id="f92dc-126">1</span></span>|<span data-ttu-id="f92dc-127">1</span><span class="sxs-lookup"><span data-stu-id="f92dc-127">1</span></span>|<span data-ttu-id="f92dc-128">1</span><span class="sxs-lookup"><span data-stu-id="f92dc-128">1</span></span>|  
|<span data-ttu-id="f92dc-129">1</span><span class="sxs-lookup"><span data-stu-id="f92dc-129">1</span></span>|<span data-ttu-id="f92dc-130">0</span><span class="sxs-lookup"><span data-stu-id="f92dc-130">0</span></span>|<span data-ttu-id="f92dc-131">1</span><span class="sxs-lookup"><span data-stu-id="f92dc-131">1</span></span>|  
|<span data-ttu-id="f92dc-132">0</span><span class="sxs-lookup"><span data-stu-id="f92dc-132">0</span></span>|<span data-ttu-id="f92dc-133">1</span><span class="sxs-lookup"><span data-stu-id="f92dc-133">1</span></span>|<span data-ttu-id="f92dc-134">1</span><span class="sxs-lookup"><span data-stu-id="f92dc-134">1</span></span>|  
|<span data-ttu-id="f92dc-135">0</span><span class="sxs-lookup"><span data-stu-id="f92dc-135">0</span></span>|<span data-ttu-id="f92dc-136">0</span><span class="sxs-lookup"><span data-stu-id="f92dc-136">0</span></span>|<span data-ttu-id="f92dc-137">0</span><span class="sxs-lookup"><span data-stu-id="f92dc-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f92dc-138">因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元的作業應該含括括號，以確保能夠正確執行。</span><span class="sxs-lookup"><span data-stu-id="f92dc-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f92dc-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="f92dc-139">Data Types</span></span>  
 <span data-ttu-id="f92dc-140">如果包含運算元`Boolean`Visual Basic 運算式及一個數值運算式，將轉換`Boolean`為數值的運算式 (– 1`True`以 0 代表`False`) 和執行位元運算。</span><span class="sxs-lookup"><span data-stu-id="f92dc-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="f92dc-141">針對`Boolean`相較之下，結果的資料型別是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="f92dc-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="f92dc-142">如需位元的比較，將結果資料類型是數值類型適合的資料類型`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="f92dc-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="f92dc-143">請參閱 < 關聯式和位元比較 」 的表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="f92dc-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f92dc-144">多載化</span><span class="sxs-lookup"><span data-stu-id="f92dc-144">Overloading</span></span>  
 <span data-ttu-id="f92dc-145">`Or`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="f92dc-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f92dc-146">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="f92dc-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f92dc-147">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="f92dc-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f92dc-148">範例</span><span class="sxs-lookup"><span data-stu-id="f92dc-148">Example</span></span>  
 <span data-ttu-id="f92dc-149">下列範例會使用`Or`操作員兩個運算式上執行內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="f92dc-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="f92dc-150">結果是`Boolean`值，表示其中兩個運算式是否`True`。</span><span class="sxs-lookup"><span data-stu-id="f92dc-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="f92dc-151">上述範例產生的結果`True`， `True`，和`False`分別。</span><span class="sxs-lookup"><span data-stu-id="f92dc-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f92dc-152">範例</span><span class="sxs-lookup"><span data-stu-id="f92dc-152">Example</span></span>  
 <span data-ttu-id="f92dc-153">下列範例會使用`Or`運算子的兩個數值運算式的個別位元執行內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="f92dc-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="f92dc-154">如果任一運算元的對應位元設為 1，會設定結果模式中的位元。</span><span class="sxs-lookup"><span data-stu-id="f92dc-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="f92dc-155">上述範例中會分別產生 10、 14 及 14 的結果。</span><span class="sxs-lookup"><span data-stu-id="f92dc-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f92dc-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f92dc-156">See also</span></span>

- [<span data-ttu-id="f92dc-157">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f92dc-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="f92dc-158">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="f92dc-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f92dc-159">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="f92dc-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f92dc-160">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="f92dc-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="f92dc-161">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="f92dc-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
