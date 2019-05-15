---
title: HOW TO：將 ToolStripContainer 新增至表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 3d69bc6ed0cf23da8315ae95565300d151069d51
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582584"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="ae89e-102">作法：將 ToolStripContainer 新增至表單</span><span class="sxs-lookup"><span data-stu-id="ae89e-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="ae89e-103">您可以程式設計方式加入 <xref:System.Windows.Forms.ToolStripContainer> 至 Windows Form 並填入控制項。</span><span class="sxs-lookup"><span data-stu-id="ae89e-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae89e-104">範例</span><span class="sxs-lookup"><span data-stu-id="ae89e-104">Example</span></span>  
 <span data-ttu-id="ae89e-105">下列程式碼範例示範如何加入 <xref:System.Windows.Forms.ToolStripContainer> 和 <xref:System.Windows.Forms.ToolStrip> 至 Windows Form，如何將項目加入 <xref:System.Windows.Forms.ToolStrip>，以及如何加入 <xref:System.Windows.Forms.ToolStrip> 到 <xref:System.Windows.Forms.ToolStripContainer> 的 <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>。</span><span class="sxs-lookup"><span data-stu-id="ae89e-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae89e-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ae89e-106">Compiling the Code</span></span>  
 <span data-ttu-id="ae89e-107">這個程式碼範例需要：</span><span class="sxs-lookup"><span data-stu-id="ae89e-107">This code example requires:</span></span>  
  
- <span data-ttu-id="ae89e-108">System.Drawing、System.Text 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ae89e-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae89e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae89e-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="ae89e-110">ToolStripContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="ae89e-110">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="ae89e-111">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="ae89e-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
