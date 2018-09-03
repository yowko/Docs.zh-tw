---
title: 如何：建立專業樣式的 ToolStrip 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 10799ad4db103fb50a25e600418fb8b5003c24ea
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486052"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="e8fb2-102">如何：建立專業樣式的 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="e8fb2-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="e8fb2-103">您可以藉由自行撰寫衍生自 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類型的類別，賦與應用程式的 <xref:System.Windows.Forms.ToolStrip> 控制項專業外觀和行為 (外觀及操作)。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="e8fb2-104">沒有這項功能在 Visual Studio 中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="e8fb2-105">請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8fb2-106">範例</span><span class="sxs-lookup"><span data-stu-id="e8fb2-106">Example</span></span>  
 <span data-ttu-id="e8fb2-107">下列程式碼範例示範如何使用<xref:System.Windows.Forms.ToolStrip>控制項，以建立複合控制項，以模擬**瀏覽窗格**Microsoft® Outlook® 提供的。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8fb2-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e8fb2-108">Compiling the Code</span></span>  
 <span data-ttu-id="e8fb2-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e8fb2-109">This example requires:</span></span>  
  
-   <span data-ttu-id="e8fb2-110">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e8fb2-111">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e8fb2-112">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e8fb2-113">另請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](walkthrough-creating-a-professionally-styled-toolstrip-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e8fb2-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8fb2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8fb2-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="e8fb2-115">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="e8fb2-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="e8fb2-116">操作說明：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="e8fb2-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
