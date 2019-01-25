---
title: HOW TO：設定 ContextMenuStrip 核取邊界和影像邊界
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], configuring check and image margins
- ContextMenuStrips [Windows Forms], configuring check and image margins
- margins [Windows Forms], setting check and image in Windows Forms ContextMenuStrips
ms.assetid: 3391c4c2-0c9e-4aa4-9492-13ff7644bdf2
ms.openlocfilehash: 100038cedaf74f9566f24b7b030531dda8f466af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609365"
---
# <a name="how-to-configure-contextmenustrip-check-margins-and-image-margins"></a><span data-ttu-id="17a56-102">HOW TO：設定 ContextMenuStrip 核取邊界和影像邊界</span><span class="sxs-lookup"><span data-stu-id="17a56-102">How to: Configure ContextMenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="17a56-103">您可以用各種組合設定 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> 和 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> 屬性來自訂 <xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="17a56-103">You can customize a <xref:System.Windows.Forms.ContextMenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17a56-104">範例</span><span class="sxs-lookup"><span data-stu-id="17a56-104">Example</span></span>  
 <span data-ttu-id="17a56-105">下列程式碼範例示範如何設定及自訂 <xref:System.Windows.Forms.ContextMenuStrip> 核取和影像邊界。</span><span class="sxs-lookup"><span data-stu-id="17a56-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check and image margins.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17a56-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="17a56-106">Compiling the Code</span></span>  
 <span data-ttu-id="17a56-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="17a56-107">This example requires:</span></span>  
  
-   <span data-ttu-id="17a56-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="17a56-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="17a56-109">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="17a56-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="17a56-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="17a56-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="17a56-111">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="17a56-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a56-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17a56-112">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="17a56-113">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="17a56-113">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
- [<span data-ttu-id="17a56-114">如何：啟用核取邊界和 ContextMenuStrip 控制項中的影像邊界</span><span class="sxs-lookup"><span data-stu-id="17a56-114">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
