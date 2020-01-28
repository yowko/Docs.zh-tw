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
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>如何：啟用 Windows Form 在執行階段時重新排列 ToolStrip 項目
您可以讓使用者重新排列 <xref:System.Windows.Forms.ToolStrip>上的 <xref:System.Windows.Forms.ToolStripItem> 控制項。  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>在執行時間啟用 ToolStripItem 重新排列  
  
- 將 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 屬性設定為 `true`。 預設會 `false`<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>。  
  
     在執行時間，使用者按住 ALT 鍵並按滑鼠左鍵，將 <xref:System.Windows.Forms.ToolStripItem> 拖曳至 <xref:System.Windows.Forms.ToolStrip>上的不同位置。  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
