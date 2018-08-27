---
title: '\= 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: bcfc59efda0627f83713fe9ada24cedc20d823e3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934509"
---
# <a name="-operator"></a><span data-ttu-id="13f25-102">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="13f25-102">\\= Operator</span></span>
<span data-ttu-id="13f25-103">將運算式的值的變數或屬性的值除以並指派整數結果給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="13f25-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f25-104">語法</span><span class="sxs-lookup"><span data-stu-id="13f25-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="13f25-105">組件</span><span class="sxs-lookup"><span data-stu-id="13f25-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="13f25-106">必要。</span><span class="sxs-lookup"><span data-stu-id="13f25-106">Required.</span></span> <span data-ttu-id="13f25-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="13f25-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="13f25-108">必要。</span><span class="sxs-lookup"><span data-stu-id="13f25-108">Required.</span></span> <span data-ttu-id="13f25-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="13f25-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13f25-110">備註</span><span class="sxs-lookup"><span data-stu-id="13f25-110">Remarks</span></span>  
 <span data-ttu-id="13f25-111">在左邊的項目`\=`運算子可以是簡單的純量變數、 屬性或陣列項目。</span><span class="sxs-lookup"><span data-stu-id="13f25-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="13f25-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="13f25-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="13f25-113">`\=`運算子將其右邊值的變數或其左邊屬性的值除以，並將整數的結果指派給變數或與其左邊的屬性</span><span class="sxs-lookup"><span data-stu-id="13f25-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="13f25-114">如需整數除法運算的詳細資訊，請參閱[\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="13f25-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="13f25-115">多載化</span><span class="sxs-lookup"><span data-stu-id="13f25-115">Overloading</span></span>  
 <span data-ttu-id="13f25-116">`\`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="13f25-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="13f25-117">多載`\`運算子會影響的行為`\=`運算子。</span><span class="sxs-lookup"><span data-stu-id="13f25-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="13f25-118">如果您的程式碼會使用`\=`上類別或結構，多載`\`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="13f25-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="13f25-119">如需詳細資訊，請參閱 <<c0> [ 運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="13f25-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f25-120">範例</span><span class="sxs-lookup"><span data-stu-id="13f25-120">Example</span></span>  
 <span data-ttu-id="13f25-121">下列範例會使用`\=`運算子，將其中一個`Integer`變數的第二個和第一個變數會導致將整數指派。</span><span class="sxs-lookup"><span data-stu-id="13f25-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="13f25-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13f25-122">See Also</span></span>  
 [<span data-ttu-id="13f25-123">\ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13f25-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="13f25-124">/ = 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13f25-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="13f25-125">指派運算子</span><span class="sxs-lookup"><span data-stu-id="13f25-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="13f25-126">算術運算子</span><span class="sxs-lookup"><span data-stu-id="13f25-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="13f25-127">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="13f25-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="13f25-128">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="13f25-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="13f25-129">陳述式</span><span class="sxs-lookup"><span data-stu-id="13f25-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
