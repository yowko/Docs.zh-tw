---
title: "決策結構 (Visual Basic) |Microsoft 文件"
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
- statements [Visual Basic], control flow
- If statement, decision structures
- If statement, If...Then...Else
- control flow, decision structures
- decision structures
- conditional statements, decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
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
ms.openlocfilehash: dcbfb4bc3318d5f79870d04e606fab8bfa2dafb9
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="22ab9-102">決策結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22ab9-102">Decision Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="22ab9-103">可讓您測試條件，並執行不同的作業，根據該測試的結果。</span><span class="sxs-lookup"><span data-stu-id="22ab9-103"> lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="22ab9-104">您可以測試條件為 true 或 false，針對各種不同值的運算式，或當您執行一系列的陳述式時，產生的各種例外狀況。</span><span class="sxs-lookup"><span data-stu-id="22ab9-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="22ab9-105">下圖顯示測試條件為 true，會採用不同的動作，取決於為 true 或 false 的決策結構。</span><span class="sxs-lookup"><span data-stu-id="22ab9-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="22ab9-106">![If 的流程圖...然後...其他建構](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span><span class="sxs-lookup"><span data-stu-id="22ab9-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="22ab9-107">條件為 true，而且是 false 時，採取不同動作</span><span class="sxs-lookup"><span data-stu-id="22ab9-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="22ab9-108">如果...然後...其他建構</span><span class="sxs-lookup"><span data-stu-id="22ab9-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="22ab9-109">`If...Then...Else`語法結構，可讓您測試一個或多個條件，並執行一或多個陳述式，根據每個條件。</span><span class="sxs-lookup"><span data-stu-id="22ab9-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="22ab9-110">您可以測試條件，並以下列方式採取動作︰</span><span class="sxs-lookup"><span data-stu-id="22ab9-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="22ab9-111">如果條件為，執行一或多個陳述式`True`</span><span class="sxs-lookup"><span data-stu-id="22ab9-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="22ab9-112">如果條件為，執行一或多個陳述式`False`</span><span class="sxs-lookup"><span data-stu-id="22ab9-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="22ab9-113">執行某些陳述式，如果條件為`True`和其他人是否`False`</span><span class="sxs-lookup"><span data-stu-id="22ab9-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="22ab9-114">如果先前的條件是，測試其他狀況`False`</span><span class="sxs-lookup"><span data-stu-id="22ab9-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="22ab9-115">提供所有這些可能性的控制結構是[如果...然後...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="22ab9-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="22ab9-116">如果您有一個測試和執行一個陳述式，您可以使用單行版本。</span><span class="sxs-lookup"><span data-stu-id="22ab9-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="22ab9-117">如果您有一組更複雜的條件和動作，您可以使用多行版本。</span><span class="sxs-lookup"><span data-stu-id="22ab9-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="22ab9-118">選取 [...]Case 建構</span><span class="sxs-lookup"><span data-stu-id="22ab9-118">Select...Case Construction</span></span>  
 <span data-ttu-id="22ab9-119">`Select...Case`建構可讓您評估運算式一次，並執行不同的陳述式，根據不同的可能值。</span><span class="sxs-lookup"><span data-stu-id="22ab9-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="22ab9-120">如需詳細資訊，請參閱[選取...Case 陳述式](../../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="22ab9-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="22ab9-121">請嘗試...Catch...最後的建構</span><span class="sxs-lookup"><span data-stu-id="22ab9-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="22ab9-122">`Try...Catch...Finally`語法結構，可讓您執行一組保留控制項，如果任何一個陳述式會導致例外狀況的環境下的陳述式。</span><span class="sxs-lookup"><span data-stu-id="22ab9-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="22ab9-123">您可以採取不同的例外狀況的不同動作。</span><span class="sxs-lookup"><span data-stu-id="22ab9-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="22ab9-124">您可以選擇性地指定一段程式碼執行之前結束整個`Try...Catch...Finally`建構，不論執行的動作。</span><span class="sxs-lookup"><span data-stu-id="22ab9-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="22ab9-125">如需詳細資訊，請參閱[試...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="22ab9-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22ab9-126">許多控制項結構，當您按一下關鍵字，所有的關鍵字，在結構中反白顯示。</span><span class="sxs-lookup"><span data-stu-id="22ab9-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="22ab9-127">比方說，當您按一下`If`中`If...Then...Else`建構，而所有執行個體的`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="22ab9-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="22ab9-128">若要移至下一個或上一個反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。</span><span class="sxs-lookup"><span data-stu-id="22ab9-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ab9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22ab9-129">See Also</span></span>  
 <span data-ttu-id="22ab9-130">[控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="22ab9-130">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="22ab9-131"> [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="22ab9-131"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="22ab9-132"> [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="22ab9-132"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="22ab9-133"> [巢狀的控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="22ab9-133"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="22ab9-134"> [If 運算子](../../../../visual-basic/language-reference/operators/if-operator.md)</span><span class="sxs-lookup"><span data-stu-id="22ab9-134"> [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)</span></span>
