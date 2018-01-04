---
title: "如何：當滑鼠指標移至 ToolStripItem 上時偵測"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b04d0ef38a8946abc43da2672ade0723f5f2446f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="01bd8-102">如何：當滑鼠指標移至 ToolStripItem 上時偵測</span><span class="sxs-lookup"><span data-stu-id="01bd8-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="01bd8-103">使用下列程序來偵測當滑鼠指標位於<xref:System.Windows.Forms.ToolStripItem>。</span><span class="sxs-lookup"><span data-stu-id="01bd8-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="01bd8-104">當指標移至 toolstripitem 上時偵測</span><span class="sxs-lookup"><span data-stu-id="01bd8-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
-   <span data-ttu-id="01bd8-105">使用<xref:System.Windows.Forms.ToolStripItem.Selected%2A>中的項目屬性<xref:System.Windows.Forms.ToolStripItem.CanSelect%2A>是`true`。</span><span class="sxs-lookup"><span data-stu-id="01bd8-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="01bd8-106">這會讓您不需要同步處理<xref:System.Windows.Forms.ToolStripItem.MouseEnter>和<xref:System.Windows.Forms.ToolStripItem.MouseLeave>事件。</span><span class="sxs-lookup"><span data-stu-id="01bd8-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bd8-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="01bd8-107">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [<span data-ttu-id="01bd8-108">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="01bd8-108">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
