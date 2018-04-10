---
title: '&lt;&lt;= 運算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c5c36e4f91155c09d01b448777483941d018d9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="d7f2b-102">&lt;&lt;= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7f2b-102">&lt;&lt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="d7f2b-103">變數或屬性的值上執行算術左的移位並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7f2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7f2b-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="d7f2b-105">組件</span><span class="sxs-lookup"><span data-stu-id="d7f2b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d7f2b-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-106">Required.</span></span> <span data-ttu-id="d7f2b-107">變數或屬性的整數類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="d7f2b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-108">Required.</span></span> <span data-ttu-id="d7f2b-109">數值運算式的資料類型可擴展成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7f2b-110">備註</span><span class="sxs-lookup"><span data-stu-id="d7f2b-110">Remarks</span></span>  
 <span data-ttu-id="d7f2b-111">在左邊的項目`<<=`運算子可以是簡單的純量變數、 屬性或陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d7f2b-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d7f2b-113">`<<=`運算子會先執行算術左的移位的變數或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="d7f2b-114">然後，運算子會將該作業的結果指派給該變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="d7f2b-115">算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="d7f2b-116">在算術左移位，移位超出結果資料類型之範圍的位元會捨棄，而且右方空出的位元位置會設定為零。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d7f2b-117">多載化</span><span class="sxs-lookup"><span data-stu-id="d7f2b-117">Overloading</span></span>  
 <span data-ttu-id="d7f2b-118">[<< 運算子](../../../visual-basic/language-reference/operators/left-shift-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d7f2b-119">多載`<<`運算子會影響行為`<<=`運算子。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="d7f2b-120">如果您的程式碼使用`<<=`上類別或結構的多載`<<`，確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d7f2b-121">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7f2b-122">範例</span><span class="sxs-lookup"><span data-stu-id="d7f2b-122">Example</span></span>  
 <span data-ttu-id="d7f2b-123">下列範例會使用`<<=`要移位的位元模式的運算子`Integer`變數向左程式指定的數量並指派結果給變數。</span><span class="sxs-lookup"><span data-stu-id="d7f2b-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d7f2b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7f2b-124">See Also</span></span>  
 [<span data-ttu-id="d7f2b-125"><< 運算子</span><span class="sxs-lookup"><span data-stu-id="d7f2b-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)  
 [<span data-ttu-id="d7f2b-126">指派運算子</span><span class="sxs-lookup"><span data-stu-id="d7f2b-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="d7f2b-127">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="d7f2b-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="d7f2b-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="d7f2b-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d7f2b-129">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="d7f2b-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d7f2b-130">陳述式</span><span class="sxs-lookup"><span data-stu-id="d7f2b-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
