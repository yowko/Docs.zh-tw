---
title: /= 運算子 (Visual Basic)
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
ms.openlocfilehash: d9d3fa021654d3be1b9d304beb83caa737660264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778465"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="82ac3-102">/= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82ac3-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="82ac3-103">將運算式的值的變數或屬性的值除以並指派浮點結果給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="82ac3-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ac3-104">語法</span><span class="sxs-lookup"><span data-stu-id="82ac3-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="82ac3-105">組件</span><span class="sxs-lookup"><span data-stu-id="82ac3-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="82ac3-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="82ac3-106">Required.</span></span> <span data-ttu-id="82ac3-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="82ac3-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="82ac3-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="82ac3-108">Required.</span></span> <span data-ttu-id="82ac3-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="82ac3-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82ac3-110">備註</span><span class="sxs-lookup"><span data-stu-id="82ac3-110">Remarks</span></span>  
 <span data-ttu-id="82ac3-111">在左邊的項目`/=`運算子可以是簡單的純量變數、 屬性或陣列項目。</span><span class="sxs-lookup"><span data-stu-id="82ac3-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="82ac3-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="82ac3-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="82ac3-113">`/=`運算子先除以變數或屬性 （在運算子的左側） 的值 （在運算子右手邊） 運算式的值。</span><span class="sxs-lookup"><span data-stu-id="82ac3-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="82ac3-114">然後，運算子會將浮點運算的結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="82ac3-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="82ac3-115">此陳述式會指派`Double`變數或左邊的屬性值。</span><span class="sxs-lookup"><span data-stu-id="82ac3-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="82ac3-116">如果`Option Strict`已`On`，`variableorproperty`必須是`Double`。</span><span class="sxs-lookup"><span data-stu-id="82ac3-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="82ac3-117">如果`Option Strict`已`Off`，Visual Basic 執行隱含轉換，並將指派到產生的值`variableorproperty`，可能在執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="82ac3-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="82ac3-118">如需詳細資訊，請參閱 < [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)並[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="82ac3-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="82ac3-119">多載化</span><span class="sxs-lookup"><span data-stu-id="82ac3-119">Overloading</span></span>  
 <span data-ttu-id="82ac3-120">[/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="82ac3-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="82ac3-121">多載`/`運算子會影響的行為`/=`運算子。</span><span class="sxs-lookup"><span data-stu-id="82ac3-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="82ac3-122">如果您的程式碼會使用`/=`上類別或結構，多載`/`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="82ac3-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="82ac3-123">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="82ac3-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82ac3-124">範例</span><span class="sxs-lookup"><span data-stu-id="82ac3-124">Example</span></span>  
 <span data-ttu-id="82ac3-125">下列範例會使用`/=`運算子，將其中一個`Integer`變數的第二個和指派給第一個變數的商數。</span><span class="sxs-lookup"><span data-stu-id="82ac3-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="82ac3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82ac3-126">See also</span></span>

- [<span data-ttu-id="82ac3-127">/ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82ac3-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="82ac3-128">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="82ac3-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="82ac3-129">指派運算子</span><span class="sxs-lookup"><span data-stu-id="82ac3-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="82ac3-130">算術運算子</span><span class="sxs-lookup"><span data-stu-id="82ac3-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="82ac3-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="82ac3-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="82ac3-132">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="82ac3-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="82ac3-133">陳述式</span><span class="sxs-lookup"><span data-stu-id="82ac3-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
