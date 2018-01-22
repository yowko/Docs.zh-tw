---
title: "如何：錨定 Windows Form 上的控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceaacc250d48e7199d7224f95aa91ed976c097e0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>如何：錨定 Windows Form 上的控制項
如果您要設計的表單，使用者可以在執行階段調整大小，將表單上的控制項應調整大小，並適當地重新調整位置。 若要調整大小以動態方式使用表單的控制項，您可以使用<xref:System.Windows.Forms.Control.Anchor%2A>Windows Form 控制項的屬性。 <xref:System.Windows.Forms.Control.Anchor%2A>屬性會定義控制項的錨點位置。 當控制項錨定至表單，並調整表單大小時，控制項就會維護控制項的錨點位置之間的距離。 例如，如果您有<xref:System.Windows.Forms.TextBox>錨定的左方、 右方和下邊緣的表單，表單調整大小時，控制項<xref:System.Windows.Forms.TextBox>水平控制項會調整大小，以便保持相同的距離，從表單的左邊和右邊側邊。 此外，控制項本身也會做垂直定位，因此其位置一律會從表單的邊緣相同的距離。 如果控制項不錨定和調整表單大小時，會變更控制項相對於表單的邊緣的位置。  
  
 <xref:System.Windows.Forms.Control.Anchor%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。 如需詳細資訊，請參閱[AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-anchor-a-control-on-a-form"></a>若要錨定在表單上的控制項  
  
1.  選取您想要錨定的控制項。  
  
    > [!NOTE]
    >  您可以按住 CTRL 鍵，按一下以選取它，每個控制項，然後遵循此程序的其餘同時錨定多個控制項。  
  
2.  在**屬性**視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Anchor%2A>屬性。  
  
     編輯器會隨即出現，顯示交叉。  
  
3.  設定錨點，請按一下左上方、 右側或底端交叉區段。  
  
     控制項可錨定至頂端，而且留下的預設值。  
  
4.  若要清除已錨定的控制項的一邊，請按一下該 arm 的交叉。  
  
5.  若要關閉<xref:System.Windows.Forms.Control.Anchor%2A>屬性編輯器中，按一下<xref:System.Windows.Forms.Control.Anchor%2A>再次屬性名稱。  
  
 當表單出現在執行階段時，控制項會調整大小以便維持在相同的距離，從表單的邊緣。 錨定的邊緣之間的距離一定會保持相同的距離會定義當控制項放置在 Windows Form 設計工具。  
  
> [!NOTE]
>  特定控制項，例如<xref:System.Windows.Forms.ComboBox>控制項，其高度限制。 錨定至底部其表單或容器控制項無法強制控制項超過其高度限制。  
  
 繼承的控制項必須是`Protected`能夠錨定。 若要變更控制項的存取層級，設定其`Modifiers`屬性**屬性**視窗。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [操作說明：將控制項停駐在 Windows Forms 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
