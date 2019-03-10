---
title: HOW TO：Join ToolStripPanels
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: 297e3bfec9bb24fb2c06e903a5f32410618812d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703669"
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="d2f85-102">HOW TO：Join ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="d2f85-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="d2f85-103">您可以在執行階段將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>，以提供多重文件介面 (MDI) 應用程式的彈性。</span><span class="sxs-lookup"><span data-stu-id="d2f85-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2f85-104">範例</span><span class="sxs-lookup"><span data-stu-id="d2f85-104">Example</span></span>  
 <span data-ttu-id="d2f85-105">下列程式碼範例示範如何將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="d2f85-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2f85-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d2f85-106">Compiling the Code</span></span>  
 <span data-ttu-id="d2f85-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d2f85-107">This example requires:</span></span>  
  
-   <span data-ttu-id="d2f85-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d2f85-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d2f85-109">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f85-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d2f85-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d2f85-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f85-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f85-111">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- [<span data-ttu-id="d2f85-112">如何：針對 MDI 使用 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="d2f85-112">How to: Use ToolStripPanels for MDI</span></span>](how-to-use-toolstrippanels-for-mdi.md)
