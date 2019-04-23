---
title: HOW TO：建立具有 ToolStripPanel 控制項的 MDI 表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms [Windows Forms]
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
ms.assetid: d198ef8e-f7c4-4b3f-a7f5-ce858cb90cec
ms.openlocfilehash: 55c2294496800fb8692d3c8215c1c13f7dac9b01
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096962"
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="4ccdf-102">HOW TO：建立具有 ToolStripPanel 控制項的 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="4ccdf-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="4ccdf-103">您可以建立在四邊都讓 <xref:System.Windows.Forms.ToolStrip> 控制項框架處理的多重文件介面 (MDI) 表單。</span><span class="sxs-lookup"><span data-stu-id="4ccdf-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ccdf-104">範例</span><span class="sxs-lookup"><span data-stu-id="4ccdf-104">Example</span></span>  
 <span data-ttu-id="4ccdf-105">下列程式碼範例示範如何使用停駐的 <xref:System.Windows.Forms.ToolStripPanel> 控制項搭配四個 <xref:System.Windows.Forms.ToolStrip> 控制項框住 MDI 視窗。</span><span class="sxs-lookup"><span data-stu-id="4ccdf-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="4ccdf-106">在範例中，<xref:System.Windows.Forms.ToolStripPanel.Join%2A> 方法會附加至 <xref:System.Windows.Forms.ToolStrip> 控制項以對應 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="4ccdf-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ccdf-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4ccdf-107">Compiling the Code</span></span>  
 <span data-ttu-id="4ccdf-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4ccdf-108">This example requires:</span></span>  
  
-   <span data-ttu-id="4ccdf-109">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="4ccdf-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4ccdf-110">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="4ccdf-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4ccdf-111">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4ccdf-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ccdf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ccdf-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- <xref:System.Windows.Forms.ToolStripPanel.Join%2A>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="4ccdf-113">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="4ccdf-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
