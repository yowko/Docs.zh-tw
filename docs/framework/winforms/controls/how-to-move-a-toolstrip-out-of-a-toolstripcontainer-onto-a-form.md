---
title: "如何：將 ToolStrip 移出 ToolStripContainer 並移至表單上"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02d1e4b105329f3d346168123debbbf73e17b9eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="1177f-102">如何：將 ToolStrip 移出 ToolStripContainer 並移至表單上</span><span class="sxs-lookup"><span data-stu-id="1177f-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="1177f-103">使用下列程序移動<xref:System.Windows.Forms.ToolStrip>超出<xref:System.Windows.Forms.ToolStripContainer>拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="1177f-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1177f-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="1177f-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1177f-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="1177f-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1177f-106">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="1177f-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="1177f-107">若要移動 ToolStrip 從 toolstripcontainer 並移至表單</span><span class="sxs-lookup"><span data-stu-id="1177f-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="1177f-108">選取 <xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="1177f-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="1177f-109">剪下<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + X，或以滑鼠右鍵按一下<xref:System.Windows.Forms.ToolStrip>選擇**剪下**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="1177f-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="1177f-110">選取的表單。</span><span class="sxs-lookup"><span data-stu-id="1177f-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="1177f-111">貼上<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + V，或選擇**貼上**從**編輯**功能表。</span><span class="sxs-lookup"><span data-stu-id="1177f-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="1177f-112">設定<xref:System.Windows.Forms.ToolStrip.Dock%2A>屬性<xref:System.Windows.Forms.ToolStrip>至**頂端**。</span><span class="sxs-lookup"><span data-stu-id="1177f-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1177f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1177f-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="1177f-114">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1177f-114">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
