---
title: /= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: a8a031e968df90496a4e263ae78d47045ccdc923
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331040"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bb953-102">/= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb953-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="bb953-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="bb953-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb953-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb953-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="bb953-105">組件</span><span class="sxs-lookup"><span data-stu-id="bb953-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="bb953-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="bb953-106">Required.</span></span> <span data-ttu-id="bb953-107">Any numeric variable or property.</span><span class="sxs-lookup"><span data-stu-id="bb953-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="bb953-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="bb953-108">Required.</span></span> <span data-ttu-id="bb953-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="bb953-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb953-110">備註</span><span class="sxs-lookup"><span data-stu-id="bb953-110">Remarks</span></span>  
 <span data-ttu-id="bb953-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="bb953-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bb953-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="bb953-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="bb953-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span><span class="sxs-lookup"><span data-stu-id="bb953-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="bb953-114">The operator then assigns the floating-point result of that operation to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="bb953-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="bb953-115">This statement assigns a `Double` value to the variable or property on the left.</span><span class="sxs-lookup"><span data-stu-id="bb953-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="bb953-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span><span class="sxs-lookup"><span data-stu-id="bb953-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="bb953-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span><span class="sxs-lookup"><span data-stu-id="bb953-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="bb953-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bb953-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bb953-119">多載化</span><span class="sxs-lookup"><span data-stu-id="bb953-119">Overloading</span></span>  
 <span data-ttu-id="bb953-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="bb953-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bb953-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span><span class="sxs-lookup"><span data-stu-id="bb953-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="bb953-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="bb953-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bb953-123">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="bb953-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb953-124">範例</span><span class="sxs-lookup"><span data-stu-id="bb953-124">Example</span></span>  
 <span data-ttu-id="bb953-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span><span class="sxs-lookup"><span data-stu-id="bb953-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="bb953-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb953-126">See also</span></span>

- [<span data-ttu-id="bb953-127">/ Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb953-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="bb953-128">\\= Operator</span><span class="sxs-lookup"><span data-stu-id="bb953-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="bb953-129">指派運算子</span><span class="sxs-lookup"><span data-stu-id="bb953-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="bb953-130">算術運算子</span><span class="sxs-lookup"><span data-stu-id="bb953-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="bb953-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="bb953-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bb953-132">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="bb953-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="bb953-133">陳述式</span><span class="sxs-lookup"><span data-stu-id="bb953-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
