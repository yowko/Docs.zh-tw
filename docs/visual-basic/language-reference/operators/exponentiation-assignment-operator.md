---
title: ^= 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 382e0b27c2dbf27e5acccf29f1b8d2b002cb6664
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592228"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="156b1-102">^= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="156b1-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="156b1-103">將變數或屬性的值引發至運算式的乘冪，並將結果指派回變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="156b1-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="156b1-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="156b1-105">組件</span><span class="sxs-lookup"><span data-stu-id="156b1-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="156b1-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="156b1-106">Required.</span></span> <span data-ttu-id="156b1-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="156b1-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="156b1-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="156b1-108">Required.</span></span> <span data-ttu-id="156b1-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="156b1-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="156b1-110">備註</span><span class="sxs-lookup"><span data-stu-id="156b1-110">Remarks</span></span>  
 <span data-ttu-id="156b1-111">@No__t-0 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="156b1-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="156b1-112">變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="156b1-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="156b1-113">@No__t-0 運算子會先將變數或屬性的值（位於運算子的左邊），提升為運算式值的乘冪（位於運算子的右邊）。</span><span class="sxs-lookup"><span data-stu-id="156b1-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="156b1-114">然後，運算子會將該作業的結果指派回變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="156b1-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="156b1-115">Visual Basic 一律會執行[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)的乘冪。</span><span class="sxs-lookup"><span data-stu-id="156b1-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="156b1-116">任何不同類型的運算元都會轉換成 `Double`，而結果一律 `Double`。</span><span class="sxs-lookup"><span data-stu-id="156b1-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="156b1-117">@No__t-0 的值可以是小數、負數或兩者。</span><span class="sxs-lookup"><span data-stu-id="156b1-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="156b1-118">多載化</span><span class="sxs-lookup"><span data-stu-id="156b1-118">Overloading</span></span>  
 <span data-ttu-id="156b1-119">[^ 運算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="156b1-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="156b1-120">多載 `^` 運算子會影響 `^=` 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="156b1-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="156b1-121">如果您的程式碼在多載 `^` 的類別或結構上使用 `^=`，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="156b1-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="156b1-122">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="156b1-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="156b1-123">範例</span><span class="sxs-lookup"><span data-stu-id="156b1-123">Example</span></span>  
 <span data-ttu-id="156b1-124">下列範例會使用 `^=` 運算子，將一個 @no__t 1 變數的值提升為第二個變數的乘冪，並將結果指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="156b1-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="156b1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="156b1-125">See also</span></span>

- [<span data-ttu-id="156b1-126">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="156b1-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="156b1-127">指派運算子</span><span class="sxs-lookup"><span data-stu-id="156b1-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="156b1-128">算術運算子</span><span class="sxs-lookup"><span data-stu-id="156b1-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="156b1-129">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="156b1-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="156b1-130">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="156b1-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="156b1-131">陳述式</span><span class="sxs-lookup"><span data-stu-id="156b1-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
