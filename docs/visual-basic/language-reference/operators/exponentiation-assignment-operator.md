---
title: ^= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: a956ffdaa3456ed09443f25c3383b6aab52fb5bf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867062"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="221d4-102">^= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="221d4-102">^= Operator (Visual Basic)</span></span>

<span data-ttu-id="221d4-103">將變數或屬性的值引發至運算式的功能，並將結果指派回變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="221d4-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221d4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="221d4-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="221d4-105">組件</span><span class="sxs-lookup"><span data-stu-id="221d4-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="221d4-106">必要。</span><span class="sxs-lookup"><span data-stu-id="221d4-106">Required.</span></span> <span data-ttu-id="221d4-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="221d4-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="221d4-108">必要。</span><span class="sxs-lookup"><span data-stu-id="221d4-108">Required.</span></span> <span data-ttu-id="221d4-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="221d4-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="221d4-110">備註</span><span class="sxs-lookup"><span data-stu-id="221d4-110">Remarks</span></span>  

 <span data-ttu-id="221d4-111">運算子左邊的元素 `^=` 可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="221d4-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="221d4-112">變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="221d4-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="221d4-113">`^=`運算子會先將運算子左邊的變數或屬性值 (，) 為運算子右邊的運算式 (值的乘冪的值) 的最右邊。</span><span class="sxs-lookup"><span data-stu-id="221d4-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="221d4-114">然後，運算子會將該作業的結果指派回變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="221d4-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="221d4-115">Visual Basic 一律會執行 [Double 資料類型](../data-types/double-data-type.md)的乘冪。</span><span class="sxs-lookup"><span data-stu-id="221d4-115">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span> <span data-ttu-id="221d4-116">任何不同類型的運算元都會轉換成 `Double` ，而且結果一律為 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="221d4-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="221d4-117">的值 `expression` 可以是小數、負數或兩者。</span><span class="sxs-lookup"><span data-stu-id="221d4-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="221d4-118">多載化</span><span class="sxs-lookup"><span data-stu-id="221d4-118">Overloading</span></span>  

 <span data-ttu-id="221d4-119">您可以多載 [^ 運算子](exponentiation-operator.md) ，這表示當運算元的類型為該類別或結構 *時，類別*或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="221d4-119">The [^ Operator](exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="221d4-120">多載 `^` 運算子會影響運算子的行為 `^=` 。</span><span class="sxs-lookup"><span data-stu-id="221d4-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="221d4-121">如果您的程式碼在多載的 `^=` 類別或結構上使用 `^` ，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="221d4-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="221d4-122">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="221d4-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="221d4-123">範例</span><span class="sxs-lookup"><span data-stu-id="221d4-123">Example</span></span>  

 <span data-ttu-id="221d4-124">下列範例會使用 `^=` 運算子將某個變數的值提升 `Integer` 為第二個變數的乘冪，然後將結果指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="221d4-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="221d4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="221d4-125">See also</span></span>

- [<span data-ttu-id="221d4-126">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="221d4-126">^ Operator</span></span>](exponentiation-operator.md)
- [<span data-ttu-id="221d4-127">指派運算子</span><span class="sxs-lookup"><span data-stu-id="221d4-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="221d4-128">算術運算子</span><span class="sxs-lookup"><span data-stu-id="221d4-128">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="221d4-129">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="221d4-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="221d4-130">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="221d4-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="221d4-131">陳述式</span><span class="sxs-lookup"><span data-stu-id="221d4-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
