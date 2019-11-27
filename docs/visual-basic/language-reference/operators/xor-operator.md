---
title: Xor 運算子
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
ms.openlocfilehash: c5c7ec87bc173f724f8c670395bc3b0458444df6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335411"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="3561d-102">Xor 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3561d-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="3561d-103">在兩個 `Boolean` 運算式上執行邏輯排除，或在兩個數值運算式上執行位排除。</span><span class="sxs-lookup"><span data-stu-id="3561d-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3561d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3561d-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="3561d-105">組件</span><span class="sxs-lookup"><span data-stu-id="3561d-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="3561d-106">必要。</span><span class="sxs-lookup"><span data-stu-id="3561d-106">Required.</span></span> <span data-ttu-id="3561d-107">任何 `Boolean` 或數值變數。</span><span class="sxs-lookup"><span data-stu-id="3561d-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="3561d-108">針對布林比較，`result` 是兩個 `Boolean` 值的邏輯排除（獨佔邏輯分離）。</span><span class="sxs-lookup"><span data-stu-id="3561d-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="3561d-109">對於位運算而言，`result` 是數值，表示兩個數值位模式的位排除（獨佔位取）。</span><span class="sxs-lookup"><span data-stu-id="3561d-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="3561d-110">必要。</span><span class="sxs-lookup"><span data-stu-id="3561d-110">Required.</span></span> <span data-ttu-id="3561d-111">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="3561d-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="3561d-112">必要。</span><span class="sxs-lookup"><span data-stu-id="3561d-112">Required.</span></span> <span data-ttu-id="3561d-113">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="3561d-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3561d-114">備註</span><span class="sxs-lookup"><span data-stu-id="3561d-114">Remarks</span></span>  
 <span data-ttu-id="3561d-115">針對布林值比較，只有在只有其中一個 `expression1` 和 `expression2` 評估為 `True`時，才會 `True` `result`。</span><span class="sxs-lookup"><span data-stu-id="3561d-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="3561d-116">也就是說，只有在 `expression1` 和 `expression2` 評估為相反的 `Boolean` 值時。</span><span class="sxs-lookup"><span data-stu-id="3561d-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="3561d-117">下表說明如何決定 `result`。</span><span class="sxs-lookup"><span data-stu-id="3561d-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="3561d-118">如果 `expression1` 為</span><span class="sxs-lookup"><span data-stu-id="3561d-118">If `expression1` is</span></span>|<span data-ttu-id="3561d-119">而 `expression2` 為</span><span class="sxs-lookup"><span data-stu-id="3561d-119">And `expression2` is</span></span>|<span data-ttu-id="3561d-120">`result` 的值為</span><span class="sxs-lookup"><span data-stu-id="3561d-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="3561d-121">在布林值比較中，`Xor` 運算子一律會評估兩個運算式，這可能包括進行程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="3561d-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="3561d-122">`Xor`沒有最少的對應，因為結果一律取決於這兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="3561d-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="3561d-123">如需最*小*運算邏輯運算子，請參閱[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)和[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="3561d-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="3561d-124">對於位運算，`Xor` 運算子會在兩個數值運算式中執行相同位置位的位比較，並根據下表設定 `result` 中的對應位。</span><span class="sxs-lookup"><span data-stu-id="3561d-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="3561d-125">如果 `expression1` 中的位為</span><span class="sxs-lookup"><span data-stu-id="3561d-125">If bit in `expression1` is</span></span>|<span data-ttu-id="3561d-126">`expression2` 中的和位是</span><span class="sxs-lookup"><span data-stu-id="3561d-126">And bit in `expression2` is</span></span>|<span data-ttu-id="3561d-127">`result` 中的位是</span><span class="sxs-lookup"><span data-stu-id="3561d-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="3561d-128">1</span><span class="sxs-lookup"><span data-stu-id="3561d-128">1</span></span>|<span data-ttu-id="3561d-129">1</span><span class="sxs-lookup"><span data-stu-id="3561d-129">1</span></span>|<span data-ttu-id="3561d-130">0</span><span class="sxs-lookup"><span data-stu-id="3561d-130">0</span></span>|  
|<span data-ttu-id="3561d-131">1</span><span class="sxs-lookup"><span data-stu-id="3561d-131">1</span></span>|<span data-ttu-id="3561d-132">0</span><span class="sxs-lookup"><span data-stu-id="3561d-132">0</span></span>|<span data-ttu-id="3561d-133">1</span><span class="sxs-lookup"><span data-stu-id="3561d-133">1</span></span>|  
|<span data-ttu-id="3561d-134">0</span><span class="sxs-lookup"><span data-stu-id="3561d-134">0</span></span>|<span data-ttu-id="3561d-135">1</span><span class="sxs-lookup"><span data-stu-id="3561d-135">1</span></span>|<span data-ttu-id="3561d-136">1</span><span class="sxs-lookup"><span data-stu-id="3561d-136">1</span></span>|  
|<span data-ttu-id="3561d-137">0</span><span class="sxs-lookup"><span data-stu-id="3561d-137">0</span></span>|<span data-ttu-id="3561d-138">0</span><span class="sxs-lookup"><span data-stu-id="3561d-138">0</span></span>|<span data-ttu-id="3561d-139">0</span><span class="sxs-lookup"><span data-stu-id="3561d-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3561d-140">由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保正確執行。</span><span class="sxs-lookup"><span data-stu-id="3561d-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="3561d-141">例如，5 `Xor` 3 為6。</span><span class="sxs-lookup"><span data-stu-id="3561d-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="3561d-142">若要瞭解原因，請將5和3轉換成其二進位表示，101和011。</span><span class="sxs-lookup"><span data-stu-id="3561d-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="3561d-143">然後使用上表來判斷 101 Xor 011 是110，這是十進位數6的二進位標記法。</span><span class="sxs-lookup"><span data-stu-id="3561d-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="3561d-144">資料類型</span><span class="sxs-lookup"><span data-stu-id="3561d-144">Data Types</span></span>  
 <span data-ttu-id="3561d-145">如果運算元包含一個 `Boolean` 運算式和一個數值運算式，Visual Basic 會將 `Boolean` 運算式轉換成數值（-1 代表 `True`，0代表 `False`），並執行位運算。</span><span class="sxs-lookup"><span data-stu-id="3561d-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="3561d-146">若要進行 `Boolean` 比較，會 `Boolean`結果的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3561d-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="3561d-147">針對位比較，結果資料類型是適用于 `expression1` 和 `expression2`的資料類型的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="3561d-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="3561d-148">請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。</span><span class="sxs-lookup"><span data-stu-id="3561d-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3561d-149">多載化</span><span class="sxs-lookup"><span data-stu-id="3561d-149">Overloading</span></span>  
 <span data-ttu-id="3561d-150">`Xor` 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="3561d-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3561d-151">如果您的程式碼在這類類別或結構上使用這個運算子，請確定您瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="3561d-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="3561d-152">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="3561d-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3561d-153">範例</span><span class="sxs-lookup"><span data-stu-id="3561d-153">Example</span></span>  
 <span data-ttu-id="3561d-154">下列範例會使用 `Xor` 運算子，在兩個運算式上執行邏輯排除（獨佔邏輯分離）。</span><span class="sxs-lookup"><span data-stu-id="3561d-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="3561d-155">結果為 `Boolean` 值，表示是否 `True`只有一個運算式。</span><span class="sxs-lookup"><span data-stu-id="3561d-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="3561d-156">上一個範例會分別產生 `False`、`True`和 `False`的結果。</span><span class="sxs-lookup"><span data-stu-id="3561d-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3561d-157">範例</span><span class="sxs-lookup"><span data-stu-id="3561d-157">Example</span></span>  
 <span data-ttu-id="3561d-158">下列範例會使用 `Xor` 運算子，在兩個數值運算式的個別位上執行邏輯排除（獨佔邏輯分離）。</span><span class="sxs-lookup"><span data-stu-id="3561d-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="3561d-159">如果運算元中只有一個對應的位設為1，則結果模式中的位會設定為。</span><span class="sxs-lookup"><span data-stu-id="3561d-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="3561d-160">先前的範例會分別產生2、12和14的結果。</span><span class="sxs-lookup"><span data-stu-id="3561d-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3561d-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="3561d-161">See also</span></span>

- [<span data-ttu-id="3561d-162">邏輯/位運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="3561d-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="3561d-163">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="3561d-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3561d-164">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="3561d-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3561d-165">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="3561d-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
