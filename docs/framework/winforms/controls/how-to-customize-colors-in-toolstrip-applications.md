---
title: HOW TO：自訂 ToolStrip 應用程式的色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
ms.openlocfilehash: 971fc8478e6ff2b5745a950daa2f04bfc8d00322
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666399"
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="f8175-102">HOW TO：自訂 ToolStrip 應用程式的色彩</span><span class="sxs-lookup"><span data-stu-id="f8175-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="f8175-103">您可以自訂 <xref:System.Windows.Forms.ToolStrip> 的外觀，藉由使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類別來使用自訂的色彩。</span><span class="sxs-lookup"><span data-stu-id="f8175-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8175-104">範例</span><span class="sxs-lookup"><span data-stu-id="f8175-104">Example</span></span>  
 <span data-ttu-id="f8175-105">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 在執行階段定義自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="f8175-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8175-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f8175-106">Compiling the Code</span></span>  
 <span data-ttu-id="f8175-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f8175-107">This example requires:</span></span>  
  
- <span data-ttu-id="f8175-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f8175-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f8175-109">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="f8175-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f8175-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f8175-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8175-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8175-111">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.ProfessionalColorTable>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
