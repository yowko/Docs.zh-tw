---
title: 如何：自訂 ToolStrip 應用程式中的色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
ms.openlocfilehash: 9a3f712a4d729452ac0d2d4755a5fba59ca102ed
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858729"
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="f3f76-102">如何：自訂 ToolStrip 應用程式中的色彩</span><span class="sxs-lookup"><span data-stu-id="f3f76-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="f3f76-103">您可以自訂 <xref:System.Windows.Forms.ToolStrip> 的外觀，藉由使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類別來使用自訂的色彩。</span><span class="sxs-lookup"><span data-stu-id="f3f76-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f76-104">範例</span><span class="sxs-lookup"><span data-stu-id="f3f76-104">Example</span></span>  
 <span data-ttu-id="f3f76-105">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 在執行階段定義自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="f3f76-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3f76-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f3f76-106">Compiling the Code</span></span>  
 <span data-ttu-id="f3f76-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f3f76-107">This example requires:</span></span>  
  
-   <span data-ttu-id="f3f76-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f3f76-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f3f76-109">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="f3f76-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f3f76-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f3f76-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f3f76-111">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="f3f76-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f76-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3f76-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
