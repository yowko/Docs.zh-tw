---
title: 如何：針對 MDI 使用 ToolStripPanels
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], using ToolStripPanels [Windows Forms]
- ToolStripPanel control [Windows Forms], using for MDI
- toolbars [Windows Forms], using for MDI
ms.assetid: d6b884fc-0846-465f-83c3-5dc0fe93b00f
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b58518b2b6fc70d9e9963f90836007511ce83b2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-toolstrippanels-for-mdi"></a><span data-ttu-id="5c020-102">如何：針對 MDI 使用 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="5c020-102">How to: Use ToolStripPanels for MDI</span></span>
<span data-ttu-id="5c020-103">藉由使用 <xref:System.Windows.Forms.ToolStripPanel.Join%2A> 方法，<xref:System.Windows.Forms.ToolStripPanel> 提供多重文件介面 (MDI) 應用程式彈性。</span><span class="sxs-lookup"><span data-stu-id="5c020-103">The <xref:System.Windows.Forms.ToolStripPanel> provides flexibility for multiple-document interface (MDI) applications by using the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c020-104">範例</span><span class="sxs-lookup"><span data-stu-id="5c020-104">Example</span></span>  
 <span data-ttu-id="5c020-105">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripPanel> MDI 控制項。</span><span class="sxs-lookup"><span data-stu-id="5c020-105">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls for MDI.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c020-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5c020-106">Compiling the Code</span></span>  
 <span data-ttu-id="5c020-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5c020-107">This example requires:</span></span>  
  
-   <span data-ttu-id="5c020-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5c020-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5c020-109">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="5c020-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5c020-110">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="5c020-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5c020-111">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="5c020-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c020-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c020-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [<span data-ttu-id="5c020-113">操作說明：聯結 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="5c020-113">How to: Join ToolStripPanels</span></span>](../../../../docs/framework/winforms/controls/how-to-join-toolstrippanels.md)
