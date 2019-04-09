---
title: HOW TO：定義停駐之 ToolStrip 控制項的疊置順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: 3347722383b7388c00335683537e00851e642bb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129164"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="3cd10-102">HOW TO：定義停駐之 ToolStrip 控制項的疊置順序</span><span class="sxs-lookup"><span data-stu-id="3cd10-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="3cd10-103">若要使用停駐將 <xref:System.Windows.Forms.ToolStrip> 控制項正確地定位，您必須依照表單的疊置順序，將控制項正確地定位。</span><span class="sxs-lookup"><span data-stu-id="3cd10-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cd10-104">範例</span><span class="sxs-lookup"><span data-stu-id="3cd10-104">Example</span></span>  
 <span data-ttu-id="3cd10-105">下列程式碼範例示範如何指定疊置順序，以排列 <xref:System.Windows.Forms.ToolStrip> 控制項和停駐的 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="3cd10-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="3cd10-106">疊置順序取決於順序<xref:System.Windows.Forms.ToolStrip>和</span><span class="sxs-lookup"><span data-stu-id="3cd10-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and</span></span> <xref:System.Windows.Forms.MenuStrip>  
  
 <span data-ttu-id="3cd10-107">控制項會加入至表單的<xref:System.Windows.Forms.Control.Controls%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="3cd10-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="3cd10-108">將對 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> 方法的這些呼叫順序反轉，並檢視配置上的效果。</span><span class="sxs-lookup"><span data-stu-id="3cd10-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cd10-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3cd10-109">Compiling the Code</span></span>  
 <span data-ttu-id="3cd10-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3cd10-110">This example requires:</span></span>  
  
-   <span data-ttu-id="3cd10-111">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3cd10-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3cd10-112">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="3cd10-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3cd10-113">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3cd10-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd10-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cd10-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [<span data-ttu-id="3cd10-115">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="3cd10-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
