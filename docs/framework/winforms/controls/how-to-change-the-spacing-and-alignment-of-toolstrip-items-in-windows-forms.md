---
title: HOW TO：變更 Windows Forms 中 ToolStrip 項目的間距和對齊方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: c7a874659be8dbaec66b78e1e065bcbec21da3b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650882"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>HOW TO：變更 Windows Forms 中 ToolStrip 項目的間距和對齊方式
<xref:System.Windows.Forms.ToolStrip>完全支援控制項的版面配置功能，例如調整大小、 間距<xref:System.Windows.Forms.ToolStripItem>彼此相對，控制項的排列方式的控制項<xref:System.Windows.Forms.ToolStrip>，以及相對於控制項的間距<xref:System.Windows.Forms.ToolStrip>。  
  
 因為預設值<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性是`true`，除非您設定控制項的自動大小<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性設`false`。  
  
### <a name="to-manually-size-a-toolstripitem"></a>若要手動調整大小 prvku ToolStripItem  
  
1. 設定<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性設`false`關聯的控制項。  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. 設定<xref:System.Windows.Forms.ToolStripItem.Size%2A>屬性是您所要關聯<xref:System.Windows.Forms.ToolStripItem>。  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>若要設定的間距 prvku ToolStripItem  
  
1. 插入所需的值，單位為像素<xref:System.Windows.Forms.ToolStripItem.Margin%2A>關聯控制項的屬性。  
  
     值<xref:System.Windows.Forms.ToolStripItem.Margin%2A>屬性指定的項目和相鄰項目之間的間距，順序如下：左側、 頂端、 右側，與下方。  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>若要靠右對齊的 ToolStrip prvku ToolStripItem  
  
1. 設定<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性設<xref:System.Windows.Forms.ToolStripItemAlignment.Right>關聯的控制項。 根據預設，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>設定為<xref:System.Windows.Forms.ToolStripItemAlignment.Left>，以配合控制項的左邊<xref:System.Windows.Forms.ToolStrip>。  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>若要排列 ToolStrip 項目，在 ToolStrip 上  
  
- 設定<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>屬性設為值的<xref:System.Windows.Forms.ToolStripLayoutStyle>您想要的。  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
