---
title: 作法：在程式碼中中斷和合併語句（Visual Basic）
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
ms.openlocfilehash: a0a77b161d81271a4cb7eecf2982a287debee6a5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991731"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="1da13-102">作法：在程式碼中中斷和合併語句（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1da13-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="1da13-103">撰寫程式碼時，您有時可能會在程式碼編輯器中建立需要水準滾動的冗長語句。</span><span class="sxs-lookup"><span data-stu-id="1da13-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="1da13-104">雖然這並不會影響您的程式碼執行方式，但它會讓您或其他人難以在監視器上看到該程式碼。</span><span class="sxs-lookup"><span data-stu-id="1da13-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="1da13-105">在這種情況下，您應該考慮將單一長語句細分成數行。</span><span class="sxs-lookup"><span data-stu-id="1da13-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="1da13-106">將單一語句分成多行</span><span class="sxs-lookup"><span data-stu-id="1da13-106">To break a single statement into multiple lines</span></span>

<span data-ttu-id="1da13-107">使用行接續字元，也就是底線（`_`），這是您想要行中斷的位置。</span><span class="sxs-lookup"><span data-stu-id="1da13-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="1da13-108">底線的前面必須加上空格，並緊接在行結束字元（回車）或（從16.0 版開始）後面加上一個加上回車的批註。</span><span class="sxs-lookup"><span data-stu-id="1da13-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="1da13-109">在某些情況下，如果您省略行接續字元，Visual Basic 編譯器會隱含地繼續下一行程式碼上的語句。</span><span class="sxs-lookup"><span data-stu-id="1da13-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="1da13-110">如需可省略行接續字元的語法元素清單，請參閱[語句](../../../visual-basic/programming-guide/language-features/statements.md)中的「隱含行接續」。</span><span class="sxs-lookup"><span data-stu-id="1da13-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>

  <span data-ttu-id="1da13-111">在下列範例中，語句會分成四行，其中行接續字元會終止所有但最後一行。</span><span class="sxs-lookup"><span data-stu-id="1da13-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="1da13-112">使用此順序可讓您的程式碼在線上和列印時更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="1da13-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="1da13-113">行接續字元必須是該行的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="1da13-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="1da13-114">您不能在同一行上以其他任何專案來追蹤。</span><span class="sxs-lookup"><span data-stu-id="1da13-114">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="1da13-115">有一些限制可供您使用行接續字元;例如，您無法將它用在引數名稱的中間。</span><span class="sxs-lookup"><span data-stu-id="1da13-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="1da13-116">您可以使用行接續字元來中斷引數清單，但引數的個別名稱必須維持不變。</span><span class="sxs-lookup"><span data-stu-id="1da13-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="1da13-117">您無法使用行接續字元來繼續留言。</span><span class="sxs-lookup"><span data-stu-id="1da13-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="1da13-118">編譯器不會檢查批註中的字元是否有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="1da13-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="1da13-119">對於多行批註，請在每一行重複批註符號`'`（）。</span><span class="sxs-lookup"><span data-stu-id="1da13-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="1da13-120">雖然建議的方法是將每個語句放在不同的行上，但 Visual Basic 也可以讓您將多個語句放在同一行。</span><span class="sxs-lookup"><span data-stu-id="1da13-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="1da13-121">若要將多個語句放在同一行</span><span class="sxs-lookup"><span data-stu-id="1da13-121">To place multiple statements on the same line</span></span>

<span data-ttu-id="1da13-122">以冒號（`:`）分隔語句，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1da13-122">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="1da13-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1da13-123">See also</span></span>

- [<span data-ttu-id="1da13-124">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="1da13-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="1da13-125">陳述式</span><span class="sxs-lookup"><span data-stu-id="1da13-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
