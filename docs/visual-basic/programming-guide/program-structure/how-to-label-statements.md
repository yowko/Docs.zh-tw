---
title: HOW TO：標籤陳述式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 69ec8c7625410f140c59ba8dd492dca76857eb96
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828637"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="82d89-102">HOW TO：標籤陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82d89-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="82d89-103">陳述式區塊所組成的以分號分隔的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="82d89-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="82d89-104">據說是幾行程式碼，加上識別的字串或整數*標示為*。</span><span class="sxs-lookup"><span data-stu-id="82d89-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="82d89-105">陳述式標籤用來標記行程式碼來加以識別，以便使用陳述式這類`On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="82d89-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="82d89-106">標籤可能是其中一個有效的 Visual Basic 識別項，例如識別程式設計項目，或整數常值。</span><span class="sxs-lookup"><span data-stu-id="82d89-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="82d89-107">標籤必須出現在原始程式碼行開頭，而且必須後面接著冒號，不論是否它後面的陳述式同一行上。</span><span class="sxs-lookup"><span data-stu-id="82d89-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="82d89-108">編譯器會藉由檢查一行的開頭是否符合任何已定義的識別項識別標籤。</span><span class="sxs-lookup"><span data-stu-id="82d89-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="82d89-109">如果不存在，編譯器會假設它是一個標籤。</span><span class="sxs-lookup"><span data-stu-id="82d89-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="82d89-110">標籤會有自己的宣告空間，而且不會干擾其他識別項。</span><span class="sxs-lookup"><span data-stu-id="82d89-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="82d89-111">標籤的範圍是方法的主體。</span><span class="sxs-lookup"><span data-stu-id="82d89-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="82d89-112">標籤宣告的任何模稜兩可的情況下，會優先。</span><span class="sxs-lookup"><span data-stu-id="82d89-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82d89-113">只能在方法內的可執行陳述式上可用的標籤。</span><span class="sxs-lookup"><span data-stu-id="82d89-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="82d89-114">若要標記一行程式碼</span><span class="sxs-lookup"><span data-stu-id="82d89-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="82d89-115">將後面接著冒號，在原始程式碼行開頭的識別碼。</span><span class="sxs-lookup"><span data-stu-id="82d89-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="82d89-116">例如，下列程式碼會加上`Jump`和`120`分別：</span><span class="sxs-lookup"><span data-stu-id="82d89-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="82d89-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82d89-117">See also</span></span>

- [<span data-ttu-id="82d89-118">陳述式</span><span class="sxs-lookup"><span data-stu-id="82d89-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="82d89-119">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="82d89-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="82d89-120">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="82d89-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
