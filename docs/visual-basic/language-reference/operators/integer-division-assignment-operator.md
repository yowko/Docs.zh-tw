---
title: '\= 運算子'
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
ms.openlocfilehash: 600acf9b41b63358da245fe602595fee4093b15b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330948"
---
# <a name="-operator"></a><span data-ttu-id="e65ce-102">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="e65ce-102">\\= Operator</span></span>
<span data-ttu-id="e65ce-103">將變數或屬性的值除以運算式的值，並將整數結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="e65ce-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="e65ce-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e65ce-105">組件</span><span class="sxs-lookup"><span data-stu-id="e65ce-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e65ce-106">必要。</span><span class="sxs-lookup"><span data-stu-id="e65ce-106">Required.</span></span> <span data-ttu-id="e65ce-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="e65ce-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e65ce-108">必要。</span><span class="sxs-lookup"><span data-stu-id="e65ce-108">Required.</span></span> <span data-ttu-id="e65ce-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="e65ce-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e65ce-110">備註</span><span class="sxs-lookup"><span data-stu-id="e65ce-110">Remarks</span></span>  
 <span data-ttu-id="e65ce-111">`\=` 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="e65ce-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e65ce-112">變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="e65ce-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e65ce-113">`\=` 運算子會將變數或屬性的值除以其右邊的值，並將整數結果指派給其左邊的變數或屬性</span><span class="sxs-lookup"><span data-stu-id="e65ce-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="e65ce-114">如需整數除法的進一步資訊，請參閱[\ 運算子（Visual Basic）](../../../visual-basic/language-reference/operators/integer-division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="e65ce-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e65ce-115">多載化</span><span class="sxs-lookup"><span data-stu-id="e65ce-115">Overloading</span></span>  
 <span data-ttu-id="e65ce-116">`\` 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="e65ce-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e65ce-117">多載 `\` 運算子會影響 `\=` 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="e65ce-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="e65ce-118">如果您的程式碼在多載 `\`的類別或結構上使用 `\=`，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="e65ce-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e65ce-119">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e65ce-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e65ce-120">範例</span><span class="sxs-lookup"><span data-stu-id="e65ce-120">Example</span></span>  
 <span data-ttu-id="e65ce-121">下列範例會使用 `\=` 運算子，將一個 `Integer` 變數除以第二個，並將整數結果指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="e65ce-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="e65ce-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e65ce-122">See also</span></span>

- [<span data-ttu-id="e65ce-123">\ 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e65ce-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="e65ce-124">/= 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e65ce-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="e65ce-125">指派運算子</span><span class="sxs-lookup"><span data-stu-id="e65ce-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="e65ce-126">算術運算子</span><span class="sxs-lookup"><span data-stu-id="e65ce-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="e65ce-127">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="e65ce-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e65ce-128">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="e65ce-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e65ce-129">陳述式</span><span class="sxs-lookup"><span data-stu-id="e65ce-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
