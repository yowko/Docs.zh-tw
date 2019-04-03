---
title: Xor 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 0cba3a995fb1ab774c8a5308e58f0b6905fc23f3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827064"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="2f0f4-102">Xor 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f0f4-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="2f0f4-103">對兩個執行邏輯排除`Boolean`運算式或兩個數值運算式的位元互斥。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f0f4-104">Syntax</span></span>  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="2f0f4-105">組件</span><span class="sxs-lookup"><span data-stu-id="2f0f4-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="2f0f4-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-106">Required.</span></span> <span data-ttu-id="2f0f4-107">任何`Boolean`或數值的變數。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="2f0f4-108">布林值相較之下，如`result`是兩個邏輯互斥 （獨佔邏輯分離）`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="2f0f4-109">對於位元運算，`result`是數值，表示兩個數值位元模式的位元互斥 （獨佔位元分離）。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="2f0f4-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-110">Required.</span></span> <span data-ttu-id="2f0f4-111">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="2f0f4-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-112">Required.</span></span> <span data-ttu-id="2f0f4-113">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f0f4-114">備註</span><span class="sxs-lookup"><span data-stu-id="2f0f4-114">Remarks</span></span>  
 <span data-ttu-id="2f0f4-115">布林值相較之下，如`result`是`True`才之一`expression1`和`expression2`評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="2f0f4-116">亦即，如果且只有`expression1`並`expression2`評估為相反`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="2f0f4-117">下表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="2f0f4-118">如果`expression1`是</span><span class="sxs-lookup"><span data-stu-id="2f0f4-118">If `expression1` is</span></span>|<span data-ttu-id="2f0f4-119">和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="2f0f4-119">And `expression2` is</span></span>|<span data-ttu-id="2f0f4-120">值`result`是</span><span class="sxs-lookup"><span data-stu-id="2f0f4-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="2f0f4-121">布林值相較之下，`Xor`運算子一律會評估這兩個運算式，這可能包括程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="2f0f4-122">沒有任何最少運算的對應項目來`Xor`，因為結果一定會相依於這兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="2f0f4-123">針對*最少運算*邏輯運算子，請參閱[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)並[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="2f0f4-124">位元運算，如`Xor`運算子會在兩個數值運算式之間執行位元比較相同位置的位元，並對應中位元設`result`根據下表。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="2f0f4-125">如果位元`expression1`是</span><span class="sxs-lookup"><span data-stu-id="2f0f4-125">If bit in `expression1` is</span></span>|<span data-ttu-id="2f0f4-126">在位元和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="2f0f4-126">And bit in `expression2` is</span></span>|<span data-ttu-id="2f0f4-127">中的位元`result`是</span><span class="sxs-lookup"><span data-stu-id="2f0f4-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="2f0f4-128">1</span><span class="sxs-lookup"><span data-stu-id="2f0f4-128">1</span></span>|<span data-ttu-id="2f0f4-129">1</span><span class="sxs-lookup"><span data-stu-id="2f0f4-129">1</span></span>|<span data-ttu-id="2f0f4-130">0</span><span class="sxs-lookup"><span data-stu-id="2f0f4-130">0</span></span>|  
|<span data-ttu-id="2f0f4-131">1</span><span class="sxs-lookup"><span data-stu-id="2f0f4-131">1</span></span>|<span data-ttu-id="2f0f4-132">0</span><span class="sxs-lookup"><span data-stu-id="2f0f4-132">0</span></span>|<span data-ttu-id="2f0f4-133">1</span><span class="sxs-lookup"><span data-stu-id="2f0f4-133">1</span></span>|  
|<span data-ttu-id="2f0f4-134">0</span><span class="sxs-lookup"><span data-stu-id="2f0f4-134">0</span></span>|<span data-ttu-id="2f0f4-135">1</span><span class="sxs-lookup"><span data-stu-id="2f0f4-135">1</span></span>|<span data-ttu-id="2f0f4-136">1</span><span class="sxs-lookup"><span data-stu-id="2f0f4-136">1</span></span>|  
|<span data-ttu-id="2f0f4-137">0</span><span class="sxs-lookup"><span data-stu-id="2f0f4-137">0</span></span>|<span data-ttu-id="2f0f4-138">0</span><span class="sxs-lookup"><span data-stu-id="2f0f4-138">0</span></span>|<span data-ttu-id="2f0f4-139">0</span><span class="sxs-lookup"><span data-stu-id="2f0f4-139">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2f0f4-140">因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元的作業應該含括括號，以確保能夠正確執行。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="2f0f4-141">例如，5 `Xor` 3 為 6。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="2f0f4-142">若要查看這為何因此，轉換成其二進位的表示法、 101 和 011 的 5 和 3。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="2f0f4-143">然後使用上表來判斷 101 Xor 011 是 110，這是 6 的十進位數字的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="2f0f4-144">資料類型</span><span class="sxs-lookup"><span data-stu-id="2f0f4-144">Data Types</span></span>  
 <span data-ttu-id="2f0f4-145">如果包含運算元`Boolean`Visual Basic 運算式及一個數值運算式，將轉換`Boolean`為數值的運算式 (– 1`True`以 0 代表`False`) 和執行位元運算。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="2f0f4-146">針對`Boolean`相較之下，結果的資料型別是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="2f0f4-147">如需位元的比較，將結果資料類型是數值類型適合的資料類型`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="2f0f4-148">請參閱 < 關聯式和位元比較 」 的表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2f0f4-149">多載化</span><span class="sxs-lookup"><span data-stu-id="2f0f4-149">Overloading</span></span>  
 <span data-ttu-id="2f0f4-150">`Xor`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2f0f4-151">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="2f0f4-152">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f0f4-153">範例</span><span class="sxs-lookup"><span data-stu-id="2f0f4-153">Example</span></span>  
 <span data-ttu-id="2f0f4-154">下列範例會使用`Xor`運算子上兩個運算式執行邏輯互斥 （獨佔邏輯分離）。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="2f0f4-155">結果是`Boolean`值，表示只有其中一個運算式是否`True`。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="2f0f4-156">前一個範例產生的結果`False`， `True`，和`False`分別。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f0f4-157">範例</span><span class="sxs-lookup"><span data-stu-id="2f0f4-157">Example</span></span>  
 <span data-ttu-id="2f0f4-158">下列範例會使用`Xor`運算子的兩個數值運算式的個別位元執行邏輯互斥 （獨佔邏輯分離）。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="2f0f4-159">如果只有其中一個運算元的對應位元設為 1，會設定結果模式中的位元。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="2f0f4-160">前一個範例會分別產生的 2、 第 12 和 14 的結果。</span><span class="sxs-lookup"><span data-stu-id="2f0f4-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0f4-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f0f4-161">See also</span></span>

- [<span data-ttu-id="2f0f4-162">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f0f4-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="2f0f4-163">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="2f0f4-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="2f0f4-164">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="2f0f4-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="2f0f4-165">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="2f0f4-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
