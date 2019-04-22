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
ms.openlocfilehash: 56165eecce5e73c4e06235dac1691774fb39b794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833296"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="bcac7-102">迴圈結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcac7-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="bcac7-103">Visual Basic 迴圈結構可讓您重複執行一或多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="bcac7-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="bcac7-104">您可以重複迴圈結構中的陳述式，直到條件為`True`，直到條件為`False`，集合中指定的次數，或是每個項目都執行過一次。</span><span class="sxs-lookup"><span data-stu-id="bcac7-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="bcac7-105">下圖顯示迴圈結構，其會執行一組陳述式，直到條件變成 true:</span><span class="sxs-lookup"><span data-stu-id="bcac7-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![顯示執行的流程圖...Until 迴圈。](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="bcac7-107">While 迴圈</span><span class="sxs-lookup"><span data-stu-id="bcac7-107">While Loops</span></span>  
 <span data-ttu-id="bcac7-108">`While`...`End While`建構執行的一組陳述式，只要在指定的條件`While`陳述式是`True`。</span><span class="sxs-lookup"><span data-stu-id="bcac7-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="bcac7-109">如需詳細資訊，請參閱[時...結束 While 陳述式](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bcac7-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="bcac7-110">Do 迴圈</span><span class="sxs-lookup"><span data-stu-id="bcac7-110">Do Loops</span></span>  
 <span data-ttu-id="bcac7-111">`Do`...`Loop`建構可讓您測試開頭或結尾的迴圈結構的條件。</span><span class="sxs-lookup"><span data-stu-id="bcac7-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="bcac7-112">您也可以指定是否要重複迴圈條件維持`True`或直到它變成`True`。</span><span class="sxs-lookup"><span data-stu-id="bcac7-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="bcac7-113">如需詳細資訊，請參閱[執行...迴圈陳述式](../../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bcac7-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="bcac7-114">For 迴圈</span><span class="sxs-lookup"><span data-stu-id="bcac7-114">For Loops</span></span>  
 <span data-ttu-id="bcac7-115">`For`...`Next`建構執行迴圈固定數目的時間。</span><span class="sxs-lookup"><span data-stu-id="bcac7-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="bcac7-116">它會使用迴圈控制變數，也稱為*計數器*、 追蹤的重複項目。</span><span class="sxs-lookup"><span data-stu-id="bcac7-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="bcac7-117">您指定的開始和結束值，這個計數器，以及您可以選擇性地指定的數量的它會增加重複一次從到下一步。</span><span class="sxs-lookup"><span data-stu-id="bcac7-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="bcac7-118">如需詳細資訊，請參閱[For...下一個陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bcac7-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="bcac7-119">For Each 迴圈</span><span class="sxs-lookup"><span data-stu-id="bcac7-119">For Each Loops</span></span>  
 <span data-ttu-id="bcac7-120">`For Each`...`Next`建構在集合中執行一組陳述式，針對每個項目執行一次。</span><span class="sxs-lookup"><span data-stu-id="bcac7-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="bcac7-121">指定迴圈控制變數，但您沒有啟動或結束值，判斷。</span><span class="sxs-lookup"><span data-stu-id="bcac7-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="bcac7-122">如需詳細資訊，請參閱[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bcac7-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcac7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcac7-123">See also</span></span>

- [<span data-ttu-id="bcac7-124">控制流程</span><span class="sxs-lookup"><span data-stu-id="bcac7-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="bcac7-125">決策結構</span><span class="sxs-lookup"><span data-stu-id="bcac7-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="bcac7-126">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="bcac7-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="bcac7-127">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="bcac7-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
