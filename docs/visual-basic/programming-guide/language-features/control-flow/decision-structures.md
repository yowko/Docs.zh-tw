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
ms.openlocfilehash: 20b60fb425278dacb56ee5f888967554a1f76aeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825374"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="472e6-102">決策結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="472e6-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="472e6-103">Visual Basic 可讓您測試條件，並執行不同的作業，視該測試的結果而定。</span><span class="sxs-lookup"><span data-stu-id="472e6-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="472e6-104">您可以測試條件為 true 或 false，針對各種不同值的運算式，或當您執行一系列的陳述式時，產生的各種例外狀況。</span><span class="sxs-lookup"><span data-stu-id="472e6-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="472e6-105">下圖顯示測試條件為 true，並採用不同的動作，取決於它是否為 true 或 false 的決策結構。</span><span class="sxs-lookup"><span data-stu-id="472e6-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="472e6-106">![流程圖表的 If...Then...其他建構](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span><span class="sxs-lookup"><span data-stu-id="472e6-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="472e6-107">當條件為 true，且當為 false 時，採取不同的動作</span><span class="sxs-lookup"><span data-stu-id="472e6-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="472e6-108">If...Then...其他建構</span><span class="sxs-lookup"><span data-stu-id="472e6-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="472e6-109">`If...Then...Else` 建構可讓您測試一或多個條件，並執行一或多個陳述式，根據每個條件。</span><span class="sxs-lookup"><span data-stu-id="472e6-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="472e6-110">您可以測試條件，並以下列方式來採取動作：</span><span class="sxs-lookup"><span data-stu-id="472e6-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="472e6-111">如果條件為，執行一或多個陳述式 `True`</span><span class="sxs-lookup"><span data-stu-id="472e6-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="472e6-112">如果條件為，執行一或多個陳述式 `False`</span><span class="sxs-lookup"><span data-stu-id="472e6-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="472e6-113">執行某些陳述式，如果條件為`True`和其他人是否 `False`</span><span class="sxs-lookup"><span data-stu-id="472e6-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="472e6-114">測試其他狀況，如果先前的條件 `False`</span><span class="sxs-lookup"><span data-stu-id="472e6-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="472e6-115">提供所有這些可能性的控制結構是[如果...Then...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="472e6-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="472e6-116">如果您有一個測試和執行一個陳述式，您可以使用單行的版本。</span><span class="sxs-lookup"><span data-stu-id="472e6-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="472e6-117">如果您有一組更複雜的條件和動作，您可以使用多行版本。</span><span class="sxs-lookup"><span data-stu-id="472e6-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="472e6-118">選取此項目...案例的建構</span><span class="sxs-lookup"><span data-stu-id="472e6-118">Select...Case Construction</span></span>  
 <span data-ttu-id="472e6-119">`Select...Case`建構可讓您評估運算式一次，並執行不同的陳述式，根據不同的可能值。</span><span class="sxs-lookup"><span data-stu-id="472e6-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="472e6-120">如需詳細資訊，請參閱[選取...Case 陳述式](../../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="472e6-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="472e6-121">再試...Catch...最後的建構</span><span class="sxs-lookup"><span data-stu-id="472e6-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="472e6-122">`Try...Catch...Finally` 建構可讓您執行一組保留控制項，如果陳述式的任何一個造成例外狀況環境下的陳述式。</span><span class="sxs-lookup"><span data-stu-id="472e6-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="472e6-123">您可以採取不同的例外狀況的不同動作。</span><span class="sxs-lookup"><span data-stu-id="472e6-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="472e6-124">您可以選擇性地指定前結束的整個執行的程式碼區塊`Try...Catch...Finally`建構，不論發生的動作。</span><span class="sxs-lookup"><span data-stu-id="472e6-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="472e6-125">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="472e6-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="472e6-126">許多控制項結構，當您按一下關鍵字的所有關鍵字在結構中反白顯示。</span><span class="sxs-lookup"><span data-stu-id="472e6-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="472e6-127">比方說，當您按一下 `If`中`If...Then...Else`建構、 所有執行個體`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="472e6-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="472e6-128">若要移到下一個或上一個反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="472e6-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="472e6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="472e6-129">See also</span></span>

- [<span data-ttu-id="472e6-130">控制流程</span><span class="sxs-lookup"><span data-stu-id="472e6-130">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="472e6-131">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="472e6-131">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="472e6-132">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="472e6-132">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="472e6-133">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="472e6-133">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="472e6-134">If 運算子</span><span class="sxs-lookup"><span data-stu-id="472e6-134">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
