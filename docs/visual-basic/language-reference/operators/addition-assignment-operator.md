---
title: += 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ac8f5679aa90c50c15c33a957cfc75d9ccecde6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="31aa1-102">+= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31aa1-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="31aa1-103">將數值變數或屬性的值加上數值運算式的值，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="31aa1-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="31aa1-104">也可用來串連`String`運算式`String`變數或屬性並指派結果給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="31aa1-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31aa1-105">語法</span><span class="sxs-lookup"><span data-stu-id="31aa1-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="31aa1-106">組件</span><span class="sxs-lookup"><span data-stu-id="31aa1-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="31aa1-107">必要項。</span><span class="sxs-lookup"><span data-stu-id="31aa1-107">Required.</span></span> <span data-ttu-id="31aa1-108">任何數值或`String`變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="31aa1-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="31aa1-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="31aa1-109">Required.</span></span> <span data-ttu-id="31aa1-110">任何數值或`String`運算式。</span><span class="sxs-lookup"><span data-stu-id="31aa1-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31aa1-111">備註</span><span class="sxs-lookup"><span data-stu-id="31aa1-111">Remarks</span></span>  
 <span data-ttu-id="31aa1-112">在左邊的項目`+=`運算子可以是簡單的純量變數、 屬性或陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="31aa1-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="31aa1-113">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="31aa1-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="31aa1-114">`+=`運算子將值加入至變數或屬性與其左邊，右邊，並將結果指派給變數或屬性與其左邊。</span><span class="sxs-lookup"><span data-stu-id="31aa1-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="31aa1-115">`+=`運算子也可用來串連`String`運算式右邊`String`變數，或在其左邊，並指派結果給變數的屬性或與其左邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="31aa1-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31aa1-116">當您使用`+=`運算子，可能無法判斷發生加法或字串串連。</span><span class="sxs-lookup"><span data-stu-id="31aa1-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="31aa1-117">使用`&=`運算子串連避免模稜兩可，以及提供自我記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="31aa1-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="31aa1-118">此指派運算子隱含執行擴展但未縮小轉換，如果編譯環境強制執行嚴格的語意。</span><span class="sxs-lookup"><span data-stu-id="31aa1-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="31aa1-119">如需有關這些轉換的詳細資訊，請參閱[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="31aa1-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="31aa1-120">Strict 及寬鬆語意的詳細資訊，請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="31aa1-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="31aa1-121">如果允許寬鬆的語意，`+=`運算子隱含地執行各種字串和數值轉換所執行的相同`+`運算子。</span><span class="sxs-lookup"><span data-stu-id="31aa1-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="31aa1-122">如需這些轉換的詳細資訊，請參閱[+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="31aa1-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="31aa1-123">多載化</span><span class="sxs-lookup"><span data-stu-id="31aa1-123">Overloading</span></span>  
 <span data-ttu-id="31aa1-124">`+`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="31aa1-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="31aa1-125">多載`+`運算子會影響行為`+=`運算子。</span><span class="sxs-lookup"><span data-stu-id="31aa1-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="31aa1-126">如果您的程式碼使用`+=`上類別或結構的多載`+`，確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="31aa1-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="31aa1-127">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="31aa1-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31aa1-128">範例</span><span class="sxs-lookup"><span data-stu-id="31aa1-128">Example</span></span>  
 <span data-ttu-id="31aa1-129">下列範例會使用`+=`運算子以結合以另一個變數的值。</span><span class="sxs-lookup"><span data-stu-id="31aa1-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="31aa1-130">第一個部分使用`+=`數值變數來加入到另一個值。</span><span class="sxs-lookup"><span data-stu-id="31aa1-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="31aa1-131">第二個部分會使用`+=`與`String`来串連的一個值與另一個變數。</span><span class="sxs-lookup"><span data-stu-id="31aa1-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="31aa1-132">在這兩種情況下，結果會指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="31aa1-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 <span data-ttu-id="31aa1-133">值`num1`13 和的值現在是`str1`現在是"103"。</span><span class="sxs-lookup"><span data-stu-id="31aa1-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31aa1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31aa1-134">See Also</span></span>  
 [<span data-ttu-id="31aa1-135">+ 運算子</span><span class="sxs-lookup"><span data-stu-id="31aa1-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [<span data-ttu-id="31aa1-136">指派運算子</span><span class="sxs-lookup"><span data-stu-id="31aa1-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="31aa1-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="31aa1-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="31aa1-138">串連運算子</span><span class="sxs-lookup"><span data-stu-id="31aa1-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="31aa1-139">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="31aa1-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="31aa1-140">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="31aa1-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="31aa1-141">陳述式</span><span class="sxs-lookup"><span data-stu-id="31aa1-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
