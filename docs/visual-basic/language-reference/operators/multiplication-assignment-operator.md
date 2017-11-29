---
title: "*= 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0a2c638f3faaf20fadb745ef437941ee29d4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1a47b-102">*= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a47b-102">*= Operator (Visual Basic)</span></span>
<span data-ttu-id="1a47b-103">將變數或屬性的值，乘以運算式的值，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="1a47b-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a47b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a47b-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="1a47b-105">組件</span><span class="sxs-lookup"><span data-stu-id="1a47b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1a47b-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="1a47b-106">Required.</span></span> <span data-ttu-id="1a47b-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="1a47b-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="1a47b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="1a47b-108">Required.</span></span> <span data-ttu-id="1a47b-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="1a47b-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a47b-110">備註</span><span class="sxs-lookup"><span data-stu-id="1a47b-110">Remarks</span></span>  
 <span data-ttu-id="1a47b-111">在左邊的項目`*=`運算子可以是簡單的純量變數、 屬性或陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="1a47b-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1a47b-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="1a47b-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1a47b-113">`*=`運算子先乘以 （在運算子右手邊） 運算式的值的變數或屬性 （在運算子的左側） 的值。</span><span class="sxs-lookup"><span data-stu-id="1a47b-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="1a47b-114">然後，運算子會將該作業的結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="1a47b-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1a47b-115">多載化</span><span class="sxs-lookup"><span data-stu-id="1a47b-115">Overloading</span></span>  
 <span data-ttu-id="1a47b-116">[* 運算子](../../../visual-basic/language-reference/operators/multiplication-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="1a47b-116">The [* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1a47b-117">多載`*`運算子會影響行為`*=`運算子。</span><span class="sxs-lookup"><span data-stu-id="1a47b-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="1a47b-118">如果您的程式碼使用`*=`上類別或結構的多載`*`，確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="1a47b-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1a47b-119">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="1a47b-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a47b-120">範例</span><span class="sxs-lookup"><span data-stu-id="1a47b-120">Example</span></span>  
 <span data-ttu-id="1a47b-121">下列範例會使用`*=`要相乘的其中一個運算子`Integer`變數的第二個和指派給第一個變數的結果。</span><span class="sxs-lookup"><span data-stu-id="1a47b-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1a47b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a47b-122">See Also</span></span>  
 [<span data-ttu-id="1a47b-123">* 運算子</span><span class="sxs-lookup"><span data-stu-id="1a47b-123">* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)  
 [<span data-ttu-id="1a47b-124">指派運算子</span><span class="sxs-lookup"><span data-stu-id="1a47b-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="1a47b-125">算術運算子</span><span class="sxs-lookup"><span data-stu-id="1a47b-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="1a47b-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="1a47b-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1a47b-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="1a47b-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="1a47b-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="1a47b-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
