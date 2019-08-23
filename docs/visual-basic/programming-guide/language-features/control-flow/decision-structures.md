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
ms.openlocfilehash: f0df649c4be50e9cadd51258c89137b68b4ffe22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963191"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="96b12-102">決策結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96b12-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="96b12-103">Visual Basic 可讓您測試條件, 並根據該測試的結果來執行不同的作業。</span><span class="sxs-lookup"><span data-stu-id="96b12-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="96b12-104">您可以針對運算式的各種值, 或在執行一連串語句時產生的各種例外狀況, 測試條件為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="96b12-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="96b12-105">下圖顯示的決策結構會測試條件是否為 true, 並根據其為 true 或 false 來採取不同的動作。</span><span class="sxs-lookup"><span data-stu-id="96b12-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![If ... 的流程圖然後 .。。Else 結構。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="96b12-107">如果 .。。然後 .。。Else 結構</span><span class="sxs-lookup"><span data-stu-id="96b12-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="96b12-108">`If...Then...Else`[結構] 可讓您測試一或多個條件, 並根據每個條件執行一或多個語句。</span><span class="sxs-lookup"><span data-stu-id="96b12-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="96b12-109">您可以透過下列方式來測試條件並採取動作:</span><span class="sxs-lookup"><span data-stu-id="96b12-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="96b12-110">如果條件為, 請執行一或多個語句`True`</span><span class="sxs-lookup"><span data-stu-id="96b12-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="96b12-111">如果條件為, 請執行一或多個語句`False`</span><span class="sxs-lookup"><span data-stu-id="96b12-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="96b12-112">如果條件為`True` , 且其他語句為, 則執行`False`</span><span class="sxs-lookup"><span data-stu-id="96b12-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="96b12-113">如果先前的條件為, 請測試其他條件`False`</span><span class="sxs-lookup"><span data-stu-id="96b12-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="96b12-114">提供所有這些可能性的控制結構是[If .。。然後 .。。Else 語句](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="96b12-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="96b12-115">如果您只有一個測試和一個語句要執行, 則可以使用單行版本。</span><span class="sxs-lookup"><span data-stu-id="96b12-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="96b12-116">如果您有一組更複雜的條件和動作, 則可以使用多行版本。</span><span class="sxs-lookup"><span data-stu-id="96b12-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="96b12-117">選取 .。。案例結構</span><span class="sxs-lookup"><span data-stu-id="96b12-117">Select...Case Construction</span></span>  
 <span data-ttu-id="96b12-118">此`Select...Case`結構可讓您評估一次運算式, 並根據不同的可能值來執行不同的語句集。</span><span class="sxs-lookup"><span data-stu-id="96b12-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="96b12-119">如需詳細資訊, 請參閱[Select .。。Case 語句](../../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="96b12-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="96b12-120">嘗試 .。。Catch .。。最後結構</span><span class="sxs-lookup"><span data-stu-id="96b12-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="96b12-121">`Try...Catch...Finally`結構可讓您在環境中執行一組語句, 如果其中任何一個語句造成例外狀況, 就會保留控制項。</span><span class="sxs-lookup"><span data-stu-id="96b12-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="96b12-122">您可以針對不同的例外狀況採取不同的動作。</span><span class="sxs-lookup"><span data-stu-id="96b12-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="96b12-123">您可以選擇性地指定在結束整個`Try...Catch...Finally`結構之前執行的程式碼區塊, 無論發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="96b12-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="96b12-124">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="96b12-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96b12-125">對於許多控制項結構而言, 當您按一下關鍵字時, 結構中的所有關鍵詞都會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="96b12-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="96b12-126">`If`例如, 當您`If...Then...Else`在`If`結構中按一下時, 會反白顯示`Then`結構中`Else`、、 `End If` `ElseIf`、和的所有實例。</span><span class="sxs-lookup"><span data-stu-id="96b12-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="96b12-127">若要移至下一個或上一個反白顯示的關鍵字, 請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="96b12-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b12-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96b12-128">See also</span></span>

- [<span data-ttu-id="96b12-129">控制流程</span><span class="sxs-lookup"><span data-stu-id="96b12-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="96b12-130">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="96b12-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="96b12-131">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="96b12-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="96b12-132">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="96b12-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="96b12-133">If 運算子</span><span class="sxs-lookup"><span data-stu-id="96b12-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
