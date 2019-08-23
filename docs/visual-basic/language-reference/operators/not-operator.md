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
ms.openlocfilehash: 29e2b159e4c6261a62e788b537102b9b457fe0c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955827"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="69a8e-102">Not 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69a8e-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="69a8e-103">在`Boolean`運算式上執行邏輯否定, 或在數值運算式上執行位否定。</span><span class="sxs-lookup"><span data-stu-id="69a8e-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="69a8e-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="69a8e-105">組件</span><span class="sxs-lookup"><span data-stu-id="69a8e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="69a8e-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="69a8e-106">Required.</span></span> <span data-ttu-id="69a8e-107">Any `Boolean`或 numeric 運算式。</span><span class="sxs-lookup"><span data-stu-id="69a8e-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="69a8e-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="69a8e-108">Required.</span></span> <span data-ttu-id="69a8e-109">Any `Boolean`或 numeric 運算式。</span><span class="sxs-lookup"><span data-stu-id="69a8e-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69a8e-110">備註</span><span class="sxs-lookup"><span data-stu-id="69a8e-110">Remarks</span></span>  
 <span data-ttu-id="69a8e-111">針對`Boolean`運算式, 下表說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="69a8e-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="69a8e-112">如果`expression`為</span><span class="sxs-lookup"><span data-stu-id="69a8e-112">If `expression` is</span></span>|<span data-ttu-id="69a8e-113">的值`result`為</span><span class="sxs-lookup"><span data-stu-id="69a8e-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="69a8e-114">對於數值運算式, `Not`運算子會反轉任何數值運算式的位值, 並根據下表設定中`result`的對應位。</span><span class="sxs-lookup"><span data-stu-id="69a8e-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="69a8e-115">如果中的`expression`位是</span><span class="sxs-lookup"><span data-stu-id="69a8e-115">If bit in `expression` is</span></span>|<span data-ttu-id="69a8e-116">中`result`的位是</span><span class="sxs-lookup"><span data-stu-id="69a8e-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="69a8e-117">1</span><span class="sxs-lookup"><span data-stu-id="69a8e-117">1</span></span>|<span data-ttu-id="69a8e-118">0</span><span class="sxs-lookup"><span data-stu-id="69a8e-118">0</span></span>|  
|<span data-ttu-id="69a8e-119">0</span><span class="sxs-lookup"><span data-stu-id="69a8e-119">0</span></span>|<span data-ttu-id="69a8e-120">1</span><span class="sxs-lookup"><span data-stu-id="69a8e-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="69a8e-121">由於邏輯和位運算子的優先順序比其他算術和關係運算子低, 因此應該將任何位運算括在括弧中, 以確保正確執行。</span><span class="sxs-lookup"><span data-stu-id="69a8e-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="69a8e-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="69a8e-122">Data Types</span></span>  
 <span data-ttu-id="69a8e-123">對於布林值否定, 結果的資料類型是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="69a8e-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="69a8e-124">若為位否定, 結果資料類型與相同`expression`。</span><span class="sxs-lookup"><span data-stu-id="69a8e-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="69a8e-125">不過, 如果 expression 為`Decimal`, 則結果為`Long`。</span><span class="sxs-lookup"><span data-stu-id="69a8e-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="69a8e-126">多載化</span><span class="sxs-lookup"><span data-stu-id="69a8e-126">Overloading</span></span>  
 <span data-ttu-id="69a8e-127">運算子可以多載, 這表示當類別或結構的運算元具有該類別或結構的類型時, 可以重新定義其行為。 `Not`</span><span class="sxs-lookup"><span data-stu-id="69a8e-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="69a8e-128">如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="69a8e-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="69a8e-129">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="69a8e-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69a8e-130">範例</span><span class="sxs-lookup"><span data-stu-id="69a8e-130">Example</span></span>  
 <span data-ttu-id="69a8e-131">下列範例會使用`Not`運算子來執行`Boolean`運算式的邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="69a8e-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="69a8e-132">結果是`Boolean`值, 表示運算式值的反轉。</span><span class="sxs-lookup"><span data-stu-id="69a8e-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="69a8e-133">上述範例會分別產生和`False` `True`的結果。</span><span class="sxs-lookup"><span data-stu-id="69a8e-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69a8e-134">範例</span><span class="sxs-lookup"><span data-stu-id="69a8e-134">Example</span></span>  
 <span data-ttu-id="69a8e-135">下列範例會使用`Not`運算子來執行數值運算式之個別位的邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="69a8e-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="69a8e-136">結果模式中的位會設定為運算元模式中對應位的反向, 包括符號位。</span><span class="sxs-lookup"><span data-stu-id="69a8e-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="69a8e-137">上述範例會分別產生–11、–9和–7的結果。</span><span class="sxs-lookup"><span data-stu-id="69a8e-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a8e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69a8e-138">See also</span></span>

- [<span data-ttu-id="69a8e-139">邏輯/位運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69a8e-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="69a8e-140">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="69a8e-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="69a8e-141">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="69a8e-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="69a8e-142">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="69a8e-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
