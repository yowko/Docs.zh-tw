---
title: 如何：計算數值 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 322e2c9fe7f668e08a42cd707c5d81090aca627c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="811e6-102">如何：計算數值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="811e6-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="811e6-103">您可以計算數字的值，透過使用數值運算式。</span><span class="sxs-lookup"><span data-stu-id="811e6-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="811e6-104">A*數值運算式*是運算式包含常值、 常數和變數代表數字的值，並執行以這些值的運算子。</span><span class="sxs-lookup"><span data-stu-id="811e6-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="811e6-105">計算數值</span><span class="sxs-lookup"><span data-stu-id="811e6-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="811e6-106">若要計算數字的值</span><span class="sxs-lookup"><span data-stu-id="811e6-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="811e6-107">結合的數值運算式的一或多個數值常值、 常數和變數。</span><span class="sxs-lookup"><span data-stu-id="811e6-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="811e6-108">下列範例顯示一些有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="811e6-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="811e6-109">前三個行顯示常值、 常數和變數。</span><span class="sxs-lookup"><span data-stu-id="811e6-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="811e6-110">每個本身構成有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="811e6-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="811e6-111">最後一行示範具有兩個常值的變數的組合。</span><span class="sxs-lookup"><span data-stu-id="811e6-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="811e6-112">請注意數值的運算式不會構成完整的 Visual Basic 陳述式本身。</span><span class="sxs-lookup"><span data-stu-id="811e6-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="811e6-113">您必須使用運算式做為完整的陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="811e6-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="811e6-114">若要儲存數字的值</span><span class="sxs-lookup"><span data-stu-id="811e6-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="811e6-115">您可以使用在指派陳述式指派值給變數，數值運算式所表示，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="811e6-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     <span data-ttu-id="811e6-116">在上述範例中，「 等於 」 運算子右邊的運算式值 (`=`) 指派給變數`j`運算子左側讓`j`276 評估結果。</span><span class="sxs-lookup"><span data-stu-id="811e6-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="811e6-117">如需詳細資訊，請參閱[陳述式](../../../../visual-basic/language-reference/statements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="811e6-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="811e6-118">多個運算子</span><span class="sxs-lookup"><span data-stu-id="811e6-118">Multiple Operators</span></span>  
 <span data-ttu-id="811e6-119">如果數字的運算式包含多個運算子，它們的評估的順序取決於運算子優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="811e6-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="811e6-120">若要覆寫的運算子優先順序的規則，您括住運算式括號，如同上述範例中。會先評估括住的運算式。</span><span class="sxs-lookup"><span data-stu-id="811e6-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="811e6-121">若要覆寫一般運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="811e6-121">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="811e6-122">您可以使用括號括住您想要先執行的作業。</span><span class="sxs-lookup"><span data-stu-id="811e6-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="811e6-123">下列範例會示範兩個不同的結果，具有相同的運算元和運算子。</span><span class="sxs-lookup"><span data-stu-id="811e6-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     <span data-ttu-id="811e6-124">在上述範例中，計算`j`執行加法運算子 (`+`) 第一個因為前後的括號`(67 + i)`一般優先順序，以及指派給的值會覆寫`j`是 276 (4 次 69)。</span><span class="sxs-lookup"><span data-stu-id="811e6-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="811e6-125">計算`k`執行其一般優先順序的運算子 (`*`之前`+`)，並指派給的值`k`為 270 （268 加上 2）。</span><span class="sxs-lookup"><span data-stu-id="811e6-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="811e6-126">如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="811e6-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="811e6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="811e6-127">See Also</span></span>  
 [<span data-ttu-id="811e6-128">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="811e6-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="811e6-129">數值比較</span><span class="sxs-lookup"><span data-stu-id="811e6-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="811e6-130">陳述式</span><span class="sxs-lookup"><span data-stu-id="811e6-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="811e6-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="811e6-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="811e6-132">算術運算子</span><span class="sxs-lookup"><span data-stu-id="811e6-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="811e6-133">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="811e6-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
