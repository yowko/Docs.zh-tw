---
title: HOW TO：啟用在 Windows Form 在執行階段重新排列 ToolStrip 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: 46a5a70206e7620341a484912c7fada82d64747a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609842"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="db10f-102">HOW TO：啟用在 Windows Form 在執行階段重新排列 ToolStrip 項目</span><span class="sxs-lookup"><span data-stu-id="db10f-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="db10f-103">您可以讓使用者能夠重新安排<xref:System.Windows.Forms.ToolStripItem>上控制項的<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="db10f-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="db10f-104">若要啟用在執行階段的 prvku ToolStripItem 重新排列</span><span class="sxs-lookup"><span data-stu-id="db10f-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
- <span data-ttu-id="db10f-105">將 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="db10f-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="db10f-106">根據預設，<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>是`false`。</span><span class="sxs-lookup"><span data-stu-id="db10f-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="db10f-107">在執行階段，而按住 ALT 鍵並拖曳滑鼠左鍵<xref:System.Windows.Forms.ToolStripItem>上的不同位置<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="db10f-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="db10f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db10f-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="db10f-109">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="db10f-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="db10f-110">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="db10f-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="db10f-111">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="db10f-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
