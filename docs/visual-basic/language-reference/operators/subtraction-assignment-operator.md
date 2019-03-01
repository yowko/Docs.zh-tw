---
title: -= 運算子 (Visual Basic)
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
ms.openlocfilehash: c3495c4e45fe5e1d497578ee3ee6afe874e90eed
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203041"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="af1c4-102">-= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af1c4-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="af1c4-103">減去運算式的值的變數或屬性的值，然後將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="af1c4-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="af1c4-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="af1c4-105">組件</span><span class="sxs-lookup"><span data-stu-id="af1c4-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="af1c4-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="af1c4-106">Required.</span></span> <span data-ttu-id="af1c4-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="af1c4-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="af1c4-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="af1c4-108">Required.</span></span> <span data-ttu-id="af1c4-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="af1c4-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af1c4-110">備註</span><span class="sxs-lookup"><span data-stu-id="af1c4-110">Remarks</span></span>  
 <span data-ttu-id="af1c4-111">在左邊的項目`-=`運算子可以是簡單的純量變數、 屬性或陣列項目。</span><span class="sxs-lookup"><span data-stu-id="af1c4-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="af1c4-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="af1c4-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="af1c4-113">`-=`第一次從變數或屬性 （在運算子的左側） 的值減去 （在運算子右手邊） 運算式的值的運算子。</span><span class="sxs-lookup"><span data-stu-id="af1c4-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="af1c4-114">然後，運算子會將該作業的結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="af1c4-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="af1c4-115">多載化</span><span class="sxs-lookup"><span data-stu-id="af1c4-115">Overloading</span></span>  
 <span data-ttu-id="af1c4-116">[-運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="af1c4-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="af1c4-117">多載`-`運算子會影響的行為`-=`運算子。</span><span class="sxs-lookup"><span data-stu-id="af1c4-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="af1c4-118">如果您的程式碼會使用`-=`上類別或結構，多載`-`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="af1c4-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="af1c4-119">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="af1c4-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af1c4-120">範例</span><span class="sxs-lookup"><span data-stu-id="af1c4-120">Example</span></span>  
 <span data-ttu-id="af1c4-121">下列範例會使用`-=`減一的運算子`Integer`從另一個變數並指派結果對應到第二個變數。</span><span class="sxs-lookup"><span data-stu-id="af1c4-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="af1c4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af1c4-122">See also</span></span>
- [<span data-ttu-id="af1c4-123">-運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af1c4-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="af1c4-124">指派運算子</span><span class="sxs-lookup"><span data-stu-id="af1c4-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="af1c4-125">算術運算子</span><span class="sxs-lookup"><span data-stu-id="af1c4-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="af1c4-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="af1c4-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="af1c4-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="af1c4-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="af1c4-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="af1c4-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
