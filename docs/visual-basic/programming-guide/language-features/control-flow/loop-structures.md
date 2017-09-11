---
title: "迴圈結構 (Visual Basic) |Microsoft 文件"
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
- control flow, loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures
- statements [Visual Basic], loop
- Do statement, Do loops
- conditional statements, loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
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
ms.openlocfilehash: eba728d782bb5a6259467fb48f738f35580049c0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="ad689-102">迴圈結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad689-102">Loop Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ad689-103">迴圈結構可讓您重複執行一或多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad689-103"> loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="ad689-104">您可以重複迴圈結構中的陳述式，直到條件為`True`，直到條件為`False`、 在集合中指定的次數，或是過一次針對每個項目。</span><span class="sxs-lookup"><span data-stu-id="ad689-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="ad689-105">下圖顯示會執行一組陳述式，直到條件變成 true 迴圈結構。</span><span class="sxs-lookup"><span data-stu-id="ad689-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="ad689-106">![重複執行相同動作的流程圖...迴圈](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="ad689-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="ad689-107">執行一組陳述式，直到條件變成 true</span><span class="sxs-lookup"><span data-stu-id="ad689-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="ad689-108">While 迴圈</span><span class="sxs-lookup"><span data-stu-id="ad689-108">While Loops</span></span>  
 <span data-ttu-id="ad689-109">The `While`...`End While`建構會執行一組陳述式中指定的條件為`While`陳述式是`True`。</span><span class="sxs-lookup"><span data-stu-id="ad689-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="ad689-110">如需詳細資訊，請參閱[時...While 陳述式結束](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ad689-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="ad689-111">Do 迴圈</span><span class="sxs-lookup"><span data-stu-id="ad689-111">Do Loops</span></span>  
 <span data-ttu-id="ad689-112">The `Do`...`Loop`建構可讓您測試開頭或結尾的迴圈結構的條件。</span><span class="sxs-lookup"><span data-stu-id="ad689-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="ad689-113">您也可以指定是否要重複迴圈條件維持`True`或直到它變成`True`。</span><span class="sxs-lookup"><span data-stu-id="ad689-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="ad689-114">如需詳細資訊，請參閱[執行...迴圈陳述式](../../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ad689-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="ad689-115">For 迴圈</span><span class="sxs-lookup"><span data-stu-id="ad689-115">For Loops</span></span>  
 <span data-ttu-id="ad689-116">The `For`...`Next`建構執行特定次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="ad689-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="ad689-117">它會使用迴圈控制變數，也稱為*計數器*，若要保留的次數。</span><span class="sxs-lookup"><span data-stu-id="ad689-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="ad689-118">您指定的開始和結束此計數器的值，您可以選擇性地指定，而增加時重複一次從到下一個量。</span><span class="sxs-lookup"><span data-stu-id="ad689-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="ad689-119">如需詳細資訊，請參閱[For...下一個陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ad689-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="ad689-120">For Each 迴圈</span><span class="sxs-lookup"><span data-stu-id="ad689-120">For Each Loops</span></span>  
 <span data-ttu-id="ad689-121">The `For Each`...`Next`建構集合中執行一組陳述式，針對每個項目執行一次。</span><span class="sxs-lookup"><span data-stu-id="ad689-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="ad689-122">您指定的迴圈控制變數，但您不需要決定開始或結束值。</span><span class="sxs-lookup"><span data-stu-id="ad689-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="ad689-123">如需詳細資訊，請參閱[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ad689-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad689-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad689-124">See Also</span></span>  
 <span data-ttu-id="ad689-125">[控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad689-125">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="ad689-126"> [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="ad689-126"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="ad689-127"> [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="ad689-127"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="ad689-128"> [巢狀控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span><span class="sxs-lookup"><span data-stu-id="ad689-128"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span></span>
