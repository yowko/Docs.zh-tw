---
title: 如何：將控制項定位在 Windows Form 上
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 6db021f2b1a29c3ef52a182c45bbc7878feebb97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-position-controls-on-windows-forms"></a>如何：將控制項定位在 Windows Form 上
若要定位控制項、 使用 Windows Form 設計工具，或指定<xref:System.Windows.Forms.Control.Location%2A>屬性。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>若要將 Windows Form 設計工具的設計介面上的控制項  
  
-   將控制項拖曳至適當的位置，使用滑鼠。  
  
    > [!NOTE]
    >  選取控制項，並將它的箭號，更精確地將它定位索引鍵。 此外，*對齊線*協助您放置在表單上的精確控制項。 如需詳細資訊，請參閱[逐步解說： 在 Windows Form 使用對齊線排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。  
  
### <a name="to-position-a-control-using-the-properties-window"></a>若要將使用 [屬性] 視窗的控制項  
  
1.  按一下您要放置的控制項。  
  
2.  在**屬性** 視窗中，型別值<xref:System.Windows.Forms.Control.Location%2A>屬性，來定位控制項容器中的控制項的逗號分隔。  
  
     第一個數字 (X) 是從容器; 左框線的距離第二個數字 (Y) 是從容器區域中，以像素表示上框線的距離。  
  
    > [!NOTE]
    >  您可以展開<xref:System.Windows.Forms.Control.Location%2A>屬性輸入**X**和**Y**個別值。  
  
### <a name="to-position-a-control-programmatically"></a>若要以程式設計方式調整控制項的位置  
  
1.  設定<xref:System.Windows.Forms.Control.Location%2A>控制項的屬性<xref:System.Drawing.Point>。  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  變更控制項的位置的 X 座標使用<xref:System.Windows.Forms.Control.Left%2A>子屬性。  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a>若要以程式設計方式遞增控制項的位置  
  
1.  設定<xref:System.Windows.Forms.Control.Left%2A>遞增控制項的 X 座標的子屬性。  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  使用<xref:System.Windows.Forms.Control.Location%2A>同時將屬性設定控制項的 X 和 Y。 若要個別設定的位置，使用控制項的<xref:System.Windows.Forms.Control.Left%2A>(**X**) 或<xref:System.Windows.Forms.Control.Top%2A>(**Y**) 子屬性。 不會嘗試隱含地設定的 X 和 Y 座標<xref:System.Drawing.Point>結構，表示按鈕的位置，因為此結構包含一份按鈕的座標。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [逐步解說：使用對齊線排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [依功能區分 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [如何： 設定 Windows Form 的畫面位置](http://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
