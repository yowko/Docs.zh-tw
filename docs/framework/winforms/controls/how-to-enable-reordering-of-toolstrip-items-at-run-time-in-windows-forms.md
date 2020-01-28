---
title: 如何：啟用 Windows Form 在執行階段時重新排列 ToolStrip 項目
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
ms.openlocfilehash: 44b52bf997819f090569d08eb395d8af18f61370
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745484"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="2bb6e-102">如何：啟用 Windows Form 在執行階段時重新排列 ToolStrip 項目</span><span class="sxs-lookup"><span data-stu-id="2bb6e-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="2bb6e-103">您可以讓使用者重新排列 <xref:System.Windows.Forms.ToolStrip>上的 <xref:System.Windows.Forms.ToolStripItem> 控制項。</span><span class="sxs-lookup"><span data-stu-id="2bb6e-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="2bb6e-104">在執行時間啟用 ToolStripItem 重新排列</span><span class="sxs-lookup"><span data-stu-id="2bb6e-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
- <span data-ttu-id="2bb6e-105">將 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="2bb6e-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="2bb6e-106">預設會 `false`<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>。</span><span class="sxs-lookup"><span data-stu-id="2bb6e-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="2bb6e-107">在執行時間，使用者按住 ALT 鍵並按滑鼠左鍵，將 <xref:System.Windows.Forms.ToolStripItem> 拖曳至 <xref:System.Windows.Forms.ToolStrip>上的不同位置。</span><span class="sxs-lookup"><span data-stu-id="2bb6e-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2bb6e-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="2bb6e-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="2bb6e-109">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2bb6e-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="2bb6e-110">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="2bb6e-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="2bb6e-111">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="2bb6e-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
