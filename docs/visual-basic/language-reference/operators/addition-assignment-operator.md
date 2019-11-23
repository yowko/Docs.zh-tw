---
title: += 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 31a6da163061b905b8ffddcfc4b44978f5cdd55e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350299"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9cb7c-102">+= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb7c-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="9cb7c-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="9cb7c-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb7c-105">語法</span><span class="sxs-lookup"><span data-stu-id="9cb7c-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9cb7c-106">組件</span><span class="sxs-lookup"><span data-stu-id="9cb7c-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9cb7c-107">必要項。</span><span class="sxs-lookup"><span data-stu-id="9cb7c-107">Required.</span></span> <span data-ttu-id="9cb7c-108">Any numeric or `String` variable or property.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="9cb7c-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="9cb7c-109">Required.</span></span> <span data-ttu-id="9cb7c-110">Any numeric or `String` expression.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cb7c-111">備註</span><span class="sxs-lookup"><span data-stu-id="9cb7c-111">Remarks</span></span>  
 <span data-ttu-id="9cb7c-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9cb7c-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9cb7c-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="9cb7c-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="9cb7c-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cb7c-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="9cb7c-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="9cb7c-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="9cb7c-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="9cb7c-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="9cb7c-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9cb7c-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="9cb7c-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="9cb7c-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="9cb7c-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9cb7c-123">多載化</span><span class="sxs-lookup"><span data-stu-id="9cb7c-123">Overloading</span></span>  
 <span data-ttu-id="9cb7c-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9cb7c-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="9cb7c-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9cb7c-127">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="9cb7c-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cb7c-128">範例</span><span class="sxs-lookup"><span data-stu-id="9cb7c-128">Example</span></span>  
 <span data-ttu-id="9cb7c-129">The following example uses the `+=` operator to combine the value of one variable with another.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="9cb7c-130">The first part uses `+=` with numeric variables to add one value to another.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="9cb7c-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="9cb7c-132">In both cases, the result is assigned to the first variable.</span><span class="sxs-lookup"><span data-stu-id="9cb7c-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="9cb7c-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span><span class="sxs-lookup"><span data-stu-id="9cb7c-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb7c-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cb7c-134">See also</span></span>

- [<span data-ttu-id="9cb7c-135">+ 運算子</span><span class="sxs-lookup"><span data-stu-id="9cb7c-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="9cb7c-136">指派運算子</span><span class="sxs-lookup"><span data-stu-id="9cb7c-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="9cb7c-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="9cb7c-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="9cb7c-138">串連運算子</span><span class="sxs-lookup"><span data-stu-id="9cb7c-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="9cb7c-139">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="9cb7c-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9cb7c-140">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="9cb7c-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9cb7c-141">陳述式</span><span class="sxs-lookup"><span data-stu-id="9cb7c-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
