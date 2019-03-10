---
title: HOW TO：將移出 toolstripcontainer 並移到表單上 ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 96fe863cee296ec292bf7010494af587d43fd8b3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708414"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="de3c4-102">HOW TO：將移出 toolstripcontainer 並移到表單上 ToolStrip</span><span class="sxs-lookup"><span data-stu-id="de3c4-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="de3c4-103">使用下列程序移動<xref:System.Windows.Forms.ToolStrip>共<xref:System.Windows.Forms.ToolStripContainer>拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="de3c4-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de3c4-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="de3c4-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="de3c4-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="de3c4-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="de3c4-106">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="de3c4-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="de3c4-107">若要移動 ToolStrip 從 toolstripcontainer 並移至表單</span><span class="sxs-lookup"><span data-stu-id="de3c4-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="de3c4-108">選取 <xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="de3c4-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="de3c4-109">剪下<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + X，或以滑鼠右鍵按一下<xref:System.Windows.Forms.ToolStrip>，然後選擇**剪下**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="de3c4-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="de3c4-110">選取的表單。</span><span class="sxs-lookup"><span data-stu-id="de3c4-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="de3c4-111">貼上<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + V，或選擇**貼上**從**編輯**功能表。</span><span class="sxs-lookup"><span data-stu-id="de3c4-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="de3c4-112">設定<xref:System.Windows.Forms.ToolStrip.Dock%2A>的屬性<xref:System.Windows.Forms.ToolStrip>要**頂端**。</span><span class="sxs-lookup"><span data-stu-id="de3c4-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3c4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de3c4-113">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="de3c4-114">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="de3c4-114">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
