---
title: HOW TO：將 ToolStrip 移出 ToolStripContainer 並移至表單上
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 100e744e6e49fbf214488e9bbb796b5b6fb9591a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142359"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="bdfb6-102">HOW TO：將 ToolStrip 移出 ToolStripContainer 並移至表單上</span><span class="sxs-lookup"><span data-stu-id="bdfb6-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="bdfb6-103">使用下列程序移動<xref:System.Windows.Forms.ToolStrip>共<xref:System.Windows.Forms.ToolStripContainer>拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdfb6-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bdfb6-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bdfb6-106">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="bdfb6-107">若要移動 ToolStrip 從 toolstripcontainer 並移至表單</span><span class="sxs-lookup"><span data-stu-id="bdfb6-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="bdfb6-108">選取 <xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="bdfb6-109">剪下<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + X，或以滑鼠右鍵按一下<xref:System.Windows.Forms.ToolStrip>，然後選擇**剪下**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="bdfb6-110">選取的表單。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="bdfb6-111">貼上<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + V，或選擇**貼上**從**編輯**功能表。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="bdfb6-112">設定<xref:System.Windows.Forms.ToolStrip.Dock%2A>的屬性<xref:System.Windows.Forms.ToolStrip>要**頂端**。</span><span class="sxs-lookup"><span data-stu-id="bdfb6-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfb6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdfb6-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="bdfb6-114">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="bdfb6-114">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
