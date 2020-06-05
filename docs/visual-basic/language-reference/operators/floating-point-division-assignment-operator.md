---
title: /= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 48ae78630aa66ad804d539f88524c456cf805889
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371241"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="67569-102">/= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67569-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="67569-103">將變數或屬性的值除以運算式的值，並將浮點結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="67569-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67569-104">語法</span><span class="sxs-lookup"><span data-stu-id="67569-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="67569-105">組件</span><span class="sxs-lookup"><span data-stu-id="67569-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="67569-106">必要。</span><span class="sxs-lookup"><span data-stu-id="67569-106">Required.</span></span> <span data-ttu-id="67569-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="67569-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="67569-108">必要。</span><span class="sxs-lookup"><span data-stu-id="67569-108">Required.</span></span> <span data-ttu-id="67569-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="67569-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67569-110">備註</span><span class="sxs-lookup"><span data-stu-id="67569-110">Remarks</span></span>  
 <span data-ttu-id="67569-111">運算子左邊的元素 `/=` 可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="67569-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="67569-112">變數或屬性不可為[ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="67569-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="67569-113">`/=`運算子會先將變數或屬性的值（位於運算子的左邊）除以運算式的值（在運算子的右邊），然後再將它隔開。</span><span class="sxs-lookup"><span data-stu-id="67569-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="67569-114">然後，運算子會將該運算的浮點結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="67569-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="67569-115">這個語句會將 `Double` 值指派給左邊的變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="67569-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="67569-116">如果 `Option Strict` 為 `On` ，則 `variableorproperty` 必須是 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="67569-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="67569-117">如果 `Option Strict` 為 `Off` ，Visual Basic 會執行隱含轉換，並將產生的值指派給 `variableorproperty` ，並在執行時間發生可能的錯誤。</span><span class="sxs-lookup"><span data-stu-id="67569-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="67569-118">如需詳細資訊，請參閱[擴展和縮小轉換](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[Option Strict 語句](../statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="67569-118">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="67569-119">多載化</span><span class="sxs-lookup"><span data-stu-id="67569-119">Overloading</span></span>  
 <span data-ttu-id="67569-120">[/運算子（Visual Basic）](floating-point-division-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="67569-120">The [/ Operator (Visual Basic)](floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="67569-121">多載 `/` 運算子會影響運算子的行為 `/=` 。</span><span class="sxs-lookup"><span data-stu-id="67569-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="67569-122">如果您的程式碼在多載 `/=` 的類別或結構上使用 `/` ，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="67569-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="67569-123">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="67569-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67569-124">範例</span><span class="sxs-lookup"><span data-stu-id="67569-124">Example</span></span>  
 <span data-ttu-id="67569-125">下列範例會使用運算子，將 `/=` 一個 `Integer` 變數除以一秒，並將該商指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="67569-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="67569-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67569-126">See also</span></span>

- [<span data-ttu-id="67569-127">/運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="67569-127">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="67569-128">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="67569-128">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="67569-129">指派運算子</span><span class="sxs-lookup"><span data-stu-id="67569-129">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="67569-130">算術運算子</span><span class="sxs-lookup"><span data-stu-id="67569-130">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="67569-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="67569-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="67569-132">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="67569-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="67569-133">陳述式</span><span class="sxs-lookup"><span data-stu-id="67569-133">Statements</span></span>](../../programming-guide/language-features/statements.md)
