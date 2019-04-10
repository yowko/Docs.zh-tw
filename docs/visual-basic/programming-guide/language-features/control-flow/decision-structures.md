---
title: 決策結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 4a76b2565c343e69ac3c11441035a7682a8f08ec
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318932"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="79821-102">決策結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79821-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="79821-103">Visual Basic 可讓您測試條件，並執行不同的作業，視該測試的結果而定。</span><span class="sxs-lookup"><span data-stu-id="79821-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="79821-104">您可以測試條件為 true 或 false，針對各種不同值的運算式，或當您執行一系列的陳述式時，產生的各種例外狀況。</span><span class="sxs-lookup"><span data-stu-id="79821-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="79821-105">下圖顯示測試條件為 true，並採用不同的動作，取決於它是否為 true 或 false 的決策結構。</span><span class="sxs-lookup"><span data-stu-id="79821-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![如果流量圖表...Then...其他建構。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="79821-107">If...Then...其他建構</span><span class="sxs-lookup"><span data-stu-id="79821-107">If...Then...Else Construction</span></span>  
 `If...Then...Else` <span data-ttu-id="79821-108">建構可讓您測試一或多個條件，並執行一或多個陳述式，根據每個條件。</span><span class="sxs-lookup"><span data-stu-id="79821-108">constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="79821-109">您可以測試條件，並以下列方式來採取動作：</span><span class="sxs-lookup"><span data-stu-id="79821-109">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="79821-110">如果條件為，執行一或多個陳述式</span><span class="sxs-lookup"><span data-stu-id="79821-110">Run one or more statements if a condition is</span></span> `True`  
  
-   <span data-ttu-id="79821-111">如果條件為，執行一或多個陳述式</span><span class="sxs-lookup"><span data-stu-id="79821-111">Run one or more statements if a condition is</span></span> `False`  
  
-   <span data-ttu-id="79821-112">執行某些陳述式，如果條件為`True`和其他人是否</span><span class="sxs-lookup"><span data-stu-id="79821-112">Run some statements if a condition is `True` and others if it is</span></span> `False`  
  
-   <span data-ttu-id="79821-113">測試其他狀況，如果先前的條件</span><span class="sxs-lookup"><span data-stu-id="79821-113">Test an additional condition if a prior condition is</span></span> `False`  
  
 <span data-ttu-id="79821-114">提供所有這些可能性的控制結構是[如果...Then...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="79821-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="79821-115">如果您有一個測試和執行一個陳述式，您可以使用單行的版本。</span><span class="sxs-lookup"><span data-stu-id="79821-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="79821-116">如果您有一組更複雜的條件和動作，您可以使用多行版本。</span><span class="sxs-lookup"><span data-stu-id="79821-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="79821-117">選取此項目...案例的建構</span><span class="sxs-lookup"><span data-stu-id="79821-117">Select...Case Construction</span></span>  
 <span data-ttu-id="79821-118">`Select...Case`建構可讓您評估運算式一次，並執行不同的陳述式，根據不同的可能值。</span><span class="sxs-lookup"><span data-stu-id="79821-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="79821-119">如需詳細資訊，請參閱[選取...Case 陳述式](../../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="79821-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="79821-120">再試...Catch...最後的建構</span><span class="sxs-lookup"><span data-stu-id="79821-120">Try...Catch...Finally Construction</span></span>  
 `Try...Catch...Finally` <span data-ttu-id="79821-121">建構可讓您執行一組保留控制項，如果陳述式的任何一個造成例外狀況環境下的陳述式。</span><span class="sxs-lookup"><span data-stu-id="79821-121">constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="79821-122">您可以採取不同的例外狀況的不同動作。</span><span class="sxs-lookup"><span data-stu-id="79821-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="79821-123">您可以選擇性地指定前結束的整個執行的程式碼區塊`Try...Catch...Finally`建構，不論發生的動作。</span><span class="sxs-lookup"><span data-stu-id="79821-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="79821-124">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="79821-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79821-125">許多控制項結構，當您按一下關鍵字的所有關鍵字在結構中反白顯示。</span><span class="sxs-lookup"><span data-stu-id="79821-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="79821-126">比方說，當您按一下 `If`中`If...Then...Else`建構、 所有執行個體`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="79821-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="79821-127">若要移到下一個或上一個反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="79821-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79821-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79821-128">See also</span></span>

- [<span data-ttu-id="79821-129">控制流程</span><span class="sxs-lookup"><span data-stu-id="79821-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="79821-130">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="79821-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="79821-131">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="79821-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="79821-132">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="79821-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="79821-133">If 運算子</span><span class="sxs-lookup"><span data-stu-id="79821-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
