---
title: ^= 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5d7b3dcb55192167512e0934e09cff7dfddb6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778517"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d2a87-102">^= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2a87-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="d2a87-103">引發的變數或運算式的乘冪的屬性值，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="d2a87-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a87-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2a87-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d2a87-105">組件</span><span class="sxs-lookup"><span data-stu-id="d2a87-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d2a87-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="d2a87-106">Required.</span></span> <span data-ttu-id="d2a87-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="d2a87-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="d2a87-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="d2a87-108">Required.</span></span> <span data-ttu-id="d2a87-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="d2a87-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2a87-110">備註</span><span class="sxs-lookup"><span data-stu-id="d2a87-110">Remarks</span></span>  
 <span data-ttu-id="d2a87-111">在左邊的項目`^=`運算子可以是簡單的純量變數、 屬性或陣列項目。</span><span class="sxs-lookup"><span data-stu-id="d2a87-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d2a87-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a87-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d2a87-113">`^=`值 （在運算子右手邊） 運算式的乘冪運算子第一次引發的變數或屬性 （在運算子的左側） 的值。</span><span class="sxs-lookup"><span data-stu-id="d2a87-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="d2a87-114">然後，運算子會將該作業的結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="d2a87-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="d2a87-115">Visual Basic 一律會執行中的乘冪[Double 資料型別](../../../visual-basic/language-reference/data-types/double-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a87-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="d2a87-116">任何不同類型的運算元會轉換成`Double`，而且結果一律`Double`。</span><span class="sxs-lookup"><span data-stu-id="d2a87-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="d2a87-117">值`expression`可以是小數、 負數，或兩者。</span><span class="sxs-lookup"><span data-stu-id="d2a87-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d2a87-118">多載化</span><span class="sxs-lookup"><span data-stu-id="d2a87-118">Overloading</span></span>  
 <span data-ttu-id="d2a87-119">[^ 運算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="d2a87-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d2a87-120">多載`^`運算子會影響的行為`^=`運算子。</span><span class="sxs-lookup"><span data-stu-id="d2a87-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="d2a87-121">如果您的程式碼會使用`^=`上類別或結構，多載`^`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="d2a87-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d2a87-122">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a87-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2a87-123">範例</span><span class="sxs-lookup"><span data-stu-id="d2a87-123">Example</span></span>  
 <span data-ttu-id="d2a87-124">下列範例會使用`^=`引發的其中一個值的運算子`Integer`變數的第二個變數並指派給第一個變數的結果。</span><span class="sxs-lookup"><span data-stu-id="d2a87-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="d2a87-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2a87-125">See also</span></span>

- [<span data-ttu-id="d2a87-126">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="d2a87-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="d2a87-127">指派運算子</span><span class="sxs-lookup"><span data-stu-id="d2a87-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="d2a87-128">算術運算子</span><span class="sxs-lookup"><span data-stu-id="d2a87-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="d2a87-129">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="d2a87-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d2a87-130">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="d2a87-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d2a87-131">陳述式</span><span class="sxs-lookup"><span data-stu-id="d2a87-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
