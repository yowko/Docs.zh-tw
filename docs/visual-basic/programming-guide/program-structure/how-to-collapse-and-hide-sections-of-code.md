---
title: 作法：折迭和隱藏程式碼區段（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: 4f11982cc0aa7654c1e456fb15d918a68bc4791b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054112"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="c26f2-102">作法：折迭和隱藏程式碼區段（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c26f2-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="c26f2-103">`#Region`指示詞可讓您折迭和隱藏 Visual Basic 檔案中的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="c26f2-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="c26f2-104">`#Region`指示詞可讓您指定程式碼區塊，當您使用 Visual Studio 程式碼編輯器時，可以展開或折迭。</span><span class="sxs-lookup"><span data-stu-id="c26f2-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="c26f2-105">可以選擇性地隱藏程式碼，讓您的檔案更容易管理且更易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="c26f2-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="c26f2-106">如需詳細資訊，請參閱[大綱](/visualstudio/ide/outlining)。</span><span class="sxs-lookup"><span data-stu-id="c26f2-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="c26f2-107">`#Region`指示詞支援程式碼區塊的`#If...#End If`語義，例如。</span><span class="sxs-lookup"><span data-stu-id="c26f2-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="c26f2-108">這表示它們不能在一個區塊中開始，也不能在另一個區塊中結束;開始和結束必須在相同的區塊中。</span><span class="sxs-lookup"><span data-stu-id="c26f2-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="c26f2-109">`#Region`函數中不支援指示詞。</span><span class="sxs-lookup"><span data-stu-id="c26f2-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="c26f2-110">折迭和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="c26f2-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="c26f2-111">將程式碼區段放在`#Region`和`#End Region`語句之間，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c26f2-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="c26f2-112">`#Region`區塊可以在程式碼檔案中多次使用，因此，使用者可以定義自己的程式和類別區塊，然後再折迭。</span><span class="sxs-lookup"><span data-stu-id="c26f2-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="c26f2-113">`#Region`區塊也可以嵌套在其他`#Region`區塊內。</span><span class="sxs-lookup"><span data-stu-id="c26f2-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="c26f2-114">隱藏程式碼不會使其無法編譯，也不會`#If...#End If`影響語句。</span><span class="sxs-lookup"><span data-stu-id="c26f2-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="c26f2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c26f2-115">See also</span></span>

- [<span data-ttu-id="c26f2-116">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="c26f2-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="c26f2-117">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="c26f2-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="c26f2-118">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="c26f2-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="c26f2-119">大綱</span><span class="sxs-lookup"><span data-stu-id="c26f2-119">Outlining</span></span>](/visualstudio/ide/outlining)
