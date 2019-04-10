---
title: HOW TO：固定 Windows Forms 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: d015dce7307bec092f6da1dc5ee31691a6baf1f0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317255"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>HOW TO：固定 Windows Forms 上的控制項
您可以將控制項停駐在表單的邊緣，或讓它們填滿控制項的容器 （表單或容器控制項）。 比方說，Windows 檔案總管停駐於其<xref:System.Windows.Forms.TreeView>視窗的左側的控制項及其<xref:System.Windows.Forms.ListView>視窗右邊的控制項。 使用<xref:System.Windows.Forms.Control.Dock%2A>所有可見定義固定模式的 Windows Form 控制項的屬性。  
  
> [!NOTE]
>  控制項停駐在反向的疊置順序。  
  
 <xref:System.Windows.Forms.Control.Dock%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。 如需詳細資訊，請參閱 < [AutoSize 屬性概觀](autosize-property-overview.md)。  
  
### <a name="to-dock-a-control"></a>若要停駐控制項  
  
1. 選取您想要停駐的控制項。  
  
2. 在 [屬性] 視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Dock%2A>屬性。  
  
     編輯器隨即出現，顯示一系列代表的邊緣和表單的中央的方塊。  
  
3. 按一下按鈕，表示您想要的控制項停駐在表單的邊緣。 若要填滿控制項的表單或容器控制項的內容，請按一下 [中心] 方塊。 按一下  **（無）** 停用停駐。  
  
     控制會自動調整大小以填滿停駐的邊緣的邊界。  
  
    > [!NOTE]
    >  繼承的控制項必須`Protected`能夠停駐。 若要變更控制項的存取層級，設定其**修飾詞**屬性 視窗中的屬性。  
  
## <a name="see-also"></a>另請參閱

- [Windows Form 控制項](index.md)
- [排列 Windows Form 上的控制項](arranging-controls-on-windows-forms.md)
- [標記個別 Windows Form 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Form 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Form 控制項](windows-forms-controls-by-function.md)
- [HOW TO：錨定和停駐 FlowLayoutPanel 控制項中的子控制項](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [HOW TO：錨定和停駐 TableLayoutPanel 控制項中的子控制項](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize 屬性概觀](autosize-property-overview.md)
- [HOW TO：錨定 Windows Forms 上的控制項](how-to-anchor-controls-on-windows-forms.md)
