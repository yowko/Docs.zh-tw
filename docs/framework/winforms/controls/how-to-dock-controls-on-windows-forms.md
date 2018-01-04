---
title: "如何：將控制項停駐在 Windows Form 上"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc7227ee46f127070b44771a56a89b82bd0930ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dock-controls-on-windows-forms"></a>如何：將控制項停駐在 Windows Form 上
您可以停駐控制項至表單的邊緣，或讓它們填滿控制項的容器 （表單或容器控制項）。 例如，Windows 檔案總管停駐於其<xref:System.Windows.Forms.TreeView>控制項視窗的左邊及其<xref:System.Windows.Forms.ListView>視窗右邊的控制項。 使用<xref:System.Windows.Forms.Control.Dock%2A>所有可見的 Windows Form 控制項定義的固定模式屬性。  
  
> [!NOTE]
>  反轉 z 軸順序停駐控制項。  
  
 <xref:System.Windows.Forms.Control.Dock%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。 如需詳細資訊，請參閱[AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。  
  
### <a name="to-dock-a-control"></a>若要停駐控制項  
  
1.  選取您想要停駐的控制項。  
  
2.  在 [屬性] 視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Dock%2A>屬性。  
  
     編輯器會隨即出現，顯示一系列代表的邊緣和表單的中央的方塊。  
  
3.  按一下代表您要停駐控制項的表單的邊緣的按鈕。 若要填滿控制項的表單或容器控制項的內容，請按一下中央方塊。 按一下**（無）**停用停駐。  
  
     控制項是自動調整大小以填滿停駐邊緣的邊界。  
  
    > [!NOTE]
    >  繼承的控制項必須是`Protected`能夠停駐。 若要變更控制項的存取層級，設定其**修飾詞**屬性 視窗中的屬性。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [依功能區分 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [操作說明：錨定和停駐 FlowLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [操作說明：錨定 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
