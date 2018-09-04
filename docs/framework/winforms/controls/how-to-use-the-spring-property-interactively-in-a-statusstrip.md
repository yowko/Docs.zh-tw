---
title: 如何：在 StatusStrip 中以互動方式使用 Spring 屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: 3319771cfcf671f5457bd3e95d264a694f9fa1c6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555382"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="27ae6-102">如何：在 StatusStrip 中以互動方式使用 Spring 屬性</span><span class="sxs-lookup"><span data-stu-id="27ae6-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="27ae6-103">您可以使用 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性，將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項放置在 <xref:System.Windows.Forms.StatusStrip> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="27ae6-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="27ae6-104"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性會判斷 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項是否會自動填滿 <xref:System.Windows.Forms.StatusStrip> 控制項上的可用空間。</span><span class="sxs-lookup"><span data-stu-id="27ae6-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27ae6-105">範例</span><span class="sxs-lookup"><span data-stu-id="27ae6-105">Example</span></span>  
 <span data-ttu-id="27ae6-106">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性，將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項放置在 <xref:System.Windows.Forms.StatusStrip> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="27ae6-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="27ae6-107"><xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式會執行 Exclusive-OR (XOR) 運算，以切換 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="27ae6-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="27ae6-108">若要使用此程式碼範例，編譯並執行應用程式，然後按**Middle (Spring)** 上<xref:System.Windows.Forms.StatusStrip>控制項的值切換為<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="27ae6-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27ae6-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="27ae6-109">Compiling the Code</span></span>  
 <span data-ttu-id="27ae6-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="27ae6-110">This example requires:</span></span>  
  
-   <span data-ttu-id="27ae6-111">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="27ae6-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="27ae6-112">建置此範例從命令列 visual Basic 或 Visual C# 的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="27ae6-112">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="27ae6-113">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="27ae6-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="27ae6-114">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="27ae6-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ae6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27ae6-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="27ae6-116">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="27ae6-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
