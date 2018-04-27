---
title: 如何：自訂 ToolStrip 應用程式中的色彩
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
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b8806878c2bac338b4bce9cbee311edd7bf7978
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="6b30a-102">如何：自訂 ToolStrip 應用程式中的色彩</span><span class="sxs-lookup"><span data-stu-id="6b30a-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="6b30a-103">您可以自訂 <xref:System.Windows.Forms.ToolStrip> 的外觀，藉由使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類別來使用自訂的色彩。</span><span class="sxs-lookup"><span data-stu-id="6b30a-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b30a-104">範例</span><span class="sxs-lookup"><span data-stu-id="6b30a-104">Example</span></span>  
 <span data-ttu-id="6b30a-105">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 在執行階段定義自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="6b30a-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b30a-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6b30a-106">Compiling the Code</span></span>  
 <span data-ttu-id="6b30a-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6b30a-107">This example requires:</span></span>  
  
-   <span data-ttu-id="6b30a-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6b30a-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6b30a-109">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="6b30a-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6b30a-110">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="6b30a-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6b30a-111">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="6b30a-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b30a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b30a-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
