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
ms.openlocfilehash: d260dffb7175e9dddcbf9acb75415f5f973727e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962008"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="23998-102">= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23998-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="23998-103">將值指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="23998-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23998-104">語法</span><span class="sxs-lookup"><span data-stu-id="23998-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="23998-105">組件</span><span class="sxs-lookup"><span data-stu-id="23998-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="23998-106">任何可寫入的變數或任何屬性。</span><span class="sxs-lookup"><span data-stu-id="23998-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="23998-107">任何常值、常數或運算式。</span><span class="sxs-lookup"><span data-stu-id="23998-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23998-108">備註</span><span class="sxs-lookup"><span data-stu-id="23998-108">Remarks</span></span>  
 <span data-ttu-id="23998-109">等號 (`=`) 左邊的元素可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="23998-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="23998-110">變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="23998-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="23998-111">`=`運算子會將其右邊的值指派給其左邊的變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="23998-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23998-112">`=`運算子也會用來做為比較運算子。</span><span class="sxs-lookup"><span data-stu-id="23998-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="23998-113">如需詳細資訊, 請參閱[比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="23998-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="23998-114">多載化</span><span class="sxs-lookup"><span data-stu-id="23998-114">Overloading</span></span>  
 <span data-ttu-id="23998-115">`=`運算子只能多載為關聯式比較運算子, 而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="23998-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="23998-116">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="23998-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23998-117">範例</span><span class="sxs-lookup"><span data-stu-id="23998-117">Example</span></span>  
 <span data-ttu-id="23998-118">下列範例示範指派運算子。</span><span class="sxs-lookup"><span data-stu-id="23998-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="23998-119">右邊的值會指派給左邊的變數。</span><span class="sxs-lookup"><span data-stu-id="23998-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="23998-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23998-120">See also</span></span>

- [<span data-ttu-id="23998-121">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="23998-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="23998-122">\*= 運算子</span><span class="sxs-lookup"><span data-stu-id="23998-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="23998-123">+= 運算子</span><span class="sxs-lookup"><span data-stu-id="23998-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="23998-124">-= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23998-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="23998-125">/= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23998-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="23998-126">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="23998-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="23998-127">^= 運算子</span><span class="sxs-lookup"><span data-stu-id="23998-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="23998-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="23998-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="23998-129">比較運算子</span><span class="sxs-lookup"><span data-stu-id="23998-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="23998-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="23998-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="23998-131">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="23998-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
