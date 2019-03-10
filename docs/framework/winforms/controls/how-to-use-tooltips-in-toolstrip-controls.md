---
title: HOW TO：使用 ToolStrip 控制項中的工具提示
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 7177daef469f6c601cfa468c6437deb9653ffc85
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707465"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>HOW TO：使用 ToolStrip 控制項中的工具提示
您可以顯示<xref:System.Windows.Forms.ToolTip>for<xref:System.Windows.Forms.ToolStrip>您想要藉由設定控制項的控制項<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性設`true`。  
  
### <a name="to-display-a-tooltip"></a>若要顯示工具提示  
  
-   設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性來控制`true`。  
  
     預設值<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>已`true`，和預設值<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>並<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`false`。  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>要用於工具提示文字的 prvek ToolStripButton ToolTipText 屬性  
  
1.  設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性的按鈕`true`。  
  
2.  設定<xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>屬性的按鈕`false`。  
  
     `AutoToolTip`屬性是`true`的預設<xref:System.Windows.Forms.ToolStripButton>， <xref:System.Windows.Forms.ToolStripDropDownButton>，和<xref:System.Windows.Forms.ToolStripSplitButton>。  
  
     A<xref:System.Windows.Forms.ToolStripButton>會使用其`Text`屬性<xref:System.Windows.Forms.ToolTip>預設的文字。 使用此程序顯示自訂的文字<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>。  
  
> [!NOTE]
>  如果您設定<xref:System.Windows.Forms.ToolStripItemDisplayStyle>要<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>，沒有文字會出現在 [] 按鈕，但仍會顯示工具提示。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
