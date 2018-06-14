---
title: 如何：使用 ToolStrip 控制項中的工具提示
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 2b10b3fcf3930d5848f1d7a9602cfcc945bc8975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534069"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>如何：使用 ToolStrip 控制項中的工具提示
您可以顯示<xref:System.Windows.Forms.ToolTip>如<xref:System.Windows.Forms.ToolStrip>您想要藉由設定控制項的控制項<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性`true`。  
  
### <a name="to-display-a-tooltip"></a>若要顯示的工具提示  
  
-   設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>控制項的屬性`true`。  
  
     預設值<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`true`的預設值和<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>和<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`false`。  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>若要使用工具提示文字的 ToolStripButton ToolTipText 屬性  
  
1.  設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>按鈕的屬性`true`。  
  
2.  設定<xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>按鈕的屬性`false`。  
  
     `AutoToolTip`屬性是`true`預設<xref:System.Windows.Forms.ToolStripButton>， <xref:System.Windows.Forms.ToolStripDropDownButton>，和<xref:System.Windows.Forms.ToolStripSplitButton>。  
  
     A<xref:System.Windows.Forms.ToolStripButton>會使用其`Text`屬性<xref:System.Windows.Forms.ToolTip>預設文字。 使用此程序來顯示中的自訂文字<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>。  
  
> [!NOTE]
>  如果您設定<xref:System.Windows.Forms.ToolStripItemDisplayStyle>至<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>，任何文字會出現在按鈕上，但仍會顯示工具提示。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
