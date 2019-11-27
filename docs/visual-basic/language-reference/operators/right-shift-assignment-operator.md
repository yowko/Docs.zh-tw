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
# <a name="-operator-visual-basic"></a><span data-ttu-id="94942-102">> > = 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="94942-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="94942-103">在變數或屬性的值上執行算術右移，並將結果指派回變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="94942-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94942-104">語法</span><span class="sxs-lookup"><span data-stu-id="94942-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="94942-105">組件</span><span class="sxs-lookup"><span data-stu-id="94942-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="94942-106">必要。</span><span class="sxs-lookup"><span data-stu-id="94942-106">Required.</span></span> <span data-ttu-id="94942-107">整數類資料類型的變數或屬性（`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`或 `ULong`）。</span><span class="sxs-lookup"><span data-stu-id="94942-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="94942-108">必要。</span><span class="sxs-lookup"><span data-stu-id="94942-108">Required.</span></span> <span data-ttu-id="94942-109">擴展為 `Integer`之資料類型的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="94942-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94942-110">備註</span><span class="sxs-lookup"><span data-stu-id="94942-110">Remarks</span></span>  
 <span data-ttu-id="94942-111">`>>=` 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="94942-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="94942-112">變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="94942-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="94942-113">`>>=` 運算子會先在變數或屬性的值上執行算術右移位。</span><span class="sxs-lookup"><span data-stu-id="94942-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="94942-114">然後，運算子會將該作業的結果指派回變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="94942-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="94942-115">算術移位不是迴圈的，這表示不會在另一端重新進入從結果的一端移位的位。</span><span class="sxs-lookup"><span data-stu-id="94942-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="94942-116">在算術右移位中，會捨棄超出最右邊位位置的位，而最左邊的位會傳播到左側空出的位位置。</span><span class="sxs-lookup"><span data-stu-id="94942-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="94942-117">這表示如果 `variableorproperty` 的值為負值，則空出的位置會設定為一個。</span><span class="sxs-lookup"><span data-stu-id="94942-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="94942-118">如果 `variableorproperty` 是正數，或其資料類型是不帶正負號的類型，則空出的位置會設定為零。</span><span class="sxs-lookup"><span data-stu-id="94942-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="94942-119">多載化</span><span class="sxs-lookup"><span data-stu-id="94942-119">Overloading</span></span>  
 <span data-ttu-id="94942-120">[> > 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)*可以多載，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="94942-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="94942-121">多載 `>>` 運算子會影響 `>>=` 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="94942-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="94942-122">如果您的程式碼在多載 `>>`的類別或結構上使用 `>>=`，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="94942-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="94942-123">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="94942-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94942-124">範例</span><span class="sxs-lookup"><span data-stu-id="94942-124">Example</span></span>  
 <span data-ttu-id="94942-125">下列範例會使用 `>>=` 運算子，將 `Integer` 變數的位模式右移指定的數量，並將結果指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="94942-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="94942-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="94942-126">See also</span></span>

- [<span data-ttu-id="94942-127">>> 運算子</span><span class="sxs-lookup"><span data-stu-id="94942-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="94942-128">指派運算子</span><span class="sxs-lookup"><span data-stu-id="94942-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="94942-129">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="94942-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="94942-130">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="94942-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="94942-131">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="94942-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="94942-132">陳述式</span><span class="sxs-lookup"><span data-stu-id="94942-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
