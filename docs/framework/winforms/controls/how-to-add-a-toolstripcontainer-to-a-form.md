---
title: 如何：將 ToolStripContainer 新增至表單
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
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d0da8f1363a4dd1bfaa3dec9dd2a1db6e22191b3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="1a549-102">如何：將 ToolStripContainer 新增至表單</span><span class="sxs-lookup"><span data-stu-id="1a549-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="1a549-103">您可以程式設計方式加入 <xref:System.Windows.Forms.ToolStripContainer> 至 Windows Form 並填入控制項。</span><span class="sxs-lookup"><span data-stu-id="1a549-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a549-104">範例</span><span class="sxs-lookup"><span data-stu-id="1a549-104">Example</span></span>  
 <span data-ttu-id="1a549-105">下列程式碼範例示範如何加入 <xref:System.Windows.Forms.ToolStripContainer> 和 <xref:System.Windows.Forms.ToolStrip> 至 Windows Form，如何將項目加入 <xref:System.Windows.Forms.ToolStrip>，以及如何加入 <xref:System.Windows.Forms.ToolStrip> 到 <xref:System.Windows.Forms.ToolStripContainer> 的 <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>。</span><span class="sxs-lookup"><span data-stu-id="1a549-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a549-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1a549-106">Compiling the Code</span></span>  
 <span data-ttu-id="1a549-107">這個程式碼範例需要：</span><span class="sxs-lookup"><span data-stu-id="1a549-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="1a549-108">System.Drawing、System.Text 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1a549-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1a549-109">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1a549-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1a549-110">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="1a549-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="1a549-111">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))或 [ToolStripContainer 工作對話方塊](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="1a549-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a549-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a549-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="1a549-113">ToolStripContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="1a549-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [<span data-ttu-id="1a549-114">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="1a549-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
