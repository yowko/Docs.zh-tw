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
ms.openlocfilehash: d70c5b8f548cf325083782d6ea185c18fd2fa003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011134"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="0928c-102">HOW TO：將 ToolStripContainer 新增至表單</span><span class="sxs-lookup"><span data-stu-id="0928c-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="0928c-103">您可以程式設計方式加入 <xref:System.Windows.Forms.ToolStripContainer> 至 Windows Form 並填入控制項。</span><span class="sxs-lookup"><span data-stu-id="0928c-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0928c-104">範例</span><span class="sxs-lookup"><span data-stu-id="0928c-104">Example</span></span>  
 <span data-ttu-id="0928c-105">下列程式碼範例示範如何加入 <xref:System.Windows.Forms.ToolStripContainer> 和 <xref:System.Windows.Forms.ToolStrip> 至 Windows Form，如何將項目加入 <xref:System.Windows.Forms.ToolStrip>，以及如何加入 <xref:System.Windows.Forms.ToolStrip> 到 <xref:System.Windows.Forms.ToolStripContainer> 的 <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>。</span><span class="sxs-lookup"><span data-stu-id="0928c-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0928c-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0928c-106">Compiling the Code</span></span>  
 <span data-ttu-id="0928c-107">這個程式碼範例需要：</span><span class="sxs-lookup"><span data-stu-id="0928c-107">This code example requires:</span></span>  
  
- <span data-ttu-id="0928c-108">System.Drawing、System.Text 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0928c-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0928c-109">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="0928c-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0928c-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0928c-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0928c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0928c-111">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="0928c-112">ToolStripContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="0928c-112">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="0928c-113">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="0928c-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
