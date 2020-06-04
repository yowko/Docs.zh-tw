---
title: <<= 運算子
ms.date: 07/20/2015
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
ms.openlocfilehash: ff7cbb02a9a10dbe11450491e93fd85fd77b44ba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370657"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2b232-102">\<\<= 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2b232-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="2b232-103">在變數或屬性的值上執行算術左移位，並將結果指派回變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="2b232-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b232-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b232-104">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="2b232-105">組件</span><span class="sxs-lookup"><span data-stu-id="2b232-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2b232-106">必要。</span><span class="sxs-lookup"><span data-stu-id="2b232-106">Required.</span></span> <span data-ttu-id="2b232-107">整數類資料類型的變數或屬性（ `SByte` 、 `Byte` 、、、 `Short` `UShort` `Integer` 、 `UInteger` 、 `Long` 或 `ULong` ）。</span><span class="sxs-lookup"><span data-stu-id="2b232-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="2b232-108">必要。</span><span class="sxs-lookup"><span data-stu-id="2b232-108">Required.</span></span> <span data-ttu-id="2b232-109">擴展至之資料類型的數值運算式 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="2b232-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b232-110">備註</span><span class="sxs-lookup"><span data-stu-id="2b232-110">Remarks</span></span>  
 <span data-ttu-id="2b232-111">運算子左邊的元素 `<<=` 可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="2b232-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2b232-112">變數或屬性不可為[ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="2b232-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="2b232-113">`<<=`運算子會先在變數或屬性的值上執行算術左移位。</span><span class="sxs-lookup"><span data-stu-id="2b232-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="2b232-114">然後，運算子會將該作業的結果指派回該變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="2b232-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="2b232-115">算術移位不是迴圈的，這表示不會在另一端重新進入從結果的一端移位的位。</span><span class="sxs-lookup"><span data-stu-id="2b232-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="2b232-116">在算術左移位中，會捨棄超出結果資料類型範圍的位，而且右邊空出的位位置會設定為零。</span><span class="sxs-lookup"><span data-stu-id="2b232-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2b232-117">多載化</span><span class="sxs-lookup"><span data-stu-id="2b232-117">Overloading</span></span>  
 <span data-ttu-id="2b232-118">[<< 運算子](left-shift-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="2b232-118">The [<< Operator](left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2b232-119">多載 `<<` 運算子會影響運算子的行為 `<<=` 。</span><span class="sxs-lookup"><span data-stu-id="2b232-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="2b232-120">如果您的程式碼在多載 `<<=` 的類別或結構上使用 `<<` ，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="2b232-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2b232-121">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="2b232-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b232-122">範例</span><span class="sxs-lookup"><span data-stu-id="2b232-122">Example</span></span>  
 <span data-ttu-id="2b232-123">下列範例會使用 `<<=` 運算子，將變數的位模式 `Integer` 向左移位指定的數量，並將結果指派給變數。</span><span class="sxs-lookup"><span data-stu-id="2b232-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="2b232-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b232-124">See also</span></span>

- [<span data-ttu-id="2b232-125"><< 運算子</span><span class="sxs-lookup"><span data-stu-id="2b232-125"><< Operator</span></span>](left-shift-operator.md)
- [<span data-ttu-id="2b232-126">指派運算子</span><span class="sxs-lookup"><span data-stu-id="2b232-126">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="2b232-127">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="2b232-127">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="2b232-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="2b232-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="2b232-129">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="2b232-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="2b232-130">陳述式</span><span class="sxs-lookup"><span data-stu-id="2b232-130">Statements</span></span>](../../programming-guide/language-features/statements.md)
