---
title: 如何：聯結 ToolStripPanels
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: 5e1688fb00e6eefa4873284e1ea1ba29536d3227
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878544"
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="86d80-102">如何：聯結 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="86d80-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="86d80-103">您可以在執行階段將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>，以提供多重文件介面 (MDI) 應用程式的彈性。</span><span class="sxs-lookup"><span data-stu-id="86d80-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86d80-104">範例</span><span class="sxs-lookup"><span data-stu-id="86d80-104">Example</span></span>  
 <span data-ttu-id="86d80-105">下列程式碼範例示範如何將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="86d80-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86d80-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="86d80-106">Compiling the Code</span></span>  
 <span data-ttu-id="86d80-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="86d80-107">This example requires:</span></span>  
  
-   <span data-ttu-id="86d80-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="86d80-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="86d80-109">建置此範例從命令列 visual Basic 或 Visual C# 的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="86d80-109">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="86d80-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="86d80-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="86d80-111">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="86d80-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d80-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86d80-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [<span data-ttu-id="86d80-113">操作說明：針對 MDI 使用 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="86d80-113">How to: Use ToolStripPanels for MDI</span></span>](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)
