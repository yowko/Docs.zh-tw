---
title: HOW TO：以動態方式新增 ToolStrip 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: d84b62005554479d227778f513e72594322791a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124926"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="59bcb-102">HOW TO：以動態方式新增 ToolStrip 項目</span><span class="sxs-lookup"><span data-stu-id="59bcb-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="59bcb-103">在功能表開啟時，您可以動態填入 <xref:System.Windows.Forms.ToolStrip> 控制項的功能表項目集合。</span><span class="sxs-lookup"><span data-stu-id="59bcb-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59bcb-104">範例</span><span class="sxs-lookup"><span data-stu-id="59bcb-104">Example</span></span>  
 <span data-ttu-id="59bcb-105">下列程式碼範例示範如何將項目動態加入 <xref:System.Windows.Forms.ContextMenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="59bcb-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="59bcb-106">此範例也示範如何針對表單上的三個不同控制項，重複使用相同的 <xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="59bcb-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="59bcb-107">在此範例中，<xref:System.Windows.Forms.ToolStripDropDown.Opening> 事件處理常式會填入功能表項目集合。</span><span class="sxs-lookup"><span data-stu-id="59bcb-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="59bcb-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> 事件處理常式會檢查 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> 屬性，並加入 <xref:System.Windows.Forms.ToolStripItem> 以描述原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="59bcb-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59bcb-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="59bcb-109">Compiling the Code</span></span>  
 <span data-ttu-id="59bcb-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="59bcb-110">This example requires:</span></span>  
  
-   <span data-ttu-id="59bcb-111">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="59bcb-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="59bcb-112">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="59bcb-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="59bcb-113">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="59bcb-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bcb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59bcb-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="59bcb-115">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="59bcb-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
