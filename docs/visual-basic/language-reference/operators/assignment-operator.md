---
title: "= 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
dev_langs:
- VB
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
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
ms.openlocfilehash: 46dc9e6018cf2ae71f1fc6dc2b8f19c2f0aadb62
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2f6aa-102">= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f6aa-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="2f6aa-103">指派值給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f6aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f6aa-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="2f6aa-105">組件</span><span class="sxs-lookup"><span data-stu-id="2f6aa-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2f6aa-106">任何可寫入的變數或任何屬性。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="2f6aa-107">任何常值、 常數或運算式。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f6aa-108">備註</span><span class="sxs-lookup"><span data-stu-id="2f6aa-108">Remarks</span></span>  
 <span data-ttu-id="2f6aa-109">等號左邊的項目 (`=`) 可以是簡單的純量變數、 屬性或陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2f6aa-110">變數或屬性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="2f6aa-111">`=`運算子會將指派其權限給變數的值或與其左邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f6aa-112">`=`運算子也可以用做為比較運算子。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="2f6aa-113">如需詳細資訊，請參閱[比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2f6aa-114">多載化</span><span class="sxs-lookup"><span data-stu-id="2f6aa-114">Overloading</span></span>  
 <span data-ttu-id="2f6aa-115">`=`運算子可以多載僅做為關聯式比較運算子，而非指派運算子。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="2f6aa-116">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f6aa-117">範例</span><span class="sxs-lookup"><span data-stu-id="2f6aa-117">Example</span></span>  
 <span data-ttu-id="2f6aa-118">下列範例示範設定運算子。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="2f6aa-119">在右邊的值指派給左邊的變數。</span><span class="sxs-lookup"><span data-stu-id="2f6aa-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 <span data-ttu-id="2f6aa-120">[!code-vb[VbVbalrOperators #&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f6aa-120">[!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6aa-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f6aa-121">See Also</span></span>  
 <span data-ttu-id="2f6aa-122">[I = 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-122">[&= Operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span></span>  
<span data-ttu-id="2f6aa-123"> [* = 運算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-123"> [*= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span></span>  
<span data-ttu-id="2f6aa-124"> [+ = 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-124"> [+= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span></span>  
<span data-ttu-id="2f6aa-125"> [-= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-125"> [-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) </span></span>  
<span data-ttu-id="2f6aa-126"> [/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-126"> [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span></span>  
<span data-ttu-id="2f6aa-127"> [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-127"> [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span></span>  
<span data-ttu-id="2f6aa-128"> [^ = 運算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-128"> [^= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span></span>  
<span data-ttu-id="2f6aa-129"> [陳述式](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-129"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="2f6aa-130"> [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-130"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="2f6aa-131"> [唯讀](../../../visual-basic/language-reference/modifiers/readonly.md) </span><span class="sxs-lookup"><span data-stu-id="2f6aa-131"> [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) </span></span>  
<span data-ttu-id="2f6aa-132"> [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="2f6aa-132"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>

