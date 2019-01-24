---
title: '&amp;= 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: dee30096f244adc34b83fdfdc6af0baabd372b4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672405"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="7efa5-102">&amp;= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7efa5-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="7efa5-103">串連`String`運算式`String`變數或屬性，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="7efa5-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efa5-104">語法</span><span class="sxs-lookup"><span data-stu-id="7efa5-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="7efa5-105">組件</span><span class="sxs-lookup"><span data-stu-id="7efa5-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="7efa5-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="7efa5-106">Required.</span></span> <span data-ttu-id="7efa5-107">任何`String`變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="7efa5-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="7efa5-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="7efa5-108">Required.</span></span> <span data-ttu-id="7efa5-109">任何 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="7efa5-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7efa5-110">備註</span><span class="sxs-lookup"><span data-stu-id="7efa5-110">Remarks</span></span>  
 <span data-ttu-id="7efa5-111">在左邊的項目`&=`運算子可以是簡單的純量變數、 屬性或陣列項目。</span><span class="sxs-lookup"><span data-stu-id="7efa5-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="7efa5-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="7efa5-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="7efa5-113">`&=`運算子會串連`String`運算式，其權限來上的`String`變數或屬性，它的左邊，並將結果指派給變數或屬性與其左邊。</span><span class="sxs-lookup"><span data-stu-id="7efa5-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7efa5-114">多載化</span><span class="sxs-lookup"><span data-stu-id="7efa5-114">Overloading</span></span>  
 <span data-ttu-id="7efa5-115">[& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="7efa5-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7efa5-116">多載`&`運算子會影響的行為`&=`運算子。</span><span class="sxs-lookup"><span data-stu-id="7efa5-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="7efa5-117">如果您的程式碼會使用`&=`上類別或結構，多載`&`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="7efa5-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7efa5-118">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="7efa5-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7efa5-119">範例</span><span class="sxs-lookup"><span data-stu-id="7efa5-119">Example</span></span>  
 <span data-ttu-id="7efa5-120">下列範例會使用`&=`運算子來串連兩個`String`變數並指派給第一個變數的結果。</span><span class="sxs-lookup"><span data-stu-id="7efa5-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7efa5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7efa5-121">See also</span></span>
- [<span data-ttu-id="7efa5-122">& 運算子</span><span class="sxs-lookup"><span data-stu-id="7efa5-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="7efa5-123">+= 運算子</span><span class="sxs-lookup"><span data-stu-id="7efa5-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="7efa5-124">指派運算子</span><span class="sxs-lookup"><span data-stu-id="7efa5-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="7efa5-125">串連運算子</span><span class="sxs-lookup"><span data-stu-id="7efa5-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="7efa5-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="7efa5-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7efa5-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="7efa5-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="7efa5-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="7efa5-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
