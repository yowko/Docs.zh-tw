---
title: HOW TO：中斷和合併陳述式中的程式碼 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb._
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
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 680084c39b90d4f664f48559fa21388ce192d999
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955619"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="cd44d-102">HOW TO：中斷和合併陳述式中的程式碼 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd44d-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="cd44d-103">當撰寫程式碼，您有時可能會建立冗長的陳述式也許水平捲軸在程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="cd44d-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="cd44d-104">雖然這不會影響的方式執行程式碼，它很難對您或其他人讀取的程式碼，此監視器上顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="cd44d-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="cd44d-105">在此情況下，您應該考慮單一長的陳述式分成數行。</span><span class="sxs-lookup"><span data-stu-id="cd44d-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="cd44d-106">若要在單一陳述式分成多行</span><span class="sxs-lookup"><span data-stu-id="cd44d-106">To break a single statement into multiple lines</span></span>  
  
- <span data-ttu-id="cd44d-107">使用行接續字元是底線 (`_`)，您想要中斷的列之處。</span><span class="sxs-lookup"><span data-stu-id="cd44d-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="cd44d-108">底線的前面必須緊接一個空格，後面則必須緊接著行結束字元 (歸位字元)。</span><span class="sxs-lookup"><span data-stu-id="cd44d-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd44d-109">在某些情況下，如果您省略行接續字元中，Visual Basic 編譯器會隱含地繼續陳述式在下一行程式碼。</span><span class="sxs-lookup"><span data-stu-id="cd44d-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="cd44d-110">可以略過行接續字元的語法項目清單，請參閱 「 隱含行接續符號 」，在[陳述式](../../../visual-basic/programming-guide/language-features/statements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd44d-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="cd44d-111">在下列範例中，陳述式會分成四行程式碼，以終止所有的行接續字元，但最後一行。</span><span class="sxs-lookup"><span data-stu-id="cd44d-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     <span data-ttu-id="cd44d-112">使用此順序可讓您的程式碼更方便閱讀，列印線上和時。</span><span class="sxs-lookup"><span data-stu-id="cd44d-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="cd44d-113">行接續字元必須是該行的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="cd44d-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="cd44d-114">您不可以跟隨它與其他任何位於同一行上。</span><span class="sxs-lookup"><span data-stu-id="cd44d-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="cd44d-115">對於您可以在其中使用行接續字元中，有部分限制例如，您無法使用它的引數名稱的中間。</span><span class="sxs-lookup"><span data-stu-id="cd44d-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="cd44d-116">您可能會中斷以行接續字元的引數清單，但個別的名稱，引數必須保持不變。</span><span class="sxs-lookup"><span data-stu-id="cd44d-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="cd44d-117">您無法繼續註解使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="cd44d-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="cd44d-118">編譯器不會檢查特殊意義的註解中的字元。</span><span class="sxs-lookup"><span data-stu-id="cd44d-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="cd44d-119">多行註解中，重複的註解符號 (`'`) 在每一行。</span><span class="sxs-lookup"><span data-stu-id="cd44d-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="cd44d-120">雖然每個陳述式置於不同行的建議的方法，Visual Basic 也可讓您將多個陳述式放在同一行。</span><span class="sxs-lookup"><span data-stu-id="cd44d-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="cd44d-121">若要將多個陳述式放在同一行</span><span class="sxs-lookup"><span data-stu-id="cd44d-121">To place multiple statements on the same line</span></span>  
  
- <span data-ttu-id="cd44d-122">將陳述式以冒號分隔 (`:`)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cd44d-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="cd44d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd44d-123">See also</span></span>

- [<span data-ttu-id="cd44d-124">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="cd44d-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="cd44d-125">陳述式</span><span class="sxs-lookup"><span data-stu-id="cd44d-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
