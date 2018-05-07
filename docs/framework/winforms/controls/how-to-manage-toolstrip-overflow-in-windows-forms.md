---
title: 如何：管理 Windows Form 中的 ToolStrip 溢位
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 32bbc06320f0dc7f096a4b9021bebfbefedaf8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>如何：管理 Windows Form 中的 ToolStrip 溢位
當上的所有項目<xref:System.Windows.Forms.ToolStrip>控制項無法放入配置的空間，您可以在啟用溢位功能<xref:System.Windows.Forms.ToolStrip>和決定特定的溢位行為<xref:System.Windows.Forms.ToolStripItem>s。  
  
 當您將加入<xref:System.Windows.Forms.ToolStripItem>s 需要更多的空間比分配給<xref:System.Windows.Forms.ToolStrip>指定表單的目前大小，<xref:System.Windows.Forms.ToolStripOverflowButton>上就會自動出現<xref:System.Windows.Forms.ToolStrip>。 <xref:System.Windows.Forms.ToolStripOverflowButton>隨即出現，並啟用溢位的項目會變成下拉式溢位功能表。 這可讓您自訂並優先處理如何您<xref:System.Windows.Forms.ToolStrip>項目適當地調整不同表單大小。 您也可以變更的項目外觀，當它們分成使用溢位<xref:System.Windows.Forms.ToolStripItem.Placement%2A>和<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType>屬性和<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件。 如果您放大表單在設計階段或執行的階段，更<xref:System.Windows.Forms.ToolStripItem>s 可以顯示在主要<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.ToolStripOverflowButton>可能甚至會消失，直到您減少表單的大小。  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a>若要啟用溢位在 ToolStrip 控制項  
  
-   請確認<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>屬性未設定為`false`如<xref:System.Windows.Forms.ToolStrip>。 預設值為 `True`。  
  
     當<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>是`True`（預設）、<xref:System.Windows.Forms.ToolStripItem>傳送至下拉式溢位功能表時的內容<xref:System.Windows.Forms.ToolStripItem>超過水平寬度<xref:System.Windows.Forms.ToolStrip>或高度的垂直<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>若要指定特定 ToolStripItem 的溢位行為  
  
-   設定<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性<xref:System.Windows.Forms.ToolStripItem>所要的值。 這些可能是`Always`， `Never`，和`AsNeeded`。 Defaultis `AsNeeded`。  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
