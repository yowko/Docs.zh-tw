---
title: And 運算子
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
ms.openlocfilehash: b4d6d08cca2907befeab2e31c6804b69849c9e38
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874857"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="df6ea-102">And 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df6ea-102">And Operator (Visual Basic)</span></span>

<span data-ttu-id="df6ea-103">在兩個運算式上執行邏輯結合 `Boolean` ，或在兩個數值運算式上執行位合。</span><span class="sxs-lookup"><span data-stu-id="df6ea-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df6ea-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="df6ea-104">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="df6ea-105">組件</span><span class="sxs-lookup"><span data-stu-id="df6ea-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="df6ea-106">必要。</span><span class="sxs-lookup"><span data-stu-id="df6ea-106">Required.</span></span> <span data-ttu-id="df6ea-107">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="df6ea-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="df6ea-108">針對布林值比較， `result` 這是兩個值的邏輯結合 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="df6ea-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="df6ea-109">在位運算中， `result` 是代表兩個數值位模式之位合的數值。</span><span class="sxs-lookup"><span data-stu-id="df6ea-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="df6ea-110">必要。</span><span class="sxs-lookup"><span data-stu-id="df6ea-110">Required.</span></span> <span data-ttu-id="df6ea-111">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="df6ea-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="df6ea-112">必要。</span><span class="sxs-lookup"><span data-stu-id="df6ea-112">Required.</span></span> <span data-ttu-id="df6ea-113">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="df6ea-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df6ea-114">備註</span><span class="sxs-lookup"><span data-stu-id="df6ea-114">Remarks</span></span>  

 <span data-ttu-id="df6ea-115">針對布林值比較 `result` ， `True` 只有在 `expression1` 和都 `expression2` 評估為 `True` 時，才為。</span><span class="sxs-lookup"><span data-stu-id="df6ea-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="df6ea-116">下表說明如何 `result` 決定。</span><span class="sxs-lookup"><span data-stu-id="df6ea-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="df6ea-117">如果 `expression1` 為 </span><span class="sxs-lookup"><span data-stu-id="df6ea-117">If `expression1` is</span></span>|<span data-ttu-id="df6ea-118">而且 `expression2` 是</span><span class="sxs-lookup"><span data-stu-id="df6ea-118">And `expression2` is</span></span>|<span data-ttu-id="df6ea-119">的值 `result` 為</span><span class="sxs-lookup"><span data-stu-id="df6ea-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="df6ea-120">在布林值比較中， `And` 運算子一律會評估這兩個運算式，這可能包括進行程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="df6ea-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="df6ea-121">[AndAlso 運算子](andalso-operator.md)會執行*最*少運算，這表示如果 `expression1` 是，則 `False` `expression2` 不會評估。</span><span class="sxs-lookup"><span data-stu-id="df6ea-121">The [AndAlso Operator](andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="df6ea-122">當套用至數值時， `And` 運算子會執行兩個數值運算式中相同位置位的位比較，並根據下表設定對應的位 `result` 。</span><span class="sxs-lookup"><span data-stu-id="df6ea-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="df6ea-123">如果中的位 `expression1` 為</span><span class="sxs-lookup"><span data-stu-id="df6ea-123">If bit in `expression1` is</span></span>|<span data-ttu-id="df6ea-124">和中的位 `expression2` 為</span><span class="sxs-lookup"><span data-stu-id="df6ea-124">And bit in `expression2` is</span></span>|<span data-ttu-id="df6ea-125">中的位 `result` 為</span><span class="sxs-lookup"><span data-stu-id="df6ea-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="df6ea-126">1</span><span class="sxs-lookup"><span data-stu-id="df6ea-126">1</span></span>|<span data-ttu-id="df6ea-127">1</span><span class="sxs-lookup"><span data-stu-id="df6ea-127">1</span></span>|<span data-ttu-id="df6ea-128">1</span><span class="sxs-lookup"><span data-stu-id="df6ea-128">1</span></span>|  
|<span data-ttu-id="df6ea-129">1</span><span class="sxs-lookup"><span data-stu-id="df6ea-129">1</span></span>|<span data-ttu-id="df6ea-130">0</span><span class="sxs-lookup"><span data-stu-id="df6ea-130">0</span></span>|<span data-ttu-id="df6ea-131">0</span><span class="sxs-lookup"><span data-stu-id="df6ea-131">0</span></span>|  
|<span data-ttu-id="df6ea-132">0</span><span class="sxs-lookup"><span data-stu-id="df6ea-132">0</span></span>|<span data-ttu-id="df6ea-133">1</span><span class="sxs-lookup"><span data-stu-id="df6ea-133">1</span></span>|<span data-ttu-id="df6ea-134">0</span><span class="sxs-lookup"><span data-stu-id="df6ea-134">0</span></span>|  
|<span data-ttu-id="df6ea-135">0</span><span class="sxs-lookup"><span data-stu-id="df6ea-135">0</span></span>|<span data-ttu-id="df6ea-136">0</span><span class="sxs-lookup"><span data-stu-id="df6ea-136">0</span></span>|<span data-ttu-id="df6ea-137">0</span><span class="sxs-lookup"><span data-stu-id="df6ea-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="df6ea-138">由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此任何位運算都應以括弧括住，以確保正確的結果。</span><span class="sxs-lookup"><span data-stu-id="df6ea-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="df6ea-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="df6ea-139">Data Types</span></span>  

 <span data-ttu-id="df6ea-140">如果運算元是由一個 `Boolean` 運算式和一個數值運算式組成，Visual Basic 會將 `Boolean` 運算式轉換成數值 ( –1，並將) 的值轉換為 `True` 0， `False` 並執行位運算。</span><span class="sxs-lookup"><span data-stu-id="df6ea-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="df6ea-141">若為布林值比較，結果的資料類型為 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="df6ea-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="df6ea-142">針對位比較，結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="df6ea-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="df6ea-143">請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「關聯式和位比較」資料表。</span><span class="sxs-lookup"><span data-stu-id="df6ea-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df6ea-144">可以多載 `And` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="df6ea-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="df6ea-145">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="df6ea-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="df6ea-146">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="df6ea-146">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df6ea-147">範例</span><span class="sxs-lookup"><span data-stu-id="df6ea-147">Example</span></span>  

 <span data-ttu-id="df6ea-148">下列範例會使用 `And` 運算子，在兩個運算式上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="df6ea-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="df6ea-149">結果是一個 `Boolean` 值，表示兩個運算式是否都是 `True` 。</span><span class="sxs-lookup"><span data-stu-id="df6ea-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="df6ea-150">上述範例會分別產生和的結果 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="df6ea-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df6ea-151">範例</span><span class="sxs-lookup"><span data-stu-id="df6ea-151">Example</span></span>  

 <span data-ttu-id="df6ea-152">下列範例會使用 `And` 運算子，在兩個數值運算式的個別位上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="df6ea-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="df6ea-153">如果運算元中的對應位都設定為1，則會設定結果模式中的位。</span><span class="sxs-lookup"><span data-stu-id="df6ea-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="df6ea-154">上述範例會分別產生8、2和0的結果。</span><span class="sxs-lookup"><span data-stu-id="df6ea-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df6ea-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df6ea-155">See also</span></span>

- [<span data-ttu-id="df6ea-156">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df6ea-156">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="df6ea-157">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="df6ea-157">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="df6ea-158">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="df6ea-158">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="df6ea-159">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="df6ea-159">AndAlso Operator</span></span>](andalso-operator.md)
- [<span data-ttu-id="df6ea-160">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="df6ea-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
