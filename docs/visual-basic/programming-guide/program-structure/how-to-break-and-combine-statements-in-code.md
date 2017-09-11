---
title: "如何︰ 中斷和合併陳述式在程式碼 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
dev_langs:
- VB
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores, in code
- statements [Visual Basic], line continuation in
- line breaks, in code
- line-continuation character
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2ca281035a0bd81a9b52cdd60f2bc59724852709
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="e7bd3-102">如何：在程式碼中中斷和合併陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7bd3-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="e7bd3-103">在撰寫程式碼時，您有時可能會建立冗長的陳述式的水平捲軸在程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="e7bd3-104">雖然這並不會影響的方式執行程式碼，它不容易為您或其他人的監視器上顯示的方式，閱讀程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="e7bd3-105">在這種情況下，您應該考慮分為數行的一個長陳述式。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="e7bd3-106">若要在單一陳述式分成多行程式碼</span><span class="sxs-lookup"><span data-stu-id="e7bd3-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="e7bd3-107">使用行接續字元，也就是底線 (`_`)，想要中斷的行之處。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="e7bd3-108">底線的前面必須緊接一個空格，後面則必須緊接著行結束字元 (歸位字元)。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7bd3-109">在某些情況下，如果您省略行接續字元 Visual Basic 編譯器會隱含地繼續陳述式在下一行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="e7bd3-110">可以略過的行接續字元的語法項目清單，請參閱 「 隱含行接續符號 」，在[陳述式](../../../visual-basic/programming-guide/language-features/statements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="e7bd3-111">在下列範例中，陳述式會分成四行程式碼，以終止所有的行接續字元，但最後一行。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     <span data-ttu-id="e7bd3-112">[!code-vb[VbVbcnConventions #&20;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd3-112">[!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]</span></span>  
  
     <span data-ttu-id="e7bd3-113">使用此順序可讓您的程式碼更方便閱讀，列印線上和時。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-113">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="e7bd3-114">行接續字元必須是在一行的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-114">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="e7bd3-115">您不能與任何其他項目跟隨它在同一行。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-115">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="e7bd3-116">有關您可以在其中使用行接續字元中，有部分限制例如，您無法使用它的引數名稱中間。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-116">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="e7bd3-117">您可以中斷引數清單使用行接續符號的字元，但個別引數的名稱必須保持不變。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-117">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="e7bd3-118">您無法繼續註解使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-118">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="e7bd3-119">編譯器不會檢查有特殊意義的註解中的字元。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-119">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="e7bd3-120">多行註解，重複執行註解符號 (`'`) 在每一行。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-120">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="e7bd3-121">雖然個別行上放置每個陳述式是建議的方法，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]也可讓您將多個陳述式放在同一行。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-121">Although placing each statement on a separate line is the recommended method, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="e7bd3-122">若要在同一行上放置多個陳述式</span><span class="sxs-lookup"><span data-stu-id="e7bd3-122">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="e7bd3-123">將陳述式以冒號分隔 (`:`)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e7bd3-123">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     <span data-ttu-id="e7bd3-124">[!code-vb[VbVbcnConventions #&10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd3-124">[!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bd3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7bd3-125">See Also</span></span>  
 <span data-ttu-id="e7bd3-126">[程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="e7bd3-126">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="e7bd3-127"> [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="e7bd3-127"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>
