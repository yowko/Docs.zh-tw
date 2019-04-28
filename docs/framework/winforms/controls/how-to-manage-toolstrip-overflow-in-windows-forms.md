---
title: HOW TO：管理 Windows Form 中的 ToolStrip 溢位
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
ms.openlocfilehash: 53f610a728925d454a8833a49e705818f027aec5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913753"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>HOW TO：管理 Windows Form 中的 ToolStrip 溢位

當上的所有項目<xref:System.Windows.Forms.ToolStrip>控制項無法放入配置的空間，您可以在啟用溢位功能<xref:System.Windows.Forms.ToolStrip>，並判斷特定的溢位行為<xref:System.Windows.Forms.ToolStripItem>s。

當您將加入<xref:System.Windows.Forms.ToolStripItem>需要更多的空間比分配給<xref:System.Windows.Forms.ToolStrip>指定表單的目前大小，<xref:System.Windows.Forms.ToolStripOverflowButton>會自動出現在<xref:System.Windows.Forms.ToolStrip>。 <xref:System.Windows.Forms.ToolStripOverflowButton>隨即出現，並啟用溢位的項目會變成下拉式溢位功能表。 這可讓您自訂並排定優先順序如何您<xref:System.Windows.Forms.ToolStrip>正確調整中的項目，以不同的表單大小。 您也可以變更項目的外觀，當他們使用屬於溢位<xref:System.Windows.Forms.ToolStripItem.Placement%2A>並<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType>屬性和<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件。 如果您放大表單，在設計階段或執行的階段，更<xref:System.Windows.Forms.ToolStripItem>s 可以顯示在主要<xref:System.Windows.Forms.ToolStrip>而<xref:System.Windows.Forms.ToolStripOverflowButton>直到您在表單的大小縮小，甚至可能會消失。

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>若要啟用溢位在 ToolStrip 控制項

- 請確認<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>屬性未設定為`false`如<xref:System.Windows.Forms.ToolStrip>。 預設為 `True`。

     當<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>是`True`（預設值），<xref:System.Windows.Forms.ToolStripItem>傳送至下拉式溢位功能表時的內容<xref:System.Windows.Forms.ToolStripItem>超過的水平寬度<xref:System.Windows.Forms.ToolStrip>或高度的垂直<xref:System.Windows.Forms.ToolStrip>。

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>若要指定特定的 prvku ToolStripItem 溢位行為

- 設定<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性<xref:System.Windows.Forms.ToolStripItem>所要的值。 您可以徹底`Always`， `Never`，和`AsNeeded`。 預設為 `AsNeeded`。

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
