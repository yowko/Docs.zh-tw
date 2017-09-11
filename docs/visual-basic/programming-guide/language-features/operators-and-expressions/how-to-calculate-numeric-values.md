---
title: "如何︰ 計算數值 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations, numeric expressions
- precedence, of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fe781cca8f716c792d3af153b2004c716bc87f90
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="3bbe8-102">如何：計算數值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bbe8-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="3bbe8-103">您可以計算數字的值，透過使用數值運算式。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="3bbe8-104">A*數值運算式*運算式包含常值、 常數和變數表示數字的值，並處理那些值的運算子。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="3bbe8-105">計算數值</span><span class="sxs-lookup"><span data-stu-id="3bbe8-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="3bbe8-106">若要計算數值</span><span class="sxs-lookup"><span data-stu-id="3bbe8-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="3bbe8-107">結合的數值運算式的一個或多個數值常值、 常數和變數。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="3bbe8-108">下列範例顯示一些有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="3bbe8-109">前三行顯示常值、 常數和變數。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="3bbe8-110">每個本身構成有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="3bbe8-111">最後一行會顯示兩個常值的變數的組合。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="3bbe8-112">請注意，數值的運算式不會構成完整[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]陳述式本身。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statement by itself.</span></span> <span data-ttu-id="3bbe8-113">您必須使用運算式做為完整的陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="3bbe8-114">若要儲存數值</span><span class="sxs-lookup"><span data-stu-id="3bbe8-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="3bbe8-115">您可以使用在指派陳述式來指派給變數，數值運算式所代表的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     <span data-ttu-id="3bbe8-116">[!code-vb[VbVbalrOperators #&82;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3bbe8-116">[!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span></span>  
  
     <span data-ttu-id="3bbe8-117">在上述範例中，「 等於 」 運算子的右邊顯示運算式的值 (`=`) 指派給變數`j`運算子的左邊，`j`評估為 276。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-117">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="3bbe8-118">如需詳細資訊，請參閱[陳述式](../../../../visual-basic/language-reference/statements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-118">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="3bbe8-119">多個運算子</span><span class="sxs-lookup"><span data-stu-id="3bbe8-119">Multiple Operators</span></span>  
 <span data-ttu-id="3bbe8-120">如果數值的運算式包含多個運算子，它們的評估的順序取決於運算子優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-120">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="3bbe8-121">若要覆寫運算子優先順序規則，您運算式括號括住，如上述範例中;會先評估括住的運算式。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-121">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="3bbe8-122">若要覆寫一般運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="3bbe8-122">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="3bbe8-123">您可以使用括號括住您想要先執行的作業。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-123">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="3bbe8-124">下列範例顯示具有相同的運算元和運算子的兩個不同的結果。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-124">The following example shows two different results with the same operands and operators.</span></span>  
  
     <span data-ttu-id="3bbe8-125">[!code-vb[VbVbalrOperators #&83;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3bbe8-125">[!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span></span>  
  
     <span data-ttu-id="3bbe8-126">在上述範例中，計算`j`執行加法運算子 (`+`) 第一個因為前後的括號`(67 + i)`覆寫一般優先順序，與指派給值`j`為 276 (4 次 69)。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-126">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="3bbe8-127">其計算方式`k`運算子會執行其一般優先順序 (`*`之前`+`)，並指派給值`k`為 270 （268 加 2）。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-127">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="3bbe8-128">如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="3bbe8-128">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbe8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bbe8-129">See Also</span></span>  
 <span data-ttu-id="3bbe8-130">[運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="3bbe8-130">[Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="3bbe8-131"> [值的比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="3bbe8-131"> [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="3bbe8-132"> [陳述式](../../../../visual-basic/language-reference/statements/index.md) </span><span class="sxs-lookup"><span data-stu-id="3bbe8-132"> [Statements](../../../../visual-basic/language-reference/statements/index.md) </span></span>  
<span data-ttu-id="3bbe8-133"> [在 Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="3bbe8-133"> [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="3bbe8-134"> [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="3bbe8-134"> [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="3bbe8-135"> [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span><span class="sxs-lookup"><span data-stu-id="3bbe8-135"> [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span></span>
