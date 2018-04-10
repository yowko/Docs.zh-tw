---
title: Xor 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b14f11f2df2df9c29e88e9188390cfe245d2cb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="27941-102">Xor 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27941-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="27941-103">執行邏輯排除在兩個`Boolean`運算式或兩個數值運算式的位元互斥。</span><span class="sxs-lookup"><span data-stu-id="27941-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27941-104">語法</span><span class="sxs-lookup"><span data-stu-id="27941-104">Syntax</span></span>  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="27941-105">組件</span><span class="sxs-lookup"><span data-stu-id="27941-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="27941-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="27941-106">Required.</span></span> <span data-ttu-id="27941-107">任何`Boolean`或數值的變數。</span><span class="sxs-lookup"><span data-stu-id="27941-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="27941-108">布林比較，`result`是兩個邏輯排除 （獨佔邏輯分離）`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="27941-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="27941-109">位元運算，如`result`是數值，表示兩個數值的位元模式的位元互斥 （位元排除分離）。</span><span class="sxs-lookup"><span data-stu-id="27941-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="27941-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="27941-110">Required.</span></span> <span data-ttu-id="27941-111">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="27941-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="27941-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="27941-112">Required.</span></span> <span data-ttu-id="27941-113">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="27941-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27941-114">備註</span><span class="sxs-lookup"><span data-stu-id="27941-114">Remarks</span></span>  
 <span data-ttu-id="27941-115">布林比較，`result`是`True`如果且只有其中一個`expression1`和`expression2`評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="27941-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="27941-116">也就是說，如果且只有`expression1`和`expression2`評估為相反`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="27941-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="27941-117">下表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="27941-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="27941-118">如果`expression1`是</span><span class="sxs-lookup"><span data-stu-id="27941-118">If `expression1` is</span></span>|<span data-ttu-id="27941-119">和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="27941-119">And `expression2` is</span></span>|<span data-ttu-id="27941-120">值`result`是</span><span class="sxs-lookup"><span data-stu-id="27941-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="27941-121">布林值相較之下，`Xor`運算子一律會評估這兩個運算式，可能會使程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="27941-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="27941-122">沒有任何最少運算的對應項目來`Xor`，因為結果一定會相依於這兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="27941-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="27941-123">如*最少運算*邏輯運算子，請參閱[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)和[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="27941-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="27941-124">位元運算，如`Xor`運算子中兩個數值運算式執行位元的比較相同位置的位元並對應中位元設`result`根據下表。</span><span class="sxs-lookup"><span data-stu-id="27941-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="27941-125">如果位元`expression1`是</span><span class="sxs-lookup"><span data-stu-id="27941-125">If bit in `expression1` is</span></span>|<span data-ttu-id="27941-126">在位元和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="27941-126">And bit in `expression2` is</span></span>|<span data-ttu-id="27941-127">中的位元`result`是</span><span class="sxs-lookup"><span data-stu-id="27941-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="27941-128">1</span><span class="sxs-lookup"><span data-stu-id="27941-128">1</span></span>|<span data-ttu-id="27941-129">1</span><span class="sxs-lookup"><span data-stu-id="27941-129">1</span></span>|<span data-ttu-id="27941-130">0</span><span class="sxs-lookup"><span data-stu-id="27941-130">0</span></span>|  
|<span data-ttu-id="27941-131">1</span><span class="sxs-lookup"><span data-stu-id="27941-131">1</span></span>|<span data-ttu-id="27941-132">0</span><span class="sxs-lookup"><span data-stu-id="27941-132">0</span></span>|<span data-ttu-id="27941-133">1</span><span class="sxs-lookup"><span data-stu-id="27941-133">1</span></span>|  
|<span data-ttu-id="27941-134">0</span><span class="sxs-lookup"><span data-stu-id="27941-134">0</span></span>|<span data-ttu-id="27941-135">1</span><span class="sxs-lookup"><span data-stu-id="27941-135">1</span></span>|<span data-ttu-id="27941-136">1</span><span class="sxs-lookup"><span data-stu-id="27941-136">1</span></span>|  
|<span data-ttu-id="27941-137">0</span><span class="sxs-lookup"><span data-stu-id="27941-137">0</span></span>|<span data-ttu-id="27941-138">0</span><span class="sxs-lookup"><span data-stu-id="27941-138">0</span></span>|<span data-ttu-id="27941-139">0</span><span class="sxs-lookup"><span data-stu-id="27941-139">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="27941-140">因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元運算應該括在括號可確保能夠正確執行。</span><span class="sxs-lookup"><span data-stu-id="27941-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="27941-141">例如，5 `Xor` 3 為 6。</span><span class="sxs-lookup"><span data-stu-id="27941-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="27941-142">若要查看為什麼會這樣，轉換成 5 和 3 101 和 011 其二進位表示。</span><span class="sxs-lookup"><span data-stu-id="27941-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="27941-143">然後使用上表，判斷 101 Xor 011 為 110 時，也就是十進位數字 6 的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="27941-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="27941-144">資料類型</span><span class="sxs-lookup"><span data-stu-id="27941-144">Data Types</span></span>  
 <span data-ttu-id="27941-145">如果運算元組成一個`Boolean`Visual Basic 運算式和一個數值運算式，將轉換`Boolean`為數值運算式 (如 – 1`True`以 0 代表`False`) 和執行位元運算。</span><span class="sxs-lookup"><span data-stu-id="27941-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="27941-146">如`Boolean`比較結果的資料類型是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="27941-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="27941-147">位元的比較，將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="27941-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="27941-148">請參閱 「 關聯式和位元比較 」 的表格[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="27941-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="27941-149">多載化</span><span class="sxs-lookup"><span data-stu-id="27941-149">Overloading</span></span>  
 <span data-ttu-id="27941-150">`Xor`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="27941-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="27941-151">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="27941-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="27941-152">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="27941-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27941-153">範例</span><span class="sxs-lookup"><span data-stu-id="27941-153">Example</span></span>  
 <span data-ttu-id="27941-154">下列範例會使用`Xor`上兩個運算式執行邏輯排除 （獨佔邏輯分離） 運算子。</span><span class="sxs-lookup"><span data-stu-id="27941-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="27941-155">結果是`Boolean`值，表示只有其中一個運算式是否`True`。</span><span class="sxs-lookup"><span data-stu-id="27941-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 <span data-ttu-id="27941-156">前一個範例產生的結果`False`， `True`，和`False`分別。</span><span class="sxs-lookup"><span data-stu-id="27941-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27941-157">範例</span><span class="sxs-lookup"><span data-stu-id="27941-157">Example</span></span>  
 <span data-ttu-id="27941-158">下列範例會使用`Xor`運算子的兩個數值運算式的個別位元執行邏輯排除 （獨佔邏輯分離）。</span><span class="sxs-lookup"><span data-stu-id="27941-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="27941-159">如果只有其中一個運算元的對應位元設為 1，會設定結果模式中的位元。</span><span class="sxs-lookup"><span data-stu-id="27941-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 <span data-ttu-id="27941-160">前一個範例會分別產生 2，12 和 14 的結果。</span><span class="sxs-lookup"><span data-stu-id="27941-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27941-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27941-161">See Also</span></span>  
 [<span data-ttu-id="27941-162">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27941-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="27941-163">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="27941-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="27941-164">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="27941-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="27941-165">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="27941-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
