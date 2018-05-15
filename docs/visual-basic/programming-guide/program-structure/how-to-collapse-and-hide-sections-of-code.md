---
title: 如何：摺疊和隱藏程式碼區段 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: f6c272b7ac016258d99873512cb789bba6739727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="efb2e-102">如何：摺疊和隱藏程式碼區段 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efb2e-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="efb2e-103">`#Region`指示詞可讓您可以摺疊並隱藏 Visual Basic 檔案中的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="efb2e-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="efb2e-104">`#Region`指示詞可讓您使用 Visual Studio 程式碼編輯器時，指定一段程式碼，您可以展開或摺疊。</span><span class="sxs-lookup"><span data-stu-id="efb2e-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="efb2e-105">選擇性地隱藏程式碼的功能可讓您的檔案，更容易管理而且更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="efb2e-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="efb2e-106">如需詳細資訊，請參閱[大綱](/visualstudio/ide/outlining)。</span><span class="sxs-lookup"><span data-stu-id="efb2e-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="efb2e-107">`#Region` 指示詞會支援這類程式碼區塊語意`#If...#End If`。</span><span class="sxs-lookup"><span data-stu-id="efb2e-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="efb2e-108">這表示無法在單一區塊中開始與結束在另一個。開始和結束必須在相同的區塊。</span><span class="sxs-lookup"><span data-stu-id="efb2e-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="efb2e-109">`#Region` 指示詞不支援在函式內。</span><span class="sxs-lookup"><span data-stu-id="efb2e-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="efb2e-110">若要摺疊和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="efb2e-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="efb2e-111">將程式碼之間的區段`#Region`和`#End Region`陳述式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="efb2e-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     <span data-ttu-id="efb2e-112">`#Region`區塊可以重複使用程式碼檔案中; 因此，使用者可以定義自己的程序和，接著可摺疊類別的區塊。</span><span class="sxs-lookup"><span data-stu-id="efb2e-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="efb2e-113">`#Region` 區塊也可以巢狀內其他`#Region`區塊。</span><span class="sxs-lookup"><span data-stu-id="efb2e-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="efb2e-114">隱藏程式碼不會阻止它正在進行編譯，且不影響`#If...#End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="efb2e-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb2e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efb2e-115">See Also</span></span>  
 [<span data-ttu-id="efb2e-116">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="efb2e-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="efb2e-117">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="efb2e-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="efb2e-118">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="efb2e-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="efb2e-119">大綱</span><span class="sxs-lookup"><span data-stu-id="efb2e-119">Outlining</span></span>](/visualstudio/ide/outlining)
