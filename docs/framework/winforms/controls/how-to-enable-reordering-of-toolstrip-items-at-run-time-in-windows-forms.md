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
ms.openlocfilehash: 0800acc955ff8cf9efa7bc183f10d2b5cc87aac6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713708"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>HOW TO：啟用在 Windows Form 在執行階段重新排列 ToolStrip 項目
您可以讓使用者能夠重新安排<xref:System.Windows.Forms.ToolStripItem>上控制項的<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>若要啟用在執行階段的 prvku ToolStripItem 重新排列  
  
-   將 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 屬性設定為 `true`。 根據預設，<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>是`false`。  
  
     在執行階段，而按住 ALT 鍵並拖曳滑鼠左鍵<xref:System.Windows.Forms.ToolStripItem>上的不同位置<xref:System.Windows.Forms.ToolStrip>。  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
