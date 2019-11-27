---
title: 決策結構
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: d0d4039ff2edc61ee8b4b732c6adcb6e420d73ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353968"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="135de-102">決策結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="135de-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="135de-103">Visual Basic 可讓您測試條件，並根據該測試的結果來執行不同的作業。</span><span class="sxs-lookup"><span data-stu-id="135de-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="135de-104">您可以針對運算式的各種值，或在執行一連串語句時產生的各種例外狀況，測試條件為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="135de-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="135de-105">下圖顯示的決策結構會測試條件是否為 true，並根據其為 true 或 false 來採取不同的動作。</span><span class="sxs-lookup"><span data-stu-id="135de-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![If...Then...Else 結構。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="135de-107">If...Then...Else 結構</span><span class="sxs-lookup"><span data-stu-id="135de-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="135de-108">`If...Then...Else` 結構可讓您測試一或多個條件，並根據每個條件執行一或多個語句。</span><span class="sxs-lookup"><span data-stu-id="135de-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="135de-109">您可以透過下列方式來測試條件並採取動作：</span><span class="sxs-lookup"><span data-stu-id="135de-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="135de-110">如果條件 `True`，請執行一或多個語句</span><span class="sxs-lookup"><span data-stu-id="135de-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="135de-111">如果條件 `False`，請執行一或多個語句</span><span class="sxs-lookup"><span data-stu-id="135de-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="135de-112">如果條件 `True`，則執行一些語句，如果是 `False` 則為其他語句</span><span class="sxs-lookup"><span data-stu-id="135de-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="135de-113">如果先前的條件 `False`，請測試其他條件</span><span class="sxs-lookup"><span data-stu-id="135de-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="135de-114">提供所有這些可能性的控制結構是[If .。。然後 .。。Else 語句](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="135de-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="135de-115">如果您只有一個測試和一個語句要執行，則可以使用單行版本。</span><span class="sxs-lookup"><span data-stu-id="135de-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="135de-116">如果您有一組更複雜的條件和動作，則可以使用多行版本。</span><span class="sxs-lookup"><span data-stu-id="135de-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="135de-117">Select...Case 結構</span><span class="sxs-lookup"><span data-stu-id="135de-117">Select...Case Construction</span></span>  
 <span data-ttu-id="135de-118">`Select...Case` 結構可讓您評估一次運算式，並根據不同的可能值來執行不同的語句集。</span><span class="sxs-lookup"><span data-stu-id="135de-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="135de-119">如需詳細資訊，請參閱[Select .。。Case 語句](../../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="135de-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="135de-120">Try...Catch...Finally 結構</span><span class="sxs-lookup"><span data-stu-id="135de-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="135de-121">`Try...Catch...Finally` 結構可讓您在環境中執行一組語句，如果其中任何一個語句造成例外狀況，就會保留控制。</span><span class="sxs-lookup"><span data-stu-id="135de-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="135de-122">您可以針對不同的例外狀況採取不同的動作。</span><span class="sxs-lookup"><span data-stu-id="135de-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="135de-123">您可以選擇性地指定在結束整個 `Try...Catch...Finally` 結構之前執行的程式碼區塊，而不論發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="135de-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="135de-124">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="135de-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="135de-125">對於許多控制項結構而言，當您按一下關鍵字時，結構中的所有關鍵詞都會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="135de-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="135de-126">例如，當您在 `If...Then...Else` 結構中按一下 `If` 時，會反白顯示該結構中 `If`、`Then`、`ElseIf`、`Else`和 `End If` 的所有實例。</span><span class="sxs-lookup"><span data-stu-id="135de-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="135de-127">若要移至下一個或上一個反白顯示的關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="135de-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="135de-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="135de-128">See also</span></span>

- [<span data-ttu-id="135de-129">控制流程</span><span class="sxs-lookup"><span data-stu-id="135de-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="135de-130">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="135de-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="135de-131">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="135de-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="135de-132">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="135de-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="135de-133">If 運算子</span><span class="sxs-lookup"><span data-stu-id="135de-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
