---
title: "/ = 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e877e98104b5c9fd679485b50a88943fac80a696
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f837d-102">/= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f837d-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="f837d-103">將運算式的值的變數或屬性的值除以和浮點結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="f837d-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f837d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f837d-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f837d-105">組件</span><span class="sxs-lookup"><span data-stu-id="f837d-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f837d-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="f837d-106">Required.</span></span> <span data-ttu-id="f837d-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="f837d-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="f837d-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="f837d-108">Required.</span></span> <span data-ttu-id="f837d-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f837d-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f837d-110">備註</span><span class="sxs-lookup"><span data-stu-id="f837d-110">Remarks</span></span>  
 <span data-ttu-id="f837d-111">在左邊的項目`/=`運算子可以是簡單的純量變數、 屬性或陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="f837d-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f837d-112">變數或屬性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="f837d-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="f837d-113">`/=`運算子第一次將變數或屬性 （在運算子的左側） 的值除以運算式 （在運算子的右側） 的值。</span><span class="sxs-lookup"><span data-stu-id="f837d-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="f837d-114">然後，運算子會將浮點運算的結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="f837d-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="f837d-115">此陳述式指派`Double`變數或屬性，在左邊的值。</span><span class="sxs-lookup"><span data-stu-id="f837d-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="f837d-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span><span class="sxs-lookup"><span data-stu-id="f837d-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="f837d-117">如果`Option Strict`是`Off`，Visual Basic 執行隱含轉換，並將結果指派至`variableorproperty`，可能在執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="f837d-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="f837d-118">如需詳細資訊，請參閱[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f837d-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f837d-119">多載化</span><span class="sxs-lookup"><span data-stu-id="f837d-119">Overloading</span></span>  
 <span data-ttu-id="f837d-120">[/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)可以是*多載*，也就是說，類別或結構可以重新定義它的行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="f837d-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f837d-121">多載`/`運算子會影響的行為`/=`運算子。</span><span class="sxs-lookup"><span data-stu-id="f837d-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="f837d-122">如果您的程式碼使用`/=`類別或結構的多載上`/`，確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="f837d-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f837d-123">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="f837d-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f837d-124">範例</span><span class="sxs-lookup"><span data-stu-id="f837d-124">Example</span></span>  
 <span data-ttu-id="f837d-125">下列範例會使用`/=`將其中一個運算子`Integer`變數的第二個和指派給第一個變數的商數。</span><span class="sxs-lookup"><span data-stu-id="f837d-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 <span data-ttu-id="f837d-126">[!code-vb[VbVbalrOperators #&17;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f837d-126">[!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f837d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f837d-127">See Also</span></span>  
 <span data-ttu-id="f837d-128">[/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f837d-128">[/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span></span>  
<span data-ttu-id="f837d-129"> [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f837d-129"> [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span></span>  
<span data-ttu-id="f837d-130"> [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="f837d-130"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="f837d-131"> [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="f837d-131"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="f837d-132"> [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="f837d-132"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="f837d-133"> [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="f837d-133"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="f837d-134"> [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="f837d-134"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

