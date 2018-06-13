---
title: 如何：標記陳述式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650120"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="ba296-102">如何：標記陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba296-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="ba296-103">陳述式區塊是由以冒號分隔的程式碼行所組成。</span><span class="sxs-lookup"><span data-stu-id="ba296-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="ba296-104">行程式碼前面有識別的字串或整數都稱為*標示為*。</span><span class="sxs-lookup"><span data-stu-id="ba296-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="ba296-105">陳述式標籤用來標記資料行的程式碼，以找出它使用陳述式例如`On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="ba296-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="ba296-106">標籤可能是其中一個有效的 Visual Basic 識別項，例如識別程式設計項目，或整數常值。</span><span class="sxs-lookup"><span data-stu-id="ba296-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="ba296-107">標籤必須出現在原始程式碼行開頭，而且必須後面接著冒號，不論是否接下來還陳述式同一行上。</span><span class="sxs-lookup"><span data-stu-id="ba296-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="ba296-108">編譯器會辨識標籤藉由檢查一行的開頭是否符合任何已定義的識別項。</span><span class="sxs-lookup"><span data-stu-id="ba296-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="ba296-109">如果不存在，編譯器會假設它是標籤。</span><span class="sxs-lookup"><span data-stu-id="ba296-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="ba296-110">標籤會有自己的宣告空間，並不會干擾其他識別項。</span><span class="sxs-lookup"><span data-stu-id="ba296-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="ba296-111">標籤的範圍是方法的主體。</span><span class="sxs-lookup"><span data-stu-id="ba296-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="ba296-112">標記宣告會優先使用在任何模稜兩可的情況下。</span><span class="sxs-lookup"><span data-stu-id="ba296-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba296-113">只有在方法內的可執行陳述式上可用的標籤。</span><span class="sxs-lookup"><span data-stu-id="ba296-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="ba296-114">若要標記的一行程式碼</span><span class="sxs-lookup"><span data-stu-id="ba296-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="ba296-115">將識別項，後面接著冒號，在原始程式碼行的開頭。</span><span class="sxs-lookup"><span data-stu-id="ba296-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="ba296-116">例如，下列程式碼則標示為`Jump`和`120`分別：</span><span class="sxs-lookup"><span data-stu-id="ba296-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ba296-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba296-117">See Also</span></span>  
 [<span data-ttu-id="ba296-118">陳述式</span><span class="sxs-lookup"><span data-stu-id="ba296-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="ba296-119">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="ba296-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="ba296-120">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="ba296-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
