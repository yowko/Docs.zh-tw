---
title: 作法：建立具有 ToolStripPanel 控制項的 MDI 表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms [Windows Forms]
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
ms.assetid: d198ef8e-f7c4-4b3f-a7f5-ce858cb90cec
ms.openlocfilehash: 4dae528d69c6c08c2005fd30d7d16fafa67afb53
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590557"
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="31c2c-102">作法：建立具有 ToolStripPanel 控制項的 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="31c2c-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="31c2c-103">您可以建立在四邊都讓 <xref:System.Windows.Forms.ToolStrip> 控制項框架處理的多重文件介面 (MDI) 表單。</span><span class="sxs-lookup"><span data-stu-id="31c2c-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31c2c-104">範例</span><span class="sxs-lookup"><span data-stu-id="31c2c-104">Example</span></span>  
 <span data-ttu-id="31c2c-105">下列程式碼範例示範如何使用停駐的 <xref:System.Windows.Forms.ToolStripPanel> 控制項搭配四個 <xref:System.Windows.Forms.ToolStrip> 控制項框住 MDI 視窗。</span><span class="sxs-lookup"><span data-stu-id="31c2c-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="31c2c-106">在範例中，<xref:System.Windows.Forms.ToolStripPanel.Join%2A> 方法會附加至 <xref:System.Windows.Forms.ToolStrip> 控制項以對應 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="31c2c-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="31c2c-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="31c2c-107">Compiling the Code</span></span>  
 <span data-ttu-id="31c2c-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="31c2c-108">This example requires:</span></span>  
  
- <span data-ttu-id="31c2c-109">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="31c2c-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c2c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31c2c-110">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- <xref:System.Windows.Forms.ToolStripPanel.Join%2A>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="31c2c-111">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="31c2c-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
