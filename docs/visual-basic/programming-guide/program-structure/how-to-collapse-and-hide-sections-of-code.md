---
title: "如何︰ 摺疊和隱藏程式碼區段 (Visual Basic) |Microsoft 文件"
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
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
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
ms.openlocfilehash: 4dcd5cd5d79629fd008534112cb72d5bcfec476e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="27c94-102">如何：摺疊和隱藏程式碼區段 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27c94-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="27c94-103">`#Region`指示詞可讓您摺疊和隱藏程式碼中的區段[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="27c94-103">The `#Region` directive enables you to collapse and hide sections of code in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files.</span></span> <span data-ttu-id="27c94-104">`#Region`指示詞可讓您使用時，指定一段程式碼，您可以展開或摺疊[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="27c94-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] code editor.</span></span> <span data-ttu-id="27c94-105">選擇性地隱藏程式碼的功能，使您更容易管理且更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="27c94-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="27c94-106">如需詳細資訊，請參閱[大綱](https://docs.microsoft.com/visualstudio/ide/outlining)。</span><span class="sxs-lookup"><span data-stu-id="27c94-106">For more information, see [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="27c94-107">`#Region`指示詞支援程式碼區塊語意 （semantics），例如`#If...#End If`。</span><span class="sxs-lookup"><span data-stu-id="27c94-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="27c94-108">這表示無法在一個區塊開始與結束在另一個。開始和結束必須是同一個區塊中。</span><span class="sxs-lookup"><span data-stu-id="27c94-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="27c94-109">`#Region`指示詞不支援函式內。</span><span class="sxs-lookup"><span data-stu-id="27c94-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="27c94-110">若要摺疊和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="27c94-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="27c94-111">將程式碼之間的區段`#Region`和`#End Region`陳述式，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="27c94-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     <span data-ttu-id="27c94-112">[!code-vb[VbVbalrConditionalComp #&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="27c94-112">[!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span></span>  
  
     <span data-ttu-id="27c94-113">`#Region`區塊可以重複使用程式碼檔案中; 因此，使用者可以定義自己的區塊的程序和，反而可摺疊的類別。</span><span class="sxs-lookup"><span data-stu-id="27c94-113">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="27c94-114">`#Region`區塊可以也巢狀內其他`#Region`區塊。</span><span class="sxs-lookup"><span data-stu-id="27c94-114">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27c94-115">隱藏程式碼不會阻止它正在進行編譯，且不影響`#If...#End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="27c94-115">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c94-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27c94-116">See Also</span></span>  
 <span data-ttu-id="27c94-117">[條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="27c94-117">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<span data-ttu-id="27c94-118"> [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="27c94-118"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="27c94-119"> [#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="27c94-119"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="27c94-120"> [大綱](https://docs.microsoft.com/visualstudio/ide/outlining)</span><span class="sxs-lookup"><span data-stu-id="27c94-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining)</span></span>
