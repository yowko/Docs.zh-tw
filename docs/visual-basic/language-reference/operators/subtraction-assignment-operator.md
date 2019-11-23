---
title: -= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 44cb226d64e9f0b86c6566eb25fbafd6323a6d4c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347803"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="03fca-102">-= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03fca-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="03fca-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="03fca-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03fca-104">語法</span><span class="sxs-lookup"><span data-stu-id="03fca-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="03fca-105">組件</span><span class="sxs-lookup"><span data-stu-id="03fca-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="03fca-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="03fca-106">Required.</span></span> <span data-ttu-id="03fca-107">Any numeric variable or property.</span><span class="sxs-lookup"><span data-stu-id="03fca-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="03fca-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="03fca-108">Required.</span></span> <span data-ttu-id="03fca-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="03fca-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03fca-110">備註</span><span class="sxs-lookup"><span data-stu-id="03fca-110">Remarks</span></span>  
 <span data-ttu-id="03fca-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="03fca-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="03fca-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="03fca-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="03fca-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span><span class="sxs-lookup"><span data-stu-id="03fca-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="03fca-114">The operator then assigns the result of that operation to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="03fca-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="03fca-115">多載化</span><span class="sxs-lookup"><span data-stu-id="03fca-115">Overloading</span></span>  
 <span data-ttu-id="03fca-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="03fca-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="03fca-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span><span class="sxs-lookup"><span data-stu-id="03fca-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="03fca-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="03fca-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="03fca-119">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="03fca-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03fca-120">範例</span><span class="sxs-lookup"><span data-stu-id="03fca-120">Example</span></span>  
 <span data-ttu-id="03fca-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span><span class="sxs-lookup"><span data-stu-id="03fca-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="03fca-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="03fca-122">See also</span></span>

- [<span data-ttu-id="03fca-123">- Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03fca-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="03fca-124">指派運算子</span><span class="sxs-lookup"><span data-stu-id="03fca-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="03fca-125">算術運算子</span><span class="sxs-lookup"><span data-stu-id="03fca-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="03fca-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="03fca-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="03fca-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="03fca-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="03fca-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="03fca-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
