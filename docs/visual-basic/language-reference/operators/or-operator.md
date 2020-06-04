---
title: Or 運算子
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
ms.openlocfilehash: 657b2a473b23789a8ba25fbd11c6b83538fa7803
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401416"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="f462b-102">Or 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f462b-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="f462b-103">在兩個運算式上執行邏輯分離 `Boolean` ，或在兩個數值運算式上執行位析取。</span><span class="sxs-lookup"><span data-stu-id="f462b-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f462b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f462b-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f462b-105">組件</span><span class="sxs-lookup"><span data-stu-id="f462b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f462b-106">必要。</span><span class="sxs-lookup"><span data-stu-id="f462b-106">Required.</span></span> <span data-ttu-id="f462b-107">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f462b-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="f462b-108">為了進行 `Boolean` 比較， `result` 是兩個值的內含邏輯分離 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="f462b-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="f462b-109">對於位運算而言， `result` 是代表兩個數值位模式之內含位分離的數值。</span><span class="sxs-lookup"><span data-stu-id="f462b-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f462b-110">必要。</span><span class="sxs-lookup"><span data-stu-id="f462b-110">Required.</span></span> <span data-ttu-id="f462b-111">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f462b-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f462b-112">必要。</span><span class="sxs-lookup"><span data-stu-id="f462b-112">Required.</span></span> <span data-ttu-id="f462b-113">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f462b-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f462b-114">備註</span><span class="sxs-lookup"><span data-stu-id="f462b-114">Remarks</span></span>  
 <span data-ttu-id="f462b-115">為了進行 `Boolean` 比較 `result` ， `False` 只有和都 `expression1` `expression2` 評估為 `False` 時才為。</span><span class="sxs-lookup"><span data-stu-id="f462b-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="f462b-116">下表說明如何 `result` 決定。</span><span class="sxs-lookup"><span data-stu-id="f462b-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f462b-117">如果 `expression1` 為 </span><span class="sxs-lookup"><span data-stu-id="f462b-117">If `expression1` is</span></span>|<span data-ttu-id="f462b-118">和 `expression2` 為</span><span class="sxs-lookup"><span data-stu-id="f462b-118">And `expression2` is</span></span>|<span data-ttu-id="f462b-119">的值 `result` 為</span><span class="sxs-lookup"><span data-stu-id="f462b-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="f462b-120">在 `Boolean` 比較中， `Or` 運算子一律會評估兩個運算式，這可能包括進行程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="f462b-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="f462b-121">[OrElse 運算子](orelse-operator.md)*會執行最*少運算，這表示如果 `expression1` 為，則 `True` `expression2` 不會評估。</span><span class="sxs-lookup"><span data-stu-id="f462b-121">The [OrElse Operator](orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="f462b-122">對於位運算， `Or` 運算子會在兩個數值運算式中執行相同位置位的位比較，並根據下表設定中的對應位 `result` 。</span><span class="sxs-lookup"><span data-stu-id="f462b-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="f462b-123">如果中的位 `expression1` 是</span><span class="sxs-lookup"><span data-stu-id="f462b-123">If bit in `expression1` is</span></span>|<span data-ttu-id="f462b-124">中的和位 `expression2` 為</span><span class="sxs-lookup"><span data-stu-id="f462b-124">And bit in `expression2` is</span></span>|<span data-ttu-id="f462b-125">中的位 `result` 是</span><span class="sxs-lookup"><span data-stu-id="f462b-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="f462b-126">1</span><span class="sxs-lookup"><span data-stu-id="f462b-126">1</span></span>|<span data-ttu-id="f462b-127">1</span><span class="sxs-lookup"><span data-stu-id="f462b-127">1</span></span>|<span data-ttu-id="f462b-128">1</span><span class="sxs-lookup"><span data-stu-id="f462b-128">1</span></span>|  
|<span data-ttu-id="f462b-129">1</span><span class="sxs-lookup"><span data-stu-id="f462b-129">1</span></span>|<span data-ttu-id="f462b-130">0</span><span class="sxs-lookup"><span data-stu-id="f462b-130">0</span></span>|<span data-ttu-id="f462b-131">1</span><span class="sxs-lookup"><span data-stu-id="f462b-131">1</span></span>|  
|<span data-ttu-id="f462b-132">0</span><span class="sxs-lookup"><span data-stu-id="f462b-132">0</span></span>|<span data-ttu-id="f462b-133">1</span><span class="sxs-lookup"><span data-stu-id="f462b-133">1</span></span>|<span data-ttu-id="f462b-134">1</span><span class="sxs-lookup"><span data-stu-id="f462b-134">1</span></span>|  
|<span data-ttu-id="f462b-135">0</span><span class="sxs-lookup"><span data-stu-id="f462b-135">0</span></span>|<span data-ttu-id="f462b-136">0</span><span class="sxs-lookup"><span data-stu-id="f462b-136">0</span></span>|<span data-ttu-id="f462b-137">0</span><span class="sxs-lookup"><span data-stu-id="f462b-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f462b-138">由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保正確執行。</span><span class="sxs-lookup"><span data-stu-id="f462b-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f462b-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="f462b-139">Data Types</span></span>  
 <span data-ttu-id="f462b-140">如果運算元是由一個 `Boolean` 運算式和一個數值運算式所組成，Visual Basic 會將 `Boolean` 運算式轉換為數值（-1 代表 `True` ，0則代表 `False` ），並執行位運算。</span><span class="sxs-lookup"><span data-stu-id="f462b-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="f462b-141">為了進行 `Boolean` 比較，結果的資料類型是 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="f462b-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="f462b-142">針對位比較，結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="f462b-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="f462b-143">請參閱[運算子結果的資料類型](data-types-of-operator-results.md)中的「關聯式和位比較」資料表。</span><span class="sxs-lookup"><span data-stu-id="f462b-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f462b-144">多載化</span><span class="sxs-lookup"><span data-stu-id="f462b-144">Overloading</span></span>  
 <span data-ttu-id="f462b-145">`Or`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="f462b-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f462b-146">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="f462b-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f462b-147">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="f462b-147">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f462b-148">範例</span><span class="sxs-lookup"><span data-stu-id="f462b-148">Example</span></span>  
 <span data-ttu-id="f462b-149">下列範例會使用 `Or` 運算子，在兩個運算式上執行內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="f462b-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="f462b-150">結果是 `Boolean` 值，表示兩個運算式的其中一個是否為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="f462b-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="f462b-151">上述範例會 `True` 分別產生、 `True` 和的結果 `False` 。</span><span class="sxs-lookup"><span data-stu-id="f462b-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f462b-152">範例</span><span class="sxs-lookup"><span data-stu-id="f462b-152">Example</span></span>  
 <span data-ttu-id="f462b-153">下列範例會使用 `Or` 運算子，在兩個數值運算式的個別位上執行內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="f462b-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="f462b-154">如果運算元中的其中一個對應位設為1，則結果模式中的位會設定為。</span><span class="sxs-lookup"><span data-stu-id="f462b-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="f462b-155">上述範例會分別產生10、14和14的結果。</span><span class="sxs-lookup"><span data-stu-id="f462b-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f462b-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f462b-156">See also</span></span>

- [<span data-ttu-id="f462b-157">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f462b-157">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="f462b-158">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="f462b-158">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f462b-159">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="f462b-159">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f462b-160">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="f462b-160">OrElse Operator</span></span>](orelse-operator.md)
- [<span data-ttu-id="f462b-161">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="f462b-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
