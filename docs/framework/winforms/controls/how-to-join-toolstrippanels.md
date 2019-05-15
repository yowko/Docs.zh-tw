---
title: HOW TO：聯結 ToolStripPanels
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: d9cacddecdf3859a0fca4038481eeab417e22e6a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592392"
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="d9c53-102">作法：聯結 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="d9c53-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="d9c53-103">您可以在執行階段將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>，以提供多重文件介面 (MDI) 應用程式的彈性。</span><span class="sxs-lookup"><span data-stu-id="d9c53-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c53-104">範例</span><span class="sxs-lookup"><span data-stu-id="d9c53-104">Example</span></span>  
 <span data-ttu-id="d9c53-105">下列程式碼範例示範如何將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="d9c53-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9c53-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d9c53-106">Compiling the Code</span></span>  
 <span data-ttu-id="d9c53-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d9c53-107">This example requires:</span></span>  
  
- <span data-ttu-id="d9c53-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d9c53-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c53-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9c53-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- [<span data-ttu-id="d9c53-110">如何：針對 MDI 使用 ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="d9c53-110">How to: Use ToolStripPanels for MDI</span></span>](how-to-use-toolstrippanels-for-mdi.md)
