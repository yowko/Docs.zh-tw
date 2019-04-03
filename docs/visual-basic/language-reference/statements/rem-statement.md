---
title: REM 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 3c63c5613b40cb2014c77a0a996e3acb2cc304d4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817015"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="72a79-102">REM 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72a79-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="72a79-103">用來在程式碼的原始程式碼中包含說明備註。</span><span class="sxs-lookup"><span data-stu-id="72a79-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a79-104">語法</span><span class="sxs-lookup"><span data-stu-id="72a79-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="72a79-105">組件</span><span class="sxs-lookup"><span data-stu-id="72a79-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="72a79-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="72a79-106">Optional.</span></span> <span data-ttu-id="72a79-107">您想要包含的任何註解文字。</span><span class="sxs-lookup"><span data-stu-id="72a79-107">The text of any comment you want to include.</span></span> <span data-ttu-id="72a79-108">之間的空間，須`REM`關鍵字和`comment`。</span><span class="sxs-lookup"><span data-stu-id="72a79-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72a79-109">備註</span><span class="sxs-lookup"><span data-stu-id="72a79-109">Remarks</span></span>  
 <span data-ttu-id="72a79-110">您可以放入`REM`陳述式單獨一行，或您可以將它放在另一個陳述式之後。</span><span class="sxs-lookup"><span data-stu-id="72a79-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="72a79-111">`REM`陳述式必須是該行的最後一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="72a79-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="72a79-112">它會依照另一個陳述式，如果`REM`必須從該陳述式，以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="72a79-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="72a79-113">您可以使用單引號 (`'`) 而不是`REM`。</span><span class="sxs-lookup"><span data-stu-id="72a79-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="72a79-114">您的註解另一個陳述式之後的同一行上還是位於單獨一行，也是如此。</span><span class="sxs-lookup"><span data-stu-id="72a79-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72a79-115">您無法繼續`REM`陳述式使用行接續序列 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="72a79-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="72a79-116">註解開始時，編譯器不會檢查特殊意義的字元。</span><span class="sxs-lookup"><span data-stu-id="72a79-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="72a79-117">對於多行註解，請使用另一個`REM`陳述式或註解符號 (`'`) 在每一行。</span><span class="sxs-lookup"><span data-stu-id="72a79-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72a79-118">範例</span><span class="sxs-lookup"><span data-stu-id="72a79-118">Example</span></span>  
 <span data-ttu-id="72a79-119">下列範例說明`REM`陳述式，這用來在程式中包含說明備註。</span><span class="sxs-lookup"><span data-stu-id="72a79-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="72a79-120">它也會顯示另一種使用單一的引號字元 (`'`) 而不是`REM`。</span><span class="sxs-lookup"><span data-stu-id="72a79-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="72a79-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72a79-121">See also</span></span>

- [<span data-ttu-id="72a79-122">程式碼中的註解</span><span class="sxs-lookup"><span data-stu-id="72a79-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="72a79-123">如何：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="72a79-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
