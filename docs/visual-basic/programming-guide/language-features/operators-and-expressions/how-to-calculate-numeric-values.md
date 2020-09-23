---
title: 如何：計算數值
ms.date: 07/20/2015
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
ms.openlocfilehash: 452a8392b46f0c25b6ad2a8a30c51071f2ae1d93
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071712"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="8e3b0-102">如何：計算數值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e3b0-102">How to: Calculate Numeric Values (Visual Basic)</span></span>

<span data-ttu-id="8e3b0-103">您可以透過使用數值運算式來計算數值。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="8e3b0-104">*數值運算式*是包含常值、常數和變數的運算式，這些變數表示數值，以及處理這些值的運算子。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="8e3b0-105">計算數值</span><span class="sxs-lookup"><span data-stu-id="8e3b0-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="8e3b0-106">計算數值</span><span class="sxs-lookup"><span data-stu-id="8e3b0-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="8e3b0-107">將一或多個數值常值、常數和變數合併為數值運算式。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="8e3b0-108">下列範例顯示一些有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="8e3b0-109">前三行會顯示常值、常數和變數。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="8e3b0-110">每一個都形成一個有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="8e3b0-111">最後一行顯示具有兩個常值之變數的組合。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="8e3b0-112">請注意，數值運算式本身不會形成完整的 Visual Basic 語句。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="8e3b0-113">您必須使用運算式做為完整語句的一部分。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="8e3b0-114">若要儲存數值</span><span class="sxs-lookup"><span data-stu-id="8e3b0-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="8e3b0-115">您可以使用指派語句，將數值運算式所表示的值指派給變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="8e3b0-116">在上述範例中，等號運算子右邊的運算式值 (`=`) 會指派給 `j` 運算子左邊的變數，所以會 `j` 評估為276。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="8e3b0-117">如需詳細資訊，請參閱[陳述式](../../../language-reference/statements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-117">For more information, see [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="8e3b0-118">多個運算子</span><span class="sxs-lookup"><span data-stu-id="8e3b0-118">Multiple Operators</span></span>  

 <span data-ttu-id="8e3b0-119">如果數值運算式包含一個以上的運算子，則評估它們的順序是由運算子優先順序的規則來決定。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="8e3b0-120">若要覆寫運算子優先順序的規則，您可以用括弧括住運算式，如上述範例所示：會先評估包含的運算式。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="8e3b0-121">覆寫一般運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="8e3b0-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="8e3b0-122">使用括弧來括住您想要先執行的作業。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="8e3b0-123">下列範例顯示兩個具有相同運算元和運算子的不同結果。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="8e3b0-124">在上述範例中， `j` 會先執行加法運算子 (`+`) ，因為覆 `(67 + i)` 寫一般優先順序的括弧和指派給的值 `j` 為 276 (4 倍 69) 。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="8e3b0-125">在 `k`) 之前，的計算會在其一般優先順序 `*` (`+` ，而指派給的值 `k` 為 270 (268 加 2) 。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="8e3b0-126">如需詳細資訊，請參閱 [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="8e3b0-126">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3b0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e3b0-127">See also</span></span>

- [<span data-ttu-id="8e3b0-128">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="8e3b0-128">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="8e3b0-129">數值比較</span><span class="sxs-lookup"><span data-stu-id="8e3b0-129">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="8e3b0-130">陳述式</span><span class="sxs-lookup"><span data-stu-id="8e3b0-130">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="8e3b0-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="8e3b0-131">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8e3b0-132">算術運算子</span><span class="sxs-lookup"><span data-stu-id="8e3b0-132">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="8e3b0-133">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="8e3b0-133">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
