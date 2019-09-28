---
title: '&amp; = 運算子（Visual Basic）'
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
ms.openlocfilehash: 82d791e5d66c301442c99d2cc73e3172c3e30f17
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591629"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="a63e4-102">&amp; = 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a63e4-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="a63e4-103">將 `String` 運算式串連至 @no__t 1 變數或屬性，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="a63e4-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="a63e4-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a63e4-105">組件</span><span class="sxs-lookup"><span data-stu-id="a63e4-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="a63e4-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="a63e4-106">Required.</span></span> <span data-ttu-id="a63e4-107">任何 @no__t 0 變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="a63e4-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="a63e4-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="a63e4-108">Required.</span></span> <span data-ttu-id="a63e4-109">任何 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="a63e4-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a63e4-110">備註</span><span class="sxs-lookup"><span data-stu-id="a63e4-110">Remarks</span></span>  
 <span data-ttu-id="a63e4-111">@No__t-0 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="a63e4-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a63e4-112">變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="a63e4-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="a63e4-113">@No__t-0 運算子會將其右邊的 `String` 運算式串連至其左邊的 @no__t 2 變數或屬性，並將結果指派給其左邊的變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="a63e4-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a63e4-114">多載化</span><span class="sxs-lookup"><span data-stu-id="a63e4-114">Overloading</span></span>  
 <span data-ttu-id="a63e4-115">[& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="a63e4-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a63e4-116">多載 `&` 運算子會影響 `&=` 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="a63e4-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="a63e4-117">如果您的程式碼在多載 `&` 的類別或結構上使用 `&=`，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="a63e4-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a63e4-118">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a63e4-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a63e4-119">範例</span><span class="sxs-lookup"><span data-stu-id="a63e4-119">Example</span></span>  
 <span data-ttu-id="a63e4-120">下列範例會使用 `&=` 運算子來串連兩個 @no__t 1 的變數，並將結果指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="a63e4-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a63e4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a63e4-121">See also</span></span>

- [<span data-ttu-id="a63e4-122">& 運算子</span><span class="sxs-lookup"><span data-stu-id="a63e4-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="a63e4-123">+= 運算子</span><span class="sxs-lookup"><span data-stu-id="a63e4-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="a63e4-124">指派運算子</span><span class="sxs-lookup"><span data-stu-id="a63e4-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="a63e4-125">串連運算子</span><span class="sxs-lookup"><span data-stu-id="a63e4-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="a63e4-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="a63e4-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a63e4-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="a63e4-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a63e4-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="a63e4-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
