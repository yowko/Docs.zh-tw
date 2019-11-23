---
title: '>>= 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352000"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="86b27-102">>>= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86b27-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="86b27-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="86b27-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b27-104">語法</span><span class="sxs-lookup"><span data-stu-id="86b27-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="86b27-105">組件</span><span class="sxs-lookup"><span data-stu-id="86b27-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="86b27-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="86b27-106">Required.</span></span> <span data-ttu-id="86b27-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span><span class="sxs-lookup"><span data-stu-id="86b27-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="86b27-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="86b27-108">Required.</span></span> <span data-ttu-id="86b27-109">Numeric expression of a data type that widens to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="86b27-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86b27-110">備註</span><span class="sxs-lookup"><span data-stu-id="86b27-110">Remarks</span></span>  
 <span data-ttu-id="86b27-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="86b27-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="86b27-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="86b27-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="86b27-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span><span class="sxs-lookup"><span data-stu-id="86b27-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="86b27-114">The operator then assigns the result of that operation back to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="86b27-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="86b27-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span><span class="sxs-lookup"><span data-stu-id="86b27-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="86b27-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span><span class="sxs-lookup"><span data-stu-id="86b27-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="86b27-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span><span class="sxs-lookup"><span data-stu-id="86b27-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="86b27-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span><span class="sxs-lookup"><span data-stu-id="86b27-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="86b27-119">多載化</span><span class="sxs-lookup"><span data-stu-id="86b27-119">Overloading</span></span>  
 <span data-ttu-id="86b27-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="86b27-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="86b27-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span><span class="sxs-lookup"><span data-stu-id="86b27-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="86b27-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="86b27-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="86b27-123">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="86b27-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86b27-124">範例</span><span class="sxs-lookup"><span data-stu-id="86b27-124">Example</span></span>  
 <span data-ttu-id="86b27-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span><span class="sxs-lookup"><span data-stu-id="86b27-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="86b27-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="86b27-126">See also</span></span>

- [<span data-ttu-id="86b27-127">>> 運算子</span><span class="sxs-lookup"><span data-stu-id="86b27-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="86b27-128">指派運算子</span><span class="sxs-lookup"><span data-stu-id="86b27-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="86b27-129">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="86b27-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="86b27-130">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="86b27-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="86b27-131">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="86b27-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="86b27-132">陳述式</span><span class="sxs-lookup"><span data-stu-id="86b27-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
