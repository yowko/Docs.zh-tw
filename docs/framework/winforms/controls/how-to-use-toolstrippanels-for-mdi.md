---
title: "如何：針對 MDI 使用 ToolStripPanels"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], using ToolStripPanels [Windows Forms]
- ToolStripPanel control [Windows Forms], using for MDI
- toolbars [Windows Forms], using for MDI
ms.assetid: d6b884fc-0846-465f-83c3-5dc0fe93b00f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8e52f2b4dd44ad05ba1dba178c05d851f802635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-toolstrippanels-for-mdi"></a><span data-ttu-id="02d65-102">如何：針對 MDI 使用 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="02d65-102">How to: Use ToolStripPanels for MDI</span></span>
<span data-ttu-id="02d65-103">藉由使用 <xref:System.Windows.Forms.ToolStripPanel.Join%2A> 方法，<xref:System.Windows.Forms.ToolStripPanel> 提供多重文件介面 (MDI) 應用程式彈性。</span><span class="sxs-lookup"><span data-stu-id="02d65-103">The <xref:System.Windows.Forms.ToolStripPanel> provides flexibility for multiple-document interface (MDI) applications by using the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02d65-104">範例</span><span class="sxs-lookup"><span data-stu-id="02d65-104">Example</span></span>  
 <span data-ttu-id="02d65-105">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripPanel> MDI 控制項。</span><span class="sxs-lookup"><span data-stu-id="02d65-105">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls for MDI.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02d65-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="02d65-106">Compiling the Code</span></span>  
 <span data-ttu-id="02d65-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="02d65-107">This example requires:</span></span>  
  
-   <span data-ttu-id="02d65-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="02d65-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="02d65-109">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="02d65-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="02d65-110">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="02d65-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="02d65-111">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="02d65-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d65-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="02d65-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [<span data-ttu-id="02d65-113">操作說明：聯結 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="02d65-113">How to: Join ToolStripPanels</span></span>](../../../../docs/framework/winforms/controls/how-to-join-toolstrippanels.md)
