---
title: HOW TO：摺疊和隱藏部分程式碼 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bbce0e4a2427843ed9d9d51b25684db8c54ba69a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980122"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="20900-102">HOW TO：摺疊和隱藏部分程式碼 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20900-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="20900-103">`#Region`指示詞可讓您摺疊並隱藏 Visual Basic 檔案中的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="20900-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="20900-104">`#Region`指示詞可讓您使用 Visual Studio 程式碼編輯器時，指定程式碼，您可以展開或摺疊的區塊。</span><span class="sxs-lookup"><span data-stu-id="20900-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="20900-105">更容易管理而且更方便閱讀，選擇性地隱藏程式碼的功能可讓您的檔案。</span><span class="sxs-lookup"><span data-stu-id="20900-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="20900-106">如需詳細資訊，請參閱[大綱](/visualstudio/ide/outlining)。</span><span class="sxs-lookup"><span data-stu-id="20900-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="20900-107">`#Region` 指示詞支援程式碼區塊的語意，例如`#If...#End If`。</span><span class="sxs-lookup"><span data-stu-id="20900-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="20900-108">這表示它們無法開始一個區塊中，並在另一個; 結束開始和結束必須位於相同的區塊。</span><span class="sxs-lookup"><span data-stu-id="20900-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="20900-109">`#Region` 指示詞不支援在函式內。</span><span class="sxs-lookup"><span data-stu-id="20900-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="20900-110">若要摺疊和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="20900-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="20900-111">放置之間的程式碼區段`#Region`和`#End Region`陳述式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="20900-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     <span data-ttu-id="20900-112">`#Region`區塊可以重複使用程式碼檔案中; 因此，使用者可以定義自己的程序和類別，接著可摺疊區塊。</span><span class="sxs-lookup"><span data-stu-id="20900-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="20900-113">`#Region` 區塊也能在其他巢狀`#Region`區塊。</span><span class="sxs-lookup"><span data-stu-id="20900-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20900-114">隱藏程式碼不會防止它正在進行編譯，並不會影響`#If...#End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="20900-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20900-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20900-115">See also</span></span>
- [<span data-ttu-id="20900-116">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="20900-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="20900-117">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="20900-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="20900-118">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="20900-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="20900-119">大綱</span><span class="sxs-lookup"><span data-stu-id="20900-119">Outlining</span></span>](/visualstudio/ide/outlining)
