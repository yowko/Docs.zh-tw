---
title: "&gt;&gt;= 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7e388471b9adf424c55b1ad1042e5aed1ea8ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="d4c77-102">&gt;&gt;= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c77-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="d4c77-103">執行算術右移位的變數或屬性的值，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="d4c77-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c77-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4c77-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="d4c77-105">組件</span><span class="sxs-lookup"><span data-stu-id="d4c77-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d4c77-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="d4c77-106">Required.</span></span> <span data-ttu-id="d4c77-107">變數或屬性的整數類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="d4c77-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="d4c77-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="d4c77-108">Required.</span></span> <span data-ttu-id="d4c77-109">數值運算式的資料類型可擴展成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="d4c77-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4c77-110">備註</span><span class="sxs-lookup"><span data-stu-id="d4c77-110">Remarks</span></span>  
 <span data-ttu-id="d4c77-111">在左邊的項目`>>=`運算子可以是簡單的純量變數、 屬性或陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="d4c77-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d4c77-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c77-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d4c77-113">`>>=`運算子會先執行算術右移位的變數或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d4c77-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="d4c77-114">然後，運算子會將該作業的結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="d4c77-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="d4c77-115">算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。</span><span class="sxs-lookup"><span data-stu-id="d4c77-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="d4c77-116">在算術右移位，移位超過右邊的位元位置的位元會捨棄，並最左邊的位元會傳播到左邊空出的位元位置。</span><span class="sxs-lookup"><span data-stu-id="d4c77-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="d4c77-117">這表示如果`variableorproperty`負值，空出的位置會設定為其中一個。</span><span class="sxs-lookup"><span data-stu-id="d4c77-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="d4c77-118">如果`variableorproperty`是正數，或其資料類型是不帶正負號的類型，如果空出的位置會設定為零。</span><span class="sxs-lookup"><span data-stu-id="d4c77-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d4c77-119">多載化</span><span class="sxs-lookup"><span data-stu-id="d4c77-119">Overloading</span></span>  
 <span data-ttu-id="d4c77-120">[>> 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="d4c77-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d4c77-121">多載`>>`運算子會影響行為`>>=`運算子。</span><span class="sxs-lookup"><span data-stu-id="d4c77-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="d4c77-122">如果您的程式碼使用`>>=`上類別或結構的多載`>>`，確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="d4c77-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d4c77-123">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c77-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c77-124">範例</span><span class="sxs-lookup"><span data-stu-id="d4c77-124">Example</span></span>  
 <span data-ttu-id="d4c77-125">下列範例會使用`>>=`要移位的位元模式的運算子`Integer`向右旋轉指定的數量並指派結果給變數的變數。</span><span class="sxs-lookup"><span data-stu-id="d4c77-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d4c77-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4c77-126">See Also</span></span>  
 [<span data-ttu-id="d4c77-127">>> 運算子</span><span class="sxs-lookup"><span data-stu-id="d4c77-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="d4c77-128">指派運算子</span><span class="sxs-lookup"><span data-stu-id="d4c77-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="d4c77-129">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="d4c77-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="d4c77-130">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="d4c77-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d4c77-131">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="d4c77-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d4c77-132">陳述式</span><span class="sxs-lookup"><span data-stu-id="d4c77-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
