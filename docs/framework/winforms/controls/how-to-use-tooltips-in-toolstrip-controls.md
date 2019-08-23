---
title: HOW TO：在 ToolStrip 控制項使用工具提示
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939737"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>HOW TO：在 ToolStrip 控制項使用工具提示
您可以藉由<xref:System.Windows.Forms.ToolTip>將控制項<xref:System.Windows.Forms.ToolStrip>的<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性設定為`true`, 為您想要的控制項顯示。  
  
### <a name="to-display-a-tooltip"></a>若要顯示工具提示  
  
- 將控制項<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>的屬性設為。 `true`  
  
     的<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>預設值`false`為`true`, 且<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>和<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>的預設值為。  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>若要針對 ToolStripButton 的工具提示文字使用 ToolTipText 屬性  
  
1. 將按鈕的`true` <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性設定為。  
  
2. 將按鈕的`false` <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>屬性設定為。  
  
     `AutoToolTip`屬性預設為<xref:System.Windows.Forms.ToolStripButton> 、<xref:System.Windows.Forms.ToolStripSplitButton>和。 `true` <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
     預設會針對`Text` <xref:System.Windows.Forms.ToolStripButton> 文字<xref:System.Windows.Forms.ToolTip>使用其屬性。 使用此程式可在中<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>顯示自訂文字。  
  
> [!NOTE]
> 如果您將<xref:System.Windows.Forms.ToolStripItemDisplayStyle>設定<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>或, 按鈕上不會出現任何文字, 但是工具提示仍然會出現。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
