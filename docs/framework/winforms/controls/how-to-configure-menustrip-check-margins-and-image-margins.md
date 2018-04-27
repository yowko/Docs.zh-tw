---
title: 如何：設定 MenuStrip 核取邊界和影像邊界
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
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3ee49ec226c99a28322822983fa086954f0ef3e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="9905a-102">如何：設定 MenuStrip 核取邊界和影像邊界</span><span class="sxs-lookup"><span data-stu-id="9905a-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="9905a-103">您可以用各種組合設定 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> 和 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> 屬性來自訂 <xref:System.Windows.Forms.MenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="9905a-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9905a-104">範例</span><span class="sxs-lookup"><span data-stu-id="9905a-104">Example</span></span>  
 <span data-ttu-id="9905a-105">下列程式碼範例示範如何設定及自訂 <xref:System.Windows.Forms.ContextMenuStrip> 核取邊界和影像邊界。</span><span class="sxs-lookup"><span data-stu-id="9905a-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="9905a-106">用於 <xref:System.Windows.Forms.ContextMenuStrip> 或 <xref:System.Windows.Forms.MenuStrip> 的程序相同。</span><span class="sxs-lookup"><span data-stu-id="9905a-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9905a-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9905a-107">Compiling the Code</span></span>  
 <span data-ttu-id="9905a-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9905a-108">This example requires:</span></span>  
  
-   <span data-ttu-id="9905a-109">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="9905a-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9905a-110">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="9905a-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9905a-111">您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。</span><span class="sxs-lookup"><span data-stu-id="9905a-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="9905a-112">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="9905a-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9905a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9905a-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="9905a-114">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="9905a-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="9905a-115">操作說明：啟用 ContextMenuStrip 控制項中的核取邊界和影像邊界</span><span class="sxs-lookup"><span data-stu-id="9905a-115">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
