---
title: HOW TO：將控制項和表單邊緣對齊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 33a3b2e996bdab280eb7a4cd8ad7c59ccb1a1bd2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713887"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>HOW TO：將控制項和表單邊緣對齊
您可設定 <xref:System.Windows.Forms.Control.Dock%2A> 屬性讓控制項對齊表單邊緣。 這個屬性會指定您的控制項在表單中的位置。 可將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為下列值：  
  
|設定|對控制項的影響|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|停駐在表單下方。|  
|<xref:System.Windows.Forms.DockStyle.Fill>|填滿表單中剩下的空間。|  
|<xref:System.Windows.Forms.DockStyle.Left>|停駐在表單左方。|  
|<xref:System.Windows.Forms.DockStyle.None>|不會停駐在任何地方，且會出現在 <xref:System.Windows.Forms.Control.Location%2A> 屬性所指定的位置。|  
|<xref:System.Windows.Forms.DockStyle.Right>|停駐在表單右方。|  
|<xref:System.Windows.Forms.DockStyle.Top>|停駐在表單上方。|  
  
 Visual Studio 中有針對此功能提供的設計階段支援。  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a>在執行階段設定控制項的 Dock 屬性  
  
1.  在程式碼中，將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為適當值。  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)
- [如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize 屬性概觀](autosize-property-overview.md)
