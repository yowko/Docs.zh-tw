---
title: 迴圈結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: b72eef632b4564abc69e6ebef43b940eb0950e9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523385"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="e190a-102">迴圈結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e190a-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="e190a-103">Visual Basic 迴圈結構可讓您重複執行一或多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e190a-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="e190a-104">您可以重複迴圈結構中的陳述式，直到條件為`True`，直到條件為`False`，集合中指定的次數，或是每個項目都執行過一次。</span><span class="sxs-lookup"><span data-stu-id="e190a-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="e190a-105">下圖顯示迴圈結構，其會執行一組陳述式，直到條件變成 true。</span><span class="sxs-lookup"><span data-stu-id="e190a-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="e190a-106">![重複執行相同動作的流程圖表...Until 迴圈](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="e190a-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="e190a-107">執行一組陳述式，直到條件變成 true</span><span class="sxs-lookup"><span data-stu-id="e190a-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="e190a-108">While 迴圈</span><span class="sxs-lookup"><span data-stu-id="e190a-108">While Loops</span></span>  
 <span data-ttu-id="e190a-109">`While`...`End While`建構執行的一組陳述式，只要在指定的條件`While`陳述式是`True`。</span><span class="sxs-lookup"><span data-stu-id="e190a-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="e190a-110">如需詳細資訊，請參閱[時...結束 While 陳述式](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e190a-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="e190a-111">Do 迴圈</span><span class="sxs-lookup"><span data-stu-id="e190a-111">Do Loops</span></span>  
 <span data-ttu-id="e190a-112">`Do`...`Loop`建構可讓您測試開頭或結尾的迴圈結構的條件。</span><span class="sxs-lookup"><span data-stu-id="e190a-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="e190a-113">您也可以指定是否要重複迴圈條件維持`True`或直到它變成`True`。</span><span class="sxs-lookup"><span data-stu-id="e190a-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="e190a-114">如需詳細資訊，請參閱[執行...迴圈陳述式](../../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e190a-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="e190a-115">For 迴圈</span><span class="sxs-lookup"><span data-stu-id="e190a-115">For Loops</span></span>  
 <span data-ttu-id="e190a-116">`For`...`Next`建構執行迴圈固定數目的時間。</span><span class="sxs-lookup"><span data-stu-id="e190a-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="e190a-117">它會使用迴圈控制變數，也稱為*計數器*、 追蹤的重複項目。</span><span class="sxs-lookup"><span data-stu-id="e190a-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="e190a-118">您指定的開始和結束值，這個計數器，以及您可以選擇性地指定的數量的它會增加重複一次從到下一步。</span><span class="sxs-lookup"><span data-stu-id="e190a-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="e190a-119">如需詳細資訊，請參閱[For...下一個陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e190a-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="e190a-120">For Each 迴圈</span><span class="sxs-lookup"><span data-stu-id="e190a-120">For Each Loops</span></span>  
 <span data-ttu-id="e190a-121">`For Each`...`Next`建構在集合中執行一組陳述式，針對每個項目執行一次。</span><span class="sxs-lookup"><span data-stu-id="e190a-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="e190a-122">指定迴圈控制變數，但您沒有啟動或結束值，判斷。</span><span class="sxs-lookup"><span data-stu-id="e190a-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="e190a-123">如需詳細資訊，請參閱[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e190a-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e190a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e190a-124">See also</span></span>
- [<span data-ttu-id="e190a-125">控制流程</span><span class="sxs-lookup"><span data-stu-id="e190a-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="e190a-126">決策結構</span><span class="sxs-lookup"><span data-stu-id="e190a-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="e190a-127">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="e190a-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="e190a-128">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="e190a-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
