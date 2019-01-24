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
ms.openlocfilehash: 0b3662a700d897607780e8d5032c498faff97753
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577015"
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
- [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
