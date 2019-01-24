---
title: HOW TO：在 Windows Forms 上控制項的錨定
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: d1f1fba28eec39202b37eb410a74df400ea461a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580938"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>HOW TO：在 Windows Forms 上控制項的錨定
如果您要設計的表單，使用者可以在執行階段調整大小，您的表單上的控制項應該調整大小，並適當地重新調整位置。 若要調整大小以動態方式與所在表單的控制項，您可以使用<xref:System.Windows.Forms.Control.Anchor%2A>Windows Form 控制項的屬性。 <xref:System.Windows.Forms.Control.Anchor%2A>屬性會定義控制項的錨點位置。 當控制項錨定至表單和表單的大小時，控制項就會維護控制項的錨點位置之間的距離。 例如，如果您有<xref:System.Windows.Forms.TextBox>表單會調整大小時，left、 right 和表單的下邊緣錨定的控制項<xref:System.Windows.Forms.TextBox>水平控制項調整大小，使它可以維持相同的距離，從表單的左邊和右邊側邊。 此外，控制項本身也會做垂直定位，使其位置一律相同從表單的下邊緣的距離。 如果控制項不會錨定和表單的大小時，會變更控制項相對於表單的邊緣的位置。  
  
 <xref:System.Windows.Forms.Control.Anchor%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。 如需詳細資訊，請參閱 < [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-anchor-a-control-on-a-form"></a>若要錨定在表單上的控制項  
  
1.  選取您想要錨定的控制項。  
  
    > [!NOTE]
    >  您可以藉由按下 CTRL 鍵，按一下每個控制項以選取它，然後遵循此程序的其餘同時錨定多個控制項。  
  
2.  在 [**屬性**] 視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Anchor%2A>屬性。  
  
     編輯器隨即出現，顯示交叉。  
  
3.  若要設定錨點，按一下 上、 左、 右、 或交叉的底部區段。  
  
     控制項錨定至頂端，而且留下的預設值。  
  
4.  若要清除的控制項已經錨定的側邊，按一下 跨該部門。  
  
5.  若要關閉<xref:System.Windows.Forms.Control.Anchor%2A>屬性編輯器中，按一下 <xref:System.Windows.Forms.Control.Anchor%2A>再次屬性名稱。  
  
 當您的表單顯示在執行階段時，控制項調整大小以維持在相同的距離，從表單的邊緣。 錨定邊緣之間的距離永遠維持不變的距離會定義當控制項位於 Windows Form 設計工具。  
  
> [!NOTE]
>  特定控制項，例如<xref:System.Windows.Forms.ComboBox>控制項，其高度的限制。 錨定到底部的其表單或容器控制項，無法強制控制項超過其高度限制。  
  
 繼承的控制項必須`Protected`能夠錨定。 若要變更控制項的存取層級，設定其`Modifiers`中的屬性**屬性**視窗。  
  
## <a name="see-also"></a>另請參閱
- [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)
- [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
- [如何：停駐在 Windows Forms 上控制項](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)
- [逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：配置 Windows Form 控制項和邊框距離、 邊界和 AutoSize 屬性](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
