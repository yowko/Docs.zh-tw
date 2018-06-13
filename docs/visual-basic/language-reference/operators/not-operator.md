---
title: Not 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 332cee57c8d25d7f51737e01e70ba515d50bd6e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604389"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="65212-102">Not 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65212-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="65212-103">上執行邏輯否定`Boolean`運算式或數值運算式上的位元否定運算。</span><span class="sxs-lookup"><span data-stu-id="65212-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65212-104">語法</span><span class="sxs-lookup"><span data-stu-id="65212-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="65212-105">組件</span><span class="sxs-lookup"><span data-stu-id="65212-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="65212-106">必要。</span><span class="sxs-lookup"><span data-stu-id="65212-106">Required.</span></span> <span data-ttu-id="65212-107">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="65212-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="65212-108">必要。</span><span class="sxs-lookup"><span data-stu-id="65212-108">Required.</span></span> <span data-ttu-id="65212-109">任何`Boolean`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="65212-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65212-110">備註</span><span class="sxs-lookup"><span data-stu-id="65212-110">Remarks</span></span>  
 <span data-ttu-id="65212-111">如`Boolean`運算式下, 表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="65212-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="65212-112">如果`expression`是</span><span class="sxs-lookup"><span data-stu-id="65212-112">If `expression` is</span></span>|<span data-ttu-id="65212-113">值`result`是</span><span class="sxs-lookup"><span data-stu-id="65212-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="65212-114">針對數值運算式，`Not`運算子反轉任何數值運算式的位元值和對應的中位元設`result`根據下表。</span><span class="sxs-lookup"><span data-stu-id="65212-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="65212-115">如果位元`expression`是</span><span class="sxs-lookup"><span data-stu-id="65212-115">If bit in `expression` is</span></span>|<span data-ttu-id="65212-116">中的位元`result`是</span><span class="sxs-lookup"><span data-stu-id="65212-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="65212-117">1</span><span class="sxs-lookup"><span data-stu-id="65212-117">1</span></span>|<span data-ttu-id="65212-118">0</span><span class="sxs-lookup"><span data-stu-id="65212-118">0</span></span>|  
|<span data-ttu-id="65212-119">0</span><span class="sxs-lookup"><span data-stu-id="65212-119">0</span></span>|<span data-ttu-id="65212-120">1</span><span class="sxs-lookup"><span data-stu-id="65212-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="65212-121">因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元運算應該括在括號可確保能夠正確執行。</span><span class="sxs-lookup"><span data-stu-id="65212-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="65212-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="65212-122">Data Types</span></span>  
 <span data-ttu-id="65212-123">布林值的否定運算結果的資料型別是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="65212-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="65212-124">位元否定運算，將結果資料類型是屬於相同`expression`。</span><span class="sxs-lookup"><span data-stu-id="65212-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="65212-125">不過，如果運算式是`Decimal`，結果是`Long`。</span><span class="sxs-lookup"><span data-stu-id="65212-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="65212-126">多載化</span><span class="sxs-lookup"><span data-stu-id="65212-126">Overloading</span></span>  
 <span data-ttu-id="65212-127">`Not`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時其運算元的該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="65212-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="65212-128">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="65212-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="65212-129">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="65212-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65212-130">範例</span><span class="sxs-lookup"><span data-stu-id="65212-130">Example</span></span>  
 <span data-ttu-id="65212-131">下列範例會使用`Not`上執行邏輯否定運算子`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="65212-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="65212-132">結果是`Boolean`值，表示運算式值的反向。</span><span class="sxs-lookup"><span data-stu-id="65212-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 <span data-ttu-id="65212-133">上述範例產生的結果`False`和`True`分別。</span><span class="sxs-lookup"><span data-stu-id="65212-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65212-134">範例</span><span class="sxs-lookup"><span data-stu-id="65212-134">Example</span></span>  
 <span data-ttu-id="65212-135">下列範例會使用`Not`運算子執行邏輯否定的數值運算式的個別位元。</span><span class="sxs-lookup"><span data-stu-id="65212-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="65212-136">結果模式中的位元會設定為在運算元模式中，包括正負號位元的對應位元的反向。</span><span class="sxs-lookup"><span data-stu-id="65212-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 <span data-ttu-id="65212-137">上述範例中會分別產生-11-9 及-7 的結果。</span><span class="sxs-lookup"><span data-stu-id="65212-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65212-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65212-138">See Also</span></span>  
 [<span data-ttu-id="65212-139">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65212-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="65212-140">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="65212-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="65212-141">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="65212-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="65212-142">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="65212-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
