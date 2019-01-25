---
title: = 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 58dcdfd21fd8701c6ac391672e768819f696aab9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643544"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3c65d-102">= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c65d-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="3c65d-103">將值指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="3c65d-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c65d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c65d-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="3c65d-105">組件</span><span class="sxs-lookup"><span data-stu-id="3c65d-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="3c65d-106">任何可寫入的變數或任何屬性。</span><span class="sxs-lookup"><span data-stu-id="3c65d-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="3c65d-107">任何常值、 常數或運算式。</span><span class="sxs-lookup"><span data-stu-id="3c65d-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c65d-108">備註</span><span class="sxs-lookup"><span data-stu-id="3c65d-108">Remarks</span></span>  
 <span data-ttu-id="3c65d-109">等號左邊的項目 (`=`) 可以是簡單的純量變數、 屬性或陣列項目。</span><span class="sxs-lookup"><span data-stu-id="3c65d-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="3c65d-110">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="3c65d-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="3c65d-111">`=`運算子會將指派給變數，其右邊的值，或是與其左邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c65d-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c65d-112">`=`運算子也可以用做為比較運算子。</span><span class="sxs-lookup"><span data-stu-id="3c65d-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="3c65d-113">如需詳細資訊，請參閱 <<c0> [ 比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="3c65d-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3c65d-114">多載化</span><span class="sxs-lookup"><span data-stu-id="3c65d-114">Overloading</span></span>  
 <span data-ttu-id="3c65d-115">`=`運算子可以多載，只為關係比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="3c65d-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="3c65d-116">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="3c65d-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c65d-117">範例</span><span class="sxs-lookup"><span data-stu-id="3c65d-117">Example</span></span>  
 <span data-ttu-id="3c65d-118">下列範例示範使用指派運算子。</span><span class="sxs-lookup"><span data-stu-id="3c65d-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="3c65d-119">在右側的值指派給左邊的變數。</span><span class="sxs-lookup"><span data-stu-id="3c65d-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3c65d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c65d-120">See also</span></span>
- [<span data-ttu-id="3c65d-121">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="3c65d-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="3c65d-122">\*= 運算子</span><span class="sxs-lookup"><span data-stu-id="3c65d-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="3c65d-123">+= 運算子</span><span class="sxs-lookup"><span data-stu-id="3c65d-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="3c65d-124">-= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c65d-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="3c65d-125">/ = 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c65d-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="3c65d-126">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="3c65d-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="3c65d-127">^= 運算子</span><span class="sxs-lookup"><span data-stu-id="3c65d-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="3c65d-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="3c65d-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="3c65d-129">比較運算子</span><span class="sxs-lookup"><span data-stu-id="3c65d-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="3c65d-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="3c65d-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="3c65d-131">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="3c65d-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
