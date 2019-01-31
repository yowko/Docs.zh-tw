---
title: '>>= 運算子 (Visual Basic)'
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
ms.openlocfilehash: 0ea1e03168da12564f148f525af977f29a43bec8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265281"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e9f54-102">>>= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9f54-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="e9f54-103">執行算術右移位的變數或屬性的值，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f54-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f54-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9f54-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="e9f54-105">組件</span><span class="sxs-lookup"><span data-stu-id="e9f54-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e9f54-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="e9f54-106">Required.</span></span> <span data-ttu-id="e9f54-107">變數或屬性的整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="e9f54-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="e9f54-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="e9f54-108">Required.</span></span> <span data-ttu-id="e9f54-109">數值運算式的資料類型可擴展成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="e9f54-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9f54-110">備註</span><span class="sxs-lookup"><span data-stu-id="e9f54-110">Remarks</span></span>  
 <span data-ttu-id="e9f54-111">在左邊的項目`>>=`運算子可以是簡單的純量變數、 屬性或陣列項目。</span><span class="sxs-lookup"><span data-stu-id="e9f54-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e9f54-112">變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f54-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e9f54-113">`>>=`運算子會先執行算術右移位的變數或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e9f54-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="e9f54-114">然後，運算子會將該作業的結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f54-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="e9f54-115">算術的排班不是循環，這表示移出結果的某一端的位元不會重新引入另一端。</span><span class="sxs-lookup"><span data-stu-id="e9f54-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="e9f54-116">在算術右移位，移位超過最右邊位元位置的位元會予以捨棄，並最左邊的位元會傳播到左邊空出的位元位置。</span><span class="sxs-lookup"><span data-stu-id="e9f54-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="e9f54-117">這表示如果`variableorproperty`的值是負數，空出的位置會設定為其中一個。</span><span class="sxs-lookup"><span data-stu-id="e9f54-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="e9f54-118">如果`variableorproperty`是正數，或其資料類型是不帶正負號的型別，如果空出的位置會設定為零。</span><span class="sxs-lookup"><span data-stu-id="e9f54-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e9f54-119">多載化</span><span class="sxs-lookup"><span data-stu-id="e9f54-119">Overloading</span></span>  
 <span data-ttu-id="e9f54-120">[>> 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="e9f54-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e9f54-121">多載`>>`運算子會影響的行為`>>=`運算子。</span><span class="sxs-lookup"><span data-stu-id="e9f54-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="e9f54-122">如果您的程式碼會使用`>>=`上類別或結構，多載`>>`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="e9f54-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e9f54-123">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f54-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9f54-124">範例</span><span class="sxs-lookup"><span data-stu-id="e9f54-124">Example</span></span>  
 <span data-ttu-id="e9f54-125">下列範例會使用`>>=`要移位的位元模式的運算子`Integer`變數權限指派給變數的結果與指定的數量。</span><span class="sxs-lookup"><span data-stu-id="e9f54-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e9f54-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f54-126">See also</span></span>
- [<span data-ttu-id="e9f54-127">>> 運算子</span><span class="sxs-lookup"><span data-stu-id="e9f54-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="e9f54-128">指派運算子</span><span class="sxs-lookup"><span data-stu-id="e9f54-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="e9f54-129">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="e9f54-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="e9f54-130">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="e9f54-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e9f54-131">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="e9f54-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e9f54-132">陳述式</span><span class="sxs-lookup"><span data-stu-id="e9f54-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
