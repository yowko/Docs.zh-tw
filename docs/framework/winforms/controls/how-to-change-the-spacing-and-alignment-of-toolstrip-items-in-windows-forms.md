---
title: "如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58cad83b7253b71363f9ccf7fbda74e03803f381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式
<xref:System.Windows.Forms.ToolStrip>完全支援控制項的版面配置功能，例如調整大小、 間距<xref:System.Windows.Forms.ToolStripItem>上的控制項，相對於彼此，控制項的排列方式<xref:System.Windows.Forms.ToolStrip>，相對於控制項的間距和<xref:System.Windows.Forms.ToolStrip>。  
  
 因為預設值的<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性是`true`，控制項自動調整大小除非您將設定<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性`false`。  
  
### <a name="to-manually-size-a-toolstripitem"></a>若要手動調整大小 ToolStripItem  
  
1.  設定<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性`false`相關聯的控制項。  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  設定<xref:System.Windows.Forms.ToolStripItem.Size%2A>屬性要關聯的方式<xref:System.Windows.Forms.ToolStripItem>。  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>若要設定 ToolStripItem 的間距  
  
1.  插入所需的值，以像素<xref:System.Windows.Forms.ToolStripItem.Margin%2A>針對關聯控制項的屬性。  
  
     值<xref:System.Windows.Forms.ToolStripItem.Margin%2A>屬性指定的項目和相鄰的項目之間的間距，依此順序： 左框線、 頂端、 右側和底部。  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>若要對齊右邊的 ToolStrip 的 ToolStripItem  
  
1.  設定<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性<xref:System.Windows.Forms.ToolStripItemAlignment.Right>相關聯的控制項。 根據預設，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>設<xref:System.Windows.Forms.ToolStripItemAlignment.Left>，這會將控制項的左半部<xref:System.Windows.Forms.ToolStrip>。  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>若要排列 ToolStrip 項目在 ToolStrip 上  
  
-   設定<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>屬性設為值的<xref:System.Windows.Forms.ToolStripLayoutStyle>您想要的。  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
